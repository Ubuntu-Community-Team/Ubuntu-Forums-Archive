---
title: "[SOLVED] Can't install Avast antivirus"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by thadacto on 2008-11-27
I have Ubuntu as well as Windows XP on my computer for the last 18 months. However, I have just got a connection to the internet at home and I am trying to install AVAST antivirus for Linux.
I have downloaded it from Avast website which offers three types for Linux users. I chose Debian as I seen to have some program of theirs.
However, when I try to install the antivirus program, I am informed that it not the correct architecture.
What's wrong - what's the architecture?
As I have only just joined the forum, I was going through some of the Beginners queries the first one struck a cord with me - another new user finds this system much more complicated than Windows.
Having said that I have it on my computer for 18 months, I have basically only used linux for a few games. I tried the office program but found many problems there (tables don't keep the formulas when saving and when you open again the formulas ain't there. Most annoying.
Any help on the antivirus will be much appreciated. Incidently I am using AMD dual core processor - is that the problem?:confused:

---

### Post by taurus on 2008-11-27
Maybe you downloaded the x86_64 version while you are running x86 or vice versa.

What is the exact name of the file that you've downloaded and what is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
uname -a
```

---

### Post by Keen101 on 2008-11-27
the architecture basically is whether your system is 32bit (default) or if you installed the 64bit version of ubuntu.

You could also try clamav open source antivirus. You will also need to install a nice gui for it though.

---

### Post by Paqman on 2008-11-27
> **thadacto said:**
> 
Any help on the antivirus will be much appreciated. Incidently I am using AMD dual core processor - is that the problem?:confused:

Nope, you processor is fine.

As for antivirus, the good news is that you don't need to bother. Ubuntu machines don't need antivirus software tacked onto them to be safe, unlike Windows boxes. Just stay current with security updates and you'll be well protected from viruses. That sounds difficult to believe if you're used to Windows, but it's true.

The error you experienced is caused by trying to install a 32-bit package on a 64-bit machine, or vice versa. To check which type of Ubuntu you are running, put this command into a terminal:
```
uname -m
```

---

### Post by thadacto on 2008-11-27
I don't remember what the file name was - I deleted it when it didn't install.
It was downloaded to my desktop and I just clicked on the file to run it.
I'll have to download it again - and as my connection only seems to run at about 12 to 15 kb per second it's going to take a while - again.
I use Avast on my Windows and find it really great.

---

### Post by taurus on 2008-11-27
Then why don't you figure out which arch you are running, i686 or x86_64, before you do any downloading because if you download the wrong arch, you're just wasting your time.

---

### Post by mkvnmtr on 2008-11-27
It is not a good idea for most of us beginners to try to install things from the internet. We have  package managers in Ubuntu with thousands of softwares . Try to find a made for Ubuntu anti virus to install with no more than a click. It has been designed for Ubuntu and checked and will probably be better than what you find to download off the net. Just go to Synaptic and put "anti virus" in the search box and install. 
By the way it is not at all needed in Ubuntu.

---

### Post by thadacto on 2008-11-27
> **taurus said:**
> Then why don't you figure out which arch you are running, i686 or x86_64, before you do any downloading because if you download the wrong arch, you're just wasting your time.

OK so, according to the Terminal I've got <x86_64>

If I get a virus and lose 15 years of work I'll just go bonkers. Though I do keep backups - but the thought of re-formatting the hard drive and installing everything again does not thrill me in any way.

---

### Post by Paqman on 2008-11-27
> **thadacto said:**
> OK so, according to the Terminal I've got <x86_64>


Which is 64-bit, also sometimes known as AMD64 (even on Intel chips)

> 
If I get a virus and lose 15 years of work I'll just go bonkers. Though I do keep backups - but the thought of re-formatting the hard drive and installing everything again does not thrill me in any way.

If you get a virus I will personally come down to Argentina and do whatever reinstalling you require. I'm that confident that it won't happen.

Btw, reinstalling actually isn't so bad with Linux. I can reinstall my system (including all software) in about an hour. The trick is to have your /home folder mounted on a separate partition, your data backed up, and use this little trick to [reinstall all your software in one step]("http://ubuntuforums.org/showthread.php?t=261366"). Windows reinstalls are not fun, but Linux is not too bad. A lot of people using Ubuntu reinstall every 6 months when the new version comes out.

---

### Post by mkvnmtr on 2008-11-27
Do a search here in the forums for virus, virus in Ubuntu, virus in linux and anti virus.  People run antivirus software only to scan the things they send to windows machines. Your firewall is very good but is to keep someone from getting in and stealing your secrets. But sure run one it can't hurt anything. By the way it only takes about an hour to reinstall. I am getting pretty good at it after messing up my system a few dozen times.

---

### Post by thadacto on 2008-11-27
OK I'll give up the antivirus -
Thanks Paqman et al.
Can't find where you get the official thanks.
thadacto

---

### Post by brigadoon on 2008-11-27
> **thadacto said:**
> OK so, according to the Terminal I've got <x86_64>

If I get a virus and lose 15 years of work I'll just go bonkers. Though I do keep backups - but the thought of re-formatting the hard drive and installing everything again does not thrill me in any way.

Unix and Linix have a high resistance to viruses. Writing a virus for Windows is easy! Writing one for Unix/Linux is tough. The following link gives some insight into Unix/Linux viruses...

[http://www.kernelthread.com/publications/security/vunix.html](http://www.kernelthread.com/publications/security/vunix.html)

also...

[http://cyber.com/details.php?id=22&section=detailpapers](http://cyber.com/details.php?id=22&section=detailpapers)

Unix/Linux viruses are rare but they exist. Stick to the synaptic repositories for Ubuntu friendly anti virus protection. The popular one to try is CLAM. You can find out more at...

[http://www.clamav.net/](http://www.clamav.net/)

As soon as you connect to the outside world you run the risk of getting a virus or passing one along. Keeping backups can minimize the damage. Using CLAM or another unix friendly anti-virus can only help.

Good luck!

---

