---
title: "A C++ program problem."
date: 2009-11-28
forum: Programming Talk
---

### Post by jianan77818 on 2009-11-28
I got a homework assignment this week, but I don't really know how to do it. Can someone tell me what should I do for this program? Don't have to show me the program, I just want some hint for that. Like what kind of loops should I used, and I just don't really get this program... Please help me!!

   **[SIZE=3][COLOR=black][COLOR=black]This program will play the game of "Hangman" - wherein the user tries to guess the proper letters forming a word selected by the computer, or by a second user. Each time an incorrect letter is chosen, a new portion of a hanged man is drawn - if the fully hanged man figure is drawn, the user has lost! If, on the other hand, the user guesses the word correctly before then, the user wins. [/COLOR][/COLOR][/SIZE]**
  
[LIST=1]
[*]**[SIZE=3][COLOR=black]The user should be able to choose between playing against the      computer, or against another human. The only difference will be how the      word to be guessed is selected: If playing against the computer, the      computer will choose from a built-in list of words, picking one of them at      random; If playing against another human, the human hangman will type in a      word (a string) [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]The user (either the guesser or the hangman) should be asked for      the number of incorrect guesses to allow the guesser... within the range 4      to 10 inclusive. [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]Before each guess entered by the user, the program should [/COLOR][/SIZE]**
[LIST=1]
[*]**[SIZE=3][COLOR=black]Display the letters already chosen [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]Display the number of guesses left [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]Display the portion of the word       already guessed, inserting an * (asterisk) for each letter not yet       guessed. [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black](Optional) Display the hanged man       portions already "drawn" - starting with a scaffold, then the       head, body, arms, legs, face, etc... [/COLOR][/SIZE]**
[/LIST]
[*]**[SIZE=3][COLOR=black]The user enters a character; the program will then indicate if an      incorrect character was chosen: [/COLOR][/SIZE]**
[LIST=1]
[*]**[SIZE=3][COLOR=black]A letter already chosen [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]Any non-alphabetic character (such as       ?, /, 4, $, etc.) (Hint: see documentation on *ctypes.h* -       especially *isalpha()*) [/COLOR][/SIZE]**
[/LIST]
[*]**[SIZE=3][COLOR=black]If the user has correctly guessed a letter that appears in the      word, the displayed word (with asterisks) is updated, replacing the proper      asterisks with the correctly guessed letter. For example, if the word were      "EAGLE" and the user guessed "E", both the first and      last letters would be filled in : E***E. [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]If the user has correctly guessed the entire word without using all      of the allowed incorrect guesses, a congratulatory message (and,      optionally, bells and whistles!) Should be displayed. If, on the other      hand, the user runs out of incorrect guesses, an appropriate message of      condolence should be displayed. [/COLOR][/SIZE]**
[*]**[SIZE=3][COLOR=black]Upon termination of a game the program should prompt the player if      another game is wanted - an 'n' or 'N' will terminate the program,      otherwise it will loop back, select another word, and do it all again!! [/COLOR][/SIZE]**
[/LIST]

---

### Post by dwhitney67 on 2009-11-28
> 
I got a homework assignment this week, ...

Not a very good way to commence a post here on the forums.  Let's see how long it will take for the moderators to close this thread down.

---

### Post by ve4cib on 2009-11-28
I assume you've played Hangman before, so the basics of the program should be easily understood.  You'll probably need to use a lot of while-loops in the program, likely with some nested within other ones.

My best advice is to break the program down in to bite-sized funcitons.  What do you need to be able to do?  A few things come to mind...

- get an input of 1 character from the user
- check that the input has not already been used, and that it is a letter
- check if the user has won (i.e. the word is complete and correct)
- check if the user has lost (i.e. have they run out of wrong-guesses)

Look at each sub-problem in isolation and try to solve each one.  Once you've figured out how to do each of those pieces then you can put them all together to make the game.

---

### Post by lisati on 2009-11-28
My $0.02: The assignment is already broken down into 7 different parts which can be tackled one by one and then combined. How would you achieve each of the sections? How would you co-ordinate the different parts into a complete functioning program?

---

