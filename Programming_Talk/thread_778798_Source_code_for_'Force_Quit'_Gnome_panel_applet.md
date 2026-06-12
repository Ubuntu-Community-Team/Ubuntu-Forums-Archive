---
title: "Source code for 'Force Quit' Gnome panel applet?"
date: 2008-05-02
forum: Programming Talk
---

### Post by Toadinator on 2008-05-02
I'm a beginner in Python programming and I need something to do, so I thought I could make an applet for the Avant Window Navigator. The only problem is that I have no idea how I should make the one I want to make, a 'Force Quit' applet. Is the source code to the fore quit applet available on my desktop install somewhere or is it online? Thanks in advance!

---

### Post by LaRoza on 2008-05-02
> **Toadinator said:**
> I'm a beginner in Python programming and I need something to do, so I thought I could make an applet for the Avant Window Navigator. The only problem is that I have no idea how I should make the one I want to make, a 'Force Quit' applet. Is the source code to the fore quit applet available on my desktop install somewhere or is it online? Thanks in advance!

How does one install this applet?

I got the source for the gnome-panel, but the force quit applet is not included. (I don't use gnome)

They are rather small, so if you give me the package name of that applet, I will find it.

---

### Post by shad0w_walker on 2008-05-02
I believe you might have better luck just setting up an applet to launch xkill. It turns the cursor into a cross and what ever you left click next will be killed, any other click (Right or middle) will cancel xkill so you don't have to kill something if managed to click it by mistake.

---

### Post by Toadinator on 2008-05-02
> **shad0w_walker said:**
> I believe you might have better luck just setting up an applet to launch xkill. It turns the cursor into a cross and what ever you left click next will be killed, any other click (Right or middle) will cancel xkill so you don't have to kill something if managed to click it by mistake.

Wow thanks for the help! Now alls I gotta do is find out how to make python run a command when left clicked...

---

### Post by shad0w_walker on 2008-05-02
I think you might have misunderstood what I was saying. You just run the command 'xkill' then click whatever window it is you want to kill, you don't need to run a command when you left click. Just need to add an applet/icon to run 'xkill'

---

### Post by Toadinator on 2008-05-02
> I think you might have misunderstood what I was saying. You just run the command 'xkill' then click whatever window it is you want to kill, you don't need to run a command when you left click. Just need to add an applet/icon to run 'xkill'

Thanks! That's all I really needed to know anyways. Now all I need to figure out is how to get python to run a command.

---

### Post by Glaxed on 2008-05-02
import os
os.system("xkill")

---

