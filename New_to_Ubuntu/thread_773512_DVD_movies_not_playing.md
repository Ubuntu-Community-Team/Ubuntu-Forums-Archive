---
title: "DVD movies not playing"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by gigaferz on 2008-04-28
the system is fully updated
 

Linux ricardo-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

VLC output > 


vricardo@ricardo-desktop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: DVD-VIDEO
libdvdnav: DVD Serial Number: 47828FDF00007530
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ricardo/.dvdnav/DVD-VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: *** pgci_ut handle is NULL ***
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86


Totem output:
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


I need help please!
I have all the gstreamer plugins and restricted extras


Thank you.

---

### Post by mc4man on 2008-04-28
> libdvdread: Encrypted DVD support unavailable.
For starters you need libdvdcss2
either enable medibuntu in sources (what ver. of ubuntu are you using )
or get it here - 2nd one down
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

---

### Post by gigaferz on 2008-04-28
> 
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: THE_MATRIX_REVOLUTIONS_D1
libdvdnav: DVD Serial Number: 304258D2
libdvdnav: DVD Title (Alternative): THE_MATRIX_REVOLUTIONS_D1
libdvdnav: Unable to find map file '/home/ricardo/.dvdnav/THE_MATRIX_REVOLUTIONS_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

My other pc is working fine

Thanks for the reply but it didnt work either I am using the newest ubuntu Hardy Heron

I tried ogle too but no luck either
> ricardo@ricardo-desktop:~$ ogle
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
SNDCTL_DSP_GETCHANNELMASK: Invalid argument
xscreensaver-command not found.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  54
  Current serial number in output stream:  54
ricardo@ricardo-desktop:~$ 



---

### Post by crjackson on 2008-04-28
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by gigaferz on 2008-04-29
thanks for the reply, my other pc doesnt have xine and it works fine..

anyway,it didnt work, I googled around and looks like it is an old bug, 

> ricardo@ricardo-desktop:~$ vlc

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DVD_VIDEO
libdvdnav: DVD Serial Number: 32514AA1
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ricardo/.dvdnav/DVD_VIDEO.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00055a84
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00055a95
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x0005bc78
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x0005bc89
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x000ade25
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x000ade36
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x000b064f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_14_1.VOB at 0x003f9e95
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_15_1.VOB at 0x003f9faf
libdvdread: Elapsed time 0
libdvdread: Found 15 VTS's
libdvdread: Elapsed time 0
[00000336] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
ricardo@ricardo-desktop:~$ 


> *** libdvdread: CHECK_VALUE failed in ifo_read.c:1572 ***
*** for c_adt->cell_adr_table[i].vob_id <= c_adt->nr_of_vobs ***

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault


I don think is a codec issue its been a long time since Ive had to do that kind of things manually ,since 7.10 it basically did it by itself , no need to look under the hood, like in dapper.....

Do you think reinstalling or trying with xubuntu might solve the problem?

---

### Post by mc4man on 2008-04-29
> Do you think reinstalling or trying with xubuntu might solve the problem?  I wouldn't do that yet - try
in vlc->Settings> Preferences> Video> Output Modules (check Advanced options bottom right) and try from dropdown list  x11
Also for the heck of it go to home directory ->.dvdcss open and delete all the folders inside

---

### Post by gigaferz on 2008-04-30
hello,  my friend got desperate and re installed ubuntu, I have never seen somebody  so happy with ubuntu before, and Ive benn trying to de-ubuntu-ize him but thats not possible.. anyway Im sure he'll start calling and messaging once if he gets that problem again , Ill post back

yep, there it is again, i just told him to hang in there  it might be fixed later on, but if he cant wait, theres still good old xp...

---

### Post by gigaferz on 2008-05-07
hello, 

After enabling the medibuntu repos,installing libdvdcss2 and w32codecs (only,nothing xine related) choosing a better server and selecting X11 in vlc, I got a dvd movie playing
Thank you

however the playback is horrible, it is an old computer but, it used to play dvd with no problems, do you think is better to go back to 7.10?

---

### Post by TakeLifeEasy on 2008-05-09
I too cannot get encrypted DVD's to play on either VLC, gXINE or Totem I just get a green scrambled strip in the middle of the screen on both VLC and Totem.  On gxine I just get the message "Encrypted media stream detected. Media stream scrambled/encrypted"

I am using 8.04 and have installed the Ubuntu-restricted add on.

Any ideas?

---

### Post by SunnyRabbiera on 2008-05-09
hmm, I am surprised that libdvdcss didnt work.

your not running a 64bit processor right?

---

### Post by TakeLifeEasy on 2008-05-09
Sorry, should have said I am running 64bit

---

### Post by SunnyRabbiera on 2008-05-09
> **TakeLifeEasy said:**
> Sorry, should have said I am running 64bit

aha, there might be the majority of your issues.
Me I cannot tell you how to solve this as I dont use a 64bit computer but at least we know your processor type.

---

### Post by TakeLifeEasy on 2008-05-09
So do I need libdvdcss?  I remember I had a whole ton of problems getting DVD playback working on openSUSE but if I remember, I forced the installation of libdvdcss and a few others and then it worked.  Not sure I want to do that on Ubuntu or even if it is possible.

DVD playback is a nightmare in Linux!  Still, everything is just a dream!

---

### Post by SunnyRabbiera on 2008-05-09
> **TakeLifeEasy said:**
> So do I need libdvdcss?  I remember I had a whole ton of problems getting DVD playback working on openSUSE but if I remember, I forced the installation of libdvdcss and a few others and then it worked.  Not sure I want to do that on Ubuntu or even if it is possible.

DVD playback is a nightmare in Linux!  Still, everything is just a dream!

Its not that bad, DVD's can work if you know how to, me I am lucky that I use a 32bit system as most crap out there is made only for 32bit systems.
I know its possible to get DVD's working in a 64bit system but how to do it is beyond me

---

### Post by mc4man on 2008-05-09
@ TakeLifeEasy
did you install libdvdcss2 ? 
Is this a new pc, ie. have you ever played commercial dvds on that dvd drive before

---

### Post by TakeLifeEasy on 2008-05-09
I have not installed the libdvdcss on this yet as I was under the impression that if you installed the Ubuntu-restricted library, that should be all you need.

Yes, I have played DVD's on this latop but that was under openSUSE.

Thanks for any help.

---

### Post by mc4man on 2008-05-09
Well then you'll have to install it. Either add medibuntu to your sources (preferred method)or you can grab the proper ver. here [http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)
11th from bottom libdvdcss2_1.2.9-2medibuntu4_amd64
I believe that's the current hardy 64 bit ver.
the ? about prior playback relates to that your drive must have a region set

---

### Post by TakeLifeEasy on 2008-05-10
Many thanks for everyones help.  I followed the instructions below -
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")

It did not work until I got to this bit -
sudo apt-get install libdvdcss2

It actually downloaded the i386 version but seems t work now.

Again, many thanks for your help.

---

### Post by TheAmigo on 2008-06-10
> **mc4man said:**
> the ? about prior playback relates to that your drive must have a region set

Ah, that's my problem!

On 32-bit hardy, I've followed every piece of advice I can find and DVDs still wouldn't play.

Then I saw that comment... my machine is brand new, hardy is the 1st OS its seen.  The region code was never set.  Quick bit of googling and I set the region code.  Now DVDs play fine (at least in Totem, Xine and Mplayer; VLC's still stubborn).

Now I just need [bug #218736]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/218736") resolved because [people are blue]("http://ubuntuforums.org/showthread.php?t=820630") in every movie.  At least adjusting the hue or switching to OpenGL fixes that for now.

---

