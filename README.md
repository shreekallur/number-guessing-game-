# number-guessing-game
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
    int number, guess;
    int attempts;
    char playAgain;

    // Initialize random number generator
    srand(time(0));

    cout << "================================\n";
    cout << "     NUMBER GUESSING GAME\n";
    cout << "================================\n";

    do
    {
        // Generate random number between 1 and 100
        number = rand() % 100 + 1;

        attempts = 0;

        cout << "\nGuess a number between 1 and 100\n";

        // Guessing process
        do
        {
            cout << "\nEnter your guess: ";
            cin >> guess;

            if (guess < 1 || guess > 100)
            {
                cout << "Enter a number between 1 and 100!\n";
                continue;
            }

            attempts++;

            if (guess > number)
            {
                cout << "Too High! Try again.\n";
            }
            else if (guess < number)
            {
                cout << "Too Low! Try again.\n";
            }
            else
            {
                cout << "\nCongratulations! You won!\n";
                cout << "Correct Number: " << number << endl;
                cout << "Total Attempts: " << attempts << endl;

                int score = 100 - (attempts - 1) * 10;

                if (score < 0)
                    score = 0;

                cout << "Your Final Score: "
                     << score << "/100\n";
            }

        } while (guess != number);

        cout << "\nDo you want to play again? (Y/N): ";
        cin >> playAgain;

    } while (playAgain == 'Y' || playAgain == 'y');

    cout << "\nThank you for playing!\n";

    return 0;
}