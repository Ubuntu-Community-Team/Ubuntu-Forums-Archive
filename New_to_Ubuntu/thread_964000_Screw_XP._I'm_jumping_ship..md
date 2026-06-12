---
title: "Screw XP. I'm jumping ship."
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Obero on 2008-10-30
I&#8217;m going to be completely honest with you&#8212;I&#8217;ve tried Ubuntu before. Then went back to XP, then ran away and hid behind Ubuntu and then crawled back to XP again. Both of them ain&#8217;t perfect operating systems, but I&#8217;m kind of more tired of XP than I am of Ubuntu. The problem I have with Ubuntu is all the systematic coding and programming you have to do, but here&#8217;s a few questions I have for you guys to answer.

1)	Printer&#8212;I have an Epson Stylus CX4600. Will this work? Will I have to press some buttons and twist some knobs for it to work, or will it work automatically?
2)	Downloading freeware&#8212;Yeah I know there&#8217;s a world-class downloading manager whatcha-ma-call-it, but what about stuff that ain&#8217;t included there. I know there&#8217;s a terminal, but I don&#8217;t know what the hell is a sudo (and I&#8217;ve watched Fringe), so can anyone give me a quick and essential step-by-step basics of how to download things manually?
3)	Downloading software&#8212;CDs. Anyway to do this, or should I scrap the idea?
4)	Media player&#8212;XP&#8217;s media player&#8217;s pretty good, if you ask me. But is there an equal (or better) open source alternative to it for Ubuntu? Does it read DVDs? Does it have a &#8216;repeat&#8217; feature so I can keep listening to the same song? Would it play most file formats?
5)	&#8220;Zip&#8221; and &#8220;Tar.Gz&#8221;&#8212;Tell me if I&#8217;m wrong, but .zip is basically a compressed folder file format, right? So is tar.gz the equivalent for Ubuntu? If so, does Ubuntu automatically read tar.gz? Hell, does it read .zip for that matter? It&#8217;s an odd question but I do a lot of design work and I have to download PSDs (PhotoShop files) which are often compressed.
6)	Limewire&#8212;HUH?
7)	Flash, Java, Adobe Reader, Shockwave, etc.&#8212;These are almost essential downloads for computers so, does it work and how do I get it on Ubuntu?
8)	Video editing&#8212;I know, it&#8217;s unlikely, but is it possible? Are there any programs that allow me to do this?
9)	PhotoShop&#8212;Does it work? How&#8230;?
10)	One more thing&#8212;how do I know if my CPU is 62-bit or 32-bit? There seems to be two separate downloads for them, so how do I know I&#8217;m getting the better deal?
11)	Would you recommend Ubuntu to just about everyone or only to programmers/computer engineers/geeks?

---

### Post by kansasnoob on 2008-10-30
Have you considered a dual boot?

I like it, it allows you to go back to what's familiar so it lets you "ease into" the transition.

Simple guide (if XP is already installed):

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Bodsda on 2008-10-30
You can do almost all of what you ask, except photoshop, if its a new version wine may not support it. To be totally honest it may not be worth it if your not willing to put the time and small amount of effort into to learning how to use Ubuntu.

---

### Post by nisaky on 2008-10-30
1) No idea, you must try :S
2) sudo if what you add to run something as root (super user, administrator), but you can see list of free games here:
[http://gaming.gwos.org/doku.php/guides:64bit](http://gaming.gwos.org/doku.php/guides:64bit)
3) You can download software as you did it before (from torrents?)
4) M player. I think it is better than media player, it has more options (faster/slower) and plays all kinds of video files.
5) tar.zg is like .zip, but ubuntu has some more types of it. It detects them all automatically. Like photoshop, you have GIMP by default, which is even more powerful.
6) No need of it...
7) Flash, you download it with your web-browser when you find it.
8) It is possible, i dont know programs.
9) GIMP.
10) type in terminal: 
```
uname -a
```
if it says X86_64 it is 64 bit, if it says i386 it is 32 bit.
11) Ubuntu is easiest to use linux, so i recommend it to everyone.

---

### Post by Periswell on 2008-10-30
wow your are inquisitive. ok im not going to do as you will have to learn if you are going to have ubuntu, just google most the questions. with the terminal problem just use synaptic package manager. With software on CDs check if they work on ubuntu first by googleing it. with media players, ubuntu has got loads and the best for you to choose from. for dvds menus though i suggest VLC or xine as the defalt media player does not support dvd menus (legal issues). and the play all the windows formats and more. .zip and .tar.gz are preety much the same, you can open .zip archives in ubuntu. yes there is limewire but i highly would suggest not using it as the police and music companys are finding the ip addresses of the people who download the songs and suing them. Flash (internet plugin) works, java works adobe reader (im quessing pdf) does not but there is a equivelent reader that is installed by default. i can't rebember if shockwave works so google that as well. the are lots of video editors on ubuntu like kino for you video camera and avidemux to change the type of video so it can go on ipods, psps ect. also there is the open movie editor and cinepaint. photoshop does not work but there is an equivilent called 'the gimp' which is free. i cant cheack if it can open you photoshop files as my computer is broken at the moment. to be safe choose 32-bit (it does run on 64-bit computers). finally as the slogon of ubuntu goes... 'ubuntu, linux for human beings' so i would suggest it to human beings and not house hold pets. 
good luck and welcome to ubuntu (hopefully if i have not put you off :).

-joshua

---

### Post by Jack1989 on 2008-10-30
To download apps, just try "sudo apt-get install" and then the name of the program. If that does'nt work, download the source code from the developers website and then compile it and install it.
"./configure"
"sudo make"
"sudo make install".

Read the install guide on the website you downloaded the software from. Very easy!

---

### Post by KnottyMars on 2008-10-30
Yeah, I hear ya about jumping from XP. I just discovered Ubuntu in the last week and its been really fun messing with it. 

Im an IT guy, but Im not really familiar with much coding other than basic html and php scripting. This has been a good learning experience and the price is right lol ;) 

Looking forward to learning more, but for a basic internet and email machine, this is awesome. No more dealing with licenses. Go Ubuntu!!!

---

### Post by lykwydchykyn on 2008-10-30
> **Obero said:**
> 
1)	Printer—I have an Epson Stylus CX4600. Will this work? Will I have to press some buttons and twist some knobs for it to work, or will it work automatically?

No idea.  You might check here: [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting)
> 
2)	Downloading freeware—Yeah I know there’s a world-class downloading manager whatcha-ma-call-it, but what about stuff that ain’t included there. I know there’s a terminal, but I don’t know what the hell is a sudo (and I’ve watched Fringe), so can anyone give me a quick and essential step-by-step basics of how to download things manually?

I guess that would depend on what it was you were downloading and how they packaged it.  If it's free, Linux compatible, and not overly restrictive in its distribution license, it's usually in the repositories.
> 
3)	Downloading software—CDs. Anyway to do this, or should I scrap the idea?

I don't know what you mean.  can you elaborate?
> 
4)	Media player—XP’s media player’s pretty good, if you ask me. But is there an equal (or better) open source alternative to it for Ubuntu? Does it read DVDs? Does it have a ‘repeat’ feature so I can keep listening to the same song? Would it play most file formats?

I typically use kaffeine because I'm a KDE user.  VLC is also pretty good, it plays just about anything.  There are a million of them to pick from, and most use either xine or mplayer for a backend so most of them support the same formats and so forth.
> 
5)	“Zip” and “Tar.Gz”—Tell me if I’m wrong, but .zip is basically a compressed folder file format, right? So is tar.gz the equivalent for Ubuntu? If so, does Ubuntu automatically read tar.gz? Hell, does it read .zip for that matter? It’s an odd question but I do a lot of design work and I have to download PSDs (PhotoShop files) which are often compressed.

zip is fully supported. tar.gz is a unix format that's been around since time out of mind.  Pretty much any major file compression format is fully supported IME.
> 
6)	Limewire—HUH?

Don't know, I don't use it, but I hear some folks use something called frostwire that does the same thing.
> 
7)	Flash, Java, Adobe Reader, Shockwave, etc.—These are almost essential downloads for computers so, does it work and how do I get it on Ubuntu?

Flash- you can get a .deb package from adobe's site, or I believe it's in the repositories.
Java - in the repositories
Adobe reader - you can download a .deb from adobe or use the Medibuntu repository
Shockwave - not on linux, adobe has no plans for it.  Thanks a lot, adobe.
> 
8)	Video editing—I know, it’s unlikely, but is it possible? Are there any programs that allow me to do this?

Yes, though I don't use them so I'm no expert.  Kino is a popular option, but there are others.
> 
9)	PhotoShop—Does it work? How…?

supposedly runs in Wine or Codeweaver's crossover office.  haven't tried it myself.
> 
10)	One more thing—how do I know if my CPU is 62-bit or 32-bit? There seems to be two separate downloads for them, so how do I know I’m getting the better deal?

Your cpu is not 62 bit because there is no such thing.  I guess you mean 64 bit.  I would recommend you use 32 bit regardless of what your cpu is, because Adobe in particular doesn't seem keen on supporting 64 bit Linux. 
> 
11)	Would you recommend Ubuntu to just about everyone or only to programmers/computer engineers/geeks?

That's a bit of a false dichotomy.  There are definitely people I wouldn't recommend it to, but not purely on some linear measurement of their computer skills.  I wouldn't recommend it to someone who:
 - absolutely must run proprietary software titles only available on Windows and won't accept alternatives.
 - owns a computer mainly just to run Games.  And I don't mean games, I mean Games with a capital "G", as in big-name blockbuster release must-have-the-latest-video-hardware-to-view-the-demo type Games.  
 - Likes going to a retail store and paying money for boxed software

Otherwise, I'd say you're a good candidate, no matter what you skill level is.  Probably a better candidate if you know very little, because you'll have less to relearn.

---

### Post by Zzl1xndd on 2008-10-30
1) your CX4600 should install automatically I'm pretty sure its in the driver list.

2) My Advice for this is look for a .deb it is a lot like an .exe for windows double click and install ([http://www.getdeb.net/](http://www.getdeb.net/))

3)Not really sure what your asking could you explain?

4)I would say go with VLC for Videos and Amarok for Music install Ubuntu restricted extras from the Add/remove to get most formats. For DVD there is a little extra to do because of the encryption or you can by the proper codec from the Ubuntu site.

5)A simple Yes to everything

6)Frostwire will connect you to the limewire network and I believe Limewire makes a Linux version as well but I could be wrong.

7)Everything but shockwave is available and comes in the restricted extras. The Adobe Reader has a .deb on the Adobe site.

8.)I hear good things about Cinelerra

9)There is no Linux Version but I am told CS2 works well in Wine

10)For the time being I would take the 32 edition unless you have more then 4 gigs of ram.

11)I recommend OS based on peoples needs. If Ubuntu fits the needs then I recommend it if not then I recommend OSX, BSD, Solaris or Windows based on what the user wants to do.

---

### Post by Jack1989 on 2008-10-30
Yes, you can use Limewire on Ubuntu, used it several times.
You can download it from the website. Link to download site:
[http://www.limewire.com/download/download.php?version=linux_deb](http://www.limewire.com/download/download.php?version=linux_deb)

I think you just have run the file and then you are ready to go :)

---

### Post by handydan918 on 2008-10-30
> **Obero said:**
> I&#8217;m going to be completely honest with you&#8212;I&#8217;ve tried Ubuntu before. Then went back to XP, then ran away and hid behind Ubuntu and then crawled back to XP again. Both of them ain&#8217;t perfect operating systems, but I&#8217;m kind of more tired of XP than I am of Ubuntu. The problem I have with Ubuntu is all the systematic coding and programming you have to do, but here&#8217;s a few questions I have for you guys to answer.

1)	Printer&#8212;I have an Epson Stylus CX4600. Will this work? Will I have to press some buttons and twist some knobs for it to work, or will it work automatically?
Best way to see if a printer is supported is to check it out at [www.linuxprinting.org](www.linuxprinting.org)> 

2)	Downloading freeware&#8212;Yeah I know there&#8217;s a world-class downloading manager whatcha-ma-call-it, but what about stuff that ain&#8217;t included there. I know there&#8217;s a terminal, but I don&#8217;t know what the hell is a sudo (and I&#8217;ve watched Fringe), so can anyone give me a quick and essential step-by-step basics of how to download things manually?
You can download anything you want to, but most of the programs out there are written for Windows, and cannot be made to run on any other O/S (except via emulation or WINE, etc.).To start off, you are well advised to stick to the available software in the Ubu repositories. There are around 20,000 titles. Plenty to get started....
> 
3)	Downloading software&#8212;CDs. Anyway to do this, or should I scrap the idea?
Not sure what you mean here.> 
4)	Media player&#8212;XP&#8217;s media player&#8217;s pretty good, if you ask me. But is there an equal (or better) open source alternative to it for Ubuntu? Does it read DVDs? Does it have a &#8216;repeat&#8217; feature so I can keep listening to the same song? Would it play most file formats?

Can't really address video too much, but I LOVE Amarok for audio. Very configurable.> 

5)	&#8220;Zip&#8221; and &#8220;Tar.Gz&#8221;&#8212;Tell me if I&#8217;m wrong, but .zip is basically a compressed folder file format, right? So is tar.gz the equivalent for Ubuntu? If so, does Ubuntu automatically read tar.gz? Hell, does it read .zip for that matter? It&#8217;s an odd question but I do a lot of design work and I have to download PSDs (PhotoShop files) which are often compressed.

tar.gz is indeed a compressed archive, but there is no further generalization that can be made. The file could contain a binary installer, or source code, or a root kit, or pictures of your wife, or anything else.
However, since photoshop won't run natively on Linux...
> 

6)	Limewire&#8212;HUH?

Double HUH.> 

7)	Flash, Java, Adobe Reader, Shockwave, etc.&#8212;These are almost essential downloads for computers so, does it work and how do I get it on Ubuntu?

Flash, Java, Adobe Reader can be run on linux. Shockwave is not available yet, AFAIK> 

8)	Video editing&#8212;I know, it&#8217;s unlikely, but is it possible? Are there any programs that allow me to do this?

Unlikely? All the hugest rendering farms run linux....There are some really good graphics and editing progs available. Just search thru synaptic.
> 
9)	PhotoShop&#8212;Does it work? How&#8230;?

Maybe in WINE....> 

10)	One more thing&#8212;how do I know if my CPU is 62-bit or 32-bit? There seems to be two separate downloads for them, so how do I know I&#8217;m getting the better deal?

You can install 32bit on a 64 bit cpu, but not vice versa. You can use google to find out if your cpu is 32 or 64 bit.> 

11)	Would you recommend Ubuntu to just about everyone or only to programmers/computer engineers/geeks?

Everyone who is not crippled by needing Windows-only software should use it. I have fought no security wars since using linux exclusively.

---

### Post by hyperhopper on 2008-10-30
W00h000!!! We got us another buddy!

yah, it can do most of what yours asking, cad uses ;imewire and the same printer... not sure about photoshop, but we have gimp which is free!!!! and, uhhh....yah installing tar.bz is easy, just click on the download link, then hit open, extract, and there is almost always a readme.txt telling you what to do....

---

### Post by Kellemora on 2008-10-30
Hi Obero

Everyone else answered your individual questions!

I'm only jumping in to say, I'm 61 years old, got my first glimpse of Ubuntu in early September.
Already I have converted my entire office over to Ubuntu!
Except for back office accounting, which is not yet supported well enough by the vendors to do so.

Yea, I had a couple of complaints the first few days because things were different.
BUT, everyone is now very happy, and so am I, we no longer are pushing deadlines in a mad rush, things are getting done much faster than ever before.

We are very heavy in graphics modification and usage.  Gimp outshines Photoshop in many ways.
Even Open Office writer does not have the glitches in it msWORD does.  Like images hopping all over the place on us, just when we think were done.

It is DIFFERENT than the DOZE, but you just gotta be different to be better!

TTUL
Gary

---

### Post by BobSongs on 2008-10-31
> **Kellemora said:**
> <snip> Gimp outshines Photoshop in many ways.</snip>

Sorry: it's off topic. But you mentioned GIMP. Thought I'd suggest meetthegimp.org for video tutorials.

---

### Post by Kellemora on 2008-10-31
Hi Bob

Thank you very much for that link!

I basically do photo editing for pamphlets and newsletter and some photo restoration on the side.

As much as I've already used Gimp, I had no idea WHAT all those other features were.

Looks like I will have to get 8.10 for some of the new stuff though.

More things to play with and learn as if I don't have my hands full already, hi hi.....

TTUL
Gary

---

### Post by Keen101 on 2008-10-31
2) Downloading freeware= [B]yes, look for easy .deb files or .run files first. They are the equivalent to .exe files on windows.
[/B]
3) Downloading software&#8212;CDs=[B]yes, but i really don't know what you are asking.
[/B]
4) Media player&#8212;**Yes, there are many. VLC is nice, but Totem can usually do fine if you install all the extra codecs. Dvd's too, but you might have to follow this guide.**[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html](http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html)

5) &#8220;Zip&#8221; and &#8220;Tar.Gz&#8221;&#8212; [B]Yes Tar files are the "zip files". Ubuntu can read them out of the box. It can read Zip files too. Hell, it can even read proprietary .rar files too, but you need to install that from synaptic as it does not have a GPL license. 
[/B]

6) Limewire&#8212;[B]yeah, the "transmission" client is built into ubuntu now.
[/B]
7) Flash, Java, Adobe Reader, Shockwave, etc.&#8212;[B]Yes these are available. Plenty of tips from googling or searching ubuntu forums. If yours is a 64bit system, there are even specific instructions.
[/B]
Video editing&#8212;[B]I've heard of kino, cinelerra, and a couple others.
[/B]
9) PhotoShop&#8212;**yes, CS2 works in WINE. But, i personally reccomend GIMP instead. I've used both, and i like GIMP better once i got used to it.**

11) Would you recommend Ubuntu to just about everyone or only to programmers/computer engineers/geeks? **I reccomend it to everyone who is willing to listen. Those who don't are either are Vista fanatics, or MAC fanatics.**

---

### Post by lykwydchykyn on 2008-11-01
Not that this is important, but people keep saying .deb files are equivalent to .exe files on windows.  This is not even true in the slightest.  .deb files are more analogous to .msi files on Windows, because they are non-executable.  Just want to say that so nobody gets confused.

---

### Post by Teabicky on 2008-11-01
I have just changed from Xp and at first found all the web advice went way over my head (I really was just a point and click man!).  So I brought a book.  It's called > Beginning Ubuntu Linux and it is amazing, it even comes with a chapter on GIMP.  My understanding of Ubuntu and Linux in general has increased no end.

---

