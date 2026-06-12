---
title: "Hardy x86_64 Howto - Install googleearth-4.3"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by | MM | on 2008-04-27
[According to Google Earth Help forum member alexsid]("http://groups.google.com/group/earth-linux/browse_thread/thread/8eca0fe2595f18de#"), Hardy Heron broke 32-bit support for DNS on 64-bit system.  This means that all 32-bit apps have problems with DNS resolution and with regard to Google Earth, you get a warning prompt on start-up similar to the following: 

[I]Google Earth detected an error while trying to authenticate.  Please 
check the following: 
- your network connection (can you get to [www.google.com?](www.google.com?)) 
- your firewall settings (are you blocking /home/username/google- 
earth/ 
googleearth-bin?) 
Error code: 29 
For more information, visit:[/I]

So here's how i installed Google Earth and got everything working great:

1)  [Add the Medibuntu repository]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f");
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``` 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
2)  Install Google Earth; 
```
sudo apt-get install googleearth-4.3
```
3) Fix 32-bit DNS support on x86_64 Hardy.
```
sudo apt-get install lib32nss-mdns
```

To launch Google Earth;
```
googleearth
```

Alternatively, navigate to the *Applications* menu -> *Internet* -> *Google Earth*

Hope that helps some people!

---

### Post by shayke on 2008-05-02
Hi MM
I followed your instructions - the installation went OK and I don't get this error massage. But still I don't see earth - just black screen with white dots.
Am I missing something? :???:

---

### Post by NiGhtPiSH on 2008-05-02
Well it's not working for me too. Is it because of the Wubi install?

---

### Post by scrapmetal on 2008-05-02
[B]Manually installing Google Earth, from as below, have encounteredthis in terminal mode after getting to _NOTE:1._

name@machine:~$ sudo apt-get install lib32nss-mdns
[sudo] password for name:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct                                                 the problem.[/B]

[B]What do I do now? As there 5 packages avaiable for update and the 
&#8220;updater reports&#8221; 

&#8220;Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).&#8221;

Would you like to attempt ot resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.&#8221;
WHAT THE........ ???[/B]

Code:
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
Code:
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
2) Install Google Earth; 
Code:
sudo apt-get install googleearth-4.3

[B]_NOTE:1._   sudo apt-get install googleearth-4.3 finished with OK(could NOT click on OK so used the enter key,....waited ... no change ...... closed the current terminal window, launched a new one, and tried below in a new terminal window)
Unable to run.&#8220;Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).&#8221;[/B]

3) Fix 32-bit DNS support on x86_64 Hardy. 
Code:
sudo apt-get install lib32nss-mdns
To launch Google Earth; 
Code:
googleearth
Alternatively, navigate to the Applications menu -> Internet -> Google Earth Hope that helps some people!
Firefox-2 install went fine using Adept Manager.
So did Skype  using terminal using,
sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb;

:)

So far 8.04 on an amd 3200+ with a nvida 6800Gt, on agigabyte motherboard and a sata 320 gig has run beutifully. Will be going on 2 others as soon as google earth runs and updates are restored. :)

:confused:**Thanks to all involved.**

---

### Post by | MM | on 2008-05-02
> **shayke said:**
> Hi MM
I followed your instructions - the installation went OK and I don't get this error massage. But still I don't see earth - just black screen with white dots.
Am I missing something? :???:

hmmm, i have seen it take a while before the earth is displayed... but i've just left it and it has appeared finally.  It may be something to do with having to download some data from google which is taking a while (but thats just speculation).

Otherwise i dont really have any ideas.

---

### Post by scrapmetal on 2008-05-03
Thanks  to  a **posting in beginners  forum**, this was corrected by
1. Make sure adept manger and all other down  load  program/terminal commands are shut/NOT running, then in terminal -run

	 	 	 	 	  sudo dpkg --configure -a
 2. Then had 5 auto updates which could be loaded. One of which was the EULA for Google Earth. Proceeded as  per  instructions  (ie: agreed to EULA). Google Earth runs, it has requested updated drivers for 6800GT to enable quicker or enhanced viewing? Will comply latter.

**Thanks to all.:)**

---

### Post by mwinslettTX on 2008-06-04
If the earth doesn't appear in the window, be sure to turn off compiz.  That worked for me.  I guess the two don't play nice with each other.

Cheers!

---

### Post by bigtel on 2008-06-05
I too have followed this method and only see stars...!!

If I use 'terminal' though with 'sudo googleearth' - it all works great. What is going on??

---

### Post by dsiddens on 2008-06-15
I'm getting stopped at the second step: sudo apt-get install googleearth-4.3: I can scroll down but cannot agree to the EULA OK.

---

### Post by jpvirgin on 2008-06-19
use tab key to move cursor to agree to terms.

I also can confirm that I only get stars when using command 

googleearth but everything seems to work when using 

sudo googleearth

---

### Post by ozzyprv on 2008-07-29
> **jpvirgin said:**
> use tab key to move cursor to agree to terms.

I also can confirm that I only get stars when using command 

googleearth but everything seems to work when using 

sudo googleearth

Same here!

---

