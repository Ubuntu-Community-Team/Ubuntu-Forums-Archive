---
title: "Problems installing McAfee 1.7 for Linux"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by imckinley on 2011-10-28
OK, I finally got the installer semi working in terminal. I get to the point where I have to accept or reject the user agreement, and it just ends. I keep having to press spacebar or enter in order to scroll down and I don't know if this is inadvertently screwing up the prompt at the end. Screenshot attached. Any suggestions?

---

### Post by BlinkinCat on 2011-10-28
As far as I know it won't work in Linux -

---

### Post by haqking on 2011-10-28
> **BlinkinCat said:**
> As far as I know it won't work in Linux -

Based on what ?

Virsuscan enterprise 1.7 has a linux version.

@OP what product are you trying to use ? have you checked the knowledge base ?

is this a corporate requirement or personal ? i take it you share files with windows users hence the need for AV which i presume is your product ?

---

### Post by lisati on 2011-10-28
> **BlinkinCat said:**
> As far as I know it won't work in Linux -

McAfee 1.7 for Linux won't work in Linux? :confused:

---

### Post by BlinkinCat on 2011-10-28
> **haqking said:**
> Based on what ?

Virsuscan enterprise 1.7 has a linux version.

@OP what product are you trying to use ? have you checked the knowledge base ?

is this a corporate requirement or personal ? i take it you share files with windows users hence the need for AV which i presume is your product ?

oops - sorry about that - I had a look around and couldn't see a linux version -

@OP please accept my humble apology - :(

---

### Post by imckinley on 2011-10-28
I am trying to install McAfee Virus Scan Enterprise For Linux Version 1.7.0 on Ubuntu 11.10 64 bit. It says in the .txt file that it is approved on Ubuntu up to 11.04. I'm new to Linux but I thought it was still worth a try. The .txt file reads:

To install VirusScan Enterprise for Linux on Ubuntu: 
 
    NOTE: 
    If you are installing VirusScan Enterprise for 
    Linux on a 64-bit Ubuntu system, ensure that you 
    perform the following steps before 
    installation: 
 
   a.  Copy pam_unix.so from /lib/security of a 
       32-bit Ubuntu (till version 10.10) system to 
       a temporary directory (/tmp) on the 64-bit 
       Ubuntu system. From Ubuntu 11.04 onwards, 
       pam_unix.so is available under 
       "/lib/i386-linux-gnu/security" folder. 
 
   b.  In the root (/) directory, create a folder 
       "pam32lib". 
 
   c.  Execute the following command to copy 
       "pam_unix32.so" to the "pam32lib" directory: 
 
       cp /tmp/pam_unix.so /pam32lib/pam_unix32.so 
 
 
1.  Download the MFErt.i686.deb and MFEcma.i686.deb 
    file. 
 
2.  Install McAfee Runtime and McAfee Agent using 
    the following commands: 
 
       dpkg -i MFErt.i686.deb 
       dpkg -i MFEcma.i686.deb 
 
3.  Type the following at the command prompt: 
 
       sh McAfeeVSEForLinux-1.7.0-installer 
**[COLOR=Red] I get to this point and fail, as per the screenshot above.[/COLOR]**
4.  Answer the questions when prompted. Accept the 
    default values, or type your own. 
 
5.  When prompted to start the VirusScan services, 
    select the default option, "Y". 
 
6.  To confirm that VirusScan Enterprise for Linux 
    is installed and running correctly, type the 
    following at the command prompt: 
 
       /etc/init.d/nails status

---

### Post by searchfgold6789 on 2011-10-28
Well, if you're new to linux, you probably won't need antivirus software.
That said, what exactly happens? does the message appear at random after you scroll down, or do you get there, press the "A" key and it spits that at you?
 - search

---

### Post by haqking on 2011-10-28
> **imckinley said:**
>  **I'm new to Linux but I thought it was still worth a try**



If you are new to linux i thought i would give you some stuff to read ;-)

Linux does not suffer from Viruses like other OS tends to, there are no known viruses in the wild currently though that doesnt mean Linux is safe from malware or other attacks, the main reason using AV on linux is to scan incase you share files with windows users.  Malware writers have not as yet targeted Linux as they have other OS, they could do so, it is not to say that Linux is inpenetrable from Malware as it is not, however currently there are no known viruses which could effect it, conversely even though viruses have been known about for a very long time certain OS are still susceptible from viruses written 10 years ago.

**No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person**

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[B][http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)[/B]

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo (make sure you read this if you only read one thing)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are typically taken care of by your home router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and their privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by Dangertux on 2011-10-28
It might not be this simple but you might need to do the following

```

sudo sh McAfeeVSEForLinux-1.7.0-installer

```

Hope this solves your problem.

---

### Post by haqking on 2011-10-29
> **BlinkinCat said:**
> oops - sorry about that - I had a look around and couldn't see a linux version -

@OP please accept my humble apology - :(

no worries, i didnt know if you knew of a specific bug or insider info on the particular product.

cheers

---

### Post by KReckner on 2012-06-15
I just ran into the same problem on Ubuntu 12.04 LTS 64. I found in the readme.txt for McAfee 1.7 for linux a reference to running the installer using:

$ sudo bash McAfeeVSEForLinux-1.7.0-installer
instead of 
$ sudo sh McAfeeVSEForLinux-1.7.0-installer

It seems dash is the default Ubuntu shell and McAfee needs good old reliable bash.

Kevin

---

