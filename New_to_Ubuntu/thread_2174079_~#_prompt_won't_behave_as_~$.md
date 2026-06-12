---
title: "~# prompt won't behave as ~$"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by OttoDidakt on 2013-09-12
A Ubuntu VPS I SSH into doesn't behave as the tutorials say.
The prompt is ~# . Does that mean that I am trying to operate from a wrong/different point?
I'm trying to set a Tor node yet the bare and simple Tor installation steps don't work because of missing bits of Ubuntu and commands it's never heard of. 
I remember a little comand line lingo from DOS days.
Getting a GUI going on Ubuntu or Windows remote computer is the preferred objective.
Thanks in advance.
Otto

---

### Post by VMC on 2013-09-12
Your topic I believe is misleading. You should have mentioned VPS or SSH in the topic. You may not draw much attention for those familiar with ssh functions.

Normally in a terminal '$' refers to a regular user, and '#' refers to root. Not sure about ssh, since a never use it, or haven't in years.

---

### Post by Lars Noodén on 2013-09-13
As mentioned you usually get # for the prompt when root and $ when logged in as a regular user.  You can use [whoami](http://manpages.ubuntu.com/manpages/raring/en/man1/whoami.1.html) to verify which account you are in.  

How are you trying to set up a Tor node?  I am going to guess you mean a relay node or an obfuscated proxy.  If you are going to set up just a client it is best to use the [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en), which takes care of everything for you.

---

### Post by OttoDidakt on 2013-09-13
Perhaps you are right about the topic but if ~# is as good as root that is not the problem.
Thanks Lars and VMC.  
I am trying to set-up either another exit or perhaps a mirror but my command line skill may be below the mirror management I think.
I tried following simple commands to get Tor installed but everything comes back with unknown, not found or the like as if the Ubuntu installation is not normal or I'm installing the wrong way.
Incidentally update and upgrade didn't install everything for when install Tor ran. All installations result in faults.
It is a cheap VPS so who knows who's managing it. They said it is a cut-down version and they don't know Ubuntu and refer to commands in Unix. It's in LA, USA and they are in Beijing.
Otto

---

### Post by Lars Noodén on 2013-09-13
You don't need any skill with the shell to work with Tor.  But I would strongly recommend reading all the FAQs over at Tor Project, especially if you are considering an Exit node.  

To work with Tor, as it is in Ubuntu, you need to edit the file /etc/tor/torrc and set things as you want.  *sudo nano -w /etc/tor/torrc*  If you want a little easier interface, you can try installing Vidalia instead.  It has a graphical user interface.

---

### Post by OttoDidakt on 2013-09-14
Lars,

I have twelve windows exit nodes and have no trouble editing the torrc file.
I tried to find and edit the torrc file after I thought I updated and upgraded and installed Tor but as I keep saying even the installation comes back with 'not found' and 'unknown' or 'no such...'.
I installed nano - I thought then tried to run it but 'no such' 'not found' or something came back.
So either the guys settingn up the server installation have done something odd or I don't know something critical about Linux command line stuff.
To test the theory that it is my knowledge which is lacking could you tell me several steps to prove the Ubuntu installation is normal.
From that I'll seek help off list to avoid annoying anyone.

Otto

---

### Post by OttoDidakt on 2013-09-14
Lars et al,

At the risk of overdoing it here is what 'locale -a' got after 'apt-get update' then 'apt-get upgrade' produced numerous 'unable's.
I gathered that the installation failure may be part of my problem and that basic settings may be a possible cause.

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)
debconf: falling back to frontend: Readline
 * Starting domain name service... bind9                                 [ OK ] 
Setting up libqtgui4:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-declarative:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-designer:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-qt3support:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-scripttools:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-opengl:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Setting up libqt4-svg:i386 (4:4.8.4+dfsg-0ubuntu9.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
root@vps06:~# locale -a
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_COLLATE to default locale: No such file or directory
C
C.UTF-8
POSIX

Any help is appreciated.
Otto

---

### Post by Lars Noodén on 2013-09-14
> **OttoDidakt said:**
> Lars,

I have twelve windows exit nodes and have no trouble editing the torrc file.
I tried to find and edit the torrc file after I thought I updated and upgraded and installed Tor but as I keep saying even the installation comes back with 'not found' and 'unknown' or 'no such...'.
I installed nano - I thought then tried to run it but 'no such' 'not found' or something came back.
So either the guys settingn up the server installation have done something odd or I don't know something critical about Linux command line stuff.
To test the theory that it is my knowledge which is lacking could you tell me several steps to prove the Ubuntu installation is normal.
From that I'll seek help off list to avoid annoying anyone.

Otto

nano should already be installed.  Which version of Ubuntu are you running?  You can see what the system claims like this:

```

lsb_release -rd

```

If you got Tor from the repository, the config file should be found as /etc/tor/torrc

```

sudo nano /etc/tor/torrc
sudo service tor restart

```

---

### Post by OttoDidakt on 2013-09-14
Lars, thank you

It is Ubuntu 13.04.
This time nano was found and the file too, inexplicably.
It seems it's working normally.
If you have anything further I welcome it.

Otto

---

### Post by OttoDidakt on 2013-09-14
Lars,

I'd be much more comfortable with a GUI at my end. Is there a way to do that?

Otto

---

### Post by Lars Noodén on 2013-09-14
Vidalia is a GUI for Tor.  So you could try that instead.  

Otherwise for GUI editors, you have Geany, Gedit, or Kate.  They can be launched with [gksudo](http://manpages.ubuntu.com/manpages/raring/en/man1/gksudo.1.html) to allow editing of *torrc*.

---

