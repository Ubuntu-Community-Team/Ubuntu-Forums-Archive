---
title: "HP plugin"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by mijdrawoh on 2011-09-24
U10.04 In trying to install my HP1020 printer, I attempted to download the required plugin. I got an error message that the digital signature and the plugin didn't match so I am unable to print. The second alternative to the download is to use a plugin previously installed. I have successfully gotten the plugin on an earlier Ubuntu version and in another Linux os. My question: where would I find the plugin?

This explanation of the problem was obviously inadequate. In order to use an HP1020 printer in UBUNTU a plugin must be downloaded from hp-setup. That plugin file apparently has been corrupted and can't be used and it is highly unlikely that HP will do anything about correcting the problem. The alternative is to use a previously downloaded plugin. I have, in the past, successfully downloaded and installed the plugin so somewhere on my computer there's a file that contains the plugin. My question is: does anyone know in what file it might be located and how I could access that file?

---

### Post by LowSky on 2011-09-25
I find HP's version always better than Ubuntu's.. well HP usually works, and Ubuntu's doesn't in my experience.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by mijdrawoh on 2011-09-25
This explanation of the problem was obviously inadequate. In order to use an HP1020 printer in UBUNTU a plugin must be downloaded from hp-setup. That plugin file apparently has been corrupted and can't be used and it is highly unlikely that HP will do anything about correcting the problem. The alternative is to use a previously downloaded plugin. I have, in the past, successfully downloaded and installed the plugin, so somewhere in my computer is a file that contains the plugin. My question is: does anyone know in what file it might be located and how I could access that file?

---

### Post by LowSky on 2011-09-25
re-installing the plugin using my link fixes your issues. it circumvents the Ubuntu version and uses the HP version which I believe is more up to date as well.

I have a HP Laserjet 1018 which is a nearly identical model. I know what I'm talking about.

---

### Post by marce155 on 2011-09-26
Same problem here...
I've already downloaded the hplip but during the setup process it needs to download the hplip-plugin from
```
http://www.openprinting.org/download/printdriver/auxfiles/HP/plugins/hplip-3.11.7-plugin.run
```[FONT=Arial][SIZE=2]problem: the site is down for maintenance (maybe due to the hack on sep/8 ) and I don't have an old version of the hplip-plugin

I would be very nice if someone who managed to download it in the past could upload the file for me (searched google but found no alt. mirror) or give me a link to a download mirror that I've missed during my search
[/SIZE][/FONT]

---

### Post by ttoolin on 2011-09-26
I am having similar problems with an HP laserjet 1000, and hp-setup reporting a corrupt plugin.  I am having a bigger problem with hp-setup not seeing the printer plugged into my Vista box on my home network (I'm hoping that if I plug the printer into the ubuntu laptop long enough to install it, then I can plug it into the Vista box and change the IP address to where the printer is).

One thing I plan to try is to install a version of hplip that pre-dates the plugin (I seem to remember a time when the plugin was not needed, a few years ago).  I've tried a bunch of stuff to successfully load this plugin.  It's worked in the past, and sure isn't now!

---

### Post by collisionystm on 2011-09-26
I always have a problem with the HPLIP setup in Ubuntu. You need to manually run the plugin script yourself and then re-run setup. 

I watched what was going on in the terminal and saw where it failed.

Run this script with sudo. Its the HP plugin download.

chmod +x hplip-3.11.1-plugin.run
sudo ./hplip-3.11.1-plugin.run

When its done, ( should take less than second ), run your HPLIP setup again.

EDIT:

File didn't attach. Had to .zip it first! 

EDIT:

Nevermind, that did not work either!

Uh... anyone care to help? I am not in front of a linux box at the moment. lol.

---

### Post by collisionystm on 2011-09-26
Here we go.

[http://www.mediafire.com/?cwe04mcvjb11j4x](http://www.mediafire.com/?cwe04mcvjb11j4x)

---

### Post by collisionystm on 2011-09-26
I am sure you can find the hp plugin file that I uploaded to mediafire on your system, Like I said, I am on a windows box right now but I keep this file on a drive for this purpose lol.

---

### Post by marce155 on 2011-09-26
> **collisionystm said:**
> Here we go.

[http://www.mediafire.com/?cwe04mcvjb11j4x](http://www.mediafire.com/?cwe04mcvjb11j4x)

thanks a lot, working fine now!

---

### Post by ttoolin on 2011-09-27
Thanks for the link for the patch.  I'm a little confused on using it, though . . . should I zip it first?  Is it not going to work?  Or . . . might it be the two lines of code, listed, to install it.

In any case, thanks a lot for the assistance!  I've been fighting this plugin problem for around two weeks, now.

terry

---

### Post by Lexus45 on 2011-09-28
**Found the solution:**
[http://hplipopensource.com/hplip-web/plugin_download.html](http://hplipopensource.com/hplip-web/plugin_download.html)
Just install the latest hplip version from [http://hplipopensource.com/](http://hplipopensource.com/) and then the downloaded plugin.

---

### Post by rimibchatterjee on 2011-11-06
Am in the process of downloading hplip for the second time (the first time it turned out to be corrupted). I notice that Ubuntu 11.10 is not listed among the supported versions. I checked 11.04 instead. Will this be an issue, and if so has anyone worked around it?
EDIT sorry my status says I'm running Ubuntu 10.04. I switched to 11.10, but every time I try to change my distro statement it says 'You do not have authority to edit this page'. Why not? It's my profile page dammit.

---

### Post by rimibchatterjee on 2011-11-06
Okay, I tried to run hplip-3.11.1-plugin.run and was told the system needs hplip-3.11.7.run. Does anyone know of a good mirror site that hosts this plugin? I tried googling the name but got a lot of weird-looking sites which I'm not sure i should trust.

---

### Post by rimibchatterjee on 2011-11-07
Sorry to bump this thread again, but I ran hplip-3.11.10.run and encountered seven missing dependencies which I'm not sure were filled. It ran without producing any more errors, but now I'm getting printer state = Idle - /usr/lib/cups/backend/hp failed 
How do I fix this? Run again?

---

### Post by rimibchatterjee on 2011-12-03
Update: I ran hp-check and got the report, hpmudext is missing. This is the relevant echo:

Checking 'hpmudext' I/O extension...
error: NOT FOUND OR FAILED TO LOAD! Please reinstall HPLIP and check for the proper installation of hpmudext.

I have subsequently reinstalled hplip-3.11.10.run multiple times and it still hasn't solved the problem. is it possible to get a working version of hpmudext and patch it in?

---

