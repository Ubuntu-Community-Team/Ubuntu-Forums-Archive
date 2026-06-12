---
title: "HP dv6000 series no display when returning from standby"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by bdfoster on 2008-08-11
I've had troubles trying to get the laptop to sleep/standby without having to restart the computer. I can tell you I have compiz, but I don't really want to have to uninstall that in order to make this work. I know that it isn't locked up, because I got it to shut down once by pressing the power button and pushing enter, then it promptly shut down. Is there a fix for this? I'm using the x32 flavor even though I'm fully capable of using the x64 version. Any tips, hits, comments, concerns, questions...?

---

### Post by gobbles414 on 2008-08-11
> **bdfoster said:**
> I've had troubles trying to get the laptop to sleep/standby without having to restart the computer. I can tell you I have compiz, but I don't really want to have to uninstall that in order to make this work. I know that it isn't locked up, because I got it to shut down once by pressing the power button and pushing enter, then it promptly shut down. Is there a fix for this? I'm using the x32 flavor even though I'm fully capable of using the x64 version. Any tips, hits, comments, concerns, questions...? Are you running Ubuntu 8.04 (Hardy)? Or, are you running an older version of Ubuntu? Recovering from sleep/standby seems to be a lot better in 8.04 than in older versions of Ubuntu.

---

### Post by bdfoster on 2008-08-12
> **gobbles414 said:**
> Are you running Ubuntu 8.04 (Hardy)? Or, are you running an older version of Ubuntu? Recovering from sleep/standby seems to be a lot better in 8.04 than in older versions of Ubuntu.
Yes, I am running Hardy. This is the only real problem I have because I can't shut the lid with it on. If I do, I risk screwing up the system, so I let it run out of battery so it will shut down itself. Like I said before, it still runs, it isn't locking up. It shuts down at 5% battery life. I guess it's good for the battery because I don't use it enough.

---

### Post by gobbles414 on 2008-08-12
And you installed 3D drivers for your graphics by going *System => Administration => Hardware Drivers*?

---

### Post by bdfoster on 2008-08-13
> **gobbles414 said:**
> And you installed 3D drivers for your graphics by going *System => Administration => Hardware Drivers*?

Well, they were installed via ndiswrapper. I went to System > Administration > Hardware Drivers, and it says they are installed. Not for sure what that means, but it shouldn't be that big of a problem because the desktop effects are working.

---

### Post by scorp123 on 2008-08-13
> **bdfoster said:**
> I've had troubles trying to get the laptop to sleep/standby without having to restart the computer.  The most likely problem is that your OS unloads the binary "nvidia" driver from your computer's memory when it goes to sleep, but then fails to reload it again. Hence: the screen stays black when you resume.

I had a similar problem with one of my laptops. So you can try my solution. I guess it should still work with Ubuntu 8.04, the files etc. haven't changed much:

[http://ubuntuforums.org/showpost.php?p=3825488&postcount=2](http://ubuntuforums.org/showpost.php?p=3825488&postcount=2)

---

### Post by scorp123 on 2008-08-13
> **bdfoster said:**
> Well, they were installed via ndiswrapper. "ndiswrapper" only concerns WiFi (WLAN) devices ;)

[http://en.wikipedia.org/wiki/NDIS](http://en.wikipedia.org/wiki/NDIS)

---

### Post by bdfoster on 2008-08-14
> **scorp123 said:**
> The most likely problem is that your OS unloads the binary "nvidia" driver from your computer's memory when it goes to sleep, but then fails to reload it again. Hence: the screen stays black when you resume.

I had a similar problem with one of my laptops. So you can try my solution. I guess it should still work with Ubuntu 8.04, the files etc. haven't changed much:

[http://ubuntuforums.org/showpost.php?p=3825488&postcount=2](http://ubuntuforums.org/showpost.php?p=3825488&postcount=2)
Tried this. I think it would work, but I cannot write to this file. For some reason, I don't have permissions to write to this file.

---

### Post by bdfoster on 2008-08-14
> **scorp123 said:**
> "ndiswrapper" only concerns WiFi (WLAN) devices ;)

[http://en.wikipedia.org/wiki/NDIS](http://en.wikipedia.org/wiki/NDIS)

I'm sorry, yes I did get those confused. I had to use that to install my wireless drivers...

---

### Post by bdfoster on 2008-08-14
> **bdfoster said:**
> Tried this. I think it would work, but I cannot write to this file. For some reason, I don't have permissions to write to this file.

False alarm. Went into terminal and opened:
```
gksudo nautilus
```
then opened folder of file by typing etc/default, then found file, right-click>Preferences>Permissions and changed to read write on all levels, but you should only have to change the Root Group setting if you are a member of the root group. Please note you should change this back because this is a system file.

---

### Post by scorp123 on 2008-08-14
> **bdfoster said:**
> but I cannot write to this file. Of course not. It's a system file and you therefore need "root" unlimited God-like superpowers ;)

So you'd open a terminal and use the "sudo" command which temporarily grants those infinite powers to you ahead of the actual editor command, e.g. ```
sudo gedit /etc/default/acpi-support 
```

As I can see from your other posting you found out how to open "Nautilus" as "root". Well ... I agree, this works. But I am not really a fan of that method. One accidental drag & drop in any wrong place and your system is pretty much instantly hosed .... Been there, done that :)

So I'd recommend only to use "sudo" and similar commands for the specific tasks at hand and not use it on potentially "dangerous" (in the sense: it might hose your system) programs.

---

### Post by bdfoster on 2008-08-15
> **scorp123 said:**
> The most likely problem is that your OS unloads the binary "nvidia" driver from your computer's memory when it goes to sleep, but then fails to reload it again. Hence: the screen stays black when you resume.

I had a similar problem with one of my laptops. So you can try my solution. I guess it should still work with Ubuntu 8.04, the files etc. haven't changed much:

[http://ubuntuforums.org/showpost.php?p=3825488&postcount=2](http://ubuntuforums.org/showpost.php?p=3825488&postcount=2)

Works. Thanks a ton. Now I don't have to freak out when someone shuts the lid anymore.

---

### Post by scorp123 on 2008-08-16
> **bdfoster said:**
> Works. Thanks a ton. Now I don't have to freak out when someone shuts the lid anymore. Feel free to hit that "Thank you" button ... ;)

---

### Post by bdfoster on 2008-08-26
> **bdfoster said:**
> Works. Thanks a ton. Now I don't have to freak out when someone shuts the lid anymore.

Problem...Doesn't work after restart. How do I make it permanent?

---

### Post by starcannon on 2008-08-26
To open a text file with root priv's its is not necessary or recommended to change the files permissions. The safest way is to open the file in a text editor that is running with the correct permissions. 
Example:

```
gksu gedit /path/to/file_name
```

edit as needed, save, and exit. permissions still intact.

If you find yourself stuck in a command line or terminal you can edit in there very simply using
```
sudo nano /path/to/file_name
```

save and exit, again permissions left in tact. 

Generally only change permissions when there is no other way to do a thing I think, Linux is as safe as it is partially because of the permissions scheme.

---

### Post by bdfoster on 2008-08-30
> **starcannon said:**
> To open a text file with root priv's its is not necessary or recommended to change the files permissions. The safest way is to open the file in a text editor that is running with the correct permissions. 
Example:

```
gksu gedit /path/to/file_name
```

edit as needed, save, and exit. permissions still intact.

If you find yourself stuck in a command line or terminal you can edit in there very simply using
```
sudo nano /path/to/file_name
```

save and exit, again permissions left in tact. 

Generally only change permissions when there is no other way to do a thing I think, Linux is as safe as it is partially because of the permissions scheme.

Covered...but thank you for your input.:)

Still can't figure out why this isn't permanent. Anyone have a suggestion? Noticed I have remarked this thread unsolved.

---

### Post by bdfoster on 2008-08-31
Any ideas?

---

### Post by rjj_04 on 2008-09-26
I have a dv6000 and tried the acpi_support settings given.  Didn't work.  So then I noticed I was not running the proprietary NVIDIA driver... go to System->Admin->HardwareDrivers and enable/install the NVIDIA driver

then I noticed that the screen was at least flickering when the system tried to come out of suspend (before it was dead).  So, I knew I was getting somewhere now.  Flickering meant it was alive, and probably getting transfers to graphics device.  So, I changed the POST_VIDEO option to "true" to see if a reset of the device would work.... and lo and behold it was a miracle.  My system now comes out of suspend successfully. Excuse me, now I need go and try Hibernate... gee this is exciting :) hehehe

---

### Post by rjj_04 on 2008-09-26
So continuing on here.  Hibernate did not work.  Shutdown.  Look into that later.  Suspend initiated from dialog box works... but from closing lid did not work.  Looked like the graphics subsystem was not initialized.  When I lifted the lid, the system tries to power up but screen dead.  Aha, but, if I lift lid and very very quickly hit touchpad or key... the system will initialize the graphics system and all is well.  Wow, this code needs an overhaul :)   I tried, via the screensaver dialog, to make the closing lid "do nothing" but that did not help... seems closing did nothing but lifting did something.  Should be some consistency there, like closing does nothing, lifting should do nothing as well.

---

