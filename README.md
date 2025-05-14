# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href= "https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Admnistração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Atividade em Grupo - Sprint 1 - Challenge

## Sistema de Prevenção de Falhas em Linhas de Produção Industrial


## 👨‍🎓 Informações do Grupo:
|Nome Completo|RM|
|---|---|
|[LEONARDO DE SENA](https://www.linkedin.com/in/leonardosena)|RM563351|
|[VIVIAN NASCIMENTO SILVA AMORIM](https://www.linkedin.com/in/vivian-amorim-245a46b7)|RM565078|
|[CAIO PELLEGRINI](https://www.linkedin.com/in/caiopellegrini/)|566575|

## 👩‍🏫 Professores:
### Tutor(a)
- [Leonardo Ruiz Orabona](https://www.linkedin.com/in/leonardoorabona)
### Coordenador(a)
- [André Godoi Chiovato](https://www.linkedin.com/in/andregodoichiovato)

## 📜 Descrição

### Problema
Indústrias de manufatura enfrentam **interrupções inesperadas em
linhas de produção** ocasionadas por falhas em equipamentos. Esses imprevistos
geram custos elevados, atrasos e redução de produtividade.

### Setor de Atuação
O projeto é voltado para o **setor industrial de
manufatura**, com foco na **gestão e prevenção de falhas em linhas de
produção**.

### Solução Proposta
A solução é um **sistema de monitoramento preditivo** que
utiliza **sensores IoT**, **processamento em nuvem** e **algoritmos de machine
learning** para identificar sinais de falhas antecipadamente. A arquitetura
integra serviços da AWS para transformar dados brutos em informações
estratégicas, permitindo decisões proativas, redução de tempo de inatividade e
aumento da eficiência operacional.

## Visão Geral

A solução proposta aborda um problema crítico enfrentado por indústrias de manufatura: interrupções inesperadas em linhas de produção causadas por falhas em equipamentos. Essas falhas geram perdas financeiras e operacionais significativas, como custos de reparo, perda de produção, atrasos em entregas e penalidades contratuais.

Este projeto propõe um sistema de monitoramento preditivo que integra sensores IoT, processamento em nuvem e algoritmos de machine learning para detectar antecipadamente sinais de falhas. Ao invés de reações corretivas ou manutenções programadas por calendário, utiliza-se a manutenção preditiva baseada em dados reais dos equipamentos.

A proposta tem como objetivo transformar dados brutos em informações relevantes, permitindo que gestores industriais tomem decisões proativas, reduzindo o tempo de inatividade e estendendo a vida útil dos equipamentos.

## Requisitos Técnicos e Funcionais

### 1. Linguagens e Ferramentas Utilizadas

- Linguagens:
  - Python
  - SQL

- Bibliotecas e ferramentas:
  - Pandas, NumPy: tratamento e manipulação de dados
  - Scikit-learn, Amazon SageMaker: criação e treinamento de modelos preditivos
  - MQTT: comunicação entre o sensor ESP32 e o gateway
  - Integração com serviços AWS: Lambda, API Gateway, RDS, DynamoDB, S3

### 2. Definição de um Pipeline de Dados

- Coleta de dados:
  Os dados são coletados por sensores IoT (ESP32), que capturam informações como temperatura e vibração. A comunicação ocorre via MQTT, passando por um Gateway IoT até o AWS IoT Core.

- Transmissão e processamento:
  O AWS IoT Core recebe os dados e os encaminha no formato JSON para o AWS Kinesis. O serviço AWS Lambda trata os dados e os direciona para os bancos de dados conforme a finalidade.

- Armazenamento:
  Os dados são distribuídos em três camadas:
  - Dados históricos: armazenados no Amazon RDS/PostgreSQL;
  - Dados em tempo real: armazenados no Amazon DynamoDB;
  - Dados brutos: armazenados no Amazon S3;

### 3. Justificativa do Uso de Banco de Dados

A opção por bancos de dados em nuvem (AWS) se baseia na facilidade de integração, escalabilidade e eficiência no acesso aos dados:

- Amazon RDS/PostgreSQL: armazenamento de dados históricos com suporte SQL e integração com ferramentas de BI;
- Amazon DynamoDB: banco NoSQL para armazenamento de dados em tempo real com alta performance;
- Amazon S3: armazenamento econômico e escalável para grandes volumes de dados brutos;
- Amazon SageMaker: plataforma para criação e gerenciamento de modelos de machine learning com integração aos demais serviços AWS.

### 4. Potencial Uso de Serviços em Nuvem

Mesmo com partes simuladas, os seguintes serviços da AWS estão previstos na arquitetura:

- AWS IoT Core: integração com sensores IoT (ESP32)
- AWS Kinesis: ingestão de dados em tempo real
- AWS Lambda: processamento dos dados
- Amazon RDS (PostgreSQL): armazenamento relacional
- Amazon DynamoDB: armazenamento NoSQL para dados em tempo real
- Amazon S3: armazenamento de dados brutos
- Amazon SageMaker: criação e implantação de modelos preditivos
- Amazon API Gateway: exposição dos dados via API REST
- Interface web responsiva: visualização dos dados processados

### 5. Integração Futura com Modelos de Inteligência Artificial

- O Amazon SageMaker será utilizado para criação de modelos preditivos baseados nos dados coletados.
- Os modelos utilizarão dados armazenados no RDS, DynamoDB e S3, gerando predições em tempo real.
- As predições serão processadas via AWS Lambda e disponibilizadas por meio do API Gateway em uma interface web.

Essa integração permitirá, no futuro, a automação de decisões e alertas em tempo real para operadores e gestores.

### 6. Organização da Documentação e Planejamento

A documentação do projeto será estruturada em etapas:

1. Aquisição e transmissão dos dados (ESP32, MQTT, IoT Core)
2. Pipeline de ingestão e tratamento (Kinesis + Lambda)
3. Armazenamento segmentado (RDS, DynamoDB, S3)
4. Desenvolvimento do modelo preditivo (SageMaker)
5. Visualização dos resultados (API Gateway e interface web)

Todo o conteúdo técnico será versionado no GitHub, incluindo códigos, diagramas e justificativas. O projeto será conduzido em fases, com ajustes contínuos conforme o avanço do desenvolvimento.

### 7. Diagrama de Arquitetura (versão simplificada)

```
Coleta de Dados
└── ESP32 (Sensor IoT)
    └── Protocolo MQTT
        └── Gateway IoT
            └── AWS IoT Core
                └── Formato de dados: JSON

Processamento de Dados
└── AWS Kinesis (Stream de dados)
    └── AWS Lambda
        ├── Armazena dados históricos em Amazon RDS (PostgreSQL)
        ├── Armazena dados em tempo real em Amazon DynamoDB
        └── Armazena dados brutos em Amazon S3

Modelos de Machine Learning
└── Amazon SageMaker
    ├── Treinamento de modelos com base nos dados armazenados
    └── Envia predições ao AWS Lambda

Apresentação dos Dados
└── Amazon API Gateway (REST API)
    └── Interface Web Responsiva
```

### Divisão de Grupo – Sprint 1

**Objetivo da Sprint:** Entregar a estrutura inicial do projeto, com definição da arquitetura, ferramentas utilizadas, simulação do pipeline e documentação técnica no GitHub.

---

**Vivian Amorim – Responsável por e Documentação Técnica**

**Tarefas:**
- Redigir o README.md com base nas decisões do grupo.

- Organizar o repositório no GitHub.
- Criar o cronograma simplificado das próximas sprints.
- Documentar como os dados são gerados e trafegam via MQTT.
- Esboçar os dados em formato JSON simulando um envio ao AWS IoT Core.


**Entregas esperadas:**
- README completo no repositório
- Estrutura do projeto no GitHub
- Revisão da documentação do pipeline de dados 

---

**Leonardo Sena – Responsável por Arquitetura da Pipeline e Simulação de Coleta de Dados**

**Tarefas:**
- Explicar os serviços da AWS e justificar o uso de cada ferramenta.
- Produzir o diagrama de arquitetura.
- Simular a coleta de dados usando ESP32.

**Entregas esperadas:**
- Ambiente de simulação configurado
- Diagrama de arquitetura atualizado
- Revisão da documentação do pipeline de dados 

---

**Caio Pellegrini – Responsável por Pesquisa e Integração com IA**

**Tarefas:**
- Levantar os requisitos básicos do Amazon SageMaker.
- Explicar como será a integração futura com os modelos de IA.
- Redigir a seção de “Integração com IA” no README e na documentação interna.

**Entregas esperadas:**
- Documento explicativo da integração com IA
- Justificativa técnica da abordagem de machine learning

---

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/RevoluxAI/fase3-cap1">FASE 3 - CAP 1</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>
