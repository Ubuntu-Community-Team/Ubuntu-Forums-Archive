---
title: "First Application Install Help?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by kevn3k on 2008-05-23
Hi everyone.  I just installed Xubuntu onto my IBM Thinkpad A31 (256 MB RAM, Pentium 4-M Processor)and I was hoping to get some help.  I'm planning on installing Skype onto this laptop (not for video, since I doubt the machine can handle it, just for voice) but I'm not sure how to do it once I've downloaded the version (I'm assuming using Skype's release for Ubuntu 7.04+ will work on Xubuntu). Can someone walk me through this?

When I download the file, it saves as skype-debian_2.0.0.68-l_i386.deb (which is a Debian GNU/Linux Package from [http://download.skype.com](http://download.skype.com))... where do I go from here?  Also, the l_386.deb might be 1_386.deb, I'm not used to the standard box font yet.

---

### Post by drs305 on 2008-05-23
deb file installation is easy. For a .deb file, just double-click the downloaded deb file and it's installed. Done. :)

---

### Post by HotShotDJ on 2008-05-23
Please DELETE the file you downloaded.

Now, go to System --> Administration --> Synaptic Package Manager
Search for "Skype"
Install Skype
Be amazed at how easy it is. :)

---

### Post by philinux on 2008-05-23
Skype is in synaptic same version. Either use system>admin>synaptic and install it from there or in a terminal

sudo apt-get install skype

Or you could just double click the deb file it's like a setup.exe file

---

### Post by neurostu on 2008-05-23
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) 
> 
skype is not available in any Ubuntu software repository, and therefore cannot be installed with Ubuntu's package management software such as Synaptic or apt-get without adding a repository containing Skype. There are two options - the Skype repository, or the Medibuntu repository.

Go to the link above, it has detailed instructions on how to install skype.

the ubuntu repositories are great but they don't contain everything. Atleast for 7.1 running:
```

aptitude search skype

```
yields no results.


download the .deb file from here:[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
then run it from your desktop, that will install skype

---

### Post by shrimphead on 2008-05-23
you need to enable the Ubuntu Partner repo IIRC for skype to show up in synaptic/aptitude

---

### Post by kevn3k on 2008-05-23
wow, thanks for all the responses! :) looks like it's up and running!

---

### Post by HotShotDJ on 2008-05-23
You may be right about which repository.  Since I have Medibuntu repositories activated, that is probably why I found it without a problem using Synaptic.

That being the case, I strongly recommend that you activate Medibuntu repositories (for several good reasons, actually).  See: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Downloading deb files and then installing using gdebi should be the second-to-last effort (last should be compiling from source).

---

### Post by neurostu on 2008-05-23
> **HotShotDJ said:**
> 
Downloading deb files and then installing using gdebi should be the second-to-last effort (last should be compiling from source).

Why should that be a 2nd to last resort? installing a .deb file using dpkg is simple easy and fast, and it is just as easy to uninstall the program using dpkg.  

Apt and synaptic are essentially just front ends to dpkg.  The deb files them selves define their own dependencies and wont install if you don't have all the dependencies installed.  Installing a .deb by hand is just as good as using a package manager. 

If you worry about being able to trust the source of the file that concern can be raised about adding other repositories to your repo list. In fact I feel that adding different repos to your list is more INSECURE then downloading the debs from trusted sources.

---

### Post by HotShotDJ on 2008-05-23
> **neurostu said:**
> Why should that be a 2nd to last resort? installing a .deb file using dpkg is simple easy and fast, and it is just as easy to uninstall the program using dpkg.First of all... yes, trust IS an issue.  And I say the same thing about adding repositories.  Use only well-established, trusted repositories (such as Medibuntu, WineHQ, and some others).  However, there is also the business of keeping up with security upgrades.  Using trusted repositories will seamlessly integrate the software into ubuntu's update system.  Downloading and installing either using dpkg or gdebi bypass this.  Now the user must manually keep up with updates.

Yes, using dpkg is simple and gdebi is even simpler.  But that is not the point.  Searching the net and downloading applications and installing them separately is the way Windows has trained its users to behave and is one of the things that leads to system instability.  Using repositories is safer, easier and is the Ubuntu way, and new users should learn how to use it right from the beginning.

---

### Post by neurostu on 2008-05-23
Ok so you're totally correct about the security updates.  If you install the .deb's yourself you have to stay on top of things. The point I was trying to make wasn't that it is better to use  dpkg or gdebi.
> 
. Searching the net and downloading applications and installing them separately is the way Windows has trained its users to behave and is one of the things that leads to system instability. Using repositories is safer, easier and is the Ubuntu way, and new users should learn how to use it right from the beginning.

What?  The linux way of doing things is to EMPOWER THE USER! Giving the user total control and CHOICE over their system.   Yes the majority of the Ubuntu COMMUNITY does things a certain way, but that by no means implies that everybody who uses ubuntu has to do them the same way, nor that is the best way of doing things.

You start by saying that "Windows has trained its users" then saying "New users should learn how to use it right from the beginning", you essentially critisize windows for training a behavior into people only to try and retrain them with a new behavior.  People shouldn't be trained, they should be taught how to make intellegent decisions.  Thats why I don't agree with :> Downloading deb files and then installing using gdebi should be the second-to-last effort (last should be compiling from source).
Because:
1. You provide a blanket statement that implies it holds on all circumstances
2. You set in stone the order or Best, Worst.

Linux isn't about this, linux is about being free (as in beer and speech). We need to empower the new linux users to make intellegent choices on their own not because we tell them what those intellegent choices are.

---

### Post by HotShotDJ on 2008-05-23
> **neurostu said:**
> You start by saying that "Windows has trained its users" then saying "New users should learn how to use it right from the beginning", you essentially critisize windows for training a behavior into people only to try and retrain them with a new behavior.No, I did NOT criticize Microsoft for training a behavior.  I criticized Microsoft for training POOR behavior.  The remedy for correcting a learned poor behavior is to train people in the BETTER behavior.

And yes, Linux gives the user many choices.  And for each choice, there are consequences.  There are more negative consequences for installing an application that is available from a trusted repository than there are for downloading a program and installing it using gdebi or dpkg.  Therefore, while users should learn about all their choices, it would be irresponsible of me to present them all as equal.  They are not.  There DOES exist a hierarchy that runs approximately from Best to Worse.  Sometimes, the "Worse" or even "Second-to-Worse" options are the appropriate choices.  This was not one of those cases.

I really don't want to further argue this with you in this thread.  Now that I've made myself clear, you are of course free to disagree with me.  If you'd like to further discuss the issue, you can start a thread in the Community Cafe and I'll be happy to join you there. :)

---

