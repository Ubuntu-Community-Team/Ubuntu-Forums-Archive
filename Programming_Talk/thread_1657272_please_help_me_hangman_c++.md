---
title: "please help me hangman c++"
date: 2011-01-01
forum: Programming Talk
---

### Post by alshidis on 2011-01-01
hi guys...
I have to write a program that plays a game of hangman with following features:
1.the program start by reading from an input file a list of words and stores them in an array of string.
2.the program then selects randomly one of the words. the word should appears like *****
3.the program should includes 3 functions:
a. function to read the list of words.
b. function to find the number of occurrences and locations of a guessed letter
c.test if a game has terminated (6 incorrect guesses attempted).
sample output:
hangman
the word: **
guess a letter: f
not exists
**
guess a letter: h
h exists 1 time in the word
h*
guess a letter: i
i exists 1 time in the word
hi
bravo
play again? (Y/N): N
thank you

---

### Post by Idefix82 on 2011-01-01
Judging by the extremely unspecific request "I need your help", you are expecting others to do the homework for you, which isn't going to happen. What exactly is your problem?

---

### Post by worksofcraft on 2011-01-01
> **alshidis said:**
> hi guys...
I have  to write a programme that plays a game of hangman with following feeatures:
1.the programme start by reading from an input file a list of words and stores them in an array of string.
2.the programme then selects randomly one of the words. the word should appears like *****
3.the programme should includes 3 functions:
a. function to read the list of words.
b. function to find the number of occurrences and locations of a guessed letter
c.test if a game has terminated (6 incorrect guesses attempted).
sample output:
hangman
the word: **
guess a letter: f
not exists
**
guess a letter: h
h exists 1 time in the word
h*
guess a letter: i
i exists 1 time in the word
hi
bravo
play again? (Y/N): N
thank you
I need your help today ,please.

Is this an assignment for school/uni or a home project?

You see we not allowed to do your homework for you ;)

However...

string aStrings[] =...
ok so how many strings will you have?
Perhaps you should make it a vector of strings then you can keep adding more as needed... ok so this is just to get you started... and I'll let the others tell you all the things that are wrong with it ^^

[php]
// g++ hangman.cpp
#include <iostream>
#include <string>
#include <vector>

using namespace std;

int main(int argc, char *argv[], char *envp[]) {
	vector<string> aStrings;
	while (cin.good()) {
		string sReadMe;
		cin >> sReadMe;
		aStrings.push_back(sReadMe);
	}

	for (int i = 0; i < aStrings.size(); ++i) {
		cout << aStrings[i] << endl;
	}

	return 0;
}
[/php]

---

### Post by alshidis on 2011-01-01
I am sorry , I just need some hints.
 
I modified the following code:
 
[PHP]
#include <iostream>
#include <vector>
#include <algorithm>
#include <ctime>
#include <cstdlib>
#include <cctype>
#include <string>
using namespace std;
int main()
{
char my_choice;
const int MAX_WRONG = 6;
vector<string> words;
words.push_back("guess");
words.push_back("hangman");
words.push_back("diffecult");
srand(time(0));
random_shuffle( words.begin(), words.end() );
const string THE_WORD = words[0];
int wrong = 0;
string soFar ( THE_WORD.size() , '*' );
string used = " ";
cout << "Hi, let's play hangman.\n";
while ( ( wrong < MAX_WRONG) && ( soFar != THE_WORD ) )
{
cout << "The secret word is:\n"<< soFar << endl;
//Getting the players guess. Here is where the function should start
char guess;
cout<<"Guess a leter: ";
cin>>guess;
while ( used.find(guess) != string::npos )
{
cout<<"Guess a leter: ";
cin>>guess;
}//while 2
used += guess;
if ( THE_WORD.find(guess) != string::npos )
{
cout<<"Letter "<<guess<<" is in the word."<< endl;
for ( int i = 0 ; i < THE_WORD.length() ; ++i )
if ( THE_WORD[i] == guess )
soFar[i] = guess;
}
else
{
cout<<"Letter "<<guess<<" is not part of the secret word."<<endl;
++wrong;
}
}//This is the end of the get the guess part
//Ending the game
if ( wrong == MAX_WRONG)
cout<<"You have been hanged!";
else
cout<<"Bravo! You have guessed the full secret word\n";
return 0;
}//main
[/PHP]
 
but it does not include all features!!!

---

