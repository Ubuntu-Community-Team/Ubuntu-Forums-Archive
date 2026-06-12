---
title: "Newbie question relating to loops in games"
date: 2008-07-08
forum: Programming Talk
---

### Post by myromance123 on 2008-07-08
Hi, yes Im a newbie at programming and I wanted to understand something so please dont go flaming me yeah, thanks, appreciate it~

  Basically its this, how do you make a loop that has more than one option to be played but can continue sequentially even if another loop is started for another object?

  For example ( this is what I believe the idea of my question closely relates to ) in WarCraft 3 if you click a character several times you will notice that he/she says something different each time, but this does not go on forever nor is it random, it eventually returns to what he first said.
 Now, how does the program look like if you press the character but he does not go blurting out all the audio made for him at once? Why does he do it on each click only?

  Secondly, if I were to click another character (B) after clicking the first character(A) how is it that when I click character (A) once again, the program is able to continue where it left off?

  If you could kindly show me in pseudocode or algorithms I would appreciate it a lot, but please not in any specific language (Im not language specific yet). 
 Your answer could be helping me move ahead in my understanding of not only game programming but also object-oriented programming, so a BIG thanks to you, cos you rock :guitar:    :lolflag:

---

### Post by Lod on 2008-07-08
Something like this. 2 counters one for character A and one for B.
The programs registers the mouseclicks and looks on which one it was. If on A then a function made for A is processed, if it was on B the function for B is processed.

```
global variable
counterA = 0
counterB = 0

function registerClicks
  if MouseOnClick = character A
      do click_on_A
  else if MouseOnClick = character B
      do click_on_B

function click_on_A
  for counterA to 8 do
    counterA + 1
    if counterA == 1 say "oi"
    if counterA == 2 say "test"
    if counterA == 3 say "how much more"
  ...
    if counterA == 8 say "finally" and set counterA to 0
  end
end

function click_on_B
  for counterB to 8 do
    counterB + 1
    if counterB == 1 say "hello A"
    if counterB == 2 say "get coffee"
    if counterB == 3 say "with sugar"
  ...
    if counterB == 8 say "so soon"
  end
end

```

---

### Post by skelooth on 2008-07-08
I believe you answered your own question when you mentioned object oriented programming. 

Each sprite in your game world can be represented as an abstracted object which shares properties with all other sprites, such as a render() method, and in the case of your example, an array of witty responses to be cycled through along with an iterator member to keep track of what position it should be in.

As for looping

while(1) {
// main game loop
handle_action_that_alters_objects(some_object);
}

calling a function from your loop will not disrupt it's flow. Normally you want to respond when an "event" (such as a mouse click) is fired off. Under different design patterns this is usually completely abstracted from your main loop with the exception of the polling pattern.


> **myromance123 said:**
> Hi, yes Im a newbie at programming and I wanted to understand something so please dont go flaming me yeah, thanks, appreciate it~

  Basically its this, how do you make a loop that has more than one option to be played but can continue sequentially even if another loop is started for another object?

  For example ( this is what I believe the idea of my question closely relates to ) in WarCraft 3 if you click a character several times you will notice that he/she says something different each time, but this does not go on forever nor is it random, it eventually returns to what he first said.
 Now, how does the program look like if you press the character but he does not go blurting out all the audio made for him at once? Why does he do it on each click only?

  Secondly, if I were to click another character (B) after clicking the first character(A) how is it that when I click character (A) once again, the program is able to continue where it left off?

  If you could kindly show me in pseudocode or algorithms I would appreciate it a lot, but please not in any specific language (Im not language specific yet). 
 Your answer could be helping me move ahead in my understanding of not only game programming but also object-oriented programming, so a BIG thanks to you, cos you rock :guitar:    :lolflag:

---

### Post by myromance123 on 2008-07-09
> ...with an iterator member to keep track of what position it should be in.

   Its words like iterator that make my understanding totally come to a halt. Im still trying to understand these terms, so please dont expect me to realise that I have answered my own question :)
  Thanks though, skelooth ~

First a big thanks to you Lod, I get your code overall except for:
```
function click_on_A
  for counterA to 8 do
    counterA + 1
    if counterA == 1 say "oi"
    if counterA == 2 say "test"
    if counterA == 3 say "how much more"
  ...
    if counterA == 8 say "finally" and set counterA to 0
  end
end
```

  Why is it 'for counterA to 8 do' and not 'for counterA 0 to 8 do' ?
Does it make a difference, or can you count counterA as 0 to begin with?
Or am I getting it all wrong?

 Oh and one more thing, what does global variable mean?

---

### Post by Lod on 2008-07-09
> **myromance123 said:**
> 
First a big thanks to you Lod, I get your code overall except for:
```
function click_on_A
  for counterA to 8 do
    counterA + 1
    if counterA == 1 say "oi"
    if counterA == 2 say "test"
    if counterA == 3 say "how much more"
  ...
    if counterA == 8 say "finally" and set counterA to 0
  end
end
```

  Why is it 'for counterA to 8 do' and not 'for counterA 0 to 8 do' ?
Does it make a difference, or can you count counterA as 0 to begin with?
Or am I getting it all wrong?

 Oh and one more thing, what does global variable mean?If you do counterA = 0 to 8 it always will start with the first one. For example: if you're at the third option and click on character B and then back on A it will start with 'oi' again. But you wanted to remember where A was with his lines. Therefore you need global counters.
A variable is something in which you can (temporarily) save values you need later in your code. These values can be defined within a specific piece of the code, the function. Or it can be made available through the whole program, known as globally.

---

### Post by skelooth on 2008-07-09
int var="This is global";

int main() {

for(int i=0; i<10; i++) { }
// i is an iterator, because it *iterates* through the numbers, in your case, as
// an indice into an array

}


Don't worry too much about the vocabulary, you will pick it up with time. It takes years to become a solid programmer.

---

### Post by Lod on 2008-07-09
> **myromance123 said:**
> Its words like iterator that make my understanding totally come to a halt. Im still trying to understand these terms, so please dont expect me to realise that I have answered my own question :)
  Thanks though, skelooth ~
To explain the iterator part the same code can be used. Simply put: an iteration is a piece of code which is repeated over and over again. This can be done endlessly (seldomly useful or wanted) or done a specific amount of times. In my code it's 9 times. To keep track of this amount you use an Iterator, a counter, to keep track of the times a certain loop has been done. This is counterA

```
function click_on_A
  for counterA to 8 do
    counterA + 1
    if counterA == 1 say "oi"
    if counterA == 2 say "test"
    if counterA == 3 say "how much more"
  ...
    if counterA == 8 say "finally" and set counterA to 0
  end
end
```

---

### Post by Lod on 2008-07-09
You could take a look at Alice: [http://www.alice.org](http://www.alice.org)
As the makers say it themselves:
> Alice is a freely available teaching tool designed to be a student's first exposure to object-oriented programming. It allows students to learn fundamental programming concepts in the context of creating animated movies and simple video games.
I never took a look at it myself but I remember some positive remarks on it.

---

### Post by myromance123 on 2008-07-10
Ooh, I think I understand now. If I did not put an iterator like counterA, then everytime I clicked characterA then clicked characterB then back to characterA, characterA would restart the loop and not continue from its last positon, but with an iterator it would remember where it was last time it was clicked, am I right?

So, basically:
  Iteration = the action of the code being repeated
  Iterator = the item that keeps track of the number of repetitons ( the storage place )

 Not to sure I get the global variable. Is it basically stating that counterA = 0 and counterB = 0 are where the values for the loops will be kept so that the position of the loops will be remembered?

  What if I were to just write counterA = 0 and counterB = 0 without the global variable?  If I dont state them as global variable would the code not recognise the counterA = 0 and counterB = 0 ?

  Thanks for helping me so far, Im learning a lot ~ 
Im downloading Alice now and hopefully will try it soon :D

---

### Post by Lod on 2008-07-10
> **myromance123 said:**
> 
So, basically:
  Iteration = the action of the code being repeated
  Iterator = the item that keeps track of the number of repetitons ( the storage place )This is correct.

> 
Ooh, I think I understand now. If I did not put an iterator like counterA, then everytime I clicked characterA then clicked characterB then back to characterA, characterA would restart the loop and not continue from its last positon, but with an iterator it would remember where it was last time it was clicked, am I right?

[...]

 Not to sure I get the global variable. Is it basically stating that counterA = 0 and counterB = 0 are where the values for the loops will be kept so that the position of the loops will be remembered?

  What if I were to just write counterA = 0 and counterB = 0 without the global variable?  If I dont state them as global variable would the code not recognise the counterA = 0 and counterB = 0 ?

Almost there. 

- If you do not put an Iterator like CounterA in the code you would not be able to loop at all. So you need an iterator.

- If you use an iterator which is not global then the situation as quoted above will occur: every time you clicked on a different character and then back on A, A will restart the loop. Because your iterator only exist within the loop. As long as your in the loop you have an iterator. Exit the loop and the iterator is destroyed. Re-enter the loop and the iterator is newly created, starting with 0.

- Global iterators exists as long as the program itself is running. Therefore if you get out of loop A, the iterator (counterA) keeps on existing (until you close the program) and can remember it's current value.

The last two points isn't only true for iterators, it goes for all variables. It's called the 'scope' of an variable. If a variable (something to (temporarily) store values in) is defined within a function (say a loop) it's scope is local. The variable is only existing AND usable in that specific function. If you want to use the value somewhere else in the code it's not possible.
If the scope of the variable is global it's defined in the upper level of the programs' code. Every function/loop can access this variable (and change it).
Disclaimer: this is offcourse a very basic and generalized view on the term scope. But I think this way it's the easiest way to explain it.

---

### Post by Vendero on 2008-07-10
Ehm, as far as I'm concerned the for-loop is wrong.


You'll only need a main loop, which polls for events (the mouse being clicked).
When the mouse is clicked, you check which object has been clicked (A or B), then you increment the counter of that object *once*.
The method LOD suggested will start looping through all sounds when an object has been clicked.

This would resolve that problem:

```

CounterA = 0 //which clip should be played for A
CounterB = 0 //which clip should be played for B

//main loop:
function mainloop
  begin
  while true
    begin
    ClickFunction
    end
  end

function ClickFunction
  begin
  if MouseOnClick = A then AClicked
  else if MouseOnClick = B then BClicked
  end

function AClicked
  begin
  //first, play the correct sound
  if CounterA = 1 say SoundA1
  if CounterA = 2 say SoundA2
   ...
  if CounterA = 8 say SoundA8
  
  //then, increment CounterA
  CounterA = CounterA + 1
  
  //now, if CounterA = 9 (ie, the number of sounds you'll play)
  //reset the counter, you'll start playing Sound0 again.
  CounterA = 0 
  end

function BClicked
  //this function is the same as AClicked, just replace A by B in each line.

```

Notice that you'll be better of using arrays for the sounds, if you have a lot of sounds that'll reduce the huge block of 
```
if CounterX = N say SoundN
``` in your XClicked function to something of the form of 
```
Say SoundsX[CounterX]
```

You can also apply this array effect to the objects you have:
```

Array Counters //this will hold the counter for each object
Array Array Sounds //this is a matrix (a twodimensional array), with all the sounds of every object.

function Clicked(object)
  begin
  CurCounter = Counters[object] //what is the number of the next sound to play?
  CurSound = Sounds[object][CurCounter] //what is the next sound to play?
  
  say CurSound //play the sound
  
  //Increase the counter for this object, modulo the number of sounds for each object
  Counters[object] = (Counters[object] + 1) mod NSounds
  
  end

```

Don't worry if you don't understand the last chunck of code, once you master arrays you might want to check back on it though :)

---

### Post by Lod on 2008-07-10
> **Vendero said:**
> 
The method LOD suggested will start looping through all sounds when an object has been clicked.Nope, it wouldn't :).
 But it wasn't meant to be a working piece of code, just trying to give an, understable, example of a possible way to solve the problem.
If I really wrote this kind of crappy code I wouldn't be getting far in my current job. ;) . 
Although I'm not sure if I want to be a full-time hardcore programmer.

---

### Post by myromance123 on 2008-07-10
Ooh, so an iterator is needed for a loop to actually run.

   About the counters, what I understand now is that there are two ( basically ) different counters, namely global and local.

  Global is for the entire code to access and it is located above pretty much the whole code and local is only for a particular function in the code and it is actually written in that part of the code as well, very interesting, I know soo much more now, thank you very much Lod you have been a big help!

  Cheers ~   :guitar: 

  Holy Cow this thread went to 2 pages !! I didnt realise until just now..

Thanks as well vendero for contributinq to my learning experience :D

---

### Post by myromance123 on 2008-07-10
Ok, new question relating to what Vendero wrote ( I would have written this Q in the last post but I didnt realise the thread was 2 pages :)  )

  What is an array ?? And what do you mean by "polls for events"  ??
I also realised Vendero did not use the global variable for his code, why?

  Sorry one last question ( hopefully) what do the // stand for ?
      (Like I said im not language specific yet so I dont really get it~)

 Im studying what you posted now Vendero and Im trying to grasp it, so please be patient with me :D

  Thanks for the replies ~

---

### Post by pmasiar on 2008-07-10
> **myromance123 said:**
> 
  Iterator = the item that keeps track of the number of repetitons ( the storage place )


That would be counter (a variable). Iterator is a specific kind of object, you do not want to dive that deep yet. Counter might (and this kind of counter should) be a property of object, so each character has set of its own counters. But you learn that later, in Object-oriented programming. Learn basics first.

> Not to sure I get the global variable. 

a variable accessible from any part of the code

>  What is an array ?? 

You really should just get a book, any book, and read it. You want us to write a book for you, in random order as your questions arise. Author wrote a book in order how learning makes sense (not necessarily in order your curiosity fed by answers).

BTW wikipedia knows all answers to simple questions like you have. But book for beginners is even better.

> And what do you mean by "polls for events"  

Don't worry about events just now. Read basics (loops, functions, variables) first.

Python is excellent for beginners, and wiki in my sig has selected best free tutorials. I recommend "Python in 3 afternoons".

---

### Post by myromance123 on 2008-07-11
OK thanks, Im only putting my questions here because I have searched for hours for a book for beginner programmer basics, all I get though is nothing but language specific books(the basics they give are far beyond the understandable answers I get here).

  I'll try what you suggested, thanks ~

---

