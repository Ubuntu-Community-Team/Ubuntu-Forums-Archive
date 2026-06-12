---
title: "rpm or debian"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Dr Noam on 2008-07-27
Hi, my first question on the forum...

I'm trying to install Curl for Linux on my brand new ubuntu (in order to play online Puerto Rico, since you asked :)) and got to this:
> Curl RTE V6.0.2 for Linux
You have chosen the Curl RTE for Linux.
Click a link to start downloading.
Curl RTE for Linux Download - rpm version
Curl RTE for Linux Download - Debian version 
I don't know which I should use - What are rpm and Debian? Synaptic seems to indicate that I have both.

Thanks.

---

### Post by Der Alte on 2008-07-27
In Ubuntu, it'll probably be a lot easier to install the Debian package.

---

### Post by Troll_the_Great on 2008-07-27
Debian.Ubuntu is a debian base distribution, so it's native packages are .deb.
Cheers!

---

### Post by eightmillion on 2008-07-27
You want the Debian version

---

### Post by Joeb454 on 2008-07-27
RPM files are for Red Hat based distro's (such as Fedora), whereas Debian based distro's (such as Ubuntu) use DEB files :)

---

### Post by SunnyRabbiera on 2008-07-27
right, as like others said ubuntu is debian based.

---

### Post by Troll_the_Great on 2008-07-27
> 
I don't know which I should use - What are rpm and Debian? Synaptic seems to indicate that I have both.

Thanks.

Rpm and Debian are packages.There are two major branches of linux:Red Hat Linux, who uses rpm packages, and Debian Linux, who uses debian packages.Ubuntu is a debian distribution, and Fedora or Mandriva are a red hat distribution.For making things simpler, .deb and .rpm packages are for linux what is .exe for windows (in a way).
Cheers and welcome to Ubuntu!

---

### Post by Dr Noam on 2008-07-27
Wow, that was some fast replying! Thanks all. Unfortunately, the download resulted in:> Error: Wrong architecture 'i386'Any advice?

---

### Post by spiderbatdad on 2008-07-27
Curl is in synaptic package manager...```
sudo apt-get install curl
```

---

### Post by tom66 on 2008-07-27
Well what computer do you have? 64-bit? PowerPC?

---

### Post by Tom--d on 2008-07-27
What are you on.
32bit
or
64bit?

---

### Post by Joeb454 on 2008-07-27
It looks like you're running 32 bit and downloaded a 64 bit deb file.

Or perhaps it could be the otherway :) Try finding a 32 bit deb (could be named x86 or i386 as well)

---

### Post by Sef on 2008-07-27
> Error: Wrong architecture 'i386' 

> Joeb454  	
Re: rpm or debian
It looks like you're running 32 bit and downloaded a 64 bit deb file.

Or perhaps it could be the otherway Try finding a 32 bit deb (could be named x86 or i386 as well) 

+1.  AMD64 architecture can only install on 64-bit.  X86 installs on 32-bit, and on 64-bit with some help.

---

### Post by Dr Noam on 2008-07-27
OK, let's see:
I DON'T KNOW if I'm 32 bit or 64 bit, and feeling a bit stupid because I don't know how to check. It's a Toshiba A200 laptop Satellite Pro.

Thanks Spiderbatdad for pointing out that curl is in synaptic, one less thing to worry about.

---

### Post by spiderbatdad on 2008-07-27
some useful information about your computer:

navigate: System>>Administration>>System Monitor>>System tab

terminal: ```
uname -r
```
```
cat /etc/lsb-release
```

---

### Post by Dr Noam on 2008-07-27
Thanks, useful, but... doesn't tell me 32 bit or 64 bit?

---

### Post by Joeb454 on 2008-07-27
In a terminal enter ```
uname -m
``` if it returns x86_64 you're running a 64 bit system :)

---

### Post by spiderbatdad on 2008-07-27
if the release doesn't say x64, i believe, then you have installed the 32 bit.```
uname -m
```will tell you about the machine hardware. uname -r about the kernel release.

```
man uname
```for other options

---

### Post by Dr Noam on 2008-07-27
x86_64 indeed!

---

### Post by render787 on 2009-11-23
> **Dr Noam said:**
> OK, let's see:
I DON'T KNOW if I'm 32 bit or 64 bit, and feeling a bit stupid because I don't know how to check. It's a Toshiba A200 laptop Satellite Pro.

Thanks Spiderbatdad for pointing out that curl is in synaptic, one less thing to worry about.


Ok, the package curl in synaptic seems to be a different curl from the one that is required...

The game is linked here:

[http://www.phial.com/puerto-rico/](http://www.phial.com/puerto-rico/)

And the curl .deb and .rpm files are here:
[http://www.curl.com/download/rte/linux/download-linux-rte.php](http://www.curl.com/download/rte/linux/download-linux-rte.php)

Their developers discuss using them here...
[http://developers.curl.com/message/3729#3729](http://developers.curl.com/message/3729#3729)

However, the curl in synaptic seems to be a glorified version of WGET, not something that executes an applet. When I run curl, as downloaded from synaptic, on the url to the game.curl app file on the phial site linked above, i simply get the text of that page back, with this message at top:

|| If you can read this sentence, then the Curl RTE has not been installed
|| properly.  See "index.html" file for information about the Curl RTE.

Meanwhile, both the RPM and DEB files above give me this message:


chris@system76-pc:/tmp$ sudo dpkg -i curl-rte-8-en_7.0.1-r24_i586.deb
 dpkg: error processing curl-rte-8-en_7.0.1-r24_i586.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 curl-rte-8-en_7.0.1-r24_i586.deb


Even when I do the ALIEN thing as described above, it fails with the same error.

Moreover, these curl folks seem to have no form of customer support to speak of, they have a small FAQ but nothing useful... I sent them an email mentioning this.

My question is, there are only 2 posts that seem to address this on ubuntu forums, and the guy above seems to either have succeeded or lost interest...

The other similar post I saw was this: [http://ubuntuforums.org/showthread.php?t=466122](http://ubuntuforums.org/showthread.php?t=466122)

Neither of these fixes worked for me. Is this likely some kind of new version thing, like it worked years ago but not now? Also, no one ever mentioned actually getting it to work, so I'm a little suspicious... 

It seems like there must be some other name for it in synaptic / apt-get, but I tried curl-ria, curl-rte, etc... and when i search curl, i only get the curl i mentioned above, and lib curl and bindings and such, nothing that seems to be what I need.

Is there something I should be searching for in synaptic besides just curl?

Any help greatly appreciated... and if anyone happens to know these guys at CURL, maybe pass some of this info on to them too? I have yet to discover the appropriate email address for this other than just [email]info@curl.com[/email] ... somehow that feels like a black hole.

Best,
Chris

---

### Post by JairunCaloth on 2009-11-23
Ok, so this Curl RTE isn't remotely similar to the common linux tool curl.

You can try to install the 32-bit deb file by telling dpkg to force the install. I've had success installing 32bit packages this way in the past, but it's not a sure thing.

ex:
```
sudo dpkg --force-architecture -i Curl.deb
```

---

### Post by render787 on 2009-11-24
> **JairunCaloth said:**
> Ok, so this Curl RTE isn't remotely similar to the common linux tool curl.

You can try to install the 32-bit deb file by telling dpkg to force the install. I've had success installing 32bit packages this way in the past, but it's not a sure thing.

ex:
```
sudo dpkg --force-architecture -i Curl.deb
```

Thank you! I didn't know you could do that!

So I tried doing this:
It told me it depends on libstdc++5 ... but I have libstdc++6! 
I downloaded the libstdc++5 version from the debian site [http://packages.debian.org/etch/libstdc++5](http://packages.debian.org/etch/libstdc++5)
I also needed to get gcc-3.3-base package... thankfully that was it.

I installed both of these with dpkg. I tried to figure out if there was someway I could force these depends, since I'm pretty sure I have better versions of these packages, but then synaptic told me I had broken packages so I figured what the hell I'll install them, hopefully they play nice.

Also, it seems like this was part of ubuntu, back during hardy? [http://packages.ubuntu.com/hardy/libstdc++5](http://packages.ubuntu.com/hardy/libstdc++5)

chris@system76-pc:~/curl$ sudo dpkg --force-architecture -i curl-rte-8-en_7.0.1-r24_i586.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 306065 files and directories currently installed.)
Preparing to replace curl-rte-8-en 7.0.1-r24 (using curl-rte-8-en_7.0.1-r24_i586.deb) ...
Unpacking replacement curl-rte-8-en ...
Setting up curl-rte-8-en (7.0.1-r24) ...

chris@system76-pc:~/curl$ 

(this is not the first time i did --force-architecture on the package, at first I did --force-architecture,depends and then worked backwards to find the depends... it shouldn't matter though?)

So now I don't seem to have any executables though. I can't type curl and make anything happen... it just wants to install the ubuntu curl tool thing.

The claim made by the original guy with this applet is that I can just click on it... when I do, firefox asks what to do with game.curl ...

Isn't the dpkg install supposed to like, set up some other ****? Also, how come this package won't show up in synaptic now that I have it installed? Normally I would go there and ask what are the related files and try to use them, but I don't know how to do that now...

How do I know what if anything happened when I dpkg --force-architecture -i 'd this guy? Is it possible that it just did nothing?

Also in general is there a way to get packages that say they want libstdc++5 to just be happy with libstdc++6 ?

Thanks,
Chris

---

### Post by Tim Williams on 2009-12-20
In case anybody stumbles across this thread: I got this working on 64-bit Jaunty by installing the Curl RTE deb package with --force-architecture then running:

```
cd /opt/curl/surge/8
bin/surge-mozilla http://www.phial.com/puerto-rico/game.curl
```

Hope that helps!

---

### Post by gtmarley on 2010-03-21
> **render787 said:**
> 

I've got the same issue, and for the same reason.  Puerto Rico on Ubuntu 64 bit.
Chris, did you make any progress?
I guess my next option is to try the windows (argh) version in virtual box.

---

