# Determinando a inibição da Cyclooxygenase com base na expressão genética e a aplicação de Machine Learning

<img src="https://github.com/saarlander/imersao-dados-desafio-final/blob/main/Images/DNA.JPG" width = "477" height = "226">

## Introdução

A busca de novas drogas para o combate de doenças tem cada vez mais aplicado técnicas sofisticadas com esse intuito. Enquanto no passado essa busca se dava, muitas vezes, com base em tentativa e erro usando substâncias encontradas na natureza, hoje a biotecnologia aprimora esse campo através da possibilidade de testes de diversos compostos diferentes, sejam naturais ou sintéticos, em células em laboratório. Os resultados de tais experimentos embasam as etapas subsequentes, tais como testes em animais e em humanos.

O objetivo do presente estudo é mostrar a aplicação de Machine Learning à avaliação da expressão gênica de centenas de genes, resultantes de testes em laboratório, e obter um veredicto se um determinado experimento envolvendo um determinado composto, dose e tempo de atuação é capaz de produzir um determinado método de ativação.

O resultado do estudo foi a demonstração da viabilidade da técnica proposta, atingindo uma precisão de 98,175% na predição do método de ativação observado.

## Método

O método aplicado resume-se às seguintes etapas básicas:

- **Importação da base de dados**
- **Verificação do formato da base de dados**
- **Organização da base de dados**
- **Determinação do algoritmo de Machine Learning a ser aplicado**
- **Aplicação do algoritmo de Machine Learning e refinamento**
- **Análise dos resultados**

## Base de dados

A base de dados constitui-se de duas tabelas com dados de experimentos biológicos e com dados dos resultados dos mecanismos de ativação obtidos.
Os experimentos tratam-se da aplicação de diferentes compostos, com diferentes dosagens e tempos de ação, em culturas de células. As culturas são então analisadas e determinam-se suas expressões gênicas.

### O que é expressão gênica?
Os diversos genes contidos no núcleo das células dos seres vivos possuem a codificação que instrui como uma determinada proteína deve ser produzida. Quando uma célula precisa produzir uma determinada proteína, o código contido no gene correspondente é copiado (processo chamado de transcrição), e esse código copiado é levado até o ribossomo através do RNAm, onde o ribossomo sintetiza a proteína requerida.
Quando a célula precisa aumentar a produção de uma determinada proteína, o gene correspondente é estimulado, ou é inibido em caso contrário. Os medicamentos também lançam mão desse processo: se um medicamento tem a intenção de fazer o corpo produzir mais insulina, por exemplo, esse medicamento pode estimular os genes correspondentes a essa enzima (enzimas são normalmente de origem proteica) para obter o aumento desejado. Neste caso, dizemos que esses genes tiveram sua expressão aumentada.

A primeira tabela traz os resultados das variações das expressões gênicas para cada experimento. Uma segunda tabela indica os resultados dos mecanismos de ativação para cada um desses experimentos. O mecanismo de ativação pode ter sido a inibição da produção de uma determinada proteína, por exemplo.

Dessa maneira, temos como entrada as condições do experimento: qual composto foi utilizado, com qual dosagem e por quanto tempo. Um resultado intermediário é a expressão gênica, que indica como esta variou para cada experimento, e for fim temos o mecanismo de atuação de cada experimento.

## Motivação

Na tabela com os resultados dos mecanismos de ativação, esses resultados foram verificados manualmente. Através da aplicação de Machine Learning, pode ser possível determinar o mecanismo de ativação dada a expressão gênica do experimento, possibilitando uma maior velocidade na análise dos dados dos experimentos e, consequentemente, uma maior rapidez na obtenção de novos medicamentos.

## Mecanismo de ativação escolhido para análise: cyclooxygenase_inhibitor

A tabela com os mecanismos de ativação possui 206 colunas com diferentes mecanismos (mais uma coluna com identificação do experimento). O objetivo aqui é relacionar um desses métodos de ativação com as expressões gênicas. O mecanismo escolhido para esse estudo foi o "cyclooxygenase_inhibitor" porque:
- Possui uma frequência alta de ocorrência (435 ocorrências nos 23814 experimentos, sendo o terceiro mecanismo com maior ocorrência, e
- Possui grande relevância farmacêutica, pois a inibição da cyclooxygenase (COX) pode causar o alívio dos sintomas de inflamação e de dor.

**Drogas anti-inflamatórias não-esteróides, tais como aspirina e ibuprofeno, agem através da inibição da COX.**

## Algoritmo de Machine Learning escolhido

Seguindo as instruções na página "Choosing the right estimator", o algoritmo "Linear SVC" pode ser o melhor para o estudo, porque:
- Há mais de 50 amostras
- O objetivo é prever uma categoria (inibe ou não a COX)
- Temos dados etiquetados (com resultados)
- A quantidade de amostras é inferior a 100k (são 23814).

<img src="https://scikit-learn.org/stable/_static/ml_map.png">

# Resultado

O modelo, após ajustes em seus parâmetros, atingiu 98,175% de score quando testado com uma porcentagem de 20% dos dados da base.
Acreditamos que esse valor seja encorajador para novas pesquisas e aplicação da técnica no desenvolvimento de novas drogas.

## Sugestões para novas pesquisas

O presente estudo avaliou apenas um mecanismo de ação. Um estudo mais aprofundado poderia configurar uma Machine Learning para cada mecanismo de ação, e poderia-se verificar o comportamento do score global.



### Fontes:
- https://en.wikipedia.org/wiki/Cyclooxygenase
- https://en.wikipedia.org/wiki/Gene_expression
- https://docs.google.com/document/d/10EhrQBChlyYIcff3to7PrCQi5HcNk2r-zd2ZCKPtcz8/edit
- https://pixabay.com/illustrations/dna-biology-science-dna-helix-163710/
- https://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html
- https://scikit-learn.org/stable/tutorial/machine_learning_map/index.html
- Introduction to machine learning with Python
