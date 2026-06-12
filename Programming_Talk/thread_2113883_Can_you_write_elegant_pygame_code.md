---
title: "Can you write elegant pygame code?"
date: 2013-02-08
forum: Programming Talk
---

### Post by lykwydchykyn on 2013-02-08
Hello all.

I've been on bedrest all week due to pneumonia, and once I got over hacking up my lungs I decided to get a better handle on pygame to pass the time.

I've watched numerous tutorials on youtube and commandeered my son's copy of "Making Games with Python & Pygame".  So far, though, all the example code I can find seems really inelegant and would be difficult to scale up to a "real game".  It seems to be rife with global variables, and the event handling given in all examples is a big nasty if/elif tree inside an infinite loop.  There seems to be a whole lot of low-level and boilerplate code to do simple things (like detect collisions or do animations).

Anyway, I'm either doing it wrong or pygame is just not what it's cracked up to be.  Anyone have any advice on this?  What am I missing?

---

### Post by oleink on 2013-02-08
> **lykwydchykyn said:**
> Hello all.

I've been on bedrest all week due to pneumonia, and once I got over hacking up my lungs I decided to get a better handle on pygame to pass the time.

I've watched numerous tutorials on youtube and commandeered my son's copy of "Making Games with Python & Pygame".  So far, though, all the example code I can find seems really inelegant and would be difficult to scale up to a "real game".  It seems to be rife with global variables, and the event handling given in all examples is a big nasty if/elif tree inside an infinite loop.  There seems to be a whole lot of low-level and boilerplate code to do simple things (like detect collisions or do animations).

Anyway, I'm either doing it wrong or pygame is just not what it's cracked up to be.  Anyone have any advice on this?  What am I missing?

Hey.  Try taking a look at "stacked python" programming language.  It is python for game development.  It was used as the core of Eve Online.  I'm no game programmer so I cannot exactly explain how it works but it looks to be a very efficient way to code games

---

### Post by Tony Flury on 2013-02-11
> **lykwydchykyn said:**
> Hello all.

I've been on bedrest all week due to pneumonia, and once I got over hacking up my lungs I decided to get a better handle on pygame to pass the time.

I do hope you are feeling much better

> 
I've watched numerous tutorials on youtube and commandeered my son's copy of "Making Games with Python & Pygame".  So far, though, all the example code I can find seems really inelegant and would be difficult to scale up to a "real game".  It seems to be rife with global variables,

In python it is always possible to replace global variables with singleton class instances (for example). My only complete game todate (a snake game) does this.

> 
 and the event handling given in all examples is a big nasty if/elif tree inside an infinite loop.  

No reason in Python why big if/elif trees can't be replaced by a very elegant and pythonic dictionaries - where the key is the event and the value is the method to be called. The event handling becomes a very simple : 
```

eventDefinitions[key](arguments)

```

> 
There seems to be a whole lot of low-level and boilerplate code to do simple things (like detect collisions or do animations).

pygame is low level - and you have to do a lot, but why not wrap your common code into some sub-classes. For instance I have a sub class which mimics a sprite class but manages my animations - including different animations for different states - it is buggy so i wont share it, but essentially I can instatiate an animated sprite class, load it with known file of animation cells, tell it which sequence of cells apply to which state and at what cell rate etc. All my application has to do is change the state of my animated sprite as appropriate, and call "tick" once each update. And because it is a module in it's own right I can re-use it, and because it a sub-class of sprite, I can use it where-ever I would want to use the sprite class.

---

### Post by lykwydchykyn on 2013-02-11
Thanks for the reply tony; I've been looking some at the code of Solarwolf too for some ideas.

I guess what I really want to see is event handling moved into the objects themselves.  I suppose there's got to be a clever way to do that, but my brain is still not all there from the cough meds.

---

### Post by Tony Flury on 2013-02-12
> **lykwydchykyn said:**
> Thanks for the reply tony; I've been looking some at the code of Solarwolf too for some ideas.

I guess what I really want to see is event handling moved into the objects themselves.  I suppose there's got to be a clever way to do that, but my brain is still not all there from the cough meds.

There is nothing clever about classes and objects - if you have an object which you want to do event handling (for instance a sprite object), then create a sub class of sprite which does the event handling - and all that your main loop has do to is call a method on your sprite sub-class

---

