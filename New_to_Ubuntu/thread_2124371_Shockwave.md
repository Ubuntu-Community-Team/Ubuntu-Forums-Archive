---
title: "Shockwave"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by jfbooth on 2013-03-10
Xubuntu 12.04, XFC.  Google CHROME 25.0.1364.160

I think I may be one of the few who has not managed to fix the problem "**Could not load Shockwave Flash**".  I say because for months I have tried every fix I could find without success ... of which there are many.

I also have a recent ver of Firefox with the same problem, but will uninstall it if I get CHROME to work.

Here is what I know.  See the attachment for the Chrome Plugins.  I have tried running both, and either/or with a CHOME restart after each.  No Joy.

[ATTACH=CONFIG]240030[/ATTACH]

I have no idea if it is pertinent, but:

**/home/jb/.config/google-chrome/PepperFlash** is an empty folder.

**/opt/google/chrome/PepperFlash** contains libpepflashplayer.so and manifest.json

**/home/jb/.config/chromium** is a loaded up folder ... but I uninstalled Chromium a little while ago.  No reference to Flash in this folder though.

**/usr/lib/flashplugin-installer/libflashplayer.so**  exists

**/usr/lib/mozilla/plugins/libflashplayer.so** exists

I have found a LOT of people with the problem with about as many solutions.  None have worked for me.  Would very much appreciate a solution.  Thank you in advance.

---

### Post by jfbooth on 2013-03-13
Waitin' for some help, I copied [COLOR="#B22222"]libpepflashplayer.so[/COLOR] and [COLOR="#B22222"][COLOR="#B22222"]manifest.json[/COLOR][/COLOR] to **/home/jb/.config/google-chrome/PepperFlash** ... restarted Chrome ... no joy ... so I deleted them.  Still trying to solve this maddening problem.

---

### Post by ManamiVixen on 2013-03-13
What CPU does your computer have?

---

### Post by jfbooth on 2013-03-13
> **ManamiVixen said:**
> What CPU does your computer have?


It's an old Windows ME desktop machine .. Intel Celeron (COPPERMINE).  512MB of memory .. maxed out.  Have not had this shockwave problem until the rest of the world started to.  Unfortunately, unlike most everyone else, ... I can't seem to fix it.

THANK YOU, for your interest.

---

### Post by ManamiVixen on 2013-03-13
Your CPU dosen't have the SSE2 instruction set which is required by the later versions of flash. You need to install something like version 11.0 or older. Otherwise, you are flash-less.

---

### Post by jfbooth on 2013-03-13
> **ManamiVixen said:**
> Your CPU dosen't have the SSE2 instruction set which is required by the later versions of flash. You need to install something like version 11.0 or older. Otherwise, you are flash-less.


Well, .. that would CERTAINLY explain it.  Brings me to .. "how do I obtain/install 11.0" ... what do I need to UNINSTALL (if anything)?.

THANK YOU for defining the problem.  If you can help w/ solution .. that would be tremendous.  I am somewhat of a Linux rookie.

edit:  Found a tremendous archive of flash at [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html) but nothing (obvious) for Ubuntu/Linux.

---

### Post by jfbooth on 2013-03-17
I found install_flash_player_10_linux.deb from an UNKNOWN site ... actually, someone's MEDIAFIRE library.  I have no idea if it is valid.  Thing is .. I have no choice but to cross my fingers and go for it ... it seems ... UNLESS SOMEONE offers better source and/or advice.  Will wait until no one replies ... then ......
Thank you in advance.

---

### Post by Bashing-om on 2013-03-17
jfbooth;
I do not use this add-on, but I have seen nothing but good for it. Have you tried the add-on "Flash-aid" ? Supposedly will (un)install conflicting flashs and according to your architecture install the proper flash. (???)
[INDENT=2]
try'n to help

[/INDENT]

---

### Post by jfbooth on 2013-03-17
> **Bashing-om said:**
> jfbooth;
I do not use this add-on, but I have seen nothing but good for it. Have you tried the add-on "Flash-aid" ? Supposedly will (un)install conflicting flashs and according to your architecture install the proper flash. (???)
[INDENT=2]
try'n to help

[/INDENT]

You are most kind, and I thank you for your reply.  Flash Aid ... a FIREFOX add-on .... and does not list at the GOOGLE CHROME web store.

There is however; "Missing Plug-in" Fix ( [https://chrome.google.com/webstore/detail/s%E1%BB%ADa-l%E1%BB%97i-missing-plug-in/plkplgmhfkkhokgkdkblfcnfeccpippe](https://chrome.google.com/webstore/detail/s%E1%BB%ADa-l%E1%BB%97i-missing-plug-in/plkplgmhfkkhokgkdkblfcnfeccpippe) ) which, apparently, strives to do the same thing (I think).  I have it installed ... and (I guess) it is doing its job .... because:

after installing that version 10 deb (which actually shows as v. 11), I now have flash function in chrome .. but it is horribly slow and mostly just buffers AND Chrome keeps telling me my add-on is out of date ... allowing me EVERY TIME to UPDATE or RUN THIS TIME ONLY.  Of course, I do not want to update because the latest ver does not run on my Celeron Coppermine.

Confession:  I am not actually running CHROME, .. I am running IRON ( [http://www.srware.net/en/software_srware_iron.php](http://www.srware.net/en/software_srware_iron.php) )

I found I can subdue this notification ... 

> Note: Although not recommended, if you don't want Google Chrome (Iron) to notify you when a plug-in is out of date, use the command line flag --allow-outdated-plugins. Instructions on how to add a command line flag can be found on our Chromium site .

but I do not know how to add a command line flag in Linux (Xubuntu 12.04).  Making progress ... but far from anything very satisfactory.  THANK YOU AGAIN.

Correction:  That ver 10 deb is actually ver 10 ... my mistake.  > Iron:plugins shows:

Adobe Flash Player - Version: 10.1 r102 Download Critical Security Update
Shockwave Flash 10.1 r102
Name:	Shockwave Flash
Version:	10.1 r102
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

---

