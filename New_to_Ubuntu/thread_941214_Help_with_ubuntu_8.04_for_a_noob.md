---
title: "Help with ubuntu 8.04 for a noob"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by b3n0 on 2008-10-07
Hey all,

I've been an on off Ubuntu user for about a year, never getting to deep into it. Yesterday I decided to take the plunge and install Ubuntu as the only OS on my laptop.
I finished the install and set up and I'm at the stage where I'm just trying to make it comfortable, familiar and practical. I'm having having a few problems, and if anyone can help with with any one of these I will be very thankful. Please be patient with me as I have yet to learn all the terms you all understand.  

1.     Ubuntu cant seem to detect the laptops built in mic. I use skype... alot. It unusual that hardy auto detected the laptops hot keys and auto configure the remote but has yet to find the mic. I have tested the front jacks they are working but really quite. Any Ideas? Are there volume levels built into ubuntu like in windows?

2.     Screen resolution. Ok you must be sick of these questions by now but I assure you, I have searched and googled. This one has particularly annoyed me mainly because I have spent the most time on it. The screen display is currently at 1280x800 but i know it can do 1440x900. How do i change it?

3.     This is the last one for now. I'm trying to install the World of Warcraft. I have read through many different guides, and I seem to get confused with how many different ways there are to do it. I have ended up following this guide [http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html]("http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html").
I'm stuck at the "Once you have them all copied from copied, run the installer' step". When I copied the dvds they came out as unknown files. Any ideas?

Thanks heaps

---

### Post by JoshuaRL on 2008-10-07
Good to hear this b3n0.  It's a headache at first but its nice once you get used to it as your only OS.  It really makes you learn when you can't just boot back into something else.

1).  Make sure you get alsamixer from the repos and see if the mic is set low or off.

2).  Do this to look at your settings without changing them:
```

displayconfig-gtk

```
And to change anything, use the temporary root privilidges for graphical apps:
```

gksu displayconfig-gtk

```

3).  Not sure about WoW, but I'm sure many here could help you.

---

### Post by b3n0 on 2008-10-08
> **JoshuaRL said:**
> Make sure you get alsamixer from the repos and see if the mic is set low or off
Sorry, 'repos'? Is that slang for the add/remove programs tab?
Thanks for your help. :)

---

### Post by bumanie on 2008-10-08
repo's are short for repositories. A repository is where all the ubuntu supported software is able to be downloaded from. There are various servers around the world that hold the programs. To get the best out of ubuntu go to System --> Administration --> software sources and check the first 4 boxes. Next open third party software an check things that are mentioned there. You will then find that downloading the majority of software will work and any updates that come through, will be sent to you. To choose a server near you, on the first screen, go to the download from box - click on the drop box, choose 'other'. A scan will occur that will choose the best mirror for you to connect to.

---

### Post by robert shearer on 2008-10-08
> **b3n0 said:**
> Sorry, 'repos'? Is that slang for the add/remove programs tab?
Thanks for your help. :)

System=>Administration=>Synaptic Package Manager.

When it opens use the search function and type in the package you want (alsamixer). 
When you find it highlight it and right click for a menu.

---

### Post by eternalnewbee on 2008-10-08
For screen resolution:
Go to main menu > system > preferences > screen resolution and make the desired changes

---

### Post by eternalnewbee on 2008-10-08
For screen resolution:
Go to main menu > system > preferences > screen resolution and make the desired changes

---

### Post by anewguy on 2008-10-08
System preferences screen resolution does not solve the problem for a very large number of new user of Linux.  The problem lies in configuring the modes for resolution and clock speed in /etc/X11/xorg.conf.  This is where the vast majority of new users must make the changes.  Looking at /var/log/Xorg.0.log can be very informative, as it tells you the driver and options it is using as well as things like max resolutions support versus those it is defaulting to.

Dave :)

---

### Post by tarps87 on 2008-10-08
For WoW I would suggest doing:```
sudo apt-get remove wine
```This will remove wine and then:```
sudo apt-get install wine
``` this will install the latest version of wine from the Ubuntu repositories. Now download wine-doors from: [http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)
(The Debian/Ubuntu DEB version) Now run this and use it to install driectx. Now you should be able to double click the install.exe. This worked for me when I install the free trial version.

---

### Post by b3n0 on 2008-10-08
Hey all, thanks for your replies.... and so fast! Well we can cross number one of the list. Alsamixer works great! I'm now skyping like a pro. I'm now working on what tarps87 suggested; uninstalling and reinstalling wine. 

In regards to WOW, can anybody tell me if [this is an ok guide ]("http://www.linuxforums.org/forum/wine/62932-howto-installing-world-warcraft-wine.html"). It is what I have been trying to follow. The guide asks me to copy the disks then install the newly created .exe's under wine in the terminal. I've copied the disks, but the files are unknown files. I've tried renaming them to .exe but it doesn't work. Any ideas? Could it but due to the fact that my copy of the game came on dvd and not cd rom?
[IMG]http://fc46.deviantart.com/fs37/f/2008/282/7/5/Screeny104_by_B3N0.png[/IMG]
[Full size]("http://fc52.deviantart.com/fs36/f/2008/282/7/0/Screeny101_by_B3N0.png")
thanks once again

---

### Post by b3n0 on 2008-10-08
> Now run this and use it to install driectx. Now you should be able to double click the install.exe. This worked for me when I install the free trial version.
I just download directx, like I would on windows; googled then downloaded the .exe (note I couldn't get it from the microsoft site i need to do a validation check). The file I found came from [here]("http://www.filehippo.com/download_directx/"). Its asking where to extract the files to. Would it be 'system32' the fake folder wine created?

By the way guys milestone today. I installed my first program in the terminal today without a guide. :D I'm slowly catching on.

---

### Post by JoshuaRL on 2008-10-08
> **b3n0 said:**
> I just download directx, like I would on windows; googled then downloaded the .exe (note I couldn't get it from the microsoft site i need to do a validation check). The file I found came from [here]("http://www.filehippo.com/download_directx/"). Its asking where to extract the files to. Would it be 'system32' the fake folder wine created?

By the way guys milestone today. I installed my first program in the terminal today without a guide. :D I'm slowly catching on.

Cool man.  If you're trying to extract an archive of some sort, it shouldn't matter where you extract it too.  But if you're trying to run that DirectX installer in Wine, just right click it and open with Wine.  It should install correctly for you.

---

### Post by b3n0 on 2008-10-09
> **JoshuaRL said:**
> Cool man.  If you're trying to extract an archive of some sort, it shouldn't matter where you extract it too.  But if you're trying to run that DirectX installer in Wine, just right click it and open with Wine.  It should install correctly for you.
When I open the direct x .exe it is filled with hundreds of .dll's and other system files. I thought they may have to go somewhere specific.

---

### Post by tarps87 on 2008-10-09
If wine-doors installed correctly it should be under applications->wine->wine-doors or type ```
wine-doors
``` in the terminal, this will bring up a list of programs, direct x should be on there.
also try ```
wine -version
``` this will this your version of wine that is installed.
You may need to do```
sudo umount /media/cdrom0
sudo mount -t udf -o ro,unhide /dev/cdrom /media/cdrom0

``` When I installed wow it was from the download, try the commands above and then clicking the install.exe on the cd

Screen shoot of wind-doors main menu, direct x should be in the list:
[IMG]http://www.wine-doors.org/screens/ss-winedoors-1.png[/IMG]

Edit: You can also try installing WoW without direct x as this may guide you through it.

---

### Post by b3n0 on 2008-10-26
Hey all,
Sorry to drag this one from the dead, I want to thanks all of you for you help. On the 26 OCT at 2330 (late last night GMT +10)I finally finished installing WOW I sat down removed all distractions and gave it a solid 3 hours of my attention. I followed the tut that I mentioned earlier, but this time it seemed to make more sence.

So thanks all... Ticks in all 3 boxes now!
Just 2 quick questions.
1. While useing skype my mates complain about alot of white noise. Any ideas? the headset I use is brand new and when I use it on windows its fine.
2. I'd love to make a shortcut to the WOW launcher.ex in my wine folder. I tried copy pasting, no joy. I also tried making a launcher. I may have somthing to do with the fact that the .wine/:c folder is hidden? Well thanks again for your help.

---

