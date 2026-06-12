---
title: "[SOLVED] I need ASCII numbers for keyboard buttons"
date: 2008-10-29
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-29
I want ASCII numbers for keyboard buttons, but I ain't got an idea where I might get them.

*Would you kindly* post me a list of them? Thanks.

---

### Post by slavik on 2008-10-29
What do you need this for?

Keyboard drivers may (and sometimes will) change the value your app sees from the keyboard ...

---

### Post by crazyfuturamanoob on 2008-10-29
> **slavik said:**
> What do you need this for?

Keyboard drivers may (and sometimes will) change the value your app sees from the keyboard ...

I'd use those ascii numbers with glut to check if keys are being pressed.

---

### Post by slavik on 2008-10-29
> **crazyfuturamanoob said:**
> I'd use those ascii numbers with glut to check if keys are being pressed.
have you tried reading glut documentation or tutorials???

usually, the letter keys correspond to the letter's ASCII code ... and google has THAT chart. for arrow keys and such, read the glut docs.

---

### Post by crazyfuturamanoob on 2008-10-29
I checked the glut reference manual and found no ascii characters there.

How to get them then? Should I write a simple app that tells the ascii code of every button when I press them?

---

### Post by slavik on 2008-10-29
go to Level2 of the documentation ... the source code ...

---

### Post by crazyfuturamanoob on 2008-10-29
What is level2? Where is it? Can't find it. Looked from here:
[http://www.opengl.org/documentation/specs/glut/spec3/node1.html](http://www.opengl.org/documentation/specs/glut/spec3/node1.html)

Also, I already started pressing the buttons and writing the numbers up.

---

### Post by slavik on 2008-10-29
you missed the part that says "the source code ..."

---

### Post by crazyfuturamanoob on 2008-10-29
Could you give me a link?

Got bored of getting the numbers manually.

---

### Post by slavik on 2008-10-29
look in the include file and follow it to the definitions of the keys ...

DIG!!!

---

### Post by Rhubarb on 2008-10-29
Not sure if this is what you're after, but:
open up a terminal, and run this:
```
xev
```
Now press a button on your keyboard (or mouse), and you get a nice hex / decimal value of the key you press.  I'm not sure if this is the ascii value or not.

---

### Post by slavik on 2008-10-29
> **Rhubarb said:**
> Not sure if this is what you're after, but:
open up a terminal, and run this:
```
xev
```
Now press a button on your keyboard (or mouse), and you get a nice hex / decimal value of the key you press.  I'm not sure if this is the ascii value or not.
he's using glut ... so glut might be changing things around ... that's a better way other than rolling your own.

---

### Post by crazyfuturamanoob on 2008-10-29
What is include file?

---

### Post by slavik on 2008-10-29
please read a proper C tutorial/book. The C Programming Language 2nd ed. by K&R is nice. :)

---

### Post by crazyfuturamanoob on 2008-10-29
Whatever.. :roll:

---

### Post by rnodal on 2008-10-29
> **crazyfuturamanoob said:**
> Whatever.. :roll:

If you are not willing to do the work for yourself then don't bother asking for help. No one here will do it for you. [http://www.lighthouse3d.com/opengl/glut/index.php?5]("http://www.lighthouse3d.com/opengl/glut/index.php?5")

-r

---

### Post by crazyfuturamanoob on 2008-10-29
If there's no way to get full list of keyboard button ascii codes, then I'll test each key manually when I need to use a specific button.

---

### Post by LaRoza on 2008-10-29
> **crazyfuturamanoob said:**
> If there's no way to get full list of keyboard button ascii codes, then I'll test each key manually when I need to use a specific button.

There is a way, get a list of the ascii codes ;)

---

### Post by crazyfuturamanoob on 2008-10-30
Keyboard asciis are same than letter asciis? I thought they were different.. :)

Found a nice table for them. 
[http://enteos2.area.trieste.it/russo/IntroInfo2001-2002/CorsoRetiGomezel/ASCII-EBIC_files/ascii_table.jpg](http://enteos2.area.trieste.it/russo/IntroInfo2001-2002/CorsoRetiGomezel/ASCII-EBIC_files/ascii_table.jpg)
And dec section equals the buttons.

---

### Post by slavik on 2008-10-30
> **crazyfuturamanoob said:**
> Keyboard asciis are same than letter asciis? I thought they were different.. :)

Found a nice table for them. 
[http://enteos2.area.trieste.it/russo/IntroInfo2001-2002/CorsoRetiGomezel/ASCII-EBIC_files/ascii_table.jpg](http://enteos2.area.trieste.it/russo/IntroInfo2001-2002/CorsoRetiGomezel/ASCII-EBIC_files/ascii_table.jpg)
And dec section equals the buttons.
not always, it depends on the library you are using (and maybe the driver)

---

### Post by stylishpants on 2008-10-30
These are also available in a man page. 

"man ascii" to see the table.

---

### Post by crazyfuturamanoob on 2008-10-30
> **slavik said:**
> not always, it depends on the library you are using (and maybe the driver)

For my library, for my keyboard, and for my drivers those ascii codes are OK. I tested them.

---

