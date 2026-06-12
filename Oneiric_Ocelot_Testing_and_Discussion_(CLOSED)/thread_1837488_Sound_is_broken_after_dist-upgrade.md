---
title: "Sound is broken after dist-upgrade"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pimentel28 on 2011-09-01
The sound is broken after a dist-upgrade, the volume slider doesn't work and there is no audio output.

Thanks in advance.

---

### Post by effenberg0x0 on 2011-09-01
I have it working partially...headphone, speaker, microphone, etc jacks became swapped. My hardware is an Intel ACL892. Are you using the same Codec by any chance?

Thanks,
Effenberg

---

### Post by pimentel28 on 2011-09-01
> **effenberg0x0 said:**
> I have it working partially...headphone, speaker, microphone, etc jacks became swapped. My hardware is an Intel ACL892. Are you using the same Codec by any chance?

Thanks,
Effenberg

My hardware is 
High Definition 6-channel audio 

[LIST]
[*]Realtek ALC 888S chipset
[/LIST]
[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141)

About codecs, it seems like restricted extras won't work. Not even flash :/

Got sound working. Restricted extras is removed and wont' work. Gah. 

Tried removing/reinstalling the codecs, did not work.

---

### Post by cariboo on 2011-09-02
> **pimentel28 said:**
> My hardware is 
High Definition 6-channel audio 

[LIST]
[*]Realtek ALC 888S chipset
[/LIST]
[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=141)

About codecs, it seems like restricted extras won't work. Not even flash :/

Got sound working. Restricted extras is removed and wont' work. Gah. 

Tried removing/reinstalling the codecs, did not work.

It would help if you at least posted whatever error message you are getting, we can't help if we don' know what the problem is.

---

### Post by rapiertg on 2011-09-02
I would check if correct output is selected. It somehow switches it to the wrong one for me every boot, and i have to change it manually, than everything is working fine.

---

### Post by willygatti on 2011-09-02
My sound is broken as well after upgrading to Ubuntu 11.10 Beta in addition to Adobe Flash Player.  I can't even increase the volume via the slider.  I tried the pasuspender command via the GNOME terminal as Launchpad suggested; [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/821052]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/821052") , and I still couldn't hear any sound.  Here is my terminal output:

```
speaker-test 1.0.24.2

speaker-test: invalid option -- '1'
Unknown option '?'

```

---

### Post by pimentel28 on 2011-09-02
> **willygatti said:**
> My sound is broken as well after upgrading to Ubuntu 11.10 Beta in addition to Adobe Flash Player.  I can't even increase the volume via the slider.  I tried the pasuspender command via the GNOME terminal as Launchpad suggested; [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/821052](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/821052) , and I still couldn't hear any sound.  Here is my terminal output:

```
speaker-test 1.0.24.2

speaker-test: invalid option -- '1'
Unknown option '?'

```

I got sound working (had to switch the output for a couple of reboots..finally saved!) and about flash, I had to reinstall restricted extras and also reinstall the plugin for Mozilla. Will take more than one try to get it working.

---

### Post by 23dornot23d on 2011-09-02
We went through this a long time back ..... each time I upgrade I automatically add the 
following and get my sound back ..... 

The solution is to do this on my system ,,,, Acer Aspire 7730ZG
 gksudo gedit /etc/modprobe.d/alsa-base.conf

```

 **options snd-hda-intel model=auto**

```But mine may be different just seen one is Realtek above was second post Intel ....

```

keith@keith-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 


you might find by adding this or similar as a last line ..... you may get stereo sound back ....... after a reboot
I do .....

[B][COLOR=Red]if not it may be another problem .....
( I did have sound yesyerday and since upgrading the above file was changed back to the default )
because my additional line was missing ...... which results in no sound at all ...... 



[/COLOR][/B][URL="http://ubuntuforums.org/member.php?u=1281472"]
@ pimentel28[/URL]
> 
I got sound working (had to switch the output for a couple of  reboots..finally saved!) and about flash, I had to reinstall restricted  extras and also reinstall the plugin for Mozilla. Will take more than  one try to get it working.
Where are you switching the sound .... output and what to ..... and do you get full surround sound ..... or stereo ?

---

### Post by pimentel28 on 2011-09-02
> **23dornot23d said:**
> [URL="http://ubuntuforums.org/member.php?u=1281472"]
@ pimentel28[/URL]
Where are you switching the sound .... output and what to ..... and do you get full surround sound ..... or stereo ?

You'll have to lookup the specifications for your sound card.

Superkey -> Type: Sound -> select the Sound application 

Go to the Hardware tab and select the Profile that works. Mine was Analog Sound 5.0 Output + Analog Stereo Input

Took a few reboots to get the hardware showing up on output, for me it was saying dummy output until a few reboots.

---

### Post by 23dornot23d on 2011-09-02
Ok thank you .... will try the new settings and some reboots ...... ;)

Hopefully I will get surround sound too .....

---

### Post by willygatti on 2011-09-02
Thank you for all your help so far, after editing alsa-base.conf with the line of code you suggested the sound problem is fixed enabling me to listen to music, and watch DVD movies, but unfortunately Adobe Flash is still broken, so I can't watch YouTube videos, or play flash based web games.

---

### Post by 23dornot23d on 2011-09-03
run alsamixer in a terminal ....

and see what settings you have ..... [**SCREENSHOT**]("http://img41.imageshack.us/img41/9610/screenshot20at202011090.jpg")

Check on the you-tube .... volume .... on its video playback screen  .... all I can advise on that one.

My flash installs ok on 64 bit ..... using _*[sevenmachines ppa]("https://launchpad.net/%7Esevenmachines/+archive/flash")*_

---

