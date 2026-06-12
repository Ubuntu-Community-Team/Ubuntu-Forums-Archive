---
title: "HOWTO: Install zsnes with libao support on AMD64"
date: 2007-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dfreer on 2007-10-23
This guide will install ZSNES 1.51 with libao support for AMD64/i386 versions of Gutsy & Feisty. Old Guide that this replaces: [http://ubuntuforums.org/showthread.php?t=272927&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=272927&highlight=zsnes)
**F.A.Q.**
[list]
[*]**What is ZSNES** - Official site: [http://www.zsnes.com/](http://www.zsnes.com/)
ZSNES is a emulator that let's you play games from the Super Nintendo Entertainment System on your computer. You will need to use images of the original SNES cartridges called ROM's, which are in most cases illegal to have. 
**DO NOT ASK HOW TO GET ROM'S**, it is against the rules of this forum. The emulator itself is not illegal. **DO NOT ASK ME FOR ROM'S BY PM OR EMAIL!!**
Some advantages of playing SNES games on your computer vs playing them on the original console:
[list]
[*] Ability to "Save State", anywhere in a game
[*] Patch games "On the fly", to be able to play games that were released only in japan with English Translations (i.e. Star Ocean, Tales of Phantasia etc), or to play custom mod's of existing games (i.e. Legend of Zelda - Parallel Worlds)
[*] You can apply filters to make your screen look more like a NTSC television, or even update the graphics to make games look better than the original.
[*] No more blowing on carts! ;)
[/list]
[*]**Why ZSNES 1.51 with libao?** - 1.51 does not support netplay, but it is the latest version of ZSNES to date. Libao was added and greatly improves sound IMO on AMD64 systems, and possible i386 as well (note: you must run zsnes with -ad oss at least once in order to use libao).
[*]**What's wrong with the 1.51 version in the main gutsy repository?** - It's only for i386, and gutsy users have been experiencing a "can not create mcop directory" error. My version AFAIK does not have this problem. See the following threads for more detail:
[http://ubuntuforums.org/showthread.php?t=584105](http://ubuntuforums.org/showthread.php?t=584105)
[http://ubuntuforums.org/showthread.php?t=571666](http://ubuntuforums.org/showthread.php?t=571666)
[*]***pSX, mupen64, and/or ZSNES segfault and I can't figure out why!*** - [rcsdnj]("http://ubuntuforums.org/member.php?u=135017") reports that the "Data execute prevention" on x86_64 processors may be the cause of a segmentation fault. I haven't tried this myself, so proceed with caution:
> **rcsdnj said:**
> 
To stop , I first did it by going to the BIOS and disabled the "XD Technology" option. Since I didn't want to disable it globally, I looked for a way to disable and I found this:

- install prelink package ( sudo aptitude install prelink - I'm not sure about the package name, I'm not in my Ubuntu machine right now)

- run the executable you want to disable the XD technology by using:

execstack -s program_name

I'm not saying this is the solution for the problem, but it's maybe a good test.
[/list]

***How to install ZSNES using my repository (Easiest Way):***
Copy the following into *Applications > Accessories > Terminal*.
**Step 1** - Add the repository to your source list.
Gutsy AMD64/i386 Users:
```
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list 
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
```

Feisty AMD64/i386 Users:
```
echo "deb http://packages.dfreer.org feisty main" | sudo tee -a /etc/apt/sources.list 
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
```

**Step 2** - Install zsnes
AMD64 Users:
```
sudo apt-get install zsnes32
```

i386 Users:
```
sudo apt-get install zsnes
```

**Step 3** - Use libao w/OSS for better sound quality (may fix scratchy sound)
Launch zsnes from Terminal with this command once, so it will use the OSS driver from now on:
AMD64 Users:
```
zsnes32 -ad oss
```
i386 Users:
```
zsnes -ad oss
```


**How to Uninstall:**
AMD64 Users:
```
sudo apt-get remove zsnes32
sudo apt-get autoremove
```

i386 Users:
```
sudo apt-get remove zsnes
sudo apt-get autoremove
```




**How to compile ZSNES 1.51 (Advanced Users)**:
*Note: this is for i386 users. I have not figured out how to compile a 32-bit executable from a 64-bit machine, so if AMD64 users wish to compile, follow the below instructions on a 32-bit machine.*
Install needed packages:
```
sudo apt-get install nasm build-essential libsdl1.2-dev zlib1g-dev libpng12-dev libncurses5-dev libao-dev
```

Download zsnes and unpack it:
```
cd ~/
wget -c http://superb-west.dl.sourceforge.net/sourceforge/zsnes/zsnes151src.tar.bz2
tar xvf zsnes151src.tar.bz2
cd zsnes_1_51/src/
```

Configure and compile:
```
./configure --with-x --enable-libao --enable-release
make

```

i386 users only:
```
sudo make install
```

AMD64 users only:
```
sudo cp ./zsnes ~/Desktop/zsnes_custom
```
AMD64 users only: Copy the zsnes_custom on your desktop to your AMD64 machine, and install the following package.
```
sudo apt-get install ia32-libs
```

To uninstall compiled version:
```
cd ~/zsnes_1_51/src/
sudo make uninstall
cd ../../
sudo rm -Rv ~/zsnes_1_51/
sudo rm zsnes151src.tar.bz2
```

---

### Post by ShadowMKII on 2007-10-26
Wow, this thread is awesome! Thanks mate for making this link, as it helped me solve a problem that I have been having for a long time with Snes! How did you go about making something like this? (Your own repository and your own way of getting Snes to work on 64 bit machines?) I just find it really intriguing, that's all! ^-^

---

### Post by mmxbass on 2007-10-26
I got the answer to your issue with configs.

See: [http://board.zsnes.com/phpBB2/viewtopic.php?t=10680]("http://board.zsnes.com/phpBB2/viewtopic.php?t=10680")

---

### Post by dfreer on 2007-10-27
Yeah, zsnes devs don't, shall we say, exactly share the spirit of the ubuntu forum :D But hey, it's a free emulator and one of the best for snes, so who cares if they are a bit crotchety? At least they responded to the OP.

Anyways, onto the actual subject matter, I do believe I ran into that --with-zconf-path=PATH option before, I do not recall what my problem was but I evidently never got it working:
[http://ubuntuforums.org/showpost.php?p=3429872&postcount=102](http://ubuntuforums.org/showpost.php?p=3429872&postcount=102)
It may have been a problem between the keyboard and the chair ;) So I will try again soon, and by soon I mean sometime before Duke Nukem Forever ships. Eh, as long as I don't forget!

@ShadowMKII - You're welcome, so it works good for you, with no scratchy sound? Hmm, I might put up a page about my history on my server here, as the whole story is rather long. The short answer is, I wanted to learn about linux. The packages, web server, and repository are all just "test subjects", me messing with things here and there learning new stuff. 
I also used to be quite an avid gamer, although now I don't play nearly as much as I'd like to.

---

### Post by ShadowMKII on 2007-10-27
Sounds exactly like me, to tell you the truth! (Except that I have Linux for about a month and know very little in comparison!) ^-^; So far, the sound is quite good at the 32000Hz (I think) sampling rate, though it is somewhat scratchy at times. That is perfectly fine though, seeing as how all emulators have been like that! Honestly, I do not mind at all, seeing as how I am able to play games that are golden even without perfect sound!!

---

### Post by dfreer on 2007-10-27
Try running zsnes once from the command line, like so:
```
zsnes32 -ad oss
```

That'll switch from using ALSA to using libao with OSS, which makes sound on my system perfect. Subsequent uses, even from the menu, should all use OSS until you switch it again.

---

### Post by ShadowMKII on 2007-10-27
That definitely did the trick! Thank you for that! ^-^

Just wondering, but what makes the sound so different between ALSA and OSS?

---

### Post by unebaguettesvp on 2007-10-27
beautiful. thank you.

---

### Post by dfreer on 2007-10-27
Actually, one of the zsnes dev's nach has a great article on his blog about it (great read btw, wish he posted a bit more), located here:
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)
I believe he was the one who incorporated libao to the linux build as well:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=10096&highlight=&sid=41aa11df23d4f665a73899894eb1403b](http://board.zsnes.com/phpBB2/viewtopic.php?t=10096&highlight=&sid=41aa11df23d4f665a73899894eb1403b)

@unebaguettesvp
You're welcome!

---

### Post by ShadowMKII on 2007-10-28
Excellent! Thanks mate!

---

### Post by Dencrypt on 2007-11-12
Hi. First post :)

When I try to install for AMD64 (sudo apt-get install zsnes) I get the following message:

> Package zsnes is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zsnes has no installation candidate


Dunno what's wrong. The repos are allright and I made the update.

I tried the zsnes32 but that only givis me segmentation error.

I run Kubuntu AMD64 Gutsy.

---

### Post by Kymus on 2007-11-12
Everything worked fine for me up until the last part

> kymus@Shouxing:~$ zsnes -ad oss
Audio driver selection invalid.


I've checked the repo and I've got alsa-oss and libao 2 both installed.

The only options I have available are auto and sdl.

ZSNES likes to crash when I change the sound sampling rate.

---

### Post by Dencrypt on 2007-11-12
Never mind my first post. :oops:

Anyone got any more suggestions about segmentation fault? I get the error but the suggestion in the first post does not work.

---

### Post by dfreer on 2007-11-12
@Dencrypt - Hmmm, it could have something to do with using Kubuntu, although I don't see why it would be any different. Can you post the exact output when you run zsnes32 in terminal?

@Kymus - So you're using i386, and -ad oss does not seem to work? Hmmm, it may be an issue specific to your soundcard, especially considering that changing the sampling rates cause zsnes to crash on you. You can try running this command, and we can see if you have an incorrect library installed:
```
cd /usr/local/games/zsnes/
ldd ./zsnes
```
Also, I'm assuming you are using Gutsy? I can double-check and see if it's an issue with my i386 package.

---

### Post by Kymus on 2007-11-12
Hi Dfreer,

I followed your example, and this is what it spit out:

> kymus@Shouxing:/usr/local/games/zsnes$ ldd ./zsnes
        linux-gate.so.1 =>  (0xffffe000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7fa7000)
        libSDL-1.2.so.0 => /usr/lib/libSDL-1.2.so.0 (0xb7f18000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7ef4000)
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7eb0000)
        libao.so.2 => /usr/lib/libao.so.2 (0xb7eac000)
        libGL.so.1 => /usr/lib/libGL.so.1 (0xb7e22000)
        libstdc++.so.6 => /usr/local/lib/libstdc++.so.6 (0xb7d34000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d0f000)
        libgcc_s.so.1 => /usr/local/lib/libgcc_s.so.1 (0xb7d04000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7bb9000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ba1000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0xb7adb000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7ad7000)
        libdirectfb-0.9.so.25 => /usr/lib/libdirectfb-0.9.so.25 (0xb7a80000)
        libfusion-0.9.so.25 => /usr/lib/libfusion-0.9.so.25 (0xb7a7a000)
        libdirect-0.9.so.25 => /usr/lib/libdirect-0.9.so.25 (0xb7a6a000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7a5c000)
        /lib/ld-linux.so.2 (0xb7fd4000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb796b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7968000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7963000)


With ZSNES crashing.. it wasn't always like that... I've had it installed for 3 days now maybe. Originally I compiled it from the source available on the website. Then of course I was having some fuzzy sound, so I tried fidgeting with the sound sample rate and I found a rate at which it sounded *better*, but of course not perfect. Fast forward to about 24 hours later and when I would mess with it (in windowed mode) it would give me audio which wasn't to my liking and then I would fidget more and sometimes it would just go black. Nothing will terminate the window at this point (tried force quit and I tried killing itin the system monitor). Now, in full screen... oooooh, it doesn't like that very much :P. 95% of the time it will just go black and nothing will make my system respond. :eek:

inded, I am using Gutsy

Dunno if it means anything, but my sound is onboard, from my *Foxconn NF4UK8AA*

---

### Post by Dencrypt on 2007-11-16
> **dfreer said:**
> @Dencrypt - Hmmm, it could have something to do with using Kubuntu, although I don't see why it would be any different. Can you post the exact output when you run zsnes32 in terminal?.

Sure.

> dencrypt@dencrypt-desktop:~$ zsnes32
Segmentation fault (core dumped)


---

### Post by dfreer on 2007-11-16
@Dencrypt - Well, I'm not entirely sure what is causing your segmentation fault here. I installed kubuntu-desktop in AMD64 Gutsy, and was able to run zsnes32 just fine. I guess there are several options you can pursue here:
(1). Try some other zsnes binaries that I have compiled, located here:
[http://www.dfreer.org/~dfreer/zsnes/binaries/](http://www.dfreer.org/~dfreer/zsnes/binaries/)
Since they are compiled with different methods, and you already have the 32-bit libraries needed to run the program, one of them may work for you. In particular, try zsnes 1.42.
(2). Try downloading the official zsnes 32-bit .deb from the main repositories, and either extract the binary out of it, or install it like so:
```
sudo dpkg -i --force-architecture *the_official_zsnes_package*.deb
```
(3). Get a Kubuntu Gutsy i386 Live CD, and try compiling zsnes specifically for your PC. I can help you through this method if you need help.

@Kymus - It sounds like your sound card is to blame here. One thing you should try, is to move your ~/.zsnes/ folder elsewhere, and then try launching zsnes from there. It may be your configuration file is messed up from changing the sound settings, although I can't be sure.

---

### Post by Dencrypt on 2007-11-17
I couldn't get to your server (down?) but yout suggestion with dpkg worked. :) Tnx a lot :D

---

### Post by dfreer on 2007-11-18
Hmmmm... must have been one of those rolling internet storms ;). Anyways, at least you got zsnes running, which is the main thing.

---

### Post by DjBones on 2007-11-18
thanks for packaging up zsnes for 64 bit dfreer! :)
i think i got it when you posted it a while ago, but the tutorial is a nice touch lol

---

### Post by mcfly2309 on 2007-11-30
dfreer, i'm trying to get zsnes32 for debian etch amd64 but the repository doesn't work, i write the 3 commands in the terminal and with apt-get update i get an error that says something like this "Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release  file?)" (the rest is in spanish :)), what does this mean? :confused:

---

### Post by dfreer on 2007-11-30
Sorry Mcfly2309 :( The reason for your error is that there is no amd64 package for zsnes32 on debian etch. I made Debian etch i386 packages, and Debian Lenny AMD64 packages, but I haven't gotten around to making AMD64 packages for debian etch yet.

The main reason for my holdup is that the new processor I bought for my VMWare server (where I can test new packages), does not support the VT technology like advertised, and so I cannot create 64-bit clients.

I just found the [Debian Live CD]("http://debian-live.alioth.debian.org/") project, so I can probably build you a package here hopefully within a week. Just keep an eye on this thread, and I'll let you know ASAP when the package is available. EDIT: No AMD64 live cd's :(



EDIT: The amd64 repository is up for etch, now. The only packages are zsnes32 and lib32ao2 (needed for zsnes32). So you should be able to follow the instructions as before and install zsnes, please let me know if it works!!

---

### Post by spyder0080 on 2007-12-04
thanks for posting this thread! I think I've installed it right but where do I get the roms from?

---

### Post by mmxbass on 2007-12-04
> **dfreer said:**
> The main reason for my holdup is that the new processor I bought for my VMWare server (where I can test new packages), does not support the VT technology like advertised, and so I cannot create 64-bit clients.Have you tried Virtualbox or Qemu? VMWare afaik does not support virtualization on AMD cpus, only Intel ones. Would your new cpu by any chance be AMD? If so, there's a strong chance that your processor does support the necessary features, and VMWare is just too much of a sub-par product to support it.

---

### Post by dfreer on 2007-12-04
> **hexnet said:**
> Have you tried Virtualbox or Qemu? VMWare afaik does not support virtualization on AMD cpus, only Intel ones. Would your new cpu by any chance be AMD? If so, there's a strong chance that your processor does support the necessary features, and VMWare is just too much of a sub-par product to support it.

I do have an Intel CPU, according to [the newegg page]("http://www.newegg.com/Product/Product.asp?Item=N82E16819115031"), in specs it says it supports VT, whereas according to an [actual Intel page]("http://www.intel.com/products/processor_number/chart/core2duo.htm") the E4500 does not (I should've checked first, my mistake :( ).

I have not tried Virtualbox or Qemu yet, as I haven't heard of any advantage of virtualbox/qemu/zen over VMWare, other than "it's SO easy to setup". Since I don't think it's particularly hard to setup vmware server, there's no advantage there.

And I didn't realize that VMWare was a "sub-par" product -_- Honestly, I'd **really** like to know if there is any advantages, I have no particular loyalty to vmware itself.

---

### Post by dfreer on 2007-12-04
> **spyder0080 said:**
> thanks for posting this thread! I think I've installed it right but where do I get the roms from?

[Please RTF F.A.Q's]("http://ubuntuforums.org/showpost.php?p=3613605&postcount=1") -_-

---

### Post by spyder0080 on 2007-12-04
lol sorry i missed that...i skipped straight to the installation part

---

### Post by mcfly2309 on 2007-12-08
Perfect! YEA, i'm playing all the snes clasics, thanks a lot man

---

### Post by poobslag on 2007-12-11
Awesome thanks, thanks to this thread i have ZSNES running on my AMD64. Sound doesn't work yet, but i'll look around for some answers to that - thanks for all your help!!

---

### Post by dfreer on 2007-12-11
This thread has a few tricks to try, plus you might want to try fiddling with this:
```
$zsnes32 --help
-ad <>  Select Audio Driver :
                  auto = Automatically select output
                  null = Null output
                   nas = NAS output
                   oss = OSS audio driver output
                  alsa = Advanced Linux Sound Architecture (ALSA) output
                   esd = ESounD output
                  arts = aRts output
                   sdl = Simple DirectMedia Layer output

```

Don't know what your audio situation is currently like, but if your sound works at all, hopefully one of those options should help you.

---

### Post by mmxbass on 2007-12-17
I got a nice little request for something that people are having trouble compiling for AMD64.... Stepmania.... think that would be possible?

---

### Post by dfreer on 2007-12-17
I'll look into it, never heard of it but I'll see what I can do.

LOL, btw I just "thanked" you for your post. Never saw that icon before so I clicked it to see what it did :D

---

### Post by mmxbass on 2007-12-18
You never heard of stepmania? It's DDR for your PC.

---

### Post by dfreer on 2007-12-18
> **hexnet said:**
> You never heard of stepmania? It's DDR for your PC.

Lol... that's probably *why* I've never heard of it, not a DDR fan ;)

EDIT: Checking out the precompiled 32-bit binary first:
ldd tells me that there are several 32-bit libraries that will need to be installed:
```
$ ldd ./stepmania
        linux-gate.so.1 =>  (0xffffe000)[B]
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => not found
        libogg.so.0 => not found
        libmad.so.0 => not found[/B]
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7ec5000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7ead000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0xf7dbc000)
        libXtst.so.6 => /usr/lib32/libXtst.so.6 (0xf7db6000)
        libGL.so.1 => /usr/lib32/libGL.so.1 (0xf7d20000)
        libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7c9d000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7c99000)
        libz.so.1 => /usr/lib32/libz.so.1 (0xf7c84000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7b91000)
        libm.so.6 => /lib32/libm.so.6 (0xf7b6b000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7b60000)
        libc.so.6 => /lib32/libc.so.6 (0xf7a16000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7950000)
        libdirectfb-0.9.so.25 => /usr/lib32/libdirectfb-0.9.so.25 (0xf78f9000)
        libfusion-0.9.so.25 => /usr/lib32/libfusion-0.9.so.25 (0xf78f3000)
        libdirect-0.9.so.25 => /usr/lib32/libdirect-0.9.so.25 (0xf78e3000)
        /lib/ld-linux.so.2 (0xf7f73000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0xf78e0000)
        libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf78db000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0xf78cd000)
        libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf6f35000)
        libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf6f32000
```

Needed 32-bit packages:
[list]
[*] [libvorbisfile3]("http://packages.ubuntu.com/gutsy/libs/libvorbisfile3")
[*] [libvorbis0a]("http://packages.ubuntu.com/gutsy/libs/libvorbis0a")
[*] [libogg0]("http://packages.ubuntu.com/gutsy/libs/libogg0")
[*] [libmad0]("http://packages.ubuntu.com/gutsy/libs/libmad0")
[/list]

Now to repackage those for 64-bit, add them to the repository. Then, to check out the source code!


**EDIT:** Ok, so after applying 3 patches to the stepmania 3.9 source and still running into various errors, I decided just to compile from CVS. Which compiled very easily, and appears to be running great.

Here's the link to the CVS version I downloaded from sourceforge: 
[http://sourceforge.net/project/showfiles.php?group_id=37892](http://sourceforge.net/project/showfiles.php?group_id=37892)

Question is, should I go ahead and repackage the 32-bit binary of 3.9? Or did you just want to compile and package the CVS version?

---

### Post by BobCFC on 2007-12-22
Thanks for the tip about using   **-ad oss**   for sound..   everything is perfect now.

Keep up the good work!

Here's an invincibility power up just for you..... :KS   quick only lasts ten seconds lol

Cheers mate

---

### Post by mmxbass on 2008-01-02
> **dfreer said:**
> Question is, should I go ahead and repackage the 32-bit binary of 3.9? Or did you just want to compile and package the CVS version?

I'm fine with compiling it myself (already have) but it never hurts to make a package for the next guy who doesn't know how to.

---

### Post by mmxbass on 2008-01-15
I'm seeing a few other threads with people who are having trouble with stepmania such as:

[http://ubuntuforums.org/showthread.php?t=433331](http://ubuntuforums.org/showthread.php?t=433331)
[http://ubuntuforums.org/showthread.php?t=251308](http://ubuntuforums.org/showthread.php?t=251308)
[http://ubuntuforums.org/showthread.php?t=34700](http://ubuntuforums.org/showthread.php?t=34700)

Maybe a package would be nice, seeing as how some of these folks seem to have compilation troubles.

---

### Post by WenSes on 2008-01-20
Worked perfectly for me! thxs!

---

### Post by |Jasp| on 2008-01-23
Thank you all for your suggestions and support.  As it turned out, Frontend had options for memory cards.  Also, I used PSXIM to rip my game discs to .bin/.toc ~ a compatible version for pSX.  I still can't see the menus.  However, loading an image is the first option under File.  It's not too bad an issue that I can't work around.

---

### Post by rs3 on 2008-01-27
Thank you dfreer for the debs and instructions!  ZSNES was the only thing I missed in my transition to 64-bit Ubuntu, and I'm glad there's a way for me to commit to the amd64 arch and still get my emulation fix, full-stop. :)

---

### Post by mmxbass on 2008-02-07
> **hexnet said:**
> I'm fine with compiling it myself (already have) but it never hurts to make a package for the next guy who doesn't know how to.I should really check for sure before I talk. I can get it to compile fine but I didn't actually try to play it until today and I noticed a problem.

It's totally dead silent.

EDIT: OH GOD it's doing the same stupid thing that zsnes used to do. Help!

---

### Post by TygerFish on 2008-02-09
I added the dfreer.org repository info manually and then tried:
```
$ wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
...
http://packages.dfreer.org/7572013D.gpg
           => `7572013D.gpg'
Resolving packages.dfreer.org... 209.173.166.154
Connecting to packages.dfreer.org|209.173.166.154|:80... failed: Connection time  
d out.
Retrying.
...
```

Trying to go to [www.dfreer.org](www.dfreer.org) in my web browser also times out...

---

### Post by mmxbass on 2008-02-09
> **TygerFish said:**
> I added the dfreer.org repository info manually and then tried:
```
$ wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
...
http://packages.dfreer.org/7572013D.gpg
           => `7572013D.gpg'
Resolving packages.dfreer.org... 209.173.166.154
Connecting to packages.dfreer.org|209.173.166.154|:80... failed: Connection time  
d out.
Retrying.
...
```

Trying to go to [www.dfreer.org](www.dfreer.org) in my web browser also times out...That's because the server is clearly out of commission at the moment.

---

### Post by dfreer on 2008-02-12
> **hexnet said:**
> That's because the server is clearly out of commission at the moment.

Yep. Although I never did have the main page of [www.dfreer.org](www.dfreer.org) working correctly, currently the server is no longer online. I moved and I need to get a new ISP. Sorry guys :(

If there is a specific package/file you need, you can try to reach me and I will work out a way to get you what you need.

---

### Post by mmxbass on 2008-02-12
> **dfreer said:**
> If there is a specific package/file you need, you can try to reach me and I will work out a way to get you what you need.A stepmania with correct sound (unlike what happened when I compiled from cvs) would be nice. See my last 3-4 posts.

---

### Post by nickthecook on 2008-02-17
zsnes32 would be really nice to have as well! The only way I've gotten zsnes working on my x86_64 machine is using your repo...

I've got a server, and I could host a few packages for a while until you get a new one.

---

### Post by dfreer on 2008-02-17
> **hexnet said:**
> A stepmania with correct sound (unlike what happened when I compiled from cvs) would be nice. See my last 3-4 posts.

I was meaning more of packages I've already made. I had worked on stepmania at one point, but at this moment I'm running without linux so I can't really finish the package. Once I get linux installed again and start working with it, I can see about stepmania.

@nickthecook - If you can PM me with an email address, I will send you any packages you would like. It would be nice if you could mirror them on your server, I've currently been emailing them to everyone.

BTW, I can attach some of the files right now, let me know if there is any dependency issues if you use these:

---

### Post by jw5801 on 2008-02-17
Me again! Dependencies are all met for this one. Love your work!

---

### Post by hungryOrb on 2008-02-18
Hey! This sounds like a very useful tutorial, can I just say thankyou in advance :D
I would like to ask a question too, would you know how possible it would be to run zsnes 1.36 with the mirc script Znet? Or would it be a better idea to work on another script that would run on a linux irc?

---

### Post by dfreer on 2008-02-19
> **hungryOrb said:**
> Hey! This sounds like a very useful tutorial, can I just say thankyou in advance :D
I would like to ask a question too, would you know how possible it would be to run zsnes 1.36 with the mirc script Znet? Or would it be a better idea to work on another script that would run on a linux irc?

No idea actually, the zsnes forums would be the best place to ask that question.

@ Everyone - ISP is installing our new FIOS on thursday, and as long as I don't have any issues with ports the server will be back up and running soon! 
Not only that, but with 15 Mbps up/15 Mbps down :D
In comparison, the server was previously hooked up to a 2.5 Mbps down/1 Mbps up connection.

---

### Post by dfreer on 2008-02-22
So as of now, **the server is up and running on port 8080**. However, I need to test and see whether that's going to affect people using apt-get, and then of course update all of the old links/how-to's. 

Example usage would be to go to [http://packages.dfreer.org:8080/pool/](http://packages.dfreer.org:8080/pool/) and download any packages you may need.

But the optimal solution would be to get a web redirect working where all traffic to the dfreer.org domain is routed to port 8080, so that all the old links would still work. I'm struggling with that right now, hopefully I will figure it out soon. In the meantime, use port 8080.

---

### Post by aanon on 2008-02-23
Thank you **dfreer** for the AMD64 Etch binary :KS

I got silence with "Audio Open Failed" on the command line with "-ad oss" which i solved by editing
```
/etc/libao.conf
```and changing the "default_driver" from "alsa09" to "oss"

i'll be sure to check out your other guides to make my Mepis 7 laptop fun:)

---

### Post by mcfly2309 on 2008-03-01
very nice to see you back man, i was missing your lenny repository, keep up the good work!! :p

---

### Post by dfreer on 2008-04-04
Ok, just got the Hardy beta. Apparently, ia32-libs now has just about every 32-bit library a person could want (I just ran ldd on a skype 2.0 binary and zsnes 1.51, and everything is there, dunno about pSX yet).

This pretty much would nullify the need for my repository, since you could just download the binary itself now. However, I know some people (myself included) would rather just apt-get the thing and be done with it, so I'll get to work on the hardy package soon (getting the website back up is a priority).

One thing I did note, however, is that upon running ZSNES on amd64 I immediately got a seg fault, likely to do with libao being improperly packaged. It ran after I passed it the -ad null argument.

---

### Post by wingnux on 2008-04-08
wingnux@wingnux:~/Downloads$ sudo dpkg -i zsnes32_1.51-3.0_gutsy-amd64.deb
Selecting previously deselected package zsnes32.
(Reading database ... 137701 files and directories currently installed.)
Unpacking zsnes32 (from zsnes32_1.51-3.0_gutsy-amd64.deb) ...
dpkg: dependency problems prevent configuration of zsnes32:
 zsnes32 depends on lib32ao2 (>= 0.8.8-3.0); however:
  Package lib32ao2 is not installed.
dpkg: error processing zsnes32 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zsnes32


I'm running hardy beta and your repository is offline =/

EDIT: Running zsnes32 crashes with a core dumped but running it with sudo zsnes32 works fine! Anyway, it's still treated as a broken package tough =/

---

### Post by dfreer on 2008-04-08
> **wingnux said:**
> wingnux@wingnux:~/Downloads$ sudo dpkg -i zsnes32_1.51-3.0_gutsy-amd64.deb
Selecting previously deselected package zsnes32.
(Reading database ... 137701 files and directories currently installed.)
Unpacking zsnes32 (from zsnes32_1.51-3.0_gutsy-amd64.deb) ...
dpkg: dependency problems prevent configuration of zsnes32:
 zsnes32 depends on lib32ao2 (>= 0.8.8-3.0); however:
  Package lib32ao2 is not installed.
dpkg: error processing zsnes32 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 zsnes32


I'm running hardy beta and your repository is offline =/

EDIT: Running zsnes32 crashes with a core dumped but running it with sudo zsnes32 works fine! Anyway, it's still treated as a broken package tough =/

The reason why it works when using sudo, and not with your user account, is most likely because your ~/.zsnes/zsnesl.cfg file (or whatever it's called) is set to use the libao, which is not currently installed on your system.

When run with sudo, it's running as root and checking the root's home directory for the config file, which most likely is set to use another sound driver, or something to that effect.

In any case, check here for the libao package you need:
[http://ubuntuforums.org/showpost.php?p=4349199&postcount=47](http://ubuntuforums.org/showpost.php?p=4349199&postcount=47)

---

### Post by wingnux on 2008-04-09
It didn't help =/ lib32-ao conflicts with ia32-libs.

---

### Post by jerome1232 on 2008-04-16
THANK YOU! I have been banging my head on the table all day on this!

I have a i386 ubuntu server so I complied zsnes on it,
```
sudo apt-get install nasm build-essential libsdl1.2-dev zlib1g-dev libpng12-dev libncurses5-dev libao-dev
```
downloaded zsnes source code off the zsnes homepage
```
$ ./configure --with-x --enable-libao --enable-release

... code omited ...

ZSNES v1.51

SDL support                   Version 1.2.11
NASM support                  NASM version 0.98.38 compiled on Jul 31 2007
zlib support                  Version 1.2.3.3
PNG support                   Yes, version 1.2.15beta5
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

$ make

```

so on my 400mhz celeron make compiles (had a sandwich while waiting lol) perfectly
copied the binary to a nfs folder that's shared with my amd64 desktop and
```
$ zsnes
zsnes: error while loading shared libraries: libao.so.2: cannot open shared object file: No such file or directory
```
... fail, I thought well looks like it's libao

```
$ sudo apt-get install libao2
[sudo] password for jeremy:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libao2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
both fail, i figured maybe i have to have a 32bit version of libao
and hit google for an hour, no luck, came back to this forum and lo and behold my file is right here! lol

Turns out you're lib32oa package did the trick and got me running, now to the testing, thanks for all the work you've done on this man. btw how do you find 32lib packages, I googled the crap out of libao2 to no avail

---

### Post by guyminuslife on 2008-04-17
First, thanks a lot. Second, your site is down again, but I got the packages from the thread.

Third, to get lib32ao to install, I had to --force overwrite, because it deals with some of the stuff from ia32-libs. Is this going to break my system in some heinous and unpredictable way? ;-)

---

### Post by jerome1232 on 2008-04-18
@dfreer I have a server with limited resources, I could also host some files, I already have the binary I compiled and the libao2 package from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
the site is [http://mailserv.dontexist.net]("http://mailserv.dontexist.net")

---

### Post by dfreer on 2008-04-19
> **aanon said:**
> Thank you **dfreer** for the AMD64 Etch binary :KS

I got silence with "Audio Open Failed" on the command line with "-ad oss" which i solved by editing
```
/etc/libao.conf
```and changing the "default_driver" from "alsa09" to "oss"

i'll be sure to check out your other guides to make my Mepis 7 laptop fun:)

Thanks, I'll make a note of that fix!

> **jerome1232 said:**
> Turns out you're lib32oa package did the trick and got me running, now to the testing, thanks for all the work you've done on this man. btw how do you find 32lib packages, I googled the crap out of libao2 to no avail

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is a great resource for finding packages, dependencies, included files, and such. Glad it's working for you!

> **wingnux said:**
> It didn't help =/ lib32-ao conflicts with ia32-libs.

Right, which is understandable because ia32-libs now comes with libao, so my lib32ao package is trying to overwrite the same files. Best thing would be to *fix* the ia32-libs package, or at least fix it on your system, and to not use my lib32ao package at all. Check the end of this post.

Of course, then you will have the dependency problem, which sadly people will have to deal with until I get things rolling. I believe **dpkg -i --force-dependencies zsnes.deb** will help here, or something of that nature.

> **guyminuslife said:**
> First, thanks a lot. Second, your site is down again, but I got the packages from the thread.

Third, to get lib32ao to install, I had to --force overwrite, because it deals with some of the stuff from ia32-libs. Is this going to break my system in some heinous and unpredictable way? ;-)

Kinda, but it should be an easy fix. Uninstall lib32ao, uninstall/purge/reinstall ia32-libs and it should fix your system. The only really problem is the file conflict, as both packages are trying to provide the same libraries.

> **jerome1232 said:**
> @dfreer I have a server with limited resources, I could also host some files, I already have the binary I compiled and the libao2 package from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
the site is [http://mailserv.dontexist.net]("http://mailserv.dontexist.net")

I don't mind people mirroring packages, feel free to do so and post a link here if you wish. However, I'm really truly busy and may not be able to provide all of the packages for you (sides, things need updated for hardy). So basically, mirroring is appreciated but you'll need to grab the packages yourself, either from this thread or from my repository when it comes online again.



**@ Everyone with AMD64 + Hardy:**
Ok, here's the deal with zsnes. It sounds best when using libao instead of SDL and such. Since zsnes is a 32-bit program, it requires 32-bit libraries to run with. So the default libao installed on your system is 64-bit and will not work.

The original solution was to repackage the 32-bit libao library for 64-bit ubuntu. The default installation for 32-bit libraries is /usr/lib32/, so libao should be installed like so.
[LIST]
[*]/usr/lib32/ao/plugins-2/libalsa09.so
[*]/usr/lib32/ao/plugins-2/libarts.so
[*]/usr/lib32/ao/plugins-2/libesd.so
[*]/usr/lib32/ao/plugins-2/libnas.so
[*]/usr/lib32/ao/plugins-2/liboss.so
[*]/usr/lib32/ao/plugins-2/libpulse.so
[/LIST]

However, zsnes/ldd seems to want to look in /usr/**lib**/ao/plugins-2/ for these files instead of /usr/**lib32**/, if it can't find it zsnes will generally segfault when using libao for sound output. To solve this, all you need to do is **symbollically link the lib*.so files located in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/**. 

You will almost surely want to rename the files as you link them so they don't overwrite the existing 64-bit libraries (my suggestion is to rename them to lib32alsa09.so, lib32arts.so, and so on). This allows the ia32-libs package to update the 32-bit libraries located in /usr/lib32/ without complaining, and as long as it doesn't change the filenames the symbolic links in /usr/lib/ will be updated along with it. Absolutely no further need for my lib32ao package, other than that my package of zsnes will complain about it not being installed. Simply copying the files into /usr/lib/ will also work, but then if you want the updated files you'll need to do it manually yourself.

When I get around to making the hardy zsnes package, I will most likely do this symbolic link myself so you guys won't have to, but for now you'll need to do it.

This is most likely the cause of zsnes failing on hardy. Not sure whether it's the zsnes guys or the package maintainers of ia32-libs/libao2 that's to blame, but whatever. The other reason that I can think of that could be causing it to seg fault is that it just needs to be recompiled on hardy 32-bit.

If you need further help with this, just examine the files in my lib32ao package, and you should be able to see where I placed everything. Feel free to ask me questions, I'm sure that in my tiredness I messed something up in the above.

---

### Post by Ongaku86 on 2008-04-20
Hey it worked on my 64 bit AMD system except after I exit out it freezes up my whole system. I have it on fullscreen,..I don´t know if that´s a problem or anything with 64 bit but thanks alot for making it...apparently it´s the only one that supports keyboard keys :P

---

### Post by Dencrypt on 2008-04-23
I installed the zsnes32-package and got dependency problems with lib32ao2 as some other had (running hardy). The only temporary solution I have found is to put 

```
aptitude::ProblemResolver::Allow-Break-Holds "true";
```

in ~/.aptitude/config

I also had to install lib32ao2_0.8.8-3.0_gutsy-amd64.deb with 'sudo dpkg -i --force-overwrite'

Just wanted to share my solution to this.

---

### Post by Dencrypt on 2008-04-23
[empty post]

---

### Post by Ongaku86 on 2008-04-23
Update...

It freezes in windowed mode as well, I cant ctrl+alt+backspace or anything...forced to manually reboot. 

It runs great and everything, but the minute I exit out it freezes my whole system. 

I think it has something to do with my VIA chipset (K8M800), so I might just wait until I get my new mobo to play my games ^_^

---

### Post by dfreer on 2008-04-24
> **Ongaku86 said:**
> Update...

It freezes in windowed mode as well, I cant ctrl+alt+backspace or anything...forced to manually reboot. 

It runs great and everything, but the minute I exit out it freezes my whole system. 

I think it has something to do with my VIA chipset (K8M800), so I might just wait until I get my new mobo to play my games ^_^

Are you running hardy? I haven't got much of a chance to play in hardy yet... Beyond that, you could always try running a 32-bit live CD and downloading zsnes, see if you get the same freezing problem. Also, run it in a terminal, dumping the output into text file. Then hopefully if it does crash your system, you can recover the text file and see if it gave any warnings before it committed ritual suicide.

---

### Post by Eric89GXL on 2008-04-27
> **dfreer said:**
> 
... To solve this, all you need to do is **symbollically link the lib*.so files located in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/**. 

You will almost surely want to rename the files as you link them so they don't overwrite the existing 64-bit libraries (my suggestion is to rename them to lib32alsa09.so, lib32arts.so, and so on)...

Feel free to ask me questions, I'm sure that in my tiredness I messed something up in the above.

I tried installing the old zsnes32 package with -force-depends, and then did the symbolic linking appropriately. After linking, the drivers showed up in the zsnes help, but didn't work when I tried to use them (e.g. zsnes32 -ad alsa). Zsnes32 wouldn't crash, but there was no sound. Using alsa there were no errors, using oss it complained that it was "unable to open slave", and it failed to open the other drivers at all, but would play without sound.

Did this procedure work for you?

---

### Post by yns88 on 2008-04-27
> **Eric89GXL said:**
> I tried installing the old zsnes32 package with -force-depends, and then did the symbolic linking appropriately. After linking, the drivers showed up in the zsnes help, but didn't work when I tried to use them (e.g. zsnes32 -ad alsa). Zsnes32 wouldn't crash, but there was no sound. Using alsa there were no errors, using oss it complained that it was "unable to open slave", and it failed to open the other drivers at all, but would play without sound.

Did this procedure work for you?

This is probably an issue with the fact that Hardy uses Pulseaudio for just about everything (I've had the same issue with a number of emulators). 

If you're running zsnes from the terminal, you can type "padsp zsnes [options]" to run a pulseaudio layer for oss (If you don't have padsp, it shouldn't be hard to look it up and find a way to install it).

If you're running zsnes from your applications menu, you can right click on Applications, go to Edit Menus, double click on the application or right click and select Properties, and then change the command to "padsp zsnes" (assuming the command was originally just "zsnes").

I'm still waiting on dfreer to put together something for hardy, since I've just started using linux and don't want to make any bad mistakes playing with the file system ;)

---

### Post by Eric89GXL on 2008-04-27
> **yns88 said:**
> This is probably an issue with the fact that Hardy uses Pulseaudio for just about everything (I've had the same issue with a number of emulators). 

I don't have pulseaudio installed because it doesn't allow for bit-perfect SPDIF output (e.g. [http://pulseaudio.org/ticket/167](http://pulseaudio.org/ticket/167)). It's possible that not having pulseaudio has something to do with it, but everything other app thus far has worked correctly (Amarok, Mplayer, mupen64plus, fceu, ...).

---

### Post by Saghaulor on 2008-04-30
> **yns88 said:**
> This is probably an issue with the fact that Hardy uses Pulseaudio for just about everything (I've had the same issue with a number of emulators). 

If you're running zsnes from the terminal, you can type "padsp zsnes [options]" to run a pulseaudio layer for oss (If you don't have padsp, it shouldn't be hard to look it up and find a way to install it).

If you're running zsnes from your applications menu, you can right click on Applications, go to Edit Menus, double click on the application or right click and select Properties, and then change the command to "padsp zsnes" (assuming the command was originally just "zsnes").

I'm still waiting on dfreer to put together something for hardy, since I've just started using linux and don't want to make any bad mistakes playing with the file system ;)

Hey Dfreer, when are you going to write a Hardy Heron version of Zsnes? I upgraded from Gutsy and now I'm poop out of luck. 

Anyways, thanks for the work so far. I had Zsnes working beautifully in Gutsy on my AMD64. Just can't wait until you get it going for Hardy.

---

### Post by twinoatl on 2008-05-02
> **Saghaulor said:**
> Hey Dfreer, when are you going to write a Hardy Heron version of Zsnes? I upgraded from Gutsy and now I'm poop out of luck. 

Anyways, thanks for the work so far. I had Zsnes working beautifully in Gutsy on my AMD64. Just can't wait until you get it going for Hardy.

Hi,

I'm also interested in a hardy version of zsnes. Moreover, it seems your server is currently down.

---

### Post by unebaguettesvp on 2008-05-02
hi!

since upgrading to hardy, i am having problems with the sound. i tried a bunch of different sound drivers. using the --help option gave this:

```

  -ad <>  Select Audio Driver :
                  auto = Automatically select output
                  null = Null output
                   nas = NAS output
                   oss = OSS audio driver output 
                  alsa = Advanced Linux Sound Architecture (ALSA) output
                   esd = ESounD output
                 pulse = PulseAudio Output
                  arts = aRts output
                   sdl = Simple DirectMedia Layer output

```

none of them work except for sdl. i thought this solved it but some of the games have strange sounds, meaning they sound kind of garbled(?).

i used to use alsa and it worked pretty well (minus some distorted sounds) and i would much rather be using that driver.

anyone get any of these others to work using dfreer's package from gutsy?

thanks!

---

### Post by Eric89GXL on 2008-05-03
Nope, I have the same problems you have. Lots of options, none work except the buggy SDL.

---

### Post by Saghaulor on 2008-05-03
I pmed DFreer about Zsnes for Hardy, and about his server, and this is what he said.

 Re: Server down
Quote:
Originally Posted by Saghaulor
Any word on when it will be up?
Quote:
Originally Posted by Dfreer
Soon, Hopefully. Right now, the packages I've made are pretty much useless for hardy, I'm working on getting zsnes and hardy to play nice with each other.

---

### Post by chefpro on 2008-05-07
I am also interested in zsnes in ubuntu amd64 and hardy.

---

### Post by dfreer on 2008-05-09
@Everyone who has waited so long...

Try [http://packages.dfreer.org](http://packages.dfreer.org) :D
You should be able to use the repository once more, without the port 8080.

Still working on hardy though...

---

### Post by shanepardue on 2008-05-12
> **dfreer said:**
> @Everyone who has waited so long...

Try [http://packages.dfreer.org](http://packages.dfreer.org) :D
You should be able to use the repository once more, without the port 8080.

Still working on hardy though...
I'm still not able to fetch packages on Gutsy or Hardy with your repository.

---

### Post by dfreer on 2008-05-13
> **shanepardue said:**
> I'm still not able to fetch packages on Gutsy or Hardy with your repository.

I'm not having any issues reaching the website from proxy sites or from work. Is your /etc/apt/sources.list file correct? Also, it could possibly be an error with the repository itself and not the website, does apt-get return any useful info?

---

### Post by jw5801 on 2008-05-13
> **dfreer said:**
> I'm not having any issues reaching the website from proxy sites or from work. Is your /etc/apt/sources.list file correct? Also, it could possibly be an error with the repository itself and not the website, does apt-get return any useful info?

I'm thinking it's probably because we're after a Hardy repo which doesn't exist yet. Using:
```
deb http://packages.dfreer.org hardy main
```
I get:
```
W: Failed to fetch http://packages.dfreer.org/dists/hardy/main/binary-amd64/Packages.gz  302 Found
```

---

### Post by shanepardue on 2008-05-13
> **dfreer said:**
> I'm not having any issues reaching the website from proxy sites or from work. Is your /etc/apt/sources.list file correct? Also, it could possibly be an error with the repository itself and not the website, does apt-get return any useful info?
W: Failed to fetch [http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz](http://packages.dfreer.org/dists/gutsy/main/binary-amd64/Packages.gz)  302 Found

I am running Hardy, but using the Gutsy repo. I'm assuming it doesn't have any amd64 packages.

---

### Post by dfreer on 2008-05-13
Hmmm... it seems to work from here... I wonder if it has to do with the webhop? It seems further testing is in order.

You should be able to reach the gutsy amd64 packages manually here:
[http://packages.dfreer.org/pool/](http://packages.dfreer.org/pool/)

---

### Post by shanepardue on 2008-05-13
> **dfreer said:**
> Hmmm... it seems to work from here... I wonder if it has to do with the webhop? It seems further testing is in order.

You should be able to reach the gutsy amd64 packages manually here:
[http://packages.dfreer.org/pool/](http://packages.dfreer.org/pool/)
Thanks! I'm available for helping you test if you need help. I'm anxious to get ZSNES 
working on this machine. However, I am running Hardy and you're working to get this 
working in Gutsy?

---

### Post by dfreer on 2008-05-14
> **shanepardue said:**
> Thanks! I'm available for helping you test if you need help. I'm anxious to get ZSNES 
working on this machine. However, I am running Hardy and you're working to get this 
working in Gutsy?

I have repos for gutsy, feisty, dapper, and debian stable/unstable (been working with zsnes for some time now). However, I haven't created the hardy repo yet because ZSNES + Hardy + pulseaudio == giant mess.

If you figure out how to get OSS sound with libao to actually work with pulseaudio, I can incorporate it into hardy package.


EDIT: I'm actually seriously considering making the hardy zsnes package conflict with pulseaudio, I like the idea of pulseaudio but I'd rather have sound working perfectly like before.

---

### Post by twinoatl on 2008-05-14
> **dfreer said:**
> EDIT: I'm actually seriously considering making the hardy zsnes package conflict with pulseaudio, I like the idea of pulseaudio but I'd rather have sound working perfectly like before.

+1. I have deactivated pulseaudio just by removing it through aptitude. The only dependency is ubuntu-desktop. Now, things are working way better for me. I read other people did the same. So I would really like a zsnes version for hardy which do not depend on pulseaudio to work.

---

### Post by dfreer on 2008-05-15
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11510](http://board.zsnes.com/phpBB2/viewtopic.php?t=11510)

Things are looking good, thanks to Nach (once again)! Still working on the repository.

EDIT: In case anyone didn't bother to click the link, it contains a patch for zsnes 1.51 that fixed the sound issues for at least me. It also contains a link to binaries with this patch already included.

---

### Post by drunkmatador on 2008-05-15
So I tried this again and it worked. Maybe I was doing something wrong before.

Except for the sound it's great. Is the sound not supposed to be working yet or is that something I'm doing wrong?

---

### Post by dfreer on 2008-05-15
> **drunkmatador said:**
> So I tried this again and it worked. Maybe I was doing something wrong before.

Except for the sound it's great. Is the sound not supposed to be working yet or is that something I'm doing wrong?

Did you try the new 1.51b binaries or compile it yourself for hardy? Or did you not read the post directly above yours? :popcorn:

---

### Post by shanepardue on 2008-05-16
> **dfreer said:**
> Hmmm... it seems to work from here... I wonder if it has to do with the webhop? It seems further testing is in order.

You should be able to reach the gutsy amd64 packages manually here:
[http://packages.dfreer.org/pool/](http://packages.dfreer.org/pool/)
Do the packages for Gutsy usually work in Hardy on and AMD64 machine? I get a failed installation on the lib32ao2_0.8.8-3.0_gutsy-amd64.deb package.

Thanks for any input!

---

### Post by dfreer on 2008-05-16
> **shanepardue said:**
> Do the packages for Gutsy usually work in Hardy on and AMD64 machine? I get a failed installation on the lib32ao2_0.8.8-3.0_gutsy-amd64.deb package.

Thanks for any input!

It really depends on the package. My libao package will certainly fail due to reasons mentioned here:
[http://ubuntuforums.org/showpost.php?p=4744755&postcount=61](http://ubuntuforums.org/showpost.php?p=4744755&postcount=61)

In this case however, especially now that Nach has provided us with a patch for znses, it is probably best to either wait for a hardy package or install zsnes manually.

This is what I would do:
[LIST]
[*]Uninstall any packages you may have already installed
[*]Download a 1.51b binary here:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)
[*]Symbolically link the files in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/
You'll probably want to rename them when linking them, as their are already files of the same name in that folder.
[*]Run the binary for the first time with zsnes -ad oss.
[*]Enjoy!
[/LIST]

---

### Post by shanepardue on 2008-05-17
With his files, I downloaded one, extracted it and ran ./zsnes..this is my error message..

```
Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Segmentation fault

```

It appeared to be a mouse problem so I even tried it with the -j argument to disable the mouse, but it still results with the same error and a crash.

---

### Post by dfreer on 2008-05-18
Which binary did you download, did you download one appropriate for your CPU? Try running ldd on zsnes. Also, did you do the symbolic link?

EDIT: Better just ask, what CPU do you have?

---

### Post by shanepardue on 2008-05-18
> **dfreer said:**
> Which binary did you download, did you download one appropriate for your CPU? Try running ldd on zsnes. Also, did you do the symbolic link?

EDIT: Better just ask, what CPU do you have?
AWESOME! I don't know what I missed before, but I got it working now! Thanks a lot of your help!

Are you planning on adding this to your repo also?

---

### Post by shanepardue on 2008-05-26
ZSNES is running just great these days, but out of nowhere I'm not able to load a rom 
now. When I click the rom, it just reverts back to the menu as if nothing happened. I 
ran it from the terminal, but that gives no output on the error. Please help!

---

### Post by shanepardue on 2008-05-27
> **shanepardue said:**
> ZSNES is running just great these days, but out of nowhere I'm not able to load a rom 
now. When I click the rom, it just reverts back to the menu as if nothing happened. I 
ran it from the terminal, but that gives no output on the error. Please help!
It's just this one rom..It worked fine and now it doesn't. Is it possible the rom became corrupt?

---

### Post by Hooya on 2008-06-18
Hey dfreer, thanks for your work on this problem.  I've tried compiling my own build of the experimental builds on two different machines with no luck on either one.  I've tried compiling my own and also tried the ready-made builds on the zsnes forums.  All give me segmentation fault during the sound check (after 0 mice detected).

One computer is an Intel Celeron, the other is on Athlon 64 3200+.  1.51 works on the Celery, but no sound with anything but sdl, and sdl sounds like crap and often crashes really hardcore and I have to reboot before zsnes will run normally again.

I guess I'm just wondering if there's any new progress on this yet or if you have any suggestions on how to fix it, since some people have got it working well.

Edit: Finally got the one from the repositories working on the Celery machine using one of the posted workarounds.  I was missing the "must reboot to work" step.  Still no luck at all getting an x64 version working though.

Edit:  OK, Got it working on 64-bit, and here's how, rather than build my own I followed the directions given by Cappy here: [http://ubuntuforums.org/showpost.php?p=4816225&postcount=2](http://ubuntuforums.org/showpost.php?p=4816225&postcount=2)
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2ubuntu1_i386.deb
sudo dpkg --force-all -i zsnes_1.510-2ubuntu1_i386.deb
```
Now you'll get the segfault if you just try to run zsnes, so I decided, the error is coming from the sound module, so just like in x86, run "$ zsnes -ad sdl" the first time to force SDL for the sound layer and it works.  Using the same command with oss or alsa options gave an invalid sound driver error.

Other people have found this working as well, but I only have just now found one post about it, so I'm posting this for anyone else who has these problems and might find the answer here.

---

### Post by themostunoriginalname on 2008-06-29
:~/zsnes_1_51/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__LIBAO__ -D__OPENGL__ -march=pentium-m -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__ -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
make: *** [tools/fileutil.o] Error 1


I'm using a Intel Core 2 Duo T8100 wiht 64-bit gutsy, so O_O?

---

### Post by HonorSystem on 2008-06-29
> **dfreer said:**
> It really depends on the package. My libao package will certainly fail due to reasons mentioned here:
[http://ubuntuforums.org/showpost.php?p=4744755&postcount=61](http://ubuntuforums.org/showpost.php?p=4744755&postcount=61)

In this case however, especially now that Nach has provided us with a patch for znses, it is probably best to either wait for a hardy package or install zsnes manually.

This is what I would do:
[LIST]
[*]Uninstall any packages you may have already installed
[*]Download a 1.51b binary here:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)
[*]Symbolically link the files in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/
You'll probably want to rename them when linking them, as their are already files of the same name in that folder.
[*]Run the binary for the first time with zsnes -ad oss.
[*]Enjoy!
[/LIST]
Just wanted to say thanks, dfreer.  Also, a big thanks to Nach for his efforts as well.  This comes despite his coming off like a linux elitest *** in that post you linked to, dfreer.  Does he not realize that Ubuntu is geared towards "everyone" which includes noob converts from windows like myself?

Anyway, your method described above with the symlinks worked well for me (i just renamed all the links to lib32*.so).  After that, ./zsnes without any switches works perfect out-of-the-box for me.  I should probably note, though, that I am using OSSv4 with ALSA and PulseAudio disabled and all but entirely gone from my system.

NOTE: I didn't do that just for zsnes, though, trust me.  Rather than relate my headaches with sound, I'll let this guy sum it up in a more generalized way: [http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html]("The Sorry State of Sound in Linux")

---

### Post by dfreer on 2008-06-29
EDIT:> **shanepardue said:**
> It's just this one rom..It worked fine and now it doesn't. Is it possible the rom became corrupt?

Possibly. You should be able to replace the ROM without destroying your saved games/saved states, just make sure to rename the new ROM to the same name as the old one. BTW, the errors you mentioned on the last page concerning the mouse are quite normal, just ignore them:
```

Unable to poll /dev/input/event6. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

```

The segmentation fault has nothing to do with them.

> **HonorSystem said:**
> Also, a big thanks to Nach for his efforts as well.  This comes despite his coming off like a linux elitest *** in that post you linked to, dfreer.

...

Rather than relate my headaches with sound, I'll let this guy sum it up in a more generalized way: [http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html]("The Sorry State of Sound in Linux")

BTW, just in case you didn't know, Nach is the author of that blog you linked to. Just thought it funny :D
EDIT: also, that link is broken. The correct link is this:
[http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html](http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html)

When I was last playing with linux, OSS4 worked amazingly well on my system. I'm glad you got zsnes working!

> **themostunoriginalname said:**
> :~/zsnes_1_51/src$ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__LIBAO__ -D__OPENGL__ **-march=pentium-m** -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__ -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
make: *** [tools/fileutil.o] Error 1


I'm using a Intel Core 2 Duo T8100 wiht 64-bit gutsy, so O_O?

For one, you **cannot** compile zsnes as a 64-bit binary. I also have not successfully been able to compile zsnes as a 32-bit binary **from** a 64-bit system. Although that might just be me being dumb, I haven't tried it for quite some time.

Furthermore, the march you'd want to use is core2 or possibly nocona, and not pentium-m.

If you can't use one of the binaries linked here:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)
I'd suggest grabbing a Hardy i386 Live CD, installing these two packages:
```
sudo apt-get install build-essential libao-dev
sudo apt-get build-dep zsnes
```
Then, using the source code linked above, try compiling zsnes like so:
```
./configure --enable-libao --enable-release force_arch=core2
```

Also, if you are really dead set on compiling in x86_64, basically you need to tell gcc that you want a 32-bit binary, by passing it some options. This thread might help you with that part, although it's for SuSE linux it should still be of use:
[http://forums.opensuse.org/archives/sf-archives/64-bit/341279-need-help-compiling-zsnes-64-bit-10-3-a.html](http://forums.opensuse.org/archives/sf-archives/64-bit/341279-need-help-compiling-zsnes-64-bit-10-3-a.html)

---

### Post by Pauan on 2008-07-02
I thank you so very much! I had such an impossible time getting this to work in Hardy (darn you PulseAudio!), so I just installed Debian Lenny.

I, too, couldn't connect to the repository via apt-get or Synaptic. However, manually browsing to the repository and hand-installing the files with dpkg worked fine.

Now ZSNES works great! :) Thank you so much!

**EDIT:** I seemed to have jumped the gun a bit. Sound doesn't work at all.
I have tried -ad auto, -ad oss, -ad alsa09, -ad arts, -ad nas, and -ad sdl. None work. Sound works flawlessly everywhere else.

**Note:** I am not on Hardy and am _not_ using PulseAudio.
Also, -ad oss, -ad nas, and -ad arts print "Audio Open Failed" in the terminal. Everything else prints "Audio Opened."

I don't seem to have aRts installed, so I'd expect it not to work.

Lastly, I have the package libsdl1.2debian-all installed.

**EDIT:** SDL works now (not too sure how it got fixed), but it sounds quite scratchy with a lot of problems.

I tried every single sampling rate, but they all either have no sound, or bad quality.

Also note that I had no problems at all on 32-bit, so it isn't a problem with my hardware.

---

### Post by NacIK on 2008-07-12
OK, now I am completely lost.  Can you post a step-by-step amd64 Hardy install for someone just learning linux?  :confused:

---

### Post by Barina on 2008-07-12
Joining NacIK's request :)
a step-by-step amd64 hardy tutorial for newbies

---

### Post by dfreer on 2008-07-13
> **NacIK said:**
> OK, now I am completely lost.  Can you post a step-by-step amd64 Hardy install for someone just learning linux?  :confused:

> **Barina said:**
> Joining NacIK's request :)
a step-by-step amd64 hardy tutorial for newbies

Alright, since it's been long since overdue...

Do the following:
```
echo "deb http://rowdy.dfreer.org:8080 hardy main" | sudo tee -a /etc/apt/sources.list 
wget http://rowdy.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
sudo apt-get install zsnes32

zsnes32 -ad oss ## First run ##
zsnes32 ## all subsquent runs, or just launch through the menu ##
```

Yes, this means **the repository is back up**! I need to get things working, such as pSX for AMD64 Hardy and new debian lenny packages, but all the old stuff is there and the old releases (feisty, gutsy, etch) should work as expected. I'll have the front page updated soon and make some announcements later.

Please note: 
-- You need to remove my old repository lines from your /etc/apt/sources.list, if you have them. They should look something like this:
```
deb http://packages.dfreer.org gutsy main
```
-- I added the man page for zsnes32 in hardy, try it out!
```
man zsnes32
```

Let me know of any problems, it's been awhile since I've made packages I may have done it wrong!




@ Pauan - Sorry I missed your post. Try doing the following:
[LIST=1]
[*]Download the attached zsnes binary
[*]Place it in /usr/local/games/zsnes32/
[/LIST]
Then:
```
sudo chown root:root /usr/local/games/zsnes32/zsnes
sudo chmod a+x /usr/local/games/zsnes32/zsnes
sudo rm /usr/bin/zsnes32
sudo ln -s /usr/local/games/zsnes32/zsnes /usr/bin/zsnes32
```

Make sure you have this package installed:
[http://packages.dfreer.org/pool/lenny/main/lib32ao2_0.8.6-1.2_amd64.deb](http://packages.dfreer.org/pool/lenny/main/lib32ao2_0.8.6-1.2_amd64.deb)

Then delete your old configuration in case there is a problem with it:
```
sudo rm ~/.zsnes/zsnesl.cfg
```

Then run zsnes. The first time, run it in the terminal like so:
```
zsnes32 -ad oss
```
If sound is scratchy, try playing with the sampling level. If sound still doesn't output for you, please provide me with the following:
```
ldd /usr/bin/zsnes32
ls -l /usr/lib/ao/plugins-2/
cat /proc/cpuinfo
```

It may be that I'll need to recompile a binary for you.

You may also want to check this thread out (everyone should who doesn't really know zsnes or are having sound problems):
[http://ubuntuforums.org/showthread.php?t=851396&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=851396&highlight=zsnes)

---

### Post by Pauan on 2008-07-13
> **dfreer said:**
> If sound still doesn't output for you, please provide me with the following:
```
ldd /usr/bin/zsnes32
ls -l /usr/lib/ao/plugins-2/
cat /proc/cpuinfo
```
Didn't work. Here's the outputs you wanted.

I already had lib32ao2 installed from your repository, but just to be safe I reinstalled it from the link you gave me.

I tried -ad oss, -ad alsa09, -ad esd, and -ad sdl. Same thing as before.

**P.S.** Oh yeah, and I tried to upgrade zsnes32 from your repository, and got this:

```
E: /var/cache/apt/archives/zsnes32_1.510b-3.5_amd64.deb: trying to overwrite `/usr/lib/ao/plugins-2/lib32nas.so', which is also in package lib32ao2
```

Guess that's what I get for being impatient. ;)

---

### Post by dfreer on 2008-07-13
> **Pauan said:**
> Didn't work. Here's the outputs you wanted.

I already had lib32ao2 installed from your repository, but just to be safe I reinstalled it from the link you gave me.

I tried -ad oss, -ad alsa09, -ad esd, and -ad sdl. Same thing as before.

**P.S.** Oh yeah, and I tried to upgrade zsnes32 from your repository, and got this:

```
E: /var/cache/apt/archives/zsnes32_1.510b-3.5_amd64.deb: trying to overwrite `/usr/lib/ao/plugins-2/lib32nas.so', which is also in package lib32ao2
```

Guess that's what I get for being impatient. ;)

Alright, I'll have to get Debian Lenny fired up. I need to update the debian etch/lenny repos anyways.

Indeed, that package is for ubuntu hardy only. Ubuntu's ia32-libs package is significantly different from Debian Lenny's. The binary that I gave you is the same binary that package contains anyways ;)

---

### Post by lgshort on 2008-07-13
this is just beautiful.  I can't thank you enough for updating the repo for hardy.  I been without for far too long.

---

### Post by jerome1232 on 2008-07-13
> **lgshort said:**
> this is just beautiful.  I can't thank you enough for updating the repo for hardy.  I been without for far too long.

I second that, now time for some Zelda - A link to the past :D

---

### Post by dfreer on 2008-07-13
Thanks guys! It's been far too long since I've updated things :D

@ Pauan - I'm on Default Gnome Desktop install of Debian Lenny 64-bit, and sound is working in zsnes for me. I am using a newer version of the 32-bit libao2 package then you, and a binary built in Debian Lenny 32-bit, so maybe that could be the issue. I've attached the zsnes binary I'm using (built for a generic i586 machine), try it.

Beyond that, I'll be getting a package made soon including an updated lib32ao2 in the Debian Lenny repository. But I suspect there may be another reason why zsnes isn't outputting any sound for you, have you tinkered with any sound settings/installed OSS4/pulseaudio or anything?

EDIT: oops, forgot the attachment ;)

---

### Post by Pauan on 2008-07-13
> **dfreer said:**
> But I suspect there may be another reason why zsnes isn't outputting any sound for you, have you tinkered with any sound settings/installed OSS4/pulseaudio or anything?
I did install OSS4 once, but purged it shortly afterwards. I haven't particularly tweaked any sound settings... except for /etc/libao.conf. I changed the default_driver from alsa to oss. Changing it back to alsa had no effect.

I haven't installed PulseAudio (it was the reason I went to Debian), and as far as I know, sound in ZSNES didn't work even before installing OSS4; though I could be wrong.

**EDIT:** No attached file? ;)

---

### Post by Pauan on 2008-07-14
Hey, the sound works on the file you attached! Sounds really great. :)

I can use this until you get the repository updated. Thank you so much!

**EDIT:** -ad oss doesn't work, but -ad alsa09 and -ad esd does. Sound quality seems top-notch (considering it's a SNES game).

---

### Post by dfreer on 2008-07-14
> **Pauan said:**
> Hey, the sound works on the file you attached! Sounds really great. :)

I can use this until you get the repository updated. Thank you so much!

**EDIT:** -ad oss doesn't work, but -ad alsa09 and -ad esd does. Sound quality seems top-notch (considering it's a SNES game).

My -ad oss is working, so I'm guessing that's a specific problem with your install. At least you have decent sound now, glad to help!

---

### Post by Tolaris on 2008-07-16
Dan,

Thank you, sincerely, from the bottom of my heart for your hard work on this.  Moving to amd64 has been a trial.  I'm an avid NES/SNES collector and player, and I have a complete ROM collection that I just love taking with me.  I was about to resort to running WinXP in VirtualBox just to play ZSNES.

I have a number of SNES pads modified with USB:

[http://retrousb.com/](http://retrousb.com/)

Would you care for a USB->SNES adaptor cable, on me?  You deserve it.  Contact me in a private message with your email, and I'll arrange it.

---

### Post by KiddDaBeauty on 2008-07-28
*EDIT: Haven't found any real fix for the problem, but I've narrowed down the source ^_^x; Apparantly zsnes (on my compy here) won't play any sound when Firefox is playbacking any flash videos. Gonna try another flash player ^_^x; Leaving post here for other people to see, in case anyone has any input or wants to read on my progress if they get the same problem or something...*

I'm so completely at a loss now. I followed your Hardy installation process, dfreer, and I must start out by saying it's amazing how much time you spend just helping people with their problems getting things to work here :)

The sound in zsnes used to work just fine, even without the special version Nach posted. And now, all of a sudden, it stopped working o_Ox

When I try running it with **-ad oss**, **-ad alsa** and **-ad sdl**, this is what I get:

```
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA snd_pcm_open error: Device or resource busy
Audio Open Failed
ZSNES could not find any joysticks.
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

(You can ignore the joysticks thing I suppose :P Just kept in there to keep the thing complete)

And when I use **-ad alsa09** it says:

```
Audio driver selection invalid.
```

But now for the interesting part. **-ad esd** gives me great sounding sound, however it lags behind by like half a second or so (the sound never used to do this) and the terminal still looks funny:

```
Audio Opened.
Driver: ESounD output
Channels: 2
Rate: 48000

ZSNES could not find any joysticks.
ALSA lib ../../../src/pcm/pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

So I suppose something really is up with this pcm_dmix.c file? What do I do? Other programs can use my sound just fine... :\

---

### Post by vilon on 2008-08-19
Hi, and thanks a lot for packaging zsnes! It mostly works like a charm. I have a question: am I the only one who notices that zsnes and compiz don't play well together? It's not a big problem, compiz is easy enough to turn off, I'm just curious.

---

### Post by Eric89GXL on 2008-08-19
My ZSNES and compiz are best friends on two of my computers. (Thanks Dfreer for the repository and packages, by the way.) What's your issue? I run an NVIDIA 7600GT, proprietary drivers on one computer; Intel X3100, open drivers on another.

---

### Post by Saghaulor on 2008-08-23
Mr. Freer, you are a god send. Thank you for sharing with us your most valuable time and energy.

---

### Post by MaindotC on 2008-09-30
Hey, Freer.  Thank you so much for supporting Zsnes on Hardy 64!  Now if I can get zbattle.net working...

---

### Post by jerome1232 on 2008-10-08
Well I just got Intrepid Ibex and to my horror your (dfreer) repositories don't seem to be hosting the packages any more? The site works it's just doesn't have any packages it seems.

Well hopefully I can find a copy of the .deb I've depended on you for my zsnes :).


edit: Okay you do seem to still be hosting the file here [http://rowdy.dfreer.org:8080/pool/hardy/main/zsnes32_1.51b-3.5_hardy-amd64.deb](http://rowdy.dfreer.org:8080/pool/hardy/main/zsnes32_1.51b-3.5_hardy-amd64.deb) it's just not reachable from the main site.

---

### Post by Tolaris on 2008-10-09
jerome1232, I can download the package just fine.  My sources for dfreer:

```
tyler@baal:~$ cat /etc/apt/sources.list.d/dfreer.list
deb http://rowdy.dfreer.org:8080 hardy main

tyler@baal:~$ apt-cache -o Dir::Etc::sourceparts=/dev/null -o Dir::Etc::SourceList=/etc/apt/sources.list.d/dfreer.list dumpavail

Package: zsnes32
...
```

And I'm able to download zsnes32.  I'm still running hardy.  Just use the "hardy" repo with intrepid, and it should work.  If not, it's likely you'll have to wait a few months for Dan to repackage it, if he's going to.

---

### Post by jerome1232 on 2008-10-09
Yeah your right, I must've made a typo the first time I added the repo.

---

### Post by dfreer on 2008-10-09
Indeed, there's no Intrepid repository as of now. Also, because my ISP blocks port 80, if your /etc/apt/sources.list has the following:
deb [http://packages.dfreer.org](http://packages.dfreer.org) hardy main
When trying to apt-get, you will recieve an error. Whereas:
deb [http://rowdy.dfreer.org:8080](http://rowdy.dfreer.org:8080) hardy main
Should work just fine. The reason for this I believe is that apt-get is unable/unwilling to accept web redirection, which is what I use. [http://packages.dfreer.org](http://packages.dfreer.org) will work just fine in a web browser, although you should notice that you are immediately redirected to [http://rowdy.dfreer.org:8080](http://rowdy.dfreer.org:8080).

I'm kinda curious as to how everyone is now calling me by a first/last name basis lol :p

---

### Post by jerome1232 on 2008-10-09
Idk; :) and btw the hardy package works great under Intrepid for me.

---

### Post by dfreer on 2008-10-09
Downloaded the beta for Intrepid today, tried it from the live CD. My ethernet card was not working, most likely due to the e1000 driver being disabled in Intrepid because of a nasty firmware bug. I also was unable to get anything that used ALSA to output sound, this hopefully will be fixed when they release 8.10. 

So testing pSX was instantly out, since it will crash unless it's able to output sound and only outputs via ALSA. Tried the ZSNES i386 binary that's in the Intrepid repositories, it gave me a nasty buffer overflow crash. Compiled the 1.51b source myself, same crash. Compiled it again using gcc-4.1, worked fine (other than that I was unable to use ALSA, only OSS).

Once Intrepid gets out of beta, I might try again. Until then, Hardy should hopefully work for everyone.

---

### Post by ynell on 2008-10-16
Am i the only one who's had trouble installing 1.42?

I ran into some of the Super Mario RPG bugs while running 1.51 and it seems the only solution thus far is to downgrade to 1.42 or 1.36

I've tried installing from deb but it doesn't show up in synaptic and I'm still trying to get used to the way linux installs things.

does anyone host a 1.42 so i can just do an apt-get? or maybe direct me to a newb-friendly guide xD

---

### Post by jerome1232 on 2008-10-16
> **ynell said:**
> Am i the only one who's had trouble installing 1.42?

I ran into some of the Super Mario RPG bugs while running 1.51 and it seems the only solution thus far is to downgrade to 1.42 or 1.36

I've tried installing from deb but it doesn't show up in synaptic and I'm still trying to get used to the way linux installs things.

does anyone host a 1.42 so i can just do an apt-get? or maybe direct me to a newb-friendly guide xD

I'm compiling 1.42 right now if I can't get it compiled on my 64-bit machine (I've had problems in the past) then I'll have to have my 400mhz computer do it... might take a while do get it compiled for you if I have to use that computer.

---

### Post by ynell on 2008-10-16
you don't have to go through all that xD i could try and do it myself if you wanted to link me somewhere haha

But i also am running amd64

thanks for your help :]

---

### Post by dfreer on 2008-10-16
> **jerome1232 said:**
> I'm compiling 1.42 right now if I can't get it compiled on my 64-bit machine (I've had problems in the past) then I'll have to have my 400mhz computer do it... might take a while do get it compiled for you if I have to use that computer.

I've never been able to compile on a 64-bit machine, trying GCC flags to compile for 32-bit targets and such never worked. Using a chroot worked quite well though, or using a Live CD also works :D

> **ynell said:**
> Am i the only one who's had trouble installing 1.42?

I ran into some of the Super Mario RPG bugs while running 1.51 and it seems the only solution thus far is to downgrade to 1.42 or 1.36

I've tried installing from deb but it doesn't show up in synaptic and I'm still trying to get used to the way linux installs things.

does anyone host a 1.42 so i can just do an apt-get? or maybe direct me to a newb-friendly guide xD

I went through my archives and this is what I came up with. Dunno if they will help or not. IIRC, I made these packages for Gutsy. One is a specific build designed for netplay, the other is the standard 1.42 release. They will use the same .zsnes/ configuration files as each other/1.51, so I'd be aware of that as it may cause problems if you have install more than one.

---

### Post by ynell on 2008-10-16
sweet thanks a ton dfreer, used the standard 1.42 and it works perfectly :] your the man :guitar:


Jerome thanks for you good intentions, i appreciate it :)

---

### Post by jerome1232 on 2008-10-16
Lol, well I guess I can stop that computer from compiling (man is it slow!)

---

### Post by ynell on 2008-10-16
Haha yeah nothing worse than a slow computer xD thanks anyways man :]

---

### Post by JayBee808 on 2008-10-24
Just wanted to report the zsnes32_1.51b3.5_hardy-amd64.deb is working great for me in Intrepid Ibex w/Compiz running.

I followed this procedure to get my gamepad working:
[http://ubuntuforums.org/showpost.php?p=6023212&postcount=5]("http://ubuntuforums.org/showpost.php?p=6023212&postcount=5")

Thank you so much!


EDIT:

I am getting considerable tearing in ZSNES, with both Compiz and Metacity.  I am running an Nvidia card.  Anyone have any suggestions to eliminate the tearing?

---

### Post by komoras on 2008-11-03
> **dfreer said:**
> Alright, since it's been long since overdue...

Do the following:
```
echo "deb http://rowdy.dfreer.org:8080 hardy main" | sudo tee -a /etc/apt/sources.list 
wget http://rowdy.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
sudo apt-get install zsnes32

zsnes32 -ad oss ## First run ##
zsnes32 ## all subsquent runs, or just launch through the menu ##
```



tnx
works fine

---

### Post by MrDelish on 2008-12-13
I was just about to follow the steps for installing in Hardy but decided to try it in Wine first. The audio takes some tweaking, but it runs perfectly. Now to get fullscreen working...

---

### Post by dfreer on 2008-12-13
> **MrDelish said:**
> I was just about to follow the steps for installing in Hardy but decided to try it in Wine first. The audio takes some tweaking, but it runs perfectly. Now to get fullscreen working...

Fullscreen works just fine in the linux native binary :D

But if you wish to use wine, it should work there too. Have you checked your winecfg? Make sure it's not running in a virtual desktop. Better question is what happens when you try to run it fullscreen?

---

### Post by BryanFRitt on 2009-02-02
I set the sound to **[COLOR="Green"]32000Hz Mono[/COLOR](see update 2)** with **[COLOR="Green"]gaussian sound interpolation[/COLOR]** and **[COLOR="Green"]none for low pass[/COLOR]**, the _**jumpiness in the sound is [U][B]significantly way less**_ than when I tried it at 8-point and Hi Quality 48000Hz stereo, with a lowpass filter(or any other sound setting combination). This setting makes it so you have to listen for the jumpiness, instead of the jumpiness being annoying. Although, having to go **[COLOR="Green"]mono[/COLOR]** sound to reduce jumpiness can be a bummer.

I tried running zsnes in **Wine**, the sound **isn't jumpy**, but the frame rate is **only 12-33fps**(see update 3) on my computer*, even when all the video effects/filters are off and resolution set to 640x480, with sound at default.

*2.2GHz Dual Core II, NVidia NVS 140 (256MiB), 4GiB Ram, Intel High Def Audio, KUbuntu 8.04.1 64bit version...
I'm able to get a constant 60fps in Windows, with all the effects on max, with resolution set to 1920x1200 ... 
and 60fps using the Linux Version with High Quality settings at 1920x1200
hqFilter=1
hqFilterlevel=4
note: Auto Frame was turned on for this which try to make it a constant 60fps(59.94?((/2)?))

(When I had a 2.2GHz P4, ATI 8500DV (64GiB) , 1GiB Ram... I remember getting 59/60 fps in Windows, full effects?, resolution 1280x1024?/1600x1200?... 
and on a k6-300, 32?/64?/128?MiB Ram, Voodoo 16MiB?, or Onboard Video?, in Windows, I think I got around 35fps at 640x480 Full Screen, default settings?, but I could be (way) off)

p.s. ZSNES on Wine is a "SNES Emulator" on a "Windows Compatibility Layer".

---

Update 1: Maybe my brain just figured out how how to ignore the sound error and/or just the section of the game I was playing, instead of it going away or being reduced. Because, I'm hearing it again.
Update 2: Now I realize I was on **'Mono'** not stereo when I started hearing it less, switching to **32000Hz** instead of **48000Hz** also helped. (Tried lower than 32000Hz, but that actually increased the sound stutter).  Switching **gaussian** on had no effect on stutter, on the quick test I gave it.
The **default** **32000Hz stereo** with **gaussian sound interpolation** and **none for low pass**(hadn't tested if the 'stereo' part is default, just assuming)
Update 3:I turned **on** HQ 4x filter in the Windows version and the frame rate went **up** to 35-55fps! (opposite of what I expected), I bet this something to do my monitor being LCD.  Getting closer to the ideal 60fps. Updated update: It later went back down to the same level as before. Then I logged out and restarted X (Left Alt+Control+Backspace), and I don't think that helped, but restarting the computer did.

I like the stereo effect(like hearing when something moves from right to left or vise versa), being able to stay in Linux, as well as a good frame rate, but I don't like the sound messing up.

update 4: I noticed with a lot of games(not just wine ZSNES) the frames rates start high, and then a few minutes later the frame rate slowly goes down and ends up being quite a bit slower.  I also hear the fan blowing a lot loader too.  Is my computer slowing down to protect the laptop from overheating?

---

### Post by BryanFRitt on 2009-02-02
Why does 'Fast Forward' sometimes quit working?  I also noticed when the 'Fast Forward' quits working the game also goes a little bit slower.

---

### Post by dfreer on 2009-02-03
> **BryanFRitt said:**
> Why does 'Fast Forward' sometimes quit working?  I also noticed when the 'Fast Forward' quits working the game also goes a little bit slower.

I honestly can't help you with any of the issues you are experiencing, you will want to try the ZSNES boards and talk to the actual ZSNES developers.

---

### Post by Matoridi on 2009-02-17
Thanks Dfreer,

Your post helped me install this and play my old Nintendo Games!:p

---

### Post by gdbutcher on 2009-03-15
Hi Dfreer, is your ZNES package still available?

when i tried:

```
echo "deb http://rowdy.dfreer.org:8080 hardy main" | sudo tee -a /etc/apt/sources.list 
wget http://rowdy.dfreer.org:8080/7572013D.gpg -O- | sudo apt-key add - 
sudo apt-get update
sudo apt-get install zsnes32

```

I get this:

```
Err http://rowdy.dfreer.org hardy Release.gpg             
  Could not resolve ‘rowdy.dfreer.org’
Err http://rowdy.dfreer.org hardy/main Translation-en_GB
  Could not resolve ‘rowdy.dfreer.org’
Reading package lists... Done       
W: Failed to fetch http://rowdy.dfreer.org:8080/dists/hardy/Release.gpg  Could not resolve ‘rowdy.dfreer.org’

W: Failed to fetch http://rowdy.dfreer.org:8080/dists/hardy/main/i18n/Translation-en_GB.bz2  Could not resolve ‘rowdy.dfreer.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
gareth@gareth-laptop:~$ sudo apt-get install zsnes32
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package zsnes32

```

Have I done something wrong?

---

### Post by dfreer on 2009-03-15
The server is currently down, after yet another hard drive failure. The packages should still be somewhere in this thread in an attachment if you'd like to search for them.

---

### Post by TygerFish on 2009-04-08
> **dfreer said:**
> The server is currently down, after yet another hard drive failure. The packages should still be somewhere in this thread in an attachment if you'd like to search for them.

Oh no!  Condolences... will you let us know when it's back up?  Your repository was, to my mind, at least, one of the highlights of the Ubuntu community.

---

### Post by Tolaris on 2009-04-09
> **dfreer said:**
> The server is currently down, after yet another hard drive failure. The packages should still be somewhere in this thread in an attachment if you'd like to search for them.

Sorry to hear that!  I've uploaded the last zsnes32 for hardy amd64 package to my repository.  See:

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

---

### Post by dfreer on 2009-04-09
> **TygerFish said:**
> Oh no!  Condolences... will you let us know when it's back up?  Your repository was, to my mind, at least, one of the highlights of the Ubuntu community.

I will certainly let people know if it comes back up :D

---

### Post by Matoridi on 2009-05-06
Sorry if this sounds alarmist, but...

Does that mean your repository might not come back?

If so, where can I find Zsnes?  I plan to install Jaunty on my computer,  and Zsnes is not in its repositories.

---

### Post by Tolaris on 2009-05-06
> **Matoridi said:**
> Sorry if this sounds alarmist, but...

Does that mean your repository might not come back?

If so, where can I find Zsnes?  I plan to install Jaunty on my computer,  and Zsnes is not in its repositories.

It's in my repo for hardy.  It should work on Jaunty, just use the hardy repo source line.  Repo instructions:

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

---

### Post by epsilon72 on 2009-05-09
So, I've had absolutely no luck with ZSNES up to this point on Debian amd64 - unfortunately, dfreer's and nach's (an admin at the zsnes forums?) binaries segfault on me, and the execstack program doesn't do anything for me.

Today though I tried my binary built by my amd64 Gentoo setup (all you have to do in gentoo is 'emerge zsnes').  It uses SDL instead of libao.  *This* one works flawlessly with no segfaults and good sound quality (as long as sound output is set to 48000hz.  I do load the snd_pcm_oss and snd_seq modules automatically...i'm not sure if that makes a difference or not).  My debian native libsdl uses alsa, and I also have ia32-libs installed.

I would attach the binary to this post, but it looks like ubuntu forums doesn't want attachments other than specified filetypes.

---

### Post by dfreer on 2009-05-09
> **Matoridi said:**
> Sorry if this sounds alarmist, but...

Does that mean your repository might not come back?

Currently my server has been converted to desktop use; as such, it is unlikely that my repository will come back up (the [Falcon Repository Manager]("http://launchpad.net/falcon") software I used is no longer mantained/working as well). By the time I ever do bring it up it will be highly likely that my repository will be obsolete or forgotten anyways. I'm still amazed at how much traffic I ever got in the first place. 

I still monitor these threads on occasion and still have all my original material available on request. And BTW, compiling ZSNES is relatively simple and a great way to learn how compiling work for people new to linux.

> **epsilon72 said:**
> So, I've had absolutely no luck with ZSNES up to this point on Debian amd64 - unfortunately, dfreer's and nach's (an admin at the zsnes forums?) binaries segfault on me, and the execstack program doesn't do anything for me.

Nach is one of the ZSNES developer's, yes. Not familiar with execstack and after reading it's man page I'm still not entirely clear on why it would help. 

> **epsilon72 said:**
> Today though I tried my binary built by my amd64 Gentoo setup (all you have to do in gentoo is 'emerge zsnes').  It uses SDL instead of libao.

Did you place symbolic links for the 32-bit libao libs? This would explain why our binaries (built using --enable-libao) segfaults on your Debian AMD64. If SDL sounds great to you, however, run with it :D I always preferred using libao myself as I would get "scratches" when using SDL.

> **epsilon72 said:**
> I would attach the binary to this post, but it looks like ubuntu forums doesn't want attachments other than specified filetypes.

tar/zip it up first :D They probably do that to save on bandwidth and security reasons.

---

### Post by epsilon72 on 2009-05-10
Well, what I did is fetch the 32-bit version of libao from packages.debian.org and put the appropriate files and symlinks into /usr/lib32/.  I suppose I could've tried symlinking to the 64 bit version of libao, but I remember it complaining to me when I tried to LD_PRELOAD the library beforehand so I didn't try that.  I'll have to give it a try just to see if it'll work...

Anyways, I'll try and attach my zsnes binary for anyone who wants to use it.  It comes with no warranty, I'm not guaranteeing that it'll work for everyone, yadda yadda blah blah blah, you get the point :)

As I said before, it runs fine for me with squeeze's libSDL, ia32-libs, and with a couple of alsa modules like snd_seq and snd_pcm_oss loaded.
I'm wondering...seeing as how zsnes is so easy to install in Gentoo, why isn't there an amd64 version in debian and jaunty's repositories?  (obviously, I know there's no such thing as a true 64-bit version of zsnes, but that doesn't mean 64-bit machines can't run it..)

---

### Post by dfreer on 2009-05-11
> **epsilon72 said:**
> Well, what I did is fetch the 32-bit version of libao from packages.debian.org and put the appropriate files and symlinks into /usr/lib32/.  I suppose I could've tried symlinking to the 64 bit version of libao, but I remember it complaining to me when I tried to LD_PRELOAD the library beforehand so I didn't try that.  I'll have to give it a try just to see if it'll work...

The idea is:
Install 32-bit libao libs into /usr/lib32/ and /usr/lib32/ao/plugins-2/, sounds like you did this already. But then, you need to symbolically link the libs in /usr/lib32/ao/plugins-2/ to /usr/lib/ao/plugins-2/, renaming them so that they do not conflict with the 64-bit libs already there. Here's an example:
```
sudo ln -s /usr/lib32/ao/plugins-2/liboss.so /usr/lib/ao/plugins-2/lib32oss.so
```

The segfault comes from libao, not zsnes or LD. The main lib libao.so.2, contains hardcoded paths to it's plugin libs (you can run strings on the file to see them). It will only look for the files in /usr/lib/ao/plugins-2/.  

BTW, not sure if you know, in debian /emul/ia32-linux/ is generally used whereas in Ubuntu /usr/lib32/ is used.

If this is what you did and it still segfaults, I would then suspect that the binary has been optimized for features that your processor can't handle.

> **epsilon72 said:**
> I'm wondering...seeing as how zsnes is so easy to install in Gentoo, why isn't there an amd64 version in debian and jaunty's repositories?  (obviously, I know there's no such thing as a true 64-bit version of zsnes, but that doesn't mean 64-bit machines can't run it..)

That is another can of worms, mainly due to debian (and hence ubuntu) is not truly multi-arch ready. Not sure why they suddenly decided to introduce a 64-bit package in the repos (and they just as suddenly decided to pull it), but I suspect it's a policy thing. I can get into a discussion of the current multi-arch problems in debian/ubuntu if you are really interested, but I can get pretty verbose :D

---

### Post by epsilon72 on 2009-05-12
> **dfreer said:**
> [B]The main lib libao.so.2, contains hardcoded paths to it's plugin libs (you can run strings on the file to see them). It will only look for the files in /usr/lib/ao/plugins-2/.  
[/B]
Ooohh okay, that makes sense now.  I didn't know the directory was static like that.
> [BTW, not sure if you know, in debian /emul/ia32-linux/ is generally used whereas in Ubuntu /usr/lib32/ is used.
Yeah I noticed that; I just use /usr/lib32 out of habit (gentoo).  Fortunately there's a symlink already in place to get me to the right place.


> That is another can of worms, mainly due to debian (and hence ubuntu) is not truly multi-arch ready. Not sure why they suddenly decided to introduce a 64-bit package in the repos (and they just as suddenly decided to pull it), but I suspect it's a policy thing. I can get into a discussion of the current multi-arch problems in debian/ubuntu if you are really interested, but I can get pretty verbose :D
Heheh, maybe some other time :D   hopefully amd64 debian gets better multilib support in the future though.

---

### Post by acer8930 on 2009-05-12
Which source would be the best to add for 9.04 Jaunty?

---

### Post by dfreer on 2009-05-12
> **acer8930 said:**
> Which source would be the best to add for 9.04 Jaunty?

? You mean which repository to use? It's probably better to compile it using GCC 4.1 for now, I haven't verified that this will fix the compilation issue in 9.04 (or if it's already been fixed), but that was the issue in 8.10.

---

### Post by malathion on 2009-06-02
> **Tolaris said:**
> Sorry to hear that!  I've uploaded the last zsnes32 for hardy amd64 package to my repository.  See:

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

Added this repo and got zsnes32 working without a hitch! Please add this to the OP!

---

### Post by sherl0k on 2009-06-05
How I got ZSNES working on 64-bit:

downloaded the 32-bit deb from [http://packages.ubuntu.com/jaunty/i386/zsnes/download](http://packages.ubuntu.com/jaunty/i386/zsnes/download)

forced the install by running this in a terminal:
sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu2_i386.deb

and run zsnes using the sdl sound output (which sounds perfect to me):
zsnes -ad sdl

---

### Post by quazi on 2009-06-11
I still get segmentation faults.  Both the 32-bit version with forced architecture and the intrepid version install fine.  However, I get a segmentation fault when trying to run either.

Is there anything here that would indicate its cause?
```
Starting Mouse detection.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 3 mice detected.
Using ManyMouse for:
Mouse 0: PS/2 Generic Mouse
Mouse 1: Logitech USB Receiver
Segmentation fault

```

EDIT: Nevermind, I read the previous post more carefully, and just appended the command -ad sdl to zsnes.

---

### Post by dfreer on 2009-06-11
Did you install the 32-bit libao and set up the symbolic links correctly? That's the most likely reason it doesn't work unless you use SDL.

---

### Post by Inkpot on 2009-06-16
My friends, I have screwed up.

I tried using the method described by the OP (ie, using his repository) and it was unsuccessful. Now I get package manager errors that state "Error: Opening the cache (E: Type 'deb' is not known on line 54 in source list /etc/apt/sources.list, that your installed packages have unmet dependencies"

Could someone please bail me out and show me how to undo what I've done? This is what I get for tinkering with things I don't fully understand... :(



Inkpot

---

### Post by jerome1232 on 2009-06-17
Sounds to me like you just butchered line 54 of your sources.list file, I would pop open a text editor and double check that line, make sure there are no spelling errors and etc...

---

### Post by Inkpot on 2009-06-17
Thanks, I did exactly that and now all is working fine again. Lesson learned. :)


Inkpot

---

### Post by Shinka.S on 2009-07-25
> **malathion said:**
> Added this repo and got zsnes32 working without a hitch! Please add this to the OP!

How ?

I added tolaris but zsnes is still greyed in Add/Remove and sudo apt-get zsnes32 doesn't work. 

I can't believe how complicated it is to install Zsnes on AMD64. It's much easier on Fedora 11 64bits, is it possible to use their package and "translate" it for Ubuntu 9.04 64 bits ?

---

### Post by dfreer on 2009-07-26
> **Shinka.S said:**
> How ?

I added tolaris but zsnes is still greyed in Add/Remove and sudo apt-get zsnes32 doesn't work. 

I can't believe how complicated it is to install Zsnes on AMD64. It's much easier on Fedora 11 64bits, is it possible to use their package and "translate" it for Ubuntu 9.04 64 bits ?

His repository is online for me. Here's a direct link to the deb package:
[http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb](http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb)

You could try [Alien]("http://packages.ubuntu.com/jaunty/alien") for converting RPM's to DEB's, that's not something I personally would do but it's up to you. There's several other methods:

(1). Compile ZSNES yourself. You can't compile it into a 64-bit binary, due to it's 32-bit assembly code, so you will need to either cross-compile it, compile it in a 32-bit chroot, or use another 32-bit machine to compile it for you (make sure to optimize it for the 64-bit machines processor).
(2). Download a 64-bit debian package that contains the 32-bit binary and install that. Make sure you have the much needed 32-bit libraries.
(3). Download a 32-bit debian package of ZSNES from *anywhere*, decompress the archive and grab the pre-compiled binary. You'll be stuck with whatever options it's compiled with (w/o libao support), will have to install all needed 32-bit libraries, and hope it wasn't optimized for another processor OR with Ubuntu's GCC 4.3.2 (which has been known to cause segfaults).
(4). Download a 32-bit debian package and use --force-architecture to install it. Pretty much exactly the same as #3.

---

### Post by daflame on 2009-09-05
Thank you so much for this post.  Currently I have found zsnes the most feature rich and compatible with games and IPS live patching support is a handy feature to retain an original copy while being able to play a patch.  I have an amd64 machine and am running the 64bit kernel/system and could not find a way to run zsnes until now.  Again thank you.

---

### Post by MethosCR on 2009-11-04
Thank you so much for this post. I will try it as soon I get home...

---

### Post by zeifertstc on 2010-05-18
Can anybody verify if this package/repository works on Lucid Lynx x64?

Thanks in advance for your reply.

---

### Post by dfreer on 2010-05-18
> **zeifertstc said:**
> Can anybody verify if this package/repository works on Lucid Lynx x64?

Thanks in advance for your reply.

If you are referring to the repository in the original post than no, the server has been offline for close to a year now. ZSNES should still work, but as always it's hard to tell with Ubuntu changing everything all the time.

BTW if you end up having problems with ZSNES, give bsnes a try instead.

---

### Post by zeifertstc on 2010-05-24
Thank you, I'll have to look into that. For now, I have a temporary solution setup. Who knew that the windows version of zsnes would work in Wine? :popcorn:

bsnes, hmm... *Starts googling*

---

### Post by barx on 2010-07-18
[QUOTE=dfreer;7684276]His repository is online for me. Here's a direct link to the deb package:
[http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb](http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb)


OH I LOVE you!!

---

### Post by Tolaris on 2010-07-19
> **barx said:**
> [QUOTE=dfreer;7684276]His repository is online for me. Here's a direct link to the deb package:
[http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb](http://www.tolaris.com/apt/pool/main/z/zsnes32/zsnes32_1.510b-3.5_amd64.deb)


OH I LOVE you!!

If anyone can confirm that this package works on lucid, please do so. I'll add it to the tolaris.com lucid section.

---

### Post by Danny Dubya on 2010-07-20
> **Tolaris said:**
> 

If anyone can confirm that this package works on lucid, please do so. I'll add it to the tolaris.com lucid section.

Works for me, Mr. Hero sir.

---

### Post by Tolaris on 2010-07-21
> **Danny Dubya said:**
> Works for me, Mr. Hero sir.

Thanks, Danny. I've added it to lucid. If any of you want to install zsnes32 from apt/Synaptic, follow the instructions here:

[http://www.tolaris.com/apt-repository/](http://www.tolaris.com/apt-repository/)

---

### Post by huntzire on 2010-08-08
The Guy in this blog, posts a binary which works fine on ubuntu 10.04 ubuntu.

[http://filthypants.blogspot.com/2008/11/how-to-run-zsnes-super-nintendo.html](http://filthypants.blogspot.com/2008/11/how-to-run-zsnes-super-nintendo.html)

The only thing you must do like most zsnes on 64 bit is make sure it runs under SDL so -ad sdl when you first run it.

---

### Post by epsilon72 on 2010-10-11
All of the old amd64 zsnes builds no longer work in maverick because of the move to libao4!  

How do we build and package zsnes for ubuntu from source?

---

### Post by jerome1232 on 2010-10-11
I remember having to build it in a 32 bit environment, I have no idea on packaging it but that will get you an exectuable binary file.

I pretty sure SOMEWHERE in this thread there were instructions on how to build it. (on a much older version of Ubuntu obviously)

---

### Post by epsilon72 on 2010-10-12
> **jerome1232 said:**
> I remember having to build it in a 32 bit environment, I have no idea on packaging it but that will get you an exectuable binary file.

I pretty sure SOMEWHERE in this thread there were instructions on how to build it. (on a much older version of Ubuntu obviously)

**EDIT: It's not even necessary to build your own zsnes deb package.  You can just use the standard 32-bit one, as I've illustrated 2 posts below this one. **

I was able to figure it out, I think.  The sound is a little scratchy but that might be because Ubuntu is running in a VM.  I'm downloading 32-bit ubuntu as we speak so I can test the "native" zsnes tomorrow.

How I did it:

Install build-essential and ia32-libs.
	```
sudo apt-get install build-essential ia32-libs
```

Install the build dependencies for zsnes
	```
sudo apt-get build-dep zsnes
```

Make a directory for building zsnes.  Call it zsnes_build, cows, whatever you want.
	```
mkdir cows
```

Change to the new directory
	```
cd cows
```

Download the zsnes source with apt-get
	```
apt-get source zsnes
```

Change to the zsnes source directory that was created with the above command
	```
cd zsnes-1.510
```

Build the package
	```
dpkg-buildpackage -us -uc -nc
```

The package will be placed in the parent directory.  Change directory to there
	```
cd ../
```

...and install the package
	```
sudo dpkg -i zsnes_1.510-2.2ubuntu4_amd64.deb
```

Zsnes will probably segfault the first time it is run.  Try running it with SDL as its sound output:
	```
zsnes -ad sdl
```

If sdl is unsatisfactory, oss is another option:
	```
padsp zsnes -ad oss
```

---

### Post by epsilon72 on 2010-10-13
I tried 32-bit Ubuntu in a VM, and zsnes sounded much better :/  I wonder if zsnes compiled in 64-bit Ubuntu would sound just as bad on an actual installation...
Zsnes on 64-bit arch and 64-bit gentoo runs just fine.

EDIT: Running zsnes with the sdl libao plugin was causing the sound problems.

---

### Post by epsilon72 on 2010-10-13
Alright, forget all that junk about building zsnes from source.  It's totally unnecessary!  Getting zsnes on 64-bit ubuntu is much easier than I thought.

I have it working perfectly now, in maverick:

1) Download the i386 maverick version of zsnes [here](http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu4_i386.deb)
2) If they aren't installed already, install ia32-libs
```
sudo apt-get install ia32-libs
```
3) Install the 32-bit zsnes package:
```
sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb
```
4) Make a symbolic link to the 32-bit libao oss plugin so zsnes will run..
```
sudo ln -s /usrlib32/ao/plugins-4/liboss.so /usr/lib/ao/plugins-4/lib32oss.so
```
5) Run zsnes with:
```
padsp zsnes -ad oss
```

...and the sound is perfect! (If it isn't, try different audio sample rates in zsnes) You could also edit the /usr/share/applications/zsnes.desktop file so that it executes 'padsp zsnes' every time (Exec=padsp zsnes)

This is pretty easy to do in 64-bit debian as well, except:
1) You have to manually download the 32-bit version of libao2 (or libao4, for squeeze) and place the files and symlinks in the lib32 directory
2) You will probably want to use the alsa libao plugin, so symbolically link that one (like in step 4 above) instead of the oss plugin.
3) Since there's no pulseaudio installed by default in debian, just run zsnes with 'zsnes -ad alsa' the first time and it will run with alsa thereafter.

I hope all that makes sense....I'm just trying to make things easier for everyone else who is trying to get this to work.

Please note: if you use this method and ever want to uninstall zsnes, you'd have to use dpkg to do it - 'sudo dpkg -r zsnes' or 'sudo dpkg -P zsnes'.

---

### Post by phz_swe on 2010-10-29
> **epsilon72 said:**
> Alright, forget all that junk about building zsnes from source.  It's totally unnecessary!  Getting zsnes on 64-bit ubuntu is much easier than I thought.

I have it working perfectly now, in maverick:

1) Download the i386 maverick version of zsnes [here](http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.2ubuntu4_i386.deb)
2) If they aren't installed already, install ia32-libs
```
sudo apt-get install ia32-libs
```
3) Install the 32-bit zsnes package:
```
sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb
```
4) Make a symbolic link to the 32-bit libao oss plugin so zsnes will run..
```
sudo ln -s /usrlib32/ao/plugins-4/liboss.so /usr/lib/ao/plugins-4/lib32oss.so
```
5) Run zsnes with:
```
padsp zsnes -ad oss
```

Thanks a lot, this worked for me.

I actually don't even have to meddle with point 5, I just run it as [FONT="Courier New"]zsnes[/FONT], without [FONT="Courier New"]padsp[/FONT] or any switches, with sound. I symlinked [FONT="Courier New"]libalsa.so[/FONT] as in step 4 instead of [FONT="Courier New"]liboss.so[/FONT], and everything works for me (maybe I've run it with the switch [FONT="Courier New"]-ao alsa[/FONT] in the past, and this setting is remembered, but I don't think so).

---

### Post by joelstitch on 2010-11-29
I got this error when trying step 3 of epsillon72:

> sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 215796 files and directories currently installed.)
Preparing to replace zsnes 1.510-2.2ubuntu4 (using zsnes_1.510-2.2ubuntu4_i386.deb) ...
Unpacking replacement zsnes ...
dpkg: dependency problems prevent configuration of zsnes:
 zsnes depends on libao4 (>= 1.0.0); however:
  Package libao4 is not installed.
dpkg: error processing zsnes (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for menu ...
Processing triggers for python-support ...
Errors were encountered while processing:
 zsnes


---

### Post by scott.enderle on 2011-01-15
> **joelstitch said:**
> I got this error when trying step 3 of epsillon72:

I got the same error using the package epsillon72 posted, but I'm running intrepid still. I tried installing the ia32 version of zsnes using dpkg -i --force-architecture and it seems to work perfectly using sdl (i.e. "zsnes -ad sdl"). I already had ia32-libs installed. 

If you're running lucid, download the package from one of the mirrors listed here: 

[http://packages.ubuntu.com/lucid/i386/zsnes/download](http://packages.ubuntu.com/lucid/i386/zsnes/download)

I'm baffled as to why this package isn't installable via apt.

---

### Post by bearaids on 2011-02-14
I can't seem to get zsnes working for the life of me.  I am running Ubuntu 10.10 64 and have tried many things mentioned in this forum and others to no avail.  Even when I run:

[PHP]zsnes -ad sdl[/PHP]

I still get:

[PHP]zsnes: error while loading shared libraries: libao.so.2: cannot open shared object file: No such file or directory[/PHP]

Any advise would be appreciated.  I would love to play some of my old games again.

---

### Post by dfreer on 2011-02-15
> **joelstitch said:**
> I got this error when trying step 3 of epsillon72:
zsnes depends on libao4 (>= 1.0.0); however:
Package libao4 is not installed.

> **bearaids said:**
> I can't seem to get zsnes working for the life of me.  I am running Ubuntu 10.10 64 and have tried many things mentioned in this forum and others to no avail.  Even when I run:

[PHP]zsnes -ad sdl[/PHP]

I still get:

[PHP]zsnes: error while loading shared libraries: libao.so.2: cannot open shared object file: No such file or directory[/PHP]

Any advise would be appreciated.  I would love to play some of my old games again.

If you are running 32-bit: Have you installed libao2 or libao4?

If you are running 64-bit: Have you manually installed the 32-bit package of libao2/4 and made sure the libraries are available in /usr/lib/ao/plugins-2/ ?

More info see here: [http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=12339](http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=12339)

---

### Post by chillincool on 2011-05-09
> **epsilon72 said:**
> 
Post #173 worked perfectly for me(except I had to add a -d to the dkpg command) on a semi-fresh install of Ubuntu 11.04 64 bit.

Also runs fine launching with just 'zsnes'.

Thanks

---

### Post by Paradoxfox93 on 2011-07-22
Grr.  This used to work for me back in lucid.  Now it whines about all the lib deps it doesn't have (that are installed and it SHOULD have).  ia32 libs borked or what?

```
:~$ sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu4_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 211256 files and directories currently installed.)
Preparing to replace zsnes:i386 1.510-2.2ubuntu4 (using zsnes_1.510-2.2ubuntu4_i386.deb) ...
Unpacking replacement zsnes:i386 ...
dpkg: dependency problems prevent configuration of zsnes:i386:
 zsnes:i386 depends on libao4 (>= 1.0.0).
 zsnes:i386 depends on libc6 (>= 2.4).
 zsnes:i386 depends on libgcc1 (>= 1:4.1.1).
 zsnes:i386 depends on libpng12-0 (>= 1.2.13-4).
 zsnes:i386 depends on libsdl1.2debian (>= 1.2.10-1).
 zsnes:i386 depends on libstdc++6 (>= 4.1.1).
 zsnes:i386 depends on zlib1g (>= 1:1.2.2.3).
dpkg: error processing zsnes:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
Errors were encountered while processing:
 zsnes:i386

```
:confused:

Also @chillincool dpkg doesn't have a -d option =/ wtf

---

### Post by dfreer on 2011-07-23
Try unpacking the .deb package and running ldd on the binary, to see what dependencies you are actually missing. Then use [http://packages.ubuntu.com/](http://packages.ubuntu.com/) to find the files you need and install them.

EDIT: Also, I myself would use the source/binaries listed here, but that's just me: [http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=11513](http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=11513)

---

### Post by Paradoxfox93 on 2011-07-24
I'm not missing any dependencies.

---

### Post by dfreer on 2011-07-24
That particular error you're getting just states that the libraries you currently have are not the versions specified by the person creating that package. It does cause dpkg to throw an error, but can likely be safely ignored as the package maintainer likely just listed the versions of packages installed on his/her own system.

It does look like the versions are >=, so as long as you have a newer version you should be good. Are you running the latest Ubuntu?

Finally I can see a problem with trying to force install a i386 package. Since those libs are installed using lib32, dpkg may be looking for the standard 32-bit library packages. Come to think of it this is exactly your problem. Solution? Either manually unpack the 32-bit package and run it that way/download a precompiled binary/compile zsnes yourself/or find a 64-bit installer like I used to have in this thread.

---

