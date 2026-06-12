---
title: "Zoneminder  Security Webcam  (updated walkthrough)"
date: 2009-01-25
forum: Philippine Team
---

### Post by loell on 2009-01-25
ZoneMinder is a free, open source CCTV software application developed for Linux.

Ubuntu version scope: (Hardy or later)
Hardware requirement: Compatible webcam. (a4tech and logitech) recommended. 

**Installation**

1.) install zoneminder via ubuntu repo 

  ```
sudo apt-get install zoneminder
``` 

1a.) during installation MYSQL prompts for password.


3.) after the initial installation link this two files.

```
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf
```

3a. reload Apache
```

sudo /etc/init.d/apache2 reload
```

4.) next type sudo zmfix -a or zmfix -a will do (fixing problem sa video device)

4a.) then type also: sudo chown www-data.www-data /usr/share/zoneminder/temp (for export)


5. access its web interface by going to 
   
  ** [http://localhost](http://localhost)** , if it says "IT WORKS" then add **/zm** at the end of the url.  the default user and passwordis "admin"



---------------
credit goes to ([boyet]("http://ubuntuforums.org/member.php?u=299765"))

---

### Post by wersdaluv on 2009-01-26
Screens? :)

---

### Post by jsgotangco on 2009-01-26
Check [http://www.zoneminder.com/screenshots.html](http://www.zoneminder.com/screenshots.html)

This is pretty neat. I remember doing stuff like this a few years ago and we use video cards that are capable of connecting 4 or 5 cameras via coax cables. USB cameras will most likely work but this would be very very useful it can actually utilize existing cards available in the market. It seems to have some control features for cameras with motorized directional functionality.

---

### Post by kiminaiseah on 2009-01-26
sa debian experimental/sid multimedia center pag nag install ng zoneminder.. sarap gamitin kung may cable ka at home at i shishare mo xa via net :d

---

### Post by hogtrough on 2009-02-07
I installed ZoneMinder with the Synaptic Package Manager but now can't find it on my PC. I'm using an Avermedia video card (for up to 8 cams). The card is installed, but I haven't plugged the cameras in yet (setting up the PC at home, the cameras are at my workplace). Could that be the problem? Any help is appreciated. Thanks

---

### Post by loell on 2009-02-07
> **hogtrough said:**
> I installed ZoneMinder with the Synaptic Package Manager but now can't find it on my PC. I'm using an Avermedia video card (for up to 8 cams). The card is installed, but I haven't plugged the cameras in yet (setting up the PC at home, the cameras are at my workplace). Could that be the problem? Any help is appreciated. Thanks

avermedia seemed to be working on current kernels.  although i don't get it, the cameras are at your workplace?

---

### Post by hogtrough on 2009-02-08
> **loell said:**
> avermedia seemed to be working on current kernels.  although i don't get it, the cameras are at your workplace?
Actually, that was the short version. I'm working on it for a friend who owns a store. Her PC bit the dust (Emachine with Windows XP). The company that installed the cameras and software has been out of business for a few years. I found her a compatible used PC and installed the Avermedia capture cards but the software CD didn't have the serial number with it. I put a different hard drive in and installed Ubuntu and have been trying to get Zoneminder loaded and working here at my house before taking it to her store and hooking up the cameras. She doesn't have internet service at her store so I wanted to get everything loaded first. I've downloaded Zoneminder and Apache and MySQL, but don't know how to get them working. I can't even find ZoneMinder. Too many years of Windows where I didn't have to know anything to get programs to work, Windows is my crutch. I hate using it but sometimes I still have to to get around. :) Thanks for responding so fast.
Jeff

---

### Post by loell on 2009-02-08
zoneminder interface is web based, so you can just launch firefox then go to

[http://localhost]("http://localhost") , just post back what you see in there.

---

### Post by hogtrough on 2009-02-08
It says, "It Works"

---

### Post by loell on 2009-02-08
> **hogtrough said:**
> It says, "It Works"

if it says "IT WORKS" then add /zm  ( [http://localhost/zm]("http://localhost/zm")) at the end of the url. the default user and password is "admin"

---

### Post by hogtrough on 2009-02-08
Uninstalled Zoneminder, Apache, and MySQL with Synaptic and used the terminal to install following all of your steps (copy and paste) and all was successful up to a point. Typed in [http://localhost/](http://localhost/) and it gave the "It works" message, but when I typed in [http://localhost/zm](http://localhost/zm) it gave a Page Load Error (Firefox can't establish a connection to the server at localhost.) so I'm not sure what that's about. Once again, thanks for your patience with me. Sometimes I'm not as smart as I look. Also, will we be able to run ZoneMinder without internet access?

---

### Post by loell on 2009-02-09
yeah sure, you can just run zoneminder as a local cctv.

can you confirm if the avermedia card is detected in ubuntu?

post the output 

```
lsmod | grep video
```

and 

```
ls /dev/vid*
```

---

### Post by joran on 2009-04-09
hogtrough, i had the same problem.. after installing zm and going to [http://localhost/zm](http://localhost/zm). it came up with page cannot be displayed. after a while i realized i had forgot to run "sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf" after reloading apache that solved the problem for me. hope this helps for you, sorry its so late i just started out w/ zm

---

### Post by Script Warlock on 2009-05-20
mga masters patulong naman sa security cam ko ngayon dumating lang last week pinadala lang sa bro-n-law ko.. swann SW215-DMD needs dvr pci card at ang mahl pala 10k above? may mura ba kayong alam na compatible din sa ubuntu/linux?

---

### Post by loell on 2009-05-20
yeah, i reckon, that pci is really expensive, i dunno if you could find cheaper once.

---

### Post by Script Warlock on 2009-05-20
tsk tsk iba kc quality ng usb cams compare to the real cctv cams pero bka makapaghanap sa mga surplus shops try lang kung wala pagiponan kung di benta ko na lang to...

---

### Post by Script Warlock on 2009-05-20
hehehe i found it rca to usb adapter galing cdr king at surplus shop atlast mapapalitan na rin usb webcam ko ginamit ng magandang quality na security cam post ko lang next week ang zoneminder with 2cams usb and cctv...

---

### Post by Roasted on 2009-06-04
How do you guys have your webcams looked up with zoneminder? Do you just have them straight plugged into USB ports or what?

I'm trying to find a way that I could somehow attach a webcam to my wireless network... I'd like to put a webcam on the front of the garage. I can get wireless there, but I obviously don't have a computer out there.

Any ideas?

---

### Post by wowiesy on 2009-06-10
> **Script Warlock said:**
> mga masters patulong naman sa security cam ko ngayon dumating lang last week pinadala lang sa bro-n-law ko.. swann SW215-DMD needs dvr pci card at ang mahl pala 10k above? may mura ba kayong alam na compatible din sa ubuntu/linux?

bttv is widely supported in linux ...  if you will buy a DVR card, look at the decoder chip sa board (PCI)...  if it says conexant 2xxx, ok yan since conexant bought out brooktree which made the original BT8xx decoder chips.. for sure gagana yan... at gilmore and in divisoria i saw some units na about 1,000/channel.. comes in 4 / 8 channel....

i've seen some chips na techwell naman yung naka label... sadly these chips don't have linux drivers 

for the others, it would be a gamble... lately mga nakikita kong mga DVR pci cards, naka heatsink na yung mga decoder chips, hindi mo na makita kung ano ang gamit na chip kaya medyo risky if you really want to run it on linux....   malalaman mo lang kapag naikabit na sa pc, then lspci...  

although.. if you buy a DVR card per se, may kasama naman talaga syang software, yun nga lang lagi windows...   

hope this helps.

---

### Post by kiminaiseah on 2009-06-15
question lang,


bakit yung creative vista cam ko may display when i use it from cheese, kopete, skype, or any qt base apps, pero sa zoneminder nag eeeeerror na?

---

### Post by Script Warlock on 2009-06-16
> **kiminaiseah said:**
> question lang,


bakit yung creative vista cam ko may display when i use it from cheese, kopete, skype, or any qt base apps, pero sa zoneminder nag eeeeerror na?

yun ba yung gumagamit ng xawtv? or ov51-jpeg?

---

### Post by kiminaiseah on 2009-06-16
> **Script Warlock said:**
> yun ba yung gumagamit ng xawtv? or ov51-jpeg?

di ko lang sure pero without installing of it gumana naman agad sa cheese kopete & skype, tinest ko sya sa Ubuntu 9.04

---

### Post by B00R4dL3y on 2009-06-16
> **Roasted said:**
> How do you guys have your webcams looked up with zoneminder? Do you just have them straight plugged into USB ports or what?

I'm trying to find a way that I could somehow attach a webcam to my wireless network... I'd like to put a webcam on the front of the garage. I can get wireless there, but I obviously don't have a computer out there.

Any ideas?

What you need is an ip camera.  It can connect via your wired/wireless network and send picture/video.

---

### Post by Script Warlock on 2009-06-16
kahit eto ang command?

zmu -d /dev/video0 -q -v

or

chmod 777 /dev/video0 or zmfix -a

---

### Post by kiminaiseah on 2009-06-20
pa tulong naman

e2 logs ko

root@ubuntu-koala:~# zmu -d /dev/video1 -qv
Video Capabilities
  Name: CIF Single Chip
  Type: 1
    Can capture
  Video Channels: 1
  Audio Channels: 0
  Maximum Width: 352
  Maximum Height: 288
  Minimum Width: 48
  Minimum Height: 32
Window Attributes
  X Offset: 0
  Y Offset: 0
  Width: 352
  Height: 288
Picture Attributes
  Palette: 0 - Unknown
  Colour Depth: 8
  Brightness: 1028
  Hue: 0
  Colour :0
  Contrast: 0
  Whiteness: 0
Channel 0 Attributes
  Name: pac207
  Channel: 0
  Flags: 0
  Type: 2 - Camera
  Format: 0 - PAL

----------

[SIZE="1"]Jun 21 01:42:20 ubuntu-koala zmdc[6601]: INF ['zmc -d /dev/video1' started at 09/06/21 01:42:20]
Jun 21 01:42:20 ubuntu-koala zmc_dvideo1[6601]: INF [Debug Level = 0, Debug Log = <none>]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' starting at 09/06/21 01:42:20, pid = 6601]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' crashed, signal 6]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: INF [Starting pending process, zmc -d /dev/video1]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' starting at 09/06/21 01:42:20, pid = 6604]
Jun 21 01:42:20 ubuntu-koala zmdc[6604]: INF ['zmc -d /dev/video1' started at 09/06/21 01:42:20]
Jun 21 01:42:20 ubuntu-koala zmc_dvideo1[6604]: INF [Debug Level = 0, Debug Log = <none>]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' crashed, signal 6]
Jun 21 01:42:20 ubuntu-koala zmdc[5600]: WAR [Can't find process with command of 'zma -m 3']
Jun 21 01:42:25 ubuntu-koala zmdc[5600]: INF [Starting pending process, zmc -d /dev/video1]
Jun 21 01:42:25 ubuntu-koala zmdc[6615]: INF ['zmc -d /dev/video1' started at 09/06/21 01:42:25]
Jun 21 01:42:25 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' starting at 09/06/21 01:42:25, pid = 6615]
Jun 21 01:42:25 ubuntu-koala zmc_dvideo1[6615]: INF [Debug Level = 0, Debug Log = <none>]
Jun 21 01:42:25 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' crashed, signal 6]
Jun 21 01:42:35 ubuntu-koala zmdc[5600]: INF [Starting pending process, zmc -d /dev/video1]
Jun 21 01:42:35 ubuntu-koala zmdc[6616]: INF ['zmc -d /dev/video1' started at 09/06/21 01:42:35]
Jun 21 01:42:35 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' starting at 09/06/21 01:42:35, pid = 6616]
Jun 21 01:42:35 ubuntu-koala zmc_dvideo1[6616]: INF [Debug Level = 0, Debug Log = <none>]
Jun 21 01:42:35 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' crashed, signal 6]
Jun 21 01:42:55 ubuntu-koala zmdc[5600]: INF [Starting pending process, zmc -d /dev/video1]
Jun 21 01:42:55 ubuntu-koala zmdc[6618]: INF ['zmc -d /dev/video1' started at 09/06/21 01:42:55]
Jun 21 01:42:55 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' starting at 09/06/21 01:42:55, pid = 6618]
Jun 21 01:42:55 ubuntu-koala zmc_dvideo1[6618]: INF [Debug Level = 0, Debug Log = <none>]
Jun 21 01:42:55 ubuntu-koala zmdc[5600]: INF ['zmc -d /dev/video1' crashed, signal 6]
[/SIZE]

---

### Post by alek66 on 2012-08-11
How did you get it to work, I have a Cif Single chip

aleza@Deathstar:~$ zmu -d /dev/video0 -qv
Error, failed to enumerate standard 0: Success

---

