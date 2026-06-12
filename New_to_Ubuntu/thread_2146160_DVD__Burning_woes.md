---
title: "DVD  Burning woes"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by briar rabbit on 2013-05-17
Hello

I have Lucid Linux 10.04, it has taken quite some time to make it a happy machine.

I recently bought a DVD Burner for this well loved machine.

I went to burn a video to the newly acquired DVD Burner and sadly it will not burn videos.

The reasons the machine give me are:
Please install the following manually and try again:
mplex (GStreamer plugin)
vcdimager (application).

My research show that "mplex" is not freeware.

I did the 'apt-get update' as told and that did not nhelp either. It did give the following error:
The following file is required: 
/usr/lib/gstreamer-0.10/libgstmplex.so
Do you want to search for this now?

When I do this it replies:
 E: The cache directory is empty. You need to run 'apt-file update' first.

But that is a closed loop.


help

---

### Post by Kopkins on 2013-05-17
Gstreamer is opensource. Which is what is sounds like you need. 

Try:
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
```

What application are you using to try to burn a DVD?

Kopkins

---

### Post by briar rabbit on 2013-05-17
Thanks Kopkins,

I am using Brasero Disk Burner.  

going to download the gstreamer as you suggested and get right back.

---

### Post by briar rabbit on 2013-05-17
Well that was quick, I did not even have to try burning again:

ferg@ferg-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
[sudo] password for ferg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 52 not upgraded.
ferg@ferg-laptop:~$ 

Any other ideas are most welcome Kopkins.

---

### Post by Kopkins on 2013-05-17
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad-multiverse libavcodec-unstripped-52 dvdauthor
```

[https://answers.launchpad.net/ubuntu/+source/brasero/+question/112041](https://answers.launchpad.net/ubuntu/+source/brasero/+question/112041)

---

### Post by briar rabbit on 2013-05-17
Kopkins,

I did both of the sudo apt get you mentioned. the brasereo does not work nor does the K3b I found (do not remember getting it).

But WOW  something turned out right because I can burn (or copy) the videos with 'CD/DVD Creator'.  

I have 'copied' several videos onto disk and some of them can be read on my other PC and some not ???  I will put the gstreamer on it as well and see if that makes a difference.

Thanks again for the support.

---

### Post by briar rabbit on 2013-05-17
I would gladly mark this thread "solved" if only i could

---

### Post by Kopkins on 2013-05-17
If you go back and edit your first post, then go into advanced editor, you can change the prefix to [SOLVED] .

Glad to hear everything is working!

---

### Post by speartip on 2013-05-18
I know you have sort of solved your problem, but for future reference, the 1st thing I do on a fresh install is install the ubuntu-restricted-extras package, then open up Brasero, go to edit/plugins & make sure all the programs listed are installed (ie the box is ticked), if not use synaptic to locate & install the missing packages. (EXCEPT Normalisation - I always untick that box)
 After that you should have no problem burning CDs/DVDs.

---

### Post by Kopkins on 2013-05-18
I forgot about restricted extras. I always sort of assume that's installed. I believe there is a bug with normalization that takes a VERY long time to actually start doing anything.

---

### Post by briar rabbit on 2013-05-18
Hello speartip  thanks for the input

I went into Brasero properties and 'cdrecord' is not checked, neither is 'mkisofs' or 'readcd'.  However everything is greyed out except - 'file checksum', 'file downloader' and 'image checksum'.  The rest that are greyed out either do not show up in synaptic or are listed as installed.

While I have some help, here is another issue that may be related, that surfaced last night.
 1- the  multi DVD 'burner
will NOT play store bought DVD's BUT will play the videos recorded with it (fine) or other DVD videos recorded years earlier on an other OS (though these play skippy).

2- the older DVD Player
The new copied videos from the multi DVD will not play on old player but the older recorded DVD's will play (poorly - skippy)  and the store bought DVD play fine.

I'm using VLC, SMPlayer or Movie Player  all same

The DVD appearing on the desktop shows the title of the DVD, why wont it play

Yes I have 2 laptops, one has the newly bought Multi DVD the other a regular DVD player.

I don't want to wear out my welcome with too many issues but at that risk any help is appreciated.

---

### Post by Kopkins on 2013-05-19
Have you installed libdvdcss? 

```
 sudo /usr/share/doc/libdvdread4/install-css.sh 
```

```
 sudo apt-get install ubuntu-restricted-extras 
#If you havent already
```****The real DVD's are encrypted and you need the libdvdcss to play them. I'm not sure about your dvd's though..

Kopkins

---

### Post by jamesisin on 2013-05-19
Here is my guide for building a new machine.  It contains some very important and useful links.

[http://jamesisin.com/a_high-tech_blech/index.php/2013/03/built-a-new-ubuntu-machine/](http://jamesisin.com/a_high-tech_blech/index.php/2013/03/built-a-new-ubuntu-machine/)

---

### Post by briar rabbit on 2013-05-20
Hey Kopkins, I just checked the synaptic package manager and both the  "libdvdcss2" and "ubuntu-restricted-extras 39" are installed.

I went to 'Built a New Ubuntu Machine' and will study on it. Thanks Jameisin. 

It is raining outside right now so nothing can be done on the car.

---

### Post by Kopkins on 2013-05-20
libdvdcss isn't installed via package manager. You have to do it manually by running the command I provided. Or else encrypted DVD's will not play.

---

### Post by jamesisin on 2013-05-20
I have libdvdcss2 and it looks like I'm getting it through the mediabuntu repository.

For those interested, my article linked above includes a link to a multimedia howto which runs through all of these procedures quite handily.

---

### Post by briar rabbit on 2013-05-22
Thanks again for the support.  I was out of town yesterday AM untill now.  

Kopkins, I ran the first 2 commands you suggested and the "libdvdcss2" and "ubuntu-restricted-extras 39" do show in package manager - so now I am a little confused.
I do know I got some 'restricted extras' a while back when I first got this laptop and it made the DVD's play then.

I have 'ubuntu freak' bookmarked and will start on it tomorrow,  I am just not ready to starting something new tonight.


what will happen if I run "sudo apt-get install ubuntu-restricted-extras" when I already have it?

thanks

---

### Post by briar rabbit on 2013-05-23
--------------------------  Did this;
ferg@ferg-laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2013-05-23 08:13:35--  [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8008 (7.8K) [application/octet-stream]
Saving to: `/tmp/dvdcss-EyxsPN/Packages'

100%[======================================>] 8,008       --.-K/s   in 0.1s    

2013-05-23 08:13:36 (56.8 KB/s) - `/tmp/dvdcss-EyxsPN/Packages' saved [8008/8008]

--2013-05-23 08:13:36--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.127.22
Connecting to packages.medibuntu.org|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39684 (39K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-EyxsPN/libdvdcss.deb'

100%[======================================>] 39,684       119K/s   in 0.3s    

2013-05-23 08:13:37 (119 KB/s) - `/tmp/dvdcss-EyxsPN/libdvdcss.deb' saved [39684/39684]

(Reading database ... 280953 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.12-0.0medibuntu1 (using .../dvdcss-EyxsPN/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ferg@ferg-laptop:~$ 

----------------------------------------- and this;
ferg@ferg-laptop:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo sed -i "/^# deb .*partner/ s/^# //" /etc/apt/sources.list && sudo apt-get --quiet update && sudo apt-get -y --force-yes --quiet --allow-unauthenticated install medibuntu-keyring app-install-data-medibuntu apport-hooks-medibuntu && sudo apt-get update
[sudo] password for ferg: 
--2013-05-23 08:09:11--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 88.191.127.22
Connecting to [www.medibuntu.org|88.191.127.22|:80](www.medibuntu.org|88.191.127.22|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-05-23 08:09:12 ERROR 404: Not Found.

did a restart and tried a store bought DVD - still gives me an error 'can not read from resource'

---

### Post by jamesisin on 2013-05-25
If you attempt to install a package you already have installed apt-get will check to see if you have the latest version and report as such.

---

### Post by gordintoronto on 2013-05-25
For burning videos, devede can make the result look a lot more professional. Spend 20 minutes browsing the *excellent* help files before you try to use the program. It creates an iso, then you burn it with K3B or Brasero.

---

### Post by briar rabbit on 2013-05-27
Thanks for the info jamesisin.

I do not have the 'devede' so I will try it, thanks gordontoronto.

---

### Post by briar rabbit on 2013-05-30
I had some time today and went back to my DVD burning woes.  And all good now with DeVeDe.  
Just like in; "http://ubuntuforums.org/showthread.php?t=1666226&page=2&highlight=devede"
my Brasero is now working properly too.
I want to thank everyone for their help and support.  This is a great place to get help for use non-techies on a great OS.
Thanks

---

### Post by UT_Libertarian on 2013-08-12
Having a similar problem.  First tried:
"sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update" as one long string of text in terminal, and when that didn't end well, intended to try:
"sudo apt-get install ubuntu-restricted-extras" followed by:
"sudo /usr/share/doc/libdvdread4/install-css.sh".  
The first command line displayed a license agreement about using the library at the end with <Ok> in the terminal. Unable to proceed, I ended up closing the terminal window, opening another, and tried to start over, but now get the following:
"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

At a loss as to how to proceed.

[UPDATE] Found my answer.  It's working now.

---

### Post by jamesisin on 2013-09-15
You should post your solution back into the thread for the benefit of others.

---

