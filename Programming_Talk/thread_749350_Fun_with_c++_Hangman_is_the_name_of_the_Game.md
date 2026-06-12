---
title: "Fun with c++ Hangman is the name of the Game"
date: 2008-04-08
forum: Programming Talk
---

### Post by nickoli on 2008-04-08
:)

My program functions except for one minor detail and thats my hangman character.
 I'm new to c++ this is my first course and I'm working on the character I can't get my switch statement to increment.
 I need the help. Any help will be appreciated and feel free to critique my program. Thanks for your time.


[PHP]/***************************
/This program is Hangman the 
/Game. It will import a list
/of words from a file and hide 
/them behind asterisks, as the 
/user guesses the correct 
/letters it will replace the 
/stars with them.
/***************************/

#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
using namespace std;

string getData(ifstream& );                                    
string stars(string );  
void ReturnModifiedHiddenWord(string word, 
			string& WordInProgress,char guess);
void display(string word);
void WinOrLose(string, string);
char prompt();
void titleOfGame();
void HangMan(int);

int main()
{
	ifstream fin;                                             
	string word,hidden, answer,
		WordToBeGuessed, WordToBeGuessed2;
	char guess, check ,yes;
	int i = 0, counter = 0, countError = 0, number = 0;

	fin.open("data.txt");
	titleOfGame();
	word = getData(fin); 														//prime read
	while(fin)
	{
		counter = 0;
		WordToBeGuessed = stars(word);
		display(WordToBeGuessed);												// display hidden word
		while( WordToBeGuessed != word &&  counter < 7)                         // give the user seven tries
		{
			 guess = prompt();                                                    //prompt user
			 ReturnModifiedHiddenWord(word, WordToBeGuessed, guess);
			 display(WordToBeGuessed);
			 counter++;
			 cout << "Would you like to solve the word?(y/n)";
			 cin >> yes;
			 if(yes == 'Y')
			 {
				cout << "What is  your guess?";
				cin >> answer;
				if( answer == word )
				{
					WinOrLose(answer,word);
					word = getData(fin);
					WordToBeGuessed = stars(word);
					cout << "The next word to guess is :" 
						<< WordToBeGuessed << endl;
				}
				else
				{
					cout << endl;
					cout << "YOUR GUESS IS WRONG:" << endl;
					cout << endl;
				}
			}
		}
		WinOrLose(WordToBeGuessed,word);
		word = getData(fin); 
	}                                                                             //last read}
	return 0;
}

   

string getData(ifstream& fin)                                                      //function to import data
{
	string word;
	fin >> word;
	return word;
}

string stars(string word)                                                           // this function will turn a word into stars 
{
	int i = 0;
	string::size_type x;    
	string hidden;
	hidden = word;
	x = hidden.length();
	for(i = 0; i < x; i++)
	hidden[i]  = '*';
	return hidden;
}

void display(string word)															  // this function is for displaying words
{
	cout << "The word is " << word << endl;
}

char prompt()																		  // prompt user for choice
{
	char userChoice;
	cout << "Please enter the letter of your choice: ";
	cin >> userChoice;
	return userChoice;
}

void ReturnModifiedHiddenWord(string word, string& WordInProgress, char guess)         //replace stars with correct letters.
{	   
	bool test = false;
	string::size_type pos;
	pos = word.find(guess);   
	int i = 0, number = 0, countError = 0;
	while(pos != string.npos)
	{
		WordInProgress[pos]=guess;
		pos = word.find(guess,pos + 1 );
		test = true;
	}

	if(pos == string.npos &&  test == false)
	{
         countError++;
		 number = countError;
		 HangMan(number);
		
	}
}

void WinOrLose(string WordToBeGuessed, string word)
{
	
	if(WordToBeGuessed == word)
	{
		cout << endl;
		cout << "YOU HAVE WON THIS ROUND! " << endl;
		cout << endl;
		
	}
	else
	{
		cout << endl;
		cout << "YOU HAVE LOST THIS ROUND! " << endl;
		cout << endl;
	}
}

void titleOfGame()
{
	cout << "WELCEOME TO THE GAME OF HANGMAN " << endl;
	cout << "developed by James Skornicka " << endl;
	cout << endl;
	cout << "* You will be given up 7 attempts to find a letter." << endl;
	cout << "* you have a chance to solve the word after each letter attempt. " << endl;
	cout << endl;
	cout << endl;
	
}

void HangMan( int variable)
{
	switch(variable)
	{
		
		case 1 :
    cout << "________" << endl;
	cout << "|      | " << endl;     
	cout << "0      | " << endl;
	cout << "       | " << endl;
	cout << "       | " << endl;
	cout <<"___________" << endl;break;

		case 2 :
	
	cout << "________" << endl;
	cout << "|      | " << endl;     
	cout << "0      | " << endl;
	cout << "o      | " << endl;
	cout << "       | " << endl;
	cout <<"___________" << endl; break;

		case 3 :

	cout << " ________" << endl;
	cout << " |     | " << endl;     
	cout << " 0     | " << endl;
	cout << "-o     | " << endl;
	cout << "       | " << endl;
	cout <<"___________" << endl;break;

		case 4 :
	
	cout << " ________" << endl;
	cout << " |     | " << endl;     
	cout << " 0     | " << endl;
	cout << "-o-    | " << endl;
	cout << "       | " << endl;
	cout <<"___________" << endl;break;

       case 5 :
	cout << " ________" << endl;
	cout << " |     | " << endl;     
	cout << " 0     | " << endl;
	cout << "-o-    | " << endl;
	cout << "/      | " << endl;
	cout <<"___________" << endl;break;
		case 6 :
	cout << " ________" << endl;
	cout << " |     | " << endl;     
	cout << " 0     | " << endl;
	cout << "-o-    | " << endl;
	cout << "/ \    | " << endl;
	cout <<"___________" << endl;break;
	}

       	
}[/PHP]

---

### Post by Zugzwang on 2008-04-08
Since you're still online, would you mind putting your code in [PHP] tags? Also please use the auto-formatter of your favourite IDE before posting the code because the way it is is hard to read.

---

### Post by nickoli on 2008-04-08
Thanks. Is that better?

---

### Post by Zugzwang on 2008-04-08
Almost. You have to keep all non-node out of the block between the tags. :-)

Just a guess: You have a line stating:
```

case '0' : 

```
...but you're probably meaning:
```

case 0:

```

The first version checks for the value 48 (the ASCII/whatever value of the letter '0').

Is that what you call "getting a switch statement to increment"?

---

### Post by nickoli on 2008-04-08
Your right the case 0 is scratched. My problem is I need to find a way to count the number of times I don't find a letter. The first time will be one of course. Then one will display. The second time a letter isn't found in the same letter two will display. etc.. etc... I believe but I'm not sure that my error is occuring in this function.

[PHP]void ReturnModifiedHiddenWord(string word, string& WordInProgress, char guess)         //replace stars with correct letters.
{	   
	bool test = false;
	string::size_type pos;
	pos = word.find(guess);   
	int i = 0, number = 0, sum = 0, countError;
	while(pos != string.npos)
	{
		WordInProgress[pos]=guess;
		pos = word.find(guess,pos + 1 );
		test = true;
	}

	if(pos == string.npos &&  test == false)
	{
         countError = 0;
		 cout << "Your Guess is wrong! Please Try again." << endl;
		 countError++;
		 number = countError;
		 HangMan(number);
	}
}[/PHP]

However there is a very real chance that I don't know what I'm talking about being that I'm new to c++ . Thanks for your time.:popcorn:

---

### Post by Zugzwang on 2008-04-08
Ah, ok, I see. So the problem is that you're declaring countError in "ReturnModifiedHiddenWord" as a local variable although you want to change the countError value declared in the main() function. Well, one way is to give a reference to this value to "ReturnModifiedHiddenWord" so it can access the number of errors from your main function.

Also, you're setting countError to 0 after you the user guessed wrongly. Why that?

So...

[PHP]
void ReturnModifiedHiddenWord(string word, string& WordInProgress, char guess, int &countError) // CHANGED HERE
{       
    bool test = false;
    string::size_type pos;
    pos = word.find(guess);   
    int i = 0, number = 0, sum = 0; // CHANGED HERE
    while(pos != string.npos)
    {
        WordInProgress[pos]=guess;
        pos = word.find(guess,pos + 1 );
        test = true;
    }

    if(pos == string.npos &&  test == false)
    {
         //countError = 0; // REMOVED THIS LINE
         cout << "Your Guess is wrong! Please Try again." << endl;
         countError++;
         number = countError;
         HangMan(number);
    }
}[/PHP]

and then in your main() function:
```

ReturnModifiedHiddenWord(word, WordToBeGuessed, guess, countError); 

```

---

### Post by nickoli on 2008-04-08
Thanks alot for your insight.  I simply made the fixes you recomended and they worked nicely. I hope you have a wonderful day.:guitar:

---

