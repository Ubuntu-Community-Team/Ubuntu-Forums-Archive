---
title: "[SOLVED] Wine not working on  Ubuntu 8.4"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jonatan5 on 2008-04-30
I installed Wine. If I click on wine, wine config or exe files there is no reaction. Screen just a bit flashes, but then nothing.

---

### Post by rokumanxes on 2008-04-30
I don't know.
I'm still really new to ubuntu.

Umm...  From what I've read, WINE appears to be
some sort of...  windows... exe loader, thingie,
or somethin'...  Is that right?

---

### Post by mikeyphi on 2008-04-30
> **jonatan5 said:**
> I installed Wine. If I click on wine, wine config or exe files there is no reaction. Screen just a bit flashes, but then nothing.

How and from where did you install Wine?

---

### Post by Adribhel on 2008-04-30
I also have problems using Wine. Windows programs just crash shortly after they start.

(I used system-->Administration-->Synaptic Program... and searched for Wine, and had it installed automatically)

---

### Post by mikeyphi on 2008-04-30
> **Adribhel said:**
> I also have problems using Wine. Windows programs just crash shortly after they start.

(I used system-->Administration-->Synaptic Program... and searched for Wine, and had it installed automatically)

Not all programs will work under wine but there are a couple of things to do:
Open Applications/wine/configure wine
and under the Applications tab select 'Add application' - find the *.exe of your program and add, then select the windows version (you can try several in turn to find the best option) then 'Apply'

To see error messages - run the program from a Terminal (wine progname.exe)

---

### Post by daschl on 2008-04-30
you can also run the wine configuration tool on the console.. i dont have a shell near me right now, but i suppose it is "winecfg" ...

---

### Post by dokdoom on 2008-04-30
You are correct, before you do anything with wine you have to run winecfg. This will create a directory in your /home/usr/ dir. The whole path is going to be ~/.wine

If you did all of this already, then you are experiencing a different issue.

---

### Post by Adribhel on 2008-04-30
Running winecfg left me with this error message:

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report


And by some reason, when I try to add programs to the Wine config list, I don't find most of the Windows folders I usealy find.

---

### Post by SpongeBob SquarePants on 2008-04-30
What version of WINE are you running? There was an issue with this error message in an older version of WINE, which seemed to be fixed by either downgrading, or upgrading. I'd suggest you try either an older or newer version of WINE. Make sure you remove your .wine folder after uninstalling (invisible folder found in home folder). I believe the bug was fixed in version 0.9.56......but may have reoccurred again later. Anyway, see below (marked in red)

wine (0.9.56-0ubuntu1) hardy; urgency=low

  * New upstream release (LP: #197588)
    - Proper handling of OpenGL/Direct3D windows with menu bars.
    - Stubs for all the d3dx9_xx dlls.
    - Several graphics optimizations.
    - Many installer fixes.
    - Improved MIME message support.
    - Lots of bug fixes.
  * debian/rules:
    - reset LDFLAGS to let wine not crash anymore, (LP: #191575)
      thx to Albert Damen <email address hidden> who came up with this solution.
      ([http://www.winehq.org/pipermail/wine-bugs/2007-July/062505.html](http://www.winehq.org/pipermail/wine-bugs/2007-July/062505.html))
    - adjust dh_strip call (LP: #185513)
  * debian/control:
    - remove gcc-3.4 build-dep
    - get rid of quilt
  * cleaned debian/patches
  * Add finnish translation to desktop files (LP: #196916)
  * dlls/winealsa.drv/waveinit.c: (LP: #195507)
    - let wine use the default alsa device
      ([http://bugs.winehq.org/show_bug.cgi?id=10942](http://bugs.winehq.org/show_bug.cgi?id=10942))
  [COLOR="Red"]* Preloader warning (preloader: Warning: failed to reserve range
    00000000-60000000) does not occure anymore (LP: #114025)[/COLOR]

---

### Post by clairegrrl on 2008-04-30
I think it depends what progy youre running with wine.  Ive loaded it and need to add cabextract to run the win program I wanted.  I was able to get everything working, and Im so new at this.  I would just re-read the docs on your program and make sure you have everything you need.

---

### Post by jonatan5 on 2008-05-01
> **mikeyphi said:**
> 
Open Applications/wine/configure wine


I just said   If i click Config nothing happens. No windows showing up nothing.

I installed wine from Add/Remove programs.

Running command winecfg resulted in
jon@jon-desktop:~$ winecfg
preloader: Warning: failed to reserve range 00000000-60000000
wine: creating configuration directory '/home/jon/.wine'...
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Could not load Mozilla. HTML rendering will be disabled.
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:seh:setup_exception_record stack overflow 840 bytes in thread 0009 eip 7bc65706 esp 7f120fe8 stack 0x7f120000-0x7f121000-0x7f220000
wine: wineprefixcreate failed while creating '/home/jon/.wine'.
jon@jon-desktop:~$ wineserver: could not save registry branch to /home/jon/.wine-LFig7j/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jon/.wine-LFig7j/userdef.reg : No such file or directory
wineserver: could not save registry branch to /home/jon/.wine-LFig7j/user.reg : No such file or directory

---

### Post by mikeyphi on 2008-05-01
Obviously a problem seen in your last post.
Try to reinstall wine

---

### Post by SunnyRabbiera on 2008-05-01
The wine in the repos might not be the best solution as sometimes its not as good as the main version of wine, check this page out for wine in ubuntu hardy:
[here]("http://www.winehq.org/site/download-deb")
just make sure to uninstall the wine you got in the repos and wipe out the the hidden wine folder in your home folder.

---

### Post by jonatan5 on 2008-05-05
I just got an upgrade. Now it works fine.  Problem solved!
 Thanks for all replays!

---

