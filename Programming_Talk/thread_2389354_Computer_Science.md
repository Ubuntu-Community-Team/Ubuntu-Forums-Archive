---
title: "Computer Science"
date: 2018-04-15
forum: Programming Talk
---

### Post by caorr on 2018-04-15
[FONT=sans-serif]The main driver:[/FONT]
[FONT=monospace]int main()[/FONT]
[FONT=monospace]{[/FONT]
[FONT=monospace]  string alpha = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"; [/FONT]
[FONT=monospace]  string words[MAX_WORDS]; [/FONT]
[FONT=monospace]  int wordNum=0, letters=0, misses=0, numWords=0;[/FONT]
[FONT=monospace]  char guess;[/FONT]
[FONT=monospace]  bool guessed[MAX_WORD_SIZE];[/FONT]
[FONT=monospace]  read_puzzles(words, numWords);[/FONT]
[FONT=monospace]  srand(time(0));[/FONT]
[FONT=monospace]  wordNum=rand() % numWords;[/FONT]
[FONT=monospace]  letters = words[wordNum].length();[/FONT]
[FONT=monospace]  for (int i=0; i<letters; i++)[/FONT]
[FONT=monospace]    guessed[i] = false;[/FONT]
[FONT=monospace]  do[/FONT]
[FONT=monospace]  {[/FONT]
[FONT=monospace]    display_puzzle(words[wordNum], guessed);[/FONT]
[FONT=monospace]    cout << "Available: " << alpha << endl;[/FONT]
[FONT=monospace]    cout << "Guess: ";[/FONT]
[FONT=monospace]    cin >> guess;[/FONT]
[FONT=monospace]    guess = toupper(guess);[/FONT]
[FONT=monospace]    for (int i=0; i<NUM_LETTERS; i++)[/FONT]
[FONT=monospace]      if (alpha[i] == guess)[/FONT]
[FONT=monospace]        alpha[i] = ' ';[/FONT]
[FONT=monospace]    if (!(found(words[wordNum], guessed, guess)))[/FONT]
[FONT=monospace]      misses++;[/FONT]
[FONT=monospace]    cout << "Misses: " << misses << endl;[/FONT]
[FONT=monospace]  } while (!winner(guessed,letters) && (misses < MAX_GUESSES));[/FONT]
[FONT=monospace]  if (misses == MAX_GUESSES)[/FONT]
[FONT=monospace]    cout  <<  "You  lose.  The  word  was:  "  <<  words[wordNum]  << [/FONT]
[FONT=monospace]endl;[/FONT]
[FONT=monospace]  else[/FONT]
[FONT=monospace]    cout << "You win. Nice job!" << endl;

return 0;[/FONT]




[FONT=sans-serif]FUNCTIONS:[/FONT]
[FONT=sans-serif]1. [/FONT]
[FONT=sans-serif]readPuzzles[/FONT]
[FONT=sans-serif] – two arguments: string array of [/FONT]
[FONT=sans-serif]words[/FONT]
[FONT=sans-serif], integer [/FONT]
[FONT=sans-serif]wordCount[/FONT]
[FONT=sans-serif] (reference parameter)[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  Returns nothing[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  This function opens up the puzzles file, verifies it opens successfully, reads the puzzles from the file into [/FONT]
[FONT=sans-serif]the array of [/FONT]
[FONT=sans-serif]words[/FONT]
[FONT=sans-serif], updates the [/FONT]
[FONT=sans-serif]wordCount[/FONT]
[FONT=sans-serif] to reflect how many puzzles were read.[/FONT]
[FONT=sans-serif]2. [/FONT]
[FONT=sans-serif]displayPuzzle [/FONT]
[FONT=sans-serif]– two arguments: string [/FONT]
[FONT=sans-serif]word[/FONT]
[FONT=sans-serif], array of bool [/FONT]
[FONT=sans-serif]guessed[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  Returns nothing[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  This function loops through each of the letters of the [/FONT]
[FONT=sans-serif]word[/FONT]
[FONT=sans-serif], looking at the corresponding position of the [/FONT]
[FONT=sans-serif]guessed[/FONT]
[FONT=sans-serif]  array.  If  the  letter  has  been  guessed,  display  it.  If  not,  display  the  underscore.  Also,  display  a [/FONT]
[FONT=sans-serif]space between each letter, as well as a couple of end lines after the word. It might output something like [/FONT]
[FONT=sans-serif]this:[/FONT]
[FONT=monospace]_ A S K _ _ B A _ _ [/FONT]
[FONT=sans-serif]3. [/FONT]
[FONT=sans-serif]found [/FONT]
[FONT=sans-serif]– three arguments: string [/FONT]
[FONT=sans-serif]word[/FONT]
[FONT=sans-serif], array of bool [/FONT]
[FONT=sans-serif]guessed[/FONT]
[FONT=sans-serif], character [/FONT]
[FONT=sans-serif]guess[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  This functions returns a bool, true if letter [/FONT]
[FONT=sans-serif]guess[/FONT]
[FONT=sans-serif] is found in puzzle [/FONT]
[FONT=sans-serif]word[/FONT]
[FONT=sans-serif], otherwise false[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  If the [/FONT]
[FONT=sans-serif]guess[/FONT]
[FONT=sans-serif]  is in the [/FONT]
[FONT=sans-serif]word[/FONT]
[FONT=sans-serif], the function should also change the [/FONT]
[FONT=sans-serif]guessed[/FONT]
[FONT=sans-serif]  array  to  true  at each position it [/FONT]
[FONT=sans-serif]exists[/FONT]
[FONT=sans-serif]4. [/FONT]
[FONT=sans-serif]winner[/FONT]
[FONT=sans-serif] – two arguments: array of bool [/FONT]
[FONT=sans-serif]guessed[/FONT]
[FONT=sans-serif], the integer number of [/FONT]
[FONT=sans-serif]letters[/FONT]
[FONT=sans-serif] in the puzzle[/FONT]
[FONT=sans-serif]&#61623;[/FONT]
[FONT=sans-serif]  This  function  will  loop  through  all  of  the  elements  of  the [/FONT]
[FONT=sans-serif] guessed[/FONT]
[FONT=sans-serif]  array.  If  any  element  is  false,  the 



[/FONT]
[FONT=monospace][FONT=sans-serif]function should return false. If all of the elements are true, the function should return true.[/FONT]}



[/FONT]







[h=2][/h]


My teacher is wanting me to use the functions she has given us to write this code using c++. She has given the main code. Help writing the code for this project would be great

---

### Post by wildmanne39 on 2018-04-15
Thread Closed!
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will either be jailed or closed, and warnings or infractions may be issued.

---

