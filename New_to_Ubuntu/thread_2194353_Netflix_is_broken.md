---
title: "Netflix is broken"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by sbcwinn on 2013-12-18
I m using a small netbook as a video server. The main reason that I have it, is to play Netflix. I am a Linux geek in training (I.E. - A Newbe!!)

At first I installed Ubuntu 13.10. I installed the Netflix application from the command line and it worked well for me, but on the whole the netbook was slow (faster than Windows 7, but slow none the less....)

I then tried an experiment and downloaded the Xubuntu desktop. Wow, what a difference! I love the distro. Its fast and easy and is convincing me to move many of my office PC's and servers to Linux. I own a software company and am a Microsoft Gold partner (Shhhhh, let's not tell them about the switch to LINUX but I am hooked!)

After switching from Ubuntu 13.10 to Xubuntu 13.10 my Netflix application has stopped running. I can browse the sight but when I go to play a movie there is a black box stating that Silverlight has crashed. I have concluded that I have to download an upgrade to the Mono libraries in Wine.

Does that make any sense? Where can I find the required upgrade?

Thanks in advance for you reply. If you have any other ideas of what could be wrong, please let me know.

---

### Post by sammiev on 2013-12-18
I just checked netflix here and it's working. I'm not really sure what your problem is but likely can be fixed. How did you install netflix? Would like to see the How To you used.

---

### Post by monkeybrain20122 on 2013-12-18
pipelight may work better (I think by the same developers)[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by sbcwinn on 2013-12-18
I tried the instructions and followed them, Pipeline is installed. I downloaded the Firefox add on to mqake the browser identify itself in a manner as directed, I still cannot play movies. Got any further suggestions? Thanks.

---

### Post by sammiev on 2013-12-18
> **sbcwinn said:**
> I tried the instructions and followed them, Pipeline is installed. I downloaded the Firefox add on to mqake the browser identify itself in a manner as directed, I still cannot play movies. Got any further suggestions? Thanks.

Have you closed FF and tried it after you opened again?

---

### Post by sbcwinn on 2013-12-18
Yes,

Then I installed Chromium. I installed the UA switcher, followed the instructions, was asked if I gave the sight permission to run Silverlight, whichb I did. I then got pages of errors after r with the application and has to be shut down.
eceivingf a general one that said Wine has encountered a serious problem

---

### Post by sbcwinn on 2013-12-18
Yes,

Then I installed Chromium. I installed the UA Spoofer, followed the instructions, was asked if I gave the sight permission to run Silverlight, which I did. I then got pages of errors after with the application had to be shut down.

---

### Post by monkeybrain20122 on 2013-12-18
I don't know why. It works well in Ubuntu 13.10 and 13.04 (I don't watch Netflix, just installed it out of curiosity,  it works seamlessly on demo pages) Maybe you should ask the developer. [https://launchpad.net/pipelight](https://launchpad.net/pipelight) 
He is very quick in answering questions.

---

### Post by sammiev on 2013-12-18
I used the same setup that monkeybrain20122 posted above on 4 or 5 systems now and they all work. Not much I can add than to post a few pics of your agent override so we could see if it's active.

---

### Post by monkeybrain20122 on 2013-12-19
Does it work on [http://www.iis.net/media/experiencesmoothstreaming1080p](http://www.iis.net/media/experiencesmoothstreaming1080p) ?
Change the user agent to Firefox24/ Windows

---

### Post by sbcwinn on 2013-12-19
I did. The instructions are clear enough but no joy. I am new to Linux, but not to following instructions. How do I delete everything and start again??

---

### Post by sbcwinn on 2013-12-19
BTW - I have Xubuntu on another PC (...its contagious .....) and I installed the Netflix player. It works just fine.....
I did install that player on this netbook. Perhaps it needalled  be uninstalled???

---

### Post by sbcwinn on 2013-12-27
I installed Lubuntu from scratch, and tested it satisfactorally as per the instructions. I installed User Agent Overrider but the vrowser identities did not match those of the article, so I tried Firefox 24 Windows. When I try to play a video I get a Wine error saying that the plugin to the browser isn't functioning. Here is the error..... got any ideas? Much appreciated if you do.

```
Unhandled exception: page fault on write access to 0x002e006c in 32-bit code (0x7d847506).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7d847506 ESP:0066efa0 EBP:0066efd8 EFLAGS:00210206(  R- --  I   - -P- )
 EAX:002e006c EBX:7d8a8000 ECX:0066eff0 EDX:ffffffff
 ESI:002e006c EDI:00000000
Stack dump:
0x0066efa0:  00f9f954 00fa16b8 0066f038 7da0e515
0x0066efb0:  00000002 00000010 7da0be35 7da0e515
0x0066efc0:  00fa9ce0 0066eff8 0066eff0 7d8a8000
0x0066efd0:  001100d8 00000000 0066f028 7d8339a7
0x0066efe0:  00000400 00000258 01026d48 7d8339a7
0x0066eff0:  002e006c 00110000 00000003 00000073
Backtrace:
=>0 0x7d847506 (0x0066efd8)
  1 0x7d8339a7 (0x0066f028)
  2 0x7d8437fd (0x0066f108)
  3 0x7da1d2c0 (0x0066f158)
  4 0x7da0e38a (0x0066f1a8)
  5 0x7d7c1dfc (0x0066f268)
  6 0x7da17966 (0x0066f448)
  7 0x7da18029 (0x0066f4b8)
  8 0x0027645a in npctrl (+0x26459) (0x0066f4f0)
  9 0x00276545 in npctrl (+0x26544) (0x0066f508)
  10 0x002765c8 in npctrl (+0x265c7) (0x0066f56c)
  11 0x002762df in npctrl (+0x262de) (0x0066f598)
  12 0x00268293 in npctrl (+0x18292) (0x0066f5ac)
  13 0x002754a7 in npctrl (+0x254a6) (0x0066f5f0)
  14 0x002755b5 in npctrl (+0x255b4) (0x0066f61c)
  15 0x007812be in agcore (+0x1112bd) (0x0066f648)
  16 0x007813e1 in agcore (+0x1113e0) (0x0066f660)
  17 0x0078143d in agcore (+0x11143c) (0x0066f670)
  18 0x0078147f in agcore (+0x11147e) (0x0066f69c)
  19 0x0027df8e in npctrl (+0x2df8d) (0x0066f6c0)
  20 0x0027db75 in npctrl (+0x2db74) (0x0066f6dc)
  21 0x0027dbc8 in npctrl (+0x2dbc7) (0x0066f6fc)
  22 0x0027de90 in npctrl (+0x2de8f) (0x0066f714)
  23 0x0027dec0 in npctrl (+0x2debf) (0x0066f724)
  24 0x00279abd in npctrl (+0x29abc) (0x0066f748)
  25 0x002f0fab in npctrl (+0xa0faa) (0x0066f78c)
  26 0x002f0e8e in npctrl (+0xa0e8d) (0x0066f7a4)
  27 0x002e9cbb in npctrl (+0x99cba) (0x0066f7d0)
  28 0x002e8a2d in npctrl (+0x98a2c) (0x0066f808)
  29 0x0040c333 in pluginloader (+0xc332) (0x0066fb98)
  30 0x00402147 in pluginloader (+0x2146) (0x0066fbf8)
  31 0x0040a955 in pluginloader (+0xa954) (0x0066fd88)
  32 0x004013da __tmainCRTStartup+0x259() [/build/buildd/mingw-w64-3.0~svn5915/build/i686-w64-mingw32-i686-w64-mingw32-crt/../../mingw-w64-crt/crt/crtexe.c:332] in pluginloader (0x0066fe60)
  33 0x7b85ecfc in kernel32 (+0x4ecfb) (0x0066fe78)
  34 0x7b85fd83 in kernel32 (+0x4fd82) (0x0066feb8)
  35 0x7bc7d940 (0x0066fed8)
  36 0x7bc808cd (0x0066ffa8)
  37 0x7bc7d91e (0x0066ffc8)
  38 0x7bc5246e (0x0066ffe8)
0x7d847506: lock xaddl    %edx,0x0(%esi)
Modules:
Module    Address            Debug info    Name (32 modules)
PE      250000-  381000    Export          npctrl
PE      400000-  462000    Dwarf           pluginloader
PE      670000-  d56000    Export          agcore
PE    63000000-63072000    Deferred        wininet
PE    7b810000-7b9ad000    Export          kernel32
PE    7bc10000-7bc14000    Deferred        ntdll
PE    7d680000-7d684000    Deferred        opengl32
PE    7d780000-7d784000    Deferred        wined3d
PE    7da00000-7da04000    Deferred        d3d9
PE    7da40000-7da44000    Deferred        uxtheme
PE    7da70000-7da74000    Deferred        iphlpapi
PE    7daa0000-7daa3000    Deferred        netapi32
PE    7dad0000-7db10000    Deferred        crypt32
PE    7dba0000-7dbb1000    Deferred        urlmon
PE    7dc40000-7dcb6000    Deferred        winmm
PE    7dd60000-7dd64000    Deferred        ws2_32
PE    7dd90000-7dd94000    Deferred        psapi
PE    7ddb0000-7ddb9000    Deferred        msacm32
PE    7dde0000-7dde8000    Deferred        oleaut32
PE    7df10000-7df3f000    Deferred        comctl32
PE    7e010000-7e018000    Deferred        shlwapi
PE    7e090000-7e1ee000    Deferred        shell32
PE    7e2c0000-7e2c4000    Deferred        imm32
PE    7e4e0000-7e4e3000    Deferred        msimg32
PE    7e500000-7e504000    Deferred        winex11
PE    7e6f0000-7e6f4000    Deferred        rpcrt4
PE    7e770000-7e774000    Deferred        version
PE    7e790000-7e797000    Deferred        gdi32
PE    7e8b0000-7e8eb000    Deferred        user32
PE    7ea10000-7ea18000    Deferred        ole32
PE    7eb50000-7eb54000    Deferred        msvcrt
PE    7ebf0000-7ebf4000    Deferred        advapi32
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000017    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    00000020    0
    0000001c    0
0000002c explorer.exe
    0000002d    0
0000003f (D) Z:\usr\share\pipelight\pluginloader.exe
    00000041    0
    00000040    0 <==
System information:
    Wine build: wine-1.7.8
    Platform: i386
    Host system: Linux
    Host version: 3.11.0-14-generic
```

---

### Post by cybergalvez on 2013-12-27
Have you tried the instructions from Webup8?
[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by sbcwinn on 2014-01-03
These were the EXACT instructions followed. I must admit I am a bit down about not being able to make this work. It seems simple enough.

---

### Post by cybergalvez on 2014-01-03
I just checked and its working for me with firefox. Have you sent email to the pipelight folkes?

---

