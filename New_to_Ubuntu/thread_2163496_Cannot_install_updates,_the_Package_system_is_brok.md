---
title: "Cannot install updates, the Package system is broken?"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by cazz1 on 2013-07-18
I am very new to ubuntu, so new that I installed this hours ago. Here's my problem:

When trying to run the Update manager I get this message:

> The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Then I get the following message: 

> The following packages have unmet dependencies:
libc6: Depends: libc-bin (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.3 is installed

After following instructions from different parts of Google, I finally came to this: 

> E: Internal Error, No file name for libc6

Same thing when trying to enter the Software Center, it tells me I cannot install or remove software until the package catalog is repaired. Any help for a newbie?

---

### Post by cazz1 on 2013-07-18
I need some sort of solution, would a complete format and reinstall work?

---

### Post by howefield on 2013-07-18
Are you running Precise 12.04.* ?

---

### Post by cazz1 on 2013-07-18
Yes I am

---

### Post by DeathByDenim on 2013-07-18
Well, reinstalling would most definitely work. But you said this happened on a system that you installed only hours ago?
Could you open a terminal and type
```
sudo apt-get update
```
Does it report errors when you do that? If so, what does it say?
If not, can you try typing this:
```
sudo apt-get upgrade
```
Does that give errors? If so, what?
Finally, try
```
sudo apt-get dist-upgrade
```

---

### Post by Bashing-om on 2013-07-18
cazz1; Hi ! Welcome to ubuntu in general and the forum in particular.

I can not imagine how you got in this situation on a new install..but, let us see about getting you straightened out.
We are going to be using the terminal.. not a scary thing in the least... just another tool and easier to relate with in these circumstances.

From your desktop the key combo ctl+alt+t yields a terminal:
To this terminal copy and past the following terminal commands, one at a time; and post these outputs back to your thread - between code tags (# at top of post).

```

lsb_release -a

```
so we know what system we are operating on;
```

dpkg -l libc6
dpkg -l libc-bin

``` so we know the status of these installed packages;
```
sudo apt-get update
sudo apt-get upgrade

```
so we know the overall state of the package management system.

[INDENT][INDENT]a tale will be told[/INDENT][/INDENT]

---

### Post by karanbpathak on 2013-07-18
Try Update command in terminal
sudo apt-get update

and then try
sudo apt-get install -f

Please take a look at this [h=1][SIZE=3][http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)[/SIZE][/h]

---

### Post by cazz1 on 2013-07-18
> **DeathByDenim said:**
> Well, reinstalling would most definitely work. But you said this happened on a system that you installed only hours ago?
Could you open a terminal and type
```
sudo apt-get update
```
Does it report errors when you do that? If so, what does it say?
If not, can you try typing this:
```
sudo apt-get upgrade
```
Does that give errors? If so, what?
Finally, try
```
sudo apt-get dist-upgrade
```

Got errors, but thats because my modem disconnected from internet, will retry and let you know.

---

### Post by cazz1 on 2013-07-18
Okay so after running > sudo apt-get upgrade it installs a few things and I get the error msg at the end. Here's a screen cap.

---

### Post by montu5742 on 2013-07-18
Hello my friend..

It looks like the screenshot does not get attached properly over here...

Please try one more time to take screenshot and attached to the thread..

Thanks
montu

---

### Post by howefield on 2013-07-18
> **cazz1 said:**
> Okay so after running  it installs a few things and I get the error msg at the end. Here's a screen cap.

I have removed the base64 that was posted instead of the image, please repost.

---

### Post by cazz1 on 2013-07-18
Thanks for all your help, I found out what the root problem was by retracing steps, don't know if it really was the issue but it seems to be working now with now errrors. I remember trying to install Spotify and searching around I found out about Wine. I remember accidentally hitting "no" on the user agreement. After that I was able to run Spotify directly but then all the error messages started to appear. I reinstalled Wine and tried to update again and so far so good.

---

