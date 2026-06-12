---
title: "How do you use SDL C++ headers to activate a function with the mouse?"
date: 2011-10-31
forum: Programming Talk
---

### Post by iamanidiot123 on 2011-10-31
To be specific: I want to use some SDL headers in C++.  I would like a certain bit of code (not necessarily a function)to be activated when the right mouse button is down, and then deactivate it when it is up.  How would I do this?  (sorry if the question is dumb, i am just learning C++ and making something for an excersize)
For those who are curious, here is the bit of code I am talking about:
```
if(difficulty <= 2)
{
    getpos(player1,targetplayer,xpos,ypos);
    player1.yaw = ypos;
    player1.pitch = xpos;
}

```
(yes, I am making a tiny game)

---

### Post by 11jmb on 2011-10-31
[http://www.libsdl.org/intro.en/usingevents.html](http://www.libsdl.org/intro.en/usingevents.html)

Do you want the pitch&yaw to update whenever the mouse button is down? if that is the case, you will also need to handle mouse motion events.

---

### Post by iamanidiot123 on 2011-10-31
> **11jmb said:**
> [http://www.libsdl.org/intro.en/usingevents.html](http://www.libsdl.org/intro.en/usingevents.html)

Do you want the pitch&yaw to update whenever the mouse button is down? if that is the case, you will also need to handle mouse motion events.

Hey, thanks for the quick reply.
The instructions in the link don't really work with what I am trying to do; the whole thing executes every frame (at something like a 30 fps rate).  So I can't do a wait for event.  What is polling for events?

---

### Post by DarkAmbient on 2011-11-01
Not sure it this is related to your problem. But I recall that the events only register the click/release itself. So if you like to keep track on for how long the button is down, you need a bool that sets to true/false on button down/up.

This site has both good basic and more advanced tutorials on C++, SDL and general gamedesign.
[http://www.sdltutorials.com/](http://www.sdltutorials.com/)

---

### Post by 11jmb on 2011-11-01
Polling is going to constantly check for events and load them into the event queue to be processed. This is asynchronous, but you can use a timer if you are 100% sure that you would like to check for events at regular intervals.

[http://www.libsdl.org/intro.en/usingtimers.html](http://www.libsdl.org/intro.en/usingtimers.html)

EDIT: I should note that using timers is a bit more difficult than event polling but may be a bit more time-efficient (i'm not 100% on this though)

---

### Post by 11jmb on 2011-11-01
> **DarkAmbient said:**
> Not sure it this is related to your problem. But I recall that the events only register the click/release itself. So if you like to keep track on for how long the button is down, you need a bool that sets to true/false on button down/up.

This site has both good basic and more advanced tutorials on C++, SDL and general gamedesign.
[http://www.sdltutorials.com/](http://www.sdltutorials.com/)

+1

I just went through the first few pages of these tutorials, and they are excellent. It may be worth your time to put your game on hold and work through these (at least up to the tic-tac-toe example). This may give you a better idea of how to approach your game.

---

### Post by iamanidiot123 on 2011-11-01
Thanks all for the replys.

I forgot to make something clear: the snippet I gave you is in a function that is essential for rendering the Heads-Up Display and therefore is executed every frame, so nothing can delay the function from finishing.  Otherwise alot of things will be messed up.
However your replies are very useful, I will try experimenting with them. /close

---

