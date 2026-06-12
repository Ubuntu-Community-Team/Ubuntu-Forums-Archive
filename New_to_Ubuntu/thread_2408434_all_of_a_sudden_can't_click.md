---
title: "all of a sudden can't click"
date: 2018-12-18
forum: New to Ubuntu
---

### Post by alex526 on 2018-12-18
howdy  (potential fix at end)

i had unplugged my newly installed ubuntu laptop for the first time. i was looking at firefox and marvelling at my i7 8 thread processor running at a constant 10-20% in the resource tab. i was wondering why resource use was so high so i switch to process view. i see no details. nothing adds up to 10-20%. just 2 processes all 1-2%.

anyways. as i was investigating, click input all of a sudden stopped. no warning no message just no more clicks. i can't click on the touch screen, the  touch pad, i even plugged in a mouse that could move on the screen but couldn't click. 

is this a thing? is this likely to happen on some hardware? is this how linux behave when an app breaks in background? idk... can someone mention please if you've seen this before, if it's bizzarre like i think it is and any insight at all would be appreciated. 
. 
the prudent thing might just be to sit tight and see if it happens again.

i've noticed this problem has been reported earlier this year by folks on another website. this problem goes back at least a year for some people. a suggested fix is to switch into and out of virtual desktop ctrl+alt+f1 and ctrl+alt+f2 to come back. i haven't tried this but is possible solution if others have this problem.

---

### Post by CatKiller on 2018-12-18
It is a thing that can happen. It isn't common.

Communication between the window manager and the display server has become interrupted - possibly because of some confusion within the window manager.

It's likely to be transient. It should be fine after a restart. If it keeps happening we can start troubleshooting to find the cause.

---

### Post by alex526 on 2018-12-18
while i've got you on the line, is it possible to investigate touch issues? it appears some of the gestures work but others don't. the on-screen keyboard is much too slow to be use-able. does this mean i am unlucky and stuck at this level of touch-screen compatibility? are there drivers i can download to improve the situation like we sometimes do with the graphics cards?

i'm not largely concerned about these features but they would be nice to have for completeness since the laptop was designed to use them. rotation works ok.

thanks for your help

---

### Post by CatKiller on 2018-12-18
I've not really done much with touch. My laptop has a touch screen, and it worked out of the box for clicking on stuff, so I never investigated further.

It's unlikely that a driver would be necessary: those things tend to be done through some kind of open framework. You either get a signal or you don't, and the difficult part is interpreting them. I don't know the state of play, though, because I've not looked into it.

I believe there's a widget for gesture control for trackpads. That might feasibly apply to touch screens too. I'm on my phone rather than my laptop, so I can't investigate.

---

### Post by alex526 on 2018-12-18
thanks. you've been helpful with the insights. i will post the widget name if i find it.

---

