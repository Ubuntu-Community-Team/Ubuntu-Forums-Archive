---
title: "HOWTO: Embed PDFs with Evince in Mozilla/Firefox"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by saik0 on 2005-04-10
Evince is a GTK+ PDF and PS viewer to replace gpdf/xpdf/acroread and ggv, and it's open source (woohoo). Using mozplugger you can embed all sorts of stuff into Mozilla and/or Firefox like media players and openoffice. There is another HOWTO on how to embed totem here in this forum at [http://www.ubuntuforums.org/showthread.php?t=17727](http://www.ubuntuforums.org/showthread.php?t=17727)

First make sure you have Evince and mozplugger installed (duh). Both of them are in the Hoary universe repositories. I assume you know how to do that...

Now open up /etc/mozpluggerrc in your favorite text editor with superuser priveleges. Here's how to do it with gedit:
```
sudo gedit /etc/mozpluggerrc
``` 

Wherever you see this:
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file

and

application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file

add this on the next line:
```
	repeat noisy swallow(evince) fill: evince "$file"
``` 

Thats it! You dont even have to restart your browser. Enjoy.

---

### Post by saik0 on 2005-04-10
Here is a screenshot, of Adobe's official manual of Adobe Reader, in what else but PDF format. I thought that was pretty hilarious.

---

### Post by dabeej on 2005-04-10
Anyone tried using the Acrobat Reader 7.0 for linux in firefox?

---

### Post by saik0 on 2005-04-10
> Anyone tried using the Acrobat Reader 7.0 for linux in firefox? 

The acroread package in the Marillat repo works fine. This guide will tell you how to add it [[http://www.ubuntulinux.org/wiki/RestrictedFormats]](http://www.ubuntulinux.org/wiki/RestrictedFormats])

If you really wanna use Adobe Reader 7 just install acroread and mozilla-acroread and you'll be in business. I really gotta recommend Evince, it has the ability to search unlike gpdf, and it uses GTK widgets, acroread looked pretty ugly. Acroread is noticably faster on rendering thumbails on some larger PDFS (lots of vector graphics slowed it down a bit for me) but overall I liked Evince better. Hope that helps =)

---

### Post by dabeej on 2005-04-11
Yes, it did. Thanks a LOT!  :grin:

---

### Post by jonny on 2005-04-11
This works with Epiphany, too  :grin: .  Personally, I prefer Epiphany to Firefox, as it's quicker to start and maintains a more consistent Gnome desktop look and feel.

---

### Post by bored2k on 2005-04-11
[QUOTE=jonny]This works with Epiphany, too  :grin: .  Personally, I prefer Epiphany to Firefox, as it's quicker to start and maintains a more consistent Gnome desktop look and feel.[/QUOTE]
 If epiphany/galeon would be able to use firefox's plugins, I would love it. Adblock and all those extensions are just too good to be left unused.

---

### Post by dejitarob on 2005-04-13
For some reason evince was removed from the ubuntu repositories. In the meantime, it is available from [debian's](http://packages.debian.org/testing/gnome/evince). You will also need an updated [libfontconfig1](http://packages.debian.org/testing/libs/libfontconfig1).

---

### Post by Nis on 2005-04-13
[QUOTE=bored2k]If epiphany/galeon would be able to use firefox's plugins, I would love it. Adblock and all those extensions are just too good to be left unused.[/QUOTE]
 Just wait until Epiphany with its own Adblock extension hits Breezy. :)

---

### Post by merlyn on 2005-04-14
Outstanding!

I for one prefer things this way, not having multiple windows open all the time.

Now if anybody out there knows how to do this with Nautilus as well, that would be cool.

Cheers.

---

### Post by veritas366 on 2005-04-23
Anyone know how to get around the mozilla acroread plugin wanting to uninstall mozplugger?  I just spent two hours getting mozplugger to play embedded videos with xine (mplayer has never worked for me.) so I don't want to lose mozplugger.  I wish firefox had a feature where you simply associate file types...but they don't.  So how can I open pdf's  I have xpdf and gpdf (or is it gxpdf) and I have acroreader.  Anyone know how to edit mozplugger to make the association? Don't care which reader.  Thanks.

---

### Post by tlepes on 2005-04-23
[QUOTE=saik0]The acroread package in the Marillat repo works fine. This guide will tell you how to add it [[http://www.ubuntulinux.org/wiki/RestrictedFormats]](http://www.ubuntulinux.org/wiki/RestrictedFormats])

If you really wanna use Adobe Reader 7 just install acroread and mozilla-acroread and you'll be in business. I really gotta recommend Evince, it has the ability to search unlike gpdf, and it uses GTK widgets, acroread looked pretty ugly. Acroread is noticably faster on rendering thumbails on some larger PDFS (lots of vector graphics slowed it down a bit for me) but overall I liked Evince better. Hope that helps =)[/QUOTE]

Here is one very good reason to avoid the official Adobe Acrobat PDF reader and plug-in...
[INDENT]
[http://helping.net/p2p/AdobeAcrobatSpyingonUsers.html](http://helping.net/p2p/AdobeAcrobatSpyingonUsers.html)

***Grrrr....!!!!!@##@$^%$#*!!!!!!***[/INDENT]

To reiterate what the author said, "[COLOR=DarkRed]Again, you can't trust software that is not open source.[/COLOR]"

Peace!
Tim

---

### Post by Gandalf on 2005-05-02
thanks for this nice HOWTO

---

### Post by veritas366 on 2005-05-02
I answered my own question by accident.  I removed all pdf references in Mozplugger.  I tried to add an entry for evince but I'm sure I got the syntax wrong.  However, the first time mozilla wanted to open a pdf, it simply asked me what program to use.  I chose evnice and didn't have to worry about it after that.

And evince is quite nice...slow if there are lots of thumbnails...but very nice viewer.

---

### Post by darkmatter on 2005-07-19
Works nicely. The only problem i have is the annoying (though brief) flash of the Evince window just as it is getting embedded. Does anyone no a way to fix this?

---

### Post by rwabel on 2005-07-30
nice howto, is it possible to have it asked to open or save. In the case of open it opens in the browser.

---

### Post by moxfyre on 2005-12-06
> Thats it! You dont even have to restart your browser. Enjoy.

A great tip, saik0!  I now have PDF viewing in firefox, and am a happy camper :D 

Only one thing to add.  From the mozplugger man page (my addition in bold):
> 
       You  have to remove ~/.netscape/plugin-list or ~/.mozilla/pluginreg.dat **or ~/.mozilla/firefox/pluginreg.dat**
       after changing the configuration, or nothing will  happen.  This  is  a
       Netscape/Mozilla bug, not a MozPlugger bug.


I had this problem!  After I installed mozplugger and tweaked its configuration file, NOTHING worked.  I had to delete my pluginreg.dat files, and then everything worked perfectly.

---

### Post by bradroger on 2005-12-14
This doesn't work for me.  I'm using firefox 1.5...upgraded using the tutorial from these forums.  At first it said I was missing a plugin and tried to install acroread.  Then I tried renaming the ~/.mozilla/firefox/pluginreg.dat file but then pdf's just gave me a prompt asking me for what program to use and opened in a new window.  For now I've reinstalled acroread and it opens embedded again.

---

### Post by art on 2005-12-23
you need to do 

 sudo cp /usr/lib/mozilla/plugins/mozplugger.so /opt/firefox/plugins/

and then it should work... Works for me...

---

### Post by kperkins on 2005-12-29
[QUOTE=tlepes]Here is one very good reason to avoid the official Adobe Acrobat PDF reader and plug-in...
[INDENT]
[http://helping.net/p2p/AdobeAcrobatSpyingonUsers.html](http://helping.net/p2p/AdobeAcrobatSpyingonUsers.html)

***Grrrr....!!!!!@##@$^%$#*!!!!!!***[/INDENT]

To reiterate what the author said, "[COLOR=DarkRed]Again, you can't trust software that is not open source.[/COLOR]"

Peace!
Tim[/QUOTE]
While this is true, the acroread in Breezy (multiverse) has the plugin that lets it do that separated from the acroread program itself, and is a separate install. (Why anyone would want to install it is beyond me, but there it is.

---

### Post by FISHERMAN on 2006-04-02
I've done everything that is said here but when I try to open a PDF(with MozPlugger-Embedded Evince), I get the following warning:
Could not launch adobe Reader 7.0. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.
How can I make it clear to MozPlugger that he has to use Evince.
I have tried everything(I've already deleted Acrobat)?

---

### Post by eeried on 2006-05-05
Hello,

Unfortumately I installed Xpdf too so my mozpluggerc file is a bit messy:
This is what I have:

```
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
	repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"
```

and

```
application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file
	repeat noisy swallow(gv) fill: gv --safer --quiet --antialias -geometry +9000+9000 "$file"
	repeat swallow(Pageview) fill: pageview "$file"
```

Which lines should I replace with the evince line?

Many thanks in advance for your help.

---

### Post by leandir on 2006-06-27
Hi, I am new here and I am no expert, but I happened to have your same problem...I got it solved deleting all the old sentences (pardon my language, I am no informatic :) ) but one, specifically my file now has written:

application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
	repeat noisy swallow(evince) fill: evince "$file"
	repeat swallow(documentShell) fill: acroread -geometry +9000+9000 +useFrontEndProgram "$file"

and 

application/x-postscript: ps: PostScript file
application/postscript: ps: PostScript file
	repeat noisy swallow(evince) fill: evince "$file"  

As far as I know it runs smoothly, although I admit I do not know exactly what I have done...just cut and pasted 'till I got it right. If someone more expert than me could check it and tell me that I have not cracked mozplugger, I would be grateful :p

---

### Post by weizenbier on 2006-10-15
Hi to all,

thanks once again to saik0 for the tip.

I was wondering why this behavior is not the default for any future ubuntu release. 
I think most of the time users like to see a PDF document right away rather than having the ususal dialog where to choose to download or to see the file.

Any opinions on that?

Bye,

weizenbier

---

### Post by hiruzzolo on 2007-05-28
I agree with the last post.. It would be very user friendly and not too difficult too, I think..

---

### Post by crhumber on 2007-08-12
I'm running firefox32 on 64 bit Feisty and this didn't work for me.  Has anyone been successful in getting PDFs embedded in firefox32?  Maybe this works, but is there something I should have to do differently?

---

### Post by crhumber on 2007-08-14
I fixed the problem in case anyone else runs into this.  I had installed the 64 bit mozplugger package, but I had to download the 32 bit package and install it using the --force-architecture tag, then I had to move the file mozplugger.so to /usr/lib32/firefox32/plugins.

---

### Post by kehan on 2007-08-23
This thread has gone a bit cold - it's even better now:
```
sudo apt-get install mozplugger
```
It now comes prerolled with the correct evince associations.

---

### Post by utopial on 2007-12-18
i just upgraded to 7.1 gutsy and it replaced my mozplugger file. neither before nor now can i open certain embedded pdfs, such as pdfs embedded in bank account pages

```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
	repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
	repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	GV()



application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
	GV()
	repeat noisy swallow(evince) fill: evince "$file"

```

---

### Post by contents on 2008-01-16
> **FISHERMAN said:**
> I've done everything that is said here but when I try to open a PDF(with MozPlugger-Embedded Evince), I get the following warning:
Could not launch adobe Reader 7.0. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.
How can I make it clear to MozPlugger that he has to use Evince.
I have tried everything(I've already deleted Acrobat)?

Though your message was posted almost two years ago, I thought I'd reply because I had the exact same problem and just figured out how to fix it. I, too, had uninstalled Acrobat Reader, but was still getting a message from firefox that it couldn't open .pdf files because Acrobat Reader wasn't there--in spite of the fact that I had evince and mozplugger installed and modified /etc/mozpluggerrc as suggested. 

It turns out that Acrobat had left a plugin called nppdf.so which was causing the problem. I was able to confirm that by typing "about:plugins" in the firefox address bar, and seeing that Adobe Acrobat was listed as the first plugin. I then did a search on my hard drive for the plugin, which is called nppdf.so, and found two instances and removed them both. I then restarted firefox, and found that I was able to open .pdf files accessed through firefox in evince normally.

I hope others might find this useful.

---

### Post by megamania on 2008-01-17
On my 7.10 install, it works by just installing mozplugger
 as somebody said above (sorry, forgot the nickname).

There's a weird problem, though. When firefox opens a PDF document, I keep seeing the "loading..." watermark and nothing else until I resize the window. ANY resize will make the pdf document magically appear.

Any ideas?

---

### Post by breity on 2008-02-05
hmm, strange.  i have the same issue too -pdf won't show until the page is resized.  anyone with ideas?

thanks for pointing it out, though, as i just thought the plugin wasn't working!

> **megamania said:**
> On my 7.10 install, it works by just installing mozplugger
 as somebody said above (sorry, forgot the nickname).

There's a weird problem, though. When firefox opens a PDF document, I keep seeing the "loading..." watermark and nothing else until I resize the window. ANY resize will make the pdf document magically appear.

Any ideas?

---

### Post by Oilarrak on 2008-04-08
I have the same problem. Looking for an answer, I read ([http://www.ubuntu-es.org/index.php?q=node/77426](http://www.ubuntu-es.org/index.php?q=node/77426))  that deleting directories 

~/.config/evince
~/.gnome2/evince

did the trick.
In my system (32 bits), I had no ~/.config/evince directory but only the other one, so I renamed it (I am a bit scared of deleting things in a rush) and seemed to work. However, in my hands it only worked the first time. Second time around, I went back to "loading" screen. If you delete the "ev-metadata.xml" file in ~/.gnome2/evince you get the same result as deleting the whole directory. This file gets created everytime evince is launched (either from within Firefox or on its own).  Now, how this translates into a working solution, I am not sure. Somebody more knowledgeable might help further.

I hope it helps getting nearer.

Cheers,

O.

---

### Post by hpalma on 2008-04-09
I'm using Hardy with Firefox 3 Beta 5.
I installed mozplugger and it worked fine without any additional configuration except for one annoying thing.

The first PDF i open shows up just fine in a new tab, if i open a second document while the other is still open instead of it opening on a new tab i get an evince window in some weird mode that's not quite full screen but very close.

Any ideas ?

---

### Post by w_m0zart on 2008-06-30
A solution for the problem where only the first pdf is placed correctly in a tab page is to use another viewer for pdf files than evince.

According to this thread:
[https://bugs.launchpad.net/ubuntu/+source/mozplugger/+bug/46017](https://bugs.launchpad.net/ubuntu/+source/mozplugger/+bug/46017)
there is a bug in Evince, which causes this.

To use another viewer for pdf files, edit your mozpluggerrc file:
```
sudo gedit /etc/mozpluggerrc
```
Make sure the corresponding pdf part is something like:
```
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
#	repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
#	repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
#	repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
	GV()
```
Evince, acroread5, acroread7 are disabled by commenting these lines. Because kpdf is not installed, this line is simply ignored.

---

### Post by macabro22 on 2008-08-21
ah. I can't get it to work.
Darn.

---

### Post by emperortux on 2008-09-20
nothing happens when i click on a pdf link...
I've tried many different combos of code, but nothing happens..

---

### Post by tachyian on 2009-03-18
Hi, I have two computers, one laptop and one desktop, and both are running on Hardy(AMD64).
I installed "mozplugger" using apt-get for both.
The firefox(64bit version) in the laptop works perfectly with mozplugger embedding a pdf file in the same firefox window.
But, the firefox in the desktop always opens a pdf file not in the same window, but in a new window,
which is not a firefox window but an application(e.g. evince or acroread) window defined in /etc/mozpluggerrc.
I've tried both evince and acroread by editing /etc/mozpluggerrc following this howto and there's no difference,
so I think the problem is not about the application linked to mozplugger, but something else.
Anyway, the weird thing is that despite the fact that I've followed the same procedure for both systems,
only one is working perfectly (and it's very annoying).
How can I fix it? Or what kind of configuration files should I check?

P.S.: I forgot to say "Thank You!" to saikO.

---

### Post by nortexoid on 2009-04-25
This is awesome. Worked just fine by installing mozplugger in Jaunty. At first I thought mozplugger wasn't working since I was trying to access pdfs via google scholar which pompts a "choose program" dialog box. I had to go to other sites to find out that it actually works.

---

### Post by Kareeser on 2009-08-12
Still works great in Karmic. It's too bad it's not installed by default, however...

---

### Post by bornagainpenguin on 2009-09-14
> **Kareeser said:**
> Still works great in Karmic. It's too bad it's not installed by default, however...

Agreed--this really should come as a default option, already preinstalled.  If someone dislikes it, they're free to remove it, but to the average user having this in place makes things 'just work' versus not having it installed and wondering why things work differently with Firefox on their other machines...

--bornagainpenguin

---

### Post by Izte.net on 2009-11-09
I first tried to just install mozplugger. Now Evince pops up without any questions when I click on a PDF-file in Firefox. That's nice enough, but its not embedded into Firefox like i want. I also tried to edit the mozplugger-config-file, but it still opens Evince in a new window.

Any clues? Running Ubuntu 9.10.

---

### Post by ceykooo on 2009-11-11
> **Izte.net said:**
> I first tried to just install mozplugger. Now Evince pops up without any questions when I click on a PDF-file in Firefox. That's nice enough, but its not embedded into Firefox like i want. I also tried to edit the mozplugger-config-file, but it still opens Evince in a new window.

Any clues? Running Ubuntu 9.10.

Same issue here, tried both unedited and edited mozpluggerrc.  Clean installed Karmic a couple days ago.

---

### Post by megamania on 2009-11-11
Thanks - works fine for me on Karmic 64-bit, clean install of the Beta release.

In case it can help someone, this is the "pdf" part of my /etc/mozpluggerrc file:
```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat noisy swallow(evince) fill: evince "$file"
	ACROREAD()
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(okular) fill: okular "$file"
	GV()
	repeat noisy fill exits: evince "$file"

```

---

### Post by Izte.net on 2009-11-18
> **megamania said:**
> Thanks - works fine for me on Karmic 64-bit, clean install of the Beta release.

In case it can help someone, this is the "pdf" part of my /etc/mozpluggerrc file:
```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat noisy swallow(evince) fill: evince "$file"
	ACROREAD()
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	repeat noisy swallow(okular) fill: okular "$file"
	GV()
	repeat noisy fill exits: evince "$file"

```

That worked like a charm, thanks! ;)

---

### Post by macabro22 on 2009-11-18
> **Izte.net said:**
> That worked like a charm, thanks! ;)

Here it worked as well!

---

### Post by wastvedt on 2009-11-27
> I first tried to just install mozplugger. Now Evince pops up without any questions when I click on a PDF-file in Firefox. That's nice enough, but its not embedded into Firefox like i want. I also tried to edit the mozplugger-config-file, but it still opens Evince in a new window.

Any clues? Running Ubuntu 9.10.

Same issue here as with Izte.net and ceykooo. Help!

---

### Post by Balau on 2009-11-29
> **Izte.net said:**
> I first tried to just install mozplugger. Now Evince pops up without any questions when I click on a PDF-file in Firefox. That's nice enough, but its not embedded into Firefox like i want. I also tried to edit the mozplugger-config-file, but it still opens Evince in a new window.

Any clues? Running Ubuntu 9.10.

> **ceykooo said:**
> Same issue here, tried both unedited and edited mozpluggerrc.  Clean installed Karmic a couple days ago.

I had to close both firefox and evince to make it work the first time.
It's safest to close all instances of the two programs.

---

### Post by wastvedt on 2009-11-29
> I had to close both firefox and evince to make it work the first time.
It's safest to close all instances of the two programs. 

Yep, that's it, at least for me. When I make changes in mozpluggerrc I have to close firefox and the plugin program for the changes to take effect. Thanks!

---

### Post by ricardisimo on 2010-10-06
Good point... why isn't it the default? Or, at the very least, why isn't there an evince plugin available from the Mozilla site?

---

### Post by leorolla on 2011-05-02
What if you don't want embedded, just that Firefox proposes the file to be externally opened by evince rather than GIMP?

---

### Post by Jasman on 2011-05-05
I've done everything suggested in here, and I still get a prompt asking where to save my PDFs. Anyone have any suggestions? This is 11.04, new install, with Evince and Mozplugger.

---

### Post by ramsri on 2011-07-28
Either I'm also having issue with Ubuntu 11.04 64Bit and Firefox 5 version. Unable to view PDF's inline with the following settings 


application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
        repeat noisy swallow(evince) fill: evince "$file"
        ACROREAD()
        repeat noisy swallow(kpdf) fill: kpdf "$file"
        repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
        repeat noisy swallow(okular) fill: okular "$file"
        GV()
        repeat noisy fill exits: evince "$file"

---

### Post by beew on 2011-07-28
I don't know about 64 bits, but it works in 32 bits.  Also the original tutorial is too complicated, all you need is to move the last line in the pdf block in mozpluggerrc to the top like the following

> application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
      repeat noisy swallow(evince) fill needs_xembed: evince "$file"
    ACROREAD()
    repeat noisy swallow(Xpdf) fill needs_xembed: xpdf -g +9000+9000 "$file"
    repeat noisy swallow(okular) fill needs_xembed: okular "$file"
    repeat noisy swallow(epdfview) fill needs_xembed: epdfview "$file"
    GV()I don't see this line in my mozpluggerrc though
> repeat noisy fill exits: evince "$file" Maybe you can comment it  out (put a # in front) or delete it and see what happens.

Anyway, if you read the first few lines in Mozpluggerrc it appears that something has changed in the 11.04 version so that your editing will not be saved whenever there is an update, this is quite stupid though fortunately mozplugger almost never updates.

I have been using mozplugger for a while but now I have switched to the gpdf plugin for Firefox basically because mozplugger is in conflict with some multimedia plugins I use.It turns out gpdf is in some ways working better.  You may try that if mozplugger doesn't work for you.

---

### Post by ramsri on 2011-08-01
Thank you for the reply. However, I referred the following article and performed the troubleshooting steps and at least I was able to view the mozpluggercc in about:plugins. Before installing mozpluggercc I used a pdf plugin and removed it but I didn't removed the file which is located at 
rm ~/.mozilla/firefox/pluginreg.dat

I deleted it and it started working but opening in new window.

Source: [https://help.ubuntu.com/community/EvinceMozilla](https://help.ubuntu.com/community/EvinceMozilla)

---

