---
title: "Please help!!!"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by jfever311 on 2012-06-16
I have no idea what happened to my laptop. Here is a shot of the screen. What do I do????

---

### Post by syteanric on 2012-06-16
hmmm... what were you doing before it happened? Have you made any system changes?

---

### Post by drs305 on 2012-06-16
Let's start by trying to update the packages.

At the command prompt, run the following:
```
sudo apt-get update && sudo apt-get upgrade
```
You will be asked for your password. Type it and press ENTER. You won't see the characters as you type.

Type y or ENTER when it prompts. When it finishes, reboot and see what happens. If you arrive at the same point, try:
```
sudo apt-get install -f
sudo dpkg --configure -a

```
Reboot.

If you still only get to a command prompt, let us know. If you have a different kernel option (perhaps in the Grub "Previous Linux versions" submenu, try it.

---

### Post by TheGuyWithTheFace on 2012-06-16
To get any form of a good answer, we'll need a bit more information. When did this start happening, is this from a regular install, can you repeat this problem, ect. Also, you'll get more attention from people who can help if you have a question title like: 

"Black text screen on logon"

or along those lines. I'm assuming this occurs on logon, but I can't be sure BECAUSE YOU DIDN'T GIVE US INFO!

Aside from that, is this from an alternate installation cd? What are your laptop's specs? I tried to do an alternate install of precise pangolin on an ancient laptop, and got pretty much the same screen on logon.

In summary:

~Please change the question title.
~When did this start happening?
~Did you recently install Ubuntu?
~Does it happen every time?
~Laptop specs?
~Ubuntu installation?
~Please tell us any other information you can think of.

---

### Post by jfever311 on 2012-06-16
Okay. I am running Ubuntu 12.04 on an Asus k52f. The problem just started this morning. I was on one of my forums and the screen dimmed by itself. I tried to exit out and the computer froze. I then manually shut down and this is what came up when the system turned on.

---

### Post by jfever311 on 2012-06-16
I have been running this same version for a while, maybe a week after it was released.

---

### Post by afixane on 2012-06-16
try write this
```
startx
```

---

### Post by TheGuyWithTheFace on 2012-06-16
> **jfever311 said:**
> Okay. I am running Ubuntu 12.04 on an Asus k52f. The problem just started this morning. I was on one of my forums and the screen dimmed by itself. I tried to exit out and the computer froze. I then manually shut down and this is what came up when the system turned on.

So, your 12.04 ran fine before that? Did you update right before it happened?

---

### Post by Gone fishing on 2012-06-16
I'd do exactly what drs305 suggested then reboot sudo reboot. If it starts as it should great if not startx as afixane suggested and tell us what the errors are.

What is pAtrIO4ever?

---

### Post by Carborundum on 2012-06-16
> **Gone fishing said:**
> What is pAtrIO4ever?

Their password, I'm guessing.

If so, you (the OP) should change that.

---

### Post by Paqman on 2012-06-16
I also recommend carrying out drs305's suggestions. When you've done all that and if you're still at a commmand prompt try:
```
sudo service lightdm start
```
If it spits out some errors, post them here and we'll see if we can make sense of them.

---

### Post by jfever311 on 2012-06-16
Okay this is what I have now after running the startx command.....

---

### Post by blackbird34 on 2012-06-16
Your screenshot looks like a tty to me (some form of fullscreen command prompt that does not use the graphical interface to run).

This is usually launched with a specific keyboard shotcut (you may have done it by accident): Ctrl+Alt+F1 (or F2, F3, F4, F5, or F6: there are 6 of these command prompts). To leave this mode, I believe you do Ctrl+Alt+F7. If you have a Fn key on your laptop keyboard press it too as it activates the function keys (rather than have them change screen brightness or whatever). 

I've just tried this on my laptop, and i have the default keyboard shortcuts. The first time i did that, i was scared too :popcorn:

---

### Post by jfever311 on 2012-06-16
Hey, so I cheated and took replaced the hard drive with my old one. I'll get around to fiddling with the other on eventually. Here is the wild part. As I said, I have been running 12.04 in this new laptop. My old HD had 11.04 on it. My laptop is noticeably faster with this older HD in it!! What is that all about??

---

### Post by critin on 2012-06-16
> **jfever311 said:**
> I have no idea what happened to my laptop. Here is a shot of the screen. What do I do????

Are you trying to run a command without entering 'sudo'?
That's what it looks like to me.

---

### Post by codingman on 2012-06-16
Press CTRL-ALT-F7, if this does not work then try reinstalling unity and then redo the first step. If you end up with a black screen when pressing CTRL-ALT-F7 after unity installation then restart uing sudo halt. If you end up with a black screen on CTRL-ALT-F7 before reinstallation, then press CTRL-ALT-F1 to return to the previous screen.

---

