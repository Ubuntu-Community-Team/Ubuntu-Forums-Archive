---
title: "startup troubles after lm-sensors"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Stefanie on 2008-05-03
i installed lm-sensors and sensors-detect to check my cpu temperature. i followed some howto's, but sudo sensor-detect kept saying that my sensors couldn't be detected. in the end i gave up and uninstalled lm-sensors and sensors-detect. 

On this forum and on other sites i read something about people being unable to startup after experiencing problems with lm-sensors: [http://ubuntuforums.org/showthread.php?t=505151](http://ubuntuforums.org/showthread.php?t=505151)

So I decided to reboot to see if everything was ok. During startup, however, i got a weird screen i've never seen before:
[IMG]http://i31.tinypic.com/4twsj8.jpg[/IMG]

in the end the sda3 check completed and to my relief the computer started up normally.

now i wonder what those invalid kernel operations are and if this weird screen will show up every time i restart. is there a problem?

---

### Post by Stefanie on 2008-05-03
my laptop is a DELL latitude D510, 1gig RAM, and i'm running ubuntu 7.10. 
the screen showed up after the ubuntu loading screen.

---

### Post by MattBD on 2008-05-03
It's OK, I think that's fine. Every now and then, Ubuntu checks the filesystem to make sure it's not corrupted (it's something like every 30th time you boot up). It's nothing to worry about - if you reboot again, you shouldn't see it.

---

### Post by Stefanie on 2008-05-03
and what about those invalid kernel operations?
just 2 secs after my previous post i started kile en ubuntu suddenly logged out... i logged back in again and i only saw my desktop, nothing else. nothing happened at all for more than 5 mins so i powered off my laptop and i rebooted. i didn't see the screen again and everything seems to be ok now, but i'm still a bit worried... :-?

---

### Post by MattBD on 2008-05-03
Don't think the invalid kernel operations are anything to worry about. If you enter the following to completely remove lm-sensors and sensors-detect:
```
sudo apt-get purge lm-sensors sensors-detect
```
That will get rid of the configuration files for lm-sensors and sensors-detect completely, so hopefully that should resolve any issues caused by those two packages. If not, that thread you mentioned looks like it would be the best place to start.

---

### Post by Stefanie on 2008-05-03
i already completely removed lm-sensors and sensors-detect (not with the purge command but with the complete removal option in synaptic). so i guess the invalid kernel operations are not related to those two packages, but to something else. has anyone got an idea?

MattBD thanks for your help!

---

### Post by Paqman on 2008-05-03
Which bit are you worried about, the invalid operations, or the disk check of sda3?

If you upgrade to Hardy the disk check will look a lot nicer, and you'll have the option to abort it by pressing ESC.

---

### Post by Stefanie on 2008-05-03
the invalid kernel operations are worrying me a bit, yes.

about hardy, i'll upgrade in a month or two when the major bugs are fixed and firefox 3 is released ;-)

---

### Post by WitchCraft on 2008-05-03
> **Stefanie said:**
> 
the invalid kernel operations are worrying me a bit, yes.

about hardy, i'll upgrade in a month or two when the major bugs are fixed and firefox 3 is released ;-)


The kernel searches in the configuration file:
/etc/udev/rules.d/gpib.rules


There are errors on line 1 and 2. 
Since this file is an empty file on my computer, it's likely that on line 1 and 2, the configuration files for your sensors were referenced.

Now, when you removed the sensor package, those configuration files got removed, but the references in /etc/udev/rules.d/gpib.rules remained.
(This is a common practice, since it's not that safe to remove lines from a file you don't know what it looks like; though it might also be an omission error).

Consequently, the kernel searches for configuration files that don't exist, and outputs an error notification.

So far nothing to worry about, since the kernel does not stop if a configuration file is not found, as you can see.

And you only saw this error anyway, because you booted in console mode, because your operating system did an automatic integrity check on your file system, which it does every 30 times you boot up. But that was just a scary coincidence in your case.

You could go to /etc/ and then do
```

gedit /etc/udev/rules.d/gpib.rules

```

And look what exactly is on line 1 & 2, and correct it.

However, I would recommend you NOT to do this, since everything will also work fine if you don't do this. And since you're posting in the absolute beginner's forum, you probably aren't aware of all the little details, so you shouldn't risk screwing up your system by doing something that isn't necessary...

You can adjust the frequency of the integrity checks, by doing:
tune2fs.
Of course, if you don't run your system as root, you need to sudo.

hda1 is the first partition of the first internal hard disk
sdb1 is the first partition of the first external USB disk
hda are all partitions on the first internal hard disk
```

# Tell the system to only check the filesystem every 60 days
sudo tune2fs -c 60 /dev/hda1
#  Tell the system to NEVER check the filesystem (not good)
sudo tune2fs -c 0 /dev/sdb1
# Not checking the filesystem in general, but setting an interval to at least check once a month
sudo tune2fs -c 0 -i 1m /dev/hda

```


PS: Next time you read that you might having problems restarting your computer afterwards, the better reaction is to immediately make a backup copy of your data, and not immediately restarting to see whether this is true or not - unless you like Russian Roulette... FYI


Regards 

Stefan

---

### Post by Stefanie on 2008-05-03
Thanks a lot!!! I am indeed a beginner, I've been using ubuntu for only 2 weeks now, but I really want to learn as much as I can about linux and ubuntu. 

It was indeed a scary coincidence, after reading about those booting problems. I opened /etc/udev/rules.d/gpib.rules and there were indeed 2 lines in this file:
```
KERNEL="gpib/*",	MODE="0660", GROUP="gpib"
KERNEL="gpib[0-9]*",	MODE="0660", GROUP="gpib"
```

I didn't delete those entries, as you told me not to. 

Oh yes, don't worry, I made sure I had a backup of my important data before rebooting. I also had the live CD and a windows partition, so in case of problems it wouldn't have been a total disaster. But I was a little bit stressed, I'm writing my MA thesis right now and the idea of having to write the rest of it in Windows wasn't exactly a happy one :-)

Now I hope I find another tool to check the temperature of my CPU... My laptop was getting a bit hot, that's why I installed lm-sensors in the first place.

---

### Post by WitchCraft on 2008-05-04
> **Stefanie said:**
> 
I opened /etc/udev/rules.d/gpib.rules and there were indeed 2 lines in this file:
```
KERNEL="gpib/*",	MODE="0660", GROUP="gpib"
KERNEL="gpib[0-9]*",	MODE="0660", GROUP="gpib"
```

I didn't delete those entries, as you told me not to. 


Mmh, these are kernel configuration files for gpib device drivers (usb).
Correct syntax would be:
```

ACTION=="add", KERNEL=="gpib/*",        MODE="0660", GROUP="gpib"
ACTION=="add", KERNEL=="gpib[0-9]*",    MODE="0660", GROUP="gpib"

```


```

Now I hope I find another tool to check the temperature of my CPU... My laptop was getting a bit hot, that's why I installed lm-sensors in the first place.

```

Since you say you're using a Laptop:
This is superfluous: Most Laptops come with an Intel processors which have built-in sensors, that first slow it down, and if that doesn't help switch it off if the processor becomes too hot... I saw this screen once, when attaching my Laptop to the power source in a train... Makes your screen black, and says your computer has been shut down because your processor got too hot, stays there for 5 seconds, then powers off... Non-saved data is lost. Non-the-less a very good thing.
Well, I hope you aren't using an AMD processor, because if so, you aren't that lucky, because AMD is "Made in Europe: cheaper, more efficient - better" - or in short: doesn't have built in sensors...

BTW, to find out what processor you're using:
```

root@all:~# cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.70GHz
stepping	: 8
cpu MHz		: 600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips	: 1198.39
clflush size	: 64

root@all:~# 

```

> 
I'm writing my MA thesis right now and the idea of having to write the rest of it in Windows wasn't exactly a happy one :-)


If the question is allowed: MA in what ?

---

### Post by Stefanie on 2008-05-04
MA in linguistics :-)

should i change those entries, then?

My processor is an Intel celeron 1.40 GHz.
Thanks for all your help!

---

### Post by WitchCraft on 2008-05-04
> **Stefanie said:**
> 
Should i change those entries, then?


You can. And since it is a USB driver, maybe this also solves your problem with your Wirless/USB. **But make a backup copy of that file first, so you can easily restore it in case this makes things worse, and not better**.
And note that the changes most likely won't take effect until you reboot.


> **Stefanie said:**
> 
MA in linguistics :-)


Mine was in Physics ;-)
And after the first 40 pages:
Error: This document is too complex for Word to open...
(Microsoft Word)
:lolflag:

Anyway, Good Luck !

---

### Post by Stefanie on 2008-05-04
I edited those lines and restarted, everything went fine but the wireless/usb thing is not solved. But that is in fact not a major issue. 

I think those wrong lines got in when i tried to set up syncing between my phone and ubuntu. I never entered them myself, though. 

So I guess I'll get back to my thesis now :-) Writing it in Word would be a total disaster, Word really can't handle special phonetic fonts. I'm using Kile and I don't know what I would do without it :-)

---

### Post by WitchCraft on 2008-05-04
> **Stefanie said:**
> I edited those lines and restarted, everything went fine but the wireless/usb thing is not solved. But that is in fact not a major issue. 

I think those wrong lines got in when i tried to set up syncing between my phone and ubuntu. I never entered them myself, though. 

So I guess I'll get back to my thesis now :-) Writing it in Word would be a total disaster, Word really can't handle special phonetic fonts. I'm using Kile and I don't know what I would do without it :-)

Mmh, as far as I know, Word has an input editor for phonetics, i think i found it when searching for the input editor for math formulas, but it's a pain to use it, since it's all mouse based.

Anyway, I never use phonetics, and I cannot read them neither. And since most modern dictionaries have the button "speak", this has never been a problem :-)))

If you have sync problems with one program, just try another, for examle kitchensync:
[http://www.urubatan.info/2007/10/it-is-getting-easier-to-sync-your-cell-phone-with-your-linux-box/](http://www.urubatan.info/2007/10/it-is-getting-easier-to-sync-your-cell-phone-with-your-linux-box/)

apt-get install kitchensync

---

### Post by Stefanie on 2008-05-04
word has indeed an input editor for phonetics, but it's a pain to use and if you manage to use it the lay-out gets completely messed up, not to mention the occasional crashes. 
several things are not supported at all or difficult to install, like an accent stretching over two vowels, dots or circles or bridges under letters, special versions of some letters ("curly" or inverted d's, n's, ...)  compared to latex it's really not worth the effort.

my syncing problem is that opensync doesn't work, it can't communicate with my phone (even not over bluetooth, the phone disconnects immediately after connecting). i've read like 50 howto's but none of them worked. kithensync uses opensync, so i don't think this will solve my problem... I will certainly give it a go, though.

---

### Post by WitchCraft on 2008-05-04
> **Stefanie said:**
> word has indeed an input editor for phonetics, but it's a pain to use and if you manage to use it the lay-out gets completely messed up, not to mention the occasional crashes. 
several things are not supported at all or difficult to install, like an accent stretching over two vowels, dots or circles or bridges under letters, special versions of some letters ("curly" or inverted d's, n's, ...)  compared to latex it's really not worth the effort.

my syncing problem is that opensync doesn't work, it can't communicate with my phone (even not over bluetooth, the phone disconnects immediately after connecting). i've read like 50 howto's but none of them worked. kithensync uses opensync, so i don't think this will solve my problem... I will certainly give it a go, though.

Hmm, well then it sounds like a driver problem.
In case you don't know, you can file a bug report at launchpad.net, in the appropriate rubrique, and then it will get reviewed. 
However, that might take a few months...

I use a multi-format card reader to read SD cards from my photo camera, with it I can read and write to the SIM card if I want to.

---

