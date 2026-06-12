---
title: "Terminal window size"
date: 2016-01-15
forum: Programming Talk
---

### Post by Matthew_Harrop on 2016-01-15
Hi all, Its been a while since I've been around (Work has been really  busy) so I thought I'd say hello and post an interesting question for us  to consider (Or one I consider interesting anyway)

**The Question:**
Can you modify the size of the terminal window, a program launches in,  at run time to ensure that the window is always the size of the screen  without the use of xterm or other window manager?

**The Background:**
So I've recently been working on a little side project to help me keep  track of some documents at work - It will create little packs, stick  them in a database with a time and date stamp and then i can modify them  easily without having to retrieve the files and do the pack again. 

I've chosen to create this as a terminal (bash) application in C++ using  xcode on my Mac (Yes, i know, Its just what I've got). I figured it  would be a good way for me to dust off some rusty skills and create  something that was a throw back to the old programs i used to use as a  kid (The old file managers on windows 3.1 for example)

I chose to use ncurses since its lightweight and will run without much  hassle, and have all that I want to do planned out in my head - sql, zip  manager ect. However I have run into a basic problem: The size of the  Terminal Window!

I have conducted a fair amount of research on the interwebs and I have  found most people claiming that its not really possible to modify the  size of the TW (Terminal window) at run time (Probably because the  program has no understanding of the TW its running in, it just runs and  can request details of its environment but not modify them) 

Most people say that its just easier to have the program say: "This will  not run without the TW being at least XXX by YYY, please resize the  window now" and then handling the SIGWINCH with an event handler on a  separate thread. That's all well and good, but I feel that it can be  handled with a little more grace. So what I put forth are these:

[B]Idea 1: Have the program launch another TW that is the size of the host screen

[/B]Write into the very beginning of the program a small function  that asks to create a new window of size _DISPLAYWIDTH and  _DISPLAYHEIGHT and run all of the program within that

[B]Idea 2: Have the program resize the TW
[/B]
Give the program the ability to resize the launch TW to be the _DISPLAYWIDTH and _DISPLAYHEIGHT size

[B]Idea 3: Accept defeat and use something else

[/B]Never give up, Never surrender! 

So what are your thoughts on this then? All ideas are welcome, no matter how silly :smile:

---

