---
title: "Help With Firefox 12.04.1 LTS"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by folgerdrinker on 2013-01-21
Hello All:

I have been a Unix and Linux user in the past, but for job purposes got heavily involved with Windows. Please do not hold that against me :)  However, I have a desire to renter the Linux community. so, I downloaded Ubuntu desktop, specifically ubuntu-12.04.1-desktop-i386.iso. My CD/DVD took a dump and I could not use the burned cd to load it so I used a thumb drive to load it. This was a total install over an older windows environment.  I checked off to download all the updates and drivers of which thee were 97. It got stuck on file number 49 and then on update-grub. I got past that and the system finally booted. Problem is, although I can go to Google and youtube with Firefox, I cannot go to any other web sites. Also, when I try to view a youtube video, it tells me that I need the flash add-on but it searches and searches and never downloads it. I tried the suggestion to go to about:config and set the ipv6 option to true, but that did not help. So... two questions:

1. Is there a simple fix for the Firefox issue.

2. And a bigger question about the grub. Is this version stable?

I am running it on an AMD64 box with only 2 gigs of memory so I downloaded the 32 bit version. My thinking is that if I can fix the Firefox problem, which ultimately would mean solid Internet access, then maybe I could get all the updates that failed during the initial install. Anyway, I am looking forward to finding that Ubuntu is solid and trustworthy. I want to escape the Windows world. I am a LAMP developer and look forward to strong performance from Linux in general and Ubuntu in specific.

Does anyone have a suggestion on how to fix my problem?  Just a note, everything seems to be set properly from a network connection standpoint, but it sure isn't functioning that way.


Much thanks in advance with any help you can offer.

---

### Post by BBQdave on 2013-01-21
> **folgerdrinker said:**
> I am running it on an **AMD64** box with only 2 gigs of memory...

I would give Ubuntu 12.04 - 64bit a go :)

2 Gigs of RAM should be enough for Ubuntu. And as you said, clicking *updates* and *third party plug-ins* should cover you on *flash player* and *mp3* playback.

---

### Post by Lightning Dragon on 2013-01-21
Hello,

How very strange. By "can't" do you mean it shows a message, or they simply never load? Does it say connection failed to load or anything? You should check your firewall and see if there is something fishy there, or in the Firefox settings like in "Network". In the mean time, I will try and find a solution for you. 

As for flash, that is strange, as it usually installs right out the box for me. Go to the Software Center (this;) and search "adobe flash player" (or just "flash"), and install it. Also type this into the Terminal; "sudo apt-get install ubuntu-restricted-extras", and if that doesn't work try "sudo apt-get install flashplugin-installer".

 Although you could go to the Update Manager and update that and see if it makes it so you can play flash, as that's how it is usually installed. It is very odd it didn't automatically install for you.

Please see the links below and tell me if any of them fixes your problem.

[http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/](http://blogdaprima.com/2012/install-adobe-flash-plugin-on-ubuntu-12-04-lts-precise-pangolin/)

[http://www.krizna.com/ubuntu/how-install-adobe-flash-player-ubuntu-12-04/](http://www.krizna.com/ubuntu/how-install-adobe-flash-player-ubuntu-12-04/)  
(^ Please make sure you do not include the person's username or the "$" in the commands when you perform them)

---

### Post by folgerdrinker on 2013-01-21
Hello Again:

Since this was a fresh install yesterday, I decided to do another fresh install. While there were still a couple of errors that happened right off the bat, like some permissions denials, overall the install went a lot better today. Firefox seems to be working fine now. Still a few issues, but I think I can work through them. I have no sound through the earphone plug and the sound settings did not generate a solution. But, that may be my computer... Anyway, I want to thank you folks for responding so quickly... that was awesome and admirable...

Sincere thanks and I will see you next problem!!!

---

### Post by folgerdrinker on 2013-01-21
BBQDave...

I was tempted to do the 64 bit install on my AMD64 machine, but I had consulted some write ups about that... it seems that the best configuration for AMD64 bit is to have at least 4 gigs of memory... I only have 2GB... the write up did say it would work on 2GB but I am trying the 32 Bit first... 

Thanks for your suggestion and I still may wind up doing the 64 bit... I can get 2 more GB for about 80 bucks...


Thank you again!!!

---

### Post by Lightning Dragon on 2013-01-21
Hello,

I am unsure of the problems you are having now. Is it still directly related to Firefox, or is there something else wrong? If the fresh install you did on post #4 worked, then I don't think you should do another reinstall.

---

