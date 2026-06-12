---
title: "XTerm"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by techbuntu27 on 2013-03-09
Okay, I'm new to Linux and Ubuntu is my choice and I am loving it. But also I also learning C Programming and currently I'm using code::block. The console I used is the XTerm but I don't like how it looks because the window is very small as well as the font. 

Here's what I mean:
[IMG]http://i.imgur.com/txHlC0F.png?1[/IMG]


I hope you guys can help a super beginner like me.

---

### Post by techbuntu27 on 2013-03-09
EDIT:

Ohh.. I am very sorry sir. It's my first time to use this forum and my connection was so laggy a while ago.

---

### Post by c2tarun on 2013-03-09
I'll suggest you spend some time in trying C programms in Terminal. To open terminal press Ctrl + Alt + T
[Here]("http://www.thiyagaraaj.com/articles/articles/compileandrunsimplecprogramwithgcccompilerinubuntulinux") is a tutorial I found after a quick google search, there might be others better than this but it'll give you a start.

Also it is not mandatory but try using vim as text editor, its powerful light, and everything is done by keyboard only, no need of mouse, so after a little practice you can achieve great speed. To install it type in terminal:

```
sudo apt-get install vim
```

Vim comes with and embedded tutor. To run its tutorial type following in terminal:
```

vimtutor
```

---

### Post by c2tarun on 2013-03-09
Please don't duplicate your thread. After posting have patience for at least 24hrs to reply. Here is the duplicate of your thread. [http://ubuntuforums.org/showthread.php?t=2124107](http://ubuntuforums.org/showthread.php?t=2124107)

---

### Post by rocketfish201 on 2013-03-09
Have you tried using gnome-terminal?

---

### Post by lisati on 2013-03-09
Threads merged.

Please do not start mutiple threads for the same question, it dilutes the community's ability to help.

---

### Post by techbuntu27 on 2013-03-09
> **lisati said:**
> Threads merged.

Please do not start mutiple threads for the same question, it dilutes the community's ability to help.


Ahh. Yes sir I'm aware of it. I just noticed right now after I received replies. I'll not do it again. It just occurs because my connection is not stable and I re-click the post because I thought It did not post successfully. So I humbly apologize guys for my mistake.

---

### Post by techbuntu27 on 2013-03-09
> **rocketfish201 said:**
> Have you tried using gnome-terminal?

Yes, I'm using it right now. By the way, everything is okay. I did some couple of research and change the default console and I'm now using gnome-terminal. Thanks!

---

### Post by techbuntu27 on 2013-03-09
Hmmm... I have another problem which is happening since I installed ubuntu 12.04. (I dual boot, Windows 7 and Ubuntu)

I adjusted the brightness settings. But whenever I turn off and turn on again my laptop ([https://www.asus.com/Notebooks_Ultrabooks/K43SJ/](https://www.asus.com/Notebooks_Ultrabooks/K43SJ/)) the brightness is again on its full settings. So I keep on adjusting the brightness every time I use my laptop. Also the bluetooth also doesn't work. But everything else works fine.


Second, why is that the Grub menu seems to be too big (I have installed ubuntu on my dekstop but it's not like this) and also the Ubuntu start-up logo is also too enlarge/big (Although I already activated the recommended graphics driver for my laptop which is GeForce GT520M). But everything with regards to video are all okay. Its just so bothering seeing the Grub and Ubuntu start-up logo is too big.

Heres some SS:

[IMG]http://i.imgur.com/V0WkvW8.jpg[/IMG]


[IMG]http://i.imgur.com/DMix7zb.jpg[/IMG]

'Another thing is that, sometimes the Shutdown and Restart mess up which doesn't work properly. Sometimes when I click shutdown and restart it will just log off.

---

### Post by Mark Phelps on 2013-03-10
You really should be starting a new thread for each problem.  These ... and I have another problem ... threads don't work well.  Folks decide which thread to answer based largely on the title -- which isn't changing.

---

### Post by rocketfish201 on 2013-03-10
> **techbuntu27 said:**
> I adjusted the brightness settings. But whenever I turn off and turn on again my laptop ([https://www.asus.com/Notebooks_Ultrabooks/K43SJ/](https://www.asus.com/Notebooks_Ultrabooks/K43SJ/)) the brightness is again on its full settings. So I keep on adjusting the brightness every time I use my laptop. 

What I did was install xbacklight.
```
sudo apt-get install xbacklight
```
I like my screen brightness to be at 15%, so I set xbacklight to set the brightness to 15% on startup. ```
xbacklight -set 15
```

---

