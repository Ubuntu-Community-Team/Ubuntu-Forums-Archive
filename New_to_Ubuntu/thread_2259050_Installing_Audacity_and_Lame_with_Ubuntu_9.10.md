---
title: "Installing Audacity and Lame with Ubuntu 9.10"
date: 2015-01-01
forum: New to Ubuntu
---

### Post by willsed394 on 2015-01-01
Hi.  Not new to Ubuntu, but new to installs that are off cd or thumb drive.

some history...for several years, used ubuntu on dsl.  then moved; have no dsl, barely have internet.  had to use windows to connect to net due to system/interface limitations.  kept ubuntu 9.10 cds, but finally evolved to using 'Audacity for Windows' to record music.  Have fought software hardware problems for a long time to record; finally, Audacity for Windows solved recording issues....but...

Windows insists on registration. I will NOT log my music computer (an old Dell) onto the internet.  Eventually, Windows will crash (or just fail to save files in usable form, or even delete the tracks), and I lose tracks if not saved to thumb drive.  Decided I would give Ubuntu and Audacity a try, having been convinced of Ubuntu's stability.  So far, despite books and digging around trying things, cannot get Audacity installed into 9.10; have downloaded the latest listed version of Audacity to both thumb and cd (along with Lame), but cannot figure out how to get them installed, much less run.

I am a musician and might even call myself a songwriter; don't need a lot of electronic help to make music.  Play analogue instruments, sing and do the 'wood and string', computer functions as mixer and recorder. Don't need 'ProTools' for what I do, nor do I want increased complexity.  Long time Windows user (first computer was a commodore 64, second was a 286 IBM with early Windwoes).  I really had/have no intention of becoming a programmer/Ubuntu expert/whatever.  All I wanted was to record music tracks and not have them disappear from Windwoes.  Have even had a long look at Puppy Linux trying to get a recording setup to work, but don't have the background to make that happen.

Is there not a simple way to install audacity without hooking computer to internet using Ubuntu?  For that matter, why has no one made an os that runs Audacity and Lame, but has NO OTHER FEATURES for musicians?  Why would I want 'games', word processing, math, painting on computer? I've got all the hobby I want recording tracks.  A dedicated os for music recording would perhaps be fast, efficient, not stress the electronics and have likely almost no latency. ah, well....wish in one hand...

Thanks for any advice or ideas.  Will have to hook up the drive with Audacity for Windows again until I get this figured out. Happy New Year.

---

### Post by sudodus on 2015-01-01
Welcome to the Ubuntu Forums :-)

First of all, ***please specify your computer***

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier to give relevant help.

Second, ***Ubuntu 9.10 is long gone*** (passed end of life 2011) 
[TABLE]
[TR]
[TD="bgcolor: #762852"][COLOR=#fff0f5]**Ubuntu 9.10**[/COLOR][/TD]
[TD="bgcolor: #f1f1dd"][Karmic Koala]("https://wiki.ubuntu.com/KarmicKoala")[/TD]
[TD="bgcolor: #f1f1dd"] /[/TD]
[TD="bgcolor: #f1f1dd"]EOL[/TD]
[TD="bgcolor: #f1f1dd"][April 30, 2011]("https://lists.ubuntu.com/archives/ubuntu-announce/2011-March/000142.html")[/TD]
[/TR]
[/TABLE]

This means that very few persons, if any, are able to give good support. And the repositories with program packages are removed from the Ubuntu servers. It might still be possible to compile Audacity from source code, but I would not recommend it, because it is difficult.

Finally there are ***several security holes***, that cannot be fixed, so a computer with Ubuntu 9.10 must not be connected to the internet.

-o-

So when we know about your computer, ***we can suggest ***which*** version and flavour of Ubuntu***, or maybe a 'community re-spin', that is likely to work well for you. Getting a current and supported version, it is *very easy* to install ***Audacity*** (I use it myself). It is also *very easy* to install ****buntu-restricted-extras*** and get a lot of codecs (among them lame).

It is even possible to start from the Ubuntu mini.iso and make a minimal system with only the particular packages that you want (and no other 'bloatware'). That is harder, so it is not what I would recommend at first, but if you wish you can get help here with such tasks too.

*Edit*: It is possible to make an installed system at another place (away from your home and your computer) where there is a good internet connection, for example in a USB pendrive, and carry that home and install it (clone it) into your computer.

---

### Post by Frogs Hair on 2015-01-01
If the title is correct and you are using 9.10 please install a supported release . The 9.10 software repositories are closed there would most likely be dependency problems with a newer version of Audacity.   If you have older hardware consider Lubuntu , Xubuntu or even Ubuntu Studio. The last being just for graphics and music . Without knowing what your hardware is it's hard to recommend which one.

---

### Post by Mike_Walsh on 2015-01-02
Hi, Willsed394.

First of all, welcome to the forums.

Secondly, I will echo what sudodus and Frogs Hair have said. 'Karmic Koala' is WAY past it's 'use by date'; it's not supported, and in general is very unsafe to use.

As sudodus has requested, we really need to know a wee bit more about your machine before any recommendations can be made. If it's capable of running the newer 'buntu flavours, then Audacity is freely available from the repos; I use it myself...it's an excellent piece of kit.

However, you mentioned investigating Puppy Linux. I run one of the newest releases, 'Tahrpup' 6.0. Audacity is also available for this, and I use it here, too. (I'm in 'Tahrpup' at the moment.)

If you're interested, 'Tahrpup' is available for download from here:-

[http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/](http://distro.ibiblio.org/puppylinux/puppy-tahr/iso/tahrpup%20-6.0-CE/)

You need the 5th entry down; 'tahr-6.0-CE_PAE.iso'. Or, depending on the age of your machine (and this is why we need the specs, to be able to help), you may need the 7th entry down; 'tahr-6.0-CE_NoPAE.iso'. Download, burn to CD, and boot in the usual way.

If you decide to try it, a version of Audacity which works with 'Tahrpup' is available from here:-

[http://puppylinuxfaq.org/add-on-software/29-pet/200-audacity-sound-editor-pet.html](http://puppylinuxfaq.org/add-on-software/29-pet/200-audacity-sound-editor-pet.html)

And some very helpful individuals can be found at the 'Puppy' Forums, here:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

>   *Edit: It is possible to make an installed system at another place (away from your home and your computer) where there is a good internet connection, for example in a USB pendrive, and carry that home and install it (clone it) into your computer.* 

This is actually a very good idea. You can, in fact, make a full install to a USB thumb drive, and then you can take it with you wherever you go, and use it anywhere you have a computer that will boot from USB. I have a thumbdrive install of Lubuntu 14.04.1 which I use in exactly this way.

> [COLOR=#000000]Windows insists on registration. I will NOT log my music computer (an old Dell) onto the internet. Eventually, Windows will crash (or just fail to save files in usable form, or even delete the tracks), and I lose tracks if not saved to thumb drive.[/COLOR]  

See, you don't have those kinda problems with Ubuntu..!

Hope this all helps. But please, QUIT using 'Karmic', for the sake of your machine's health! ;)


Regards,

Mike.

---

### Post by Bucky Ball on 2015-01-02
Agree with all other re. upgrade to a supported release. Slightly off-topic, but the LTS releases might suit you better as they are now supported for five years, 12.04 LTS to April 2017 and 14.04 LTS til April 2019. The interim releases, at this time 14.10, have nine months support.

Used Audacity extensively for audio editing and love it. Recently used it for recording some ideas 'on the fly'. No issues. Works great for me. ;) 

And +1 for the suggestion re. the mini.iso install. For an audio setup, mini.iso with only the apps you want/need is ideal. A project for down the track a bit, perhaps. It can take a while to figure out which apps suits your needs best. You can always mess around with a minimal install on another partition once you have a supported release up and running.

Good luck with it. ;)

---

### Post by grahammechanical on 2015-01-02
Ubuntu Studio has been mentioned already but here is the link

[http://ubuntustudio.org/](http://ubuntustudio.org/)

[https://ubuntustudio.org/about-ubuntustudio/](https://ubuntustudio.org/about-ubuntustudio/)

It uses a real time kernel, whatever that means, but I understand that a real time kernel is necessary for visual and audio work. During installations we get options as to which groups of packages to install. We can select only audio packages or only visual packages and there are other choices. Or we can install the whole lot. Need DSL for that.

Also we can install Ubuntu without an Internet connection but we will need to update at some point as the ISO image is fixed at the date of release. And that is another reason for going to an LTS release. Its ISO images are updated about every six months for the first 2 years.  But standard release ISO images are not updated during the support life of the release.

Some people are way ahead of you with this idea of a distribution with Audacity as a default application

[https://ubuntustudio.org/tour/audio/](https://ubuntustudio.org/tour/audio/)

Regards.

---

### Post by newb85 on 2015-01-02
As others have pointed out, using an unsupported release and connecting to the web is unsafe.  That said, it is still possible to access the repos for all releases back to Warty by switching to old-releases.ubuntu.com.  

If you're planning to stay disconnected from the web once your machine is set up, that would be a way to install audacity on 9.10.  Of course, it would be the version of audacity that was in the repos for 9.10, which is probably five years older than the current version.

---

### Post by willsed394 on 2015-01-03
thank you all very much for responding.

the machine is a dell running windows 7 home premium, 2 gb ram. i am nearly certain it was the cheapest or near cheapest dell made in 2007.  at the moment, i can't tell you more; tossed nearly all of the original documents that came with the dell, so the only way to look at the rest of the hardware is to run the windows sata, and i have the second sata hooked  up right now.  i found the original dell diagnostic cd, have that running. why?

when i posted my first post, i was digging around the net trying to find some answers on os that might give me an audacity 'start'. i found a post on 'frugalguitarist' forum; the poster has just about the same hardware i am using 'pre daw'.  he is using ubuntu studio, and seems very satisfied with it (but i hve not heard any of his music, so....is it working well enough to 'make his work come through'? anyway...

i downloaded the iso of ubuntu studio. took 3 hours on my connection.  when i attempted to boot it from dvd on the dell, ubuntu 9.10 would not allow the bios to boot from dvd.  took 'eRace' and tried to wipe the sata drive that i had ubuntu 9.10 on...and it wiped it...so well that the drive nor cd drive will boot now using the 'ubuntu' sata drive; bios does not recognize the wiped sata drive. hence, running dell diagnostics. am trying to determine if the harddrive is still working enough to bother trying to get ubuntu studio on it.

i have another sata drive with windows 7 on it in the case, so i am not out of bidness.  that drive will boot and still has windwoes and audacity on it. i did have the sense to unhook that drive when i put eRase into the cd drive.

however, back to anything coming from the internet...no matter what i have done (and i did at one point take the old ubuntu 9.10 to best buy geek squad), i have been unable to get verizon wireless software to work with ubuntu.  here, i have 3 options for internet:

1. dial up
2. verizon wireless with a tower 2 miles away
3. hughes net

i think i might have one other option, nowadays, with the satellite tv having internet, but i don't really want or need satellite tv, and am suspicious their internet connections may be no better than hughes.

in any case, i really don't want to do an internet download 'direct into the music computer', which is why i did the iso of ubuntu studio. now, it remains to be seen if i can get it on the wiped sata. if i cannot, i'm thinking i will have to order another sata, as i don't want to kill the windows sata drive until i have a working ubuntu studio drive. i have read a couple of comments elsewhere something to the effect of  'i have an old os. i am running a daw (fill in any you like). i have never updated my computer with anything, and it has never given me problems in 5 years.'.  most of the computer issues i have had were because of 'updates'. they should be called 'downdates', especially if apple or microsoft is involved, i think. my prejudices are showing. in any case, i don't want any update; if the os version i get that has audacity works to start, i don't want to mess with it in ANY way.  the only external 'computer devices' other than recording necessary items will be a usb stick to copy an mp3 file so it can be carried over the 'new cheap throwaway internet computer' with windows and the wireless internet and posted on soundclick. (any/all of you are welcome to listen to anything i have posted there....search term under 'band' 'cogbern', which is 'me,myself and i' as a friend of mine says)

as with many human endeavor, trying to fix one thing leads to problems with something else.  when i had dsl, ubuntu worked perfectly (despite the fact it was 'old' 8 years ago...

so, now i have an antivirus download going and better post this before this machine gets overloaded and crashes.  

again, thanks. i'll be back with updates on my keystone cops computer adventures later.

---

### Post by Bucky Ball on 2015-01-03
Your other option is to install a mini.iso or Xubuntu (which uses xfce4 desktop environement same as UStudio) and just install ubuntustudio-audio. That will give you all the UStudio audio apps and not the video stuff and other things which you probably don't need. Just throwing in some options.

If you just want Audacity, though, that should install on any supported releases without a problem. Never had any probs with it myself. ;)

---

### Post by mörgæs on 2015-01-04
Best is to install using wired internet connection. 

Don't buy new hard drives or other gear.

In Buntu people should always up*date* (within a version) whenever new packages are ready but not up*grade* (to the next version). Always a fresh install.

---

### Post by willsed394 on 2015-01-04
morgaes, wish i HAD a wired internet connection. frustrating to take 3 hours to download a 'free' os, then have to pay $15 to increase data by 2gb due to data limit. more corporate theft of the internet....  dell computer technical specs:  intel celeron cpu 450@2.2 ghz 2 gb ram 32 bit 'high definition audio controller' using microsoft driver usb audio codec intel g45/g43 chipset   after several hours of diagnostics, the 2nd hard drive is not responding, so will get recycled after treatment with acetylene torch. life goes on.    thanks. keep on truckin'!

---

### Post by codingman on 2015-01-04
So, you *don't* have a possible internet connection apart from wireless? With your system specifications, I'd recommend either Lubuntu or Xubuntu on the latest LTS release (that would be 14.04).

---

