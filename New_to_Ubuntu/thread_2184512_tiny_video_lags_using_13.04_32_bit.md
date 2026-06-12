---
title: "tiny video lags using 13.04 32 bit"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by garylord07 on 2013-10-29
hi.

i am new to using ubuntu and i have 13.04 installed.


when i try to watch a video online either on youtube or redbulltv.com it lags a tiny bit. its almost like its freezing every 10th of a second. does anyone know how to fix this problem?

---

### Post by sudodus on 2013-10-29
Welcome to the Ubuntu Forums :-)

There can be several reasons. Two of them are

- Your computer does not have enough horsepower (CPU) or memory (RAM) to run standard Ubuntu with the Unity desktop environment.
- Your graphics driver is not working properly with your graphics card.

The solutions are different, so please post the specs of your computer

- Brand name and model
- CPU, RAM (size), graphics chip/card

You find information about it running
```

sudo lshw > lshw.txt
```

and view the file lshw.txt with a viewer or editor, for example

```
less lshw.txt
```

or running

```
hardinfo
```

---

### Post by garylord07 on 2013-10-29
Hi thanks for the reply. this is what i know about the pc at the moment...memory=2.0GiB
                                                                                                  processor=intel pentium 4 cpu 3.06ghz
                                                                                                  graphics= intel 915gx86/mmx/sse2
                                                                                                  os type= 32 bit
                                                                                                  disk= 194.7 GB

i am still getting to grips with how to control ubuntu. my old computer with windows xp died and a friend recommended using ubuntu so he built me the computer i am using now. is the info i have given here any help??

Thanks

---

### Post by sudodus on 2013-10-29
Yes. It is one of the fastest Pentium 4 CPUs and you have 2 GB RAM which is good, but I think not quite enough for standard Ubuntu with Unity. The built-in drivers probably work well with the Intel graphics.

Check also what version of Ubuntu you are running. What is the output of this command?

```
lsb_release -a
```

So I suggest that you try

- Lubuntu with the ultra-light desktop environment LXDE or
- Xubuntu with the light desktop environment XFCE

You can try it different ways depending on your internet speed.

1. If fast internet, download a Lubuntu and or Xubuntu iso file and make a CD/DVD/USB drive and boot live session (try without installing).

2. If slow internet, install the corresponding desktop environments including or excluding all the Lubuntu/Xubuntu software and tweaks. The engine behind the desktop environment is the same in all Ubuntu flavours.

```
sudo apt-get install lxde  # the desktop environment
sudo apt-get install xfce4  # the desktop environment
```
```
sudo apt-get install lubuntu-desktop  # including software and tweaks
sudo apt-get install xubuntu-desktop  # including software and tweaks
```

Edit: Select desktop environment alias session clicking on the round symbol near the log in text window.

**Backup** your system before adding the desktop environments, because it might be hard to get a clean environment afterwards, even if there is a tutorial about it, [URL="http://www.psychocats.net/ubuntu/"]http://www.psychocats.net/ubuntu/
[/URL]

---

