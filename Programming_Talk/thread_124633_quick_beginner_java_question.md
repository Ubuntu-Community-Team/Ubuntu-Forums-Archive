---
title: "quick beginner java question"
date: 2006-02-01
forum: Programming Talk
---

### Post by Griff on 2006-02-01
Does a variable of char type need to be initialized?
I ask because when I use a char variable in a if...else statement I get a 

P1.java:17: variable B might not have been initialized
if (selection == B) {

I did declare B and selection as a char earlier.  I don't see what's causing the error. :-k
Any help appreciated.

---

### Post by LordHunter317 on 2006-02-01
Posting the entire method and/or class would be prudent.

---

### Post by Griff on 2006-02-01
class P1 {
  public static void main(String args[]) {
  
  boolean correct = false;
  boolean incorrect = true;
  char selection, A, B, C;
  int number;

  //FIRST QUESTION
  System.out.println("Welcome to Trivia!\n");
  System.out.println("Who was the first player to win the " +
                     "Heisman Trophy?\n");
  System.out.println("A) Danny Wuerffel\n" +
                     "B) Steve Spurrier\n" +
                     "C) Emmitt Smith");
  System.out.print("Enter Choice:");
  selection = UserInput.readChar();
    if (selection == B) {
    System.out.println(incorrect);
    }
    else {
    System.out.println(correct);
    }

  }


}

---

### Post by Revert on 2006-02-01
You're trying to compare the user input in "selection" to something named "B" that has no value yet.  If you're trying to see if they're inputting the letter B, just do if(selection == 'B')

---

### Post by LordHunter317 on 2006-02-01
You declare them, you don't initalize them.  Declaring a variable mearly notes it's existance.  Initializing it means you give it a initial value, usually when you declare it.  If you mean to compare to the literal character B, however, that's not how you would do it.  You would compare to the literal 'B'.

---

### Post by Griff on 2006-02-01
Gah! That it! Thanks guys!
:mrgreen:

---

