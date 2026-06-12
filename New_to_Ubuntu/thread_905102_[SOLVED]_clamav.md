---
title: "[SOLVED] clamav"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Camilia on 2008-08-30
I want to use clamav. Read at 1st day in ubuntu post that, according to DRDN best to first compiles the files. Tried and result? I had added in the synapse. Removed before doing this. Confused as to what to do now.

sudo apt-get install build-essential
[sudo] password for dawn: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How should I begin getting clamav on my computer?  
If via synapse, what do I do after I install it?
I've searched for answer and didn't find it.

---

### Post by Pro-reason on 2008-08-30
Firstly, if you find this hard, then you should probably not be compiling software.  You should just use software in the repositories (install using Synaptic).

Secondly, that error normally comes up when you try to access the package-management system with two programs at the same time.  Make sure that you use only one of Synaptic, apt-get, Aptitude, etc. at the same time.  Shut down any others.

Once you have ClamAV installed, I believe that it scans files automatically.  In any case, viruses for Ubuntu are essentially unheard-of, so I don't know why you're stressing about it.

---

### Post by nicedude on 2008-08-30
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

These errors mean you had synaptic package manager open and tried to run the apt-get command, only one installation or package manager can be open at once.

You should not compile clamav from source and instead install it from the repositories, but it will only find viruses that are windows based there are no Linux viruses :-) so if you are just using Ubuntu you have no need for clamav.

If you must have it then this command will install it and everything you need to have a GUI interface to use it

sudo apt-get install clamtk

---

### Post by Camilia on 2008-08-30
I had synapse open the first time I tried it. Tried it again and it work.

Did this before I read what nicedude posted.
Then did sudo apt-get clamtk. So now clam is on my computer, but where? I checked the system. 

I want it, for I like to scan my computer. I don't believe anything is impregnable. 

I am beginning to wonder what happens if I run out kbs.

---

### Post by nicedude on 2008-08-30
LOL clamav only has virus signatures for windows viruses period end of story, there is no Linux virus detectors for you to install since there are no Linux viruses in the wild that are being exploited. There are very few proof of concept linux viruses in computer labs that none of which are available to the outside world, Windows has 40,000+ that any jerk can join the right site and download so you do the math. So if you are just using Ubuntu then you have zero need for any AV as it will only detect windows viruses included in its virus signature database, end of story. And no nothing is impregnable and trying to install things from source rather than the repositories is the number one way to catch a rootkit if you get the source code from an untrusted source ( Like not the repositories or a software author you trusts site ). So until you get the hang of linux I strongly suggest you stick to things in the repositories and don't try to compile anything from source.

To uninstall the clam av you installed from source go into the folder ( directory ) that contains the code and run "sudo make uninstall" and see if that removes it. You also should not install a program from source and then from the repositories as it is both unnecessary and can cause problems.

Please just trust us that Ubuntu cannot get a virus and forget about viruses.

PS and before you freak out and think Ubuntu or Linux can only get rootkits, windows has that vulnerability too but most people don't even know that they do ( rootkits are bad news as once installed they are a big backdoor to your system that a hacker then uses to control your PC etc but if you use the software in the repositories then you find any in anything there )

---

### Post by lovinglinux on 2008-08-30
> **Camilia said:**
> I want it, for I like to scan my computer. I don't believe anything is impregnable.

The thing is that it will look for Windows viruses and you will get many false-positives. Since you are a Linux newbie like me, you will probably try to delete stuff that isn't supposed to be deleted, so the anti-virus program will create a paranoia state.

You should learn how to protect your system and not fix the problem after it occurs. 

Try this [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

I haven't found viruses in my old Windows box for many years. This is because I studied how to protect my computer and changed my habits to avoid infection.

---

### Post by Camilia on 2008-08-30
I removed it through synapse.  Guess I will just scan with superantispyware in windows section.

I guess rootkits are the best scanners in ubuntu. I have been trying to understand them. 

I will the necessity to have a scanner, since I got 3 trojans after copying pictures from the network for my advatar.

This is a really great forum. I get answers even for my stupid answers. Thus going to keep trying to understand linux.

I shall have to read more at [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421) later. Got to get some rest before I go to work.

---

### Post by nicedude on 2008-08-30
You still should do what I suggested and go into the source directory and at a command line type "sudo make uninstall" as you installed it twice and therefore I believe there is a good chance that the source you installed will still be installed somewhere, if not then running the install command won't do any harm either. Just make sure you open the terminal in the source codes directory just like you had to when you installed it. And yes if you still have windows on this machine then you will need to run AV and antispyware to be safe. But I would run those from within Windows and only on your windows or data partitions.

---

### Post by Camilia on 2008-08-30
Pated sudo make uninstall and got - make: *** No rule to make target `uninstall'.  Stop.

---

