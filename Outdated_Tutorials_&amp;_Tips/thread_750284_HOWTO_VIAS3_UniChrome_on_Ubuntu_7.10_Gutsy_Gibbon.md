---
title: "HOWTO: VIA/S3 UniChrome on Ubuntu 7.10 Gutsy Gibbon"
date: 2008-04-09
forum: Outdated Tutorials &amp; Tips
---

### Post by tjankus on 2008-04-09
Hi all,

I don't know if this is the right place to post my first words, however I can see how many people are struggling with UniChrome chipsets and I have it all made for my pc (should work on notebooks too). Be aware i'm only using Ubuntu for 4 days and i have never used linux before. So, don't blame me if anything goes terribly wrong using my advice :D

Ok, let's start with our problem.

**1. Download via drivers** from
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=110]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=110")
(if we are to believe via, it works for **CLE266, CN400, CN700, CN800, CN896, CX700(M/M2), VN800, VX700(M/M2), PM880, PN880, PM800, PN800, P4M800CE, and P4M800Pro** north bridge chips)

**2. Extract .zip file** and follow the **Readme.pdf** found inside to install.

**3.** After installing the drivers it messed up my monitor (only allowed me the maximum resolution of 1024x768@85), so this step may not be needed for you, however i had to edit xorg.conf, please follow [http://ubuntuforums.org/showthread.php?t=76387]("http://ubuntuforums.org/showthread.php?t=76387") to do that if needed.

**NOTE:** If you see a lot of modelines in the monitor section already made by via drivers - feel free to delete them. You can also try changing between 16 and 24 bit depths to see which works better for you.

**This is how the discussed part of my xorg.conf looks now:**

```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ViewSonic G8"
	Option		"DPMS"
	Modeline "1600x1200_75.00"  205.99  1600 1720 1896 2192  1200 1201 1204 1253  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"ViewSonic G8"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

Now you should have the screen resolution you want and also a working 3D (try "glxgears", don't worry about the errors, just be glad if it works at all :-)).  However if you try watching dvd, or even playing music with Rhythmbox, it will not go. Let's fix it:

**4.** Right click on the panel where it says "applications, places, system" (sorry folks, don't know how do you call this thing, menu bar ?, or smt :-)) and chose Edit Menus. Now find** "Multimedia Systems Selector"** under System => Preferences and enable it.
After doing this, go to **System => Preferences => Multimedia Systems Selector**, open the **Video tab** and change the **Default Output** from Autodetect to **X Window System (No Xv)** (might be different one for you that works, just click "Test" to find the right one).

Try opening dvd now - whoala! :-) And Wine applications works even better than normal Ubuntu software for me :D

**NOTE:** I still get some strange problems with my graphics sometimes (like a fps of 1 frame per 20 seconds for 3D :D), however a simple restart fixes everything every time. I guess, this is somehow related to mesa, not the drivers itself.

I hope i did not miss a thing, and also would like to ask you not to be angry on me if i am somewhere wrong :-) Just a beginner. Feel free to post comments if you know any better :-)

---

### Post by sofamensch on 2008-04-12
I am going to test this ASAP. Can you run Compiz?

---

### Post by Eindar on 2008-05-02
man, i want to know if it's possible to run Compiz with a VIA VN800

---

### Post by starcannon on 2008-05-03
The fully accelerated official VIA drivers are now out, and available here:
[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)
I have compiz running on a cx700 but am still working out my xorg.conf I have some nasty screen flickering and some artifacting.
I have gotten 840fps using glx gears (amazing for this gpu under linux)
Desktop Cube working:
[IMG]http://img329.imageshack.us/img329/7893/cloudcompizsa1.png[/IMG]
Oddly the screen shot does not show the flickering or artifacting problems(there is an artifact visible on the top of the cube but the stuff that really drives me nuts does not show up in the screen shot /stumped)

---

### Post by Eindar on 2008-05-04
man i have a question.
I've a Via VN800 card...which platform have i to download on the four available?

---

### Post by starcannon on 2008-05-04
> **Eindar said:**
> man i have a question.
I've a Via VN800 card...which platform have i to download on the four available?

Heres the release notes from the 2 files available for download, note there are 4 options but actually only 2 files for download.

[QUOTE=unichrome]
Supported Chipsets
==================
Target system must contain one of the following VIA Chipsets:

       CX700 family including CX700/700M/700M2 and VX700/700M/700M2
       CN700

The following chipsets might work but haven't been verified yet

       CN400
       P4M800

Please check with your system provider to determine chipset used
in your system before continue.[/QUOTE]

And heres the ones from the
[QUOTE=chrom9]
Supported Chipsets
==================
Target system must contain one of the following VIA Chipsets:
       CN896, P4M900
Please check with your system provider to determine VIA Chipset used in your system.[/QUOTE]

---

### Post by Eindar on 2008-05-04
pal, first of all thanks for paying attention to this noob here :KS
but so it means that none of the two files is suitable for my VN800 ?
you think that drivers will come further for my card?

---

### Post by starcannon on 2008-05-04
VIA support looks promising, but am uncertain how much to expect.
I'm not a huge via fan, and only got interested in them when I messed up and bought an Everex Cloudbook.

---

### Post by Eindar on 2008-05-05
the same here...
i am very unsatisfied with via technology, looks most of the time something like obsolete.
but for error i found myself with this useless card on laptop

---

### Post by uhappo on 2008-05-12
I have K8M800-chipset in my laptop, is there any VIA-drivers for me?

---

### Post by sofamensch on 2008-05-16
> **uhappo said:**
> I have K8M800-chipset in my laptop, is there any VIA-drivers for me?

Same issue here. Seems like we have almost no chance.
But there is a way if ya got some time i guess x)
[http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/articulos/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

---

### Post by lordwalsh on 2008-06-17
i installed both of the VIA drivers recommended on the VIA website linked above for my brand new hp compact mini note and it didn't help my problem. ever since i installed ubuntu over SUSE I have had red blurs like my screen is overheating. I think the color depth is %^&^ up. If anyone has any ideas I would love to here them

---

