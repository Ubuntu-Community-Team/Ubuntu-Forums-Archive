---
title: "HOWTO: Homebrew LIRC under fiesty (no kernel source, no compiling!)"
date: 2007-06-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Stormx on 2007-06-18
[SIZE="4"]**Preamble**[/SIZE]
[SIZE="3"]**Intro**[/SIZE]
This is a guide on building a homebrew (that means, not shop-bought) LIRC (Linux Infrared) receiver, and setting it up to work with your Ubuntu Feisty installation.

The device itself will use very few componants, and will connect via the line-in port of your sound card. LIRC can be installed from the Ubuntu repositories. You don't need to install the kernel source, do *any* compiling, or worry about what happens when a kernel update comes along! The whole process is easy; I did this when I was 15.

[SIZE="3"]**Background on LIRC**[/SIZE]
LIRC allows you to use a remote control to control some of your favourite apps. MythTV (a PVR system), VLC (A video player) and a lot of music players all have a LIRC interface. You can run any command-line command from LIRC (such as "audacious --play-pause") too, so it gives you a huge range of possibilities. I've got buttons to blank my screen, lock it, etc. Read: the sky is the limit.

All this is controlled through a remote control. You _could_ build one, but there isn't much point. A huge range of remote controls are supported.

[SIZE="3"]**Sources**[/SIZE]

[http://people.inf.ethz.ch/mringwal/lirc/](http://people.inf.ethz.ch/mringwal/lirc/) - Used for schematic
[http://lirc.org/html/audio-alsa.html](http://lirc.org/html/audio-alsa.html) - Information on the LIRC ALSA drivers
Various help from lots of people :-)

[SIZE="3"]**Requirements/Materials**[/SIZE]

[LIST]
[*] Ubuntu, running feisty fawn (I previously compiling LIRC on Edgy, which also worked, but a repo install should work on any version of ubuntu with lirc in the repos. I tested in an x86 architecture, but again, it shouldn't matter)
[*] A full duplex sound card with a 3.5mm input port (for example, mic or line-in) that you don't mind using while you need to use LIRC
[*] A +5V power source (USB, Motherboard, shop-bought adapter, serial port... discussed later)
[*] A soldering iron, some solder.
[*] 3.5mm Audio jack/wire. You can use old headphones for this, or buy one from a shop.
[/LIST]

Electrical componants:

[LIST]
[*] TSOP 1738 (The IR componant)
[*] 4k7 resistor
[*] 1k resistor
[*] 100nF capacitor
[/LIST]

[SIZE="4"]**Step 1: Circuit wizardry**[/SIZE]

Here is a schematic of the circuit you'll build, courtesy of the first aforementioned guide:

[img]http://people.inf.ethz.ch/mringwal/lirc/images/sensor_lirc_audio.png[/img]

First thing you need to worry about is a power supply. There are a few ways of going about this. You need 5V, and there are lots of things in the computer that supply it. Find a spare pin on the motherboard, or strip a serial / usb lead and fiddle around with a voltmeter. You'll soon find +5V. Or you can be lazy, like I did. I bought an adapter from a shop that can switch its voltage supply, etc. To save ruining a perfectly good adapter, I also bought something of an extension cable for this, which is cheaper and I don't mind dedicated its life to this specific project. Some photos:

[img]http://www.goldenfalcon.net/lirc/adapter.jpg[/img]
*The adapter I used*
[img]http://www.goldenfalcon.net/lirc/wires.jpg[/img]
*Connecting the adapter up to the extension: adapter wire on right*

You need to get hold of the components above. If you go to a school, college, ask if you can get the resistors/capacitor. My school let me use them. if that doesn't work, chances are they won't notice they're gone ;-). If stealing doesn't appeal to you, talk to anyone you know who might be willing to part with them. If all else fails, order some, but it will cost a bit more because you aren't buying in bulk. The IR chip will probably need to be ordered anyway.

I'm not going to go into how to solder, there are other guides for that sort of thing. Here's the jist of setting up the circuit:

[LIST=1]
[*] Set up your power supply. If you're using my method, cut the wire, plug it in, and figure out which wire is positive (using a meter)
[*] Solder stuff! Connect your power supply (but make sure it's off!) to the IR chip. Connect up ground too. You'll have one "leg" of the chip remaining, the output
[*] Solder the resistors together, and then to the IR chip. Solder the capacitor between them.
[*] Cut and strip your headphone wire (or whatever you are using). If it's stereo, you'll have two wires, each surrounded by more wire (which is ground). You only need one channel. Strip the inner wire (the coloured one) and connect this to the free leg of the capacitor. Finally, connect the other end of the resistors in series to the headphone ground (the outer, protective wire). Yay!
[/LIST]

[SIZE="4"]**Step 2: Make a case**[/SIZE]

This is a little more imaginative. You can mount the circuit inside your computer, but I didn't bother. I actually got an old audio cassette case, cut holes in it, cellotaped everything down, and then cellotaped it to the top of my monitor:

[img]http://www.goldenfalcon.net/lirc/screen_top.jpg[/img]

It's not pretty, but I don't mind. It does the job and keeps the circuit safe.

[SIZE="4"]**Step 3: Check the circuit works**[/SIZE]
If you haven't already, connect everything up. Put the audio jack into the line-in of your sound card. Connect the power! 

(side note: tapping one of the legs of the capacitor sends a very low base note. if you have the speakers for it, try it. it's pretty cool :))

Now, open your sound settings. You can do this from the GNOME menu (Applications > Sound and Video > Volume Control) or from the command line:

```
$ gnome-volume-control
```

You can also use alsamixer for this if you prefer to use terminal.

Go to **Edit > Preferences**. Make sure the following are checked: Line-in, Line-in capture, capture.

Hit close on the preferences window. Under the "playback" tab, locate "Line-in". Raise the volume to full, and be sure it isn't muted (icon at the bottom). Now find a remote control, any! VCR, DVD, TV, Stereo, whatever. We're just testing here. Press some buttons. You'll hear some sci-fi-ish noises. YAY! That means your circuit is working.

Not hearing anything? Check your volume is on, your speakers on/connected, that line-in is unmuted, etc. Check your circuit has power with a meter, check the solder joints and that you've soldered stuff to the right pins of the IR chip.

[SIZE="4"]**Step 4: Getting LIRC to work**[/SIZE]

```
$ sudo apt-get install lirc lirc-x
```

Install any/all dependencies.You need the "universe" repo enabled to run the above. To enable it, check out the excellent wiki page: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Now to do some configuring. You need a remote control that LIRC will work with. That's any remote control, however they all need configuring. That means converting the noises you heard earlier into button codes. Thankfully, people submit their files for this sort of thing:

[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

I went through my entire house looking for remotes. Eventually my dad pointed out that Philips had invented the RC-5 specification, so any Philips remotes would be a safe bet. Luckily it was. My Phillips VCR remote was supported, which is nice.

**If you can find a supported remote:**
Great! Download the file to your desktop. Then:

```
~/Desktop$ sudo mv filename /etc/lirc/lircd.conf
```

**If you can't find a supported remote:**

You may need to make the configuration file yourself. There are guides around for this, google it. I'll add links to this guide later.

-----

That's one half of the lirc configuration. The next step is to launch the lirc daemon (lircd). This runs as root.

```
$ sudo lircd --driver=audio_alsa -d hw@48000
```

A little explaination! The --driver=audio_alsa sets up LIRC to use the ALSA driver, which means it looks at sound input
-d hw@48000 is the device. hw is the sound card itself, so you can set this to hw1,0 if you are using your second sound card. the 48000 bit is the sample rate. Lower than this, and lircd doesn't pick up all your button presses. 

[SIZE="4"]**Step 5: Test LIRC configuration**[/SIZE]
First, set up line-in as your capture device. With the gnome-volume-control window you left open, go to the "switches" tab. Check the "line-in capture" box. Move to the "recording" tab. Make sure the volume is on max and that it is unmuted. Finally, check that the line-in is still on full volume and still unmuted. 

Open a terminal. Run:
```
$ irw
```
Two things can happen here. Either the command will end straight away, or hang there. The former is bad, it means it couldn't connect to the LIRC session. Start lircd with -n as an argument to see what the trouble could be.

Otherwise, hit buttons! With any luck you should see their relevant codes showing up. For example, when I press 1, 2, 3 I get:

```
$ irw
0000000000001141 02 sys_05_command_01 PHILIPS_RC-5
0000000000001142 00 sys_05_command_02 PHILIPS_RC-5
0000000000001143 00 sys_05_command_03 PHILIPS_RC-5

```

That's good news, again. If your button-pressing yields nothing, you've got a problem. First, check that the circuit is still working (do this by unmuting line-in). If that works, check the config file you have is suitable for your remote control. Try killing lirc (sudo killall lircd) and starting it again (as above).


[SIZE="4"]**Step 6: LIRC application configuration**[/SIZE]

Next we need to turn the kind of thing returned by irw into useful commands. A few apps have lirc modules build into them, which is nice. Others, you can do command-line control. This configuration revolves around a configuration file in your home directory, called .lircrc

Open your favourite text editor and save as this file. Configuring this file is covered in the LIRC documentation: [http://www.lirc.org/html/configure.html](http://www.lirc.org/html/configure.html) (scroll down to "The .lircrc file format"). Here's the just of it anyway:

```

begin
	remote = PHILIPS_RC-5
	prog = vlc
	button = sys_05_command_34
	config = key-next
	repeat = 0
end

```

Above is a snippet of my configuration file. It uses data returned from irw. You can see the remote is set to PHILIPS_RC-5 (which is from irw) and the button is sys_05_command_34 (again, from irw). VLC provides a LIRC interface, so I can set "prog" to vlc. Note that this isn't a bash command, as only apps which have LIRC plugins/interfaces can be used here. The "config" is the big passed to VLC, in this case telling it to go the next item in the playlist. repeat is explained by the above documentation:

> 
repeat tells the program what shall happen if a key is repeated. A value of zero tells the program to ignore repeated keys. Any other positive value 'n' tells the program to pass the config string every 'n'-th time to the according application, when a key is repeated. The default for repeat is zero.


Want to run commands? Here's another snippet.

```

begin
	remote = PHILIPS_RC-5
	prog = irexec
	button = sys_05_command_31 
	config = gnome-screensaver-command -a
end
```

Here, irexec is the program. irexec accepts applications in the config. I've set config to gnome-screensaver-command -a, which blanks the screen for me.

--

The next step is getting this configuration in action. First, restart lircd.

```
 $ sudo killall lircd
$ sudo lircd --driver=audio_alsa -d hw@48000
```

Finally, to put the configuration in action, start irexec

```
 $ irexec -d
```

Start the apps you configured, have a play around!

[SIZE="4"]**Step 7: Finishing up**[/SIZE]

You probably don't want stupid beeping whenever you hit a button. Go back into Volume Manager and mute line-in (DON'T mute capture or switch the capture device). 

Also, running all those commands is a hassle, so:

```
 $ gksudo gedit
```
Enter:
```
#!/bin/bash
lircd --driver=audio_alsa -d hw@48000
```
Save this as "lirc" (without the quotes) in /etc/init.d/
Exit gedit, then:
```
$ cd /etc/init.d
$ sudo update-rc.d lirc defaults
$ sudo chmod +x lirc

```

That starts lircd on boot (as root). You can't put irexec in there because that needs to be run as your user. Add that to your GNOME startup (System > Preferences > Sessions).

You're all done! No compiling, nothing! I'd do this over buying a receiver any day! :)

---

### Post by segalion on 2007-08-26
Wow!!!
Great howto!!! Thats what I was searching a long...

I have connected directly the "Remote Interactive" interface of my "Onkyo AV Receiver TX-SR501E" jack2jack over the mic input (no IR circuit. Only the simplest cable).
I dont know if this is tipical in Onkyo AV Receivers or even in other products (tipical video-senders...)

Notes:
- First of all I had to run...
>sudo lircd --driver=audio_alsa -d plughw:0,0,0
instead of only "hw"
- seems that rate is fixed to 48000 by default ( "cat /proc/asound/card0/pcm0c/sub0/hw_params"), but "@48000" dont works for me.
- I had to use mic in instead of line-in (its a laptop) in Volume Manager.
- One similar remote conf for me was [http://lirc.sourceforge.net/remotes/onkyo/Remote_Interactive](http://lirc.sourceforge.net/remotes/onkyo/Remote_Interactive)
- The final step 7 is not necesary in feisty, due you have a /etc/init.d/lirc file. I had to set DRIVER="audio_alsa" and DEVICE="plughw0,0,0" in /etc/lirc/hardware.conf
That's 
>sudo nano /etc/lirc/hardware.conf 
to edit config args
and 
>sudo /etc/init.d/lirc [start|stop|restart] 
to start or stop service (the natural ubuntu fashion for services)


And this work fantastic!!!
Next time I will explain my configurations...


[B][COLOR="Red"]To rest of people. Inform that this let control your linux machine with every infrared control you have in house (old tv, etc...)
[/COLOR][/B]

One question for StormX:
Do you know if I could begin with simplest circuit?
[http://www.lirc.org/ir-audio.html](http://www.lirc.org/ir-audio.html)

---

### Post by segalion on 2007-09-11
I recomend to use irxevent 
[http://www.lirc.org/html/irxevent.html](http://www.lirc.org/html/irxevent.html)
in same way that irexec

irexec for execute commands
irxevent for send keystrokes and mouse events to X

# i.e making the dvd-rigth remote button to emulate key Right keyboard key (widely usable)

begin
        prog = irxevent
        button = DVD_CursorRight
        config = Key Right CurrentWindow
end
#i.e. DVDmenu to reach ubuntu menu desktop
begin
        prog = irxevent
        button = DVD_Menu
        config = Key ctrl-F1 RootWindow
end

in $HOME/.lircrc file

---

### Post by praveen_p on 2007-12-22
Hi,

When I run irw, it ends straight away so I started lircd with -n option and I got the following errors. Could you please help me to solve this? I googled with the error message "ALSA function snd_pcm_hw_params_set_format returned error: Invalid argument" but no luck so far. Sorry I'm new to Linux. I'm running Ubuntu 7.10 and lircd 0.8.2

praveen@ubuntu:/$ sudo lircd -n --driver=audio_alsa -d hw@48000
lircd-0.8.2[7052]: lircd(userspace) ready
lircd-0.8.2[7052]: accepted new client on /dev/lircd
lircd-0.8.2[7052]: ALSA function snd_pcm_hw_params_set_format returned error: Invalid argument
lircd-0.8.2[7052]: hw_params_set_format: Success
lircd-0.8.2[7052]: caught signal
Terminated
praveen@ubuntu:/$ 

Thanks for your help,
Warm Regards
Praveen.

---

### Post by segalion on 2008-01-09
maybe:

lircd --driver=audio_alsa -d plughw:0,0,0

changing 0,0,0 for your microphone alsa port.

---

### Post by eschvoca on 2009-11-18
Hi,

Great guide.  To simplify the circuit I decided to use the tip of the audio connector to carry the power (5V) by removing a resistor on the left channel of my sound card to open the circuit and then wiring up the left channel pin to a 5 V pin on the game port (all pins on two sides of the game port are 5V).  Then I cut the other end of the cable and soldered on the IR module (out=right, Vdd=left, ground=ground) and sealed the end with liquid electrical tape.  Now I can just plug it in with a regular stereo plug.

The IR module has a 80k pull-up and the input of the sound card is 10k so the voltage gets stepped down to 1/9th which is OK.  Otherwise I would add a 20k resistor from the left pin to a ground pin to step down the voltage.  (Note I actually used a 100 Ohm resistor to connect left to power for a safety to prevent frying something in case someone plugs something else into the port.  I also put a 4.7 pF capacitor between the left pin and ground to prevent ripple on the 5 V going to the IR module.)

It all works fine and is only about a 10 minute mod.  To configure you have to specify to use the right channel (default is left) like so:

REMOTE_DEVICE="hw@8000,r"

Where the ",r" represents the right channel.

My problem is that the duty cycle is at about 40% (instead of 50%) and the "zero" voltage isn't (max-min)/2.  

To fix the zeroing problem I edited daemons/hw_audio_alsa.c:

```

                        /* Track signal middle value (it could differ from 0x80) */
-                       sz = (signal_min + signal_max) / 2;
+                       sz = 0x80;

```


Since my steady voltage was at 0 V.  To fix the timing problem I reasoned that if you know the protocol then you can snap the pulses to the right times and clean up the signal.  So to test out this theory I chose to snap to 50 by doing this:

```

                                write (alsa_hw.fd, %u,)\n", x);
+                               x = round(x/50.0)*50;
                                write (alsa_hw.fd, &x, sizeof (x));


```

But then when I run "./mode2 -d hw@8000,r -H audio_alsa" I get:

```

...
pulse 534
space 800
pulse 934
space 300
pulse 534
space 300
pulse 534
space 300
pulse 534
space 300
pulse 584
...

```

So you can see that only the "space" values are rounded to 50.  If I could figure out how to round the "pulse" too then it would be pretty easy to enter the correct rounding value and have all your timings come out perfectly for a given [protocol]("http://www.sbprojects.com/knowledge/ir/rc6.htm").  An advanced mode could parse lircd.conf and see what protocol you are using and then determine the best way to clean up the signal.

Anybody have any ideas on how the pulse time can be modified?

Thanks.

---

### Post by pwhalley on 2009-11-30
Greetings all:

I hope this request fits in here.  Sorry if it doesn't - point me in the right direction...

I have spent very many hours trying to resolve this problem ( actually 2 - problems - not hours).

I have an AR3610 nettop that I am working on getting functioning as a media center pc.

I have loaded ubuntu 9.10 on for now using wubi.  I wanted to be able to load and test various applications prior to deciding on my final config.  In addition I need to get  properly functioning remote(S) working fully.  This brings us to the problem(S).

I have an  old ATI USB RF remote that I can use for now.  I need to work on matching up buttons to functions AFTER I have it working completely in LIRC.  This will of course be true for any rmt and I think I can handle this fairly ok.

I also have a large number of other remotes that I would like the option to use for many purposes.  Ultimately I will probably need several remotes configured and handled by one box ( not necessarily the nettop) but it makes sense for me to use this as the testbed for the moment.  I want to test using the audio-alsa driver.

Another complicating factor is that the nettop came with a wireless kbd & mouse connected via USB dongle.  This is picked up by the gui remote setup pgm that I tried from the repos.  It is picked up first and the pgm appears not to be smart enough to handle more than one 'device'.  Furthermore the two device/methods I am using don't appear to be accounted for in this pgm.  If they were, I might get some insights into some of the answers I am looking for.

I have tested the hardware and it works.  I had the ati rmt working sort of but I think I have broken the lirc config for it by now.  I have also tested my homebrew audio-alsa setup and get good waveforms on xoscope.  From this test I learned that I need to use the "-r" channel.  I have seen some remarks that say alsa defaults to "l".

I am trying to make sense of the /etc/lirc/hardware.conf file since I think I need to modify it to get LIRC to work.

My questions I think are fairly simple:


[LIST]
[*]I don't undersand the distinction between REMOTE_MODULES=" ",  REMOTE_DRIVER=" ", and REMOTE_DEVICE=" ".   Can someone point me to a differentiating explanation?
[/LIST]

[LIST]
[*]A second part to the question above is where can I find a listing of modules, drivers, and devices with an explanation of what each supports?  I can't be confident that I am putting the right thing in the right place...
[*]How / where do I pass the info like -l selector for the left channel?  And, can I force conditioning on the hardware to unmute input to capture, set gain, mute output, etc?
[/LIST]
 
[LIST]
[*]For my case, I have the ATI rmt on the atiusb interface and for now, just a Hauppauge remote configured to use the homebrew alsa interface.  Since I have two different interfaces needing two different drivers using two (for the moment) different controls,  how do I specify this in the hardware.conf file?  Separate lines or do I put each driver one after the other in the same line?  In the section I inlcude,  you will see I was trying to use multiple lines but this dosn't make sense to me...
[/LIST]

If I can find these answers, I think I will be able to deduce most of what I need to do where in order to get everything working.

This is a portion of my butchered hardware.conf.  I am confident this is a disaster atm but with a few answers...
```


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
# need to make certain this is the correct ati remote 
#REMOTE="ATI/NVidia/X10 RF Remote (userspace)"
REMOTE="ATIUSB_5000015900A"
# next line needs to be the hauppauge remote entry somehow
REMOTE="Hauppauge"
REMOTE_MODULES="lirc_atiusb"
#REMOTE_MODULES=""
REMOTE_DRIVER="default"
#trying to add a driver for incoming ir from microphone audio 
#REMOTE_DRIVER="audio-alsa -d hw@48000 -r"

# REMOTE_DEVICE=""
# next line added pw for audio input for ir sig. on right channel 
# REMOTE_DEVICE="hw@48000 -r"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="''"
REMOTE_LIRCD_ARGS="''"

```I also changed lircd.conf to be:

```
# I am taking this one out because I dont think it is correct
#Configuration for the ATI/NVidia/X10 RF Remote (userspace) remote:
#include "/usr/share/lirc/remotes/atiusb/lircd.conf.atilibusb"

# I put this instead because I found what I think is the correct remote in it 
# I dont know what the difference for userspace remote means
include "/usr/share/lirc/remotes/atiusb/lircd.conf.atiusb"

#I added this one for the hauppauge remote myself
include "/usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge"

```Here, for the Hauppauge remote I found two entries in the  lircd.conf.hauppauge file with the same name.  I haven't taken the time to dig into that one yet, I just changed the name of the one that didn't match my remote to something else and assume that when lirc looks through the file it will pick up the unchanged entry as the one I wanted.
[COLOR=SeaGreen]
[/COLOR] [SIZE=3][COLOR=SeaGreen]From this:[/COLOR][/SIZE]

```

# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  [COLOR=DarkOrange]Hauppauge[/COLOR]
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2
...

# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  Hauppauge
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800
...


```[SIZE=3][COLOR=SeaGreen]To this: [/COLOR][/SIZE]

```

# brand:             Hauppauge
# model:             
# supported devices: WinTV primo; WinTV pci; WinTV radio
#
# This config file will work with both homebrew receivers and 
# original Hauppauge TV cards !!!
#

begin remote

  name  [COLOR=DarkOrange]Hauppauge_trying_to_disable[/COLOR]
# because there is another with the same name in this file
  bits           13
  flags SHIFT_ENC
  eps            30
  aeps          100

  one           950   830
  zero          950   830
  plead         960
  gap          89584
  repeat_bit      2
....


# this config file was automatically generated
# using lirc-0.8.3pre1(default) on Sat Jun 21 12:36:46 2008
#
# contributed by Matthew Wright
#
# brand:  Hauppauge (HRV-1600 RT Remote)
# model no. of remote control: A415-HPG-A
# devices being controlled by this remote:
#

begin remote

  name  [COLOR=DarkOrange]Hauppauge[/COLOR]
  bits           13
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           919   852
  zero          919   852
  plead         930
  gap          112908
  toggle_bit_mask 0x800
...

```

Thanks to all who take the time to read and especially to any who reply.

Peter

---

### Post by morten_ on 2010-02-11
How dee,
 
I have a Bose Lifestyle 48 system controlled by an RF remote however there is an IR(-blaster?) out so that DVD players, PVR's etc can be controlled. The IR out port is the size of a minijack and so I have connected it to mic port on pc. This seems to work; arecord returns gobbledegook on button press and 

irrecord -H audio_alsa -d hw@8000,0 <file>

works up to the point of registering buttons then it fails. Something about range, is there a device that I can set on the Bose system that lends itself better to LIRC (and XBMC Live)?

Also, I cannot get irw to return anything, nor do I have any /dev/lirc* or /dev/lirc/* devices after /etc/init.d/lirc start. There is however, a /dev/lircd but 

irrecord -d /dev/lircd <output file> 

does not get anything when buttons are pushed on the remote. I have tried several /etc/lirc/hardware.conf's: Any pointers on /etc/lirc/hardware.conf ?

Running 
XBMC live (on Ubuntu Karmic, I think)
kernel 2.6.31-19-generic

Any comments or help is greatly appreciated.

Morten

Edit: I have two soundcards, using the one onboard for the mic (card0)

---

