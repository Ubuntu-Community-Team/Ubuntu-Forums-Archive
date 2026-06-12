---
title: "non-unix based open-source OSes?"
date: 2007-01-22
forum: Other OS Talk
---

### Post by Mateo on 2007-01-22
Are there any OSes not based on unix that are open-sourced?

---

### Post by riven0 on 2007-01-22
Isn't ReactOS an open-source OS not based on Unix? Not sure, though, got check...


EDIT: Okay, [here is some info from the official site]("http://www.reactos.org/en/about_whatisreactos.html"). It's is open-source, and as far as I can tell, it doesn't seem to be based on Unix... someone correct me if I'm wrong.

---

### Post by Mateo on 2007-01-22
Doesn't ReactOS use wine?  so it must have a unix base, correct?

I found one though: Haiku, based on BeOS.  i guess beos went defunct, does that mean they released their source code?

---

### Post by Dr. C on 2007-01-23
ReactOS is a project to create a free as in speech Windows clone, just as GNU / Linux is a free as in speech Propriety Unix clone.  Sharing code with the WINE project makes sense since they both are designed to support Windows applications, but that does not make ReactOS a Unix based OS. 

Another non Unix free as in speach OS is FreeDOS [http://www.freedos.org]("http://www.freedos.org")

---

### Post by 3rdalbum on 2007-01-23
ReactOS uses DLLS from Wine, but the kernel is completely non-Unix (designed to eventually support Windows drivers).

BeOS was not open-sourced. Haiku is a "start from scratch" project, but apparantly it uses a kernel written by the same guy who wrote the BeOS kernel.

There's also Syllable, which is a GPL'ed, partially-POSIX desktop OS for new users. I follow its development, and there's even a Live CD. Unfortunately, although it's more useful than Haiku and more interesting than ReactOS, it's still buggy and there are very few programs for it yet.

---

### Post by Magnes on 2007-01-23
There is also AROS - [http://aros.sourceforge.net/](http://aros.sourceforge.net/) - Amiga Research Operating System - it's not GPL though but has it's own licence based on MPL. 
Screenshots: [http://aros.sourceforge.net/pictures/screenshots/](http://aros.sourceforge.net/pictures/screenshots/)
It's aim is to make operating system with look and feel of AmigaOS.

---

### Post by mips on 2007-01-23
[AROS]("http://aros.sourceforge.net/")
[Cefarix]("http://sourceforge.net/projects/cefarix")
 [ Chaos]("http://www.chaosdev.org/")
[Cosmoe]("http://www.cosmoe.com/")
[ CP/M]("http://www.seasip.demon.co.uk/Cpm/")
[Darwin]("http://www.publicsource.apple.com/projects/darwin/")
[ DCP]("http://www.kc85.de/")
[ Debian GNU/Hurd]("http://www.debian.org/ports/hurd/")
 [ E.R.I.K.A]("http://erika.sssup.it/")
[ eCos]("http://ecos.sourceware.org/")
[ ELKS]("http://elks.sourceforge.net/")
[E/OS]("http://meos.sourceforge.net/")
[ ERaMS]("http://erams.sourceforge.net/")
[ EROS]("http://www.eros-os.org")
 [ Fiasco]("http://os.inf.tu-dresden.de/fiasco/")
[ Free-VMS]("http://freevms.free.fr/indexGB.html")
[ FreeDOS]("http://www.freedos.org/")
[ Freedows]("http://sourceforge.net/projects/freedows/")
[Haiku]("http://haiku-os.org/")
[JTMOS]("http://www.fortunecity.com/tattooine/obiwan/32/")
[ Menuet]("http://www.menuetos.org/")
[ Minix]("http://www.minix3.org/")
[ MorphOS]("http://www.morphos.de")
[ Oberon]("http://www.oberon.ethz.ch/native/")
[ OpenBEOS]("http://www.beosmax.org/")
 [ Plan 9]("http://plan9.bell-labs.com/plan9dist/")
 [ PowerOS]("http://www.poweros.de")
[QNX]("http://www.qnx.com/")
 [ ReactOS]("http://www.reactos.com")
[ RTEMS]("http://www.rtems.com/RTEMS/rtems.html")
[ S.Ha.R.K]("http://shark.sssup.it")
 [ SkyOS]("http://www.skyos.org/")
[Solaris]("http://www.sun.com/software/solaris/index.jsp")
[Syllable]("http://www.syllable.org/")
[TriangleOS]("http://www.wcools.nl/")
 [ Unununium]("http://sourceforge.net/projects/uuu")
[ V2_OS]("http://www.v2os.cx/")
[ VSTa]("http://www.vsta.org:8080/")
[ Winmac]("http://sourceforge.net/projects/winmac")
[ xMach]("http://sourceforge.net/projects/xmach/")
 [ Yamit]("http://yamit.sourceforge.net/")
[ ZotOS]("http://www.zotos.tk/")

A few of the above are unix-like and also the license might have changed.

[http://en.wikipedia.org/wiki/List_of_operating_systems#Nonproprietary_non-Unix-like](http://en.wikipedia.org/wiki/List_of_operating_systems#Nonproprietary_non-Unix-like)
[http://en.wikipedia.org/wiki/Category:Operating_systems](http://en.wikipedia.org/wiki/Category:Operating_systems)

Wonder what RAV TUX is gonna do with this list...

---

### Post by RAV TUX on 2007-01-23
> **Mateo said:**
> Are there any OSes not based on unix that are open-sourced?

As Mips has listed in his very long list....I would recommend [Haiku.]("http://haiku-os.org/")


Unfortunately YellowTab has halted development of Zeta:
> 
	On the 24th of November 2006 the public content of yellowTAB.com got closed on the server. 
             
      In fact the data is still available internally on this server, but this is for internal use only from now on.
     
      
       yellowTAB is not developing ZETA anymore due to the insolvence procedures, which started 8 months ago. 
       If you have any further questions, please head over to [www.zeta-os.com]("http://www.zeta-os.com/"), the successor to yellowTAB ZETA.
      
      
       The yellowTAB ZETA team wish to thank you all for staying by our side all these years. 
       
     
      
       Bernd-T. Korz

This means that [Haiku]("http://haiku-os.org/")
 is the only chance for an Open-Source BeOS based OS.

---

### Post by Mateo on 2007-01-23
why not the ZetaOS?  They have a livecd, I might try it out.

---

### Post by RAV TUX on 2007-01-23
> **Mateo said:**
> why not the ZetaOS?  They have a livecd, I might try it out.give it a try...;)

I may have mis-understood...since I didn't translate the German web page...I thought development had ended all together,....I f they are still active...then this is great news!

---

### Post by Mateo on 2007-01-23
Wikipedia page sheds some light:

[http://en.wikipedia.org/wiki/Zetaos](http://en.wikipedia.org/wiki/Zetaos)

Sounds like another company took over.  Either way, it's closed source, so it doesn't fit with this thread ;)

---

### Post by 3rdalbum on 2007-01-24
SkyOS, which was in the list, is also not open-source. The betas are available for download only as long as you agree to an NDA.

---

### Post by mips on 2007-01-24
> **RAV TUX said:**
> give it a try...;)

I may have mis-understood...since I didn't translate the German web page...I thought development had ended all together,....I f they are still active...then this is great news!

It's not dead from what I recall. Merely taken over by another company.

EDIT:

Look on the left of the page for **Language / Sprache**, click on the dropdown & select **English**.

---

### Post by RAV TUX on 2007-01-24
> **mips said:**
> It's not dead from what I recall. Merely taken over by another company.

EDIT:

Look on the left of the page for **Language / Sprache**, click on the dropdown & select **English**.MIPS I know how to translate the page....I just didn't have time to review the translated version....still don't so I will rely on your input:D

---

### Post by Mateo on 2007-01-24
anyways, it's not open source.  Only Haiku is.

---

### Post by RAV TUX on 2007-01-26
> **Mateo said:**
> anyways, it's not open source.  Only Haiku is.this is what I thought.

---

### Post by RCC2k7 on 2007-02-16
In times like these I miss OS/2. I wish IBM had turned OS/2 into open source, especially since they discontinued development more than a year ago. I took a look at osFree (an OS/2 clone) but it's too raw to be usable. :(

---

### Post by 3rdalbum on 2007-02-17
Look on Wikipedia's page for OS/2 - it links to the petition to make OS/2 open-source.

---

