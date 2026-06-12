---
title: "Java"
date: 2006-07-02
forum: Programming Talk
---

### Post by *tina* on 2006-07-02
Hello to everyone, hope your all doing well! Okay so i've got this assignment, which is probably going to be very straightforward to all of you, and i'm just going out of my brain trying to answer it (thats right not so smart in programming, but thats okay) So you would be doing a very good deed if you agreed to help the dazed and confused, who,i might add has the deadline due in 1 day...thank you very much for your time and effort!

the question is

Write a java application that allows a user to input a positive integer number that displays 
              a. the number of digits in that number
              b. Sum of the digits in the number.
so lets say for example you enter 735, its consisted of 3 digits(which should be the output) and then find the sum 15, whish is also displayed...

SO any helpful ideas...thanks!

---

### Post by QMario on 2006-07-02
Why not just parse the number as a String, and then convert the string to a Character array.You should know what to do from there.

Here is a start:

```

import java.util.Scanner;

public class Digits
{
  public static void main(String[] args)
  {
    Scanner scanner = new Scanner(System.in);
    int num = scanner.nextInt();
    Integer number = new Integer(num);
    String numString = new String( number.toString() ); 
    Character digits = new Character[numString.length()];

    for(int i = 0; i < numString.length(); ++i)
    {
       digits[i] = new Character( numString.charAt(i) );
    }
  }
}
```

---

### Post by *tina* on 2006-07-02
Wow, i didnt even know you could do that, i'm sorry it's only been a couple of days that ive been introduced to the java lang., so honesty, i dont even know what 'Char[] digits = new digits[numString.length()];'  :confused:  that means...perhaps theres an easier way, seeing that my professor hasnt gotten past chap. 3?? 
But thanks alot, ill try to read more, and TRY to figure it out, and figure out where your trying to get to, too

---

### Post by *tina* on 2006-07-02
Okay, i'm really confused, we didnt even start on arrays yet, so with that i dont think the doc. is going to give us hmwk on something we didnt get to yet, know what i mean, yeah, so any other helpful 'simple' requests? 8-[

---

### Post by Lster on 2006-07-02
...

---

### Post by *tina* on 2006-07-02
actually, no, i dont know it, we havent got there yet, but do you think its the only way? If it is, i geuss i can read up on it and check it out, but the thing is i'm not so good at independent study, especialy if its branching out with a bunch of other "need to understand inorder to understand this' kind of thing...like i said i've only had a cuople of days, so weve started with the basics, you know input output, the control structers, thats about it.

---

### Post by Lster on 2006-07-02
...

That would print 5 because there are 5 letters in the String.

---

### Post by *tina* on 2006-07-02
Oh...well that doesnt seem too complicated, (score!!!), Thanks! \\:D/ 

Sorry to bother you Lster, (your awesome), but do you happen to have any idea how i might be able to add the digits in the inputed number, like the ex. you used, 12345, have it output 15, i'm sure a control structure is used, should the string.length be placed in a for loop or something(is that even permitted?)
ok, plz bear with me!

---

### Post by Lster on 2006-07-02
...

---

### Post by *tina* on 2006-07-02
right...method i knew that. adding it is harder, great, i was waiting for that comment to come. I prefer the while, its alot less confusing, i think.

---

### Post by Horsman on 2006-07-02
It sounds much mroe liek this is what your professor would liek at this point in your java career.

```

class myinto{

        public static void main(String args[]){
                int myint = 735;
                int mycopy = myint;
                int mydigits = 0;
                int myadd = 0;
                while(mycopy > 0){
                        mydigits++;
                        myadd += mycopy % 10;
                        mycopy = mycopy / 10;
                }
                System.out.println(myint +" : "+ mydigits +" : "+
myadd);
        }
}


```

The % (pronounced mod) symbol finds the remainder after a divsion, so if you % 10 something, you get the last digit.
The number of digits in a number is the amount of times you can dvide it by 10 before its got no "one's" digit. With integers, a number rounds down always, so in this case, when we get to the fourth iteration of the while loop, .735 = 0 and it does not continue.
We divide the number by 10 each time in order to get teh next lowest digit, as well as ensure the loop will terminate.

Feel free to ask any questions.
Output:
```

735 : 3 : 15

```

---

### Post by Lster on 2006-07-02
...

---

### Post by *tina* on 2006-07-02
Okay this is going to take a while for me to consume...wouldnt the mod come out as 30? I thought it was similar to the remainder of division

---

### Post by Horsman on 2006-07-02
735 / 10 = 73 + (5) so you'd get 5 as your first answer,
then 73 / 10 = 7 + (3) so youd get 3 as your next answer,
then 7 / 10 = 0 + (7) so youd get 7 as your last answer.

---

### Post by *tina* on 2006-07-02
sory i didnt see ur post...time to analyze

houstin weve got a problem...what is all this about (a.charAt(i))??

---

### Post by Lster on 2006-07-02
...

---

### Post by Lster on 2006-07-02
...

---

### Post by *tina* on 2006-07-02
so  a.length()...is in the place of "12345"...god i know i'm driving you guys crazy, its just this all new info.!!!!!!! and (a.charAt(i)), is taking the string 1, and placing it with 0?? AHHH!!!!!!

Horsman, how did you get 3 for mydigits??? (i am a bit more faimiliar with your way, just not understanding the procedure!!!)

---

### Post by *tina* on 2006-07-02
Are you sure its ok to bother ou with some ridiculus q's, well, ok horsman, brace yourself for some crazy q's!! :oops:  

while(mycopy > 0){
                        mydigits++;
                        myadd += mycopy % 10;
                        mycopy = mycopy / 10;

okay starting with mydigits, its being incremented so it becomes one then, myadd = 5, then mycopy = 73.5...is that completly wrong?

erm..lster did i scare you off?? I missed your last post...i geuss we posted at the same time, but you did an excellent job explaning, your a teacher right??

---

### Post by Lster on 2006-07-02
...

---

### Post by QMario on 2006-07-02
Thank God!!! :)
Here is how I did it:

```

import java.util.Scanner;
import java.lang.Exception;
import java.util.InputMismatchException;

public class Digits
{
  public static void main(String[] args)
  {
    try
    {
      System.out.print("Enter a number: " );
      Scanner scanner = new Scanner(System.in);
      int num = scanner.nextInt();
      Integer number = new Integer(num);
      String numString = new String( number.toString() );
 
      int numDigits = numString.length();

      Character[] digits = new Character[numString.length()];
      Integer[] integerDigits = new Integer[numString.length()];

      for(int i = 0; i < digits.length; ++i)
      {
        digits[i] = new Character( numString.charAt(i) );
      }

      int sum = 0;
      for(int i = 0; i < integerDigits.length; ++i)
      {
        integerDigits[i] = new Integer( digits[i].toString() );
        sum += ( integerDigits[i].parseInt( digits[i].toString() ) );
      }

      System.out.println("Sum=" + sum);
    }
    catch(InputMismatchException e)
    {
      System.out.println("The number entered is too large.\nOnly 10 ten digits  please");
      e.printStackTrace();
    }    
  }
}

```

---

### Post by *tina* on 2006-07-02
OH OMG!!! I get it!!!! lets do the little dance again \\:D/ !!! Thanks alot for clearing that up!! Man, horsman, your a genius, ive got to give you a thumbs up, you jus tmade my life alot easier!!!!!!!!!!!!!!!!!

okay this was going to be posted before i read the one you  just posted...goodness gracious lord have mercy on my brain..um, and you guys too!! ok ive got to analyze again thatll take only 10 yrs..jk

---

### Post by *tina* on 2006-07-02
oh woops i thought horsman posted that last post


the thing is, your using terms that im not yet faimliar with, soo thats just a tiny problem, yeah my hmwk is due in one day, yeah thats not much time to 'scan' the whole book is it...

import java.lang.Exception
(HUH??)
try
(try what..lol)

oka, i'm sure your way is absolutely correct but its way off my level of understanding..god i feel like an idiot...lol

---

### Post by *tina* on 2006-07-02
um one last question to horsman, int myint = 735;, thats an initialized variable, the question was to allow the user to input any int. number, so do i just use the Scanner scanner = new Scanner(System.in);, does the program follow the procedure the same, nothing changes right?

---

### Post by Horsman on 2006-07-02
[QUOTE=*tina*]um one last question to horsman, int myint = 735;, thats an initialized variable, the question was to allow the user to input any int. number, so do i just use the Scanner scanner = new Scanner(System.in);, does the program follow the procedure the same, nothing changes right?[/QUOTE]

yes, same process exactly, although you want to make sure to scan for nextint rather than a string, but Im sure youre teacher mentioned that.

---

### Post by QMario on 2006-07-02
[QUOTE=*tina*]oh woops i thought horsman posted that last post


the thing is, your using terms that im not yet faimliar with, soo thats just a tiny problem, yeah my hmwk is due in one day, yeah thats not much time to 'scan' the whole book is it...

import java.lang.Exception
(HUH??)
try
(try what..lol)

oka, i'm sure your way is absolutely correct but its way off my level of understanding..god i feel like an idiot...lol[/QUOTE]

Oh, that is just exception handling.
You don't need that for your program to accomplish its purpose.

---

### Post by Max Luebbe on 2006-07-02
If you need a quick escape from exception handling and don't want to figure it out now, add 'throws Exception' to the end of public void main (String args[])

---

### Post by ynef on 2006-07-03
This is one of those tasks where it *really* helps to use a pen and paper to figure out how you would approach this, without even thinking about the programming language. 

Your first question should be: ``how do I solve this mathematically/systematically?'' As I understand it, you haven't covered a lot of ground in your class yet, so the standard way of solving this (using modulus and division) is most likely the best way of doing it.

Your second question, once you've figured out *what* to do is *how* you do it. The answer to that includes getting familiar to the API[1] (describes what every single class in Java and its libraries can do) and using other resources, such as a forum, to get to know what is given to you.

Using the API as a starting point, and going to the String class, you'll find that everything you need for a String based approach is already there for you -- you've got String.length() and String.charAt(). These, combined with Integer.parseInt() are sufficient to perform your task as well. I believe a solution using these have already been posted.

Using this two step approach teaches a valuable concept -- programming is nothing more than *implementing* a solution to a problem, not the actual solution. 

[1] [http://java.sun.com/j2se/1.5.0/docs/api/index.html](http://java.sun.com/j2se/1.5.0/docs/api/index.html)

---

### Post by Horsman on 2006-07-03
Couldn't have said it better myself. I find it very important to think of programming as only an implementation of a solution rather than the actual sulution, and the String solution to me is more like a programming hack than the implementation of a pre meditated solution.

---

### Post by Max Luebbe on 2006-07-03
I disagree about the String solution being a hack.
String is more or less an immutable Character array.

It's a lot more efficient and clear to other people who may have to read the code if you solve it in a way that skips unneccessary steps and does it as simply as Possible. The API is there to help, and can really make things a lot easier. I agree with Ynef completely.

Whats wrong with:

```

Scanner keyboard = new Scanner(System.in);
String theNumber = keyboard.nextInt();
int sum = 0;

for (int i = 0; i < theNumber.length(); i++)
  sum+=Integer.parseInt(theNumber.charAt(i));

System.out.println("Length of Number: " + theNumber.length());
System.out.println("Sum of Number: " + sum);

```

---

### Post by QMario on 2006-07-04
[QUOTE=Max Luebbe]I disagree about the String solution being a hack.
String is more or less an immutable Character array.

It's a lot more efficient and clear to other people who may have to read the code if you solve it in a way that skips unneccessary steps and does it as simply as Possible. The API is there to help, and can really make things a lot easier. I agree with Ynef completely.

Whats wrong with:

```

Scanner keyboard = new Scanner(System.in);
String theNumber = keyboard.nextInt();
int sum = 0;

for (int i = 0; i < theNumber.length(); i++)
  sum+=Integer.parseInt(theNumber.charAt(i));

System.out.println("Length of Number: " + theNumber.length());
System.out.println("Sum of Number: " + sum);

```[/QUOTE]

I thought about that way too, but after looking at the Java API, I couldn't find a parseInt method that took a char as an argument, so I was forced to use the toString() method for the Character class. 

That line could be rewritten like this:
```
parseInt(  ( new Character( theNumber.charAt(i) ) ).toString() );
```

---

### Post by Horsman on 2006-07-04
you can easily change a char that is a number to an int by subtracting the char for 0 from it:

```

int num = (int)(string.charAt(i) - '0');

```

---

### Post by Max Luebbe on 2006-07-04
If you need a string, you can always do things like this too:

Char - > String
String newStr = "" + 'c';

Int - > String
String newStr = "" + 7;

There's never just one way to do a task in programming - as you get more experience, you'll start being able to come up with 6 or 7 ways to do the same thing, and then rationalize a choice between them. When that happens for the first time, its an awesome feeling.

---

### Post by Horsman on 2006-07-04
I love java.

---

