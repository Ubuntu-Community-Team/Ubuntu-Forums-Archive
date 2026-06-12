---
title: "XServer Input Interruption &amp; Processing"
date: 2011-03-03
forum: Programming Talk
---

### Post by xorgsApprentice on 2011-03-03
Hello everyone, 

I'm currently working with touchscreens and advanced control elements, with an included xorg implementation. 
This requires me to f.e. catch a mouse event / touch event, interrupt it, process some information, and based on that information, send a different signal to the XServer. 

For example, tapping the screen twice in a specific motion translates to a right click mouse event. 

My problem is, that I am fairly new to X and that I have been stalking tutorials and forums for the past four days without tripping over a solution. 

Could somebody point me in the right direction? 

In short, I need:
capability to interrupt input signals, such as mouse clicks completely until I did some processing on other stuff. 
once that is done, I want to resubmit the signal, or depending on new information, even send a different signal, such as right mouse click instead of left. 

I hope that someone here is willing to help me with this. 

Thanks for your time ppl!

---

