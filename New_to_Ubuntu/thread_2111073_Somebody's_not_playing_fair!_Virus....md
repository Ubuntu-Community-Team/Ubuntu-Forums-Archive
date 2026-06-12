---
title: "Somebody's not playing fair! Virus..."
date: 2013-01-31
forum: New to Ubuntu
---

### Post by Tarka Dal on 2013-01-31
I have to say I have not had a very good experience with Ubuntu. Not only the problem with having to learn a whole new process. Also, having to deal with malware when there is no visible Anti virus or anti malware that we can use to keep out the little critters. Clam TK is useless. I have had to install several times now and my patience is wearing thin! I am going to try one last time and start with a clean Install.
Would any members of the Ubuntu community like to suggest how to keep a cleanish computer please fire away!):P

(Whist I am doing a clean install that is!)

---

### Post by Grinage on 2013-01-31
I don't think I've ever had a viral infection on my linux boxes, ClamAV and the attendant modules that go with it have always done the job superbly, quietly, and without my interference or direction.

I'd be interested to hear more about this viral infection please.

For a more windows like experience try another flavor such as Kubuntu or Xubuntu

---

### Post by lisati on 2013-01-31
Computer security is a process, which begins with what you allow on your computer and what you run.

Some information about antivirus software for Ubuntu can be found here:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

---

### Post by Tarka Dal on 2013-01-31
> **Grinage said:**
> I don't think I've ever had a viral infection on my linux boxes, ClamAV and the attendant modules that go with it have always done the job superbly, quietly, and without my interference or direction.

I'd be interested to hear more about this viral infection please.

For a more windows like experience try another flavor such as Kubuntu or Xubuntu
 
@ Grinage

I can here the computer revving up to full blast and the computer becomes unusable. 

The point is from my point of view is that Ubuntu can never be a viable option for the masses until there are suitable AV and malware protection which would cost loads on this format because no-one wants to pay for it!

But that's another story I don't want to get into...

@ lisati

Being a noob! I can only guess what you actually mean... I have in good faith installed what I deem fit. Does that mean I'm stupid?

Chrome 4 Viri so clam says Quarantined! 
Hp printer
Kazam screencaster
Compiz settings manager
Compiz fusion Icon
Clam TK
Bombono DVD
Skype VLC player

Nothing else?

---

### Post by Grinage on 2013-01-31
Interesting links, lisati, I'd still like to know more about Tarka Dal's virus situation.  I've seen people create virus like problems on their box but assuming ClamAV and the other associated components that help secure your system are installed, configured, and working, I really want to know more about the specifics of the infection.

---

### Post by lisati on 2013-01-31
I haven't encountered a need for anti-virus on my Ubuntu installations in the 5 years I've been using Ubuntu. I do, however, use it on my email server out of courtesy to the Windows users I interect with.

---

### Post by Tarka Dal on 2013-01-31
There is also a problem with cross-platforms. If you have a virus in Ubuntu it could multiply fast on Windows machines and cause havoc on Linux and vice versa! There is no cross-platform AV. 
So, is there "No" better AV than ClamTK?

---

### Post by Grinage on 2013-01-31
So let me see if I understand this correctly, you've just completely wiped your install and done a clean installation from a live CD/USB, and after the reboot it immediately halts?  

As for Clam, there are several additional components of Clam that may or may not apply to your specific application, clam TK  by itself is nothing but a front end for clamAV you also need to make sure you install freshclam and if you're using some type of mail server spamassassin to help stop the spread of viral infections.

---

### Post by Tarka Dal on 2013-01-31
> **Grinage said:**
> So let me see if I understand this correctly, you've just completely wiped your install and done a clean installation from a live CD/USB, and after the reboot it immediately halts?  

As for Clam, there are several additional components of Clam that may or may not apply to your specific application, clam TK  by itself is nothing but a front end for clamAV you also need to make sure you install freshclam and if you're using some type of mail server spamassassin to help stop the spread of viral infections.

Ok I'll deal with the last bit first...
No email gets on my computer so no need for freshclam.
I had been on the computer for an hour then opened up Kazam then about a half an hour later this Virus kicked in. I couldn't move my cursor and I could here the computer ramp up like on windows when you got a virus...Then I shutdown the computer. On restart I was working again for five minutes then the same thing happened again!

---

### Post by BBQdave on 2013-01-31
> **Tarka Dal said:**
> The point is from my point of view...

Which appears to be coming from a Windows' or Mac world.

A Linux machine can be cracked into... but it takes a very concentrated effort, such as social cracking, weak pass words, etc.

Linux is different from Windows or Mac, in that the system is hardened, whether it be the SELinux layer in Fedora or root disabled in Ubuntu. ClamAV on Linux, is to scan for threats to Windows machines - so as, you do not pass on malware to a friend using Windows, such as through an email.

First and foremost, a strong pass word in Linux is key.

And I would offer that there are several *honey pot* projects out there - people placing a Linux machine on the web with the challenge to crack it. Difficult to do, and a learning process to further harden Linux.

You would not do this with a Windows or Mac machine - in fact, most come loaded with third party protection programs to activate before you get on the web :p

---

### Post by BBQdave on 2013-01-31
> **Tarka Dal said:**
> I had been on the computer for an hour then opened up Kazam then about a half an hour later this Virus kicked in. I couldn't move my cursor and I could here the computer ramp up like on windows when you got a virus...Then I shutdown the computer. On restart I was working again for five minutes then the same thing happened again!

With the limited information you are offering, this appears to be hardware related. I am not familiar with any current malware that lives in ram - if you were dual booting Windows and Ubuntu.

It appears you are getting a system freeze :(

---

### Post by Grinage on 2013-01-31
freshclam is for ensuring you always have up to date virus definitions without you having to do it manually,  clamAV can run in Daemon mode if you want it to run all the time.  

Linux in general is typically supremely secure, millions or probably billions of people use some form of linux every day and the numbers continue to grow, linux is everywhere from Microsoft's own Servers to Android Phones, more and more users are leaving windows behind because of it's massive security problems.  Usually the selling point on two identical machines one with a linux OS and one with a MS OS is the security of the system and correctly configured the near impossibility of infection.  

If  you're getting a quarantine message please post the message.  If it's hardware it could be ACPI or powersave related, sometimes these functions are not handled correctly.

---

### Post by Tarka Dal on 2013-01-31
> **BBQdave said:**
> Which appears to be coming from a Windows' or Mac world.

A Linux machine can be cracked into... but it takes a very concentrated effort, such as social cracking, weak pass words, etc.

Linux is different from Windows or Mac, in that the system is hardened, whether it be the SELinux layer in Fedora or root disabled in Ubuntu. ClamAV on Linux, is to scan for threats to Windows machines - so as, you do not pass on malware to a friend using Windows, such as through an email.



And I would offer that there are several *honey pot* projects out there - people placing a Linux machine on the web with the challenge to crack it. Difficult to do, and a learning process to further harden Linux.

You would not do this with a Windows or Mac machine - in fact, most come loaded with third party protection programs to activate before you get on the web :p

I am not making a gripe even though it may look like that! I am just observing the problem I have and trying to find a way to fix it if possible but, it looks unlikely!
BTW, I always use a strong password...
First and foremost, a strong pass word in Linux is key.
And I'm sorry if I am looking at it from a windows view...Haha! joke...
No serious I am sorry!

---

### Post by coldcritter64 on 2013-01-31
OP, there are currently NO viruses "In the wild" you are likely to run into, even if you do, following a few simple precautions in the security links here, you are safe. Being new here sounds like you are still operating in a "Windows Mindset".

Please read the link below, Ubuntu Security, contains a section on "The Windows Mindset" ;),
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Your Ubuntu system if used wisely is effectively "toxic" to viruses. There are other worse problems than viruses, rootkits and other malware etc, safe practices will mitigate their effects as well.

Like lisati, I've been on Ubuntu 5 + years, not 1 virus, ever. They do exist, "rare as hens teeth, imo" :) I have installed and used Avast for Linux when I've had to share files with windows machines, there is no need for virus protection for Linux itself at this time, so little effective effort seems to have been expended on something this system really DOESN'T need.  Cheers.

---

### Post by monkeybrain2012 on 2013-02-01
BTW clam av is for scanning windows virus if I am not mistaken. There is no Linux virus in the wild as others have said, I have never had a need for anti-virus in Linux. 

Your description is rather vague, what makes you think you have a virus?

---

### Post by Grinage on 2013-02-01
in a mixed enviroment as we all are clamAV and it's components help stop the spread of windows viruses and just in case there is a linux virus it stops that too

---

### Post by monkeybrain2012 on 2013-02-01
> **Grinage said:**
> in a mixed enviroment as we all are clamAV and it's components help stop the spread of windows viruses and just in case there is a linux virus it stops that too

I don't babysit Windows users. It is their responsibility to install Av on their ends.

---

### Post by Grinage on 2013-02-01
I wonder, was this a "built for windows x" machine?  The power ramp ups you described seem like you have one of those streamlined for microsoft BIOS chips.  If that's the case you're definitely having ACPI problems.   This relates to powersaver, cpu stepping, and energystar functions.   If this is the case there are solutions to that.

---

### Post by BBQdave on 2013-02-01
> **monkeybrain2012 said:**
> I don't babysit Windows users. It is their responsibility to install Av on their ends.

Yeah, not trying to pick at the OP...

I do not understand the need of anti-virus programs on Linux. And friends and family with Windows 7 machines, malware protection seems built in. That is to say the normal channels of receiving virus's are protected: virus filters on Yahoo Mail and Gmail. I like lavabit mail, virus protection built in there too. Work email for folks I know using Windows 7, have built in virus protection.

I know of no one, in my circle of family and friends with Windows and Mac machines, that use third party security programs - they just go with what is built into the system.

I think you are seeing a rise in malware, malware injected into a system through loading *apps*. Again though, with Ubuntu, if you load applications through the Ubuntu software center - apps are filtered, your protected :)

---

### Post by Tarka Dal on 2013-02-01
Just suffered another occurrence. This time I have an Idea??? It may not be a viri. I'll try again.

---

### Post by Grinage on 2013-02-01
if it's ACPI then in the few minutes you have uptime there are some options.  Be careful with these!

1 check in your BIOS settings if you can get at them and see if you can disable ACPI
2. from a terminal sudo nano /etc/default/grub

look for these lines

GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

and change them to

GRUB_CMDLINE_LINUX_DEFAULT="nolapic"
GRUB_CMDLINE_LINUX=""

alternatively you might have to use this

GRUB_CMDLINE_LINUX_DEFAULT="acpi=off"
GRUB_CMDLINE_LINUX=""

or 

GRUB_CMDLINE_LINUX_DEFAULT="noapic"
GRUB_CMDLINE_LINUX=""

CTRL +X to close choose to save and run
sudo update-grub

then reboot your machine

Be cautions in changing the grub file you can brick your system very quickly and you may or may not have the necessary recovery tools easily available.

---

### Post by Bucky Ball on 2013-02-01
> **Tarka Dal said:**
> Just suffered another occurrence. This time I have an Idea??? It may not be a viri. 

#-o Exactly. I think you've gotten off on the wrong foot to solving your system freeze by presuming it is. 

It might be a good idea to post another thread with a title that fits your new line of thought and as much info as you can rather than continuing with this one.

Your issue seems to be related to something else and the information provided here so far gives us no clue as to what that might be.

Post a link to any new thread here so we might continue delving.

---

### Post by Tarka Dal on 2013-02-01
Turns out it's not a viri. It's Kazam playing jokes on me....
What's happening is the computer slows right down when recording! It must be the CPU can't cope with all the information it receives...
I did buy this cpu for it's economy not it's power...
All those years ago!
Never mind a! all in the name of fun!
Well it's 05:36 am time to go to bed!
Bloody Poms eh!

---

### Post by Bucky Ball on 2013-02-01
I have marked this thread as solved. Please post a new thread with any further issues.

---

### Post by Tarka Dal on 2013-02-01
Turns out it was a bug after all. I found it still wreaked havoc 10 minutes later. Suffice to say I have re-installed another fresh copy. Now it's the last time!:popcorn:

---

### Post by Bucky Ball on 2013-02-01
***Thread Closed***

Report any further problems on a new thread as this thread title will have nothing to do with it. 

Start again and this time tell us exactly what you've done, exactly what's happening, and anything you've done attempting to fix it. Include relevant hardware details and Ubuntu release ... on another thread appropriately titled.

As you've mentioned: > Turns out it's not a viri. It's Kazam playing jokes on me....

A bug is not a virus and if you can identify and repeat a bug in Kazam or anything else you should report it.

---

