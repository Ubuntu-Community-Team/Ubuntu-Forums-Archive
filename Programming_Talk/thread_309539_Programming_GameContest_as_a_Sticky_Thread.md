---
title: "Programming Game/Contest as a Sticky Thread"
date: 2006-11-29
forum: Programming Talk
---

### Post by imaiden22 on 2006-11-29
[COLOR="Blue"]**Contest 1:**

Write a program that takes a string as input, and outputs it backwards.[/COLOR]



Hey everyone, i had a great idea for this section of the forum.

I thought we might spark some fun into this forum and make a new sticky thread where we have programming contests and puzzle to make accomplish certain tasks (not limiting the task to any one language) and doing something like that once a week

im definitely open to any other ideas you guys might have, but im a new programmer learning java and python and this would be an awesome way to work on my skills and learn from other peoples code.

let me know what you think out there!

-Nick

---

### Post by kthakore on 2006-11-29
That would be awesome, especially for new developers. I suggest a contest that just gives us a problem and we can solve it anyway and with any language we want. Also at the end of each challenge the programmers can ctricque the work! So I suggest three stickys, one for contest management, one for WIP, and one for voting.

---

### Post by imaiden22 on 2006-11-29
hey, sounds good to me, i just want the practice and it'd probably be fun for all of us here on the forums

---

### Post by coder_ on 2006-11-29
Neat, back when I was using Windows, the game programming forum I visited did this, as well with 3D imagery competitions.


On a slightly unrelated note, Quizzes and puzzles in programming, which are moderately similar to this idea, are always fun.  See [Ruby Quiz.]("http://rubyquiz.com/")

---

### Post by addicted68098 on 2006-11-29
I have always wanted to make a game,
A Tetris is supposed to be easy to make, why not make a tetris clone to start out with, and add visual and sound effects to it?

Maybe make it like Lumines, and Tetris Combined!

---

### Post by coder_ on 2006-11-29
If you are going for your very, very, very first game, here are some REALLY easy games to write (They have simple logic):
[LIST]
[*]Pong
[*]Arkanoid (Breakout)
[*]Space Invaders
[/LIST]

Back when I did graphics programming, we typically started out with these.

---

### Post by imaiden22 on 2006-11-29
Haha, I guess my title could've been a bit confusing, but my intent wasn't to program games, but to have a little game that involves programming, on a much more basic level. I mean if you advanced coders out there wanna tackle the tougher stuff that's fine but my intent was to make it a simple thing for new programmers like myself to handle and sharpen our skills with!

I like the ideas though people, keep them coming!

---

### Post by kthakore on 2006-11-30
maybe the person proposing the challenge could provide hints for beginners to begin programming with, especially with games like tetris.

---

### Post by imaiden22 on 2006-11-30
yeah, that's a great idea, it would give us a starting point and ensure that we weren't clueless going into this thing.

---

### Post by coder_ on 2006-11-30
We did programming/art challenges in a neat way at our my old game programming forum.

One person starts off the competition, and choses the theme (Or objective, or however you do your competition).  He picks a winner (Or we can do it by a poll), and the winner chooses the next topic, and this goes on forever.  :)   It's really neat.  Our compos typically lasted one week, so people in school/work could at least have a full weekend to devote to it, and weekdays for planning/doing small amounts of code.

I'd really be interested in doing this.  It is really fun.  I'd be reallllly interested in this actually :P

We need a theme/topic/challenge to jumpstart it...  I'll be thinking, and anyone else, feel free to post an idea so we can start this up :)

**EDIT: See my next post (On 2nd page, if you have number of posts per page on default) for info on my idea.**

---

### Post by po0f on 2006-11-30
First contest: port the Linux kernel source to Java.  Get a JVM boot-strapped environment up and running capable of booting said kernel.  :p

---

### Post by coder_ on 2006-11-30
For the Kernel to JVM idea:  You have 2 days, starting... now :P

[B]EDIT:
Also, for an idea of what to do, quizzes are fun.  See [Ruby Quizzes]("www.rubyquiz.com") for an example of this.  An objective is defined, testing code is written, a basic class with the needed methods and parameters are created, and the contestant must implement the idea in the methods to achieve the desired output.

Simplistic Example:[/B]
```

Objective:  
Convert an xml file describing instances of a class to actual objects


Provided Testing code (Program must create correct output to "win"):
s = xmlobjmaker('objects.xml')
s.read_data()  # Should read the xml file, storing the data
s.create_objects()  # Should create the objects
# Actual testing code that verifies program is working would go here in a real quiz...
# Also, the correct output would be specified in the quiz for programs that do output, 
#   and the contestant would have to implement his program so it creates that same output


Provided file - objects.xml:
<xml ...whatever, too lazy to do the doctype and whatnot>
   <!-- will create a Ninja object with properties specified -->
   <Ninja height="5.5" speed="10" ... />
   ...
</xml>


Provided xmlobjmaker class (Contestant must write code here to implement the program):
def xmlobjmaker():
   def __init__(self,xmlfile):
      # Create xml document, etc.

   def read_data(self):
      # Store the data read from the xml file to use to make the objects

   def create_objecs(self):
      # Implement creating of objects from stored data


The Would-Be Provided Ninja Class:
def Ninja():
   #  Ninja objects were used in the xml file for the test, and in a real competition,
   #     this would be implemented for you, so you have a class to work with
   ...
   ...

```
The files above would either be provided as an archive (zip,rar,tar.gz,tar.bz2,etc.), or just posted and you have to create the files.


P.S:  Ruby quiz is exactly like this almost, and is real fun.

---

### Post by imaiden22 on 2006-11-30
Hey guys, I love the initiative but like we mentioned before, a nice solid clue to get some of us newer coders on the same level would be awesome, myself included :)

---

### Post by po0f on 2006-11-30
imaiden22,

I'm sorry, my post was sarcastic.  What I posted is near impossible without a Herculean effort.  I guess you really can't tell if you aren't a programmer.  :)

Here's a simple one:

**Contest #1**

Write a program that takes as input one string, and outputs the string backwards.

Think I should repost this?

---

### Post by imaiden22 on 2006-12-01
Haha, yeah it hit me like 20 seconds after my post...I was just a bit slow, yeah that sounds like a great first post and don't worry about the sarcasm, after it hit me, I laughed pretty hard!

I was thinking we could make this thread sticky but I'm not sure how to go about it and as for your first contest, I say LET THE GAMES BEGIN! 8)

oh and i'll put the contest in my first post for all to see and thanks for the contribution!

---

### Post by rappo on 2006-12-01
```
public class string {

public static void main(String[]args) {
 String phrase="imaiden22";
 int l=phrase.length();
 char[] charArray = new char[l];

 for(int i=0; i<l; i++) {
  charArray[i]=phrase.charAt((l-1)-i);
 }
 
 for(int i=0; i<charArray.length; i++) {
  System.out.println(charArray[i]);
 }
}

}
```

This is a sort of nooby way to do it, but it is what it is.  The problem with this is that the reverse is only outputted, it is not an actual string in the program.  I understand that that can be easily fixed using the StringBuffer junk, but I don't care to do it :P

By the way, that's Java.

---

### Post by coder_ on 2006-12-01
rappo:  Nice :)
Official thread is here though: [http://ubuntuforums.org/showthread.php?t=310297](http://ubuntuforums.org/showthread.php?t=310297)

---

