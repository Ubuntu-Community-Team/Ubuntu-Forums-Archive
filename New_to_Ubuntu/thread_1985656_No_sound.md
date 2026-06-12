---
title: "No sound"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by Bachey on 2012-05-23
Hi!

I'm experiencing a possibly common problem, but still couldn't find a way to fix it. I'm using now Ubuntu 11.10(64 bit) and Windows 7 (dual OS), and the front jack panel does not have any output. 

In windows 7 it works well, so it is some kind of missing drivers.

My motherboard is: ASUS M4A785TD-V EVO, which has a built in sound card. 

Any suggestions? :popcorn:

---

### Post by donkyhotay on 2012-05-23
My first question would be, do you get sound from the rear sound ports in ubuntu?

---

### Post by Bachey on 2012-05-23
Yes, rear jack ports work very well, unlike the front headphone. :(

---

### Post by d4m1r on 2012-05-23
You mean you get no sound out of the front headphone jack under Ubuntu but you do under Windows 7 correct?

That means it is most likely is a sound setting issue under Ubuntu only, and I'd start by checking all the settings in "Sound".

---

### Post by Hadaka on 2012-05-23
I had the same thing happen last week,11.10 here also. somehow alsamixer
master was muted. at terminal   ctrl/alt/t
enter

alsamixer

good luck.

---

### Post by Bachey on 2012-05-24
I've found out that Headphone is greyed out in alsamixer, but still no idea how to enable it.
 [IMG]http://i47.tinypic.com/2qa5quc.png[/IMG]

---

### Post by Bachey on 2012-05-25
I downloaded GNOME Alsamixer, but still no luck, anyone? :(

---

### Post by Hadaka on 2012-05-25
Try using left or right arrow to highlight the headphone
then use down arrow and zero it out...then up arrow to
set the strength. I would lower the other maxed out settings
to around 75 at most...see if that helps.
good luck

---

### Post by Hadaka on 2012-05-25
If the above suggestion doesnt help, please post the out put of:


[CODE][lspci | grep -i audio/CODE]

cat /proc/asound/card0/codec* | grep Codec

thanks
oops....first command is

lspci | grep -i audio

---

### Post by Bachey on 2012-05-26
I tried that in alsamixer, but it didn't work.

"lspci | grep -i audio" output:
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)

```"cat /proc/asound/card0/codec* | grep Codec" output:
```
Codec: VIA VT1708S
```

---

### Post by Hadaka on 2012-05-26
Try this

echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf
if that doesnt work..and hopefully it will.
be sure to gedit /etc/modprobe.d/alsa-base.conf

and remove that added line.
hope this helps

---

### Post by Bachey on 2012-05-27
I ran the command, it added the line, I restarted my pc, but it still didn't work. :( I wonder what the problem is.

---

### Post by Hadaka on 2012-05-27
Its odd that everything else seems to work except the headphones and they do
work with windows. Lets take a peek at the trigger bit and see if its zero'd out.

cat /proc/asound/card0/codec* | grep -iA4 Jack

---

### Post by codingman on 2012-05-27
check in gnome alsa mixer whether the microphone is on mute

---

### Post by Hadaka on 2012-05-27
try this.

first gedit /etc/modprobe.d/alsa-base.conf
then replace
options snd-hda-intel model=asus
with
options snd-hda-intel model=m4a785td-v position_fix=0

your machine must be fairly new as your chipset was not on this list


[http://doc.ubuntu-fr.org/audio_intel_hda#acer](http://doc.ubuntu-fr.org/audio_intel_hda#acer)

so you may have to experiment and change the model= "X"
go slow..be patient.  and reboot after each attempt.

---

### Post by Bachey on 2012-05-27
Output of that code: 
```
Pin Default 0x01011012: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x01a19036: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x6
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x0181303e: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x3, Sequence = 0xe
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=21, enabled=1
--
  Pin Default 0x02a19038: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x3, Sequence = 0x8
  Pin-ctls: 0x21: IN VREF_50
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x074311f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = ATAPI, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
--
  Pin Default 0x074521f0: [Jack] SPDIF Out at Ext Rear Panel
    Conn = Optical, Color = Grey
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
--
  Pin Default 0x01016011: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=20, enabled=1
--
  Pin Default 0x01012014: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=20, enabled=1
```In gnome alsamixer microphone is not muted, and I also changed the alsa configuration as you recommended, but still no luck. However I hear a little tick sound in my headphone at bootup, but later it is mute. (It's not a hardware problem, because it still works under windows)

---

### Post by Hadaka on 2012-05-27
I think i see the problem. notice how every thing else is tag20..except HP
HP is the headphone. change that to 20 instead of 21 and see if that fixes it.

 Pin Default 0x0221401f: [Jack] HP Out at Ext Front     Conn = 1/8, Color = Green     DefAssociation = 0x1, Sequence = 0xf   Pin-ctls: 0xc0: OUT HP VREF_HIZ   Unsolicited: tag=21, enabled=1 --   Pin Default 0x02a19038: [Jack] Mic at Ext Front     Conn = 1/8, Color = Pink     DefAssociation = 0x3, Sequence = 0x8   Pin-ctls: 0x21: IN VREF_50   Unsolicited: tag=20, enabled=1

---

### Post by Hadaka on 2012-05-27
sorry about the jumbeled mess i posted..i copied and pasted some of your 
output and it strung it all together. I built a quick file from you last post 
of settings and then grep'd it for "tag values"

Unsolicited: tag=20, enabled=1
  Unsolicited: tag=20, enabled=1
  Unsolicited: tag=20, enabled=1
  Unsolicited: tag=20, enabled=1
  Unsolicited: tag=21, enabled=1
  Unsolicited: tag=20, enabled=1
  Unsolicited: tag=20, enabled=1
  Unsolicited: tag=20, enabled=1
this was the result...and the only tag 21 is the HP tag.
this has been interesting...i hope this is the fix let me know.

---

### Post by Bachey on 2012-05-28
Thanks, now i get what the problem is. :) But well, I'm kinda noob, how do I change it?

---

### Post by Hadaka on 2012-05-28
sorry about just now getting back to you...mem day and all..got busy.
anyway. after looking at the settings in my system..im not so sure that 21 tag in yours is the problem. From all the research ive done on this..it seems to be an old bug..but only with 64bit not 32. and the fix was getting the correct model and position_fix=
values correct. so before you attempt to change that tag value lets try a different
fix= value..its going to be 0,1 or 2 so you will have to experiment..it should be currently
set at 0.

thus far you entered.  

1.  #"options snd-hda-intel model=asus"# 
2.  #"options snd-hda-intel model=m4a785td-v position_fix=0"#

try to gedit  /etc/modprobe.d/alsa-base.conf

again and remove the first line...if its still there
then change     options snd-hda-intel model=m4a785td-v position_fix=0
to:                       options snd-hda-intel model=auto position_fix=1

reboot and test....if it doesnt work change it to fix=2
you can also experiment and change the model to ..asus...m4a....785 and try each fix=
value....0,1 or 2 with each model change. Its going to take a little time and may be a
bit frustrating but there is no simple fix i can find...so be patient,take your time.

---

### Post by Bachey on 2012-05-29
Hi! I tried: 

options snd-hda-intel model=asus position_fix=0
options snd-hda-intel model=asus position_fix=1
options snd-hda-intel model=asus position_fix=2
options snd-hda-intel model=m4a785td-v position_fix=0
options snd-hda-intel model=m4a785td-v position_fix=1
options snd-hda-intel model=m4a785td-v position_fix=2

None of them worked, and for value 2 in position fix for both m4a..td and asus got worse, so I just set it back to 0. currently: "options snd-hda-intel model=m4a785td-v position_fix=0"

I'm getting a little afraid, why so hard to fix? :O

---

### Post by Bachey on 2012-05-30
Does this mean my problem is unfixable?

---

### Post by Hadaka on 2012-05-30
Its fixable..and i have been chasing the wrong number,i was looking for
the model number you gave me. but..i found you have the x5dab 1708
chipset. try one more time with the model = and fix=
this time say model = auto and fix =1
if that doesnt work..let me know and i will send you the only link
i have for a different possible fix.  thanks

---

### Post by Hadaka on 2012-05-30
incase you are curious how i came up with the different model number,
you actually gave it to me and i overlooked it. while your mother board
is the M4a785 the built on  sound card also has its own number.
If you look at ...alsamixer...the 1708 number is upper left..chipset vt1708s
and i asked you to show the results of command ....

cat /proc/asound/card0/codec* | grep Codec
it also came back vt1708s...that is here on this thread.
then i went to the link i posted earlier and it shows the Asus chipset as 1708s
model number X5DAB. and of no direct command line fix...just another link
to fixes for that sound card...but no "headphone" not working example.
you might also try this link from ubuntu Asus forum.

[http://ubuntuforums.org/showthread.php?t=1685073](http://ubuntuforums.org/showthread.php?t=1685073)
thanks.

it is for headphones not working..and has a possible fix.

---

### Post by Bachey on 2012-06-04
I tried model=auto with fix 0,1,2 and the result is still the same, I also found this: [http://yamz.wordpress.com/2010/06/11/front-panel-audio-jack/](http://yamz.wordpress.com/2010/06/11/front-panel-audio-jack/), and it is also the same. 
Still no solution for my problem. :( But thanks for your help.

---

### Post by Hadaka on 2012-06-04
Glad to see you havent lost hope. I just spent 3 days unwinding a mess from
a 12.4 load,so i can relate to the frustration. I found a post with the exact
chip 1708 and same problems you are having..and the trys with the fix= routine.
he spent 3 weeks and finally found the fix at.

 [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

take a read and see what you think.

---

### Post by Bachey on 2012-06-07
Or I should simply upgrade to 12.04 LTS, IF there's a solution to fix this: [http://ubuntuforums.org/showthread.php?t=1976859](http://ubuntuforums.org/showthread.php?t=1976859) . There the sound works perfect, however I cannot watch 3D movies unlike in 11.10 (which I'm currently using). looks like there's always a problem to face. :D

---

### Post by Hadaka on 2012-06-07
one question i havent asked is...did the headphones ever work using 11.10?

also i spent some considerable time looking for any kind of answer for your VT1708s
chip. Seems there are alot of different PC's out there, different models,manufactures
and types that have the same issue. 

This is a file in the alsa documents that lists massive amount of info on drivers and
what should be the correct input for model= and fix= values. Getting those correct
should fix your problem. I ran this file and couldnt find VT1708, but was able to get
data with Asus. My Alsa mixer version is differnt than yours so perhaps you will get
what you need with VT1708 search on this file.

code:

touch 1708

zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz > 1708

grep -iA5 asus 1708
---------------------------------
or grep VT, your computer model,1708,x5dab ANYTHING that relates to your sound
card.
I also read some blurb about a switch for the headphone...i dont know if it was
a physical hardware or software switch,the poster wasnt clear.  You also might try
loading the 12.4 in "try without really loading" and see what the settings are in the
alsa config file.  Hope this helps.

---

### Post by Hadaka on 2012-06-07
also would you please look at this other Alsa documents file and see if there
is anything at all that relates to your computer..model name of computer,
description of sound output locations..anything. thanks
terminal command. ctrl/alt/t

code:

zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt

note: to navigate the file..arrow down for next line
           and then   q    to quit...followed by exit. for both document txt files.

---

### Post by Bachey on 2012-08-14
I still did not manage to fix it, however I don't need it now, I'm using my laptop. Thank you anyways. :)

---

