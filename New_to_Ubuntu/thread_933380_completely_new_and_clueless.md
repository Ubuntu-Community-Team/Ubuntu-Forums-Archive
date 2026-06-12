---
title: "completely new and clueless"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ljh on 2008-09-29
hi everyone i've decided i want to use ubuntu ver 8.04 as my os rather than vista i've give it a try and i'm kinda lost with it due to only ever using windows most i could do was access the internet anyway i use my pc for gaming, watching dvds and web surfing and i need help with these i need exact instructions 

1 how do i install games on ubuntu 

2 how do i setup raid 0 with ubuntu

3 how do i watch dvds with it

my hardware spec is as follows

intel q6600 @ 2.67 ghz g0 stepping
 asus P5N-E-SLI (i'm wanting to change this in the future to a MSI P35 Neo2-FR iP35 Socket 775)so i can overclock better
leadtek 8500gt (i will be upgrading to a hd4850 soon as RMA is complete i've heard ati's linux support is not the best but will i still be able to use it?)
ocz 2x2 gb ddr2 gold series dual channel
2x250gb 7200 rpm seagate barracuda
thanks in advance

---

### Post by Schonste on 2008-09-29
Linux isn't really gonna be the best choice for an OS if you only use your computer to play PC games and watch DVDs.

---

### Post by overdrank on 2008-09-29
> **ljh said:**
> hi everyone i've decided i want to use ubuntu ver 8.04 as my os rather than vista i've give it a try and i'm kinda lost with it due to only ever using windows most i could do was access the internet anyway i use my pc for gaming, watching dvds and web surfing and i need help with these i need exact instructions 

1 how do i install games on ubuntu 

2 how do i setup raid 0 with ubuntu

3 how do i watch dvds with it

my hardware spec is as follows

intel q6600 @ 2.67 ghz g0 stepping
 asus P5N-E-SLI (i'm wanting to change this in the future to a MSI P35 Neo2-FR iP35 Socket 775)so i can overclock better
leadtek 8500gt (i will be upgrading to a hd4850 soon as RMA is complete i've heard ati's linux support is not the best but will i still be able to use it?)
ocz 2x2 gb ddr2 gold series dual channel
2x250gb 7200 rpm seagate barracuda
thanks in advance

Hi and welcome, it depends on the games you would like to play. You may look at wine to play some window games.
For DVD and such you will need the restricted formats
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by bumanie on 2008-09-29
Check out [here]("http://www.transgaming.com/")and [here]("http://www.winehq.org/") re proprietary games. Look [here]("http://whdb.com/2008/top-25-linux-games-for-2008/") for native linux games. As far as dvd's go, I choose to use vlc player - it plays virtually all codecs. You will have to go to the medibuntu site and download codecs as per the site instructions. Raid 0 I know is possible and supported in linux, but I don't run raid so can't tell you how to set it up.

---

### Post by shifty_powers on 2008-09-29
well hold on a mo :D

1). What games did you have in mind? a lot of windows games will happily run under wine.... and there are quite a few linux games as well you know :D

2). The best way to go about raid is to use a hardware raid controller, as this will then make the whole process completely transparent to the os... (though i'm sure someone will give you more advice about that).

3). install vlc:

```
sudo apt-get install vlc
```

in the terminal.

---

### Post by LowSky on 2008-09-29
Watching DVD's is very possible, I have no idea what Schonste is talking about. As for gaming, well it depends on the game and if it's supported by WINE, you can check that here: [http://winehq.org/](http://winehq.org/)

and for Software RAID I'm assuming [http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/998-create-raid-on-ubuntu-804-part-1](http://beginlinux.com/index.php/server_training/server-managment-topics/116-server-management/998-create-raid-on-ubuntu-804-part-1)

---

### Post by E-mol on 2008-09-29
Hey, welcome to ubuntu :)

If the games you are thinking about are "windows-games" try "[WINE]("http://www.winehq.org/")". It cannot run all games, but a lot of them. There is a compatibilitylist [here]("http://appdb.winehq.org/"). 
If you can't run the games you want, you have to make a dual boot. There is some good guides [here]("https://help.ubuntu.com/community/WindowsDualBoot").
I used this one myself. Should work with xp too :)

And raid 0, i haven't worked with it myself, but found a wiki about it [here]("https://wiki.ubuntu.com/Raid"). It looks okay good :)

And dvds, i would say VLC. It is maybe i little complicated, but far the most stable movie/media-player right now. Install it, go "file->open disc" then choose the device the dvd is in. You can for example open the disc from your desktop, and copy-paste the "place". But useally the default dvd-device is set already.

If you haven't tried installing in ubuntu yet, it is damn simple, when it is learned. Choose "system -> admistration -> synaptic" it ask you for your password, and you can search for hundreds of programs. Fx vlc.

Hope ypu can use this ;)

Happy Everafter
E-mol :)

(Sorry for my not perfect English)

---

### Post by JoshuaRL on 2008-09-29
> **Schonste said:**
> Linux isn't really gonna be the best choice for an OS if you only use your computer to play PC games and watch DVDs.

I disagree.  DVDs are super easy, as many have said.  VLC is the awesomeness.  As far as games go, it may or may not be a problem

What specific games do you like?  What types of games to you like?  We may be able to help you get stuff running in Wine, or show you Linux games you might like.

---

### Post by ljh on 2008-09-29
ok thanks guys/girls i'll give those a read through feel free to add anything else i might find useful
for games i like pretty much anything that is not football

---

### Post by kansasnoob on 2008-09-29
First things first. I'm assuming that you already have Vista installed. If I'm wrong say so.

Do you have the Live CD?

If not get it either by download or ordering one, then run the Live CD, and run it some more, and still some more. Get a general idea of how it looks and feels!

And come back here and ask lots and lots of questions!!!!!!!!!!!

Then, if I was right about you already having Vista installed, you could consider a dual boot, a Wubi Installation, or creating a virtual machine with either VMware or Virtualbox.

I personally prefer a dual boot. It's not as scary as it sounds:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Just believe me. Every moment you spend on planning will be well worth it! If you're used to windows there is a learning curve, I started with gOS 1.0.1 and I thought I'd lose my mind the first few weeks until I found Ubuntu 7.10, but I'm still learning (and loving it) after 7 months.

I'm still multi-booted with Win XP but hardly ever use XP anymore, but it's still there if I feel the need to use it, and what the heck - I bought it - I might as well have it!

Just use common sense, be patient, and enjoy!

---

### Post by Thelasko on 2008-09-29
[I recommend this to every new/clueless user.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by ljh on 2008-09-29
thanks everyone that will do for now i'll come back if i run into problems

---

### Post by kansasnoob on 2008-09-29
> **JoshuaRL said:**
> I disagree.  DVDs are super easy, as many have said.  VLC is the awesomeness.  As far as games go, it may or may not be a problem

What specific games do you like?  What types of games to you like?  We may be able to help you get stuff running in Wine, or show you Linux games you might like.

+1 on the DVD front! With the Medibuntu support I have no problem!

---

