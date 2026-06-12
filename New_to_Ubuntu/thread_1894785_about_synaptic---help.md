---
title: "about synaptic---help"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by jiangchongyi on 2011-12-13
Hello all,
 
I've been trying the install the java6.
 
After using the apt-get in the teminal and got nothing i turned to the synaptic. Then this is what i get:
 
 
E: Malformed line 65 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
 
Closing the error window just closes Synaptic, too - so I can't check the repository 
 
And I've looked for solution in the forums and get the  following answer:
 
 
in a terminal:

sudo gedit /etc/apt/sources.list

--

Remove the line (or uncomment it) you added.

Then do 

sudo apt-get update

--

 
did what it had been suggested but get 
 
sudo: gedit/ect/apt/sources.list: command not found
 
 
Any help would be great appreciation!
 
Daniel

---

### Post by cortman on 2011-12-13
> **jiangchongyi said:**
> 

sudo: gedit/ect/apt/sources.list: command not found


Hi Daniel,

If you copy/pasted the terminal output there, the problem is no space between "gedit" and the path, plus the directory is "etc", not "ect". It should be

```
gksu gedit /etc/apt/sources.list
```

---

### Post by yetiman64 on 2011-12-13
> **cortman said:**
> ....

```
sudo gedit /etc/apt/sources.list
```

gedit is a graphical app as such gksu or gksudo should be used instead eg.

```
gksudo gedit /etc/apt/sources.list
```[[COLOR=Blue]--this link--[/COLOR]]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo") will explain why.

---

### Post by cortman on 2011-12-13
> **yetiman64 said:**
> gedit is a graphical app as such gksu or gksudo should be used instead eg.

```
gksudo gedit /etc/apt/sources.list
```[[COLOR=Blue]--this link--[/COLOR]]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo") will explain why.

>sudo gedit < will still work for the OP's intended purpose.
After reading over the link, though, it makes sense, so I'll correct myself and say gksu is the way to do it.
Thanks, yetiman64!

---

### Post by jiangchongyi on 2011-12-13
> **yetiman64 said:**
> gedit is a graphical app as such gksu or gksudo should be used instead eg.
 
```
gksudo gedit /etc/apt/sources.list
```[[COLOR=blue]--this link--[/COLOR]]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo") will explain why.
 
 
Problem solved! 
Thanks a lot!!

---

### Post by anewguy on 2011-12-13
I'll add something to the end here about synaptic package manager and ubuntu 11.10.

First, you'll need to download it via:

sudo apt-get synaptic


Second, you'll want to go to settings and then icon for help for handicapped, etc., people.  Once there, the default tab will have as it's first item the reader app - click to turn it on, then immediately click to turn it off.

Third, in this same window, go to the keyboard tab and turn the on-screen keyboard and then immediately back off.

If you don't do the above, chances are pretty good you'll fall victim to a known bug and synaptic will ask for your password and then abort.  This bug is already in launchpad and as weird as it sounds (or at least it did to me when I read it), doing the above lets synaptic work - I don't know why.

Dave ;)

---

### Post by MartijnNL on 2011-12-14
> **jiangchongyi said:**
> Problem solved! 
Thanks a lot!!

Can you mark the thread as solved using the thread tools?

---

