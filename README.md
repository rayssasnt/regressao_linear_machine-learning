# Regressão Linear

📍 Projeto é de uso pessoal e educacional , desenvolvido através do Curso: `Data Science: testando relações com Regressão Linear` da @Alura. 

Este notebook tem como objetivo prever o preço de casas com base em diversas características. O objetivo é explorar a relação entre as variáveis de uma propriedade e seu preço de venda, construindo e comparando diferentes modelos de regressão.

## Conjunto de Dados

O conjunto de dados usado foi :  `Preços_de_casas.csv` 
que esta disponível nesse repositório

Um segundo conjunto de dados, `Novas_casas.csv`, é utilizado para testar a previsão do modelo com novas propriedades.

## Metodologia

### 1. Carregamento e Exploração Inicial dos Dados
- A coluna `Id` é removida, pois não é uma variável explicativa.

### 2. Análise Exploratória de Dados (EDA)
- **Correlação**: Uma matriz de correlação é gerada para visualizar a relação entre as variáveis, com foco no `preco_de_venda`.
- 
- **Visualizações**: Gráficos de dispersão são usados para analisar a relação entre a `area_primeiro_andar` e o `preco_de_venda`.
- **Pairplot**: é utilizado para visualizar relações entre as variáveis e identificar possíveis padrões.

### 3. Treinamento e Avaliação do Modelo de Regressão Linear Simples
- O conjunto de dados é dividido em treino e teste (`train_test_split`).
- Um modelo de regressão linear simples (`statsmodels.formula.api.ols`) é treinado usando apenas a `area_primeiro_andar` como variável explicativa.
- O sumário do modelo é analisado para verificar o R², coeficientes e p-valores.
- Os resíduos do modelo são plotados para verificar a distribuição.
- O R² é calculado para o conjunto de teste.

### 4. Treinamento e Avaliação de Modelos de Regressão Linear Múltipla
- **Modelo 2 (Todas as variáveis explicativas)**: Um segundo modelo é treinado usando todas as variáveis restantes como explicativas.
- **Modelo 3 (Sem área do segundo andar)**: Um terceiro modelo é treinado excluindo a `area_segundo_andar`.
- **Modelo 4 (Sem informação sobre garagem)**: Um quarto modelo é treinado excluindo `capacidade_carros_garagem`.
- Os sumários de cada modelo são analisados para comparar o R² ajustado, coeficientes e significância estatística das variáveis.

### 5. Comparação de Modelos
- Os valores de R² de todos os modelos são comparados para entender qual combinação de variáveis oferece a melhor explicabilidade.

### 6. Investigação de Multicolinearidade
- O Fator de Inflação da Variância (VIF) é calculado para identificar multicolinearidade entre as variáveis explicativas nos diferentes modelos (`vif_1`, `vif_4`).

### 7. Análise dos Resíduos
- Os resíduos do `model_4` são plotados contra os valores previstos para verificar a homogeneidade da variância e a distribuição dos erros.

## Resultados Chave

- **Modelo 1 (Simples)**: R² de aproximadamente 0.38. A área do primeiro andar explica cerca de 38% da variação nos preços.
- **Modelo 2 (Todas as variáveis)**: R² de aproximadamente 0.74. Um aumento significativo na explicabilidade com a inclusão de mais variáveis.
- **Modelo 3 (Sem área do segundo andar)**: R² de aproximadamente 0.71. A remoção de `area_segundo_andar` resultou em uma pequena queda no R², mas o VIF pode ser melhor.
- **Modelo 4 (Sem capacidade de garagem)**: R² de aproximadamente 0.65. Uma queda no R² comparado ao Modelo 2, mas com um melhor VIF.

O modelo com todas as variáveis (`model_2`) apresentou o maior R², mas `model_4` foi considerado para a análise de resíduos devido a possíveis questões de *multicolinearidade* no `model_2` (alto VIF para `existe_segundo_andar` e `area_segundo_andar`).

## Tecnologias Utilizadas 🔨

- Pandas
- numpy
- matplotlib.pyplot
- seaborn
- plotly.express
- scikit-learn
- statsmodels
- pickle

