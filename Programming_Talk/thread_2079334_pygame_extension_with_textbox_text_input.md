---
title: "pygame extension with textbox? text input"
date: 2012-11-01
forum: Programming Talk
---

### Post by snowlizard31 on 2012-11-01
I'm making an app to help me learn kanji and I need a textbox to let the user try to guess the kanji but pygame doesn't have a textbox module? does anyone know if theres an extension for this?

---

### Post by MG&amp;TL on 2012-11-01
Not to my knowledge. If you want a GUI toolkit, use a GUI toolkit.

However, if it's a one-off, just take keyboard input: [http://www.pygame.org/docs/ref/key.htm]("http://www.pygame.org/docs/ref/key.html")l

...and draw your own "text box". :)
[]("http://www.pygame.org/docs/ref/key.html")

---

### Post by snowlizard31 on 2012-11-01
oh well are there any tutorial out there that lead up to making textboxes and widgets with python for pygame?

---

### Post by MG&amp;TL on 2012-11-01
> **snowlizard31 said:**
> oh well are there any tutorial out there that lead up to making textboxes and widgets with python for pygame?

Ah right. I can't find any, but should be pretty simple:

1) Draw an image on your screen where you want your textbox to be. My guess is you want an image of a textbox. :)

2) Take keyboard input into a string buffer...do all of that stuff.

3) As you continuously draw, render the buffer as text over the input box image.

That should do what you want.

---

### Post by snowlizard31 on 2012-11-01
To be honest I'm still a noob so I don't really don't know where to start. Its probably to much to ask you to go into details because its seems there'd be a lot of code involving the creation of a textbox for input. Do you know of any tutorials so I can gain the experience to eventually make a textbox?

---

### Post by MG&amp;TL on 2012-11-01
This is a good place to start: [http://www.pygame.org/wiki/tutorials](http://www.pygame.org/wiki/tutorials)

How good are you with python? It's probably worth learning at least a bit of that before moving on to more complex things.

Don't worry about it anyway, you'll be zipping around pygame in no time.

---

### Post by snowlizard31 on 2012-11-01
Ah Thanks those tutorials will really help! I've finish zed shaws' python book, and some other tutorials but I'd have to say I still feel like a noob.

---

### Post by MG&amp;TL on 2012-11-01
> **snowlizard31 said:**
> Ah Thanks those tutorials will really help! I've finish zed shaws' python book, and some other tutorials but I'd have to say I still feel like a noob.

Excellent book, you'll be fine if you've finished that. :)

The "feeling like a noob" thing is common, you'll get over it sooner or later when you make something impressive. Better than "I'm so awesome." ...and then failing miserably.

---

### Post by snowlizard31 on 2012-11-01
haha Thanks for the help ;D

---

### Post by Tony Flury on 2012-11-02
There are a couple of GUI toolkits suggested on the pygame web site : 

[http://www.pygame.org/wiki/gui](http://www.pygame.org/wiki/gui)

---

