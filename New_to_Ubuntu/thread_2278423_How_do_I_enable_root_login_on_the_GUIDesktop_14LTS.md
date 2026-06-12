---
title: "How do I enable root login on the GUI/Desktop 14LTS"
date: 2015-05-16
forum: New to Ubuntu
---

### Post by jonjsinger on 2015-05-16
I'm not new to *nix OS however this is the first time I've worked with a desktop/GUI in many years. I searched and it seems that many of the prior solutions posted worked for previous releases but do not work any longer on 14.04 LTS. I also hesitate in asking this question publicly as I do understand the risks and potential consequences of enabling the root account. As such, if someone would be more comfortable sending me a private message I would very much appreciate it and I will follow up with this question providing a reply asking for a moderator to remove/delete my question. 

I am trying to install some proprietary software on ubuntu for development and testing. I have it working on CentOS but I am running into issues with some of the install scripts on Ubuntu where the install is hanging and I believe that logging in as a root user to perform the install may resolve the issue. That's all I want to do is be able to log in as root as one would log in as any other user, install this software and then remove and disable the root account. 

Again, I realize that this is dangerous and risky. I am doing this on a virtual machine. I am documenting the install process of this software and taking snapshots of the VM frequently so that when I blow up the OS (I already have a few times) I can revert it back to prior snapshots. It does not matter if I make mistakes and end up destroying the machine.

---

### Post by dino99 on 2015-05-16
i cant agree with your solution to workaround the scripts issues: its not a professional way  ;) but you already know that
anyway that wiki might resolve your wish (and more) [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by corti-nico on 2015-05-16
Hi,

As you've already said it's *dangerous and risky*.

Anyway you can log as root with command
```
sudo -i
```

Or you can enable root user using command
<snip>

Details: [https://help.ubuntu.com/community/RootSudo#root_account](https://help.ubuntu.com/community/RootSudo#root_account)

---

### Post by jonjsinger on 2015-05-16
Thanks for the fast replies! 

unfortunately I have done all of that. From the command line I can log in and do whatever I need as root however when I try to select or change user there is no option to login as root. I'm not a developer by any means however all I'm trying to do is get a little more information before I go back to the guys who built this thing. I need to ask them to make some changes and recompile however I need to be specific as to the errors I'm getting. If the install works as root then it's a permissions thing however if the install hangs and fails as root then it's on our end as a coding/programming thing --we have only put this on CentOS so since this is the first time I'm trying to put it on Ubuntu... and I was told very specifically that it "should" work without issue... I just need to know if it's a permissions thing or if it's on our end with something in the installer probably being hard-coded for CentOS that doesn&#8217;t fly with ubuntu... if that makes sense. 

I've gone though the wiki's and documentation and have yet to find instructions as to how to get the root user listed on the initial desktop login screen.??? Thanks again for the replies... and yes dino99, I know it's stupid and not professional but it would never be used in production...

EDIT: For clarification, in CentOS we create our users and then at the login prompt you can select "other" and then enter "root" and then its password and login as root for the install and to perform a few specific tasks, and then logout and log back in as a normal user... if that makes sense... That's all I want to be able to do however it seems that Ubuntu may not allow for that.

---

### Post by cariboo on 2015-05-16
Using:

```
sudo -i
```

allows you run as root, you should be able to run your install commands from the prompt.

---

### Post by dino99 on 2015-05-16
glance at the link provided on my first post, where it talk about 'sudoers', and add the required 'user' to the admin group

and something that ubuntu name 'oem' installation: 
old wiki example  [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/228687/difference-between-oem-install-and-custom-ubuntu-image](http://askubuntu.com/questions/228687/difference-between-oem-install-and-custom-ubuntu-image)

---

### Post by mastablasta on 2015-05-18
> **dino99 said:**
> glance at the link provided on my first post, where it talk about 'sudoers', and add the required 'user' to the admin group



or perhaps even add the script to sudoers.

it should then be able to run with root privileges without passord needed. i means since you trust the source it shouldn't be an issue.

in about 6 hours after opening the port, root user got attacked by "chinese". however it was disabled. so... :P

---

### Post by grahammechanical on 2015-05-18
I think that we are missing something here.

Because of the risk we do not go into great detail about this subject on this forum. Especially in a section labelled New to Ubuntu. As I understand things it is recommended that we post a link to the relevant Ubuntu wiki page and leave it at that. And that has already been done.

That wiki page makes the point that if we give someone directions on how to enable the root account on Ubuntu then we must be prepared to give individual help to that person if the power of working as root messes up their OS.

> **Please keep in mind, a substantial number of Ubuntu users are new to Linux.**  There is a learning curve associated with any OS and many new users try  to take shortcuts by enabling the root account, logging in as root, and  changing ownership of system files.

It is logical to think that new users would look in a section called New to Ubuntu.

> [B]If you disable the sudo password for your account, you will  seriously compromise the security of your computer. Anyone sitting at  your unattended, logged in account will have complete root access, and  remote exploits become much easier for malicious crackers.

[/B]
[LIST]
[*]**This method is NOT suggested nor supported by the designers of Ubuntu.** 
[*]Please  do not suggest this to others unless you personally are available 24/7  to support the user  if they have issues as a result of running a shell  as root. 
[/LIST]


Why are we even discussing this? The question was answered with the link to the wiki page. Each of us takes personal responsibility for how we use our computers.

---

