---
title: "Ubuntu with Linux 3.0.0-12-generic"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Paulie746 on 2013-06-16
Hi I'm pretty new to Ubuntu I just got an acer aspire one from one of my friends when I start it up it comes to screen where I can click on Ubuntu or do a recovery or a memory test the problem is that it won't boot up and when I try to do a recovery it starts and then this comes up 

/lib/recovery-mode/recovery-menu:line109:/lib/recovery-mode/options/whiptail :
: no such file found or directory 

How do I fix it or is it even fixable please help thanks

---

### Post by Impavidus on 2013-06-16
Kernel 3.0 was used in Ubuntu 11.10, which is no longer supported. It doesn't boot and you just recieved it, so you don't have any valuable data or even customisations on it. You don't know what happened in the past to the system and neither do we, so anything may be wrong. My suggestion: wipe the hard drive and install a supported version. I suggest you make a live disk of Ubuntu 12.04 (or Xubuntu, or Kubuntu, or any other flavour or variant), boot from the live medium and decide whether you like it. Then install. It will be faster than troubleshooting your current problem. Ubuntu 12.04 is a long term support version, so you will recieve security updates until 2017.

---

### Post by Paulie746 on 2013-06-23
thanks for the help i installed 12.04 and its working great i have one more qeustion thou ive installed comodo for my virus protection i have this for my windows it wants me to run /opt/COMODO/post_setup.sh but when i try it tells me that i need adminastrator permission how do i do that

---

### Post by Paulie746 on 2013-06-23
thanks for the help i installed 12.04 and its working great i have one more qeustion thou ive installed comodo for my virus protection i have this for my windows it wants me to run /opt/COMODO/post_setup.sh but when i try it tells me that i need adminastrator permission how do i do that and sorry it took so long to answer back i was useing my phone and for some reason it wasnt updateing the reply

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]Paulie746; Hi !

Glad you are making the switch..
Administrative authority is gained by using the term "sudo" -no quotes-  == Supper User Do.
Any time access to modify a system file outside of your home directory is needed precede the command with that term sudo, your password will be required (same one used to log onto ubuntu) and there will be no response to the screen ...security reasons.
Is comodo a Windows  application ? As I do not see it in 13.04's software repository I do not know where you got it from. You are aware that you can not run Windows' aps on ubuntu's file system directly ?

Over abundance of info available from the system's manual on commands; Terminal code:
```
man sudo
``` where man == manual and the argument to man is a command or application name
try for reference:
```
man gedit
``` where gedit is the default text editor in ubuntu.

Food for thought: I have ran ubuntu for many years...with NO virus protection and have yet to suffer an adverse affect. There are those who do have virus protection installed, mostly to protect Windows. Presently I know of no virus out there that can effect ubuntu. The ubuntu file system is "closed"-no ports initially open to the outside world. However, security is a issue that does not hurt to study up on - security of ubuntu - and decide for your self if additional measures should be taken... Who knows what may perchance tomorrow. Be aware I do have a firewall in my router.
[/COLOR][INDENT=2][COLOR=#000000]
and again, welcome to our wonderful world of open source

[/COLOR][/INDENT]

---

### Post by mastablasta on 2013-06-24
right clicking the file and then run as root is will also run it in administrator mode. root= administrator

---

### Post by Paulie746 on 2013-06-24
yes it is a windows program but they have the opiton for linux google comodo its pretty good just being a windows user since windows 98 came out lol just figured id better put some kind of protection on here you guys rock i tell you that much everyones been a big help so far thanks

---

