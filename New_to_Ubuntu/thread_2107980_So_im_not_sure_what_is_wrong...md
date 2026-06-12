---
title: "So im not sure what is wrong.."
date: 2013-01-23
forum: New to Ubuntu
---

### Post by KhaoticLogic on 2013-01-23
For the past two days, every couple of hrs, my screen will black out, and then display a lot of error text. I tried to take a printscreen of it but it wouldnt capture it.the screen behind it, youtube facebook that sort of thing, i can still interact with, and thats what my printscreen captured. How would i go about diagnoseing this? any thoughts on what i might have broken, and need to update? 

recently pulled down openjdk6, but i dont know if thats the issue or not

thanks yal in advance

---

### Post by von Corax on 2013-01-23
A few questions to help narrow down the problem:

What version of Ubuntu?

Can you provide a sample of the error text? (I get that you can't take a screen-cap, but could you write some of it down, then post it?)

Do you remember what you were doing just before all this began?

---

### Post by audiomick on 2013-01-23
> **von Corax said:**
> but could you write some of it down, then post it?)

Or take a photo of it an post that. 

That fact that a screenshot shows what would have been on the screen if the problem hadn't shown up seems to me to indicate a problem with the graphics card. No idea what it could be though...

---

### Post by Thee on 2013-01-24
What graphics card are you using? Is the fan on the graphics card dusty? Does it spin? What cable are you using to connect the graphics card to your monitor? VGA, DVI, HDMI? Does this happen only in Ubuntu?

---

### Post by von Corax on 2013-01-24
I'm actually suspicious that the machine is writing console messages to one of the alternate TTY screens. Knowing what the messages say would help pin this down.

---

### Post by audiomick on 2013-01-24
> **von Corax said:**
> I'm actually suspicious that the machine is writing console messages to one of the alternate TTY screens.

That would mean that the TTY involved is "hijacking" the video card from the logged on user. Is that likely? I expect it is technically not impossible, but it would indicate something very odd is happening in the system... :-k


>  Knowing what the messages say would help pin this down.

Yes, indeed.

---

