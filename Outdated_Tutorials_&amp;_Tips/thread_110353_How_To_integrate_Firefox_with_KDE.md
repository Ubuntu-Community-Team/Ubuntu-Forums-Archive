---
title: "How To: integrate Firefox with KDE"
date: 2005-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by NeoChaosX on 2005-12-30
[CENTER][SIZE=4]For Edgy please go [here]("http://ubuntuforums.org/showthread.php?t=327828")![/SIZE]
[/CENTER]

As fan of Firefox, and a user of Kubuntu, I'm sort of disappointed how GNOME-centric Firefox is in Linux (i.e., the GTK file dialogs). However, I've found several steps that allow one to better integrate everyone's favorite open-source browser with KDE.

**Step 1: Replace the GTK file dialogs with the built-in dialogs**
Go to the component directory in the folder Firefox is installed to (if you have the Ubuntu Firefox package installed,  it's /usr/lib/mozilla-firefox/component) and open up the **nsFilePicker.js** file with your favorite text editor. Now, find this set of lines:

```
compMgr.registerFactoryLocation(FILEPICKER_CID,
                                    "FilePicker JS Component",
// *really long comment here*
                                    "",
// *really long comment here*
                                    fileSpec,
                                    location,
                                    type);
``` and change it so it looks like this:
```
compMgr.registerFactoryLocation(FILEPICKER_CID,
                                    "FilePicker JS Component",
// *really long comment here*
                                    FILEPICKER_CONTRACTID,
// *really long comment here*
                                    fileSpec,
                                    location,
                                    type);
```To make this change take effect, you need to reset Firefox's chrome registry, which you can do by installing or disabling an extension, then restarting Firefox. Now, when you need to open or save a file, it should come up with the following dialog, rather than the default GTK file dialogs:
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=4957&stc=1&d=1135976302[/IMG]


**Step 2: Install a matching Firefox theme**
This one's a little more tricky. [Mozillux]("http://www.polinux.upv.es/mozilla/") has a few KDE themes for Firefox, but they are locked to the default KDE colors of  white and blue and the Plastik look and feel, while the default Firefox theme (assuming you have GTK apps take on the QT feel) will look like whatever KDE theme you use.

Luckily, a user on KDE-Look.org recently uploaded a version of the Firefox default theme that replaces some of the stock icons with icons from the KDE default iconset Crystal SVG. I took this theme, and tinkered a bit more with it some more so that just about all the icons (save for a few that don't have comparable equivalents in Crystal SVG) and have uploaded it here.

[Download the CrystalDefault theme for Firefox]("http://www.ubuntuforums.org/attachment.php?attachmentid=5296&d=1137196572"). Untar the file, then load the jar theme file it produces into Firefox, and apply the theme to the program. Feel free to replace the images in the theme with whatever KDE iconset you use if you want.

Voila, you have a Firefox that looks a little bit more like a native KDE app.

---

### Post by jamuir on 2006-02-06
THANK-YOU FOR THIS INFO!  

I have been frustrated with the gnome file dialogue for some time now.  I could never understand why it appeared in Firefox; I have always used KDE a la kubuntu.

You have restored peace and order to my browsing experience.:D 

-j

---

### Post by dejitarob on 2006-02-06
Thanks for the nice guide! This works for the "Open with" dialog as well so now you can just type in the path of the app you want to use instead of being forced to browse to it with the silly GTK dialog. 

[Here]("http://www.kde-look.org/content/show.php?content=11442") is the matching theme for the default Plastik theme in Kubuntu. Get the 2.0 alpha version for Firefox 1.5. To install, untar the contents and drag the install.html to Firefox's address bar. It will also give the option of switching the button order to how they normally are ordered ('OK' first instead of last) in other KDE/Kubuntu apps.

*Edit*: Thanks to the advice of Sokraates I fixed the Plastik theme to work with the latest 1.5.0.1 version of Firefox. [Here]("http://plaza.ufl.edu/rheck/firefox/plastikfox-crystalsvg-2.0alpha_fixed.tar.bz2") is the fixed version.

---

### Post by Parkotron on 2006-02-07
Excellent work! Thank you. I'm really surprised that I'd never seen this before, but it certainly makes life easier.

---

### Post by darknightuk on 2006-02-07
thanx:KS

---

### Post by cutOff on 2006-02-07
No matter IMHO ;)

Gnome rulezz.

---

### Post by cwf on 2006-02-08
Thanks for the howto.  I need clarification on this part:

Download the CrystalDefault theme for Firefox. Untar the file, **then load the jar theme file it produces into Firefox, and apply the theme to the program**.

How do I load the jar them into Firefox?

---

### Post by Sokraates on 2006-02-08
@ dejitarob:
Since FF 1.5.0.1 didn't introduce any UI-changes, one simply needs to change the theme's version-compatibility in the RDF-file. It's a bit of a hassle, though, so I suggest using [Nightly Tester Tools]("http://users.blueprintit.co.uk/%7Edave/web/firefox/buildid/nightly.html") to up the theme's version (use the button "make compatible"). Afterward you can remove the extension.

@ cwf:
Simply drag-and-drop the JAR-file onto the theme-manager. Alternatively browse to the file using the theme-manager and select "open".

---

### Post by dejitarob on 2006-02-09
Thanks Sokraates. It was really easy, I just edited the install.rdf files and imported them back into the .jar files. [Here]("http://plaza.ufl.edu/rheck/firefox/plastikfox-crystalsvg-2.0alpha_fixed.tar.bz2") is the fixed version, working with the latest Firefox 1.5.0.1 version.

---

### Post by goombah88 on 2006-02-09
hey dejitarob, when we click your link it asks for a username and password.

---

### Post by dejitarob on 2006-02-10
Wups, fixed it. Thanks for pointing out that I used the ftp instead of http link. I also uploaded it to [kde-look.org]("http://www.kde-look.org/content/show.php?content=35055").

---

### Post by cwf on 2006-02-11
This may be a little off topic...

Any idea how to do this with other apps?  Like Azureus...want to integrate that into KDE...so the file manager is KDEish and not Gnomeish.

---

### Post by jago25_98 on 2006-05-03
is there any effort to bring Mozilla/Firefox to kde so that the meny bar can be put to the top of the screen etc?

Is it going to be gnome/gtk forever because the Firefox guys don't like kde?

---

### Post by El Menda on 2006-05-04
Wow this is awesome! Look at my new Firefox:

---

### Post by Ensnared on 2006-05-04
This is nice, but I'm having a very hard time with the Firefox fonts. I've managed to get the UI fonts fairly much the way the rest of my KDE setup is, but the fonts on websites is way out of whack.

Input-boxes especially are way too huge, but there are also other elements, while some text is the size it should be (e.g. the size it is in Windows and if using Gnome).

If someone writes a guide to fix this stuff that would be great, but I'm beginning to wonder if it's at all possible.

---

### Post by acidphex on 2006-05-10
Suprisingly this didn't work for me...

---

### Post by dejitarob on 2006-05-10
[QUOTE=acidphex]Suprisingly this didn't work for me...[/QUOTE]Please be more specific. Did you get any error messages? What part did you get stuck on?

---

### Post by barbarian on 2006-05-10
Yep, it works perfectly, now my fox wears Bagira theme:-D

---

### Post by evilhomer on 2006-05-11
excellent, works great.  anybody know of a way to change the print dialog?  a kde one would allow us to easily print to pdf :)

---

### Post by hpv on 2006-05-17
Does anyone know if there is a way to make the builtin file dialog use single click instead of double for navigating directories?

---

### Post by cesera on 2006-05-17
[QUOTE=acidphex]Suprisingly this didn't work for me...[/QUOTE]

I had the same problem, and then realised that I had put the FILEPICKER_CONTRACTID in quotes, you haven't done the same thing by any chance?

---

### Post by cesera on 2006-05-17
This is great, thank you very much, and it works for thunderbird as well (of course).

---

### Post by K2712 on 2006-05-17
For some reason, editing my nsFilePicker.js did not change my open file menus.  I tried it on my Arch box and it worked fine, so I copied the file to my Kubuntu box, replaced the present file, and tried again, and still nothing.  Any idea why?

---

### Post by rmn30 on 2006-05-19
I'm thinking of integrating this and a few other changes into a firefox-kde-support package which can be installed via synaptic.

Check out my bug report here:

[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/43238](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/43238)

I won't have any time to work on it till after exams (June) but I think it has the potential to make firefox much more usable for us kde folks!

Robert

---

### Post by evilhomer on 2006-06-07
Figured out how to get the KDE print dialog box in Firefox!  So now we can print directly to pdf :)

Go to about:config

change the string print.postscript.print_command to:
kprinter

then when you you go to print, select Postscript/default and you'll be given a KDE print dialog box!

note: I also changed print.print_command to kprinter when I was experimenting.  I don't *think* you need it, but I'm now unable to change it back to tell for sure.

---

### Post by arizonagroovejet on 2006-06-08
You can get Firefox, and some other GTK based apps to use the proper KDE file dialogs with this -
[http://www.kde-apps.org/content/show.php?content=36077](http://www.kde-apps.org/content/show.php?content=36077)

Just tried it out on Dapper and it works. To get it to compile you need to install gcc, g++. Also the dev packages for kde gtk and xorg and a bunch of other stuff. I'm wishing I wrote them down as I installed them now.
You need to use
```

./configure --prefix=/usr
```

if you don't specify the prefix it won't work.

---

### Post by msak007 on 2006-06-25
[QUOTE=evilhomer]Figured out how to get the KDE print dialog box in Firefox!  So now we can print directly to pdf :)

Go to about:config

change the string print.postscript.print_command to:
kprinter

then when you you go to print, select Postscript/default and you'll be given a KDE print dialog box!

note: I also changed print.print_command to kprinter when I was experimenting.  I don't *think* you need it, but I'm now unable to change it back to tell for sure.[/QUOTE]

I was going to suggest this, but will go 1 step further so that it'll be seamless and you won't have to select "PostScript/default" to bring up the kprinter dialog. As you've mentioned, change the value of 

```
print.postscript.print_command
``` 

to [COLOR="Red"]kprinter[/COLOR]. This will like you said force FireFox to use the kprinter dialog when choosing PostScript/default as the printer. Next, you need to add 2 lines that aren't there by default. Right-click in about:config and choose New --> Boolean. Add the following line:```


print.always_print_silent
```

and set its value to "[COLOR="Red"]true[/COLOR]". This will force FireFox to print to the default printer without prompting you. If PostScript/default is the only printer you have and no local / network printers, it works. But if you install a local printer through CUPS, FireFox will want to use that as a default and all the prints will go there without prompting you! So regardless of whether or not you do have a local printer, it's a good idea to add the following line in case you add one later. Once again add another line, and also make it a Boolean:

```
print.postscript.cups.enabled
```

and set its value to "[COLOR="Red"]false[/COLOR]". That way if you do have a CUPS printer, it won't be detected and FireFox will default to PostScript/default. And since you've changed the output of that to kprinter, you'll see a "processing" dialog for a split second when you print, after which kprinter will open up. There you can choose all your printers, including your CUPS installed printers :). Hope that helps a lot of people out, I almost pulled all my hair trying to figure it out.

---

### Post by groove on 2006-06-25
DONE! Thank you!
&#35874;&#35874;

---

### Post by asimaythink on 2006-08-08
Works like a charme. Thank you for this How To!

---

### Post by Psquared on 2006-08-11
So does this explain why some of the themes available for Firefox cause it to crash in KDE? I found it the hard way, but I've been unable to figure out which theme (or possibly an extension) caused it.

---

### Post by Ali_Taimur on 2006-08-11
Thank you so much. I was looking for this for a while

---

### Post by dalco on 2006-08-31
There is an easier way to get the XUL File Picker, that doesn't involve to edit file (so you could update Firefox quickly and without problems):
[LIST=1]
[*]Insert *about:config* in the address bar of Firefox and hit Enter
[*]Insert *ui.allow_platform_file_picker* in the filter bar and hit Enter or wait a moment
[*]The window will show only the above property (*ui.allow_platform_file_picker*): double-click the item to change its value to *false*
[/LIST]
All is done! The new file picker is immediately available. No need to restart Firefox nor Activate/Deactivate any estension.

Bye,
Michele

---

### Post by msak007 on 2006-08-31
> **dalco said:**
> There is an easier way to get the XUL File Picker, that doesn't involve to edit file (so you could update Firefox quickly and without problems):[LIST=1]
[*]Insert *about:config* in the address bar of Firefox and hit Enter
[*]Insert *ui.allow_platform_file_picker* in the filter bar and hit Enter or wait a moment
[*]The window will show only the above property (*ui.allow_platform_file_picker*): double-click the item to change its value to *false*[/LIST]All is done! The new file picker is immediately available. No need to restart Firefox nor Activate/Deactivate any estension.

Bye,
Michele

This entry is not there by default. You should probably include in the instructions that this will be a Boolean value if you need to create it. I deduced that from the "set it to false", but you need to know what type of string this will be before you create it. Anyway, I just tried this and it doesn't work for me, still get the ugly GTK file picker. I even tried disabling / re-enabling an extension and restarting (even though you said you don't have to) and it still doesn't work. Do you have a screenshot of this working for you?

---

### Post by nixternal on 2006-09-01
msak007, i believe you and I are in the same boat. Are you using Edgy and/or Firefox 2 Bon Echo Beta 1?

This hack doesn't work with Edgy and/or Firefox 2. Any other ideas? I have been doing this hack for a year or so, and now Firefox changes up. The nsFilePicker file is exactly the same as well, however I still get that nasty GTK box.

Any ideas?

---

### Post by msak007 on 2006-09-01
> **nixternal said:**
> msak007, i believe you and I are in the same boat. Are you using Edgy and/or Firefox 2 Bon Echo Beta 1?
 
I'm still on Dapper, using Firefox 1.5.0.6 (downloaded from Mozilla's site, not the repo version). I initially tried the method in this thread, and it worked OK (no more ugly GTK menus). Then I saw Mozillux's modified nsFilePicker.js [here]("http://www.kde-look.org/content/show.php?content=13967"), which uses KDE's native file picker (or at least looks like it), so I tried that. It looks better, more integrated with KDE, but it's a crude hack and after saving something once the "Save As" dialog stops coming up unless you restart Firefox (and the "Preview" function / F11 is disabled). So I revereted to a backed up (unmodified) version of nsFilePicker.js, added the Boolean as suggested ([here's]("http://kb.mozillazine.org/Ui.allow_platform_file_picker") the MozillaZine on it) and set its value to "false", but it doesn't change at all. I'm also out of ideas.

---

### Post by linuxpenguin on 2007-03-18
Anyone know how to get it to use KDE's scrollbar?  I like the KDE scrollbar (the way I have it set up) better.

---

### Post by TheWizzard on 2007-04-21
what do you think of this: 
[http://konquefox.free.fr/](http://konquefox.free.fr/)

i think it's exacly what we're looking for ;)

---

### Post by Sokraates on 2007-04-24
> **TheWizzard said:**
> what do you think of this: 
[http://konquefox.free.fr/](http://konquefox.free.fr/)

i think it's exacly what we're looking for ;)

It's not a bad idea, though I haven't missed those buttons. The tricks to make FF look more native are more important, IMO.

---

### Post by L_V on 2007-07-29
If not already said, you should also investigate **gtk-qt-engine** .

---

### Post by TheWizzard on 2007-07-29
> **L_V said:**
> If not already said, you should also investigate **gtk-qt-engine** .

this is installed and activated by default in kubuntu

---

### Post by Kalinda on 2007-07-29
Oh, it's lovely you can integrate! Although.. I do wonder..

Is there any way to produce the newer KDE dialogs, like this one?
[img]http://ubuntuforums.org/attachment.php?attachmentid=39297&stc=1&d=1185738802[/img]

I don't much like the GTK ones, but they have that nifty little panel on the side where you can have a list of locations.. the above KDE dialog has that, too, but with it you can also change your view to see images and thumbnails and whatnot. The ability to add locations to that panel is one of the coolest things, I always thought it'd be lovely if I could do that whilst using Windows.

I know some other programs (like aMSN Messenger) have KDE integration that uses that dialog... so does anybody know a way to use it in Firefox?

I did find a utility that let me do it.. but it would always crash Firefox whenever I saved anything.

Thanks!

---

### Post by Naatan on 2007-10-13
Thanks a lot man! This totally helped me out :) The GTK interface was bugging the hell out of me..

---

### Post by msak007 on 2007-10-14
> **Kalinda said:**
> Oh, it's lovely you can integrate! Although.. I do wonder..

Is there any way to produce the newer KDE dialogs, like this one?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=39297&stc=1&d=1185738802[/IMG]

I don't much like the GTK ones, but they have that nifty little panel on the side where you can have a list of locations.. the above KDE dialog has that, too, but with it you can also change your view to see images and thumbnails and whatnot. The ability to add locations to that panel is one of the coolest things, I always thought it'd be lovely if I could do that whilst using Windows.

I know some other programs (like aMSN Messenger) have KDE integration that uses that dialog... so does anybody know a way to use it in Firefox?

I did find a utility that let me do it.. but it would always crash Firefox whenever I saved anything.

Thanks!
Don't hold your breath. Firefox has always been a GTK app and will probably always be that way, and they don't do any work with Qt. Firefox 3 won't have much integration in the way of a unified theme / look for Linux in general, let alone KDE. I would suggest reading the following article:

[http://blog.mozilla.com/faaborg/2007/10/10/the-firefox-3-visual-refresh-system-integration/](http://blog.mozilla.com/faaborg/2007/10/10/the-firefox-3-visual-refresh-system-integration/)

That article came out a couple days ago and talks about Firefox 3's visual refresh and integration with Vista and OSX, but completely left out Linux which caused an uproar (read the comments). The article was later edited and this part was added:

> [**Update**: *I made the unfortunate mistake of not mentioning Linux when first posting because we still aren’t sure what the best way to visually integrate with Linux is, given the number of different distributions. Mozilla’s lead Firefox engineer Mike Connor and our user experience lead Mike Beltzner have both written **[followup]("http://steelgryphon.com/blog/?p=108")**[posts]("http://www.beltzner.ca/mike/archives/2007/10/11/giving_the_penguin_a_makeover.html")** about this.  Some links to how you can join the discussion about visual integration on Linux appear below*].These are the 2 links in that part of the article:

[http://steelgryphon.com/blog/?p=108](http://steelgryphon.com/blog/?p=108)

The most notable part of that article for me was the following line at the beginning:> 
We’ve had really good native appearance  and drawing hooks for GTK2 (Qt doesn’t get much love, but we’ve asked/begged/pleaded for interest, and no one really seems to have it, including the distros that invest time into Firefox).I'm not sure who they asked, but it'd be nice if there was Qt work done so we could have native integration into KDE. 

And here's the 2nd article, talking about why a unified theme for even GTK in general is tough:

[http://www.beltzner.ca/mike/archives/2007/10/11/giving_the_penguin_a_makeover.html](http://www.beltzner.ca/mike/archives/2007/10/11/giving_the_penguin_a_makeover.html)

My point is that you won't see anything KDE specific for a long time, if ever, coming directly from Mozilla. Unless people step up (I'm not a coder so I can't help) and offer their help, all we'll get is some hacks here and there to make it look more KDE like (sans the functionality of an actual KDE / Qt interface).

---

### Post by Flare183 on 2008-02-29
I am create KDEFox for KDE. But I need some help. I need help with switching the GTK Libraries to KDE Libraries.

---

