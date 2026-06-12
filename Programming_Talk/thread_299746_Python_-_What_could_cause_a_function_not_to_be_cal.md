---
title: "Python - What could cause a function not to be called?"
date: 2006-11-14
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-14
Hey all

For some time now I have been writing a text based rpg. Everything has been going great until now. I have a major problem. Basically You can access the inventory from inside a battle or outside it. Here is an example of the testing session.

1) Start game
2) Create char
3) Look in inventory out of battle => Success
4) Begin battle
5) Look in inventory in battle => Success
6) Kill enemy using melee ONLY
7) Look in inventory out of battle => Success
8) Begin battle
9) Look in inventory in battle => Success
10) Kill enemy with spells
11) Look in inventory out of battle => Failure

I put a few prints in before I call the inventory function and they print on the failed one but the very first line of the inventory (print "TEST") does not execute. It looks as though the spellcast function stops the inventory function from ever being called again. What could cause this. I could post the code but there is an awful lot of it and I don't know what would be relevant.

The basic structure of the battle system goes like this

Main Menu
  |
  -> Battle
       |
       -> Attack
       |
       -> Cast
       |
       -> Inventory
  |
  -> Inventory

When the battle is over it goes back to the main menu. So does the Inventory.

If anyone can give me anything that may help fix this that would be great.

Thanks

Ironfistchamp

---

### Post by po0f on 2006-11-14
ironfistchamp,

Is the battle run inside its own function separate from the main loop?  Without any example code, it's kinda hard to diagnose.

---

### Post by cwaldbieser on 2006-11-14
> **ironfistchamp said:**
> Hey all

For some time now I have been writing a text based rpg. Everything has been going great until now. I have a major problem. Basically You can access the inventory from inside a battle or outside it. Here is an example of the testing session.

1) Start game
2) Create char
3) Look in inventory out of battle => Success
4) Begin battle
5) Look in inventory in battle => Success
6) Kill enemy using melee ONLY
7) Look in inventory out of battle => Success
8) Begin battle
9) Look in inventory in battle => Success
10) Kill enemy with spells
11) Look in inventory out of battle => Failure

I put a few prints in before I call the inventory function and they print on the failed one but the very first line of the inventory (print "TEST") does not execute. It looks as though the spellcast function stops the inventory function from ever being called again. What could cause this. I could post the code but there is an awful lot of it and I don't know what would be relevant.

The basic structure of the battle system goes like this

Main Menu
  |
  -> Battle
       |
       -> Attack
       |
       -> Cast
       |
       -> Inventory
  |
  -> Inventory

When the battle is over it goes back to the main menu. So does the Inventory.

If anyone can give me anything that may help fix this that would be great.

Thanks

Ironfistchamp

Something silly I do every once in a while is to "def" the same function twice.  Then I scratch my head for a while when I call it but it doesn't seem to work the way I thought.  E.g.
```

def foo():
  print "This is Foo!"

...

def foo():
  print "This is Foo, too!"

...

foo() #Prints, "This is Foo, too!"

```

---

### Post by ironfistchamp on 2006-11-15
This is weird. Now that I have sent the code to another computer (to work on at college) I can't even use any items. Using an item in battle will break it in the same way that spell casting does.

I have changed the way it works too many times. I am just going to re write the whole battle module. At least I will still have all the basics fresh in my head.

Thanks for the replies people. Once I have a working battle module working I am going to tar it and let people download if they feel like it. It is going to turn into a game with a story but the first one will just be that battling.

Thanks again

Ironfistchamp

---

### Post by dwblas on 2006-11-15
It's almost impossible to figure out what is going on without any code.  My first thought was that you were running out of memory because of redundancy but that probably isn't the problem, i.e. Kill The Enemy calls Look in Inventory calls Kill The Enemy calls Look in Inventory calls Kill The Enemy 

instead of Kill the Enemy --> exit to control loop
control loop calls Look In Inventory --> exit to control loop, etc.
Keep it up though.  This is a good way to stretch the mind.

---

### Post by ironfistchamp on 2006-11-15
Well thanks for the replies. I finally got it. what was happening was that when the Inventory func was called it checked to see if there was a key monst["hp"]. If there was and it was 0 or less then it would not continue. Because I had killed the enemy and not generated a new one it was still 0 so it would never continue. Thats why if I got into another fight and fled it would work again.

I have made more use of functions and now things really seem to be working.

The only real pain I have with this is that I can't figure out Curses, Urwid or PyGTK(which would really help with the UI). Currently the UI looks very primitive and is best played at full screen or maximized. I have never tried playing it from a TTY (if thats what it's called).

If anyone wants to have a look at it just PM me and I can send it to you.

Catch y'all later

Ironfistchamp

---

### Post by cwaldbieser on 2006-11-15
> **ironfistchamp said:**
> Well thanks for the replies. I finally got it. what was happening was that when the Inventory func was called it checked to see if there was a key monst["hp"]. If there was and it was 0 or less then it would not continue. Because I had killed the enemy and not generated a new one it was still 0 so it would never continue. Thats why if I got into another fight and fled it would work again.

I have made more use of functions and now things really seem to be working.

The only real pain I have with this is that I can't figure out Curses, Urwid or PyGTK(which would really help with the UI). Currently the UI looks very primitive and is best played at full screen or maximized. I have never tried playing it from a TTY (if thats what it's called).

If anyone wants to have a look at it just PM me and I can send it to you.

Catch y'all later

Ironfistchamp

If you haven't already, you might consider setting up a CVS or SVN repository, even if it is just for your own personal use.  I find that it is a great time saver, because I get interrupted in the middle of my work all the time.  Because I commit my changes regularly, though, I can look up and see what I last did, diff local changes to see what I was doing, etc.  If I want to try out something I am not sure will work out, I can always revert it, too.  I wish I had learned about version control back in my early days of programming.  I can't tell you how many programs I must have re-written because I wasn't able to remember what I had changed.

---

### Post by ironfistchamp on 2006-11-16
Thanks I shall check that out. I have never really heard much about SVN or CVS. I have downloaded latest builds of apps from it but never thought about using it myself.

Thanks again


Ironfistchamp

---

