---
title: "wierd fonts with wine"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by muted1987 on 2008-11-29
i dont know how to explain so theres a screen of whats happening followed the instructions on  wine's apps db can anyone explain and resolve please thx in advance.

[IMG]http://i174.photobucket.com/albums/w85/muted_apoc/Screenshot-Settings-Steam.png[/IMG]

---

### Post by MasterSander on 2008-11-29
Try disabling compiz to see if that changes anything.

---

### Post by muted1987 on 2008-11-29
i have the desktop to no effects and same result

---

### Post by GeekyBeans on 2008-11-29
Same problem here.
No 3D desktop effects enabled.


muted1987 : Have you installed PlayOnLinux?

---

### Post by gandaran on 2008-11-29
this could be due to the theme you using, try changing to another and install some microsoft fonts in wine

---

### Post by GeekyBeans on 2008-11-29
I have the msttcorefonts package installed.

I have also copied the fonts into .wine/drive_c/windows/Fonts without success.

The problem still exists.

---

### Post by muted1987 on 2008-11-30
hey no i dont have playforlinux installed never heard of it and i also have the msstcorefonts package insdtalled wil try diff theme and see whats going on or if it works

no changing themes doesnt work

---

### Post by Terrycymru on 2008-11-30
> **GeekyBeans said:**
> I have the msttcorefonts package installed.

I have also copied the fonts into .wine/drive_c/windows/Fonts without success.

The problem still exists.

 Don't you mean ~/.wine/drive_c/windows/fonts ?

---

### Post by ets2006 on 2008-11-30
Try running another application under wine, some apps dont work very well under wine.

Just had a proper look at the picture, and it looks like wine is decoding all of the languages in your application, perhaps install XN resource editor and edit all of the dialogs foreign language text, it might stop the text overlaying??

---

### Post by muted1987 on 2008-11-30
> **ets2006 said:**
> Try running another application under wine, some apps dont work very well under wine.

the app im trying to run is steam and that apparently has a gold status but i have also tried  running lg3g.exe which is a nice lil program that will unlock your lg phone as long as you follow a tutorial on how to back up first but i get the same look as wit hsteam

---

### Post by ets2006 on 2008-11-30
i am trying to install steam on my machine, and i might be able to create a patch.

ok, steam installed ok and the fonts so far have been fine...

perhaps you need to do some updates, make sure that you have the latest version of steam, wine and wine's dependencies.

---

### Post by muted1987 on 2008-11-30
steam is easy enough to install if you run into troubles just follow what they say on appsdb and everything is sorted

---

### Post by ets2006 on 2008-11-30
yeah, i installed steam ok and the fonts are fine, it looks like a version thingy now!

could you tell me your ubuntu version and your wine version?

---

### Post by muted1987 on 2008-11-30
using 8.10 and wine from synaptic think thats the stable version 1.00.1

---

### Post by ets2006 on 2008-11-30
hmm, i got wine 1.0, and ubuntu 8.04lts
try changing wine settings, like adding app compatibity..

applications>wine>configure wine
open applications tab
click on add application
browse for app
  C:\program files\steam\steam.exe
on the applications tab, there will be a drop-down labeled windows version
 select windows xp
click on apply
click on ok
run steam
if this dosent work, then i'm guessing that its ibex thats causing the problem.(unlikely)

---

### Post by muted1987 on 2008-11-30
i cant get into it as all the gfonts aare overlapping on this aswell and i cant see where to cahnge anything

---

### Post by ets2006 on 2008-11-30
if the fonts are overlapping on that then i cannot help you - sorry!

---

### Post by Smigh on 2008-12-04
I have the exact same problem. Fonts seem to be overlapping on wine configuration utility.

This is a fairly new install of Intrepid and I got wine from synaptic (stable 1.0.1).

I just installed java, likewise-open, compiz manager app and startupmanager. The first time I tried wine I had no text at all but after I've disabled desktop effects I was still left with this overlapping issue.

Any ideas?

---

### Post by muted1987 on 2008-12-06
im still trying to work this one out myself

---

### Post by Kellemora on 2008-12-06
Hi ets2006

You don't perchance have the SAME fonts installed in two different font files do you?

If you are using Truetype fonts, they should be installed in
/usr/share/fonts/truetype and you can keep them in their own folders in that directory for convenience reasons too.

When I first started using Ubuntu, I was told to make a hidden folder in my home directory:  EG: /home/user/.fonts which I found out is not only a BAD idea, it means you need to load the same fonts for each user on the computer and in some cases, for each program that resides elsewhere, such as in .wine.

Everything was fine until I installed msttcorefonts and it duplicated some fonts I already had in the hidden .fonts file, that's when I started getting screens that looked like yours.
I deleted the hidden .fonts file from my home directory and everything returned to normal once again.

I have ZERO fonts in the .wine/windows/fonts folder, it's completely MT of any and all fonts.  If a Windows program installs any fonts there, I immediately move them to /usr/share/fonts/truetype and the programs I've installed work just fine and use the fonts they are supposed to use.

Don't know if that's your problem or not, but it fixed my problems with text on text offset a tad so it was unreadable or weird looking.

TTUL
Gary

---

### Post by GeekyBeans on 2008-12-17
SOLVED (for me anyway):

add this line (at/near the bottom) of file "user.reg" (user.reg is inside .wine folder)

     "ClientSideWithRender"="N"

below section:

     [Software\\Wine\\X11 Driver]


.

---

### Post by jalehtor on 2008-12-17
Geekybeans, if I put my desktop effects on none, I get smudgy wine config. If I put my desktop effects on anything else, I get the wine thing with no text.

Could conpizconfig have anything to do with this? Should I get rid of conpiz? If so, how?

As far as your suggestion, how do I locate my .wine folder?

---

### Post by shae on 2008-12-17
Do you have Tomaha font installed for wine?

Get it form here: [http://www.google.com/search?hl=en&q=tahoma+filetype%3Attf&btnG=Search](http://www.google.com/search?hl=en&q=tahoma+filetype%3Attf&btnG=Search)

Put it in your fonts folder in your wine directory.

---

### Post by GeekyBeans on 2008-12-23
> **jalehtor said:**
> Geekybeans, if I put my desktop effects on none, I get smudgy wine config. If I put my desktop effects on anything else, I get the wine thing with no text.

Could conpizconfig have anything to do with this? Should I get rid of conpiz? If so, how?

As far as your suggestion, how do I locate my .wine folder?

to locate your .wine folder, open your "Home Folder", click  "View" and click in the box next to "Show Hidden Files".

you will now find the .wine folder inside your "Home Folder".

as far as your desktop fx issue(s): i do not have desktop fx enabled and am uncertain what to suggest. sorry.

---

### Post by thimo.jansen on 2009-01-18
Geekybeans, thanks! That solved it for me on Ubuntu 8.10

---

