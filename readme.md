
# Título do Trabalho: Perfil dos Participantes da TELOS - Fundação Embratel de Seguridade Social

#### Aluno: Maísa Gerk (https://github.com/maisagerk/PerfilParticipantes)
#### Orientadora: Manoela Kohler (https://github.com/maisagerk/PerfilParticipantes) 

---

Trabalho apresentado ao curso BI MASTER(https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- https://github.com/maisagerk/PerfilParticipantes/blob/main/Perfil_de_Aloca%C3%A7%C3%A3o_dos_Participantes_vfinal.ipynb 

---

### Resumo

Este trabalho teve por objetivo analisar os participantes da TELOS - Fundação Embratel de Suguridade Social, sendo essa uma Entidade Privada de Previdência Complementar, para identificar se os mesmos possuem perfis de investimentos que poderiam ser agrupados a partir de suas características individuais. Para isso, observou-se a base de dados da Fundação, que contém dados de seus participantes como idade, sexo, escolaridade, faixa salarial e dependentes, assim como quais as alocações dos participantes nos fundos de investimentos oferecidos pela Fundação, além de quanto dos seus salários é reservado para este fim e o histórico de suas alocações. A partir desses dados, pôde-se ver que grande parte desses participantes, apesar de apresentarem diferentes características, acabam escolhendo alocações bem semelhantes, sendo a maioria em fundos de investimento de Renda Fixa.

### 1. Introdução

A partir da base de dados da Fundação TELOS, uma Entidade Privada de Previdência Complementar, foram analisados os perfis de alocações de investimentos de seus clientes, que são chamados de participantes. Esta Fundação disponibiliza quatro fundos de investimentos para alocação das contribuições dos participantes, sendo dois desses de Renda Fixa Baixo Risco, um de Renda Fixa Médio Risco e um de Renda Variável. Para os fins deste estudo, considerou-se suficiente separar os fundos de investimentos apenas em Renda Fixa e Renda Variável. E os participantes podem escolher quanto do seu salário será alocado em cada um desses fundos mensalmente.

Logo, utilizando os dados de idade, sexo, escolaridade, faixa salarial, dependentes, percentual de contribuição e alocações dos participantes, foi identificado se os participantes poderiam ser agrupados de acordo com suas características em perfis de investimentos específicos. Esperava-se que a maioria dos participantes optassem por fundos de Renda Fixa, por saber que os maiores patrimônios são desses fundos, e que partipantes com maiores escolaridade, salário e contribuição tendessem a ter as maiores alocações no fundo de Renda Variável, por terem mais instrução e estarem mais dispostos a correrem risco. Os resultados encontrados apontaram que a primeira expectativa estava correta, porém a segunda não.

### 2. Modelagem

Este estudo foi então realizado com dados de quatro tabelas, referentes a 6042 participantes. A primeira delas foi a do grupo dos participantes, que contém dados de identificador do participante, data de nascimento, sexo, escolaridade, faixa salarial e data de inscrição no plano. Os dados de escolaridade foram separados em sete grupos: "1º Grau Completo", "2º Grau Incompleto", "2º Grau Completo", "Superior Incompleto", "Superior Completo", "Pós-graduação" e "Mestrado". Os dados de faixa salarial foram divididos em três grupos: "L1" (até R$ 3.000,00), "L2" (até R$ 10.000,00) e "L3" (maior que R$ 10.000,00). A segunda tabela utilizada foi de dependentes, que contém dados de identificador do participante, parentesco com dependente e data de nascimento do dependente. Os dados de parentesco estão divididos em onze grupos: filho(a), menor sob guarda, pai ou mãe, sogro(a), cônjuge, ex-cônjuge, irmão ou irmã, designado (indivíduo que não tem parentesco com o participante), companheiro(a), ex-companheiro(a) e enteado(a). A terceira tabela se refere ao histórico de contribuições dos participantes e contém dados de identificador dos participantes, data vigência da contribuição, percentual da contribuição básica e percentual da contribuição adicional (opcional). A contribuição básica considerada no estudo foi superior a zero (já que os indivíduos que pararam de contribuir não são relevantes para este estudo) e inferior a 8% (que é o máximo permitido pelo Regulamento do Plano de Contribuição Variável). E a quarta tabela se refere ao histórico de perfil dos participantes, contendo os dados de identificador dos participantes, data de vigência do perfil, tipo de perfil (Renda Fixa ou Renda Variável) e alocação (o máximo permitido pelo Regulamento do Plano de Contribuição Variável é de 60% em Renda Variável). Para este estudo, foi utilizado apenas o perfil mais recente, atualizado em novembro de 2020.

Logo, após tratamento dos dados, foi feita uma análise prévia para avaliar as características dos 25% dos participantes que mais têm alocação em Renda Variável, sendo essa entre 30% e 60% em Renda Variável. E observou-se que dos 6042 participantes, 1774 estão nesse grupo. Desses, a maioria apresenta escolaridade "Superior Completo", assim como no grupo total dos participantes, sendo um pouco menor, e a proporção de 2º Grau Completo é um pouco maior nesse grupo. Além disso, observa-se que proporcionalmente existem mais homens do que mulheres nesse grupo. E em relação a faixa salarial, há mais participantes na faixa L2 e menos na L3, em relação ao grupo total, o que não era esperado. Ainda, em relação aos dependentes, observou-se que a proporção de filho(a) é menor nesse grupo e a proporção de pai ou mãe é maior. E em relação a contribuição, tem-se uma média, desvio-padrão e moda inferiores ao grupo total, com um máximo de contribuição de 20% do salário.

Após essa análise, foi realizada também uma análise dos 25% dos participantes com as maiores alocação em Renda Fixa, sendo essas de 100% em Renda Fixa. Observou-se que esses representam 2305 dos participantes. Proporcionalmente, esses tem nível de escolaridade Superior Completo maior do que no grupo total e 2º Grau Completo pouco menor. E também, há mais mulheres nesse grupo do que homens, em relação ao grupo total. E em relação a faixa salarial, há mais participantes na faixa L2 e menos na L3, em relação ao grupo total. Em relação aos dependentes e as contribuições, as distribuições são bem semelhantes as do grupo total. 

Em seguida, foi realizada a clusterização, utilizando o algoritmo k-means. Para isso, foi usada a tabela principal "grupo", transformando as colunas não numéricas em colunas dummy para que fosse possível utilizar o algoritmo. Pensava-se que o número ideal de clusters seria 3, já que foram observadas diferenças no grupo total dos participantes entre os participantes que mais tinham Renda Variável e os que mais tinham Renda Fixa, restando um grupo intermediário. Porém, a partir do método de cotovelo, observou-se que o ideal seriam 4 clusters.

### 3. Resultados

Utilizando os dados dos participantes da Fundação TELOS, com suas características de idade, sexo, escolaridade, nível salarial, dependentes e contribuições, foi possível classificá-los em grupos de diferentes alocações em fundos de investimento. Observou-se, por exemplo, que participantes homens com faixa salarial média e 2º grau completo tendem a ter maior alocação em Renda Variável.

### 4. Conclusões

Este trabalho teve por objetivo analisar os participantes da TELOS - Fundação Embratel de Suguridade Social, para identificar se os mesmos possuem perfis de investimentos que poderiam ser agrupados a partir de suas características individuais. Para isso, observou-se a base de dados da Fundação, que contém dados como idade, sexo, escolaridade, faixa salarial e dependentes, assim como quais as alocações dos participantes nos fundos de investimentos oferecidos pela Fundação, além de quanto dos seus salários é reservado para este fim e o histórico de suas alocações. A partir desses dados, pôde-se ver que grande parte desses participantes, apesar de apresentarem diferentes características, acabam escolhendo alocações bem semelhantes, sendo a maioria em fundos de investimento de Renda Fixa. E ainda, enquanto esperava-se que participantes com maiores escolaridades e faixa salarial tivessem maiores alocações em Renda Variável, já que esses têm maiores conhecimentos e base para realizar suas alocações, viu-se que não é isso que ocorre. O que significa que é possível que participantes com pouca instrução estejam arriscando seus investimentos mais do que deveriam e que a Fundação poderia disponibilizar mais informações a respeito ou passar a indicar perfis mais seguros para participantes com menores salários e escolaridade.

---

Matrícula: 192.190.114

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
