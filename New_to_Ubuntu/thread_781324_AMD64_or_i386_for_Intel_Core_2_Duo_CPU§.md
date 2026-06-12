---
title: "AMD64 or i386 for Intel Core 2 Duo CPU§"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-04
So am wondering whether I need to download the AMD64 or i386 Live CD version to make the full use of my C2D?

---

### Post by cwgatling on 2008-05-04
It would be the i386 for an Intel processor as far as I know.

---

### Post by liquidfunk on 2008-05-04
I'm running AMD64 on my Core2Duo 2.2Ghz, it runs faster than the i386 32bit version.

 Use 64bit ^^

---

### Post by roaldz on 2008-05-04
No, C2D´s support 64-bit instructions. You can download the AMD64 (it´s just a name, you don´t need the AMD..) iso and run it. I did too, and it works like a charm for a year now.
Good luck!

Roald

---

### Post by Joeb454 on 2008-05-04
> **cwgatling said:**
> It would be the i386 for an Intel processor as far as I know.

Not quite :) I run the 64 bit (AMD64) version of Ubuntu on my C2D, works great, even flash works for me with 8.04 :)

---

### Post by PmDematagoda on 2008-05-04
> **roaldz said:**
> No, C2D´s support 64-bit instructions. You can download the AMD64 (it´s just a name, you don´t need the AMD..) iso and run it. I did too, and it works like a charm for a year now.
Good luck!

Roald

But that does not necessarily mean that you can't run i386 on it either, which might be useful in the cases where certain hardware drivers may not have a proper/existing 64-bit version.

---

### Post by cwgatling on 2008-05-04
Cool, I didn't know that the Core 2 Duo was 64-bit :)

---

### Post by Joeb454 on 2008-05-04
Well now you do :D I didn't know for a while either

---

### Post by iSplicer on 2008-05-04
If you are new to Ubuntu, please use the i386. It is easier to set up and troubleshoot if you run into any problemos

---

### Post by cwgatling on 2008-05-04
@joeb
Indeed I do. That's why I like this forum 8)

---

### Post by Canis familiaris on 2008-05-04
Well Core 2 Duos and their lower end counterparts Pentium Dual Core have always been 64-bit. Even their predecessors like the Pentium D and newer Pentium 4 (Prescott based) were also 64-bit.
Intel copied exactly the specifications of AMD64 instruction set and earlier called it EM64T and now calls it Intel 64. Both Intel 64 and AMD64 are almost identical except very minor cases but it doesn't matter to most at least not to Ubuntu 64-bit version.
But however Ubuntu 64bit edition is not compatible with IA-64 instruction set which must not be confused with the AMD64 or Intel 64 (both are in general collectively referred to as AMD64 or x86-64 or x64) and thus Ubuntu 64bit is incompatible with the Intel Itanium Processors. I doubt whether any of you are using an Itanium though.

---

### Post by Paqman on 2008-05-04
> **iSplicer said:**
> If you are new to Ubuntu, please use the i386. It is easier to set up and troubleshoot if you run into any problemos

I disagree. The user experience is identical for both. What are you thinking of that might be more difficult to troubleshoot?

---

### Post by Vicfred on 2008-05-04
> **Paqman said:**
> I disagree. The user experience is identical for both. What are you thinking of that might be more difficult to troubleshoot?

the 64 bit version is less compatible afaik

---

### Post by Canis familiaris on 2008-05-04
I suppose he may be thinking of Flash, Java, and WINE but I think they run all right in Ubuntu 64bit, don't they?

---

### Post by Canis familiaris on 2008-05-04
> **Vicfred said:**
> the 64 bit version is less compatible afaik

What is it less compatible with?

---

### Post by Vicfred on 2008-05-04
> **Anurag_panda said:**
> What is it less compatible with?

the applications, there are more 32 bit supported aplications (i couldn't use cedega and some more when i was using the amd64 6.10 version)

---

### Post by HunterThomson on 2008-05-04
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

I had a long and unnecessary discussion about this before. Just to make sure there is no misunderstanding all Core 2 Duo processors are full on 64bit processors.... 

Ya, I agree use the 64bit version of Ubuntu. It is faster and uses the full potential of your processor. But, as you can read you 64bit processor also support the full x86 instruction set, so you can go that route if you want. However, I think it is unfounded. Even if you want to use one of the rare programs that doesn't have a 64bit package like skype you can still install and run the i386 (x86) program just as well as if you were running the 32bit OS.

---

### Post by Vicfred on 2008-05-04
> **HunterThomson said:**
> [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

I had a long and unnecessary discussion about this before. Just to make sure there is no misunderstanding all Core 2 Duo processors are full on 64bit processors.... 

Ya, I agree use the 64bit version of Ubuntu. It is faster and uses the full potential of your processor. But, as you can read you 64bit processor also support the full x86 instruction set, so you can go that route if you want. However, I think it is unfounded. Even if you want to use one of the rare programs that doesn't have a 64bit package like skype you can still install and run the i386 (x86) program just as well as if you were running the 32bit OS.

No, you can't run 32 bit applications if you are running the 64 bit version of the os afaik

edit
sorry i meant 64 bit OSes

---

### Post by PmDematagoda on 2008-05-04
> **Vicfred said:**
> No, you can't run 32 bit applications if you are running the 32 bit version of the os afaik

Don't you mean that 32-bit applications won't run on 64-bit OSes? If 32-bit applications don't work on a 32-bit version OS then how do you think millions of people run their 32-bit applications on their 32-bit OSes?;)

---

### Post by Vicfred on 2008-05-04
oops i meant 64 bits OSes i already edited the post epic fail lol

---

### Post by HunterThomson on 2008-05-04
> **Vicfred said:**
> No, you can't run 32 bit applications if you are running the 32 bit version of the os afaik

Yes you can... I do.... But you do have to install the 32bit libs.

i.e. for Skype

Hardy
 sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb;



Gusty
sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype

---

### Post by Joeb454 on 2008-05-04
:lolflag:

You can run 32 bit app's on a 64 bit OS, not sure about Windows, but I know you can on Ubuntu, I used to run 32 bit Firefox back when flash was a problem. Like I said earlier, Flash or Java aren't issues anymore :)

---

### Post by SuperAndy on 2008-05-04
i am running 64 bit hardy on a core2quad, and its fantastic. I dont have any issues with incompatibility, since 64 bit has matured now, and lots of people dont think twice about releasing 64 bit version of programs. about the name AMD64, its because AMD were the first to use that type of instruction set in a processor. but intel quickly copied them, but sadly the name has stuck. some people like to call it x64 or x86-64 to kind of negate the AMD input.

I still think the only real reason to use a 64 bit OS is for the purposes of memory. If you have more than 4 Gb of total system memory, including RAM, graphics memory, caches and stuff, then a 32 bit OS can never address the full amount, and depending on how your motherboard and BIOS is configured, it could end up addressing quite a bit less than that (at one point 32 bit ubuntu could only see 2gb of my 4gb of RAM).

Saying that, ubuntu only needs 2 gb to run well. So unless you are really after all the RAM you can muster, and willing to spend money for it, 32 bit ubuntu is absolutely fine.

/essay

---

### Post by Joeb454 on 2008-05-04
> **SuperAndy said:**
> 
I still think the only real reason to use a 64 bit OS is for the purposes of memory. If you have more than 4 Gb of total system memory, including RAM, graphics memory, caches and stuff, then a 32 bit OS can never address the full amount

Not true, you can recompile the kernel if you wanted, I know for a fact that some 32 bit systems (usually servers) can actually address 64GB RAM.

> **SuperAndy said:**
> 
Saying that, ubuntu only needs 2 gb to run well.

I run Ubuntu perfectly fine on 1GB RAM, In fact my RAM usage never goes above 512MB :) I can't say the same for Vista...

---

### Post by HunterThomson on 2008-05-04
If you are ripping DVD's and stuff that uses a lot of CPU time 64Bit is quite a bit faster.

No pun intended....

---

### Post by Canis familiaris on 2008-05-04
> **Vicfred said:**
> No, you can't run 32 bit applications if you are running the 64 bit version of the os afaik

edit
sorry i meant 64 bit OSes

NO! You could create a 32 bit chmod environment and you'll be able to run any 32bit application in Ubuntu 64bit. AFAIK it is two installations of 32 and 64 bit versions of Ubuntu rolled into one.

---

### Post by Canis familiaris on 2008-05-04
> **Joeb454 said:**
> Not true, you can recompile the kernel if you wanted, I know for a fact that some 32 bit systems (usually servers) can actually address 64GB RAM.

I did not know that! Interesting!

---

### Post by madsmeg on 2008-05-04
I dont know where all this rubbish of 64 bit not being as compatible comes from... maybe a couple of years ago, but not now, even a few games have a 64 bit native installer (Linux only i might add)

Go with the 64 Bit, i have NEVER had trouble and there is plenty of support for 64 bit users.

---

### Post by mivo on 2008-05-04
> **Paqman said:**
> I disagree. The user experience is identical for both. What are you thinking of that might be more difficult to troubleshoot?

There are no 64-bit versions of Java Webstart (javaws) and Sun's Java browser plugin. You can work around this by using a 32-bit browser, which worked for me in 64-bit Feisty and Gutsy, but not in Hardy (works for some others, though). Since I need javaws and the original plug-in, I fell back on the 32-bit Ubuntu. I actually notice no speed differences, so for this release it's the more convenient solution for me.

---

### Post by ugm6hr on 2008-05-04
@OP:  The answer is either will work.  Your choice.

As for the debate re: which is better, I don't know.

I have always recommended i386 before now, since the driver and software support for 32-bit *was* better.

Yesterday, I installed Hardy and went with AMD64.  It is definitely faster at bootup, although I'm not sure if that is the Hardy vs Gutsy difference or i386 vs AMD64.

I think the Stickies are worth reading here: [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

I also found it easy to install 32-bit browser with full Java / Flash here: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537) - this is not strictly necessary, but I needed FF2, so chose a 32-bit version, while leaving FF3 installed.

The AMD64 repos seem as well populated as i386 to me.  If not, the 32-bit versions can be installed with a bit of meddling (see here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790))

Hope that helps people.

---

### Post by mivo on 2008-05-04
> **ugm6hr said:**
> It is definitely faster at bootup, although I'm not sure if that is the Hardy vs Gutsy difference or i386 vs AMD64.

It is the Hardy vs Gutsy difference. I had gone from 64-bit Gutsy to 64-bit Hardy, and noticed the faster boot up, too. Then I dropped to 32-bit because of my above mentioned Java issues, and the boot up was still as fast. If I didn't know, I couldn't tell which version I'm using. I think it's pretty much software-dependent. If I didn't need javaws and Sun's native plugin, either version would work for me. If I compiled a lot of code, edited videos or audio, then the 64-bit version would be better. The differences are really small, so for most users it probably doesn't matter either way. (64-bit tends to use 10-15% more RAM, but that is also rather insignificant with the amounts of memory most machines have today.)

---

### Post by T-Virus on 2008-05-04
> **HunterThomson said:**
> Yes you can... I do.... But you do have to install the 32bit libs.

i.e. for Skype

Hardy
 sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb;



Gusty
sudo apt-get install ia32-libs lib32asound2; wget -N boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i getlibs-all.deb; sudo dpkg -i --force-all skype-install.deb; sudo getlibs /usr/bin/skype

Funny thing, I don't remember installing 32bit libs for Skype. :) I must agree that 64bit version runs tat faster on my Intel Core DUO.

---

### Post by Sef on 2008-05-04
I've just installed 64-bit Ubuntu and installing went easy. For Java, I used OpenJDK, which reads as Sun Java 1.6.0. The only problem I have encountered is that some sites require the latest Sun Java 1.6.5.  I wrote a [sticky]("http://ubuntuforums.org/showthread.php?t=774956") about Java on 64-bit systems.

---

### Post by mivo on 2008-05-04
> **Sef said:**
> I've just installed 64-bit Ubuntu and installing went easy. For Java, I used OpenJDK, which reads as Sun Java 1.6.0.

Tried it, didn't work with the two Java applets I need/want to use. I believe it is because they use audio or are otherwise tightly dependent on Sun's Java plugin. (But even if it worked, I'd still have the javaws issue.) I'm counting on Java 7 or 8.

---

### Post by liquidfunk on 2008-05-04
Whilst we are on the topic of whether things work on 64bit or not, is there a way of using the 32bit version of NDISwrapper with 32bit drivers, on the 64bit OS to make my card work?

---

### Post by Joeb454 on 2008-05-04
I think you can just install NDISWrapper from the repositories and it should work :)

---

