# DSLIST - Catálogo de Games

DSList é um projeto backend desenvolvido durante um curso, com o objetivo de disponibilizar uma API REST para gerenciamento de listas de jogos. O sistema permite organizar games por categorias (listas), consultar informações detalhadas e alterar a ordem de cada jogo dentro de sua lista.

---

## 🕹️ Sobre o Projeto

O objetivo da aplicação é fornecer um catálogo de games associado a diferentes listas, como "Aventura", "RPG", "Ação", entre outras. Cada jogo conta com suas próprias características e pode pertencer a várias listas.

A API disponibiliza endpoints para:

* Listar todos os games
* Buscar game por ID
* Listar jogos de uma lista específica (ex: Aventura)
* Listar todas as listas cadastradas
* Alterar a posição dos jogos dentro de uma lista (feature de reorder)

---

## 🧩 Modelo de Domínio

A modelagem principal do projeto contém:

### **Game**

Representa um jogo individual.

**Propriedades:**

* `id` (Long)
* `title` (String)
* `year` (Integer)
* `genre` (String)
* `platforms` (String)
* `score` (Double)
* `imgUrl` (String)
* `shortDescription` (String)
* `longDescription` (String)

---

### **GameList**

Representa uma lista/categoria de jogos.

**Propriedades:**

* `id` (Long)
* `name` (String)

---

### **Belonging**

Entidade de associação (tabela intermediária), definindo a posição de cada jogo dentro de uma lista.

**Propriedades:**

* `position` (Integer)

---

## 🛠️ Tecnologias Utilizadas

* **Java 17+**
* **Spring Boot**
* **Spring Web** (APIs REST)
* **Spring Data JPA**
* **Banco H2** (ambiente de teste)
* **Banco PostgreSQL** (opcional)
* **Maven**
* **JPA/Hibernate** para ORM

---

## 🚀 Como Rodar o Projeto

### **1. Pré‑requisitos**

* Java 17+ instalado
* Maven instalado

### **2. Clonar o repositório**

```bash
git clone <URL_DO_REPO>
cd dslist
```

### **3. Rodar com Maven**

```bash
mvn spring-boot:run
```

### **4. Acessar a API**

Aplicação inicia por padrão em:

```
http://localhost:8080
```

### **5. Exemplos de Endpoints**

* `GET /games` — lista todos os games
* `GET /games/{id}` — busca game por ID
* `GET /lists` — lista todas as listas de games
* `GET /lists/{id}/games` — lista os games de uma lista
* `POST /lists/{listId}/games` — troca posição de jogos em uma lista

---

## 🧱 Arquitetura

O projeto segue uma arquitetura em camadas:

### **1. Controller**

Recebe as requisições HTTP e delega para o service.

### **2. Service**

Contém as regras de negócio, como a troca de posições dos jogos.

### **3. Repository**

Acesso ao banco via Spring Data JPA.

### **4. Entities e DTOs**

* **Entities** representam as tabelas.
* **DTOs** são usados para transferir dados de maneira mais enxuta.

### **5. Database**

* Scripts SQL para popular base (teste)
* H2 para ambiente local simples

---

## 📦 Estrutura de Pastas (Resumo)

```
src/
 └── main/
      ├── java/com/dslist/
      │      ├── controllers/
      │      ├── services/
      │      ├── repositories/
      │      ├── dto/
      │      ├── entities/
      │      └── config/
      └── resources/
             ├── application.properties
             └── import.sql
```

---

## 📝 Conclusão

Este projeto é uma excelente base para aprender:

* CRUD com Spring Boot
* Relacionamentos N:N com entidade associativa
* Organização de listas e ordenação customizada
* Uso de DTOs e boas práticas de API REST

Sinta-se livre pra expandir, criar novas funcionalidades ou integrar com front-end! 🎮🔥
