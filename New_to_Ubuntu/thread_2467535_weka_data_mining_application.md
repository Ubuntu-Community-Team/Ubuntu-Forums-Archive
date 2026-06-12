---
title: "weka data mining application"
date: 2021-09-29
forum: New to Ubuntu
---

### Post by saffronsailor on 2021-09-29
Hi
Brand new to Ubuntu
Installed successfully - as is weka (I think)

when I enter weka at the prompt I get exception error

No X11 display variable set

I have googled it but do not follow the comments

my terminal says bob@Desktop-XXXXXXX

what do I need to do - simple language please

Bob M
New Zealand

p.s. Windows 10 machine

---

### Post by ActionParsnip on 2021-09-30
How did you install the application? What steps did you take?

---

### Post by Holger_Gehrke on 2021-09-30
Does that 'p.s.' mean you're dual booting or does it mean you're running Ubuntu in the **W**indows **S**ubsystem for **L**inux ? If it's the latter, than you need to install and run an X-Server in Windows and point the DISPLAY variable at that in Ubuntu (export DISPLAY=localhost:0.0).

Also, the only data mining tool named 'weka' I can find is a Java application, so I don't really understand the need to run it in an environment you're not (yet ?) familiar with, since Java is meant to be platform independent.

Holger

---

### Post by grahammechanical on 2021-09-30
X11 is the display server. It is the program that puts all the visual stuff on the screen. This X-server has been the display server on Linux for decades. Slowly it is being superseded with a modern alternative where the window compositor complies with the standards in a protocol called Wayland.

If you have installed Ubuntu 20.04 then the X11-server will still be the default display server and there will be an option at the login screen to use Wayland instead. If you have installed Ubuntu 21.04 then a Wayland compositor will be the display server by default. At the login screen there will be an option to use the X-server.

Look for a Ubuntu icon at the bottom right of the screen and click on it. A menu will appear. With Ubuntu 21.04 the menu will offer Ubuntu or Ubuntu on X-server. With Ubuntu 20.04 the options will be Ubuntu and Ubuntu on Wayland.

P.S. Is it Ubuntu server that you have installed?

Regards

---

### Post by saffronsailor on 2021-09-30
Ubuntu 20.04.3 LTS is what I have installed

Why am I doing this ?

Because under windows 10, weka does NOT offer the autoWEKA classifier on my screens

However, weka people at Waikato University say they can see the above classifier running under linux

So I am trying to get an environment where I have access to this classifier

I have installed Ubuntu [not Ubuntu server]

The terminal said "it would take a few minutes"................

'sudo apt install weka' was the command I used

at one stage it says 'setting up weka (3.6.14-1) - don't understand why it is setting up an old version when the current one is 3.8.5 ??

Bob M

p.s. not dual booting
p.s. don't understand reference to icons on bottom of screen ??

---

### Post by grahammechanical on 2021-09-30
> p.s. don't understand reference to icons on bottom of screen ??

We load Ubuntu and we get to a login screen with our username. We click enter and we get to a screen where we enter our password. At the bottom of that screen on the right is a circular icon. Click on that icon and we get an option to change the display server. If we choose to automatically login we do not get to see that icon and we cannot change the display server.

You are using Ubuntu 20.04.3 LTS. This means that the X-Server is by default the display server. So, I conclude that this error message:

> No X11 display variable set

must be referring to a setting in the weka application. We have eliminated possibilities.

Regards

---

### Post by saffronsailor on 2021-09-30
thank you for your help

I do not see the icon you refer to ???

Attached a screenshot of my terminal

Bob M

---

### Post by ActionParsnip on 2021-10-01
The OS installs the version in the repositories. This is not the latest version and Ubuntu is rarely bang up to date as it isn't a rolling release distribution. Packages can be left in favour of packages with issues.

---

