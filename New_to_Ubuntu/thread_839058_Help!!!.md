---
title: "Help!!!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-06-24
I was updating my computer when it locked up.  I could not figure out what to do (nothing like ctrl-alt-del in ubuntu that i know of), so i shut the computer off.  now when i turn it on, since the updates were incomplete it is messed up.
   
i tried going to the update manager and reinstalling the updates, but it says:
         An error occured
         The following details are provided:
   E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
   correct the problem.
   E:_cache->open()failed, please report.

i tried typing dpkg --configure -a into the terminal but i got:
      dpkg: requested operation requires superuser privilege

i have absolutely no idea what to do!!!!:confused:

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> I was updating my computer when it locked up.  I could not figure out what to do (nothing like ctrl-alt-del in ubuntu that i know of), so i shut the computer off.  now when i turn it on, since the updates were incomplete it is messed up.
   
i tried going to the update manager and reinstalling the updates, but it says:
         An error occured
         The following details are provided:
   E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to 
   correct the problem.
   E:_cache->open()failed, please report.

i tried typing dpkg --configure -a into the terminal but i got:
      dpkg: requested operation requires superuser privilege

i have absolutely no idea what to do!!!!:confused:

Insert your sudo:

```
sudo dpkg --configure -a
```

---

### Post by sdennie on 2008-06-24
Try:

```

sudo dpkg --configure -a

```

---

### Post by Tomatz on 2008-06-24
Open a terminal and type:


```
sudo dpkg --configure -a
```

That should fix the issue ;)

---

### Post by overdrank on 2008-06-24
I did not get that command could you repeat it lol :-P

---

### Post by Tomatz on 2008-06-24
> **overdrank said:**
> I did not get that command could you repeat it lol :-P

NO!


:lolflag:

---

### Post by pikabuntu on 2008-06-24
Ok... it seems to be working ...

it says :

Setting up gdb (6.8-1ubuntu2)...

setting up gdm (2.20.6-0ubuntu2) ...
*reloading gnome display manager configuation...
*changes will take effect when all current x sessions have ended.
 [ok]

EDIT:
oh wait its doing some more now

---

### Post by pikabuntu on 2008-06-24
p.s. what exactly does sudo do anyway?

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> p.s. what exactly does sudo do anyway?

It allows you to run selected commands as root, using your own password.

---

### Post by overdrank on 2008-06-24
To add to iaculallad
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by pikabuntu on 2008-06-24
ok, and what should do if ubuntu locks up like that again??

---

### Post by iaculallad on 2008-06-24
You will also be needing this when you want to access GUI applications that needs root privilege.

i.e: > gksu gedit /etc/X11/xorg.conf

Open your terminal and read more on gksu and gksudo

```
man gksu
```

and 

```
man gksudo
```

and

-To edit your sudoers file:

```
man visudo
```

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> ok, and what should do if ubuntu locks up like that again??

That is dependent from case to case basis, in your first situation, issuing the command **sudo dpkg --configure -a** solved the problem. Maybe, the next case would require other commands to fix your system.

---

### Post by sdennie on 2008-06-24
> **overdrank said:**
> I did not get that command could you repeat it lol :-P

Sure:

[b]```

sudo dpkg --configure -a

```[/b]

(Bolded for extra emphasis on the command)

---

### Post by pikabuntu on 2008-06-24
> **iaculallad said:**
> That is dependent from case to case basis, in your first situation, issuing the command **sudo dpkg --configure -a** solved the problem. Maybe, the next case would require other commands to fix your system.


this was after it locked up and i manually shut down the ocmputer & restarted it

---

### Post by pikabuntu on 2008-06-24
what is x windows?

---

### Post by Methuselah on 2008-06-24
X is what allows you to see windows on your screen.
[More technically, it manages access to your display hardware]
[Kind of like the GDI/DirectX in microsoft windows]

You can kill X with CTRL+ALT+BACKSPACE then log in again.
However, all programs you're running will be closed when X dies.

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> what is x windows?

It is the graphical system used primarily by Unix and Linux system. (X11)

---

### Post by pikabuntu on 2008-06-24
ok, it is letting me finish teh updates now 
hopefully after that it will be back to normal again
*crosses fingers*

---

### Post by Methuselah on 2008-06-24
Great!

---

### Post by pikabuntu on 2008-06-24
thanks everyone!! its working again!

---

### Post by iaculallad on 2008-06-24
> **pikabuntu said:**
> thanks everyone!! its working again!

I'm glad that you made it to work again. Go Ubuntu

---

### Post by Tomatz on 2008-06-24
You can mark the thread as solved to help others ;)

---

