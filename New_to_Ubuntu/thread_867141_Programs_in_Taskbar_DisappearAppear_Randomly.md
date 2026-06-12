---
title: "Programs in Taskbar Disappear/Appear Randomly"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by XCan on 2008-07-22
I've run into a minor annoyance using Ubuntu. It seems like the programs I have open sometimes dissappear from the taskbar, at the same time disappeared programs reappear randomly. 

It also seems like programs open in one desktop sometimes also appear on the taskbars of other desktops. If I try to click it, ubuntu automatically jump to the correct 'home desktop'.

A program I've noticed to disappear/reappear as described above _a lot_ is Matlab. While Open Office seems to 'jump around' _a lot_.

All I know is that both of them are using java, and I wonder if there might be an issue with java? I did have to install a newer java version to get Matlab to work properly.

---

### Post by Potatoj316 on 2008-07-22
if a program is doing something on the unfocused workspace it can try to get your attention by showing itself on the taskbar of every workspace.  I dont know if that is what your talking about though

---

### Post by XCan on 2008-07-22
Unfortunately, I don't think that's it, unless the spreadsheet part of open office runs in the background doing something periodically. Only thing I can imagine it doing is autosave, but that shouldn't bring it to focus right?

---

### Post by Potatoj316 on 2008-07-22
No that shouldnt, only if the program is just starting or if there was an error (ive never seen an error, im just guessing) anything that would cause a new window to show up would do that and probably nothing else.

---

### Post by AnythingBut on 2008-07-22
> **XCan said:**
> 
A program I've noticed to disappear/reappear as described above _a lot_ is Matlab.

I have the same problem with Matlab R2008a.  I find maximizing/restoring gets it back on the taskbar.  I too would like a real solution.

Are you running compiz?  I not sure but I don't think it happens to me when I switch to metacity.

---

### Post by XCan on 2008-07-22
Hmm, I haven't touched the compiz settings. But I assume compiz is responsible for the 'pretty' stuff when closing windows and such? I'll try turning that off and see if it helps.

---

### Post by msntrf on 2009-02-23
Has any found the cause of this problem?

I have the same problem with Matlab R2008b and Ubuntu 8.10.

Thanks!

---

### Post by 243kof on 2009-03-23
I have the same problem with Matlab 7.6 (R2008a) in Ubuntu 8.10 and I can confirm it goes away if I turn Compiz off. Maybe it has been fixed in Jaunty?

---

### Post by JanNeggers on 2009-08-12
I can confirm this problem, i use jaunty and matlab 7.7.0 and compiz, and experience a lot of disappearing matlab taskbar items.

I'm still looking for a fix

P.S. atppp posts a vague solution on his blog:
[http://blog.wuxinan.net/archives/376](http://blog.wuxinan.net/archives/376)
i didn't try it though.

<edit>
I've found some relevant links, no solutions yet though
[http://www.mathworks.com/matlabcentral/newsreader/view_thread/157118](http://www.mathworks.com/matlabcentral/newsreader/view_thread/157118)

[http://linuxinside.blogspot.com/2008/01/solution-for-compiz-matlab.html](http://linuxinside.blogspot.com/2008/01/solution-for-compiz-matlab.html)
</edit>

---

### Post by JanNeggers on 2009-08-26
Bump,


Has anybody found a solution?

---

### Post by XCan on 2009-08-26
No, only way to do it is still to get rid of compiz.

---

### Post by JanNeggers on 2009-08-31
For now i use matlab together with compiz and the "desktop wall" option which i have configured when touching the corner of the screen with the mouse cursor"

All matlab windows will show up in the desktop wall, allowing a quick switch. But this is not a true solution. Hopefully a new java or compiz version will solve this problem.

---

### Post by bilderbuchi on 2009-11-03
any updates on this? i found a relevant bug at [https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/144406](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/144406)

---

### Post by thomas42. on 2009-11-03
something like that happened i never solved it as i use virtual box now ..but on talking to a friend later about he reckons it could a been compiz try removing compiz if u hav it worth a shot & sounds plausible

---

### Post by bilderbuchi on 2009-11-04
yeah turning compiz off solves the prob, but what if you don't want to turn compiz off?
the behaviour that min/maxing the windows makes them reappear on the taskbar should help in diagnosing the prob, no?

---

### Post by JanNeggers on 2010-07-22
I bump this thread because the problem is still not solved
Now using matlab 2010a and Ubuntu 10.04 Lucid

---

### Post by Warthaug on 2010-07-29
I too am having this problem - matlab 2010a, in ubuntu 10.04.  No idea how to fix it, other than the minimize/maximize button.  Its a problem I see with java-based programs as well (ImageJ, and others).

Bryan

---

### Post by wajda on 2010-08-02
Yeah, this problem has been there a while...
It seems to be a compiz bug - [http://bugs.opencompositing.org/show_bug.cgi?id=1316](http://bugs.opencompositing.org/show_bug.cgi?id=1316)
Hopefully it won't take the guys too long to fix, because it's getting so annoying that I abandoned using Compiz only because of this crap :)

---

### Post by Tovi on 2011-07-29
In 11.04 this problem is still not fixed. Haven't checked in unity yet, am using ubuntu classic for the time being. (Unity is not that great tbh).

Haven't tried matlab, but most java-based apps (such as eclipse and intellij) have this problem.

It seems to be triggered whenever the java window opens a new window.

The workaround to minimize and then maximize still works, but you can't expect me to do this every couple of minutes, as its tedious.

Also, I noted that after the bar disappears, you can still hover over it to get a preview using compiz window preview. You can't click on it though, so it's almost like it's still there in a way, but you can't see or do anything with it.

---

