---
title: "Where to put the code."
date: 2014-04-30
forum: New to Ubuntu
---

### Post by Colin_Reece on 2014-04-30
I am a complete newbie to Ubuntu, I installed it on my laptop yesterday, I am used to working with MS Windows so this is a new thing for me.

My problem is the screen keeps timing out after around 10 minutes, I searched online and it appears it is a common problem, so I downloaded a program or code for Caffiene, I looked at the files I downloaded and they have some lines of code which I presume I need to put somewhere to make it all work, so where and how do I do it please?

I have Ubuntu 14.04 by the way.

Also I have the power settings correct but as above it still times out.

---

### Post by Bucky Ball on 2014-04-30
Welcome. When you say 'timing out' do you mean the screensaver pops up or the screen simply goes black?

14.04 LTS is still quite 'wet behind the ears' so this could be a bug yet to be ironed out. I generally wait for the point release (14.04.1 in July) before using a new release as my main squeeze (as in I need it to work!). I have a few 14.04 installs but it's still 12.04 when I need reliability here. ;)

---

### Post by Colin_Reece on 2014-04-30
Thanks for the quick reply, Yes I mean the screen goes black, then when I move the mouse I have to log in again with my password.

As I said in my above post, I am used to working in Windows, I do realise this is an open saurce OS and I am trying to get used to it, I have a few things in the Software Centre that if I click on them I get the option to install, I was hoping some of these other programs were the same but it appears I need to input code, this is where I'm stuck because I don't know where to input it once I get it.

I downloaded 14.04 because I thought it was the latest and more up to date but as you say it still has a few bugs yet.

---

### Post by LastDino on 2014-04-30
Codes? Commands? 
Press> ctrl+alt+T
You will see command line and that's where commands are suppose to be entered. 

Word of caution, make sure those commands you're going to enter are coming from trusted source.

---

### Post by Colin_Reece on 2014-04-30
Thanks, when I open the Caffeine file I downloaded I have 4 files in it:

Applicationsintance.py
core.py
_init_.py
main.py

All have command/code lines so which do I input please?

---

### Post by DogMatix on 2014-04-30
You can alter settings for the screen sleeping, locking, etc. in Light Locker Settings.

Menu > Preferences > Light Locker Settings

---

### Post by LastDino on 2014-04-30
> **DogMatix said:**
> You can alter settings for the screen sleeping, locking, etc. in Light Locker Settings.

Menu > Preferences > Light Locker Settings

+1

Have you actually tried doing this? What you're doing now is installing completely new app do deal with screen savers.

Anyhow, you can do this to install caffeine on Ubuntu 14.04

> 
$ sudo add-apt-repository ppa:caffeine-developers/ppa

$ sudo apt-get update

$ sudo apt-get install caffeine

Put them in terminal one by one and press ''enter'' after each, let the process run its course and answer ''y'' if asked.


I would suggest sticking with default if possible and just changing the settings as suggested.

---

### Post by Colin_Reece on 2014-04-30
WoW!  thanks for the replies, when I was searching I never saw the Light Locker suggestion anywhere, but that seems to have done the trick, I waitede before I posted and the screen stayed on, thank you very much for all your help guys.

---

