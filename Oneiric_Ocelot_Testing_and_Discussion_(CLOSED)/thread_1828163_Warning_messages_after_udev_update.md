---
title: "Warning messages after udev update"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-18
After todays udev (173-0ubuntu2) update I can see a number of warning messages early on boot process.
These do not harm in any way booting or anything else, but it does not look professional either :D .

---

### Post by ratcheer on 2011-08-18
Yes, I get them too.

Tim

---

### Post by brazov on 2011-08-18
> **Harry33 said:**
> After todays udev (173-0ubuntu2) update I can see a number of warning messages early on boot process.
These do not harm in any way booting or anything else, but it does not look professional either :D .

+ 1

It writes 100 times something like

Failed to execute /lib/udev/input_id ...

---

### Post by Quackers on 2011-08-18
Me too :-)

---

### Post by cecilpierce on 2011-08-18
Que Sera Sera ...

Just when things were looking better :mad:

---

### Post by ventrical on 2011-08-18
Same here for 2 days now .. but still works. I am tempted to install GRUB Legacy and see if that clears that up because I use to have the latest GRUB Menu but that  has been wiped out somwhere.. but boot still works. I would guess to wait for the next kernel update and this may fix it .. or any ideas anyone ?

---

### Post by jagallagher on 2011-08-18
Same here.

---

### Post by dino99 on 2011-08-19
Dont complain about the new udev package rules: devs want it strict now, so its normal that it show warnings that was unknown before. That way debugging will be more complete.

---

### Post by Harry33 on 2011-08-19
> **dino99 said:**
> Dont complain about the new udev package rules: devs want it strict now, so its normal that it show warnings that was unknown before. That way debugging will be more complete.

Right, like I said, just visual carbage, no operational problems so far.
However, it would look a lot better if these would be printed to some log file only.

---

### Post by dino99 on 2011-08-19
> **Harry33 said:**
> Right, like I said, just visual carbage, no operational problems so far.
However, it would look a lot better if these would be printed to some log file only.

fully agree  ;)

---

### Post by ventrical on 2011-08-19
Here...


[http://www.youtube.com/watch?v=2uR_TVm1e0I](http://www.youtube.com/watch?v=2uR_TVm1e0I)

---

### Post by cariboo on 2011-08-19
I only see the error messages on my install from the middle of June. The fresh install I did last night, doesn't show the errors.

---

### Post by ventrical on 2011-08-19
I am thinking of just that , a fresh install on my Dell Inspiron, but I would like to resolve this on my Acer somehow. Thanks so much for your reply.

---

### Post by ventrical on 2011-08-19
Ok.. I  took a chance and experimented by installing GRUB Legacy from Synpatic and it worked as far as getting rid of the larger warning messages from the pre-boot screen. All that there is, is the little screen with warning messages.

I can only wonder why installing GRUB legacy would get rid of those large opening warning messages.

---

### Post by Harry33 on 2011-08-20
> **ventrical said:**
> Ok.. I  took a chance and experimented by installing GRUB Legacy from Synpatic and it worked as far as getting rid of the larger warning messages from the pre-boot screen. All that there is, is the little screen with warning messages.

I can only wonder why installing GRUB legacy would get rid of those large opening warning messages.

If you mean the font size is now smaller for those warning messages, it is because the grub can now choose a higher resolution suitable for your mother board.

For example with nvidia proprieatary drivers you typically need to use additional commands (gfxpayload=keep) in /etc/default/grub to get the correct resolution.

---

### Post by ventrical on 2011-08-20
> **Harry33 said:**
> If you mean the font size is now smaller for those warning messages, it is because the grub can now choose a higher resolution suitable for your mother board.

For example with nvidia proprieatary drivers you typically need to use additional commands (gfxpayload=keep) in /etc/default/grub to get the correct resolution.

Thank you for that clarification. Perhaps you have a suggestion as to what to do about this. Caribou suggested a fresh install (or at least chose that route). Myself, I am trying to get a better understand how how to clean things up without having to always do fresh installs. For me it is a matter of 'usage' from my IP and I am trying to keep things to budget.

Would it be frugal to wait this bug out or do a fresh install? I am just curious as to your opinion.

Thanks in advance.

---

### Post by Harry33 on 2011-08-20
> **ventrical said:**
> Thank you for that clarification. Perhaps you have a suggestion as to what to do about this. Caribou suggested a fresh install (or at least chose that route). Myself, I am trying to get a better understand how how to clean things up without having to always do fresh installs. For me it is a matter of 'usage' from my IP and I am trying to keep things to budget.

Would it be frugal to wait this bug out or do a fresh install? I am just curious as to your opinion.

Thanks in advance.

OK.
First tell us what is your graphics card and the driver you are using.
The warning messages are not harmfull, just a bit ugly to see, though.

---

### Post by Xgen on 2011-08-20
I don't know about a fresh install...I am testing different variations of oneiric on four partitions. One I reinstalled yesterday with the latest daily. The half dozen lines of warning messages are still there...albeit harmless. All testing done with the 64 bit version.

---

### Post by Harry33 on 2011-08-20
> **Xgen said:**
> I don't know about a fresh install...I am testing different variations of oneiric on four partitions. One I reinstalled yesterday with the latest daily. The half dozen lines of warning messages are still there...albeit harmless. All testing done with the 64 bit version.

It may very well be that the warning messages are still generated even though they are not visible during every boot.
For example, I do not see them every time.
Often the screen is black right after mobo booting text, until I see the login screen.
This is because I use these lines in /etc/default/grub

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

GRUB_GFXPAYLOAD_LINUX=1024x768

```

So those commands just hide the warning messages in my setup.

---

### Post by ventrical on 2011-08-20
> **Harry33 said:**
> OK.
First tell us what is your graphics card and the driver you are using.
The warning messages are not harmfull, just a bit ugly to see, though.


00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)


 I think the poster after you has the right idea_ multiple partitions.  I have 3 extra laptops to work with.
I just like trying different things.

  Oneiric works beautifully, especially with compiz pre-release working alongside it. I know most of this install is going to be overwritten by updates and then beta installs so I should just save my settings. It is just that it seems to work so well (it's almost like a stable release).

Thanks for your time.

btw .. Did you get rid of  those warning msgs on your PC?

---

### Post by Harry33 on 2011-08-20
> **ventrical said:**
> 
...
btw .. Did you get rid of  those warning msgs on your PC?

No I did not.
It is just that grub usually hides them, like I explained above.

---

### Post by ventrical on 2011-08-20
> **Harry33 said:**
> No I did not.
It is just that grub usually hides them, like I explained above.

 I  re-installed grub-pc from synaptic, edited that 'grub' file in root, entered the code you had posted and the LARGEer warning messages are gone at the first screen with just the reduced ones there as to when I was running with GRUB legacy.

 Thanks.

Doing multiple partitons  then would not work either.

---

### Post by pqwoerituytrueiwoq on 2011-08-21
is there a way i can view the full report it does not fit on the screen? (edit: cat /var/log/boot.log | less)

if you want them off
sudo nano /etc/udev/udev.conf
change info to err

---

### Post by Harry33 on 2011-08-21
> **pqwoerituytrueiwoq said:**
> 
if you want them off
sudo nano /etc/udev/udev.conf
change info to err

The default setting in /etc/udev/udev.conf
is
udev_log="err"

---

### Post by pqwoerituytrueiwoq on 2011-08-21
> **Harry33 said:**
> The default setting in /etc/udev/udev.conf
is
udev_log="err"
it was set to info when i installed the daily in my virtual box yesterday

---

### Post by JRV on 2011-08-21
Since I updated I get the same messages, also my gigabit ethernet runs at 100 meg, and it is not enabled until I log on.  So I can't log on with ssh or xdmcp.

This happened early in the Natty and Oneiric development cycles, it went away and now it is back.

My /etc/udev/udev.conf setting is 

udev_log="err"

---

### Post by mhsy on 2011-08-22
Hey,

This is my first post. In my case, only the recovery session runs. I cannot get into ubuntu or gnome. I was wondering if there was anything I could do?

After an update to 11.10 a few days ago, I started getting the udev error, and since then have not been able to log in.

Thanks,
Jean

---

### Post by garvinrick4 on 2011-08-22
> **mhsy said:**
> Hey,

This is my first post. In my case, only the recovery session runs. I cannot get into ubuntu or gnome. I was wondering if there was anything I could do?

After an update to 11.10 a few days ago, I started getting the udev error, and since then have not been able to log in.

Thanks,
Jean
You upgraded into oneiric so try to see what you are running lightdm or gdm most likely
have both installed.
cltr/alt/F1
```
sudo dpkg-reconfigure lightdm
```Choose lightdm
I believe it is one of those toggle with tab key things.
I do not know if gdm still works in 11.10
But most likely the udev lines you are getting are not the problem I think most all are
getting that now, we are in middle stages of 11.10 so still some breakage now and again. I would look into lightdm.
Provides: x-display-manager
Description: Display Manager
 LightDM is a X display manager that: * Has a lightweight codebase * Is
 standards compliant (PAM, ConsoleKit, etc) * Has a well defined interface
 between the server and user interface * Cross-desktop (greeters can be written
 in any toolkit)
#Might get by with starting and stopping lightdm and or stopping gdm and starting lightdm? Got to fiddle with it after upgrade instead of fresh install I believe.
#Hope this is not one of your first installs of Ubuntu, hard to keep the Alpha and Beta's runnig if it is.

---

### Post by ratcheer on 2011-08-22
edited to remove off topic question...

---

### Post by Harry33 on 2011-08-22
Please,
for lightdm, start a new thread.

---

### Post by ratcheer on 2011-08-22
Sorry.

Tim

---

### Post by ventrical on 2011-08-22
> **Harry33 said:**
> No I did not.
It is just that grub usually hides them, like I explained above.

I ended up doing a fresh install of Oneiric beside my current install. A few strange things happened, (like the installer reported and error that it could not finish the install) however - I was able to reboot and logg on to the new install and use synaptic to update those files. After doing this I now have my GRUB bootloader and all those  large verbose warning files - so I will have to edit the /grub  in the new install because GRUB never seemed to take off from the first install.I did edit /grub and was able to remove the larger verbose files , but , now that GRUB is being over written by the updates in the second install I will edit that file there.

---

### Post by Harry33 on 2011-08-22
> **ratcheer said:**
> Sorry.

Tim

Thanks Tim.

---

### Post by Harry33 on 2011-08-22
Here is a bug report (831516) on this udev issue:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/831516](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/831516)

---

### Post by ventrical on 2011-08-22
Thanks.

  My attempt at editing /grub in my new install failed to do anything - I still have those verbose warning msgs ... and I am not complaining .. I know this is A3 test.

---

### Post by ventrical on 2011-08-22
> **Harry33 said:**
> Here is a bug report (831516) on this udev issue:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/831516](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/831516)


Looks as if a fix may soon be on the way.

---

### Post by ventrical on 2011-08-22
@harry33,

What I did was just complete a successful install on a sideXside with two other Oneirics running. That is kernel 3.0.0.7 and the verbose warnings are completely gone.

  I would also like to note that during the install I did not choose to tic off the update box.

  Whatever the case , I am about to update with synaptic and most likely I will inherit whatever is in the repositories.

---

### Post by ventrical on 2011-08-22
Booting from 3.0.0 7 is a clean fix for now :)

---

### Post by cariboo on 2011-08-22
> **ventrical said:**
> Booting from 3.0.0 7 is a clean fix for now :)

That doesn't prove anything, as the problem didn't start until 3.0.0-8 was released.

---

### Post by ventrical on 2011-08-23
> **cariboo907 said:**
> That doesn't prove anything, as the problem didn't start until 3.0.0-8 was released.


Thats just my point. I thought this bug started at the kernel level. 3.0.0-7 no verbose warnings - 3.0. 0-8 =verbose warnings.

However.. I'm not 100% sure, but I did find some interesting script while installing the pre-release compiz ppas..

-------------------------------------------------------

dale1@dale1-Aspire-3620:~$ sudo add-apt-repository ppa:unity-tean/compiz-testing[sudo] password for dale1: 
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 77, in <module>
    ppa_info = get_ppa_info_from_lp(user, ppa_name)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 65, in get_ppa_info_from_lp
    lp_page = urlopen(req).read()
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 400, in open
    response = meth(req, response)
  File "/usr/lib/python2.7/urllib2.py", line 513, in http_response
    'http', request, response, code, msg, hdrs)
  File "/usr/lib/python2.7/urllib2.py", line 438, in error
    return self._call_chain(*args)
  File "/usr/lib/python2.7/urllib2.py", line 372, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 521, in http_error_default
    raise HTTPError(req.get_full_url(), code, msg, hdrs, fp)
urllib2.HTTPError: HTTP Error 404: Not Found
dale1@dale1-Aspire-3620:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg        
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [39.8 kB]          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [873 kB]               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,313 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,722 kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [153 kB]         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,582 kB]       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [9,032 B]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [6,451 kB]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [181 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Fetched 14.0 MB in 1min 3s (220 kB/s)                                          
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  udev
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 365 kB of archives.
After this operation, 8,192 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/main udev i386 173-0ubuntu2 [365 kB]
Fetched 365 kB in 1s (190 kB/s)
(Reading database ... 148794 files and directories currently installed.)
Preparing to replace udev 172-0ubuntu5 (using .../udev_173-0ubuntu2_i386.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up udev (173-0ubuntu2) ...
udev start/running, process 17900
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-9-generic
dale1@dale1-Aspire-3620:~$ 

--------------------------------

What gets me is that during the update just after fresh install I 'unmarked'   (udev) just to see what would happen. Of course this had nothing to do with it but I do notice that installing some softwares will invoke other updates to be installed (which were originally unmarked)!

As previously discussed the warning messages leaked into the startup for other various reason at the kernel level.

So, just for the sake of clairity, when I choose  3.0.0-7 from the Grub menu I do not get any verbose warning at boot.

---

### Post by VinDSL on 2011-08-23
w00t!

The "fake udev" update, I just performed, got rid of the warning messages.  

Sweet! :D

---

### Post by Harry33 on 2011-08-23
Right,
the udev update (173-0ubuntu3) fixes this issue.

> udev (173-0ubuntu3) oneiric; urgency=low

  * Include input_id in the initramfs to prevent errors when enumerating
    devices in early init (LP: #831516).

Here:
[https://launchpad.net/ubuntu/oneiric/+source/udev/173-0ubuntu3](https://launchpad.net/ubuntu/oneiric/+source/udev/173-0ubuntu3)

---

### Post by VinDSL on 2011-08-23
Yep, that's the one.

Worked a treat!  ;)

---

### Post by ventrical on 2011-08-23
..and that now went to the Omnibus and kernel update!

Looks great!

---

