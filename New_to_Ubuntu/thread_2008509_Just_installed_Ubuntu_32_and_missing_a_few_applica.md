---
title: "Just installed Ubuntu 32 and missing a few applications."
date: 2012-06-22
forum: New to Ubuntu
---

### Post by Frank E on 2012-06-22
Hi folks, I've just installed Ubuntu 11_10* as my main operating system  after the XP32using had its licence revoked. It was an OEM version and I  had to replace mobo/CPU and RAM. The OS starts to load then goes to a  clear blue screen.
Cheers for kicking me when I'm down, manufacturer of aforementioned OS.
 
There are a few things I could really do with that I took for granted on my old machine.
* I now have Ubunto 12_04 ISO, the 11_10 was all I had to hand on CD.

**Roboform**
I've been using Roboform Pro for almost a year to fill in numerous  webforms. Roboform site doesn't list any supported Ubuntu browsers. Is  there an application like Roboform that runs on any Ubuntu browsers
[B]
Google Toolbar[/B]
Can I run this on any browser on Ubuntu?

**Asset UPnP /DNLA Server**
I used Asset to stream 1411 WAVs from my media HDD over ethernet to a  (Naim) hi-fi streamer. dbpoweramp which II used to rip the WAVs provides  private tags which the naimstreamer can render. I had a look on  dBpoweramp and there doesn't seem to be a Ubuntu version of Asset. Are  there any DNLA compliant uPnP servers that can run on  Ubuntu boxes and  which will serve up the private tags too?

**Secondary (NTFS) drive hasn't mounted**
To stream my media I will need access to my media HDD (though I have  some of my collection on my accessible main HDD to get on with). I'm  getting the following error though:

Quote
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
End Quote 

My XP licence has been revoked, I can no longer boot to XP32, so are there any tools I can run from Ubuntu to  chkdsk the drive?

Any help to a nood would be appreciated.

---

### Post by PhantomTurtle on 2012-06-22
Roboform Lite runs on Ubuntu in Chrome or Firefox, Roboform Pro is a desktop app(I've never used it, so I wouldn't know) then you might be able to run it in Wine. You could also try [LastPass]("https://lastpass.com/"), which runs natively in Ubuntu.

Google toolbar, no. It is for Internet Explorer. Get Google Chrome, it has many similar feature or those features can be added with extensions and it is a a lot better than Internet Explorer. Firefox, which comes preinstalled is also a great browser which can have those features added with extensions.

[Configuring a DNLA Player Under Ubuntu]("https://www.ebower.com/docs/ubuntu-dlna-player/")

Sorry can't help you with the last one, Hope the other help though.

---

### Post by DingusFett on 2012-06-22
Not really help, but why Google Toolbar? I'm not familiar with them, but most of the time I've found if someone has those add-on toolbars, they have  some sort of malware too. I've never used them and can't think of a need for them. Firefox has a search box that can search google, wikipedia, etc; Can't think of anything else it'd do that would be particularly useful?

---

### Post by Frank E on 2012-06-23
> **PhantomTurtle said:**
> Roboform Lite runs on Ubuntu in Chrome or Firefox, Roboform Pro is a desktop app(I've never used it, so I wouldn't know) then you might be able to run it in Wine. You could also try [LastPass]("https://lastpass.com/"), which runs natively in Ubuntu.
 
Google toolbar, no. It is for Internet Explorer. Get Google Chrome, it has many similar feature or those features can be added with extensions and it is a a lot better than Internet Explorer. Firefox, which comes preinstalled is also a great browser which can have those features added with extensions.
 
[Configuring a DNLA Player Under Ubuntu]("https://www.ebower.com/docs/ubuntu-dlna-player/")
 
Sorry can't help you with the last one, Hope the other help though.
 
Thanks, got Roboform Lite installed
I had Chrome installed, couldn;t find where to launch it. Found it now though
Must say the inbuilt spellchecker in Firefox / Ubuntu is handy.
I'll have a play with the DNLA server tomorrow.

---

### Post by Bucky Ball on 2012-06-23
Welcome. Enjoy the ride. You never know, MS might have done you a favour! 

Try and go native, if possible, and if your old software doesn't work in Ubuntu.

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8E_Q.VPfX8ASB436At.?p=linux+alternatives+to+windows+programs&fr2=sb-top&fr=altavista&type_param=](http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8E_Q.VPfX8ASB436At.?p=linux+alternatives+to+windows+programs&fr2=sb-top&fr=altavista&type_param=)

BTW, Firefox and others are not 'Ubuntu' browsers. They are just not IE and work perfectly well on other platforms. When I started using Ubuntu I was already using a heap of open-source programs in XP anyway so no big shakes (Open Office, Firefox, Thunderbird, Gimp, and others ...). Adjusting my attitude about computing remains an ongoing process ...  ;)

Incidentally, for Chrome you might try Iron; a hybrid that gobbles less of your personal info ...

[http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php)

You might find it a bit tricky to install as a newcomer, though ...

PS: You have 32bit on a 32bit machine, not 64bit? If not I'd install the 64bit before getting to deep ...

---

### Post by Frank E on 2012-06-23
> **DingusFett said:**
> Not really help, but why Google Toolbar? I'm not familiar with them, but most of the time I've found if someone has those add-on toolbars, they have some sort of malware too. I've never used them and can't think of a need for them. Firefox has a search box that can search google, wikipedia, etc; Can't think of anything else it'd do that would be particularly useful?
 
Thanks, got Firefox to default to Google when I installed 12_04, still a tiny search box though. I've used all browswers on Win boxes and prefer IE to the others. As for the Google toolbar it's:
To make it quicker to search Google scholar, Google images etc.
For the favourites bar so I can launch the most used pages quickly 
 
Managed to get Win XP running. It is in fact activated. Not sure why it was blank blue screening but repaired it anyway from installation CD repair console.
So was therefore able to repair the media HDD with chkdsk, so that Ubuntu is now seeing it. Will set up a DNLA upnp server tomorrow night.

---

