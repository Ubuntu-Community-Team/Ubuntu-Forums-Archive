---
title: "NVidea Dashboard Command"
date: 2013-06-15
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-06-15
Hello Everybody,
what, or Is, there a command to get to the NVidea Dashboard?
Ubuntu 13.04
Thanks

---

### Post by sum1nil on 2013-06-15
Just type 'Nvidia' at the dashboard prompt, unless something is wrong, the settings icon will show up.
Good luck.

---

### Post by GUZZLR on 2013-06-15
I was afraid you would say something like that,  I've treid installing various drivers, and all have led to a very ugly boot screen, which all have led to yet another reinstall of Ubuntu on my hard drive.  I have found information at this site, just haven't tried it yet as I'm really tired of having to reload Ubuntu for the upteeth jillion time.

news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml

---

### Post by sum1nil on 2013-06-15
Plenty more to play with here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


Remember' at least in MHO open source and Nvidia are mutually exclusive beasts.

---

### Post by deadflowr on 2013-06-15
Do you mean nvidia-settings?

The nvidia control panel system.

---

### Post by GUZZLR on 2013-06-15
```
Do you mean nvidia-settings?
```

Yes, the control panel where I can set colors, digital vibrance, etc...

---

### Post by 3rdalbum on 2013-06-15
The instructions are for Ubuntu 10.04, not 13.04. You will probably break your system if you try.

---

### Post by deadflowr on 2013-06-16
> **GUZZLR said:**
> ```
Do you mean nvidia-settings?
```

Yes, the control panel where I can set colors, digital vibrance, etc...

nvidia-settings is the command.

you can even manipulate the settings via command line.
look at
```
man nvidia-settings
```

If it says no manual entry then install it
```
sudo apt-get install nvidia-settings
```

---

### Post by GUZZLR on 2013-06-16
```
The instructions are for Ubuntu 10.04, not 13.04. You will probably break your system if you try.
```

Right...10.04.  But at this point, it doesn't matter if I break my system, because I already have broke my system time and time again, and reloaded the system time and time again.  I've tried multiple drivers with NVidia, and nothing seems to work, been working on it now for about two months...really annoying.

---

### Post by GUZZLR on 2013-06-16
```
man nvidia-settings
```

In Mint, there is an X.org application which is similar to the NVidiea dashboard used in Windows.  It's odd that I can not find this application in the Ubuntu software store, but it is the Mint Software store. I visited the developers website hoping I could find some code to install the application in Ubuntu, but I did not see anything like that.
Has anybody been succesfull in installing the application in Ubuntu?
Thanks

---

### Post by wc711 on 2013-06-17
I had the Nvidia problem as well.  I got everything loaded, but the screen was horrible I could barely read it, but I stumble along and discovered the "additional drivers" icon.  I clicked it and got a screen that showed 3 Nvidia drivers.  This was with 12.01 and the descriptions of each were difficult to understand. I activated all 3 drivers and rebooted;  the screed was beautiful.  i ran into a problem when I tried to update the 300 updates that were ready.  It eventually was impossible. I uninstalled everything and decided to go with 13.04 so i wouldn't get back into the problem with 12.01.  I discovered a lunux program called Penn Drive for Linux.  It will do the install  from your DVD.  It just locks onto the iso file and takes off. At one point it wanted to know where I wanted to install.  Since I have a 500 gig HD I chose to partition option and took 175 gigs for my Ubuntu.  It does all the work for you.  Of course when I booted up, I got that horrible screen because of the missing Nvidia driver. Once again I found the "additional drivers" icon and the screen pop showed the 3 Nvidia drivers again.  The descriptions are a  lot better, but I still couldn't figure out which one.  I loaded the last one and it turned out to be not compatible. I went with the middle selectiion, and it was accepted.  After I rebooted, I got the screen the way it's supposed to be.  The Penn Drive program really saved me because I'm a total newbie.

---

### Post by GUZZLR on 2013-06-18
```
you can even manipulate the settings via command line.
look at
     Code:
man nvidia-settings 

If it says no manual entry then install it

Code:

sudo apt-get install nvidia-settings
```

So this is what I found on the Mint15 App store (thumb nail) and I can't seem to find this app on the Ubuntu App. Store.  I've been to the developers website, and was hopeing to find some code...which I didn't.  
Does any body know how I can get this Nvidia console on an Ubunt install? I prefer this NVidia Console to the command line style in a terminal.
 I have it installed on my Mint15 external drive and it's working great! It'd be really nice to have it on Ubuntu as I prefer Ubuntu over Mint.
Thanks for the help...

[ATTACH=CONFIG]243950[/ATTACH]

---

### Post by 3rdalbum on 2013-06-18
It's called nvidia-settings and it is in Ubuntu Software Center.

---

### Post by deadflowr on 2013-06-18
If you can run it via a command line, then you should have the app as they are one and the same.
In the menu system it would be called nvidia x server settings.

It truly is a gui program, but has command line capabilities for those who prefer it.

If you just type nvidia-settings in the terminal it should open the program interface.(the window)
If it doesn't, some sort of error message would presumably appear.

---

### Post by GUZZLR on 2013-06-18
```
It's called nvidia-settings and it is in Ubuntu Software Center.
```

So this is what I keep getting when I search for this app.?  What am I doing wrong here?

[ATTACH=CONFIG]243952[/ATTACH]

---

### Post by deadflowr on 2013-06-18
What comes up if you type only nvidia in the software center search?

---

### Post by GUZZLR on 2013-06-18
three entries for nvidia drivers, no x.org user panel.  Odd that it works for me with Mint15, but does not work for Ubuntu?

---

### Post by GUZZLR on 2013-06-20
IT WORKS!

[ATTACH=CONFIG]243992[/ATTACH]

So here's what I did, maybe it will help others. I reloaded Ubuntu and basically started all over.  I selected the Recomended Driver in Additional Drivers. let it install, rebooted, and then went back to software/updates and installed the update for the Nvidia driver previously installed, and rebooted once again.  As usual, the normal Plymouth Ubuntu logon splash screen was replaced with a cryptic, ugly looking logon screen.  However, this time the Nvidia control panel was automatically loaded along with all my other applications.
To get the nice Ubuntu log-in screen back, I followed these instructions below, which also works for Mint15 on my other exteranal drive:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

The instructions given by the author above are for an earlier Ubuntu version, so the line item numbers are a little off, however, the line codeing remains the same, so it is easily found. 

Here's what I have:
HP Pavilion, Windows 7 Pro, Nvidia GForce GT 230M card
external drive 1: Ubuntu 13.04, installed Recommended Driver 310.44, and the corresponding update after rebooting
external drive 2: Mint 15, installed Recommended Driver 310.44-Obuntu2, and the corresponding update after rebooting

Another thing I have noticed, is the machine shuts down very quickly and efficiently now at a consistant 13 seconds...startup remains the same at 45 seconds.

After many many failed attempts, I've finailly got my Digital Vibrance back...life is good!

---

