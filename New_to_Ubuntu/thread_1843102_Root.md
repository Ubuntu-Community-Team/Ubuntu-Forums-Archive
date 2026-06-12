---
title: "Root"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by (Nes) on 2011-09-12
I need to login to root for 5 minutes to fix the issues I'm having with my printer, but even though I followed the ubuntu directions and set a password, when I try to switch into root it's telling me I've got the wrong password.

I need access to the /usr /lib etc. files to copy over a working edition of the drivers, the ones you can download from the software centre are not working for me. 

#-o

---

### Post by papibe on 2011-09-12
> Logged as a regular user do this:
```
$ sudo su
```
and you'll stay working as root.

Be very careful!
Regards.

;-) But first read haqking's links

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> I need to login to root for 5 minutes to fix the issues I'm having with my printer, but even though I followed the ubuntu directions and set a password, when I try to switch into root it's telling me I've got the wrong password.

I need access to the /usr /lib etc. files to copy over a working edition of the drivers, the ones you can download from the software centre are not working for me. 

#-o


Root account is locked by default.

It is not needed and Sudo is supported here.

See here about why sudo is supported in the canonical model and the root account is locked by default, it is possible to enable root and possible to have a blank password but neither are recommended.

Please see here[ rootsudo]("https://help.ubuntu.com/community/RootSudo") as sudo is preferred for all admin tasks (the password you use for sudo is your own password that you login with)

and in addition

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)


See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by (Nes) on 2011-09-12
Where is "Administration" on my ubuntu version?
It's not in system settings (that I can see) did they give in a new name?

---

### Post by sisco311 on 2011-09-12
> **papibe said:**
> Logged as a regular user do this:
```
$ sudo su
```
and you'll stay working as root.

Be very careful!

Regards.

```
sudo -i
```
is the preferred method for starting a root shell in Ubuntu.

If the root account is enabled, then **su -**

Using *sudo su* is pointless and it behavior is not documented in a single man page. 

@OP
Please read the links provided by haqking.

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> Where is "Administration" on my ubuntu version?
It's not in system settings (that I can see) did they give in a new name?

i presume natty narhwal 11.04 ?

Click the applications icon in the panel, then click All Applications in the upper right and select System.

---

### Post by (Nes) on 2011-09-12
sudo -i 

is what I was doing (I've already read the first link, that I what I started from) I remain unable to log into root.

---

### Post by (Nes) on 2011-09-12
And thanks for putting up with my noob-ness guys :D 
You rock ;)

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> sudo -i 

is what I was doing (I've already read the first link, that I what I started from) I remain unable to log into root.

> **(Nes) said:**
> And thanks for putting up with my noob-ness guys :D 
You rock ;)

you dont log into root.

from terminal you type sudo <command> and it will ask for your password which is your user password, this will give your root privelge for the command in the <command> section.

and no problems, its a community working together to support evryone who needs it, even those that give support need it too ;-)

---

### Post by (Nes) on 2011-09-12
I don't have "System" I have "system settings"

---

### Post by sisco311 on 2011-09-12
Don't want to sound rude, but I think this is an XY qeustion. *I want to do X, but I'm asking Y.*

So, please share with as, what are you trying to accomplish? What's your ultimate goal? 

And try to explain the steps you followed and where did you fail.

Thank you!

---

### Post by (Nes) on 2011-09-12
That's what I thought but I need to drag & drop some files so my permissions are not being extended beyond the terminal.

---

### Post by haqking on 2011-09-12
Looks to me like you need access to a folder.

So you can copy the files into it from command using sudo, or by running nautilus with gksudo

but we need a better explanation of what you need to do and why so we can better help

---

### Post by (Nes) on 2011-09-12
Oh! I'm trying to fix the drivers for my brother printer. Every time I ask it to print it just spits out all the paper in it until I turn it off.

I've tried to look up solutions and I'm trying to follow instructions on the brother page, but I'm unable to install the drivers from the ubuntu software centre. I have the correct drivers downloaded onto my computer now but I can't put them in the folders they need to go in :S

So I've got the files right here and I want to drag them into my folder on the (... / directory) and don't have the permissions. All those files are "owned" by root.

---

### Post by (Nes) on 2011-09-12
and I wanted to adjust my password so it's nice and short while I make all these changes to my new ubuntu, but that file is also owned by root.

That is not as big a deal.

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> and I wanted to adjust my password so it's nice and short while I make all these changes to my new ubuntu, but that file is also owned by root.

That is not as big a deal.


ok like ive already said.  Use

sudo 

or

gksudo to run something graphically

so

sudo cp /path /path

or

gksudo nautilus

when asks for password then enter your own, you are now temporarily running your file browser as root.

as for changing your password to a shorter one it is 4 minimum. this can be changed but not recommended

dont enter your root password, enter your own login password.

---

### Post by sisco311 on 2011-09-12
> **(Nes) said:**
> Oh! I'm trying to fix the drivers for my brother printer. Every time I ask it to print it just spits out all the paper in it until I turn it off.

I've tried to look up solutions and I'm trying to follow instructions on the brother page, but I'm unable to install the drivers from the ubuntu software centre. I have the correct drivers downloaded onto my computer now but I can't put them in the folders they need to go in :S

So I've got the files right here and I want to drag them into my folder on the (... / directory) and don't have the permissions. All those files are "owned" by root.

So you are trying to install the driver. Good. Please post a link to the instructions/driver & from there we will be able assist you.

You can deal with the sudo/root stuff later. :)

---

### Post by (Nes) on 2011-09-12
Well I got into root but now it can't find the directories I want and I need to enable user sharing?
*headdesk*

Feels like when I went from skiing for 10 year (windows) to trying to learn to snowboard :D.

---

### Post by (Nes) on 2011-09-12
I've got all my per-required procedures done with no problem, I'm stuck on install.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

As mentioned, I can't get the right drivers to install from the software centre, I can't remember the message it gave me but it just would not work.

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> Well I got into root but now it can't find the directories I want and I need to enable user sharing?
*headdesk*

Feels like when I went from skiing for 10 year (windows) to trying to learn to snowboard :D.


ok you got me completely confused now.

as Sisco311 said above me, can you post a link to the instructions for your driver you are following ?

---

### Post by (Nes) on 2011-09-12
> **haqking said:**
> ok you got me completely confused now.

as Sisco311 said above me, can you post a link to the instructions for your driver you are following ?

That may be because I have no idea what the heck I'm doing :redface:

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> That may be because I have no idea what the heck I'm doing :redface:


Still no link.  Can you post a link to the instructions you are following or its hard to offer support.

cheers

---

### Post by (Nes) on 2011-09-12
> **haqking said:**
> ok you got me completely confused now.

as Sisco311 said above me, can you post a link to the instructions for your driver you are following ?

Oops & sorry, I was trying the gk w nautilus

---

### Post by (Nes) on 2011-09-12
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

Sorry :)

---

### Post by (Nes) on 2011-09-12
I know there have been a few people with this problem, there are more then a couple questions/answer on the forum I just can't seem to get them to work for me :S

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

Sorry :)


ok so like it said.  and i said before use the sudo command.

all the commands you need are there, append sudo to the first command made and should hold for the time needed to carry out rest.

assuming you made sure the pre-required procedures are done

so first command would be:

sudo dpkg  -i  --force-all  (lpr-drivername)

carry this out in the directory where the downloaded driver is

---

### Post by (Nes) on 2011-09-12
Okay now I'm really confused as to what I did, but I did get the files copied over to where I want them and can try to continue on with the install :S

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> Okay now I'm really confused as to what I did, but I did get the files copied over to where I want them and can try to continue on with the install :S


there was no copying required.

you downloaded the driver, you then should cahnge to location of where that is, usually your Downloads directory.

then carry out the commands listed using sudo

---

### Post by (Nes) on 2011-09-12
AHA!!! I wasn't running THAT command as sudo before :D.

I see, I see! :)

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> AHA!!! I wasn't running THAT command as sudo before :D.

I see, I see! :)


linux assumes you know exaclty what you are doing at all times 

read, read, take a break, come back and read again then try ;-)

oh and i refer you back to my first post at post #3...sudo...LOL ;-)

---

### Post by Pariah819 on 2011-09-12
This thread was an interesting read, please remember to mark it as solved if your printer is now working.

---

### Post by (Nes) on 2011-09-12
***ARG!!!!***

Well... it's installed properly and still spitting out every piece of paper it's got ...

---

### Post by (Nes) on 2011-09-12
> **haqking said:**
> linux assumes you know exaclty what you are doing at all times 

Yeah, see that's the problem because I only half-know what I'm doing all the time, on the computer or not :D

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> ***ARG!!!!***

Well... it's installed properly and still spitting out every piece of paper it's got ...


oh well sorry but its time for me to hit the sack, 0230hrs here.

I willl check back tomorrow morning to see the results ;-)

perhaps someone will chime in with more help.

good luck

---

### Post by (Nes) on 2011-09-12
Thanks very much for trying haq - it is GREATLY GREATLY appreciated!! :)

---

### Post by (Nes) on 2011-09-12
No! It DID work, it's just sneaky and created a second printer with the exact same name to trick me!!!

Right... only half knowing what I'm doing all the time ;). 

Thanks again for all the help guys!! Now onto my leapfrog issue... :D

---

### Post by haqking on 2011-09-12
> **(Nes) said:**
> No! It DID work, it's just sneaky and created a second printer with the exact same name to trick me!!!

Right... only half knowing what I'm doing all the time ;). 

Thanks again for all the help guys!! Now onto my leapfrog issue... :D


ok cool, using thread tools mark your thread as solved.

glad we could help.

cheers

---

### Post by (Nes) on 2011-09-12
Even though it ended up working the way it was supposed too (plus a sudo command, lol!) I learned a LOT and I definitely have more reading too do ;)

---

### Post by lisati on 2011-09-12
Apologies for jumping in late about "root" access and administator privileges, it almost looks like a useful link might have been forgotten or lost in a cleanup of the thread somewhere: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by haqking on 2011-09-13
> **lisati said:**
> Apologies for jumping in late about "root" access and administator privileges, it almost looks like a useful link might have been forgotten or lost in a cleanup of the thread somewhere: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


Jump in when you like ;-)  However it was in my first post at post #3

which i referred him back to aafter all this when he realised it was not using sudo that caused the problem...LOL

---

