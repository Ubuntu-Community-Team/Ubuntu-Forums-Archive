---
title: "Problem after upgrade"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by Gelai on 2012-05-13
Hi Ubuntu People, :)

im one of the Newbie people who using Ubuntu, 

I Upgraded my system thru Termnal, then when it says i need to restart the system, so then i Restarted it, and now if Flash the Pink Screen then after the Terminal Screen Came and some sort of process there saying like: 

[implemented]                    [OK]

and That's IT I'm STUCK there FOREVER.. I've tried some sorts of commands which I red from Forums, but i still didn't get it Working again.. I feeling hopeless finding the solution, i didn't touch my Ubuntu OS for almost 3weeks, and Reinstalling again is not a good solution for me.. 

Could Please Someone Help me to resolve my Problem.. 
Thank You Very Much..!

---

### Post by mörgæs on 2012-05-13
Moved to a new thread.

---

### Post by NikTh on 2012-05-13
> **Gelai said:**
> I've tried some sorts of commands which I red from Forums, but i still didn't get it Working again..

Hi ,
Can you tell us what commands did you tried ?

When you are in this black terminal try to login with your username & password and run these commands.
```
sudo apt-get update ; sudo apt-get install --fix-missing 
sudo apt-get -f install 
sudo dpkg --configure -a
``` 

Then reboot to see if anything fixed.

---

### Post by Gelai on 2012-05-16
> **NikTh said:**
> Hi ,
Can you tell us what commands did you tried ?

When you are in this black terminal try to login with your username & password and run these commands.
```
sudo apt-get update ; sudo apt-get install --fix-missing 
sudo apt-get -f install 
sudo dpkg --configure -a
``` 

Then reboot to see if anything fixed.



Hi Sir, :)

I already re-installed UBUNTU 11.10 on my Laptop (HP G6 1045SX) and now I gradually installing some Updates and upgrades this is what I did.

1. Fresh Install Ubuntu 11.10 alongside Win7 (works and boot properly after installation)
2. I installed kernel 3.0.0.19-generic-PAE then after reboot it bring me to terminal and showing like "wl_--------   implement   [OK] then it hangs there. so I restarted the system to "Previous Version w/c is 3.0.0.12-generic-pae. then i am able to login again.
3. I always need to choose the option "Previous Version" on boot bcoz of the 3.0.0.19 -pae error brings me. Then I installed my ATI 6470M via previous version. followed similar like on this site (i can't find the real site w/c i get the commands) [http://penreturns.rc.my/2012/04/how-to-install-amd-ati-catalyst-124.html](http://penreturns.rc.my/2012/04/how-to-install-amd-ati-catalyst-124.html)
4. I totally won't able to get in to LOG IN GUI, always bring me to the terminal and appearing error like i mentioned on No. 2.
5. So when im in the No. 4, what i did is to login on the Terminal w/c is using  Alt+CTRL + F1 then, there I Ran commands "sudo apt-get update && sudo apt-get upgrade"
6. After Successfull "Update and Upgrade" I rebooted and it Stuck-Up in Terminal Saying something Like "BATTERY STATE" ...?

sorry i can post some commands and SS now regarding my system, coz im in my work right now, but i try to post it here soon as i get home.. 

But Please can you Help Me, to solved my Problem using Ubuntu 11.10.. What I want to do is to Manage Perfectly the Installation and Run Perfectly my UBUNTU like what I am doing in Windows.
I mean I want to established it like what Ive done on Windows. ie.(firewall, connections, graphics installed and perfectly working,Fully 100% RAM working,) you know what mean.. :) 
Please Sir,, :)

Thank you very much...!! :) :)

---

### Post by Gelai on 2012-05-17
Updated: :)
i followed instruction on this link [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)  and it all installation went well, but again after the reboot im stuck-up at the terminal with "battery state" is ther and 3 lines of some sort process.

So, to be able to get back to the LogIn GUI, I issued command $sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disable and reboot.. and it works and Im able to login Ubuntu 11.10. but when i re-instated the command and reboot it brings back to the same error. so i Disable it again.

I ran this and it showed:
$lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible Controller [0300]: ATI Technologies Inc NI Seymour [AMD Radeon HD 6470M] [1002:6760]

how can i activate and work properly the ATI VGA..??? 

Pleasee............. Anyone There.....? =)

---

### Post by Peter09 on 2012-05-17
OK - this is often caused by an incompatible graphics card. Try getting into recovery mode by holding the shift key during boot. This should get you into a screen showing a couple of boot options. Leave the top one selected and press e (for edit).
 
You should see the boot parameters on the screen, move the cursor to just before the 'quiet' parameter and insert the text (as a separate word)
 
```
nomodeset
```
 
Having done that press F10, which should start the boot proceess (I tink B also works).
 
See what happens and report back (tell us which graphics card you have)

---

### Post by Gelai on 2012-05-17
Thanks Sir Peter09,, i've tried pressing and holding SHIFT but it always goes me to the Ubuntu Login.. any other idea..? :)  

I also manually choose the recovery mode, but it didn't show up anything on my screen, it just hanging..

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> OK - this is often caused by an incompatible graphics card. Try getting into recovery mode by holding the shift key during boot. This should get you into a screen showing a couple of boot options. Leave the top one selected and press e (for edit).
 
You should see the boot parameters on the screen, move the cursor to just before the 'quiet' parameter and insert the text (as a separate word)
 
```
nomodeset
```
 
Having done that press F10, which should start the boot proceess (I tink B also works).
 
See what happens and report back (tell us which graphics card you have)


I Got what your instruction :) and here is the results after inserting this "ro   nomodeset quiet" press "F10" and it goes again the terminal saying *PulseAudio configure blahh..blaahhh.."
"saned disabled; edit /etc/default/saned"

like before, but this one dont have the battery state..

---

### Post by Peter09 on 2012-05-17
Mmmm .. make sure that you hold shift as early as you can, just after the Bios boot (or even earlier). How are you getting to recovery mode?

---

### Post by Peter09 on 2012-05-17
Do you get to a terminal prompt after the boot with nomodeset (its not permanaent you will need to do this everytime). If you get to a terminal prompt can you login?
 
If so try this line:
 
```
sudo apt-get install fglrx
```
 
what happens?

---

### Post by Gelai on 2012-05-17
i have dual-boot win 7 first installed. and UBUNTU GRUB is the first seen on screen, like this

Ubuntu, w/ Linux 3.0.0-19-generic-pae
Ubuntu, w/ Linux 3.0.0-19-generic-pae(recovery mode)
Previous Linux Version
-(Mem TEst)
-Memtest + serial
Windows 7 (loader) (on /dev/sda1)

there. so LET The TOP LINE option Highlighted and press "E"
and i change it there then press "F10"

here's what i've did:
1. when reinstated "sudo mv /etc/X11/xorg.conf.disable /etc/X11/xorg.conf"
and rebooted, I still get same error happens.
2. i reboot my machine again and Do as what you've instructed for entering "nomodeset" and press "F10" and still it didn't bring me to the Ubuntu GUI Login.
3. While in the terminal error i login to tty by pressing "CTRL+ALT+F1" and i ran this command again "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disable" to be able for me to Get in the GUI again.
 __Note: I;ve reinstall my ubuntu Yesterday, and ran "sudo apt-get update && apt-get upgrade" Ones..

i really don't understand.. Please! :) :)

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> Do you get to a terminal prompt after the boot with nomodeset (its not permanaent you will need to do this everytime). If you get to a terminal prompt can you login?
 
If so try this line:
 
```
sudo apt-get install fglrx
```
 
what happens?


I've ran this and this is the message.

Reading  package lists.. Done
Building dependency tree
Reading State information... Done
fglrx is already the newest version
0 upgrade, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by Peter09 on 2012-05-17
Just to get to a baseline can you do:
 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> Just to get to a baseline can you do:
 
```
sudo apt-get update
sudo apt-get upgrade
```

ohh.... i dont have internet access for my Laptop now :( :(
i bring it here in my office but they're using proxy here, and i don't know how to get internet working in my Ubuntu terminal.. :( :( 

do have other option how to make it working on my laptop...? =)

---

### Post by Peter09 on 2012-05-17
OK,
what happens if you issue these commands
 
```
startx
```
 
and the output of 
 
```
 
lspci -C video

```

---

### Post by Peter09 on 2012-05-17
Also get rid of the xorg.conf file that you created, move it to a new filename, that will be confusing things.
 
Try to reboot again using the nomodeset option.

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> Also get rid of the xorg.conf file that you created, move it to a new filename, that will be confusing things.
 
Try to reboot again using the nomodeset option.


I'm logged in now to my ubuntu again, coz every time I config my graphic card and it doesnt work after the reboot. ive run this command "sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.disable" and restart. so then my ubuntu get works again,and im able to log-in..but still it doesnt solve the issue of ATI VGA, its still not working on my system.

---

### Post by Peter09 on 2012-05-17
If you are into a desktop can you check in settings - third party software, see if it is asking you to install a driver.

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> If you are into a desktop can you check in settings - third party software, see if it is asking you to install a driver.

in my Additional Drivers Settings, theres a 
1. "ATI/AMD propriety FGLRX graphics driver(post-release updates)"
2. "Broadcom STA Wireless driver"
3. "ATI/AMD propriety FGLRX graphics driver"

i have not yet "Activate" one of them coz I am thinking that i may have an error again, cause i install ATI via Terminal command and may be there will be a conflict when i try to activate this VIA GUI... what do you think Sir Peter06.? =)

---

### Post by Peter09 on 2012-05-17
Activate 2 and 3 but not 1.
 
(you may not be able to do this without an internet link)

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> Activate 2 and 3 but not 1.
 
(you may not be able to do this without an internet link)

Im having Failure message, 
"please hava a look at the log file for details: /var/log/jockey.log"

oppss.. sorry may be i will just try this when i connected to internet later. :) 
i will keep you posted.. =)

Thank U verymuch Mr Peter.. i highly appreciated your Time giving some help to me.. I hope it'll resolved this soon.. =) i am almost a month with this error regarding my ATI Graphic Card.

---

### Post by Peter09 on 2012-05-17
the command
 
```
tail /var/log/jockey.log
```
 
will show the last few lines of this log.

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> the command
 
```
tail /var/log/jockey.log
```
 
will show the last few lines of this log.


it seems that it trying to download something and in the end of the lines says " DEBUG: BroadcomWLHandler enable(): kmod disabled, bcm43xx: Blacklisted, b43: Blacklisted, b43legacy: Blacklisted"

---

### Post by Peter09 on 2012-05-17
Think you need an internet connection.

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> Think you need an internet connection.


Hi Peter I already manage to activate the Broadcom .. the "jockey.log" error still exist when i tried to update the ATI Propriety Drivers w/c is number 3.  do you have idea how can fix this one..? 

many thanks.. :)

---

### Post by Gelai on 2012-05-17
Hi there.. Anybody can help me pleasseeee! :( :(

---

### Post by Peter09 on 2012-05-17
IF you are on the internet you could try 
 
 
```
sudo apt-get purge fglrx
```
 
to remove any installed drivers and then try again. You must be on the internet because if you reboot before enabling the driver you could lose your graphics and would have to reinstall through the command line.

---

### Post by Gelai on 2012-05-17
sudo apt-get update
[sudo] password for vale: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources/DiffIndex                    
Get:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Get:5 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [2,604 B]           
Get:6 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [4,338 B]     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [2,472 B]                  
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [4,266 B]            
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric InRelease                             
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports InRelease                   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [37.8 kB]       
Get:10 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric Release.gpg [198 B]                
Get:11 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [1,959 B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [16.5 kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,644 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [118 kB] 
Get:16 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]      
Get:17 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric Release [40.8 kB]                  
Get:18 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates Release [40.8 kB]          
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [3,939 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [36.5 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,371 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [71 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:26 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports Release [40.8 kB]        
Get:27 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [56.5 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_PH                    
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [25.2 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_PH             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:30 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]       
Get:31 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]        
Get:32 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]        
Get:33 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
Get:34 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:35 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:36 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Get:37 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]    
Get:38 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]
Get:39 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:40 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Get:41 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/main Sources [140 kB]      
Get:42 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/restricted Sources [3,347 B]
Get:43 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/universe Sources [52.7 kB] 
Get:44 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,660 B]
Get:45 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/main i386 Packages [344 kB]
Get:46 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6,631 B]
Get:47 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/universe i386 Packages [113 kB]
Get:48 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,363 B]
Get:49 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:50 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:51 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [72 B]
Get:52 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:53 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/main Sources [2,742 B]   
Get:54 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]
Get:55 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/universe Sources [9,019 B]
Get:56 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]
Get:57 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/main i386 Packages [3,296 B]
Get:58 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:59 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/universe i386 Packages [13.4 kB]
Get:60 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:61 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:62 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:63 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:64 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [73 B]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric/universe Translation-en               
Get:65 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/main Translation-en [155 kB]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:66 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-updates/universe Translation-en [67.7 kB]
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Fetched 12.9 MB in 1min 2s (206 kB/s)                                          
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I encountered this when i tried to update.

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> IF you are on the internet you could try 
 
 
```
sudo apt-get purge fglrx
```to remove any installed drivers and then try again. You must be on the internet because if you reboot before enabling the driver you could lose your graphics and would have to reinstall through the command line.


Hi peter, here is the results. what should i do next...? :)

vale@r-vaLe:~$ sudo apt-get purge fglrx
[sudo] password for vale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle* fglrx-dev*
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
After this operation, 130 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 162335 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx-dev ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: while removing fglrx, directory '/usr/lib/i386-linux-gnu/xorg/extra-modules' not empty so not removed.
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-19-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by Peter09 on 2012-05-17
Now try to install number 2 using the third party software in settings

---

### Post by Gelai on 2012-05-17
after issuing this "sudo apt-get purge fglrx" i activate the (ATI/AMD propriety FGLRX graphics) and it download and activated. But after it rebooted. Im back to terminal again.. it says like.. 
"Stopping.. finding unattende downloads.." like that.. i think im close to the Finish line.. :D :D please sir.. :) :)

---

### Post by Peter09 on 2012-05-17
think you may need to do
 
```
sudo apt-get upgrade
```

---

### Post by Gelai on 2012-05-17
i've checked on what the error is .. its says..
"speech Dispatcher disable; edit /etc/default/speech-dispatcher"
"Checking for running unattended-updates
Stopping anac(n)ronistic cron
_"

this is the last lines.. =)

---

### Post by Gelai on 2012-05-17
> **Peter09 said:**
> think you may need to do
 
```
sudo apt-get upgrade
```

i've already issued this command. but still i get the same problem and there is another 2 lines added. 

"Starting CUPS printing spoolet/sever"
"Starting CPU Interrupts Balancing daemon"

that is the last two lines. and it stuck-up there.. 

do you have way to resolved this..? thank you so much..

---

### Post by Gelai on 2012-05-17
Please help me.. anyone has an idea to solved my Problem..? please tell me the solution... thank you.. thank you..

---

### Post by Gelai on 2012-05-17
Anyone has an idea..? please help me solve this issue..

---

### Post by Gelai on 2012-05-18
I Disable again the xorg.conf by doin it at the TTY1 by typing this commands; "sudo mv /etc/X11/xorg.conf etc/X11/xorg.conf.diasble" to able for me to go back inside my ubuntu again,,i think there something wrong with my "xorg.conf" file and need to edit the content. but i have no idea how to do it. Please can someone guide me to fix my ATI graphic cards and get it working.. i struggling with this issue. hope you wont mind helping me..

---

### Post by Gelai on 2012-05-18
vale@r-vaLe:~$ sudo aticonfig --initial -f
Uninitialised file found, configuring.
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.

Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-6
vale@r-vaLe:~$ sudo aticonfig --input=/etc/X11/xorg.conf --tls=1
Warning: Option 'UseFastTLS' doesn't affect running session.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-12

i ran above commands, and i dont know now of what is going to happen again, if i reboot my system.

---

### Post by Gelai on 2012-05-18
and again,, i encounter the same problem like on my post #32 and #33, and i renamed xorg.conf again, to get in here.. =( =(

---

### Post by Gelai on 2012-05-18
i ran "sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*" and now i am totally cracked-down my Ubuntu, no more TTY only black screen, and won't boot to recovery.

---

### Post by Gelai on 2012-05-18
i manage to get in to TTY1 by erasing the "splash" in the GRUB, and i activated the ATI/AMD again at the Drivers Update.. but now i still don't understand why my ATI is still not in the system info,, and i don't know if it is working or not.. any help...?

---

