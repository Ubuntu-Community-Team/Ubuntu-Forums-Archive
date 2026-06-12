---
title: "Beginner C++ projects"
date: 2009-06-07
forum: Programming Talk
---

### Post by Mirge on 2009-06-07
I've been playing with C++, reading through some guides/tutorials and mostly reading and working through the examples & exercises in Accelerated C++ (loving the book so far, btw).

My only gripe is the examples they use so far (at least some of them)... involving computing median, average, etc of student grades. I mean, that's all fine and dandy, but it's boring and I'm losing interest... and am less inclined to actually TRY the examples & exercises.

So I went out looking for other "beginner c++ projects", so I'm not just reading a book and getting no actual experience... reading the book is fine, but if I don't actually build a program or 2 demonstrating what I just learned, I guarantee I'll forget everything 5 mins later after I close the book.

One site suggested making a double linked list... but not really what I had in mind. Another suggested a number guessing game... pretty simple, so I knocked that out (code posted below).

What I'm after is some more relatively easy beginner C++ projects that I can work on that'll give me just enough "hands on" experience so that I'll actually retain the knowledge I'm getting and give me a better understanding in general. Something that can be expanded upon would be great too!

So, I'm all ears... anybody have suggestions?

```

#include <iostream>
#include <cstdlib> // for srand() and rand()
#include <ctime> // for time(NULL) in srand()

using namespace std;

int main(int argc, char *argv[])
{
    int max_num = 50;
    int max_tries = 5;

    int random_number;
    int guess = 0;
    int current_tries = 0;

    int low_guess = 1;
    int high_guess = max_num;

    srand(time(NULL));
    random_number = rand() % max_num + 1;

    while(current_tries < max_tries) {
        cout << "Enter a number from 1 to " << max_num << " (" <<  max_tries-current_tries << " tries left - between "
        << low_guess << " and " << high_guess << "): ";
        cin >> guess;

        if(guess == random_number) {
            cout << "Congratulations! You guessed correctly!" << endl;
            break;
        }

        if(guess > random_number) {
            cout << "Too HIGH!!" << endl;
            if(guess < high_guess || high_guess == max_num) {
                high_guess = guess;
            }
        }

        if(guess < random_number) {
            cout << "Too LOW!!" << endl;
            if(guess > low_guess || low_guess == 1) {
                low_guess = guess;
            }
        }

        current_tries++;
        if(current_tries >= max_tries) {
            cout << "Outta tries! Better luck next time. The number was " << random_number << endl;
            break;
        }
    }
    
    return 0;
}

```

---

### Post by Mirge on 2009-06-07
"If you simply want to get practice with various C++ "isms" (particularly how to use the STL) then you could try rewriting some of the simple unix commandline utilities using the STL."

There's something I may try...

---

### Post by Arppa on 2009-06-08
Coding games has been fun for me so I recommend making some kind of simple game. When learning a new programming language, I have usually done simple tic-tac-toe -game for my first project. It's quite easy to program, yet many improvisations can be made under the hood. I suggest you try making a simple two player tic-tac-toe: no AI needed, console program, keyboard input. And when you have finished the basic version of the game, you can start polishing it further. You can even code a simple AI to kick the player's *** all the way down to Siberia!
Good luck and keep coding!

---

### Post by dcraven on 2009-06-08
The Practice Rooms at TopCoder.com have some very good and challenging problems to solve. That's my favourite source for coding practice problems.

Cheers,
~djc

---

### Post by Mirge on 2009-06-08
Thanks guys!

I've seen tic-tac-toe mentioned a few times too, but I really don't know how I'd code that on the console... I'll hafta think on that one.

Checking out the other site now...

This is where I got a couple ideas:
[http://code.bluedinosaurs.com/beginner%20c++%20projects.html](http://code.bluedinosaurs.com/beginner%20c++%20projects.html)

---

### Post by unknownPoster on 2009-06-08
If you're into math, the problems over at Project Euler can be fun and challenging.

[http://www.projecteuler.net](http://www.projecteuler.net)

Here is the "easiest" problem there:

> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.
 Find the sum of all the multiples of 3 or 5 below 1000.


---

### Post by Mirge on 2009-06-08
Ok, I wrote a basic hangman style game. It works pretty well, surprisingly. Left room for expansion so I can make it better as I learn more, but it was a pretty fun learning experience!

```

#include <iostream>
#include <vector>
#include <map>
#include <cstdlib>
#include <ctime>
#include <string>
#include <locale>

/*    Design a hangman-type game on paper first.
    Then build it here. It can be a rough first attempt...
*/

using namespace std;

int GetRandomElement(int max);
string strtolower(string str);
string ShowLettersUsed(map<string, int> letters);
string RevealWord(string hidden_word, string word, string letter);

int main(int argc, char *argv[])
{
    int total_possible_guesses = 10;
    vector<string> possible_words;
    possible_words.push_back("Mike");
    possible_words.push_back("Aimy");
    possible_words.push_back("Computer");
    possible_words.push_back("Television");
    possible_words.push_back("Movie");
    possible_words.push_back("Book");
    possible_words.push_back("Wedding");
    
    string word = possible_words[GetRandomElement(possible_words.size())];
    word = strtolower(word);

    string hidden_word = string(word.length(), '-');

    map<string, int> letters_used; // Keep track of individual letters used.
    int guesses = 0; // Keep track of total guesses used.
    string letter; // Buffer for the letter entered in the loop.

    // Greeting / instructions.
    cout << "A word has been selected at random... it is " << word.length() << " characters long. " << endl
    << "You have " << total_possible_guesses << " incorrect guesses allowed. Good luck! " << endl;

    while(1) {
        cout << endl << hidden_word << endl;

        cout << "Guesses remaining: " << total_possible_guesses - guesses << endl;
        cout << "Letters used: " << ShowLettersUsed(letters_used) << endl;
        cout << "Enter a letter: ";
        cin >> letter;
        letter = strtolower(letter);

        if(letters_used[letter]) {
            cout << "Already used that letter!" << endl;
            continue;
        }

        letters_used[letter]++; // Letter was not already entered. Mark it as used.
        // A valid guess was made, increment the counter IF it's not in the word.
        if(word.find(letter) == string::npos) {
            guesses++;
        }

        // Lets re-generate our hidden_word, revealing each occurance of that letter if it exists.
        hidden_word = RevealWord(hidden_word, word, letter);

        // Is the word complete?
        if(word == hidden_word) {
            // Yes!
            cout << "CONGRATULATIONS! YOU WON!!" << endl;
            break;
        }

        // Is the player out of tries?
        if(guesses == total_possible_guesses) {
            cout << "Sorry, but you lost! The word was: " << word << endl;
            break;
        }
    }
    
    return 0;
}

// ##############################################
int GetRandomElement(int max) {
    srand(time(NULL));
    
    return rand() % max;
}

// #############################################
string strtolower(string str) {
    locale loc;
    string retval = str;

    for(size_t i = 0; i < str.length(); i++) {
        retval[i] = tolower(str[i], loc);
    }

    return retval;
}

// ##############################################
string ShowLettersUsed(map<string, int> letters) {
    string retval;

    for(map<string, int>::const_iterator it = letters.begin(); it != letters.end(); it++) {
        retval += it->first;
    }

    return retval;
}

// ##############################################
string RevealWord(string hidden_word, string word, string letter) {
    for(unsigned int i = 0; i < hidden_word.length(); i++) {
        if(hidden_word[i] == '-' && word[i] == letter[0]) {
            // This occurance should be revealed.
            hidden_word[i] = letter[0];
        }
    }

    return hidden_word;
}

```

---

### Post by Nahjil on 2012-07-26
One thing I think you should get in the habit of doing now, is commenting on every line of your code. Telling people why you have that line in there. It will help you immensely on group projects, or when you have to shift through thousands of lines of code. It will also help you when you are trying to make your code more efficient. I would like it because, I'm a complete beginner in C++ and looking at your code I don't have much of a clue what is going on. If I was to spend some time with it I'm sure I could figure it out, but it would be nice. As for ideas how about a random dice roller that can take any number of dice with any number of sides. It would be a handy thing for some table top gaming.

---

### Post by muteXe on 2012-07-27
Dunno about *every* line of code :)

---

### Post by trent.josephsen on 2012-07-27
Seems to be quite a rash of thread necromancy going around.

I also think "comment on every line of code" is bad advice. Every function, yes. Every variable, ok. But if you have to explain every single statement then your code must be virtually unreadable. Comments on code, like typedefs, should exist only to make things clearer.

---

### Post by ratcheer on 2012-07-27
Build an object-oriented Yahtzee game. It is simple enough to get your head around, but complicated enough to give you meaningful experience.

Make it a text-based game to start. Once you perfect it, see if you can use the guts of that and carry it forward to a graphical game.

Just an idea.

Tim

---

### Post by kbaumen on 2012-07-31
I think this is a beautiful resource. Most of the assignments there talk about using Java or C, but that doesn't matter. Any language can be used. In fact, a lot of the problems are somewhat open-ended so there are a lot of other things to do besides the basic functionality that is asked for.
 
[http://introcs.cs.princeton.edu/java/assignments/](http://introcs.cs.princeton.edu/java/assignments/)
 
Mind you, I have nothing to do with Princeton (other than that I will be starting a course on algorithms on [www.coursera.org]("http://www.coursera.org") next week, the course being run by some folk from Princeton).

---

