---
title: "New user installation of Ubuntu"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by mikepelton on 2008-08-15
I have just loaded Ubuntu instead of Windows XP Home by using a Ubuntu CD and adding all updates. I am able to access the programme and get applications etc, however when I try to listen to music from previous MP3 files Rhythmbox Music Player does not load them and I cannot see how to load the approriate codecs. CD player loads songs from Cd's but there is no sound when I try to play them. Also Ubuntu recognises my printer Epson Stylus CX5900 but I cannot load any drivers to make it print. All I get is blank paper coming through the feed. Can anybody assist this very novice user?:confused: I shall be eternally grateful. Cheers

[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by arpanaut on 2008-08-15
This will get you the media stuff going.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

another more advanced how to...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mevets on 2008-08-15
To solve the codecs problem Applications > Add/Remove > Search 'ubuntu restricted extras' > Install that

Or you could copy this into the terminal:
```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by Yuki_Nagato on 2008-08-15
First, install the mp3 codecs by using:

```
sudo apt-get install ubuntu-restricted-extras
```


Printing I cannot help you with personally, as I send my documents over a network to print, and the printer is hooked to a Windows machine (the jobs are created there.)

I know the place to start would be to look up a program called "CUPS."  I hear it has great success with the HP printers, but I am not sure about Epson.

---

### Post by str8line on 2008-08-15
A quick search at [http://www.linuxprinting.org](http://www.linuxprinting.org) revealed this information on your printer:

[Epson Stylus]("http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX5900")

I have had similar problems with Canon and Lexmark Printers.  Every HP printer I have ever owned instantly is recognized and works better than with the Windows bloat.

Chris Powell
Lemming CIR
London, ON

---

