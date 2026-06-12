---
title: "[SOLVED] Temperature display"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by garfunk3l on 2008-10-15
Hi, I'm very new to Ubuntu.
Basically, I have a hp laptop with core2duo T5500 and nvidia go 7200. The cooling system is bad so a friend recommended I try ubuntu as it's more efficient than windows.
So I set it up for dual-booting and to test the theory I want some way of checking the temp of the cpu cores, the hdd and the gpu. I have spent hours reading various forums but nothing seems to work. I have to work through a proxy at my university and for some reason the system won't accept the proxy settings (even though firefox does) and so I can't use the terminal or add/remove to get programs. Some I managed to download with firefox but don't work, the only thing that has brought me any joy was emifreq 0.18 but it doesn't support multi-cores. So I downloaded the version that does but it downloaded as an archive that I couldn't get to work (and probably messed up a lot in my system trying as I don't know what I'm doing).
I have hardy heron, and it says that Lm-sensors are installed but the how tos on the net either don't work for me or refer to things I don't know how to do.
So my question is, is there a simple (minimal fuss) applet I can get that will show me these temps, and is there a way I can undo any damage I may have done to my settings from groping around in the dark so to speak.

Any help will be very much appreciated but bear in mind I'm new to this and I don't know the first thing about the terminal or how to navigate around in the files (they're so different to xp)

David

---

### Post by TCSnyder on 2008-10-15
If you are just wanting to Display your thermal reading you can open a terminal and try 
```
acpi -t
``` 

acpi is used for battery charge ( if on a laptop ) and thermal. 

That command will give you a reading in celcius. for Fahrenheit try

```
acpi -t -f
``` 

that should do the trick

---

### Post by garfunk3l on 2008-10-15
Thanks, that worked. So next step, how do I get the gpu temp and the hard drive temp?
Is there a way of restoring the system to make sure I didn't wreck anything trying to install those archive things?
Also is there an applet I can use to display the temperatures?

Cheers,

David

---

### Post by TCSnyder on 2008-10-16
as far as an applet goes you could try screenlets. it is a widget manager and you can use its widgets or you can get them from google gadgets and use them in screenlets. so you might want to give it a try. i am not sure about your other questions though. Good Luck.

---

### Post by garfunk3l on 2008-10-16
Cool, how do I get screenlets? It didn't come up in add/remove (system seems to be okay with the proxy all of a sudden, can't comlain). Also it seems that one should only use add/remove unless they really know what they're doing, would that seem accurate?

Cheers,

Dave

---

### Post by TCSnyder on 2008-10-16
here is a link to another thread 

[http://ubuntuforums.org/showthread.php?t=901633]("http://ubuntuforums.org/showthread.php?t=901633")

you can install screenlets through a cite called [http://www.getdeb.net]("http://www.getdeb.net") 
search for it and just click to install

---

### Post by garfunk3l on 2008-10-16
Ok, I downloaded screenlets, its .deb so it installed easy. There was no temperature monitor so I downloaded one called temperature2 off this site: [http://screenlets.org/index.php/Temperature2](http://screenlets.org/index.php/Temperature2)
So it's downloaded as a .tar.gz file on the desktop. The site says that for installation: "Install as usual by extracting the contents of the screenlet's archive to the directory "$HOME/.screenlets". "
Can you talk me through how to do that?

Cheers,

David

PS: What does this mean? "Requires no additional libraries. Runs with the default installation. If you want to be able to monitor HDD temperature, you need hddtemp installed and running as daemon."

---

### Post by garfunk3l on 2008-10-16
Cool, I found another thread that says you can just drag and drop a .tar.gz screenlet thing into the screenlets main window and it installs automatically. Only CPU2 seems to change though, I'll have to play around with it.

---

### Post by garfunk3l on 2008-10-16
Everything works. I have 4 little temperature2 screenlets showing CPU1, CPU2, GPU and HDD. I have checked each using the terminal and it all works. After all this I have discovered that ubuntu makes no difference to the temperature of my computer but at least I know that now.

Cheers for your help.

David

---

