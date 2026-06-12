---
title: "I'm new -- what to use instead of a few XP applications"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by DavidVS on 2008-09-25
Thank you for any help!
[COLOR="DarkRed"]**Edit: Thanks again for several prompt replies.  My results based upon your help are in red-bold.**[/COLOR]

What do I use in Ubuntu instead of the following applications I am used to using in XP?  (After eight years I finally got a new computer, this time a laptop with Ubuntu 8.10, even though I am new to Linux.)

1. E-mail Notification: I used Gmail, but the official Gmail Notifier needs XP
[COLOR="DarkRed"]**     The application cgmail is great.  How do I get it to automatically load at startup?**[/COLOR]

2. HTML Editor: I used PSPad, which is really nice with colors and pair-identification to help with HTML
[COLOR="DarkRed"]**Bluefish Editor seems to be exactly what I am looking for.  (Gedit is too simple without any addons.)**[/COLOR]

3. Internet Safety: I used ZoneAlarm for a firewall and Norton (uhg) for virus detection
**[COLOR="DarkRed"]There is a Firefox addon named "Ubuntu Firefox Modifications" which folk say is sufficient.  Since I use Gmail instead of having e-mail in local software I'm not worried about e-mail viruses.[/COLOR]**

4. Photo Organization and Minor Touch-Ups: I used Picasa
[COLOR="DarkRed"][B]DigiKam has troubles uploading to Pacasaweb, and F-Spot wants to rearrange my directory structure.  So I'm using gThumb to weed out bad photos and then the Linux version of Picasa.
[http://picasa.google.com/linux/download.html](http://picasa.google.com/linux/download.html)[/B][/COLOR]

5. Music: I have an iPod Shuffle, so unfortunately was using iTunes to be able to sync
[COLOR="DarkRed"]**Banshee won't play AAC for me.  Rhythmbox is decent, Amarok might take getting used to.**[/COLOR]

6. Palm: Can I still use my Palm Tungsten E2 PDA?
[COLOR="DarkRed"]**Help!  My Tungsten E2 seems invisible to gnome-pilot.**[/COLOR]

7. Video: I have a Flip Ultra and upload family videos to Blip.tv, so all I need with video is software to translate videos to a smaller sized format, and crop sections from a file
[COLOR="DarkRed"]**Avidemux is great.**[/COLOR]

8. E-Sword: It does not seem to like wine.
[COLOR="DarkRed"]**A simple installer for e-Sword is here: [http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)**[/COLOR]

[COLOR="Sienna"]**Edit: the Update Manager says I have 359 updates available.  Are these all safe to install?**[/COLOR]

Thank you again!
 David V.S.

---

### Post by crazypenguin2008 on 2008-09-25
welcome david!!  

there is just as good programs in linux that will suit the needs you have. 

picasa will work on ubuntu i do belive.

you can get a gmail notifier in aplications>add/remove. 

i cant rember the exact name of the app but its in internet section of add/remove.

you can run itunes thru wine. 


no need to worry about the virus scanner but if you insist you can get avast! i have avast! free on my thinkpad but its not a necisity.


ubuntu has the apps to palm. my palm centro syncs with ubuntu easily. 

and the website for wine is [www.wine.org](www.wine.org) i do belive 


good luck and im sure other can add more than me.

---

### Post by lisati on 2008-09-25
Have a look [here]("https://help.ubuntu.com/community/WindowsApplicationsEquivalents?highlight=%28equivalents%29%7C%28linux%29")

---

### Post by Diabolis on 2008-09-25
For your ipod: Amarok plus [Last Client]("http://code.google.com/p/lastagent/") which is used to access your lastfm profile if you have one.

---

### Post by paultag on 2008-09-25
1. E-mail Notification: I used Gmail, but the official Gmail Notifier needs XP

--> gmail-notify ( sudo apt-get install gmail-notify )

2. HTML Editor: I used PSPad, which is really nice with colors and pair-identification to help with HTML

--> gedit ( Text Editor under Applications -> Accessories )

3. Internet Safety: I used ZoneAlarm for a firewall and Norton (uhg) for virus detection

--> Firefox Plugins is the most you need, The community patches security issues as they come along, no need for 3ed party apps here.

4. Photo Organization and Minor Touch-Ups: I used Picasa

--> F-Stop ( Applications -> Graphics )

5. Music: I have an iPod Shuffle, so unfortunately was using iTunes to be able to sync

--> amarok ( sudo apt-get install amarok )

6. Palm: Can I still use my Palm Tungsten E2 PDA?

--> works by default :)

---

### Post by vikramaditya on 2008-09-25
Bluefish is a great HTML editor.  You can install it from terminal:
```
sudo apt-get install bluefish
```

If it isn't what you had in mind, just,
```
sudo apt-get remove bluefish
```

---

### Post by Primefalcon on 2008-09-25
1. E-mail Notification: I used Gmail, but the official Gmail Notifier needs XP
cGMAIL

2. HTML Editor: I used PSPad, which is really nice with colors and pair-identification to help with HTML
Quanta plus or if your advanced vi

3. Internet Safety: I used ZoneAlarm for a firewall and Norton (uhg) for virus detection
not really needed 

4. Photo Organization and Minor Touch-Ups: I used Picasa
f-spot

5. Music: I have an iPod Shuffle, so unfortunately was using iTunes to be able to sync
rythmbox

6. Palm: Can I still use my Palm Tungsten E2 PDA?
gnome pilot

---

### Post by oldsoundguy on 2008-09-25
here is a list that may help:
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

Note that it is not completely up to date, but it can get you into the ballpark!

---

### Post by nowshining on 2008-09-25
for the pda i suggest jpilot...

---

### Post by DavidVS on 2008-09-26
Thank you for many prompt replies.  I've edited my original post to share what has worked for me so far.

---

### Post by Sycron on 2008-09-26
:) well if you are a new user, I can bet that linux is NOT hard for someone that used linux at least 5mins.

---

### Post by billgoldberg on 2008-09-26
7. Add the medibuntu repo to ubuntu (google it).

Install ffmpeg:

```
sudo apt-get install ffmpeg
```

Then go to google and search for winff. 

Download the .deb package from their website and double click to install it.

Winff is a easy video converter and works very well.

For cropping and such, I suggest you try one of the linux video editors. (do this before converting the video file !!!!!).

Open Movie Editor I believe can do this and is extremely easy to use (but almost has no features). Google for more video editors should you need another.

*[COLOR="Sienna"]**Edit: As a second final question, the Update Manager says I have 359 updates available.  Are these all safe to install?**[/COLOR]*

Yes.

---

### Post by I Use Dial on 2008-09-26
Try CheckGmail.  I like the look and functionality more than Gmail-Notifier and it doesn't require Firefox to be open.

I don't see anyone here discussing it yet, but Zonealarm and other security software you used in XP are not necessary for Linux.  Ubuntu installs with all ports closed by default.  Spyware, viruses, malware, trojans, etc., to date have not been written for Linux.  You can bet that Microsoft will happily promote the first occurence of this, so you'll get good warning when the day comes that you need to install something of this nature.  The only security concern currently present in Ubuntu is to be sure and install updates as they are made available.

I have not found an easy to use video editor for Linux.  Some say Cinelerra is easy to use, but I didn't find that to be the case.  The only one I have been able to use with any success is Kino, but it is a major pain in the but.  I edit TV recordings that come to me in mpeg-2, so the software has to convert the file to dv.  Then I have to crop the file and export back to the format I want.  Takes about an hour to do this, although I don't have to sit at the computer the entire time.

All of the updates listed in Update Manager are completely safe.  The repositories those packages come from are updated by the Ubuntu team and are very trustworthy.  In fact, it is more dangerous not to update than it is to update them.  The only thing that becomes unsafe is when you are adding someone else's repository.

---

### Post by DavidVS on 2008-09-28
It appears that the winff downloads are here:
 [http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)

There are two .deb files, one for i386 and one for amd64.  Is an Intel Pentium processor pair (Dual CPU T2370) the i386 version?

Thanks,
 David V.S.

---

### Post by DavidVS on 2008-09-29
I still cannot get my Tungsten E2 to work with gnome-pilot.  (I can sink with j-Pilot but its month calendar view is inferior.)

Google searching shows me I am not the only Tungsten E2 owner who has had problems with gnome-pilot initially seeing the PDA after choosing "Yes I've used sync software before..." during the initial setup routine.

I found some help on this web page:
 [http://osdir.com/ml/gnome.apps.pilot/2006-01/msg00006.html](http://osdir.com/ml/gnome.apps.pilot/2006-01/msg00006.html)

I tried adjusting all of the gnome-pilot settings in that setup routine, to no avail.  (Does the "timeout" still have the bug I read about so that setting it to 100 might help?)

I did manage to find a file manager and inspect the text file
  /usr/share/gnome-pilot/devices.xml
but it does claim to know about the Tungsten E2 already.  Nothing to fix there.

What else can I try?  The other suggestions on that web page are beyond me at my current new-to-Ubuntu state!

Similarly, gnome-pilot help tells me:
   "You will need to make sure that your user account has read, write,
    and execute permissions on this device... Some devices such as
    /dev/ttyUSB1 only exist while the PDA is attempting to sync.
    In such cases, you will need to configure permissions using the
    udev system."
which is also meaningless to me!

More detailed help, please!

Thank you,
 David V.S.

---

