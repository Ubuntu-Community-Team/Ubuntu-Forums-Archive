---
title: "Can this autohotkey script be replaced by something available in linux"
date: 2019-09-11
forum: Programming Talk
---

### Post by kaladar2 on 2019-09-11
I have been using autohotkey on windows and it is stopping me from moving back to linux.

I have bad wrists and needed some quick keys to minimize traversal on the keyboard a few years back I couldn't figure out how to make this work on linux. So I started using AHK on windows to bind the ON state of capslock to create multiple shortcuts.
These shortcuts are a true life saver for me and work in any application. 

Example script. If capslock is toggled and I press S it triggers left arrow keypress. If I press W while capslock is toggled it triggers control+w keystroke.
This is just a tiny sample, but if it's possible under linux I could finish the rest of my script.

#if GetKeyState("Capslock", "T")
{
    S::Send {Left}   
    W::Send ^w
}

---

