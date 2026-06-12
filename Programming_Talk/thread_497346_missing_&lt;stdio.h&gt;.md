---
title: "missing &lt;stdio.h&gt; ?"
date: 2007-07-10
forum: Programming Talk
---

### Post by jnorthr on 2007-07-10
Morning all -
i'm using ubuntu 7.0.4 fawn. The gcc compiler must already be installed as part of it. So my 'HelloWorld'  is in a file called HelloWorld.c on my desktop. from a terminal command line pwd=~Desktop , we type 'gcc HelloWorld.c' and compiler runs to end reporting a missing header specification. 

Do i need to revise the PATH environment variable to include the 'include' folder ? If so, where do i point it ? I'm slowly learning ubuntu and my 'find / stdio.h never finds anything on my install by that name. The 'locate' command does not either. What gives ? Are the headers included in gcc or is this another download ?
thx

---

### Post by lisati on 2007-07-10
Try:
```

sudo apt-get install build-essentials

```
and let us know how you get on. (Don't panic if you get asked for your password and nothing shows when you type it - it will still work!)

---

### Post by jnorthr on 2007-07-10
O)k, thx for that. There is no net access on my ubuntu machine - just my wife's windows xp kit - which she gaurds like an eagle!!! So I have only bin able to create a CD of ubuntu 7.0.4 and do an install on an old laptop. Can i download a .deb for build-essentials or is it on the install CD ? If so maybe i can point dpkg at it ?  Dunno - but i call tell you one thing - since putting ubunto on my laptop, i have not used windows at all.


just need to installl .mp3 and dvd support (which is a pain)  but that's another story :lolflag:

---

### Post by jnorthr on 2007-07-10
Good news. I did think you need to be on-line to run apt-get in order to install further packages. But, guess what ?  I thought I'd see what would happen if i just put the ubuntu 7.0.4 cd into the drive while 'the feisty fawn' is running.
'The fawn' notices the Cd and asked if i wanted to start the package manager. Do I ? You bet your brown boots !! I want to post some screen shots for you to see. Later me thinks. but browsing thru the available packages, I did find the libc6-dev package which i clicked on to install, then had to click apply button to do it. Ran ok. Then did further research into the 'All' packages options and think i found the 'build-essentials' so installed that too.

The C headers now live in my machine. And HelloWorld now really does say 'Hello World'. But i don't see any syntax errors when i compile. How do i do that ?
ta

---

### Post by jespdj on 2007-07-10
You can download the Ubuntu .deb packages manually from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

After downloading, you install a package with the following command:
```
sudo dpkg -i filename.deb
```

---

