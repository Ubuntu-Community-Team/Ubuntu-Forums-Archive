---
title: "unable to open terminal"
date: 2012-08-25
forum: New to Ubuntu
---

### Post by cilybeb on 2012-08-25
I am unable to open my terminal . I have clicked on cntrl+alt+t as usual but I am presented with a black box . I am unable to type into this box.I wonder if anyone can advise please

---

### Post by oldos2er on 2012-08-25
Can you provide a screenshot? If you type Alt-F2 and enter **gnome-terminal**, does it work?

---

### Post by cilybeb on 2012-08-25
thanks for the reply,

altf2 does not seem to make any effect,so could not input gnome. could not get a screenshot to appear.
 the appearance is  the normal window that appears after ctrl alt t but is black with no curser in it.

---

### Post by Bashing-om on 2012-08-25
Clybeb;

  How about this approach.. Reboot and hold shift key to get boot options menu.
choose the alternate to get single user mode and login from terminal...
see if then you can apply the venerable oldos2er's suggestion ?

  Please try and advise <==BDQ

---

### Post by oldos2er on 2012-08-25
> **cilybeb said:**
> thanks for the reply,

altf2 does not seem to make any effect,so could not input gnome. could not get a screenshot to appear.
 the appearance is  the normal window that appears after ctrl alt t but is black with no curser in it.

Can you tell us which version of Ubuntu you're using, and your hardware specs? Are you having any other display problems?

---

### Post by Thacker on 2012-09-12
> **oldos2er said:**
> Can you tell us which version of Ubuntu you're using, and your hardware specs? Are you having any other display problems?

I too have this problem both with Mint 13 and ubuntu 12.04;
terminal - fine on ubuntu 8.04 (still on system!)
No other display problems

---

### Post by NikTh on 2012-09-12
Hi , 

If the problem is specific to gnome-terminal then try to reinstall it from Console and see if this fixed your problem. 

Press Ctrl+Alt+F2 to go in Console Mode . Login with username & password and give these commands

```
sudo apt-get purge gnome-terminal
``````
sudo apt-get install gnome-terminal
```Then go back to Desktop Environment with Ctrl+Alt+F7 and see . 

Thanks

---

### Post by Thacker on 2012-09-12
No still the same.
just reinstalled ubuntu 12.04 used the unity desktop; initial startup
terminal ok able to type commands etc.
reboot -  back to square one - blank window (unity desktop)

---

### Post by Bashing-om on 2012-09-12
@ ehacker;

  Just as an aid in the trouble shooting process:
When you boot up the install cd in the "try ubuntu" mode, is the terminal then functional ?

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Thacker on 2012-09-12
> **Bashing-om said:**
> @ ehacker;

  Just as an aid in the trouble shooting process:
When you boot up the install cd in the "try ubuntu" mode, is the terminal then functional ?

[INDENT]regards <==BDQ

[/INDENT]
Yes works in the "try mode"

---

### Post by zazlox on 2012-09-12
any errors or warnings on log files ?

```
/var/log/
```

---

### Post by Bashing-om on 2012-09-12
@Thacker;

Lets look at something simple.
system settings->keyboard ..what is launch terminal set to ?

[INDENT]hth <==BDQ 
[/INDENT]

---

### Post by Thacker on 2012-09-13
> **Bashing-om said:**
> @Thacker;

Lets look at something simple.
system settings->keyboard ..what is launch terminal set to ?

[INDENT]hth <==BDQ 
[/INDENT]

Ctrl+Alt+T  with the same result - an unusable empty black box

---

### Post by NikTh on 2012-09-13
Hi , 

@Thacker what did you hack ? :P 
The terminal by default in Ubuntu is not a black-box. Is  like a dark purple color or something like that. 

Do you remember anything about .bashrc or .profile you involved with ? 

Can you install another terminal and use it ? 

Open synaptic package manager (if you have not installed , search on Software-Center) and in search box write **lxterminal** . Install lxterminall and see if you are able to work with it. 
Thanks

---

### Post by Thacker on 2012-09-13
> **NikTh said:**
> Hi , 

@Thacker what did you hack ? :P 
The terminal by default in Ubuntu is not a black-box. Is  like a dark purple color or something like that. 

Do you remember anything about .bashrc or .profile you involved with ? 

Can you install another terminal and use it ? 

Open synaptic package manager (if you have not installed , search on Software-Center) and in search box write **lxterminal** . Install lxterminall and see if you are able to work with it. 
Thanks
NikTh,

What can I say - that's worked a treat and such a simple cure in the end; can't thank you enough.

Kind Regards

Thacker

---

### Post by NikTh on 2012-09-13
> **Thacker said:**
> NikTh,

What can I say - that's worked a treat and such a simple cure in the end; can't thank you enough.

Kind Regards

Thacker

Hi , 

is gnome-terminal working now ? 
or 
you just leave it away and use the lxterminal ? 

Thanks

---

### Post by chipchop on 2012-10-08
Could it be as simple as a bad font color?

Right click in the terminal window, profiles, profile preferences, color tab, uncheck "use colors from system theme", choose text color white and background color black.  You can change it to your preference after that, but at least you know if that was your problem.

---

