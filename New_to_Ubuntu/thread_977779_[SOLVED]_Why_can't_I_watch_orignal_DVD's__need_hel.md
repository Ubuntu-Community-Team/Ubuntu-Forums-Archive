---
title: "[SOLVED] Why can't I watch orignal DVD's ??? need help Please"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by IrishDom on 2008-11-10
Hi everyone,
 I just installed Ubuntu 8.04 on a new computer with only ubuntu as my OS . My problem is this : I can not watch orginal dvd's , when I put in a bootleg dvd for the first time it downloaded the codecs but when I put in the orginal it says "unable to open" why??? Is there a new player that I should get ?? Like I said I am completely new to Linux.. And I want to be able to use it . I **do not want to have to revert to MircoCrap[B]**[/B] 
thankyou for your help

---

### Post by Ryadt on 2008-11-10
Make sure that you have ubuntu restricted extras installed.
```
sudo apt-get install ubuntu-restricted-extras
```

Also get the medibuntu repos
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sirebral on 2008-11-10
This will help: [http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html](http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html)

Eventually problems like this will end.  DMR is a faulty service as it is right now, and DVD encryption follows suit partially.

The main reason there is no DVD decryption available for Linux distros is because it is proprietary and from what I understand there is no deal with the OS developers.  You have the right to watch your DVD though, so while they can't offer it to you because of Copyright Laws, you can download it.

As for DMR, that system is so faulty to begin with.  Know your rights concerning DMR (Digital Media Rights).  DMR is a 'robotic' device that has been instituted to protect the rights of the Artists, but in it's development it is neglecting the rights of the End User.  Because DMR is instituted by the Labels, and the distributor needs to provide the DMR Protection, the End User is getting screwed over.  Case Example would be when Yahoo! Music collapsed, taking their DMR servers, and the end user certificates, down with it.

Record Labels should be forced to provide their own servers and DMR services.  Digital Media should be treated like a physical object, with the right to share (lend / borrow), give, and trade included.  DMR Services should allow a person to re-register a computer, instead of allow a total of 5.  After so many re-installs the DMR are gone!

Yet, because we live in Civil America, where the Bill of Rights states your rights can be removed if you infringe on others, the record labels have forfeited a portion of their rights by neglecting yours.

I know that was a long statement, but it is something to recognize if you feel you are breaking the law when you download proprietary digital media that you have the right to use.

---

### Post by saj0577 on 2008-11-10
```
sudo apt-get install vlc vlc-plugin-esd
```

Then install all the gstreamer plugins (but check you can legally in your country first)

Saj

---

### Post by IrishDom on 2008-11-10
thanks so much I installed the medibunutu repository w/the libdvdcss codec and the gstreamer... I have also ran across one other problem I've installed Starwars Knights of the old republic, and medal of honor pacific assault .. under wine (with just wine installed) and it installs but the game won't start?? is this b/c i'm using a 64-bit os??? bc both of these games are on the supported list at winehq.com

any help is very much appreciated
Dom

---

