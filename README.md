# jutub
package com.example.myapplication;

import java.util.Scanner;

public class MainActivity {
    public static void main(String[] args) {
        String secretWord = "programowanie";
        int maxAttempts = 6;

        char[] guessedLetters = new char[secretWord.length()];
        int attempts = 0;

        Scanner scanner = new Scanner(System.in);
        while (attempts < maxAttempts) {
            displayWord(secretWord, guessedLetters);

            System.out.print("Podaj literę ");
            char guess = scanner.next().charAt(0);

            if(secretWord.contains(String.valueOf(guess))) {
                System.out.println("Dobrze Litera jest w słowie.");
                updateGuessedLetters(secretWord, guessedLetters, guess);
                else {
                    System.out.println("Nieprawidłowa litera.");
                    attempts++;
                }
                if(isWordGuessed(guessedLetters)) {
                    displayWord(secretWord, guessedLetters);
                    System.out.println("Gratulacje! Odgadłeś słowo.");
                    break;
                }
            }
            if(attempts >= maxAttempts) {
                System.out.println("Przegrałeś. Słowo to: " + secretWord);
            }
        }
        public static void displayWord(String secretWord, char[] guessedLetters) {
            StringBuilder display = new StringBuilder();
            for (char letter : secretWord.toCharArray()) {
                if(containsLetter(guessedLetters, letter)) {
                    display.append("_");
                } else {
                    display.append(" ");
                }
                System.out.println(display.toString());
            }

        }
        public static void updateGuessedLetters(String secretWord, char[] guessedLetters, char guess) {
            for (int i = 0; i < secretWord.length(); i++) {
                if(secretWord.charAt(i) == guess) {
                    guessedLetters[i] = guess;
                }
            }
        }
    }
}
