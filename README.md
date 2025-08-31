# CP4 - IoT e Mineração de Dados

## 📌 Descrição

Este repositório contém as atividades desenvolvidas no **Checkpoint 4**
da disciplina, abordando análise de consumo energético doméstico
utilizando **Python (Parte 3)** e **Orange Data Mining (Parte 4)**.

------------------------------------------------------------------------

## 📂 Estrutura do Projeto

-   `cp4.py` → Código em Python que realiza análise exploratória,
    regressão, clustering e classificação usando o dataset
    `energydata_complete.csv`.
-   `README.md` → Este documento, com instruções de entrega, respostas
    às questões e informações detalhadas dos datasets.
-   `hist_appliances.png`, `serie_appliances_diaria.png`,
    `pca_scatter.png` → Gráficos gerados na Parte 3.

------------------------------------------------------------------------

## 📊 Parte 3 --- Appliances Energy Prediction (Python)

### Dataset utilizado

-   Arquivo: `energydata_complete.csv`
-   Linhas: **19.735**
-   Colunas: **29**
-   Período: registros de 2016 (consumo de eletrodomésticos e variáveis
    ambientais).

### Resultados principais

**26)** O dataset possui 19.735 registros e 29 variáveis (1 datetime, 2
inteiras, 26 numéricas).\
**27)** O consumo de `Appliances` é concentrado em valores baixos (\~60
Wh mediana), com cauda longa de picos.\
**28)** Maiores correlações: `T2` (0,12), `T6` (0,118), `T_out` (0,099).
Negativa mais forte: `RH_out` (-0,152).\
**29)** Normalização Min-Max aplicada às variáveis numéricas.\
**30)** PCA: PC1 = 44,3%, PC2 = 25,6% (≈70% da variância explicada). Não
há clusters naturais visíveis.\
**31)** Regressão Linear: RMSE ≈ 86,5 \| MAE ≈ 51,1 \| R² ≈ 0,097 →
desempenho fraco.\
**32)** Random Forest: RMSE ≈ 231,5 \| MAE ≈ 210,3 \| R² ≈ -5,466 → pior
que linear (sem features temporais).\
**33)** K-Means (k=3): perfis de baixo, médio e alto consumo
relacionados a `T_out` e `RH_out`.\
**34/35)** Classificação binária: logistic regression e random forest
tiveram dificuldade em prever altos consumos (classe minoritária).

------------------------------------------------------------------------

## 📊 Parte 4 --- Household Power Consumption (Orange Data Mining)

### Dataset utilizado

-   Arquivo: `household_power_consumption.txt`
-   Linhas: **2.075.259**
-   Colunas: **9** (`Date`, `Time`, `Global_active_power`,
    `Global_reactive_power`, `Voltage`, `Global_intensity`,
    `Sub_metering_1`, `Sub_metering_2`, `Sub_metering_3`)
-   Período: **2006 a 2010**.

### Resultados principais

**36)** O dataset possui **2.075.259 registros** e **9 variáveis**.\
**37)** A amostra de 1% (20.753 registros) apresenta distribuição
semelhante à base completa para `Global_active_power`.\
**38)** O consumo (`Global_active_power`) está concentrado em valores
baixos, com cauda longa para consumos altos.\
**39)** Scatter Plot mostra correlação **negativa** entre `Voltage` e
`Global_intensity` (quanto menor a tensão, maior a corrente).\
**40)** K-Means (k=3) com `Sub_metering_1`, `2`, `3`: clusters
representam perfis distintos de consumo --- cozinha, aquecimento de
água, e outros eletrodomésticos.

------------------------------------------------------------------------

## 🚀 Instruções de execução

### Parte 3 (Python)

1.  Instalar dependências:

    ``` bash
    pip install pandas matplotlib scikit-learn
    ```

2.  Executar o código:

    ``` bash
    python cp4.py
    ```

3.  Resultados: métricas impressas no terminal + gráficos salvos como
    `.png`.

### Parte 4 (Orange)

[⬇️ Download workflow Orange (cp4-iot-pt4.ows)](https://github.com/raphatatto/cp4-iot/raw/main/cp4-iot-pt4.ows)

------------------------------------------------------------------------

## ✅ Conclusão

-   **Parte 3** mostrou que os modelos simples não explicam bem o
    consumo apenas com variáveis ambientais → seria necessário adicionar
    variáveis temporais (hora do dia, lags, médias móveis).\
-   **Parte 4** revelou, via Orange, padrões claros de consumo
    doméstico, incluindo clusters distintos de uso de energia em
    diferentes contextos (cozinha, aquecimento de água,
    eletrodomésticos).

------------------------------------------------------------------------

📅 **Entrega final**: inclui `cp4.py`, gráficos gerados e este
`README.md`.
