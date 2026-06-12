---
title: "Need HELP with collision and scoring Again."
date: 2009-01-14
forum: Programming Talk
---

### Post by Waylon777 on 2009-01-14
Hi, I'm making a spaceship shooting game and I kind of got the collision part right but, still can't figure it out and the scoring either. For the collision, when the shots collides with one of the players, the player will blow up with the image explosion. For the scoring, it has to count how many kills, and if you kill the opponent 3 times, the game will post "Player!@#!@ wins!" with the applause music. Also it's a Ready To Program Java File.

---

### Post by sandyd on 2009-01-15
Bump!
Help him please!

---

### Post by bfhicks on 2009-01-15
I couldn't figure out how to run it, as you didn't provide a driver, and I'm not sure exactly what you are trying to do with the applets. Maybe this is just my lack of expertise using java. However, I have a few things that could help (I think).

Some notes:
_Player.java & Enemy.java_ are the exact same! You don't need them both, simply use only the Player.java class and keep an array of active players, or something to that extent.

The reason for doing this is upkeep of the code. For instance, inside your Enemy.java you have a 
**private boolean isDead = false;**
which is not inside the Player class. Shouldn't both be aware if they are alive or dead? I'm not sure how you want to keep track of that.

_Main.java_:
    public void init ()
    {
	setSize (winWidth, winHeight);
	//setSize (1440, 820);
	setBackground (Color.black);
	**player** = new Player (winWidth / 2, winHeight - playerH);
	enemy = new Enemy (winWidth / 2, enemyH + 20);
	setBackground (Color.black);
	**player **= new Player (720, 700);
	enemy = new Enemy (720, 120);

You are eliminating the initial player variable with the 2nd, is this something you want to do? Also, you set the background twice to the same exact thing...


It appears that you are using all rectangle 2d's for your graphics. So, you are trying to determine when they encounter each other. An easy way to do this is compare the corners with one rectangle to the other. If a rectangle has points within another, then you know they've collided.

If you provided me with a way to test this out, I could perhaps provide you with more insight.

---

### Post by Waylon777 on 2009-01-15
bfhicks, this program needs Ready To Program to run. You can find the Ready To Prgram in [http://compsci.ca/holtsoft/](http://compsci.ca/holtsoft/)

---

### Post by sandyd on 2009-01-15
your apparently supposed to run the program with ShootingSpaceship.html

---

### Post by sandyd on 2009-01-15
maybe this?

try using an IDE such as netbeans next time. instead of Ready To Java.  Its easier for other users to understand your code. 

and 1 more thing. don't forget to add comments. 

changes ive made....



if (shot.intersects (player)){
	imgPlayer = null;
	}
if (shot.intersects (enemy)) {
	imgEnemy = null;
	}
since i DON'T have ready to java, nor am i going to use it, i simply put that in Shot.java and hoped that it would work. you might have to make some edits to get this rolling	because of that.

---

