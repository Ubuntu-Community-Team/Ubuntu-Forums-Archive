---
title: "Unable to play .dat files"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by eternalnewbee on 2008-10-22
Hi there.
I'm trying to play a vcd with the extension avseq01.dat.
Can anyone tell me how to make it work?
Thanks.

---

### Post by sethvath on 2008-10-22
Dat files are vcd video files in mpeg-1/2 format. Mplayer or vlc will be able to play them

---

### Post by eternalnewbee on 2008-10-22
But they don't.
Although I have to say on my computer I have no problems. ( this is me mom's computer )

---

### Post by sethvath on 2008-10-22
She is on ubuntu? 

Try changing the format from .dat to .mpg/.mpeg and playing in vlc. If that does not work convert the file to avi with ffmpeg or any vidconverter

---

### Post by eternalnewbee on 2008-10-22
Yep, and she's celebrating her 60th birthday in two months...
Thanks for the tip, but could you please tell me how to do that?

---

### Post by sethvath on 2008-10-22
She might be missing the ubuntu-restricted-extras package and medibuntu repo. Get that and the w32codecs while you're at it. 

If nothing works, search synaptic for a video converter.

---

### Post by eternalnewbee on 2008-10-22
OK. Thanks.

---

### Post by Rhubarb on 2008-10-22
You could try pressing F2 on the File (to rename it), delete the .dat extension and put in .mpg
See if that works.

---

### Post by eternalnewbee on 2008-10-22
Can't copy to my hard drive. See attachment

---

### Post by MKdx on 2008-10-22
The CD is probably scratched, so the copy process can't read all data, but you still might be able to play it on the CD itself.

Try this in terminal to see the message:
```
mplayer avseq01.dat
```

---

### Post by eternalnewbee on 2008-10-22
I'm at my own computer again, but I'll try that when I get there. Btw., I doubt the problem is caused by a scratch, as i can play the cd just fine on my computer, and anyways she can't play any cd's. But thanks again for your advice.

---

### Post by eternalnewbee on 2008-10-23
That didn't work.

---

### Post by Dynamo_Joe on 2008-10-23
Hi eternalnewbee, 

Install VCDRip/VCDimager from the repos and use:

> vcdrip

in a terminal and it will start to transfer the DAT file to your HD as a MPG file. 

Type: 

> info vcdrip

for more options.

---

### Post by eternalnewbee on 2008-10-23
Hi there Dynamo_Joe.
Sorry for my late reply ( no internet connection ).
I installed vdc/imager and ran the command vcdrip, but got the message  command not found. Then I ran the command info vcdrip and got this:
What to do next?

---

### Post by Dynamo_Joe on 2008-10-24
Sorry, eternalnewbee ... my bad, spelling mistake! 

The man pages are here: 

[http://linux.die.net/man/1/vcdxrip]("http://linux.die.net/man/1/vcdxrip")

1. Put the VCD into your optical drive. 
2. Open a terminal and type: 

> vcdxrip

3. It will (automatically) find the drive with the disk in it and start copying the DAT file over to your HD with an MPG extension. 

NOTE: Depending on where your were last (that is, in your "home" folder) when you started vcxrip, the MPG will be placed in that directory. 

Once again, apologies for the typo and late reply.

---

### Post by eternalnewbee on 2008-10-24
I'll try that Dynamo_Joe. Unfortunately I'm not at my parents now but will try soon.
Btw. this only solves part of the problem. I should be able to play directly form the cd instead of copying to the hard drive...

---

### Post by medic2000 on 2008-10-24
In vlc or smplayer there is an option "Open VCD". Use it.

---

### Post by eternalnewbee on 2008-10-24
It doesn't work...

---

### Post by Dynamo_Joe on 2008-10-25
Hi eternalnewbee, 

Not very good with forums and still learning how to set preferences ... :) 

Understand your situation ... VCD support was never great after Dapper, yes, Dapper played VCDs "out of the box" but like I mentioned earlier in another post on another thread, I haven't had time to sort out my Dapper installation (it's still on a 10GB HD somewhere in the study). 

Back to your problem, understand that you wish to make it simple for your mother (she is 60) and ideally the media player should start automatically whenever she inserts a VCD into the optical drive. 

Some have suggested amending the command in totem (if you google, you'll find you're not the only one with this problem) but it never worked for me. 

Sorry if I can't be much more of a help.

---

### Post by Dynamo_Joe on 2008-10-25
Hi eternalnewbee, 

This thread maybe of help: 

[http://ubuntuforums.org/showthread.php?t=906110&highlight=vcd]("http://ubuntuforums.org/showthread.php?t=906110&highlight=vcd")

---

### Post by eternalnewbee on 2008-10-27
Didn't work. The solutions from the threads did not apply to this computer. I had already tried them.
Bump.
EDIT: the command vcdxrip seemed to work, but this was the end result:
<!-- command line used: vcdxrip -->
&#8722;
<videocd class="vcd" version="2.0">
&#8722;
<info>
<album-id/>
<volume-count>1</volume-count>
<volume-number>1</volume-number>
<restriction>0</restriction>
</info>
&#8722;
<pvd>
<volume-id>New VideoCD 2.0</volume-id>
<system-id>CD-RTOS CD-BRIDGE</system-id>
<application-id>VOB InstantVideo</application-id>
<preparer-id/>
<publisher-id>The Netmech</publisher-id>
</pvd>
&#8722;
<filesystem>
&#8722;
<folder>
<name>CDI</name>
</folder>
</filesystem>
&#8722;
<sequence-items>
&#8722;
<sequence-item src="avseq01.mpg" id="sequence-00">
<default-entry id="entry-000"/>
</sequence-item>
</sequence-items>
</videocd>

---

### Post by eternalnewbee on 2008-10-28
Bump...

---

