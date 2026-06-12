---
title: "[SOLVED] Terminal does not give root option?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by socngill on 2008-11-06
OK.  had my last thread deleted as helping make root easy to use is a big no, no.

So I am going to ask a more straight forward question which I hope will not get anybody's back up.

Before I upgraded from 8.04 to 8.10 I could open up the terminal, go to options (or something along those lines) and select open as root (or with root priveladges - I can't remember the exact text as I am on an XP machine at the moment).  But in 8.10 that option is no longer available.  

I was trying to install some drivers and software for a new webcam but it came up with "are you root?", but I can not access a root terminal anymore.

Is this another "security" issue that has been put in place to stop us from accidently selecting a drop down menu, then accidently selecting a root option, and then accidently using said root terminal to perform a task which didn't need root, which leads to the system crashing, creating a spark in the electrics which blows up the house, causing all the houses in my street to also blow up, which eventually creates a black hole which the entire universe gets sucked into and all that we know ceases to exist?

Or do i simply need to amend a setting or install something which the upgrade missed?

Thanks.

---

### Post by llamakc on 2008-11-06
If you type in a Terminal 

```

sudo -i

```

You will be dropped into a root environment. Remember to exit out of it, and as always BE CAREFUL. I still recommend just using

```

sudo NAME_OF_COMMAND

```

as a one-time method instead.

---

### Post by handydan918 on 2008-11-06
Ya know, I feel your pain. I am not in agreement with the "root" policy here either. 
As an alternative, I would suggest:

1) If you want root and Gnome, use Debian.

2) If you want root and KDE, use MEPIS.

---

### Post by socngill on 2008-11-06
Cheers people.  I was hoping for a way to get the root option back, but maybe it is no longer possible.

Seeing as I will already be in the terminal, typing the root command won't be too much of a hassle :D

However, if I can get the option back that would be great.

---

### Post by Kellemora on 2008-11-06
I haven't tried 8.10 yet, but can't you just right click on Applications and INSTALL (Edit Menus) the Root Terminal like you could on 8.04?

TTUL
Gary

---

### Post by overdrank on 2008-11-06
> **socngill said:**
> OK.  had my last thread deleted as helping make root easy to use is a big no, no.

So I am going to ask a more straight forward question which I hope will not get anybody's back up.

Before I upgraded from 8.04 to 8.10 I could open up the terminal, go to options (or something along those lines) and select open as root (or with root priveladges - I can't remember the exact text as I am on an XP machine at the moment).  But in 8.10 that option is no longer available.  

I was trying to install some drivers and software for a new webcam but it came up with "are you root?", but I can not access a root terminal anymore.

Is this another "security" issue that has been put in place to stop us from accidently selecting a drop down menu, then accidently selecting a root option, and then accidently using said root terminal to perform a task which didn't need root, which leads to the system crashing, creating a spark in the electrics which blows up the house, causing all the houses in my street to also blow up, which eventually creates a black hole which the entire universe gets sucked into and all that we know ceases to exist?

Or do i simply need to amend a setting or install something which the upgrade missed?

Thanks.

Hi and your last thread was not deleted but merely closed. :)
As I linked in your last thread the policy on the forums of root login, the advice given is the best as use sudo.

---

### Post by socngill on 2008-11-06
Cheers for all the replies.  Looks like I will have to do it the sudo way.  Sure I will get used to it :)

I have actually discovered that a major issue on my upgrade is that AT seems to have not been installed.  So maybe that has caused this issue as well?  But I have started another thread for that little problem :D

---

### Post by Kellemora on 2008-11-06
You mean to tell me that the new 8.10 release is beginning to take on the characteristics of GASP Mickey$oft WinDOZE??????

I came to Ubuntu to GET AWAY from WinDOZE, NOT end up back in the same pot of boiling oil!

What are they going to revert down to from that?  Syntax Error!!!!!

TTUL
Gary

---

### Post by B34ST1Y on 2008-11-06
> **socngill said:**
> OK.  had my last thread deleted as helping make root easy to use is a big no, no.

So I am going to ask a more straight forward question which I hope will not get anybody's back up.

Before I upgraded from 8.04 to 8.10 I could open up the terminal, go to options (or something along those lines) and select open as root (or with root priveladges - I can't remember the exact text as I am on an XP machine at the moment).  But in 8.10 that option is no longer available.  

I was trying to install some drivers and software for a new webcam but it came up with "are you root?", but I can not access a root terminal anymore.

Is this another "security" issue that has been put in place to stop us from accidently selecting a drop down menu, then accidently selecting a root option, and then accidently using said root terminal to perform a task which didn't need root, which leads to the system crashing, creating a spark in the electrics which blows up the house, causing all the houses in my street to also blow up, which eventually creates a black hole which the entire universe gets sucked into and all that we know ceases to exist?

Or do i simply need to amend a setting or install something which the upgrade missed?

Thanks.

try creating a script that simply enters in "sudo -i" ...make it an icon where you want to create a root command shell. Problem solved :)

---

### Post by socngill on 2008-11-07
I didn't realise you could do that?  Create a command that would open the terminal and auto fill it?

Would love to know how please :)

---

### Post by B34ST1Y on 2008-11-07
Actually, I figure there's an easier way for you. Try opening a terminal, and create a new profile. Under profile preferences there's an option to run a command at the start of terminal, and then either terminate the window, or continue (we want to continue). Enter the command ```
sudo -i 
``` into the box, and make sure the tickbox is selected for it.

THEN

close that window, go back to your terminal window. edit > profiles .  Select your new theme as the default theme. 


You should now have a root terminal everytime you click your regular terminal box. :)

---

### Post by keplerspeed on 2008-11-07
whenever I need to use sudo multiple times I would usually 'sudo su' first, and then exit when im finished. I find it convenient.

sudo is there for safety, and to make you think before you do.

---

### Post by socngill on 2008-11-07
Cheers B34ST1Y.  I shall give that a go this evening.  Are you any good at solving AT problems :( [http://ubuntuforums.org/showthread.php?t=973393](http://ubuntuforums.org/showthread.php?t=973393)

---

### Post by socngill on 2008-11-07
> **B34ST1Y said:**
> Actually, I figure there's an easier way for you. Try opening a terminal, and create a new profile. Under profile preferences there's an option to run a command at the start of terminal, and then either terminate the window, or continue (we want to continue). Enter the command ```
sudo -i 
``` into the box, and make sure the tickbox is selected for it.

THEN

close that window, go back to your terminal window. edit > profiles .  Select your new theme as the default theme. 


You should now have a root terminal everytime you click your regular terminal box. :)

OK, I have created a new profile, and there is a box which says command next to it, defualt is /bin/bash.  I have tried adding sudo -i and replacing it with sudo -i but it doesn't seem to make any difference?  Also there is no mention of continueing or terminating the window?  I might be in the wrong place????

---

### Post by bodhi.zazen on 2008-11-07
> **socngill said:**
> Is this another "security" issue that has been put in place to stop us from accidently selecting a drop down menu, then accidently selecting a root option, and then accidently using said root terminal to perform a task which didn't need root, which leads to the system crashing, creating a spark in the electrics which blows up the house, causing all the houses in my street to also blow up, which eventually creates a black hole which the entire universe gets sucked into and all that we know ceases to exist?

Yes this is how security works in Ubuntu.

See this post : [http://ubuntuforums.org/showpost.php?p=5769207&postcount=77](http://ubuntuforums.org/showpost.php?p=5769207&postcount=77)

These types of security measures are ubiquitous to all modern OS, including windows. If you are asking for assistance on the Ubuntu forums you will be given the standard answers. These answers are intended to teach you to use your new OS and have been graciously given to you by many more experienced users. It does take some adjustment (I came from a rpm system myself), but most users prefer it. Sudo has a number of powerful features that are simply lacking in su.

See : [uwiki]RootSudo[/uwiki]

If you prefer not to run your system this way, that if fine with us. In that case you are more then welcome to use Google or RTFM and do as you wish. And the best part is, if you break Ubuntu you get to keep both pieces.

I would advise you that ranting on the design of Ubuntu is unlikely to get you the assistance you seek. If you do not like Ubuntu, I suggest Fedora, SUSE, Slackware, Debian, Gentoo, Arch, FreeBSD, OpenSolaris, or even Windows.

I am sure you can look at all your options and find the OS that best suits your style and needs. But ranting that, for example, OpenSolaris does not work like Windows is counter productive.

---

### Post by socngill on 2008-11-07
sudo apt-get install --reinstall sense of humour

Kubuntu works great for me and I have no real issues with it.  The actual quesitons I have been asking is in relation to what appears to be changes from 8.04 to 8.10, that's all.

I am having all sorts of issues following an upgrade from 08.04 to 08.10 with AT not installing and I can't install, reinstall anything.  I am wondering if that is why some things are missing.  but as nobody has answered my plea for help in another thread I have been unable to ascertain if this is the problem or not.

If all of these changes are supposed to be in place then that's fine, i'll get used to the changes.  but I have received no help thus far on the main problem so I may just have to do a clean install and see what happens.  I don't want to do that as I don't want to spend half a day re-installing all the software I want.

---

### Post by maybeway36 on 2008-11-07
Try making a desktop shortcut to "konsole -e sudo -i".

---

### Post by socngill on 2008-11-07
> **maybeway36 said:**
> Try making a desktop shortcut to "konsole -e sudo -i".

Done, and done

:guitar:

---

### Post by B34ST1Y on 2008-11-07
> **maybeway36 said:**
> Try making a desktop shortcut to "konsole -e sudo -i".

good call. Most roads lead to Rome, here. :-P 


my way worked fine for me, but hey that's good too!

---

