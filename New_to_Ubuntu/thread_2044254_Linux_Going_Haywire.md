---
title: "Linux Going Haywire"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by linuxn00bface on 2012-08-19
Hey guys, Linux noob here, so while I can describe the symptoms, I can't do much beyond that.

1. When I click the left hand menu bar for the VPN GUI I use, it flashes like it'll open, then doesn't. Repeated clicks yield the same result.

2. There's a "Do not enter" red/white minus (-) sign thing next to the battery indicator
, top right of the screen. I'm using the Chinese version, and it basically says:
"Encountered error. Please run the package manager or apt-get to see what it is.
Error msg: Error: Open Cache (E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.
)  This is usually because the package you were about to install can't meet the conditions for software compatibility"

Wtf, mate?

3. The Package manager just closes after opening for a few seconds.

4. Probably unrelated, but I ran the output.txt here after fixing that Youtube Flash blue tint bug ...                                                          [FONT=Liberation Serif, serif]http://ubuntuforums.org/showpost.php?p=6749149&postcount=3[/FONT]


[FONT=Liberation Serif, serif]Where does the output.txt file actually go, and how to open it?[/FONT]


[FONT=Liberation Serif, serif]Thanks you guys
[/FONT]

---

### Post by linuxn00bface on 2012-08-19
[http://ubuntuforums.org/showpost.php?p=11797047&postcount=2](http://ubuntuforums.org/showpost.php?p=11797047&postcount=2)
Btw I assume I should try this, and I'd like to know what I'm doing, why the problem occurred, and how this guy knew that this would solve it. Basically, what is he trying to accomplish with these commands:

> 
     Code:
     sudo rm -vf /var/lib/apt/lists/* 
and then see if you can update/upgrade as normal.

If that doesn't work, try:

     Code:
     sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status sudo apt-get update && sudo apt-get upgrade # or sudo apt-get dist-upgrade if no dependency issues

---

### Post by Paqman on 2012-08-19
Have you got the "haywire" feature enabled? If so, turn it off.

Seriously though, let's have a look at what you've been told to do:
```
sudo rm -vf /var/lib/apt/lists/* 

```

This uses Super User powers (sudo) to remove (rm) everything in the location /var/lib/apt/lists/, which is part of the config for your package manager.


```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED

```

This uses sudo to move (mv) the file at /var/lib/dpkg/status to a new location with a different name. Basically it makes a backup copy of the file. This is always good practice when editing config files.

```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

This copies (cp) the old status file and puts it where the current one is, overwriting it. So you've now backed up your current config and rolled back to the previous one.

```

sudo apt-get update && sudo apt-get upgrade

```

Contacts the repositories and checks for updates, then installs them.

```

or sudo apt-get dist-upgrade
```

This is a slightly beefed-up version of apt-get upgrade that will install and remove packages if required. The basic apt-get upgrade won't install or remove anything as a safety feature.

---

### Post by Bashing-om on 2012-08-19
=>:face;
  In addition to the last post: NikTh has this solution:
from:  [https://answers.launchpad.net/ubuntu/+source/apt/+question/206222](https://answers.launchpad.net/ubuntu/+source/apt/+question/206222)
quote:
[NikTh (nick-athens30)]("https://launchpad.net/%7Enick-athens30")          said     15 hours ago:                  #2               Hello ,
 please close all other applications and open only a terminal (ctr+alt+t)
 copy-paste from here to your terminal the below commands one at time . One line=One command.
 +++++++++++++++++++++++++++++
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get dist-upgrade
+++++++++++++++++++++++++++++
 Make all the updates . If error occur please post it here.
Thanks

---

### Post by Jay MC on 2012-08-19
> **linuxn00bface said:**
> Btw I assume I should try this, and I'd like to know what I'm doing, why the problem occurred, and how this guy knew that this would solve it. Basically, what is he trying to accomplish with these commands:

This is an interesting point.

When providing help, the easiest and most efficient thing to do is provide commands.  Even if fixes can be done in the gui, it's far easier and faster to provide a line of text that can be copied and pasted into Terminal (otherwise, you'd have to say click on this, click on that, do this, do that, etc.).

But a potential problem is that some newbies (not necessarily talking about the OP) might find this daunting.

For starters, the commands aren't instantly lucid to a layman, and you don't necessarily know what they're doing.  It's a bit like being told to recite a spell to make something happen.

Also, when non-Linux users happen to read Linux support forums, they would be forgiven for thinking (based on the amount of commands provided) that Linux users have to do everything from a command prompt.  I think this is why complete newbies are surprised by the usability of stuff like the software centre (or even Synaptic) and the launcher.  If you had only support forums to go by, you might think that Linux was all about typing impenetrable commands.

This isn't a criticism of the people who are kind enough to provide help, because the easiest and quickest way to help someone is to provide a command.  But I think it presents an interesting dilemma for Linux, in terms of appealing to users of Windows, Mac OS, etc..

---

### Post by linuxn00bface on 2012-08-20
Hey guys, thanks for all your help. I did what people suggested and it cleared the ( - ) do not enter sign, but there is still something weird going on, and what was originally just my VPN app not opening, now includes Teamviewer, which I only downloaded and installed so my VPN could troubleshoot the problem! I tried opening them via the terminal, no dice there either.

Why are some of my apps not opening?!

EDIT: This might have something to do with it... every once in a while a dialog window will appear, in Chinese and translated roughly as "Detected a system program problem. Do you want to report the problem?" Then a Cancel button, and a Report Problem button. Help, pwease.

---

### Post by newb85 on 2012-08-20
The files at /var/lib/apt/lists/ are list files that apt (the package manager for Ubuntu) uses to keep track of information about your setup.  However, if they are missing, apt creates them.  (They basically save apt the trouble of tracking down certain information if they're there.)  If the lists are corrupted, it creates problems with apt (and by extension, any GUI package managers built on apt) that are most easily remedied by deleting the lists.

On your other issues, you should provide more information.  "The VPN GUI I use" isn't very specific.  However, I would first try rebooting (in case there are hanging processes keeping them from opening), and if that didn't work, I would try reinstalling the programs that aren't starting (in case there are missing dependencies).

Question 4 should have been posted on the thread you linked.  However, the file will be in your Home folder.  The default program to open it is Gedit.

---

### Post by linuxn00bface on 2012-08-21
> **newb85 said:**
> The files at /var/lib/apt/lists/ are list files that apt (the package manager for Ubuntu) uses to keep track of information about your setup.  However, if they are missing, apt creates them.  (They basically save apt the trouble of tracking down certain information if they're there.)  If the lists are corrupted, it creates problems with apt (and by extension, any GUI package managers built on apt) that are most easily remedied by deleting the lists.

On your other issues, you should provide more information.  "The VPN GUI I use" isn't very specific.  However, I would first try rebooting (in case there are hanging processes keeping them from opening), and if that didn't work, I would try reinstalling the programs that aren't starting (in case there are missing dependencies).

Well, Teamviewer is crashing just like my VPN. They simply don't open... what do I do? Nobody seems to have any idea, and my VPN company says it's not "compatible," even though I was using it last week with no probs.

>  Question 4 should have been posted on the thread you linked.  However,  the file will be in your Home folder.  The default program to open it is  Gedit.

Thread is three years old. Help?

---

### Post by newb85 on 2012-08-21
Please give the name of the VPN frontend you are using.  

Did you try my suggestions?

What exactly is the problem you're trying to solve with Question 4?  The post you linked has nothing to do with a blue tint in flash.  If your flash videos (such as youtube) are all showing up with a blue tint, that issue is addressed [here]("http://ubuntuforums.org/showthread.php?t=2043694&highlight=flash+blue").

---

### Post by linuxn00bface on 2012-08-21
> **newb85 said:**
> Please give the name of the VPN frontend you are using.  

Astrill.

> Did you try my suggestions?Yes, I tried your suggestion. Unfortunately, while it got rid of the do not enter icon up top as I mentioned, the error
 ( "
 every once in a while a dialog window will appear, in Chinese and  translated roughly as "Detected a system program problem. Do you want to  report the problem?”
 ”&#65289;
 
 is still occurring.
> 
 What exactly is the problem you're trying to solve with Question 4?  The  post you linked has nothing to do with a blue tint in flash.  If your  flash videos (such as youtube) are all showing up with a blue tint, that  issue is addressed [here]("http://ubuntuforums.org/showthread.php?t=2043694&highlight=flash+blue").With Question 4, the problem I'm trying to solve is where that output  file actually went. I solved the blue issue by installing the patched  libvdpau.

---

### Post by newb85 on 2012-08-22
> **linuxn00bface said:**
>   Yes, I tried your suggestion. Unfortunately, while it got rid of the do not enter icon up top as I mentioned 
You mentioned that before I ever posted to this thread.

> **linuxn00bface said:**
> the error
 ( "
 every once in a while a dialog window will appear, in Chinese and  translated roughly as "Detected a system program problem. Do you want to  report the problem?”
 ”&#65289;
 
 is still occurring.
That dialog window was Apport.  And did you tell Apport to report the problem?  If it's a bug, the developers can't fix it unless they know it exists.  Also, Apport would have offered you more information on the problem.  You should post that information in this thread so that the experts (not me) have a much better idea of what's going wrong.

> **linuxn00bface said:**
> With Question 4, the problem I'm trying to solve is where that output  file actually went. I solved the blue issue by installing the patched  libvdpau.
Did you try looking in your Home folder, as I said before?

---

### Post by linuxn00bface on 2012-08-22
> **newb85 said:**
> You mentioned that before I ever posted to this thread.


That dialog window was Apport.  And did you tell Apport to report the problem?  If it's a bug, the developers can't fix it unless they know it exists.  Also, Apport would have offered you more information on the problem.  You should post that information in this thread so that the experts (not me) have a much better idea of what's going wrong.


Did you try looking in your Home folder, as I said before?

Crap I'm sorry, I've been all over the place these days. Yes it was in my home folder, thank you. And yes, I told Apport to report the report the problem. I guess being a Mac convert, I just assume that these things take forever and I might as well go straight to the experts (this forum) to see if I can get it addressed myself. Will reporting it give them enough details to fix it? My Linux really is messed up these days, I'm worried it's on the brink of breaking. Errors left and right popping up.

Oh, and I still [can't get Chinese working]("http://ubuntuforums.org/showthread.php?p=12180881#post12180881") :\

---

### Post by newb85 on 2012-08-23
> **linuxn00bface said:**
> I guess being a Mac convert, I just assume that these things take forever and I might as well go straight to the experts (this forum) to see if I can get it addressed myself. [\QUOTE]

It might take forever, or it might be fixed within a week.  On a few occasions, I've had the package contact me within a day and issue a fix within a week.

[QUOTE=linuxn00bface;12189529]Will reporting it give them enough details to fix it?

It will give them a lot of detail from the technical side, but if you want to give them an explanation of what you're trying to do and what you're experiencing, that could be helpful, too.  When the error message comes up, note what package it's associated with.  Then, search launchpad.net for the bug and comment on it.

---

