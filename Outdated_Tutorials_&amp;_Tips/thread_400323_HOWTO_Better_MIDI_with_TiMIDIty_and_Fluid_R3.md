---
title: "HOWTO: Better MIDI with TiMIDIty and Fluid R3"
date: 2007-04-03
forum: Outdated Tutorials &amp; Tips
---

### Post by D-- on 2007-04-03
[B][COLOR="DarkRed"]The system I tested it on was 32-bit Ubuntu Feisty 7.04.

The guide is provided at users' own risk. I will try to provide support and answer questions in the thread, but if you somehow type something wrong and send your OS spiraling into /dev/null, don't blame me.[/COLOR][/B]

Timidity is a great little software MIDI synth which can use nearly anything you throw at it to generate blips and beeps. By default, it comes with the &#8220;freepats&#8221; patch collection. Unfortunately, the quality of  freepats is not terribly good, and it is missing many instruments.

If you use RoseGarden or another program to skim through your MIDIs and print sheet music, or just track your own stuff without a hardware synth, freepats is not up to snuff.

Enter Fluid R3, one of the biggest, bulkiest, free (but not in the GNU sense) sound archives out there.

In this HowTo, I'll demonstrate how you can get Fluid R3 working in your Ubuntu with TiMIDIty, which is available in the Ubuntu repo.

First, you need to download Fluid R3. It is available from the [HammerSound Soundfont Library](http://www.hammersound.net/) ([direct link](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_category&category=Collections&ListStart=15&ListLength=15)).

The zip is a hefty 68.5MB and will take some time to download. While you are getting it, go download sfArk, which is needed to uncompress the soundfont. There is a Linux version available at [the sfArk website](http://www.melodymachine.com/sfark.htm) which works fine in Ubuntu.

**[COLOR="DarkRed"]Warning:[/COLOR] it has some strange problem where &#8220;tar zxpvf&#8221; won't recognize it. So you need to unpack in two steps.**

Lastly, grab my attached archive in this thread: TiMIDIty-FluidR3-ubuntu.tar.gz. It contains all the sample scaling for the instruments included in the soundfont. If you know who created the file, please inform me. I've been using this TiMIDIty setup on Windows for several years, and have lost the website I found the Fluid R3 definition at. [color="DarkRed"]Edit:Garybrlow pointed out it is from [TiMidity++ experimental](http://timidity.s11.xrea.com/index.en.html).[/color]

Now that you have the the files, open a terminal and punch in these commands:

```
$ unzip FluidR3122501.zip
$ gunzip sfarkxtc_lx86.tar.gz
$ tar xvf sfarkxtc_lx86.tar
$ ./sfarkxtc FluidR3\ GM.sfArk
$ tar zxpvf TiMIDIty-FluidR3-ubuntu.tar.gz
$ mv FluidR3\ GM.SF2 timidity/sf2/
# apt-get install timidity
# mv timidity /usr/local/
# mousepad /etc/timidity/timidity.cfg
```

In timidity.cfg, comment out the last line by adding a pound symbol (like: #source) and add this line:

```
source /usr/local/timidity/timidity_fluid3.cfg
```

Congrats. TiMIDIty is now installed and set up to use the Fluid R3 soundfont. If you would like to use TiMIDIty as your default synth to play MIDI files, you will need to install a service to run it whenever gdm launches.

You can do this using the GNOME Services menu in Control Panel, clicking add, and using this command line:

```
timidity -iA -B2,8 -Os1l -s 44100
```

Just make sure your MIDI software is pointing to device zero and you should get some groovy, TiMIDIty synthed tunes.

This tutorial will also get working MIDI on a machine where the hardware MIDI device is not supported by the Linux kernel.

---

### Post by muxecoid on 2007-04-06
Hi.
It would be good to mirror Linux version of sfArk. The official site is not reliable and other mirrors provide only Win32 executables.

---

### Post by mosestruong on 2007-04-16
How do you add a new service? When I click on services, it only allows me to start, stop and set properties for already defined services.

---

### Post by D-- on 2007-04-17
It's in the first pane. You might need to right click to do it. You'll need to make a name for it, and also a command.

---

### Post by garybrlow on 2007-04-23
sfARK for windows works fine under wine. :)

Cheers!!!


GaryBrlow :biggrin:

---

### Post by garybrlow on 2007-04-23
D--,

All config files for FluidR3 and others are found here [http://timidity.s11.xrea.com/index.en.html](http://timidity.s11.xrea.com/index.en.html). The site is called Timidity++ experimental and it has a new GUI for the windows version. There is also somebody who made a TCL-TK gui for timidity and says that he overhauled it and made a better gui. I can't test this one since am not sure how to compile his provided source code. If you can make heads or tails on compiling this one I'd be interested to know. The code is found here [http://tkgames.sourceforge.net/](http://tkgames.sourceforge.net/), perhaps he does provide a better GUI than the default ones that come with timidity.

Cheers!!!

GaryBrlow :biggrin:

---

### Post by D-- on 2007-04-24
I've noticed my machine is running TiMIDIty at boot. Not sure if this is normal, but if it is, you can dump that line about adding the Gnome service.

Thanks. I'll amend the first post to point to where you can get his Fluid R3 stuff. Not sure if he's updated it at all since I downloaded it years back.

By the way, if you run across any other soundfonts config files for TiMIDIty, those can easily be used too.

---

### Post by sebas.rhcp on 2007-04-24
How do you add a new service?

---

### Post by D-- on 2007-04-24
I don't have Ubuntu anymore (only Xubuntu), but I remember it is the Settings menu, then either the user controls or Admin ones has an option that says "Services". Pick that, then right click in the list to add a new one. You need to give it a name and command line.

---

### Post by ziffnabb on 2007-04-26
I followed your guide, and finally have midi working - at least I can play midi files now - so that means it's working, right?  I have a Sound Blaster Live 128, where the midi output is not working with linux.

Anyway, I am trying to get sound output with a program called Finale 2006.  It is a music notation program.  I don't like the linux ones that I have tried.  The program runs under Wine - but I cannot get any sound out of it.  Is there any way to get a program running under wine to use Timidity for midi output?  

Thanks,
Ziffnabb

---

### Post by Kaobear on 2007-04-26
Everything worked like a charm, bravo and a good tutorial to boot.

---

### Post by D-- on 2007-04-27
> **ziffnabb said:**
> I followed your guide, and finally have midi working - at least I can play midi files now - so that means it's working, right?  I have a Sound Blaster Live 128, where the midi output is not working with linux.

Anyway, I am trying to get sound output with a program called Finale 2006.  It is a music notation program.  I don't like the linux ones that I have tried.  The program runs under Wine - but I cannot get any sound out of it.  Is there any way to get a program running under wine to use Timidity for midi output?  

Thanks,
Ziffnabb

How is your Wine set up? I get MIDI fine. I think the trick is Wine needs to be outputting to where Timidity is running: ALSA.

Run winecfg and click the Audio tab. Check ALSA Drive, then set Hardware Acceleration to Emulation.

I'm running this setup using a POS Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04). On-board laptop audio rocks :(

---

### Post by ziffnabb on 2007-04-27
That did the trick!  Thanks so much!

Ziffnabb

---

### Post by alainhenry on 2007-04-29
Works great! 
I must be taxing my system (512 Megs RAM, Pentium @ 3 MHz, though).  I am using noteedit, which provides as a sample the first movement of Beetthoven's 5th, with 12 staffs on the score.  When I play this, i hear scratches from time to time, when all 12 staffs are playing with plenty of notes. CPU is 100% busy at those time. 

However, playing a more reasonable piece, 3 or 4 staffs, as we sing in our chorale (choir ?) is fine.  And it's a much more beautiful sound than with Unison that I used before.  

Alain

---

### Post by D-- on 2007-04-29
Yeah. I've noticed that when I play things through Rosegarden it sometime crackels if it has over 4 staffs. But the same one plays fine through console timidity. My guess is it must be due to some other demands the software is putting on MIDI. Haven't tried with kmidi or anything like that yet.

---

### Post by wayne1pow on 2007-05-09
helllo i'm pretty new to linux and especially ubuntu i did all the things you instructed but it wont play now. the only thing i'm not sure about is wether the midi software is pointing to device zero. how do i check that? 
i'm using 32-bit Ubuntu Feisty 7.04

---

### Post by D-- on 2007-05-15
That would be something you need to check in the program you are using ...

---

### Post by mcman42 on 2007-05-19
> **D-- said:**
> 

You can do this using the GNOME Services menu in Control Panel, clicking add, and using this command line:



Thanks for the how-to, just to make it more perfect, it's not control panel, it's:

System -> Preferences -> Sessions -> New

---

### Post by shador on 2007-05-20
My install stopp at Opening "sequencer port: 128:0 128:1 128:2 128:3"

It just doesn't go beyond that line, any idea?

---

### Post by apricot on 2007-05-20
This is a test

> Test

```
Test
```

[HTML]Test[/HTML]

[PHP]Test[/PHP]

---

### Post by apricot on 2007-05-20
Sorry. :)

---

### Post by D-- on 2007-05-28
shador: Hi, sorry. No idea about this one.

I think you should ask someone more experienced with the workings of Timidity. It sounds like some kind of a port conflict.

---

### Post by trontonic on 2009-01-21
Thank you for the tutorial. Worked for me on Jaunty.

---

### Post by zicho on 2009-07-11
[http://www.melodymachine.com/sfark.htm](http://www.melodymachine.com/sfark.htm)

Doesnt work anymore... does anyone know where else to get it?

---

### Post by tornavis on 2009-10-12
> **zicho said:**
> [http://www.melodymachine.com/sfark.htm](http://www.melodymachine.com/sfark.htm)

Doesnt work anymore... does anyone know where else to get it?

Remove the www:
[http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm)

---

### Post by FactTech on 2011-04-23
Since Google directed me to this post, I thought I'd mention for anyone else that comes along that the Fluid R3 soundfonts are now available in the Ubuntu repository (at least for lucid). The package is called fluid-soundfont-gm.

---

