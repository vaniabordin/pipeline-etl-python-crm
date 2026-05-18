C# Pipeline de ETL: Inteligência de Negócios e Engajamento de Clientes (CRM)

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-green.svg)](https://pandas.pydata.org/)
[![Etapa](https://img.shields.io/badge/Status-Conclu%C3%ADdo-brightgreen)](#)

## 🎯 Objetivo do Projeto
Este projeto foi desenvolvido como parte de um desafio prático de Ciência de Dados focado no fluxo **ETL (Extração, Transformação e Carregamento)**. O objetivo principal é simular um motor de CRM de uma plataforma de educação ou serviços, segmentando clientes com base em seus comportamentos de engajamento (`Score`) e gerando insights e recomendações personalizadas para as equipes de Marketing e Sucesso do Cliente.

> 🛠️ **Abordagem Estratégica:** Diante da indisponibilidade de uma API externa pública originalmente proposta, adotei uma **solução alternativa resiliente** (Arquitetura Local baseada em arquivos). Desenvolvi uma lógica de negócios customizada em Python que simula um motor de IA de segmentação, garantindo a entrega do valor analítico do projeto de forma independente.

---

## 🏗️ Arquitetura do Pipeline (ETL)

O projeto foi totalmente modularizado utilizando boas práticas de desenvolvimento, dividindo o pipeline em funções com responsabilidades únicas e logs de acompanhamento.
```text
       [ Base de Clientes ] (CSV)
                │
                ▼
      ┌──────────────────┐
      │  1. EXTRACT      │ ──> pd.read_csv()
      └──────────────────┘
                │
                ▼
      ┌──────────────────┐
      │  2. TRANSFORM    │ ──> Regras de Negócio & Insights de IA
      └──────────────────┘
                │
                ▼
      ┌──────────────────┐
      │  3. LOAD         │ ──> pd.to_csv() [Base Enriquecida]
      └──────────────────┘
```


### 1. Extração (`Extract`)
A ingestão dos dados consome uma base local em formato CSV (`clientes_desafio.csv`) que contém atributos fundamentais como `ID`, `Nome`, `Score` de engajamento, `Setor` de atuação e a data da `Última Compra`.

### 2. Transformação (`Transform`)
A etapa de inteligência do pipeline utiliza o `pandas` de forma avançada. Através da vetorização de dados e aplicação de funções de linha (`.apply()` com `pd.Series`), o script avalia o score de cada cliente e injeta duas novas variáveis estratégicas de forma simultânea:
*   **Status de Segmentação:** Classificação automatizada entre `Premium`, `Ativo` ou `Alerta de Churn`.
*   **Mensagem Personalizada:** Geração de um insight focado no setor do cliente para maximizar a conversão (Up-selling, Cross-selling ou Retenção).

### 3. Carregamento (`Load`)
Os dados limpos, transformados e enriquecidos são consolidados em um novo ativo de dados (`clientes_insights_finais.csv`), pronto para ser consumido por ferramentas de BI (como Power BI) ou sistemas automatizados de disparo de e-mails/CRM.

---

## 🛠️ Tecnologias e Ferramentas
*   **Linguagem:** Python 3
*   **Ambiente de Desenvolvimento:** Google Colab
*   **Biblioteca Principal:** Pandas (Manipulação de dados estruturados e Engenharia de Recursos)

---

## 📊 Estrutura dos Dados e Resultados

O pipeline processa a base e retorna uma estrutura de dados enriquecida semelhante a esta:

| ID | Nome | Score | Setor | Status | Mensagem_IA |
| :---: | :--- | :---: | :--- | :--- | :--- |
| **1** | Vânia Bordin | 95 | Data Science | Premium | Parabéns Vânia Bordin! Como especialista em Data Science, você tem acesso a mentorias VIP. |
| **4** | Roberto Junior | 20 | Marketing | Alerta de Churn | Sentimos sua falta, Roberto Junior. Preparamos um cupom especial para retomar seus estudos em Marketing. |

---

## 🚀 Como Executar o Projeto

1. Clone este repositório:
   ```bash   
   git clone [https://github.com/vaniabordin/pipeline-etl-python-crm](https://github.com/vaniabordin/pipeline-etl-python-crm)
