---
title: "software center issue in 14.04"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by windowsfree on 2014-04-23
when i attempt to install software, I get this message:
[ATTACH=CONFIG]252432[/ATTACH]

noted not all software installs cause this.  i did install gparted, it shows under Settings but is not usable.  
[ATTACH=CONFIG]252432[/ATTACH]

what has to be done?


thank you.

---

### Post by Wilson_Perdomo on 2014-04-23
Take a look at this link. It seems to be a problem with policykit not running up at startup.
[http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center](http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center)

---

### Post by windowsfree on 2014-04-24
did as stated - see attached screenshots.  ([http://askubuntu.com/questions/21896...oftware-center]("http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center"))
policy kit authentication agent is checked in startup.

---

### Post by windowsfree on 2014-04-30
I re-installed Xubuntu and issue persists.  I can also add, everytime now that I log into account, I get a system crash that asks to be reported.  this popup appears three times.  I find this very non-productive.  So the system crashes and the software installs are my major problem.  I am going to attempt to install other distro to see if it is my hardware combo that causes the issue or is the Xubuntu distro.   
Any suggestions welcome.

---

### Post by LastDino on 2014-04-30
I really doubt it has anything to do with hardware. Have you tried manually enabling it in GI front end rather than command line?  
''settings>system>season and start-up>application auto start>policy-kit ....'' 
Tick mark the box in front of policy kit.

Also please check ''software update'' option in settings. Go into ''Authentication'' window and see if you see the same thing as I do on my Xubuntu 14.04

[ATTACH=CONFIG]252668[/ATTACH]

---

### Post by windowsfree on 2014-04-30
I have tried the GUI and mine is the same as yours.

I installed SolydX and no issues with that, other than the wireless card.  SolydX does run a bit slower though.  I may format my partition and try Xubuntu again.

I appreciate your quick response, thank you.

---

### Post by LastDino on 2014-04-30
That is rather odd, I'll subscribe  the thread just to see what kind of solution is found. Sorry for not being much of help :/

---

### Post by windowsfree on 2014-04-30
no problem,  in between posts, i have installed Ubuntu and did not have the software issue, although the Netbook was very slow with that OS.  I downloaded the Xubuntu ISO again and attempted it and had less system crashes but still had the software install issue.  Thanks for subscribing, I will post results, hope to get some time with it this Sunday.

Thank you.

---

### Post by pfeiffep on 2014-04-30
> **windowsfree said:**
> no problem,  in between posts, i have installed Ubuntu and did not have the software issue, although the Netbook was very slow with that OS.  I downloaded the Xubuntu ISO again and attempted it and had less system crashes but still had the software install issue.  Thanks for subscribing, I will post results, hope to get some time with it this Sunday.

Thank you.

Not an answer to your original question:KS
 ... I found that Ubuntu 14.04 'out of the box' was sluggish on my old laptop so I installed [gnome flashback]("https://wiki.gnome.org/action/show/Projects/GnomeFlashback?action=show&redirect=GnomeFlashback") and I'm quite impressed with the how quick this machine is. I personally like the Metacity choice provided by flashback. I beleive it's located in the software center.

---

### Post by windowsfree on 2014-04-30
Thanks Pete,

I did try that and it seemed ok.  If SolydX does not work for me, I will attempt Xubuntu again.

---

### Post by LastDino on 2014-04-30
Well, since you're on that popular distro ''testing'' journey as it is, I think you should have a look at Fedora-Xfce just in case Xubuntu doesn't work for you at the end of the day. It more or less feels like using Xubuntu with different package manager.

---

### Post by windowsfree on 2014-04-30
Thanks,  I actually have Fedora XFCE 19 running on a 9 year old laptop that has a celeron 1.4ghz cpu, 1 gig of ram in it.  It even configured the broadcom wireless card out of the box.

---

### Post by ian-weisser on 2014-04-30
> **windowsfree said:**
> what has to be done?

If there is an existing bug report on the issue, subscribe to it and help test patches.
If there is not an existing bug report, make one. That's a bad bug!

One workaround: You can install using the command line - that doesn't use PolicyKit.
Another workaround: You can start PolicyKit manually before telling Software Center to install/remove software.

---

### Post by windowsfree on 2014-04-30
Thanks, I have installed software from the command line, I currently have the OS off the computer and will try a few things prior to installing.   I appreciate your input to this issue.

---

### Post by Warren Hill on 2014-04-30
I've just checked and I don't see a bug reported so I suggest you report one.

If you don't have a launchpad account already [create one]("https://help.launchpad.net/YourAccount/NewAccount")

If you can repeat the bug do so the open a terminal and enter

```
ubuntu-bug -w
```

and click on the software center window.

If the bug is not easy to replicate go [here]("https://launchpad.net/software-center") and click on "Report a bug"

---

### Post by windowsfree on 2014-04-30
**I appreciate the info, but as stated above, the OS is no longer on the computer.   There are screenshots in this thread, but probably not enough information.**

---

### Post by windowsfree on 2014-05-05
to close this thread, uninstalled the OS and reinstalled Ubuntu 14.04 - no issues.

---

