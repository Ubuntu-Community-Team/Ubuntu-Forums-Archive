---
title: "[SOLVED] synaptic error, How to fix?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by ysNoi on 2008-06-17
I don´t know how it goes after checking the Reload of Synaptic Package Manager so I did a post in this way....

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/synaptic_1.png[/IMG]

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/Synaptic_2.png[/IMG]

Can anyone explain why this is happening and How to solve it...?

I´m a newbie in Ubuntu and new world to Linux Distros so please help me...

Any effort is highly appreciated...! Thanks in advance..! :guitar:

---

### Post by Sef on 2008-06-17
What version of Ubuntu are you running?  Edgy is no longer supported.  If you are using that, you need to upgrade.

---

### Post by wormser on 2008-06-17
You need to add the key.  This [blog]("http://ubuntu-tutorials.com/2006/10/21/seveas-ubuntu-packages/") has directions.

Here is the command.
```
wget http://mirror.ubuntulinux.nl/1135D466.gpg -O- | sudo apt-key add -
```Then run
```
sudo apt-get update
```

Update: Good point Sef.

---

### Post by ysNoi on 2008-06-17
I´m using Hardy Heron with kernel version 2.6.24-19-generic....!

Don´t know about Edgy so far...!

Anyway, thanks for helping....What will I do now..? 

:guitar:

---

### Post by wormser on 2008-06-17
You need to remove that repository because it is for Edgy.  It looks like you added the wrong one.  System> Administration> Software Sources> Third-Party Software tab and highlight the one with Edgy and remove.  Then it should work.

---

### Post by ysNoi on 2008-06-18
It´s very amazing! :guitar:

I got it wormser....with your help guys here....A million of thanks to all of you Guys...!

I got no ERROR anymore..! :):)

[IMG]http://i249.photobucket.com/albums/gg226/ysnoi_lacroxste/Ubuntu/synaptic_4.png[/IMG]

One more thing before I proceed, do I have to Mark All upgrades here?

Thank you very much Guys...!

---

### Post by PmDematagoda on 2008-06-18
Open Update Manager in System>Administration>Update Manager, that will take care of the updates for you.

---

### Post by wormser on 2008-06-18
> **ysNoi said:**
> It´s very amazing!  I got it wormser....with your help guys here....A million of thanks to all of you Guys...!

I got no ERROR anymore..! :):)

One more thing before I proceed, do I have to Mark All upgrades here?

Thank you very much Guys...!

Mark the thread as solved and click the star icon on the post that solved it.  PmDematagoda post has the solution to your last question.

---

