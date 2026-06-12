---
title: "Could not write bytes : Broken pipe"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by naveenchandra_kumar on 2013-09-15
Hi all,

I am getting the boot menu where I can select the linux kernel 3.8 generic, but that onwards it goes to balck monitor mode and prompts the following message **"Could not write bytes : Broken pipe"** and stops and not able to boot further.

I hardly remember having done anything mysterious or adventurous on my machine. I was just git cloning some repositories and installing some python related libraries. The installation of ubuntu 12.04 had worked for two months without this problem. 

What is the remedy for this? **Only remedy visible for me as of now is to do clean installation,** since I can not get network now where I can apt-get and all that. I worked with live CD, it works fine and that means, my hardware is fine. 

I am able to go to safe mode while booting. Is there anything I can do in safe mode to get the X server corrected?

This is highly demoralizing for me. I loved ubuntu and freedom it offered me. But this crash of my machine is killing my spirit. Please, experts on linux and ubuntu, help me at the earliest.


Naveen C K

---

### Post by naveenchandra_kumar on 2013-09-15
Is this correct forum for this problem?

---

### Post by naveenchandra_kumar on 2013-09-15
[COLOR=#000000]Hi all,[/COLOR]

[COLOR=#000000]I am getting the boot menu where I can select the linux kernel 3.8 generic, but that onwards it goes to balck monitor mode and prompts the following message [/COLOR]**"Could not write bytes : Broken pipe" **and stops and not able to boot further.

I hardly remember having done anything mysterious or adventurous on my machine. I was just git cloning some repositories and installing some python related libraries. The installation of ubuntu 12.04 had worked for two months without this problem. 

What is the remedy for this? **Only remedy visible for me as of now is to do clean installation**, since I can not get network now where I can apt-get and all that. I worked with live CD, it works fine and that means, my hardware is fine. 

I am able to go to safe mode while booting. Is there anything I can do in safe mode to get the X server corrected?

This is highly demoralizing for me. I loved ubuntu and freedom it offered me. But this crash of my machine is killing my spirit. Please, experts on linux and ubuntu, help me at the earliest.
[B]

Naveen C K[/B]

---

### Post by naveenchandra_kumar on 2013-09-15
Hi all,

Ubuntu 12.04 is not booting up with GUI, but instead shows the meassge " Could not write bytes : Broken pipe". What does this mean?

Naveen C K

---

### Post by naveenchandra_kumar on 2013-09-15
Sorry all,

Looking at the cold response from the Ubuntu community I am planning for a clean installation.

---

### Post by radiowave911 on 2013-09-15
It means you had better have a bucket handy - broken pipes tend to leak! :D

Sorry, I had to do that.  More seriously, I believe the 'Broken Pipe' means that the system had an issue writing data somewhere.  Do you get anything at all (like a login prompt with no GUI)?  There is another post here about the issue occurring and related to nvidia drivers.  That post is at [http://ubuntuforums.org/showthread.php?t=2058521](http://ubuntuforums.org/showthread.php?t=2058521).  Maybe the purge/reinstall listed there would be of assistance to you.

Good luck.

---

### Post by lisati on 2013-09-16
Threads merged.

Please do not start multiple threads for the same problem, it dilutes the community's ability to help.

---

### Post by naveenchandra_kumar on 2013-09-16
No login prompt is available when I get this message. black coloured blank screen with "could not write bytes : Broken pipe" message on the top-left corner.

---

### Post by naveenchandra_kumar on 2013-09-16
No login is available, only black window with the message

---

### Post by naveenchandra_kumar on 2013-09-16
I have seen that post, it is of no help to me as I don't get anything like he/she gets. (CLI)

---

### Post by naveenchandra_kumar on 2013-09-16
sorry all,

Due to shortage of time I decided to go for reinstallation.

---

### Post by lisati on 2013-09-16
> **naveenchandra_kumar said:**
> I have seen that post, it is of no help to me as I don't get anything like he/she gets. (CLI)

Which post was that?

---

