---
title: "lirc 0.8.4 on intrepid"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by danilo74 on 2008-11-06
I'd like to install lirc 0.8.4 on intrepid (Ubuntu 8.10). Unfortunately it is not available in Synaptic.

I had a look on the lirc website and googled a bit but I couldn't find instructions for the installation.

Does someone have useful link or can explain me how to do it?

Thanks!

Danilo

---

### Post by NT4usB on 2008-11-06
Here's instructions I used a hundred years ago, to install lirc on Dapper. Scroll down to step 7. Remote Control (LIRC). Gotta be something newer out there though...
[http://hyams.webhop.net/MythTV/myth_ubuntu.html](http://hyams.webhop.net/MythTV/myth_ubuntu.html)

---

### Post by fooman on 2008-11-06
did you extract the file and look in there?

...download the file and right-click on it.  choose "extract here" from the drop down menu.  there will be an "install" file in there with the installation/compile instructions.  have a read there and post back with any more questions.

btw...0.8.3 is available from synaptic (much easier install).

---

### Post by danilo74 on 2008-11-07
Hi guys,

thanks to both of you for the very quick reply. I tried the link but it didn't help.

The reason I want to try the 0.8.4 version is that I have a PC in an Antec Fusion Black case that comes with a remote control (SoundGraph 15c2:0038), LCd screen and a volume knob.

I've found instructions to make it working in hardy here

[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

I followed the instruction (with poor understanding of what I was doing) and it worked as described but unfortunately after updating to intrepid it doesn't work anymore.

Then I've tried to remove all the lirc related files and install the 0.8.3 version that comes in synaptic. In principle this version includes the patch I've used to make the remote and LCD working in hardy but after installation I can't see in the /dev/ folder the /lirc0 and /lirc1 files I used to have with hardy.

Browsing a bit more I found that there were still some problems with the 0.8.3 version that apparently are solved in the 0.8.4 version. So I gave it a try but unsuccessfully.

Obviously I can reinstall hardy and stick with it but I was trying to find another solution before doing that and maybe understanding a bit more how lirc works.

I agree anyway that 0.8.3 is much much easier to install!
Simply it doesn't work as expected and I have no idea how troubleshooting it.

---

### Post by mdalacu on 2008-11-11
Did you find something new, i have exactly the same hardware and problem :) The diffrence it's that i've broke my system trying. :( . Had to reinstall everything, but no success until now.

---

### Post by fastie81 on 2008-12-14
hi guys

Ok I have got it working with the 0.8.3 driver.. 
have a look here.. it is just a draft pointing to the site but the is my highlights for 8.10
Like I said I got it working and the LCD.
I know the 0.8.4a looks like have the support now so no need to patch but until we get an easy install I think this is much easier.
good luck and let me know if I can help more.
C
[http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote?pli=1](http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote?pli=1)

---

### Post by Cuppa-Chino on 2009-01-04
> **fastie81 said:**
> hi guys

Ok I have got it working with the 0.8.3 driver.. 
have a look here.. it is just a draft pointing to the site but the is my highlights for 8.10
Like I said I got it working and the LCD.
I know the 0.8.4a looks like have the support now so no need to patch but until we get an easy install I think this is much easier.
good luck and let me know if I can help more.
C
[http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote?pli=1](http://sites.google.com/site/it1stop/Home/linux/mythbuntu---linuxmce/lirc-remote?pli=1)

0.8.4a is available via backport, anybody got it working on on imon 0038 model? also which patch to use, they are very very different in length...

has anyone tried fastie's method on amd64 with success?

---

### Post by Dupey on 2009-01-04
Cuppa-Chino,
 
   I am using mythbuntu 8.10 with lirc 0.8.3 on amd64. I used fastie81's patch and directions and the remote works great. In irw I see returns for all keys on the remote. I am having a little trouble in mythtv but I think that is because I used the mythbuntu lircrc generator which only seems to setup the basics. I have all the basic functions but I would like to be able to use the jump keys for DVD, music, ect. 
   I have tried to setup the lcd with fastie81's dierctions but the information is a little vague. Going between the blog linked in those directions and the snippets of information provided by fastie81 I have not been able to piece it all together yet. I keep getting permission denied when I try to send the commands listed on ron's blog. To be honest I would be ok if I could just turn the back light off.
   I am going to do a clean install next week to hopefully fix an unrelated problem and will give the lcd setup a second try. Any clarification of fastie81's instructions would be very helpful.

---

### Post by Cuppa-Chino on 2009-01-05
hi dupey,

I am currently also at the same place as you. I cannot access the lcd display (although oddly on a previous install it worked).

If you are getting permission errors when trying to put the perl commands in then try the following

```
$sudo su

```

this will give you proper root access, and will give you full permissions.

also remember to put the KERNEL=LIRC0...9 bit into xx-permission.rules as per the fastbie LCD page, that will control your permissions for the LIRC device

---------------------------------------------------------------------------------
if someone could also post their /etc/lirc/, their lircd.conf and hardware.conf that would be grand, because that is where I think I have gone wrong



---------------------------------------------------------------------------------

well well stupid me tried following these instructions: [http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452]("http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452")

but that seems to currently fail in the dkms step.

I am totally lost now, I cannot face wiping the hd again....

---

### Post by Cuppa-Chino on 2009-01-09
well I think I am much further but not quite there yet.
found the codeka forums and this page:
[http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452]("http://codeka.com/forums/viewtopic.php?f=3&t=23&st=0&sk=t&sd=a&start=50#p452")

that worked for me -- nb I ensured that I reinstalled a fresh lirc-modules-source before applying his 1st patch..

I followed the instructions and then the well known:
[http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html]("http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with.html")

to get LCDd responsive, I can both use the perl commands and call up LCD -f -r 4 to get responses.

I ran an mythbuntu-lirc-geneator with the provided lirc0.conf now I have partial control with the remote I will try and see if there is a way combining the two parts (lirc0.conf and lirc1.conf) to generate a full .lirc

the lcd is still only saying thanks for using LCDproc ...

---

### Post by Dupey on 2009-01-10
thanks for you suggestion cuppa-chino

I tried in using the sudo su command and it no longer says permission denied. Instead it says the device is busy. I think the problem could be that I hadn't killed all instances of lircd before running the two commands to set up the ports. I tried and was able to get 2/3 but one kept showing up, when I would try to shut it down it would say it was successful but then when I looked again it was still there, it just changed some of the numbers. I am haveing some issues with my integrated ATI video card and will probably end up reformatting after I break my xorg setup. I will give this a try on a fresh setup then.

---

### Post by Cuppa-Chino on 2009-01-10
> **Dupey said:**
> thanks for you suggestion cuppa-chino

I tried in using the sudo su command and it no longer says permission denied. Instead it says the device is busy. I think the problem could be that I hadn't killed all instances of lircd before running the two commands to set up the ports. I tried and was able to get 2/3 but one kept showing up, when I would try to shut it down it would say it was successful but then when I looked again it was still there, it just changed some of the numbers. I am haveing some issues with my integrated ATI video card and will probably end up reformatting after I break my xorg setup. I will give this a try on a fresh setup then.

dupey:
couple of things:
a) did you see I am now trying a different method from the codeka forums (slightly more sucessful)
b) you might want to install something like quickstart for convient backups: [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11]("http://quickstart.phpbb.net/viewtopic.php?f=8&t=11")

---

