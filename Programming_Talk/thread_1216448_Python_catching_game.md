---
title: "Python catching game"
date: 2009-07-18
forum: Programming Talk
---

### Post by matmatmat on 2009-07-18
I have made the attached catching game in python

1) Does anyone know of any clip art I could use
2) Please can someone gave some improvements I could make

Thanks

---

### Post by smartbei on 2009-07-18
I think you forgot to attach.

---

### Post by matmatmat on 2009-07-18
Oops!

---

### Post by smartbei on 2009-07-18
Neat! Here are some ideas for improvements:
[list=1]
[*] Make the falling objects be transparent around the ellipse (use png images, or check out surface.set_colorkey)
[*] There are images falling slightly off the screen to the right, though they are still caught by the basket. (You are using randint(0, 640) which sets the top left pixel X position - how about randint(0, 640 - bomb.get_width()))
[*] I guess the code could be a bit more organized - The class could be called Bomb, the and the list bombs, rather than bombs and bombss :-)
[*] You could also use constants a bit more - there a lot of places where you use magic numbers in several different places. For example, the window size, the color white, etc.
[/list]

Nice anyway. As for clipart, you can search google images for what you want, along with the word 'clipart' and generally what you will find are sites offering free clipart.

---

### Post by matmatmat on 2009-07-18
Thanks!

---

### Post by Nevon on 2009-07-18
Been reading Beginning Python by Magnus Lie Hetland? :P 

Anyway, the basket should go on top of the balls, as they are supposed to fall into the basket. Also, you should probably make it so that the balls are caught as soon as they touch the top of the basket, rather than somewhere along the bottom/middle.

---

### Post by matmatmat on 2009-07-18
> **Nevon said:**
> Been reading Beginning Python by Magnus Lie Hetland? :P 

No

---

### Post by matmatmat on 2009-07-18
Does anyone have any ideas for simple games that I could do (about the same complexity as the attached game)

---

### Post by Nevon on 2009-07-18
> **matmatmat said:**
> No

No? I could swear there was a game almost exactly like this one in that book.

As for other game ideas, you could always make another breakout, pong or asteroids clone. That shouldn't be all that much harder than this game.

---

### Post by matmatmat on 2009-07-20
Ended up doing a game like [this]("http://www.miniclip.com/games/base-jumping/en/")

---

