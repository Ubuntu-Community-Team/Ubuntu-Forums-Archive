---
title: "Wireless? Device Manager? Help!"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by MisanthropicAnthropoid on 2008-08-17
Just got Ubuntu (7.10), can't get online (I'm dual-booting with Vista, and I'm currently online with Vista). It won't recognize any of the wireless networks in range. I clicked "help," and it told me to click on device manager, which was a subtab under system -> administration. That subtab doesn't even exist! I'm quite confused. I'm sure this question is insulting to your intelligence, but can anyone tell me what to do?

---

### Post by Ryadt on 2008-08-17
Can you post the output of ```
iwconfig
```

---

### Post by MisanthropicAnthropoid on 2008-08-17
I don't even know where I would input that (as I said, complete newbie). I can shut down, restart, try to figure it out, shut down, restart, get back on Vista, and tell you if I got anything.

---

### Post by rossjman1 on 2008-08-17
Right click on the desktop and select open terminal. Then type in the command the above user posted.

---

### Post by Ryadt on 2008-08-17
Input it in the terminal- Application > Accessories > Terminal

---

### Post by MisanthropicAnthropoid on 2008-08-17
ross' directions to find the terminal failed. But ryadt's worked. Anyways, here's the output:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID: off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jay@jay-laptop:~$

---

### Post by Ryadt on 2008-08-17
Sorry but did you install your wireless card?

---

### Post by MisanthropicAnthropoid on 2008-08-17
Do I need to install something? Vista recognizes my wireless automatically.

---

### Post by Ryadt on 2008-08-17
You will need to install your wireless card. Just follow this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by MisanthropicAnthropoid on 2008-08-17
Okay. Like I said, I kinda dropped myself into this with no knowledge at all. And the directions in your link are broken. I wonder if I can get them somewhere else.

---

### Post by MisanthropicAnthropoid on 2008-08-17
Yeah, this universe repository they want me to go to is non-working. Are there other places to download the necessary files?

---

### Post by Ryadt on 2008-08-17
I just clicked on it and it's not broken. Anyway try this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Choose Ubuntu Gustsy 7.10 at the bottom of the page.

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **Ryadt said:**
> I just clicked on it and it's not broken. Anyway try this link [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Choose Ubuntu Gustsy 7.10 at the bottom of the page.

The main link to the bcm43. . . is broken, but the individual ones are not. So presumably I just follow the AMD one, since I have AMD.

---

### Post by Ryadt on 2008-08-17
> **MisanthropicAnthropoid said:**
> Yeah, this universe repository they want me to go to is non-working. Are there other places to download the necessary files?
Have you got the universe repos checked? If not go in System > Administration > Software Sources and check everything under the Ubuntu Software tab.

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **Ryadt said:**
> Have you got the universe repos checked? If not go in System > Administration > Software Sources and check everything under the Ubuntu Software tab.

I didn't. I now do, and still cannot access anything at packages.ubuntu. . .

---

### Post by Ryadt on 2008-08-17
> **MisanthropicAnthropoid said:**
> I didn't. I now do, and still cannot access anything at packages.ubuntu. . .

First try```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by MisanthropicAnthropoid on 2008-08-17
I did, however, find that I'm using a Broadcom94311; I was previously unaware of the specific sort of wireless card. 

Is the reason I can't access packages.ubuntu.com that I'm trying to access it with Vista rather than Ubuntu?

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **Ryadt said:**
> First try```
sudo apt-get update && sudo apt-get upgrade
```

That gave me quite the laundry list of errors:

```



Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err http://archive.ubuntu.com gutsy Release.gpg                                
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/main Translation-en_US                     
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/universe Translation-en_US                 
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/restricted Translation-en_US               
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/multiverse Translation-en_US               
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates Release.gpg                        
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/universe Translation-en_US         
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/main Translation-en_US             
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_US       
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/restricted Translation-en_US       
  Could not resolve 'archive.ubuntu.com'
Err http://security.ubuntu.com gutsy-security Release.gpg                      
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/universe Translation-en_US    
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Translation-en_US        
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/multiverse Translation-en_US  
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
  Could not resolve 'security.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security Release                          
Err http://archive.ubuntu.com gutsy-proposed Release.gpg    
  Could not resolve 'archive.ubuntu.com'
Ign http://security.ubuntu.com gutsy-security/universe Packages
Err http://archive.ubuntu.com gutsy-proposed/universe Translation-en_US        
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/main Translation-en_US            
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_US      
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_US      
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports Release.gpg                      
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/universe Translation-en_US       
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/main Translation-en_US           
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_US     
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com gutsy Release.gpg                             
  Could not resolve 'archive.canonical.com'
Err http://archive.ubuntu.com gutsy-backports/restricted Translation-en_US     
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com gutsy/partner Translation-en_US               
  Could not resolve 'archive.canonical.com'
Ign http://archive.canonical.com gutsy Release               
Ign http://archive.ubuntu.com gutsy Release               
Ign http://archive.ubuntu.com gutsy-updates Release       
Ign http://archive.ubuntu.com gutsy-proposed Release      
Ign http://archive.ubuntu.com gutsy-backports Release     
Ign http://security.ubuntu.com gutsy-security/main Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://security.ubuntu.com gutsy-security/restricted Packages
Ign http://security.ubuntu.com gutsy-security/universe Sources
Ign http://security.ubuntu.com gutsy-security/main Sources
Ign http://archive.canonical.com gutsy/partner Packages    
Ign http://archive.canonical.com gutsy/partner Sources     
Err http://archive.canonical.com gutsy/partner Packages    
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com gutsy/partner Sources     
  Could not resolve 'archive.canonical.com'
Ign http://archive.ubuntu.com gutsy/main Packages          
Ign http://archive.ubuntu.com gutsy/universe Packages      
Ign http://archive.ubuntu.com gutsy/restricted Packages    
Ign http://archive.ubuntu.com gutsy/multiverse Packages    
Ign http://archive.ubuntu.com gutsy/universe Sources       
Ign http://archive.ubuntu.com gutsy/main Sources           
Ign http://archive.ubuntu.com gutsy/multiverse Sources     
Ign http://archive.ubuntu.com gutsy/restricted Sources     
Ign http://archive.ubuntu.com gutsy-updates/universe Packages
Ign http://archive.ubuntu.com gutsy-updates/main Packages  
Ign http://archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://archive.ubuntu.com gutsy-updates/restricted Packages
Ign http://archive.ubuntu.com gutsy-updates/universe Sources
Ign http://security.ubuntu.com gutsy-security/multiverse Sources
Ign http://security.ubuntu.com gutsy-security/restricted Sources
Ign http://archive.ubuntu.com gutsy-updates/main Sources  
Err http://security.ubuntu.com gutsy-security/universe Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Packages
  Could not resolve 'security.ubuntu.com'
Ign http://archive.ubuntu.com gutsy-updates/multiverse Sources
Err http://security.ubuntu.com gutsy-security/multiverse Packages
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Packages
  Could not resolve 'security.ubuntu.com'
Ign http://archive.ubuntu.com gutsy-updates/restricted Sources
Err http://security.ubuntu.com gutsy-security/universe Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/main Sources 
  Could not resolve 'security.ubuntu.com'
Ign http://archive.ubuntu.com gutsy-proposed/universe Packages
Err http://security.ubuntu.com gutsy-security/multiverse Sources
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com gutsy-security/restricted Sources
  Could not resolve 'security.ubuntu.com'
Ign http://archive.ubuntu.com gutsy-proposed/main Packages 
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Packages
Ign http://archive.ubuntu.com gutsy-proposed/restricted Packages
Ign http://archive.ubuntu.com gutsy-proposed/universe Sources
Ign http://archive.ubuntu.com gutsy-proposed/main Sources
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Sources
Ign http://archive.ubuntu.com gutsy-proposed/restricted Sources
Ign http://archive.ubuntu.com gutsy-backports/universe Packages
Ign http://archive.ubuntu.com gutsy-backports/main Packages
Ign http://archive.ubuntu.com gutsy-backports/multiverse Packages
Ign http://archive.ubuntu.com gutsy-backports/restricted Packages
Ign http://archive.ubuntu.com gutsy-backports/universe Sources
Ign http://archive.ubuntu.com gutsy-backports/main Sources
Ign http://archive.ubuntu.com gutsy-backports/multiverse Sources
Ign http://archive.ubuntu.com gutsy-backports/restricted Sources
Err http://archive.ubuntu.com gutsy/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/main Sources          
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/main Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-updates/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/main Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-proposed/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/universe Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/main Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/multiverse Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/restricted Packages
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/universe Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/main Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/multiverse Sources
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy-backports/restricted Sources
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/Release.gpg  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/source/Sources.gz  Could not resolve 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jay@jay-laptop:~$ 



```

---

### Post by MisanthropicAnthropoid on 2008-08-17
I'm sorry for being so exasperating, but I'm really stuck. I've been searching, but I can't find any guides for how to install a wireless card without an internet connection (save the one that sends me to the non-working packages.ubuntu.com).

---

### Post by nicedude on 2008-08-17
By that last output it looks like whatever source lists it is trying to pull are not being gotten correctly, try changing in sources where it says "server" just change that to a different server and see if that works better for you. Also 7.10 is not the newest Ubuntu install disk available and I would recommend you to get a copy of 8.04 Hardy Heron as the Wifi support out of the box is probably a little better ( supposed to be allot better, but some people still have probs ). Since you have already installed though ( assuming you work out the sources thing ) you can use the commands the gentleman told you before which will both update your sources lists & update your system to 8.04, just if you install to other machines in future you should arm yourself with the newest disk as it means less stuff will need updating etc. You should also just really google around using your exact wifi adapter model and the word Ubuntu and you will probably find articles by people who use the same device that will tell you what works best etc. Ubuntu is not Vista as the hardware manufacturers spend most all of their time providing drivers to MS and they add them all to their install disks, this is so people who can just turn on a computer can use one, Ubuntu can be that easy but usually isn't as you will hit a snag here and there with certain hardware. This is not the Ubuntu developers fault as they try to get drivers for everything as well but sometimes the manufacturers won't provide either Linux drivers or enough info about how a piece of hardware works to allow others to build linux drivers for said hardware. So feel free to send an Email to whoever the manufacturer or your wifi is and let them know you want to see them give support for Linux. On its own that email will do nothing but if they get 1000 such emails they might have to change their minds and give support where it is needed. If everyone using Linux did this then we would all be much better off in short order ( I send one whenever I hit a device that won't work - mostly printers though ). As a final note I would say to research hardware's linux compatibility before purchasing it as that will save you tons of hassle in the end.

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **nicedude said:**
> By that last output it looks like whatever source lists it is trying to pull are not being gotten correctly, try changing in sources where it says "server" just change that to a different server and see if that works better for you. 


 This is not the Ubuntu developers fault as they try to get drivers for everything as well but sometimes the manufacturers won't provide either Linux drivers or enough info about how a piece of hardware works to allow others to build linux drivers for said hardware. So feel free to send an Email to whoever the manufacturer or your wifi is and let them know you want to see them give support for Linux. On its own that email will do nothing but if they get 1000 such emails they might have to change their minds and give support where it is needed. If everyone using Linux did this then we would all be much better off in short order ( I send one whenever I hit a device that won't work - mostly printers though ). As a final note I would say to research hardware's linux compatibility before purchasing it as that will save you tons of hassle in the end.

1. Before I shut down again, will this work without an internet connection? 

2. This hardware is extremely standard; people get it recognized all the time. I just can't find any tutorial that's comprehensible to a newb.

---

### Post by MisanthropicAnthropoid on 2008-08-17
So, after trying all of these things, my problem remains that I still can't download the bcm43xx-fwcutter package while using Vista (and I can't download anything while using Ubuntu). Any new suggestions, or things that I'm screwing up?

---

### Post by MisanthropicAnthropoid on 2008-08-17
On second thought, I found a lot of places to download certain forms of this, I just have no way of telling which one I need. How do I tell which to choose from this list? [http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/](http://archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/)

---

### Post by decoherence on 2008-08-17
hi there

you want one of the ones ending in .deb.

if you were running ubuntu 8.04 i'd suggest getting the latest. maybe get it anyway. worst case it complains about not being able to satisfy dependencies. if that happens, try an older one.

why is this such a pain? because you're trying to mix non-free (the broadcom firmware) with free (everything else.) this remains the biggest source of problems for anyone using linux.

---

### Post by MisanthropicAnthropoid on 2008-08-17
Wow. This is such a mess. I was able to find a hardwired connection for about 45 seconds (long enough to follow the instructions on page that ryadt linked me to) before the cable crapped out. It's now jammed into an old computer, which for some reason, will accept a cable with some serious loose wires. 

However, I still can't get it to recognize any wireless connections. When I type in iwconfig, I still get the same output as before (page 1).

ETA: Also, "network connections" all of a sudden takes 1-2 minutes to load. And still doesn't recognize anything.

---

### Post by nicedude on 2008-08-17
You are not screwing up per se , beyond using a 7.10 gutsy install disk instead of a 8.04 Hardy disk ( which I would say use the newest one ). Most people in this type of situation just connect their Ethernet cable up to the laptop to the router and use it until they get the Wifi up and running correctly. So if there is anyway for you to use your wired connection until you get everything working that is best, heck go to a friends and do it if need be. If instead you only have wifi with Vista to work with and no other way then you need to download a DEB package of whatever software you need. Deb packages are kind of like windows EXE installers as you just double click it and once open you select install , if install says there are unsatisfied dependencies ( other stuff you need that isn't installed ) then you can write those all down and get Debs of them as well, then install the dependancies before the app that said it needed them :-) 

There are several sources for deb packages, which is short for debian packages. A google search for those terms will find several sources.

Here is a link to a deb of b43-fwcutter package

[http://es.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/](http://es.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/)

Just select the i386 one if you installed 32bit or AMD64 if you installed 64bit.

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **nicedude said:**
> You are not screwing up per se , beyond using a 7.10 gutsy install disk instead of a 8.04 Hardy disk ( which I would say use the newest one ). Most people in this type of situation just connect their Ethernet cable up to the laptop to the router and use it until they get the Wifi up and running correctly. So if there is anyway for you to use your wired connection until you get everything working that is best, heck go to a friends and do it if need be. If instead you only have wifi with Vista to work with and no other way then you need to download a DEB package of whatever software you need. Deb packages are kind of like windows EXE installers as you just double click it and once open you select install , if install says there are unsatisfied dependencies ( other stuff you need that isn't installed ) then you can write those all down and get Debs of them as well, then install the dependancies before the app that said it needed them :-) 

There are several sources for deb packages, which is short for debian packages. A google search for those terms will find several sources.

Here is a link to a deb of b43-fwcutter package

[http://es.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/](http://es.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/)

Just select the i386 one if you installed 32bit or AMD64 if you installed 64bit.

Trouble is, I got the CD from a friend, who only had 7.10. As I said earlier, I was able to get the ethernet cord from my parents' computer for long enough to install the b43-fwcutter package. Unfortunately, that ethernet cord is old and the wires are loose, and I lost connection. After a half hour, I was able to get it to connect back into their computer, and I'm not taking it out again. But I have the deb package, the firmware for Broadcom 43xx chipset family claims to be "enabled." But aside from that, I'm in an identical position to before, and I'm not sure why.

---

### Post by oldsoundguy on 2008-08-17
The reason that Vista installs your wireless card is the underlying reason for the bloat within the system.  The fact that every driver known to man loads with the system and is available at a seconds notice.

Linux builds, on the other had, are custom built by the user (in a way) by only installing what they need to function.  Sometimes that has to be done manually for cards with questionable ancestry. (most Atheros chip based cards will install right out of the box.)(all of mine did)

[http://www.google.com/search?q=install+wireless+in+gutsy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=install+wireless+in+gutsy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

how to's of all kinds.  Really depends on the card, and some even have to be installed with "ndswrapper", a program that fools the card chip into thinking it is working in Windows.

You need to FIRST and foremost find out what chip you are dealing with. That will refine your install choices.

---

### Post by MisanthropicAnthropoid on 2008-08-17
> **oldsoundguy said:**
> The reason that Vista installs your wireless card is the underlying reason for the bloat within the system.  The fact that every driver known to man loads with the system and is available at a seconds notice.

Linux builds, on the other had, are custom built by the user (in a way) by only installing what they need to function.  Sometimes that has to be done manually for cards with questionable ancestry. (most Atheros chip based cards will install right out of the box.)(all of mine did)

[http://www.google.com/search?q=install+wireless+in+gutsy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=install+wireless+in+gutsy&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

how to's of all kinds.  Really depends on the card, and some even have to be installed with "ndswrapper", a program that fools the card chip into thinking it is working in Windows.

You need to FIRST and foremost find out what chip you are dealing with. That will refine your install choices.

1. The reason for the trouble is understandable. I suspect the switch will pay off fabulously in the long run (else I wouldn't have made it), but it's a pain in the butt right now. 

2. I did everything that they told me to on the howto that Ryabt linked me, but it's still giving me the same message.

3. I have a Broadcom 94311. Ubuntu recognized the BCM 43xx family, and after a long time of soliciting help in this thread, I was able to enable the firmware. Now I'm stuck again.

---

### Post by MisanthropicAnthropoid on 2008-08-17
So, I've continued to try different combinations of instructions found here and elsewhere, and I've still gotten nowhere. I do have another output that may be relevant. It doesn't mean anything to me, but I'm sure it does to y'all. Whether or not the information is useful is the real question. Anyways, here's what I input/output: ```

jay@jay-laptop:~$ sudo lshw -C network
[sudo] password for jay:
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 7c:8b:cf:24:1b:00
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.60 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:00:00:1a:73:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
jay@jay-laptop:~$ 



```

---

### Post by nicedude on 2008-08-17
try giving me the output of this command

sudo iwlist eth1 scan

That should list if your card at the present time can see any wifi networks.
Also give us all a iwconfig to see what that says at this time.

iwconfig

post those and I can see maybe what is the state of this adapter.

---

### Post by MisanthropicAnthropoid on 2008-08-18
iwconfig results in the exact same error as I posted on page 1. I'll go hunt down the output to that other command.

---

### Post by MisanthropicAnthropoid on 2008-08-18
> **nicedude said:**
> try giving me the output of this command

sudo iwlist eth1 scan



eth1 no scan results

---

### Post by nicedude on 2008-08-18
Well if iwlist eth1 scan says that no results and you know that there is a wireless router transmitting nearby then your wifi card is not installed properly. I was hoping it would see something and maybe this is a WPA/WEP configuration problem but it is not as the scan would have at least saw the AP.


I assume you installed bw43-cutter package ? If so did you use the command to  download and install a driver with it? You will have to be connected to the internet via Ethernet for this to work.

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

This command downloads the correct driver legally from Broadcom and installs it. This is assuming you have the bw43-cutter package already installed. Please do whatever it takes to plug in your Ethernet card for 5 minutes and do this and report back here the result ( sorry but we need some network access here to do this as I don't know anyway to download a driver that I don't which one you need, that script will/should know and should grab it ) I just had to read through forums and find that piece of info for you as I don't use Broadcom hardware ( Atheros here :-) ). Also you could send an Email to broadcom to complain about Linux driver support as each Email they get means nothing on its own but together our Emails matter more than anything else we can all do.

Post back after you do this, whether it works or not as I want to see what happens :-)

---

### Post by MisanthropicAnthropoid on 2008-08-18
I believe I was able to install that in my five minutes of snagging an ethernet cord earlier, but I'll try that command and report back on what it does (probably tomorrow though). Thanks for the help!

---

### Post by nicedude on 2008-08-18
You are welcome but please do that as I found that the command I gave you is step 2 of installing with the bw43-cutter software. Aparently bw43-cutter is just a sort of driver downloader and installer not the actual driver itself and running that command which calls a script should install the correct driver. Please post if it works though ( I hate when people just disappear and you don't know and someone else might ask me this sometime :-) ). Also mark this thread as solved if it works as well.

---

### Post by MisanthropicAnthropoid on 2008-08-18
> **nicedude said:**
> 

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh


Output: command not found 


I'm sure that's exactly what you wanted to hear. :-\

ETA: For clarification, I didn't directly download the b43-fwcutter package. I just clicked "enable" on the firmware button in the "restricted drivers" section, and it said it was downloading what was needed.

---

### Post by nicedude on 2008-08-18
Please do it like I said and install the bw43-fwcutter package as the command that didn't work is because you didn't do that. Also in the stupid restricted driver manager uncheck this device. I just uninstall that silly Jockey restricted manager as it causes more problems than it ever solves. Please just try it like I type it. I will help you till hell freezes over ( or preferably till you get wifi :-) ) but I cant help if you don't follow my advice. Linux has a very small margin for getting creative in this type of problem. From what I saw on the net your adapter is not supported by the default drivers like Jockey tries to download and instead you must use the bw43-fwcutter and let it download the driver that will work.

Please just try exactly what I suggested, If it doesn't work I will try and research why.

nicedude

---

### Post by MisanthropicAnthropoid on 2008-08-18
> **nicedude said:**
> Please do it like I said and install the bw43-fwcutter package as the command that didn't work is because you didn't do that. Also in the stupid restricted driver manager uncheck this device. I just uninstall that silly Jockey restricted manager as it causes more problems than it ever solves. Please just try it like I type it. I will help you till hell freezes over ( or preferably till you get wifi :-) ) but I cant help if you don't follow my advice. Linux has a very small margin for getting creative in this type of problem. From what I saw on the net your adapter is not supported by the default drivers like Jockey tries to download and instead you must use the bw43-fwcutter and let it download the driver that will work.

Please just try exactly what I suggested, If it doesn't work I will try and research why.

nicedude

I tried exactly what you suggested, although I couldn't download it from your link, so I picked one of the 32 bit ones from the link I posed at the beginning of page 3 (I don't know if this was a mistake, but that's what I did). Still having trouble on the output: ```
 jay@jay-laptop:~$ sude /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
bash: sude: command not found
jay@jay-laptop:~$ 
```

Also, I found another thread giving a step by step instruction for this particular wireless card, but it's sadly using outdated links, so I don't know how to follow the instructions. Here is the link though, in case it helps: [http://ubuntuforums.org/showthread.php?t=769990](http://ubuntuforums.org/showthread.php?t=769990)

---

