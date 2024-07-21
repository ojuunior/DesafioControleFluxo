# Desafio Controle de Fluxo

Este é um projeto Java desenvolvido como parte do desafio do curso "DIO - Trilha Java Básico". O desafio envolve a criação de um sistema que recebe dois números inteiros como entrada e realiza uma contagem baseada na diferença entre esses números, imprimindo cada incremento no console. Se o primeiro número for maior que o segundo, uma exceção personalizada é lançada.

## Informações do Curso

- **Plataforma**: [Digital Innovation One](https://www.dio.me)
- **Bootcamp**: Java com a Claro
- **Módulo**: Controle de Fluxo
- **Instrutor**: Gleyson Sampaio

## Descrição do Desafio

O sistema deve:
1. Receber dois parâmetros via terminal que representarão dois números inteiros.
2. Obter a quantidade de interações (for) com base na diferença entre esses números e realizar a impressão dos números incrementados no console.
3. Lançar uma exceção personalizada chamada `ParametrosInvalidosException` se o primeiro parâmetro for maior que o segundo, com a mensagem: "O segundo parâmetro deve ser maior que o primeiro".

## Estrutura do Projeto

O projeto consiste em duas classes principais:

1. **ParametrosInvalidosException**: Classe personalizada de exceção.
2. **Contador**: Classe principal que contém a lógica de leitura de parâmetros e contagem.

## Pré-requisitos

- [JDK (Java Development Kit)](https://www.oracle.com/java/technologies/javase-downloads.html) 8 ou superior.
- [Git](https://git-scm.com/) para clonar o repositório (opcional).

## Como Executar

1. Clone o repositório (opcional):

    ```bash
    git clone https://github.com/seu-usuario/desafio-controle-fluxo.git
    cd desafio-controle-fluxo
    ```

2. Compile o arquivo Java:

    ```bash
    javac Contador.java
    ```

3. Execute o programa:

    ```bash
    java Contador
    ```

4. Siga as instruções no console para inserir os parâmetros.

## Código Completo

```java
import java.util.Scanner;

// Classe personalizada de exceção
class ParametrosInvalidosException extends Exception {
    public ParametrosInvalidosException(String message) {
        super(message);
    }
}

public class Contador {
    public static void main(String[] args) {
        Scanner terminal = new Scanner(System.in);
        
        System.out.println("Digite o primeiro parâmetro");
        int parametroUm = terminal.nextInt(); // Leitura do primeiro parâmetro
        
        System.out.println("Digite o segundo parâmetro");
        int parametroDois = terminal.nextInt(); // Leitura do segundo parâmetro
        
        try {
            // Chamando o método contendo a lógica de contagem
            contar(parametroUm, parametroDois);
        } catch (ParametrosInvalidosException exception) {
            // Imprimir a mensagem: O segundo parâmetro deve ser maior que o primeiro
            System.out.println("O segundo parâmetro deve ser maior que o primeiro");
        }
        
        terminal.close();
    }

    static void contar(int parametroUm, int parametroDois) throws ParametrosInvalidosException {
        // Validar se parametroUm é MAIOR que parametroDois e lançar a exceção
        if (parametroUm >= parametroDois) {
            throw new ParametrosInvalidosException("O segundo parâmetro deve ser maior que o primeiro");
        }
        
        int contagem = parametroDois - parametroUm;
        
        // Realizar o for para imprimir os números com base na variável contagem
        for (int i = 1; i <= contagem; i++) {
            System.out.println("Imprimindo número " + i);
        }
    }
}
