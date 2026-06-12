---
title: "Best program for a beginner Hidden Object Game"
date: 2013-03-20
forum: Programming Talk
---

### Post by deanwell13 on 2013-03-20
Hello everyone and thankyou for looking at my question.
I have absolutely no experience in making games at all and have never used a program language but it something i am very interested in.
I have had an idea, mainly for friends and family who like Hidden Object Games that i would like to try and make.

It would be a story based HOG where the player would have to complete a 'level' to proceed to the next scene.
I am not afraid of hard work or learning a programming language for this, but with so many about nowadays i dont know which one to choose.
I would probably like this to be available to play on Ipad, but more importantly just on a laptop would probably be more realistic.


I dont really know what else to add, so i hope somebody can help me with this.


Again, thankyou for reading.

---

### Post by Tony Flury on 2013-03-21
> **deanwell13 said:**
> Hello everyone and thankyou for looking at my question.
I have absolutely no experience in making games at all and have never used a program language but it something i am very interested in.
I have had an idea, mainly for friends and family who like Hidden Object Games that i would like to try and make.

It would be a story based HOG where the player would have to complete a 'level' to proceed to the next scene.
I am not afraid of hard work or learning a programming language for this, but with so many about nowadays i dont know which one to choose.
I would probably like this to be available to play on Ipad, but more importantly just on a laptop would probably be more realistic.


I dont really know what else to add, so i hope somebody can help me with this.


Again, thankyou for reading.

With something like this - were you don't need fast processing of vast amounts of data, then you could well find that Puthon (with pygame) would be a great combination - however the big challenge is going to be the graphics - Hidden object games are not challenging programming challenges - the basic logic is not overly compex :

Psuedo code
```

Load background image for this level
Load hidden object data for this level
Display background and objects
while not all objects found 
     let user click on image
     if user click on object 
        remove object from display
        increase user score

```

The challenge is in the graphics and making sure the objects are actually hidden.

---

