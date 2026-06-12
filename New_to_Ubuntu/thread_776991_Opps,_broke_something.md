---
title: "Opps, broke something"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by nigelm187 on 2008-05-01
Hi All,

Ubuntu all installed ok and connects to the internet with my wired connection....but I decided to have a play to see if I could connect my wireless usb device. I was stepping through the instructions on a website

I typed in 

sudo apt-get install wpasupplicant

.. and that was it, no internet access to carry on the rest of the install

e.g.
sudo apt-get update

etc

I managed to get my browser and emails working agin by reenabling the ethr network under system/network, but any attempt to install apps via Applications / Add & Remove or from the terminal window with apt-get just timeout


Any ideas anyone.

Regards

Nigel.

---

### Post by warbread on 2008-05-01
Interesting.  If you have internet access, you should be able to use the repositories.  What happens when you do a "sudo apt-get update" from the terminal?

---

### Post by nigelm187 on 2008-05-01
Wow, that was a quick response!

If I type 'sudo apt-get update' at a terminal, it just sits at 0% [.....ubuntu address in here can't remember what it is...] until it times out

---

### Post by warbread on 2008-05-01
Argh!  I'm at work, which won't let me ping out.  Try doing a 'ping archive.canonical.com' and see if it returns anything.  If it doesn't, the repos might be down.  Since I doubt that's the case, we'll have to look into what would be affecting you in particular. Since I have no idea, we'll start with the basics, which means getting information.

I'll need:
Whatever site you were using for isntructions.
A post of the output of:
```
:-$ cat /etc/apt/sources.list
```
What version of Ubuntu are you using?

It might also be worth your while to uninstall wpasupplicant, since it seems the trouble started when you installed in.

```
:-$ sudo apt-get remove wpasupplicant
```

---

### Post by nigelm187 on 2008-05-01
Ah uhmm - hang on - spotted a faux pas in my original post - sorry...

"sudo apt-get install wpasupplicant"

was meant to say :

"sudo apt-get remove wpasupplicant"

I was trying to install my Safecom wireless USB driver from the following link

[http://ubuntuforums.org/showthread.php?t=92327](http://ubuntuforums.org/showthread.php?t=92327)

 got as far as the typing in the command above (verbatum)

then tried the next bit under -

"The following may not be essential, but it's worth doing to ensure better success with other programs."

At which point, I discovered all was not well, no network anymore....

Recovered a bit by enabling network under System, but currently no apt-get or add/remove functionality.

I *can't* even track back by typing  

sudo apt-get install wpasupplicant

as it won't connect 

Many thanks for your help with this. I am new to Ubuntu, but think its great - had a a couple of days now - its **far** better than XP..

Regards

Nigel

---

### Post by warbread on 2008-05-01
Wow!  I see nothing that would screw up your apt-get, but let's try undoing the other step.  

```
:-$ sudo modprobe zd1211
```

If that doesn't work, you can get wpasupplicant back by putting an Ubuntu cd in the drive.  It should ask you if you want to enable it as a source in the repositories, or something like that.  Accept whatever similar offer it may pose.  Then, in Synaptic, go into Software -> Sources and disable all sources that are on the web (anything that doesn't say 'CD').  Click the 'Refresh' button and you should be able to install wpasupplicant from there.  

I apologize if that's confusing.  I'm not at my Ubuntu machine right now and am doing this from memory.  I believe that the dialogues and menus are straitforward enough that my choppy directions should at least point you in the right direction.

---

### Post by nigelm187 on 2008-05-01
Thanks again. 

Pleased to hear that the instructions were correct as I still need to use them to setup the wireless usb stick.

I'm also away from the machine, so will try your advice tonight. Will let you know how far I get.


Nigel.

---

### Post by nigelm187 on 2008-05-02
Hi 

I tried - sudo modprobe zd1211
It returned on the next line with a FATAL error. I don't think it was / has been installed.

so I put the Ubunut CD into the drive.

Synaptic Sources - Settings Repositories 
Unticked all 'Downloadable from the internet' options Ticked 'Installable from CD-ROM/DVD'
    'cdrom with Ubuntu 8.04 "Hardy Heron"'

Searched 'wpa'
    wpasupplicants - selected 'mark for installation'

Message:

"wpasupplicant:

Package wpasupplicant has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"

Regards

Nigel.

---

