---
title: "[SOLVED] Python help!"
date: 2008-08-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-05
In every game, where happens shooting, the shooting is like that you can shoot at any time you want, you know, you don't have to wait for the previous bullets to disappear. Its normal.

Always you press the shooting button, it creates new variables for each bullets. But I get no idea, how to keep creating new variables when the program is running, in any language.

I am trying to do this in python, but can you just tell me, how does the trick work? How to create new 'bullet' objects which all have their own identity and variables when pressing a button, for example?

Do you even get what I mean? Hope you do, because I can't speak english too well.

---

### Post by Zugzwang on 2008-08-05
You might want to look into some Python tutorial and keep an eye open on structures like the list. It allows you to put (almost) arbitrarily much data into the *same* variable and gives you the possibility to access *each* stored data item by its index. You don't create a variable for each new bullet. This is considered bad style in almost every language and in all commonly used languages and is even impossible in a lot of languages.

There are other types of containers, too.

---

### Post by days_of_ruin on 2008-08-05
Are you using pygame?
[http://www.linuxjournal.com/article/7694]("http://www.linuxjournal.com/article/7694")

---

### Post by crazyfuturamanoob on 2008-08-05
Thanks, list tells me a lot. But I have tried to search for those examples and tutorials, but found none. Also, what was that command in python that doesnt do anything but is needed sometimes?

---

### Post by Torajima on 2008-08-05
You might want to look into object oriented programming.

You could create bullet objects, and each object would have it's own stats (location, animation frame, speed, etc.)

If you're using Python, you should look into pygame or pyglet.

---

### Post by Wybiral on 2008-08-05
For this, you can use a list of the bullet objects, and append one for a shot, pop one off when the bullet is done.

---

### Post by fifth on 2008-08-05
> **crazyfuturamanoob said:**
> Also, what was that command in python that doesnt do anything but is needed sometimes?

The keyword is 'pass',ie
```

def myFunc(a,b):
   pass

```

---

### Post by crazyfuturamanoob on 2008-08-06
Ok, I can't remember names very well, so I just thank all posters.

I am currently not using pygame, since I make my python games for nokia's smartphones with PyS60.
But if pygame will be ported to PyS60 then I'll use it (thats not happening in long time).

Well, list sounds perfect solution for this, but you can't make more slots into the list while program is running, right?
Will I have to make a million empty slots which will never exeed or what do I do? 

"append" says index errors when trying to add to list that has too little slots. Or can I create new slots to lists? How?

And I found that "pass" with google before your post, but thanks anyway. :)

---

### Post by Torajima on 2008-08-06
Look into pyglet, as I believe it's pure python and can be distributed with your code.

Also, you should be able to add to an existing list by using append.

```
mylist = [1, 2, 3]

mylist.append(4)
```

mylist becomes [1, 2, 3, 4]

You could also do:

```
mylist += [5, 6, 7]
```

---

### Post by pmasiar on 2008-08-06
> **Torajima said:**
> Look into pyglet, as I believe it's pure python and can be distributed with your code.

Nothing at [http://www.pyglet.org/](http://www.pyglet.org/) website says it is pure Python - it just says it has no other external dependencies (just core). Quite a different thing. Why do you think it is pure Python? That would be awesome, but certainly they would brag about it?

---

### Post by Torajima on 2008-08-06
> **pmasiar said:**
> Nothing at [http://www.pyglet.org/](http://www.pyglet.org/) website says it is pure Python - it just says it has no other external dependencies (just core). Quite a different thing. Why do you think it is pure Python? That would be awesome, but certainly they would brag about it?

Oops, you're right. Still, with no external dependencies, I imagine it would be easier to make it work on a cellphone.

---

### Post by slavik on 2008-08-06
it is done by using dynamic memory allocation.

---

### Post by crazyfuturamanoob on 2008-08-07
The pyglet thing you have been talking about is completely useless. 
It's only for windows and mac. And I am too lazy and incapable to make pys60 version of it.
> **Torajima said:**
> Look into pyglet, as I believe it's pure python and can be distributed with your code.

Also, you should be able to add to an existing list by using append.

```
mylist = [1, 2, 3]

mylist.append(4)
```

mylist becomes [1, 2, 3, 4]

You could also do:

```
mylist += [5, 6, 7]
```
Wow! Thanks. But how do I remove the bullets that are done? That way my cellphone will run out of memory. :confused:

---

### Post by DaymItzJack on 2008-08-07
You can use list.pop(index) or list.remove(index)

>>> l = [1, 2, 3, 4]
>>> l.pop(0)
1
>>> l.pop()
4
>>> l
[2, 3]

---

### Post by samjh on 2008-08-07
> **slavik said:**
> it is done by using dynamic memory allocation.

No need to worry about that in Python. ;)

[quote=crazyfuturamanoob]In every game, where happens shooting, the shooting is like that you can shoot at any time you want, you know, you don't have to wait for the previous bullets to disappear. Its normal.

Always you press the shooting button, it creates new variables for each bullets. But I get no idea, how to keep creating new variables when the program is running, in any language.

I am trying to do this in python, but can you just tell me, how does the trick work? How to create new 'bullet' objects which all have their own identity and variables when pressing a button, for example?

Do you even get what I mean? Hope you do, because I can't speak english too well.[/quote]
Define a simple "bullet" object, and a list to store all the instances of bullet objects.

1. Every time you shoot, you create an instance of a bullet object and store it in the list.

2. When a bullet object's location is off-screen or hits something, you remove it from the list.

3. Loop through the list of bullets and draw whatever is in there onto the screen.

---

### Post by crazyfuturamanoob on 2008-08-08
> **samjh said:**
> 


Define a simple "bullet" object, and a list to store all the instances of bullet objects.

1. Every time you shoot, you create an instance of a bullet object and store it in the list.

2. When a bullet object's location is off-screen or hits something, you remove it from the list.

3. Loop through the list of bullets and draw whatever is in there onto the screen.

How does that part 3 work? Could somebody make and example for me?
I don't actually know how 'for' works. So if you'd make me as simple example as possible about 'for'?

Don't make it too complicated, instead of complicated keyboard checking events & objects, just type "if a key is pressed".

I know all other things needed but 'for'. And remember to include 1. and 2. into it, so I could understand it better.

---

### Post by DaymItzJack on 2008-08-10
```
bullets = []
# 3 bullets
bullets.append(class_bullet())
bullets.append(class_bullet())
bullets.append(class_bullet())

#I'm assuming you have a position (x, y) or something in the class
for bullet in bullets:
    whateveryouusetodraw.draw(bullet.x, bullet.y)
```

Of course this is a rough code since I'm not entirely sure what you are using.

---

### Post by samjh on 2008-08-10
> **crazyfuturamanoob said:**
> How does that part 3 work? Could somebody make and example for me?
I don't actually know how 'for' works. So if you'd make me as simple example as possible about 'for'?

Don't make it too complicated, instead of complicated keyboard checking events & objects, just type "if a key is pressed".

I know all other things needed but 'for'. And remember to include 1. and 2. into it, so I could understand it better.

You'll need to specify a class of objects for bullets.  Let's call it "Bullet":
```
class Bullet:
    def __init__(self, xpos, ypos, visible):
        x = xpos
        y = ypos
        visible = True
```So a Bullet object has attributes x and y, x being the x co-ordinate position of the object, and y being the y co-ordinate position.  The visible attribute is set to True if the bullet should appear on screen, and False if it shouldn't.

When a player presses a key to "fire" (I will pretend the SPACE key does this), you create a Bullet object and add it to a list of bullets.  A bullet will initially be placed at the same location as the player (ie. xplayer, yplayer), and you'll presumably have some code elsewhere to update the positions of each bullet to make them move:
```
bulletlist = []

... blah blah blah...

if keypressed == SPACE then:
    newbullet = Bullet(xplayer, yplayer)
    bulletlist.append(newbullet)

... blah blah blah...
```

At some time, bullets will leave the screen or hit an object, so they no longer need to be displayed.  So then, you mark such bullets as invisible by setting the visible attribute for them as False.  I will assume that you have some code elsewhere to detect when things have collided or gone off-screen.  Now you need to draw the bullets that are still visible, and get rid of the ones that aren't:

```
for abullet in bulletlist:
    if abullet.visible == True:
        drawsomething(abullet)
    else:
        bulletlist.remove(abullet)
```

The code above won't work by themselves, obviously.  But I'm trying to give you a general idea on how this can be done in the simplest manner I can think of.  There are alternative methods which are both more efficient and more complex. :)

---

### Post by crazyfuturamanoob on 2008-08-10
OK, I got it. Thanks. :)

---

### Post by Lux Perpetua on 2008-08-10
> **crazyfuturamanoob said:**
> In every game, where happens shooting, the shooting is like that you can shoot at any time you want, you know, you don't have to wait for the previous bullets to disappear. Its normal.Which games do you have in mind? In most games I've played that involve shooting, you can't have more than two or three shots on screen at once. (Not to diminish your goal, though; I've always found it a bit annoying, personally.)

---

### Post by samjh on 2008-08-10
> **Lux Perpetua said:**
> Which games do you have in mind? In most games I've played that involve shooting, you can't have more than two or three shots on screen at once. (Not to diminish your goal, though; I've always found it a bit annoying, personally.)

When was the last time you played space invaders? ;)  I used to just hold down the fire key and unleash dozens of laser/phaser/plasma/bolts/bullets on the screen.  Spray-and-pray FTW! :p

---

