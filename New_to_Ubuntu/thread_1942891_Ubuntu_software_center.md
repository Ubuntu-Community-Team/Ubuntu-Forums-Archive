---
title: "Ubuntu software center"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Oinkzter on 2012-03-18
Hello, i have this problem with ubuntu 11.10's software center that i was hoping you could help me with.
Every time i try to download something from the software center it gives me this error message


There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.


i really hope that you could help me



- Oinkzter

---

### Post by Holdolin on 2012-03-18
Is this a fresh install, or something you've been using a while?

---

### Post by linuxd1 on 2012-03-18
Try to install a program using terminal or synaptic and let us know if you get the same problem !

---

### Post by Oinkzter on 2012-03-18
> **Holdolin said:**
> Is this a fresh install, or something you've been using a while?

its a couple of weeks since i installed it but i haven't installed anything yet.
I have already tried to search for updates xD

---

### Post by Oinkzter on 2012-03-18
> **linuxd1 said:**
> Try to install a program using terminal or synaptic and let us know if you get the same problem !

i don't have synaptic and im not sure how to download in terminal?

---

### Post by linuxd1 on 2012-03-18
> **Oinkzter said:**
> i don't have synaptic and im not sure how to download in terminal?

Open terminal and write for example sudo apt-get install amsn          | after write your password

---

### Post by mcduck on 2012-03-18
> **Oinkzter said:**
> i don't have synaptic and im not sure how to download in terminal?

Just for a start, pop open a terminal, run the following commands, and post the output here:

```
sudo apt-get update
sudo apt-get upgrade
```

(The first command loads lists of latest available package versions from the servers. And the second one installs any available updates.)

---

### Post by matt_symes on 2012-03-18
Hi

Open a terminal (ctrl + alt + t) and type

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen.

Post back any errors by copying  the text from the terminal (select text->right click->copy)

Paste the text into your next post between code tags like trhis

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

Open a terminal (ctrl + alt + t) and type

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen.

Post back any errors by copying  the text from the terminal (select text->right click->copy)

Paste the text into your next post between code tags like trhis

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards


```
oinkzter@Oinkzter:~$ sudo apt-get update
[sudo] password for oinkzter: 
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease              
Ign http://archive.ubuntu.com oneiric-backports InRelease            
Hit http://archive.canonical.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release.gpg
Ign http://archive.ubuntu.com oneiric-security InRelease
Hit http://archive.ubuntu.com oneiric Release.gpg                    
Hit http://archive.canonical.com oneiric Release                     
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://archive.ubuntu.com oneiric-updates Release.gpg
Hit http://archive.ubuntu.com oneiric-backports Release.gpg
Hit http://archive.ubuntu.com oneiric-security Release.gpg            
Hit http://archive.canonical.com oneiric/partner i386 Packages
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://archive.ubuntu.com oneiric Release  
Hit http://archive.ubuntu.com oneiric-updates Release
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main i386 Packages               
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric-backports Release              
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric/universe i386 Packages         
Hit http://archive.ubuntu.com oneiric/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources     
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/universe Sources       
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources     
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex  
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/main Sources         
Hit http://archive.ubuntu.com oneiric-backports/restricted Sources   
Hit http://archive.ubuntu.com oneiric-backports/universe Sources
Hit http://archive.ubuntu.com oneiric-backports/multiverse Sources   
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages   
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/restricted Sources    
Hit http://archive.ubuntu.com oneiric-security/main Sources          
Hit http://archive.ubuntu.com oneiric-security/universe Sources      
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources    
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages    
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex 
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en      
Hit http://archive.ubuntu.com oneiric/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric/universe Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en    
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by matt_symes on 2012-03-18
Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Do you currently have update-manager or software-center currently open ?

If you do then close it and re-run the command again. 

If neither are open then this may be your problem so post back and say so.

Kind regards

---

### Post by Holdolin on 2012-03-18
from the last line in that output, it looks like there may be another package manager running.

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Do you currently have update-manager or software-center currently open ?

If you do then close it and re-run the command again. 

If neither are open then this may be your problem so post back and say so.

Kind regards

they are not open, and know i i try to open ubuntu software center nothing happens, its just blank.

---

### Post by matt_symes on 2012-03-18
Hi

From the terminal, type this command

```
lsof /var/lib/dpkg/lock
```

Does it return anything ? Post back results.

Kind regards

---

### Post by Ownager on 2012-03-18
> **Oinkzter said:**
> they are not open, and know i i try to open ubuntu software center nothing happens, its just blank.

Hello, can you please post a screenshot of your desktop include your terminal here? We will be able to see what's wrong with that situation. Thanks a lot.

---

### Post by speedwlk on 2012-03-18
Hi!
I have seen a similar problem before. In that situation, one of the software sources was set as the Ubuntu CD, so that - while checking for updates the system kept waiting for the cd.


I am not sure whether you have the same problem, but please try the following.

Go to "Software Sources" [should be available under "System Settings"]
If the Ubuntu 11.10 CD is marked as a source, uncheck the corresponding box and reboot the system.
Then do "sudo apt-get update" followed by "sudo apt-get upgrade" from the terminal.


Please note that if the CD is not marked as a source then your problem is different from what I have just mentioned.

Good Luck!

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

From the terminal, type this command

```
lsof /var/lib/dpkg/lock
```Does it return anything ? Post back results.

Kind regards

that brings up nothing

---

### Post by Oinkzter on 2012-03-18
> **speedwlk said:**
> Hi!
I have seen a similar problem before. In that situation, one of the software sources was set as the Ubuntu CD, so that - while checking for updates the system kept waiting for the cd.


I am not sure whether you have the same problem, but please try the following.

Go to "Software Sources" [should be available under "System Settings"]
If the Ubuntu 11.10 CD is marked as a source, uncheck the corresponding box and reboot the system.
Then do "sudo apt-get update" followed by "sudo apt-get upgrade" from the terminal.


Please note that if the CD is not marked as a source then your problem is different from what I have just mentioned.

Good Luck!

the CD is not marked and never has been

---

### Post by Oinkzter on 2012-03-18
> **Ownager said:**
> Hello, can you please post a screenshot of your desktop include your terminal here? We will be able to see what's wrong with that situation. Thanks a lot.

this was fixed after a reeboot

---

### Post by matt_symes on 2012-03-18
Hi

> **Oinkzter said:**
> that brings up nothing

Try this

```
ps aux | egrep "update-manager|software-center|apt|dpkg|synaptic"
```

You can copy and paste it from this post into the terminal to make it easier.

Please paste back the results. 

I assume you are still get that same error (locked file) after sudo apt-get update ? Run that command again just to be sure.

Kind regards

---

### Post by matt_symes on 2012-03-18
Hi

> this was fixed after a reeboot

I'm glad it's fixed :)

Something had a lock on dpkg. A reboot will often help but it would have been nice to see what was locking it just in case the problem survived reboots.

Kind regards

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Do you currently have update-manager or software-center currently open ?

If you do then close it and re-run the command again. 

If neither are open then this may be your problem so post back and say so.

Kind regards

none of this is open. And if i try installing using terminal it gives me this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by matt_symes on 2012-03-18
Hi

See my posts #19 and #20.

I assume it's fixed ?

Kind regards

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```Do you currently have update-manager or software-center currently open ?

If you do then close it and re-run the command again. 

If neither are open then this may be your problem so post back and say so.

Kind regards

none of this is open. when i try to install something using terminal it gives me this error:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

See my posts #19 and #20.

I assume it's fixed ?

Kind regards

when i do that it give me:

```
oinkzter@Oinkzter:~$ ps aux | egrep "update-manager|software-center|apt|dpkg|synaptic"
root      2493  0.0  0.0   4764  1184 ?        S    20:21   0:00 sudo apt-get upgrade
root      2494  0.1  0.6  33232 24200 ?        S    20:21   0:00 apt-get upgrade
root      2984  0.0  0.7  32592 28728 pts/1    Ss+  20:21   0:00 /usr/bin/dpkg --status-fd 43 --unpack --auto-deconfigure /var/cache/apt/archives/ttf-mscorefonts-installer_3.3ubuntu4_all.deb /var/cache/apt/archives/libssl1.0.0_1.0.0e-2ubuntu4.2_i386.deb
root      2991  0.0  0.2  13508  9104 pts/1    S+   20:21   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
root      3004  0.0  0.0   2048   512 pts/1    S+   20:21   0:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
oinkzter  4157  0.0  0.0   4452   776 pts/2    S+   20:33   0:00 egrep --color=auto update-manager|software-center|apt|dpkg|synaptic

```

---

### Post by matt_symes on 2012-03-18
Hi

I'm confused. Is the problem fixed ?

Kind regards

---

### Post by Oinkzter on 2012-03-18
lets try once more, when im trying to download something from the software center it gives me this error message:

```
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.
```

i have already tried to download it in the terminal but that did not work.

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

I'm confused. Is the problem fixed ?

Kind regards

i'm confused to xD

---

### Post by matt_symes on 2012-03-18
Hi

```
oinkzter@Oinkzter:~$ ps aux | egrep "update-manager|software-center|apt|dpkg|synaptic"
root      2493  0.0  0.0   4764  1184 ?        S    20:21   0:00 sudo apt-get upgrade
root      2494  0.1  0.6  33232 24200 ?        S    20:21   0:00 apt-get upgrade
root      2984  0.0  0.7  32592 28728 pts/1    Ss+  20:21   0:00 /usr/bin/dpkg --status-fd 43 --unpack --auto-deconfigure /var/cache/apt/archives/ttf-mscorefonts-installer_3.3ubuntu4_all.deb /var/cache/apt/archives/libssl1.0.0_1.0.0e-2ubuntu4.2_i386.deb
root      2991  0.0  0.2  13508  9104 pts/1    S+   20:21   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
root      3004  0.0  0.0   2048   512 pts/1    S+   20:21   0:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
```

So it's not fixed.  This looks to be your problem > usr/bin/dpkg --status-fd 43 --unpack --auto-deconfigure /var/cache/apt/archives/ttf-mscorefonts-installer_3.3ubuntu4_all.deb /var/cache/apt/archives/libssl1.0.0_1.0.0e-2ubuntu4.2_i386.deb
(Let's kill all the processes using dpkg). From the terminal type

```
sudo kill 2493
```

```
sudo kill 2494
```

```
sudo kill 2984
```

```
sudo kill 2991
```

```
sudo kill 3004
```

Try to fix what is there.

```
sudo apt-get install -f
```

If/when asked to accept the EULA on the ms-ttf-core-fonts screen hit the TAB key to move to OK and hit then enter key.

Kind regards

---

### Post by Oinkzter on 2012-03-18
> **matt_symes said:**
> Hi

```
oinkzter@Oinkzter:~$ ps aux | egrep "update-manager|software-center|apt|dpkg|synaptic"
root      2493  0.0  0.0   4764  1184 ?        S    20:21   0:00 sudo apt-get upgrade
root      2494  0.1  0.6  33232 24200 ?        S    20:21   0:00 apt-get upgrade
root      2984  0.0  0.7  32592 28728 pts/1    Ss+  20:21   0:00 /usr/bin/dpkg --status-fd 43 --unpack --auto-deconfigure /var/cache/apt/archives/ttf-mscorefonts-installer_3.3ubuntu4_all.deb /var/cache/apt/archives/libssl1.0.0_1.0.0e-2ubuntu4.2_i386.deb
root      2991  0.0  0.2  13508  9104 pts/1    S+   20:21   0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
root      3004  0.0  0.0   2048   512 pts/1    S+   20:21   0:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst upgrade 3.3ubuntu4
```So it's not fixed.  This looks to be your problem 
(Let's kill all the processes using dpkg). From the terminal type

```
sudo kill 2493
``````
sudo kill 2494
``````
sudo kill 2984
``````
sudo kill 2991
``````
sudo kill 3004
```Try to fix what is there.

```
sudo apt-get install -f
```If/when asked to accept the EULA on the ms-ttf-core-fonts screen hit the TAB key to move to OK and hit then enter key.

Kind regards


All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
oinkzter@Oinkzter:~$ 
 
now what?


YES!!!! that helped, i'm now able to download from the software center. thanks a lot guys xD

---

### Post by matt_symes on 2012-03-18
Hi

This time i'm glad it *is* fixed :D Please mark this thread as solved using the thread tools.

Kind regards

---

### Post by Ownager on 2012-03-18
This thread needs to be completely solved now. I am going to inform one of these administrators. I am glad that your problem is solved now. I was confused at first too. Anyway, good luck with installing new applications and games.

---

