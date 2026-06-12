---
title: "Installing Broadcom drivers, and minor terminal problem"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Lostin60's on 2008-11-29
I am getting my internet going on a new 8.1 install. And found a very helpful posting. Now I need to understand it.
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
My assumptions
line 1 puts bcmw into ndiswrapper
line 2 creates aliases
line 3 and 4 take all conffile files in bcmw and replace all instances of radiostate 1 with radiostate 0
I am not a coder, well some cobal, so I am using common sense(Ihope) to work this out. My first problem is when I display the conffiles none of them have a radiostate anything. Secondly, all of a sudden, when I run a sudo, after it asks for my pass, it wont let me type?? Thats brand new.
Any suggestions will be appreciated.

---

### Post by psquared89 on 2008-11-29
First off, you only need ndiswrapper if you have a wireless adaptor of some kind that does not have native Linux support. Unfortunately, there are still quite a few of these, and I'm guessing if you found this, you've already gotten that far.  Next, you have to make sure you have the right windows drivers for YOUR specific network adapter - ie bcmwl5.inf might not be right for you, make sure you have the correct driver. Given that, let's look at what's happening here:

First off "sudo" <-- "su" (super-user, or root) + "do". Sudo is a big part of ubuntu (and all linux) security. It allows a regular user (you) to run one command (in this case ndiswrapper) as root. When you're prompted for your password, your given a shadow prompt, as you type, you won't see the characters (or even *'s) on the screen; that way someone looking over your shoulder can't see what you're typing (or other slightly more nefarious ways of looking). Just have faith that the letters you're typing are there and hit enter when you're done.

> sudo ndiswrapper -i ~/Desktop/bcmwl5.inf

From the ndiswrapper man page:

>        -i <inf file>
              installs new Windows XP driver, where <inf file> is full path to INF file for that driver.

> sudo ndiswrapper -m

From the ndiswrapper man page:
>        -m     writes an alias for wlan0 (default wireless device) into module configuration file so that ndiswrapper kernel module is loaded
              automatically when this interface is used.
Basically, this is a hook so that whenever your wireless adapter is accessed, ndiswrapper + your installed driver will be called instead of the default kernel module (as it does not have the correct drivers for it)

> for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done
This is unnecessary AFAIK. What it's doing is going through every configuration file (files ending in .conf) in the /etc/ndiswrapper/bcmwl5/ directory and then replacing every instance of RadioState|1 with RadioState|0.  Unless this is some quirk unique to your adapter, this step is unnecessary, the first two are enough to get you set up a going.

Side note: Whoever wrote this doesn't really understand how sed works (it can operate on files, instead of piping the cat'ed file into sed and then redirecting the result back into the same configuration file), so I'd take advice from the page with a grain of salt.

--Hope this helped.

---

### Post by andrew.46 on 2008-11-30
Hi,

Broadcom should not require ndiswrapper with the newer kernels. Can you have a look at which broadcom chip you have? Mine is:
```

andrew@skamandros:~$ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

This operates with the bcm43 firmware and kernel driver.

  Andrew

---

### Post by nakama85 on 2008-11-30
This is what worked for me

In terminal run ```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
```
 then run ```
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe
cabextract sp34152.exe
```

Then ```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```
Then
```
sudo aptitude remove b43-fwcutter
```

then ```
sudo gedit /etc/init.d/wirelessfix.sh
```

paste in the following

> #!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

save and close

then in terminal again run
```
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
```

finally run this:

```
sudo update-rc.d wirelessfix.sh defaults
```

then reboot the machine

Hope this works:) 

*Note: I got the above steps from this tutorial [http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy). Although My card was different it still worked*

---

### Post by MittbaraMitt on 2008-11-30
Hi! I'm new to Ubuntu and this is my first go in a thread :) I have some problems with getting my wireless broadcom 4318 working and I have been following some threads, doing a lot of copy-pasting. It's still not going my way and I tried to follow this thread now. I come to this error:

pia@Pias:~$ wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
--21:30:33--  [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp3...00 ... 
No such directory `pub/softpaq/sp3...00'.

pia@Pias:~$ cabextract sp34152.exe
sp34152.exe: No such file or directory

All done, errors in processing 1 file(s)


Could you please help me to get forward?

Thanks
/Pia

---

### Post by Lostin60's on 2008-11-30
> **psquared89 said:**
> First off, you only need ndiswrapper if you have a wireless adaptor of some kind that does not have native Linux support. Unfortunately, there are still quite a few of these, and I'm guessing if you found this, you've already gotten that far.  Next, you have to make sure you have the right windows drivers for YOUR specific network adapter - ie bcmwl5.inf might not be right for you, make sure you have the correct driver. Given that, let's look at what's happening here:

First off "sudo" <-- "su" (super-user, or root) + "do". Sudo is a big part of ubuntu (and all linux) security. It allows a regular user (you) to run one command (in this case ndiswrapper) as root. When you're prompted for your password, your given a shadow prompt, as you type, you won't see the characters (or even *'s) on the screen; that way someone looking over your shoulder can't see what you're typing (or other slightly more nefarious ways of looking). Just have faith that the letters you're typing are there and hit enter when you're done.



From the ndiswrapper man page:





From the ndiswrapper man page:

Basically, this is a hook so that whenever your wireless adapter is accessed, ndiswrapper + your installed driver will be called instead of the default kernel module (as it does not have the correct drivers for it)


This is unnecessary AFAIK. What it's doing is going through every configuration file (files ending in .conf) in the /etc/ndiswrapper/bcmwl5/ directory and then replacing every instance of RadioState|1 with RadioState|0.  Unless this is some quirk unique to your adapter, this step is unnecessary, the first two are enough to get you set up a going.

Side note: Whoever wrote this doesn't really understand how sed works (it can operate on files, instead of piping the cat'ed file into sed and then redirecting the result back into the same configuration file), so I'd take advice from the page with a grain of salt.

--Hope this helped.

Thanks much. Very helpful. I had figured out the pass thing. DUH! And I had correct driver..pulled it from my windows(Boo) install. I have found out a few things, though. Well, I *think*I have. 
sudo ndiswrapper -i ~/desktop/bcmwl5.inf If I figure it right, that should put the driver inf file into ndiswrapper. If so, it didn't. But when I used sys>admin>Windows wireless drivers my .inf file was placed in correct folder. As to the conffiles.. /etc/ndiswrapper/bcmwl5 was there. I opened every conffile, and found NO RadioState files at all.  Then I found this post.
Jim,
I took me over a year to figure how to get my wireless working.
If you are using Ubuntu v8.10, you must enable all the repositories to be able to download the needed drivers.
Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

AFTER doing this, the drivers for my Broadcom BCM4306 rev. 02 wifi card were downloaded/installed, and now works!

Good luck.
Joe2Shoe.

It gave me 127 files to d/l, but when I rebooted, my wireless was working. There are still no RadioState files though..lol.  I think you're right about it being a quirk. Again, I appreciate your time and effort.

---

### Post by MrWES on 2008-11-30
> **andrew.46 said:**
> Hi,

Broadcom should not require ndiswrapper with the newer kernels. Can you have a look at which broadcom chip you have? Mine is:
```

andrew@skamandros:~$ lspci | grep -i broadcom
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

This operates with the bcm43 firmware and kernel driver.

  Andrew

Andrew is correct. Ibex 8.10 should have your broadcom drive in System | Administration | Hardware Drivers. All you need to do is activate it. That is after you follow the above procedure and activate third party sources.

Bill

---

### Post by Lostin60's on 2008-11-30
> **MittbaraMitt said:**
> Hi! I'm new to Ubuntu and this is my first go in a thread :) I have some problems with getting my wireless broadcom 4318 working and I have been following some threads, doing a lot of copy-pasting. It's still not going my way and I tried to follow this thread now. I come to this error:

pia@Pias:~$ wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
--21:30:33--  [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
           => `sp34152.exe'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp3...00 ... 
No such directory `pub/softpaq/sp3...00'.
pia@Pias:~$ cabextract sp34152.exe
sp34152.exe: No such file or directory
All done, errors in processing 1 file(s)

Could you please help me to get forward?

Thanks
/Pia

I too am a noob. I have a broadcom card, and my inf file is bcmwl5. 
Now you will see several posts telling you command line approaches to installing the drivers, I tied a few with no luck. This approach worked for me. I believe it even auto-configured my network for me.
First find your network cards .inf and .sys files.
Copy them to your desktop.
Go to system >administration >windows wireless drivers and follow the instructions there.

Now follow the instructions below.
 My thanks to Joe2shoes for the following post.

Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

When I rebooted my wireless was up and running. I hope this  helps.

---

### Post by andrew.46 on 2008-12-01
Hi Bill,

> **MrWES said:**
> Andrew is correct. Ibex 8.10 should have your broadcom drive in System | Administration | Hardware Drivers. All you need to do is activate it. That is after you follow the above procedure and activate third party sources.

The trouble seems to be that there are so many older walkthroughs that were accurate in their time that lead people down the ndiswrapper route although this need has vanished in many cases. But it is great to see Linux wireless coming of age finally :-).

  Andrew

---

### Post by MittbaraMitt on 2008-12-03
> **Lostin60's said:**
> I too am a noob. I have a broadcom card, and my inf file is bcmwl5. 
Now you will see several posts telling you command line approaches to installing the drivers, I tied a few with no luck. This approach worked for me. I believe it even auto-configured my network for me.
First find your network cards .inf and .sys files.
Copy them to your desktop.
Go to system >administration >windows wireless drivers and follow the instructions there.

Now follow the instructions below.
 My thanks to Joe2shoes for the following post.

Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

When I rebooted my wireless was up and running. I hope this  helps.


Thank you, it's still not working though. Under "Third-Party Software I have three choises instead of two. All of them Hardy. Under system>administration I don't have any option called windows wireless or anything alike?

Greatful for any kind of tip. I don't exactly know what I'm doing/what I have done but probably there is some kind of file I have missing..?

---

