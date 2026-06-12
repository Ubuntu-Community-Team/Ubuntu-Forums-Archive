---
title: "How do I burn music onto a DVD (Ubuntu 12.01)?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by zzllxxllzz on 2013-03-09
Hello, 

I'm struggling with making a simple audio DVD.

I've tried Amarok, Brasero, and K3b.

My problem with Amarok: no option to burn onto a CD/DVD

My problem with Brasero: it does not recognize mp3 files

My problem with K3b: it will not recognize my blank dvd


I just want to make an audio DVD and I would appreciate any help.
 I am open to use whatever program you think is best. 
I know enough to cut and paste things into the terminal...but not much else.

---

### Post by zzllxxllzz on 2013-03-09
ps. I know that this issue isn't new...I've found a lot of posts regarding amarok, k3b and brasero and what to do in this situation... my main problem is that I have trouble understanding the lingo pertaining to using the command prompt...etc...

I'd appreciate any help!

---

### Post by rocketfish201 on 2013-03-09
Brasero uses the Gstreamer plugin for audio. If you don't have the mp3 plugin installed, you can install the Ubuntu restricted extras.```


sudo apt-get install ubuntu-restricted-extras 
```

---

### Post by zzllxxllzz on 2013-03-11
Hi rocketfish,

Thanks for the code, it installed 23 new things and I'm sure they will all be useful.

I am able to access all audio file types now, but I still can't burn onto a DVD. 

Brasero encounters an error while burning, Amarok still doesn't give me the option to burn, and K3b won't recognize my DVD.

Just to make it easier, I'll focus on getting help for one program instead of all 3. So...how about K3b?

Here's a screenshot of me trying to burn a DVD with K3b: [http://i1295.photobucket.com/albums/b626/zzllxxllzz/Screenshotfrom2013-03-10214059_zps6dc91fa2.png](http://i1295.photobucket.com/albums/b626/zzllxxllzz/Screenshotfrom2013-03-10214059_zps6dc91fa2.png)  

...K3b recognizes that there's a DVD in there, but it won't give me the option to burn onto it.

I know the ultimate solution would be to just use a damn CD, but I have a stack of DVDs that I'd like to get rid of...and I''ve been using them for years to burn music onto (via windows)

---

### Post by Jerry N on 2013-03-11
It appears that normal CD/DVD writing software does not create audio DVDs.  Are you sure your player is compatible with audio DVDs?
Check [http://dvd-audio.sourceforge.net/]("http://dvd-audio.sourceforge.net/") for possible solutions for you problem.


Jerry

---

### Post by JLUbunt on 2013-06-03
Hello I was trying to burn a CD and looking to see if there was an answer.  I am not sure if I should start a new thread or ad dto this one.  If the former let me know.
using Rythmbox which gave the option to burn a playlist and took me to Brasero. I am using Ubuntu 12,04 LTS. Idealy I'd like to copy MP3s from my hard disk on to a CD so I can play them in the car.  It does not accept USBs. 
Ubuntu does not seem to know there is a CD/DVD drive unless there is a formatted disk in it. If I put an unformatted disk in it is not seen so I can't do anything with it. 
I tried to fool it by putting a music foratted disk in which it found. When I took it out the drive disappeard from the file manager. 
Do you know how to tell Ubuntu that there is a CD/DVD Drive (mount). then tell it to format it. I think for MP3s it has to be a data disk. 
Hopefully then Brasero will know it is there and let me burn to is. 
Hope this makes sense, and might  al least identify the issue.  
Thanks

---

### Post by speartip on 2013-06-03
2 things to think about.

1. If you're trying to burn mp3s to a dvd, you do not want to be "creating an audio cd". to burn mp3s you need to be creating a "data DVD", where you can add folders or files. I have just tried it with Brasero & it works fine. The "audio cd" option is for creating a bog standard cd that can play on anything.

2. Go into k3b & check what programs/plugins are installed & see whats missing, then install them from synaptic/software centre. The only one I leave unticked is "Normalisation".

Hope this helps.

---

### Post by JLUbunt on 2013-06-05
Hi Speartip Thanks for you reply.  I agree that I need to create a data CD / DVD. I have not been able to find out how to create/format a CD or DVD to make it a data CD/DVD.  Did you do this in Brasero? My system does not seem to know there is a CD/DVD device if there is not a fromatted CD or DVD in the drive.  When I put a formatted CD/DVD in the drive it finde the drive. When I take it out and put a blank CD/DVD in it does not find the drive.  So I've not found how I can format one.  I am sure I am missing something simple.  I attach a couple of screen dumps showing the drive the not showing it. 
Once I can format the CD DVD I can experiment a bit.  I also downloaded Kb3.  When start it it give the message. "No CD/DVD/BD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features such as audio track extraction, audio transcoding or ISO9660 image creation."

---

### Post by JLUbunt on 2013-06-05
I have just read the error message better and thought probably my device can't write!!  I would have made the wrong assumption it could.  I'll se if I can find a device that I know can write.  I imagine your device can write. Does it show up in in the home folder when ther is a blank cd in it?

---

### Post by mastablasta on 2013-06-05
when you burn you choose the blank CD which is then formatted and data is burned on it. this could not be easier to do than with brasero: [http://www.linux.com/news/software/applications/280100-using-brasero-for-data-backup-and-iso-burning](http://www.linux.com/news/software/applications/280100-using-brasero-for-data-backup-and-iso-burning)

> Here are the steps:

[LIST=1]
[*]Insert a blank CD or DVD.
[*]Click the Data Project button.
[*]Add files to your project.
[*]Click the Burn button.
[/LIST]

why should a non formated disk show in the file manager? it doesn't have any files and it doens't have any file format.

---

### Post by JLUbunt on 2013-06-15
Hi I confirmed that the reason I could not burn CDs/DVDs was that my DVDplayer could not burn. Nothing to do with the software.  I'm a bit embarassed to make such an obvious mistake.  I don't want to invalidate the warranty so have plugged in a usb dvd burner in. It all loked good till I received an error message "error while burning. You do not have the required permission to  use this device"  Not sure wht to do next.

Any advice would be appreciated. Thanks.

---

### Post by JLUbunt on 2013-06-17
Hi I confirmed that the reason I could not burn CDs/DVDs was that my DVDplayer could not burn. Nothing to do with the software.&nbsp; I'm a bit embarassed to make such an obvious mistake.&nbsp; I don't want to invalidate the warranty so have plugged in a usb dvd burner in. It all loked good till I received an error message "error while burning. You do not have the required permission to&nbsp; use this device"&nbsp; Not sure wht to do next.<br><br>Any advice would be appreciated. Thanks. <br>&nbsp;

---

