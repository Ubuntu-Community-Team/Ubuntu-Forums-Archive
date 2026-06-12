---
title: "HOWTO: Install IceWeasel Web browser in Dapper or Edgy"
date: 2006-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by K.Mandla on 2006-10-03
**[COLOR="Red"]STOP![/COLOR]** Before following the instructions in this howto, check to see if any important links or instructions have been updated on the InstallIceweasel wiki page.

[https://wiki.ubuntu.com/InstallIceweasel](https://wiki.ubuntu.com/InstallIceweasel)

Additionally, if you have tweaks or suggestions for installing Iceweasel, the wiki page is a preferable place to put them. Thanks, all! :mrgreen: *-- 06/11/01*

**Background**

[INDENT]This is a terribly simple howto for installing IceWeasel. With the recent unpleasantness between the Mozilla organizers and Debian (and ultimately, Ubuntu), some people have threatened to drop Firefox altogether from their machines. 

I won't get into the underlying issues or debate; if you've found your way to this page, you probably already know why you want it. However, there is a nice encapsulation of the issue at [Firefox not really free?]("http://www.internetnews.com/dev-news/article.php/3634591") If you want to read more about the legal issues attached to using Firefox, the original Debian "bug report" is [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354622"). 

If you want more information than that, the subject has been discussed *ad nauseum* in the forums; search for "firefox" and chances are the top ten threads will all be about it. 

IceWeasel is a direct outgrowth of that spat, and you can find out all you want to know about the browser at [the IceWeasel home page]("http://www.gnu.org/software/gnuzilla/"). (A quick note: Gnuzilla is the Mozilla suite, while IceWeasel is just the browser. I won't get into the suite for this howto; I'll leave that to someone else. ;) 

This howto has been tried on Dapper and Edgy machines running straight Ubuntu, Xubuntu and Openbox, and the results are the same. Furthermore, I think you'll find that IceWeasel looks and behaves just like Firefox or [Swiftfox]("http://www.getswiftfox.com"), and that most -- if not all -- of your extensions work as well. Having said that, there is always the chance that it won't play nice with your hardware ... but really, having come this far, isn't worth trying? ;) )
[/INDENT]

**Installation**

[INDENT]**[COLOR="Red"]UPDATED 06/10/05: [/COLOR]**Kilz was kind enough to put up a .deb of IceWeasel, if you'd prefer to go that route. It's  located [here]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.4-g1-i386.deb"). Kilz also has a Iceweasel howto for 64-bit users [here]("http://www.ubuntuforums.org/showthread.php?p=1174435"). Be sure to read those pages for any special installation instructions.  

Installing is as simple as downloading the compressed package, decompressing it and pointing your operating system at it. For a list of GNU FTP mirrors, look here: [http://www.gnu.org/prep/ftp.html](http://www.gnu.org/prep/ftp.html). Browse one of the mirrors and look for a *gnuzilla* folder, then a file called "iceweasel-1.5.0.4-g1-i386.tar.bz2". Remember that the version number could change; what you want is the i386 designation. I don't think there are versions for other architectures; that could change in the future. 

**[COLOR="Red"]NOTE:[/COLOR]** As predicted, the version has jumped to 1.5.0.7. Kilz has updated his [1.5.0.7 package]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.7-ubuntu-i386.deb"), and there's a [new Iceweasel download page]("http://gnuzilla.gnu.org/download/") as well. ...

However you get it, download it to your computer. Now, **for terminal junkies**, open a terminal and move to the folder where you put the file. Then ...

```
tar -xvf iceweasel* -C the_directory_where_you_want_iceweasel_installed
```
If you decide to put it outside your own home directory, remember to use *sudo* before that command. Tar will decompress the package into a folder. Now might be a good time to rename that folder too, if you want it to be easier to type in the future.

**For GUI junkies**, open the file with XArchiver, and tell it to extract the package. :)
[/INDENT]

**Making it the default**

[INDENT]Inside that folder is the iceweasel shell script -- it's called (of all things) "iceweasel." (Not iceweasel-bin. You don't want that one.) The trick now is setting your desktop to open that shell script by default. 

Personally, I'm an Openbox man, so for me it's as easy as opening ObMenu and changing the trigger line to point at the iceweasel shell script.

For Xubuntu or XFCE fans, open Applications > System > Preferred Applications, and select Other. Browse to the iceweasel shell script.

For Gnome, click System > Preferences > Preferred Applications. Change the Web browser option to point at the iceweasel shell script. (Sorry if I'm slightly off the mark on Gnome; I haven't used it in a while. ;) )

For KDE ... well, I'm not very familiar with KDE, and chances are if you're using KDE, you're a Konqueror fan. If someone can chime in on that, I'd appreciate the help. 

One last note: Remember that the "globe icon" on your desktop might or might not trigger your desktop's default browser. In that case, you'll have to change the properties of the icon and redirect it to the iceweasel shell script.

**Added 06/10/10: **If you want an icon that you think better reflects the name "Iceweasel," there's a [wiki page]("https://wiki.ubuntu.com/IceWeaselIcon") chock full of ideas that you can try. Grab your favorite and click to your heart's delight![/INDENT]

I think that's about it. You can now surf with a clear conscience. :mrgreen: If you like it and decide to stick with it, a quick note of thanks to the folks who made it would be a nice thing to do.

**ADDED: 06/10/05**

[INDENT]If you're having trouble with browser identification -- in other words, sites block your access because you're "not using Firefox" -- try this:

[LIST=1]
[*]Open "about:config" in IceWeasel's address bar.
[*]In the "Filter" box, type **general.useragent.extra.firefox**.
[*]Where you see the word "Iceweasel", right-click and pick "Modify"
[*]Then replace the word "Iceweasel" with "Firefox".
[*]Close the page (or the tab).
[/LIST]
"Masquerading" your browser like that simply prevents the host site from telling you you're not using Firefox. Aside from that, it should have no effect whatsoever on your collective Internet experience. :biggrin: Of course, if it doesn't work, let us know.[/INDENT]

**ADDED: 06/10/10** A corrected link to the Gnuzilla download page and the link to the wiki.

---

### Post by stateq2 on 2006-10-07
to add....you can also associate your mozilla plugin directory w/ iceweasel...in the syntax:
```

ln -s /path/to/mozilla/plugins ~/.gnuzilla/

```

if you have firefox installed, you can do it w/ this command:
```

ln -s /usr/lib/firefox/plugins ~/.gnuzilla/

```

---

### Post by K.Mandla on 2006-10-07
> **stateq2 said:**
> to add....you can also associate your mozilla plugin directory w/ iceweasel...in the syntax:
```

ln -s /path/to/mozilla/plugins ~/.gnuzilla/

```

if you have firefox installed, you can do it w/ this command:
```

ln -s /usr/lib/firefox/plugins ~/.gnuzilla/

```
Thanks! I knew there was something I had forgotten. Cheers! :mrgreen:

---

### Post by motang on 2006-10-07
> **K.Mandla said:**
> **Background**

[INDENT]This is a terribly simple howto for installing IceWeasel. With the recent unpleasantness between the Mozilla organizers and Debian (and ultimately, Ubuntu), some people have threatened to drop Firefox altogether from their machines. 

I won't get into the underlying issues or debate; if you've found your way to this page, you probably already know why you want it. However, there is a nice encapsulation of the issue at [Firefox not really free?]("http://www.internetnews.com/dev-news/article.php/3634591") If you want to read more about the legal issues attached to using Firefox, the original Debian "bug report" is [here]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=354622"). 

If you want more information than that, the subject has been discussed *ad nauseum* in the forums; search for "firefox" and chances are the top ten threads will all be about it. 

IceWeasel is a direct outgrowth of that spat, and you can find out all you want to know about the browser at [the IceWeasel home page]("http://www.gnu.org/software/gnuzilla/"). (A quick note: Gnuzilla is the Mozilla suite, while IceWeasel is just the browser. I won't get into the suite for this howto; I'll leave that to someone else. ;) 

This howto has been tried on Dapper and Edgy machines running straight Ubuntu, Xubuntu and Openbox, and the results are the same. Furthermore, I think you'll find that IceWeasel looks and behaves just like Firefox or [Swiftfox]("http://www.getswiftfox.com"), and that most -- if not all -- of your extensions work as well. Having said that, there is always the chance that it won't play nice with your hardware ... but really, having come this far, isn't worth trying? ;) )
[/INDENT]

**Installation**

[INDENT]**[COLOR="Red"]UPDATED 06/10/05: [/COLOR]**Kilz was kind enough to put up a .deb of IceWeasel, if you'd prefer to go that route. It's  located [here]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.4-g1-i386.deb"). Kilz also has a Iceweasel howto for 64-bit users [here]("http://www.ubuntuforums.org/showthread.php?p=1174435"). Be sure to read those pages for any special installation instructions.  

Installing is as simple as downloading the compressed package, decompressing it and pointing your operating system at it. For a list of GNU FTP mirrors, look here: [http://www.gnu.org/prep/ftp.html](http://www.gnu.org/prep/ftp.html). Browse one of the mirrors and look for a *gnuzilla* folder, then a file called "iceweasel-1.5.0.4-g1-i386.tar.bz2". Remember that the version number could change; what you want is the i386 designation. I don't think there are versions for other architectures; that could change in the future.

I did notice that some of the mirrors didn't have a *gnuzilla* folder; it might be that it's too new. Here's one that's working (at USC in California, I think): [ftp://mirrors.usc.edu/pub/gnu/gnuzilla](ftp://mirrors.usc.edu/pub/gnu/gnuzilla). Again, grab the i386 file.

If you just want a direct link, click [here]("ftp://mirrors.usc.edu/pub/gnu/gnuzilla/iceweasel-1.5.0.4-g1-i386.tar.bz2") (7072 KB). Remember that if the packages are updated, that link might not work.

However you get it, download it to your computer. Now, **for terminal junkies**, open a terminal and move to the folder where you put the file. Then ...

```
tar -xvf iceweasel* -C the_directory_where_you_want_iceweasel_installed
```
If you decide to put it outside your own home directory, remember to use *sudo* before that command. Tar will decompress the package into a folder. Now might be a good time to rename that folder too, if you want it to be easier to type in the future.

**For GUI junkies**, open the file with XArchiver, and tell it to extract the package. :)
[/INDENT]

**Making it the default**

[INDENT]Inside that folder is the iceweasel shell script -- it's called (of all things) "iceweasel." (Not iceweasel-bin. You don't want that one.) The trick now is setting your desktop to open that shell script by default. 

Personally, I'm an Openbox man, so for me it's as easy as opening ObMenu and changing the trigger line to point at the iceweasel shell script.

For Xubuntu or XFCE fans, open Applications > System > Preferred Applications, and select Other. Browse to the iceweasel shell script.

For Gnome, click System > Preferences > Preferred Applications. Change the Web browser option to point at the iceweasel shell script. (Sorry if I'm slightly off the mark on Gnome; I haven't used it in a while. ;) )

For KDE ... well, I'm not very familiar with KDE, and chances are if you're using KDE, you're a Konqueror fan. If someone can chime in on that, I'd appreciate the help. [/INDENT]

One last note: Remember that the "globe icon" on your desktop might or might not trigger your desktop's default browser. In that case, you'll have to change the properties of the icon and redirect it to the iceweasel shell script.

I think that's about it. You can now surf with a clear conscience. :mrgreen: If you like it and decide to stick with it, a quick note of thanks to the folks who made it would be a nice thing to do.

**ADDED: 06/10/05**

If you're having trouble with browser identification -- in other words, sites block your access because you're "not using Firefox" -- try this:

[LIST=1]
[*]Open "about:config" in IceWeasel's address bar.
[*]In the "Filter" box, type **general.useragent.extra.firefox**.
[*]Where you see the word "Iceweasel", right-click and pick "Modify"
[*]Then replace the word "Iceweasel" with "Firefox".
[*]Close the page (or the tab).
[/LIST]
"Masquerading" your browser like that simply prevents the host site from telling you you're not using Firefox. Aside from that, it should have no effect whatsoever on your collective Internet experience. :biggrin: Of course, if it doesn't work, let us know.

Thanks for .deb file I am using it right now.  So is Ubuntu take the same route as Debian and starting using IceWeasel so are they going to stick with Firefox with current icon?

---

### Post by K.Mandla on 2006-10-07
To be honest, I have heard nothing new on the issue. [This article]("http://www.internetnews.com/dev-news/article.php/3636651") suggests Debian developers are teaming up with the Iceweasel crew, and my own stream of logic says if Debian ships a new browser -- whether it's called Iceweasel or Freefox or what have you -- Ubuntu will pick it up. That's just my guess, though.

---

### Post by Kilz on 2006-10-10
I have new versions of iceweasel. 1.5.0.7 avialable.

[i386 ]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.7-ubuntu-i386.deb")

I recommend amd64 users check out my 64bit howto as there are a few other things that need to be done. Just use the Firefox link in my signature.

---

### Post by IusedTObeSOMEONEelse on 2006-10-10
Hi Kilz! I downloaded your link to i386 and when package installer opened I got error message:** This package might be corrupted or you are not allowed to open the file. Check the permissions of the file** What would I do now?

---

### Post by fatsheep on 2006-10-10
Simply pointing the web browser in preferred applications at the iceweasel startup script is not enough.  That will just start up a new Iceweasel window every time you click on a link in an external application like GAIM or Open Office.  You need to change the web browser command to "Iceweasel32 %s".  That way all links opened externally open in Iceweasel and to the correct URL.

Also, I've made a script that will install w/ mplayer, flash, java, and widgets based off Kilz's firefox32 script if you want it (attached below).

---

### Post by beerorkid on 2006-10-10
tee he he

what a cute little fella.

Kinda silly, just like the whole issue.  Me likey and using.

[IMG]http://www.beerorkid.com/wp-content/uploads/2006/10/120px-Iceweasel-icon-mini.png[/IMG]

---

### Post by K.Mandla on 2006-10-10
> **fatsheep said:**
> Simply pointing the web browser in preferred applications at the iceweasel startup script is not enough.  That will just start up a new Iceweasel window every time you click on a link in an external application like GAIM or Open Office.  You need to change the web browser command to "Iceweasel32 %s".  That way all links opened externally open in Iceweasel and to the correct URL.

Also, I've made a script that will install w/ mplayer, flash, java, and widgets based off Kilz's firefox32 script if you want it (attached below).
I don't see an Iceweasel32 file in the 1.5.0.4 or 1.5.0.7 package. Is that something that kilz put into his/her deb? :-k

---

### Post by Kilz on 2006-10-10
> **MustangSallydd said:**
> Hi Kilz! I downloaded your link to i386 and when package installer opened I got error message:** This package might be corrupted or you are not allowed to open the file. Check the permissions of the file** What would I do now?

Im going to upload the file, its possible something got messed up when uploading.
> **K.Mandla said:**
> I don't see an Iceweasel32 file in the 1.5.0.4 or 1.5.0.7 package. Is that something that kilz put into his/her deb? :-k

I made Iceweasel32 the package name for users of the amd64 version of Ubuntu. Signifing that it is a 32bit package in a 64bit system. Just as the 32bit firefox is named firefox32.
It is also the location in a 64bit system of /usr/local/Iceweasel32 where on a i386 its placed in /usr/local/Iceweasel. It's also the name of the startup script in /usr/bin/ for a 64bit user, I know fatsheep runs the 64bit version . :D
Just as a note, Im a him. I also like the firefox logo in this thread and will be using it for the next set of packages.

---

### Post by nuzzy on 2006-10-10
Is there a way to get the Iceweasel icon to replace the blank windows menu icon in the upper left corner of the browser?

---

### Post by nrayever on 2006-10-11
let's try iceweasel. hope that iceweasel 2 comes up! ;) ;)

---

### Post by nrayever on 2006-10-11
> **nuzzy said:**
> Is there a way to get the Iceweasel icon to replace the blank windows menu icon in the upper left corner of the browser?

i'm asking my self the same question as you nuzzy. that icon looks damn ugly!! and iceweasel didn't work when i tries to run it in alt-f2.

is there any way to fix those 2 horrors??? sorry errors....

and another question. firefox extensions work in iceweasel??

nrayever

---

### Post by K.Mandla on 2006-10-11
> **nrayever said:**
> firefox extensions work in iceweasel??
I have yet to run into an extension that didn't work, but I only use about four. 

As far as changing out that corner icon ... I really don't know. I'll keep my eyes peeled. ;)

---

### Post by beerorkid on 2006-10-11
it is stramnge cuz you will get the same errors as you would get from firefox but it says iceweasel.  I think extentions and themes have no clue it is different.

---

### Post by wislon on 2006-10-11
> **K.Mandla said:**
> 
As far as changing out that corner icon ... I really don't know. I'll keep my eyes peeled. ;)

I haven't had much experience in programming linux applications, but from my windows experience, that icon would be based on an internal icon/image resource built into the binary of the application. In other words, in order for it to use that icon, the person doing the development of the package would have to include that as an image resource somewhere within the app. 

Please correct me if I am wrong! But hopefully that answers your question? :)

---

### Post by stateq2 on 2006-10-11
BTW...for those that got used to middle clicking to close a tab like I did...and considering that iceweasel doesn't include this ability...theres an extension for it:
[https://addons.mozilla.org/firefox/260/](https://addons.mozilla.org/firefox/260/)

---

### Post by kalle314 on 2006-10-11
> **wislon said:**
> I haven't had much experience in programming linux applications, but from my windows experience, that icon would be based on an internal icon/image resource built into the binary of the application. In other words, in order for it to use that icon, the person doing the development of the package would have to include that as an image resource somewhere within the app. 

Please correct me if I am wrong! But hopefully that answers your question? :)

In Firefox, the icon can be changed by changing the image file, there is a script somewhere on this forum which does this (restore_mozilla_icons changes the icons to the official mozilla icons).
The window corner icon is a default icon for gnome i think, so it shouldnt be in the iceweasel binary.
Maybe the current code doesn't look for a specific Iceweasel icon though, and just takes the default application icon (just a guess)?

---

### Post by K.Mandla on 2006-10-11
> **wislon said:**
> I haven't had much experience in programming linux applications, but from my windows experience, that icon would be based on an internal icon/image resource built into the binary of the application. In other words, in order for it to use that icon, the person doing the development of the package would have to include that as an image resource somewhere within the app. :)
That's kind of what I suspected. I hadn't the experience or the proof of it, but it seemed logical.

I'm guessing once the Gnuzilla team settles on icons, they'll appear in the corner.

---

### Post by Antipodean on 2006-10-11
> **stateq2 said:**
> BTW...for those that got used to middle clicking to close a tab like I did...and considering that iceweasel doesn't include this ability...theres an extension for it:
[https://addons.mozilla.org/firefox/260/](https://addons.mozilla.org/firefox/260/)

Can also be done without installing an extension.

1. Open Iceweasel
2. In address bar type about:config
3. Locate line: middlemouse.contentLoadURL
4. Double click the line to change from true to false

Or

For those who use a user.js file
```
user_pref("middlemouse.contentLoadURL", false);
```

See [this thread](http://www.ubuntuforums.org/showthread.php?t=260707)

---

### Post by joshua neff on 2006-10-11
Thanks to this (thumbsucking? nah, *useful*!) HOWTO, I downloaded IceWeasel and got it installed. And I'm digging it. It definitely loads up faster than Firefox or Swiftfox.

There's only one problem: Gnash. The "Install Missing Plugin" trick didn't work, I'm guessing because I didn't open IceWeasel as root. I tried opening it as root (*gksudo iceweasel*), but that didn't do anything. I downloaded Gnash, but...which folder should it be in to work in IceWeasel?

---

### Post by fatsheep on 2006-10-11
> **joshua neff said:**
> Thanks to this (thumbsucking? nah, *useful*!) HOWTO, I downloaded IceWeasel and got it installed. And I'm digging it. It definitely loads up faster than Firefox or Swiftfox.

There's only one problem: Gnash. The "Install Missing Plugin" trick didn't work, I'm guessing because I didn't open IceWeasel as root. I tried opening it as root (*gksudo iceweasel*), but that didn't do anything. I downloaded Gnash, but...which folder should it be in to work in IceWeasel?

The gnash install didn't work for me either but the command to run Iceweasel as root would be *gksudo Iceweasel32*.  Note the capitalized "I".

---

### Post by joshua neff on 2006-10-11
> **fatsheep said:**
> The gnash install didn't work for me either but the command to run Iceweasel as root would be *gksudo Iceweasel32*.  Note the capitalized "I".

I just tried that and it still didn't work. Weird.

---

### Post by fatsheep on 2006-10-11
> **joshua neff said:**
> I just tried that and it still didn't work. Weird.

Do you mean that Iceweasel doesn't start up?  Or do you mean that Gnash still won't install?

---

### Post by joshua neff on 2006-10-11
> **fatsheep said:**
> Do you mean that Iceweasel doesn't start up?  Or do you mean that Gnash still won't install?

Sorry. I meant that Iceweasel doesn't start up. I just get another cursor line in the terminal. No error message, just...nothing.

---

### Post by ninjad on 2006-10-11
I ran the script in terminal and after a few minutes it kinda froze at essential-20060501/wnvwinx.dll and it hasnt moved or said anything about finishing.

---

### Post by BLTicklemonster on 2006-10-14
> **Kilz said:**
> I have new versions of iceweasel. 1.5.0.7 avialable.

[i386 ]("http://home.comcast.net/~ubuntu64user/iceweasel-1.5.0.7-ubuntu-i386.deb")

I recommend amd64 users check out my 64bit howto as there are a few other things that need to be done. Just use the Firefox link in my signature.

Thank you. 

Wow, that's one quick little browser!

---

### Post by BLTicklemonster on 2006-10-14
Is there a simple way for all us knuckle draggers to associate all our firefox browser plugins with iceweasel? Can you put it in knuckledraggerlish where we understand? ie:

open terminal, at prompt, type suchandsuch

Please?

---

### Post by K.Mandla on 2006-10-14
> **BLTicklemonster said:**
> Is there a simple way for all us knuckle draggers to associate all our firefox browser plugins with iceweasel? Can you put it in knuckledraggerlish where we understand? 
Did you try stateq2's suggestion above?

[http://www.ubuntuforums.org/showpost.php?p=1589369&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1589369&postcount=2)

I think that's what you're looking for, but let us know if it's not.

---

### Post by joshua neff on 2006-10-14
> **K.Mandla said:**
> Did you try stateq2's suggestion above?

[http://www.ubuntuforums.org/showpost.php?p=1589369&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1589369&postcount=2)

I think that's what you're looking for, but let us know if it's not.

Where exactly do we put that code? (My knowledge of programming is pretty basic.)

---

### Post by BLTicklemonster on 2006-10-14
I did the second one, but where's my add blocker and video grabber? Certainly not at the bottom of my browser. Thanks for posting it, though. What do I do now?

---

### Post by stateq2 on 2006-10-16
> **joshua neff said:**
> Where exactly do we put that code? (My knowledge of programming is pretty basic.)

If you used firefox previously, and installed your plugins globally, you want to put that code into a terminal (Applications->Accessories->Terminal)
```

ln -s /usr/lib/mozilla/plugins ~/.gnuzilla/

```
or
```

ln -s /usr/lib/firefox/plugins ~/.gnuzilla/

```

It basically makes a symobolic link in your Iceweasel directory that points to your firefox plugin directory.  

This is just a temporary solution until plugins actually get installed in the global iceweasel directory, or the global mozilla directory gets added to the iceweasel plugin search path.

---

### Post by stateq2 on 2006-10-16
> **joshua neff said:**
> Thanks to this (thumbsucking? nah, *useful*!) HOWTO, I downloaded IceWeasel and got it installed. And I'm digging it. It definitely loads up faster than Firefox or Swiftfox.

There's only one problem: Gnash. The "Install Missing Plugin" trick didn't work, I'm guessing because I didn't open IceWeasel as root. I tried opening it as root (*gksudo iceweasel*), but that didn't do anything. I downloaded Gnash, but...which folder should it be in to work in IceWeasel?

I know that Iceweasel is designed to support opensource plugins...but I've found that the gnash plugin is not near the quality of the official flash plugin.

---

### Post by BLTicklemonster on 2006-10-16
lol just go here and start downloading. if it won't work, it will say so once you click to install. I have no script and addblock and my weather thingy ma bob now. [https://addons.mozilla.org/](https://addons.mozilla.org/)

---

### Post by cor2y on 2006-10-20
Ice weasel install went ok and linking the defaukt media plugins worked.
.
However man to have to re-install themes and extensions.
Is there anyway to link those already in the default firefox local folder?

Swiftfox alows that i think

Iif theres no other way i guess i'll have to install then remove firefox and its profile no sense in havingtwo folders with the same things in them.

---

### Post by dolphinsonar on 2006-10-20
> **stateq2 said:**
> to add....you can also associate your mozilla plugin directory w/ iceweasel...in the syntax:
```

ln -s /path/to/mozilla/plugins ~/.gnuzilla/

```if you have firefox installed, you can do it w/ this command:
```

ln -s /usr/lib/firefox/plugins ~/.gnuzilla/

```


The second line of code got flash working in Iceweasel for me, which is a HUGE help.  The most amazing part of all is that now flash audio and video are actually IN SYNCH.  Thanks!

---

### Post by joshua neff on 2006-10-21
I don't know why I didn't think to just type that in the terminal. I must have been having a brain freeze. Anyway, I tried both of those lines and they didn't work. But I did do a little jigging and...Flash is now working fine in IceWeasel. So thanks for all of your help everyone.

---

### Post by cor2y on 2006-10-23
Can someone help me figure out why Iceweasel is not staying as either the default webbrowser and the default web browser in Sytem->Preferences->Preferred Applications?
Every time i start it says its not the default webbvrowser i disbled checking in firefox, as for the Preferred Applications it gets reset every reboot to /usr/local/bin/Iceweasel/firefox %s

Which is weird

---

### Post by nuzzy on 2006-10-24
Hi all,

Earlier in this thread I was wondering about replacing the ugly icon in the title bar to the left.  I figured it out:

```
sudo mkdir /usr/local/Iceweasel/chrome/icons
sudo mkdir /usr/local/Iceweasel/chrome/icons/default
sudo cp /usr/share/pixmaps/iceweasel32.png /usr/local/Iceweasel/chrome/icons/default/default.xpm
```

That's it!  It should be there!

---

### Post by glotz on 2006-10-24
Wouldn't a wiki page make much more sense than this thread? Thus anybody could edit it instead of just the original poster (K.Mandla). Threads are good for discussions, wiki pages for instructions.

---

### Post by simianMiscreant on 2006-10-25
I know this might be considered off-topic, but...you guys are where I go for help :-)

I got IceWeasel running on my Dapper box, and I'd like it running on my family's Mac as well, but don't have a clue how to get this done - there's a screenshot on Wikipedia of IceWeasel running on a Mac, but I don't have the slightest idea of what to do with the tarball in OS X. If I'm too far off-topic, feel free to flame, but I'm just hoping someone here has an answer, because I've never been let down in the past.

---

### Post by K.Mandla on 2006-11-01
> **glotz said:**
> Wouldn't a wiki page make much more sense than this thread? Thus anybody could edit it instead of just the original poster (K.Mandla). Threads are good for discussions, wiki pages for instructions.
An excellent idea!

[https://wiki.ubuntu.com/InstallIceweasel](https://wiki.ubuntu.com/InstallIceweasel)

I've amended the OP to direct people to the wiki as well. Thanks glotz! :mrgreen:

---

### Post by BLTicklemonster on 2006-11-01
I put iceweasel on my edgy last night, and when I come here to log in, it acts like normal until the forums load back up, and my user name and password aren't there.

---

### Post by iPirates on 2007-01-24
Hey all - 

I've got Ice weasel up and running, with all the plugins working fine ( thanks to this thread! )

However, there's a little bit of a problem I'm having with starting up more than one Ice weasel browser windows.  It seems that whenever I have an Ice weasel browser window open, and I click on  the short cut to open another, it opens 2 more.  One opens my home page, as it should, and the other just sits in the task bar saying "Starting Iceweasel Web Browser" without actually opening a window.  Then it eventually disappears... it looks like a bug.... 

It's not a big problem, I was just wondering if anybody was experiencing the same problem.

---

### Post by K.Mandla on 2007-01-26
Very strange. I've not seen that happen before. I know if I try to start two Iceweasels (or Firefoxes, for that matter) too quickly I get that behavior, but not if I have one already running.

---

### Post by iPirates on 2007-01-26
I know... Like I said, it's not really a big deal, the browser functions perfectly, and I usually only have one browser open at a time....
I'm going to try re-installing Iceweasel, to see if that miraculously fixes my problem..

---

### Post by quixotic-cynic on 2007-09-02
Edit: Problem mysteriously resolved itself.

---

### Post by ubu-for on 2008-01-04
I would like to install a current version of Iceweasel, but I can't find anything. Does the project still exist?

---

### Post by K.Mandla on 2008-01-04
:D It's hard to follow this stuff any more. It looks like IceWeasel became IceCat, because there was already an IceWeasel even before Gnuzilla took it up. 

[http://en.wikipedia.org/wiki/GNU_IceCat](http://en.wikipedia.org/wiki/GNU_IceCat)
[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

You should be able to find similar packages on the Gnuzilla site.

---

### Post by ubu-for on 2008-01-05
After a search of 3 days I've found a [source for the current Iceweasel](http://packages.debian.org/sid/iceweasel/i386/download) and hope they keep the old name and logo.

---

