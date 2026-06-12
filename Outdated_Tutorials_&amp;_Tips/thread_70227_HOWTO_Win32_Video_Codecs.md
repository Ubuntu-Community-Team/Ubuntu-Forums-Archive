---
title: "HOWTO: Win32 Video Codecs"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tseliot on 2005-09-29
This HOWTO is aimed at all the users of Ubuntu (both 32 and 64bit although wmv9 files don't work in Ubuntu 64bit) and it is useful because win32 codecs aren't available anymore in the repositories for legal reasons.

This guide is a revised version of a guide of mine specifically aimed at 64bit users. I decided to post this new one in order to avoid misunderstandings.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:

1)You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install &#8220;xine-ui&#8221; and &#8220;totem-xine&#8221; in Synaptic or type in the command line: 
sudo apt-get install xine-ui ; totem-xine

3) Launch Xine (or Totem) and try to play a video (this will create a .config file)

4) Download the codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the &#8220;essential codecs package&#8221;)

if the link above is temporarily down try this mirror:
[http://www4.mplayerhq.hu/homepage/design7/dload.html]("http://www4.mplayerhq.hu/homepage/design7/dload.html")

5) Open the command line(&#8220;Konsole&#8221; if you are using KDE, &#8220;Terminal&#8221; if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is &#8220;essential-20050412.tar.bz2&#8221;:

tar -xjf essential-20050412.tar.bz2 (this will extract the file)

sudo mv essential-20050412/* /usr/lib/win32 (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!


[COLOR="Red"]NOTE: It seems wmv9 don't work with my HOWTO if you use Ubuntu 64bit.[/COLOR] 

Alberto

---

### Post by sal on 2005-09-29
thanks for this.
do you know if there will be HOWTO's for the other thing removed from the repos? such as sun-java and dvd playing?

---

### Post by tseliot on 2005-09-29
[QUOTE=sal]thanks for this.
do you know if there will be HOWTO's for the other thing removed from the repos? such as sun-java and dvd playing?[/QUOTE]
No, I don't. But I might be writing a guide about sun-java almost as soon as I get my hands on Breezy stable (because then I will need to install java again).

---

### Post by sal on 2005-09-29
yes, this is what i expect to have happen. most of the HOWTo's will be writen when breezy go's gold. i wounder how soon untill breezy gets its own sector on the forums? hopefully soon.

---

### Post by bluemist on 2005-09-29
Playing WMV9 didn't work for me in Totem, although it now worked in Mplayer.

Totem may be looking at all the other codecs I installed, anyone know how to configure it?

---

### Post by tseliot on 2005-09-29
[QUOTE=bluemist]Playing WMV9 didn't work for me in Totem, although it now worked in Mplayer.
Totem may be looking at all the other codecs I installed, anyone know how to configure it?[/QUOTE]
1) Did you follow EVERY STEP of my guide?
2) Do you use Ubuntu 32bit?

---

### Post by sinbad782 on 2005-09-29
I didn't know the CSS decryption libraries for commercial DVD playback had been removed. This seems a bit ridiculous given that playing back your DVDs is fair use (at least in my book) and having a library available ensures interoperability. 

In any case, I think [www.videolan.org](www.videolan.org) have a repo that you can add to your source.list which contains this package (libdvdcss2)

---

### Post by ions on 2005-09-29
Nothing plays with xine/totem-xine but mplayer works now thanks to this.

Edit: mplayer seems to choke on audio from some files.

---

### Post by mcduck on 2005-09-30
You could also get win32 codecs with 
'wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb'
..and..
'sudo dpkg -i w32codecs_20050412-0.0_i386.deb'

---

### Post by tseliot on 2005-09-30
[QUOTE=ions]Nothing plays with xine/totem-xine but mplayer works now thanks to this.

Edit: mplayer seems to choke on audio from some files.[/QUOTE]
1) Did you have problems with totem before?
2) If you didn't have problems try to install totem-gstreamer in synaptic (it will uninstall totem-xine)

---

### Post by tseliot on 2005-09-30
I've noticed I can install libdvdcss2 and I suppose it's thanks to this line in my repos:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

Which should be the only repository of backports for now.

---

### Post by ions on 2005-09-30
[QUOTE=tseliot]1) Did you have problems with totem before?
[/QUOTE] 
It's never played video for me.

[QUOTE=tseliot]
2) If you didn't have problems try to install totem-gstreamer in synaptic (it will uninstall totem-xine)[/QUOTE]
I installed totem-gstreamer just to see if it'd make a difference.  None.

---

### Post by tseliot on 2005-09-30
[QUOTE=ions]It's never played video for me.
I installed totem-gstreamer just to see if it'd make a difference.  None.[/QUOTE]
I've never had problems with Xine. I've done a search in this forum and it looks like you're not the only one having problems with xine. (I hope it has been fixed in Breezy)

Open Synaptic and install "vlc-gnome" or "vlc-gtk" and try to play your videos with this program.

Tell me if it works.

---

### Post by Kyral on 2005-09-30
Yanno...this might stop me from doing a clean Breezy install...

Then again, I think I found the only use for that XP Pro disc I have laying around (Yes its legal)

---

### Post by bored2k on 2005-09-30
Howcome? I have a clean Breezy and I have everything running.

---

### Post by tseliot on 2005-09-30
[QUOTE=Kyral]Yanno...this might stop me from doing a clean Breezy install...

Then again, I think I found the only use for that XP Pro disc I have laying around (Yes its legal)[/QUOTE]
Sooner or later you will have to reinstall your OS (I hope to be wrong ;) ) so you should try Breezy.

P.S. I've always used my method to install win32 codecs (and it has always worked for me)

---

### Post by bored2k on 2005-09-30
[QUOTE=tseliot]Sooner or later you will have to reinstall your OS (I hope to be wrong ;) ) so you should try Breezy.

P.S. I've always used my method to install win32 codecs (and it has always worked for me)[/QUOTE]
It's pretty much the same as installing a debian package. And if users are afraid of not knowing about upgrades, I think we'd know from several sources when Divx 6 and above codecs for Linux are made ;).

Off topic: tselio, what anime is that ?

---

### Post by tseliot on 2005-09-30
[QUOTE=bored2k]It's pretty much the same as installing a debian package. And if users are afraid of not knowing about upgrades, I think we'd know from several sources when Divx 6 and above codecs for Linux are made ;).

Off topic: tselio, what anime is that ?[/QUOTE]
It's my favourite (and old) one: Kimagure Orange Road

---

### Post by bored2k on 2005-09-30
[QUOTE=tseliot]It's my favourite (and old) one: Kimagure Orange Road[/QUOTE]
[Kimagure Orange Road]("http://anidb.info/perl-bin/animedb.pl?show=anime&aid=153")

Whoa, quite old :D.

---

### Post by tseliot on 2005-09-30
[QUOTE=bored2k][Kimagure Orange Road]("http://anidb.info/perl-bin/animedb.pl?show=anime&aid=153")

Whoa, quite old :D.[/QUOTE]
Yep, I was a child the first time it was transmitted in Italy (I was born in 1983, and maybe I'm older than you)

---

### Post by bored2k on 2005-09-30
[QUOTE=tseliot]Yep, I was a child the first time it was transmitted in Italy (I was born in 1983, and maybe I'm older than you)[/QUOTE]
Never saw it. When I was small I was probably blinded with mecha anime and military type cartoons. And yes, you're older than me by about two years.

Now, back on topic ^__^

---

### Post by greywolf73 on 2005-10-01
Thanks it work. I just have a few questions. Do you know it does not work with gstreamer? In order to install xine and it components I had to uninstall gstreamer, totem, totem gstreamer, and ubuntu-desktop. Do you why ubuntu desktop was uninstalled and is that a bad thing?

---

### Post by bored2k on 2005-10-01
It is not a bad thing greywolf73. ubuntu-desktop is simply a meta-package and yes, there's no problem with installing totem-xine over gstreamer.

---

### Post by TakisX on 2005-10-05
I followed your how to and xine plays the avi files i have but totem asks for some plugin in order to play .
Any ideas ?

---

### Post by tseliot on 2005-10-05
[QUOTE=TakisX]I followed your how to and xine plays the avi files i have but totem asks for some plugin in order to play .
Any ideas ?[/QUOTE]
1) Did you install totem-xine (open synaptic and make sure you did)?

2) Are you trying to use Totem while using KDE?

---

### Post by bored2k on 2005-10-05
[QUOTE=tseliot]1) Did you install totem-xine (open synaptic and make sure you did)?

2) Are you trying to use Totem while using KDE?[/QUOTE]
2. TakisX, if so, install kaffeine-xine and use that instead of totem.

---

### Post by ubuntumaneh on 2005-10-05
Besides debian marillat, there are non-official repositories out there (there will be no support from Ubuntu people, for what I understood). One I know contains w32codecs is:

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) hoary main

With this, you can use apt-get. But be cautious with this kind of repository.

I may suggest we should try to set a list of non-official repositories and post here. With the proper cautious warnings, of course.

However, this kind of how-to's is great, indeed. I have been installing some ubuntu in many computers these days, ann these how-to's happens to be very handy. Besides that, there is always googling non-official repositories.

As come to sun-java, usually, which the proper changes, i follow or recommend the offical how-to on linux installation:

[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

---

### Post by albertoramirez on 2005-10-05
Worked fine!!!

Thanks a lot:razz:

---

### Post by Vytas on 2005-10-06
If you use Breezy (might work with Hoary, too), and you want totem-gstreamer, you can install those codecs for gstreamer, too (works with minor issues for me).

1. Install codecs into /usr/lib/win32, as mentioned.
2. Install gstreamer0.8-pitfdll.
3. If it doesn't work, or you mixed 1. and 2., run ```
sudo gst-register-0.8
```

---

### Post by tseliot on 2005-10-06
[QUOTE=Vytas]If you use Breezy (might work with Hoary, too), and you want totem-gstreamer, you can install those codecs for gstreamer, too (works with minor issues for me).

1. Install codecs into /usr/lib/win32, as mentioned.
2. Install gstreamer0.8-pitfdll.
3. If it doesn't work, or you mixed 1. and 2., run ```
sudo gst-register-0.8
```[/QUOTE]
Nice addition :)

---

### Post by delaguer on 2005-10-07
> **tseliot]This HOWTO is aimed at all the users of Ubuntu (both 32 and 64bit although wmv9 files don't work in Ubuntu 64bit) and it is useful because win32 codecs aren't available anymore in the repositories for legal reasons.

This guide is a revised version of a guide of mine specifically aimed at 64bit users. I decided to post this new one in order to avoid misunderstandings.

If you want to watch your movies (avi and wmv) or listen to your music files (wma) which require Win32 codecs this is what you need:

1)You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install &#8220 said:**
> http://www.mplayerhq.hu/homepage/design7/dload.html[/url]
(just download the &#8220;essential codecs package&#8221;)

5) Open the command line(&#8220;Konsole&#8221; if you are using KDE, &#8220;Terminal&#8221; if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is &#8220;essential-20050412.tar.bz2&#8221;:

**[color=red]tar -xjf essential-20050412.tar.bz2 (this will extract the file)[/color]**

sudo mv essential-20050412/* /usr/lib/win32 (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!


[COLOR="Red"]NOTE: It seems wmv9 don't work with my HOWTO if you use Ubuntu 64bit.[/COLOR] 

Alberto

thanks for the howto :)

however, i tried this to manual install azureus, but the tar.bz2 just won't extract. 
(don't worry about the java package, i have all that azureus needed)

alf@DeBuntu:~$ sudo tar -xjf azureus_2.3.0.4_linux.motif.tar.bz2
tar: azureus_2.3.0.4_linux.motif.tar.bz2: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

what did i do wrong? any idea? 

i have installed azureus before using apt-get install azureus, but now it just does not work anymore. i don't know why. wish it was as simple as before. :(

---

### Post by tseliot on 2005-10-07
[QUOTE=delaguer]thanks for the howto :)

however, i tried this to manual install azureus, but the tar.bz2 just won't extract. 
(don't worry about the java package, i have all that azureus needed)

alf@DeBuntu:~$ sudo tar -xjf azureus_2.3.0.4_linux.motif.tar.bz2
tar: azureus_2.3.0.4_linux.motif.tar.bz2: Cannot open: No such file or directorytar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

what did i do wrong? any idea? 

i have installed azureus before using apt-get install azureus, but now it just does not work anymore. i don't know why. wish it was as simple as before. :([/QUOTE]
cd directory_in_which_you_put_the_file
ls (a list will appear)
check that the file is in the list
tar -xjf azureus_2.3.0.4_linux.motif.tar.bz2 (there's no need to use sudo)

It worked for me (with the same file)

---

### Post by Heretushi on 2005-10-08
[QUOTE=Vytas]If you use Breezy (might work with Hoary, too), and you want totem-gstreamer, you can install those codecs for gstreamer, too (works with minor issues for me).

1. Install codecs into /usr/lib/win32, as mentioned.
2. Install gstreamer0.8-pitfdll.
3. If it doesn't work, or you mixed 1. and 2., run ```
sudo gst-register-0.8
```[/QUOTE]
I followed the original Howto. Totem didn't read video at all.

I followed this addition. Now Totem will read WMV files. But DivX still shows as audio stream only.

Weird.

---

### Post by tseliot on 2005-10-08
[QUOTE=Heretushi]I followed the original Howto. Totem didn't read video at all.

I followed this addition. Now Totem will read WMV files. But DivX still shows as audio stream only.

Weird.[/QUOTE]
I 've never had your problem and I really don't know how to help you. Sorry :(

---

### Post by delaguer on 2005-10-08
[QUOTE=tseliot]cd directory_in_which_you_put_the_file
ls (a list will appear)
check that the file is in the list
tar -xjf azureus_2.3.0.4_linux.motif.tar.bz2 (there's no need to use sudo)

It worked for me (with the same file)[/QUOTE]

I tried several times with this motif.tar.bz2 files, I can extract it but I always got these error messages when I tried to run azureus. 
Then I tried with GTK.tar.bz2, extracted it, run it and it worked!!! it's a bit weird though because I tried to manual install azureus with GTK files few days ago and it didn't work.  

anyway, thanks for your help. I appreciate it. 
great HowTo! keep up the good work. ;-) 

-al-

---

### Post by Garde on 2005-10-17
Hi, I'm using ubuntu 5.10 (Breezy) and have followed every step in your guide.  I read through everything else, and I tried the gstreamer alternative, and I still have no luck.

However, when I use Nautilus to navigate to my ntfs partitions where my video files are located, something is decoding the video for the thumbnail images.  For some reason, Mplayer, Totem and Xine don't work (with the respective steps followed in order to use each).  I was wondering if anyone had any advice to fix this...

Thanks.

Edit: Okay, my college's LUG helped me out, so now it runs in mplayer through the command line with the command and args: 

mplayer -vo x11 <filename>

Do you guys have any ideas on how to get Totem to play the files?

---

### Post by tseliot on 2005-10-17
[QUOTE=Garde]Hi, I'm using ubuntu 5.10 (Breezy) and have followed every step in your guide.  I read through everything else, and I tried the gstreamer alternative, and I still have no luck.

However, when I use Nautilus to navigate to my ntfs partitions where my video files are located, something is decoding the video for the thumbnail images.  For some reason, Mplayer, Totem and Xine don't work (with the respective steps followed in order to use each).  I was wondering if anyone had any advice to fix this...

Thanks.

Edit: Okay, my college's LUG helped me out, so now it runs in mplayer through the command line with the command and args: 

mplayer -vo x11 <filename>

Do you guys have any ideas on how to get Totem to play the files?[/QUOTE]
Sorry, I have no idea. I've never had your problem.

---

### Post by samjam on 2005-10-17
[QUOTE=tseliot]I've noticed I can install libdvdcss2 and I suppose it's thanks to this line in my repos:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse

Which should be the only repository of backports for now.[/QUOTE]

Well this is how I did it, add this to sources.list
deb-src [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

and then
apt-get -b source libdvdcss
apt-get -b source libdvdcss2
apt-get -b source w32codecs

dpkg -i libdvdcss*deb w32codec*deb

Building from SOURCE from debian repos is safe, unlike madly installing binaries from all over the place.

---

### Post by mallternative on 2005-10-18
[QUOTE=tseliot]
4) Download the codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the “essential codecs package”)



[/QUOTE]

mplayerhq.hu cannot be found at this time from here. darn.

---

### Post by mallternative on 2005-10-18
[QUOTE=mcduck]You could also get win32 codecs with 
'wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb'
..and..
'sudo dpkg -i w32codecs_20050412-0.0_i386.deb'[/QUOTE]
--That worked for me on Hoary- 32-bit.  I haven't tested it extensively. Totem plays an old wmv file I had around, and it wouldn't do it before I did that. and it also plays divx files fine. I think at this point I am using totem-xine and xine is installed.

---

### Post by tseliot on 2005-10-18
[QUOTE=mallternative]mplayerhq.hu cannot be found at this time from here. darn.[/QUOTE]
try here:
[http://www4.mplayerhq.hu/homepage/design7/dload.html]("http://www4.mplayerhq.hu/homepage/design7/dload.html")

---

### Post by elapointe on 2006-02-21
I have problem with WMV !

There are many stripe and doubled video (horizontaly) 

The video seam badly decoded !

Mpeg work file !

---

### Post by tseliot on 2006-04-19
[QUOTE=elapointe]I have problem with WMV !

There are many stripe and doubled video (horizontaly) 

The video seam badly decoded !

Mpeg work file ![/QUOTE]
try with Mplayer

---

### Post by AlexanderDGreat on 2010-02-02
Hi, tseliot your links don't work. I'm using JJ 32bit. Can you update on this? Thanks.

---

### Post by mc4man on 2010-02-02
You've pretty much got all the same codecs when you installed w32codecs.

 There are a few additional obscure ones available, 2 of which can't run in 9.10+ 
( out of those 2 ffmpeg handles one, the other is for some older real video I believe. Installing libstdc++5 from jaunty will enable if need be

Anyway the full page for curiosities sake 
[http://www1.mplayerhq.hu/MPlayer/releases/codecs/](http://www1.mplayerhq.hu/MPlayer/releases/codecs/)


(by the way it's libdvdread4 and libdvdnav4 - libdvdcss2 itself  hasn't changed in quite some time, only the medibuntu version #'s

---

### Post by andrew.46 on 2010-02-03
Hi mc4man,

> **mc4man said:**
> There are a few additional obscure ones available [...]

My favourite obscure codec is lagarith:

[http://ubuntuforums.org/showpost.php?p=8081511&postcount=10](http://ubuntuforums.org/showpost.php?p=8081511&postcount=10)

for which I have only ever encountered a single sample :).

Andrew

---

