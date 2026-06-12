---
title: "HOWTO: Take back the Firefox Logo"
date: 2005-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by Sionide on 2005-04-27
HOWTO: Get rid of that *blue globe thing* and put the original Firefox Logo where it belongs!

**Why would I want to do this?**
To me, Firefox looks kinda weird without its unique icon. The logo itself is incredible, it's eye-catching, colourful and sexy :P For more information on the logo, [click here](http://www.actsofvolition.com/archives/2004/february/brandingmozilla) and [here](http://www.spreadfirefox.com/?q=node/view/3064) and [here.](http://www.hicksdesign.co.uk/journal/377/branding_firefox")


**Brief Overview**
1 - Download the original Firefox Logo (and associated icons) in png format
2 - Rename and copy a few files to various locations
3 - Log out / Log in to apply the changes
*It's that simple.*


**Take Back the Firefox Logo**

**#1** - You will need two versions of the Firefox Logo.

The first is the actual logo file, in .png format. (right-click -> save image as)

[CENTER][img]http://img105.echo.cx/img105/1515/firefoxrgb2oa.png[/img][/CENTER] 

The second is the "document" icon, indicating for example, that a file has a .htm extension which opens it in Firefox. (right-click -> save image as)

[CENTER][img]http://img231.echo.cx/img231/5930/document8nq.png[/img][/CENTER] 

**#2** - Preparing the files

You will need to rename the files you just downloaded in the following way;

```

mv firefoxrgb2oa.png mozilla-firefox.png

mv document8nq.png document.png

```

**#3** - You are now ready to begin replacing the old icons

(At this point, you may wish to make backups of the old icons for future reference - simple navigate to the mentioned directories and move the old files out before replacing them with the new icons)

There are three directories which contain Mozilla Firefox icons, they are as follows;

**/usr/share/pixmaps** - is the location of the icons for the launcher
**/usr/lib/mozilla-firefox/icons** - is the location of the icons the application uses
**/usr/lib/mozilla-firefox/chrome/icons/default** - is the 2nd location of application icons

You will need *root access* to those directories, using the *sudo* command from the command line helps. I also assume that the files you downloaded have been placed in your ~home directory.

```

sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png

sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm

```

```

sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm

sudo cp document.png /usr/lib/mozilla-firefox/icons/document.png

```

and finally;

```

sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm

```

**#4** - the final step, you're nearly there!

Log out and log back in. Behold, the Firefox logo is back with avengence!! :D

Or restart X using "Ctrl+Alt+Backspace"

#5 - optional extras

Make an alias, to put all the commands into one easy one. I've done this;

```
sionide@sphinx:~$ alias firefoxicons='sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png; sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm; sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm; sudo cp document.png /usr/lib/mozilla-firefox/icons/document.png; sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm'
```

Alternatively you could write a bash script to do it for you...

_____________________________________

This HOWTO is based on [this](http://ubuntuforums.org/showthread.php?t=29908) thread. Thanks to bored2k and panickedthumb for their input.
Feedback will be appriciated as this is my first HOWTO :)

---

### Post by Sniffer on 2005-04-27
Simple

But nice, thks for your work.

---

### Post by ssam on 2005-04-27
just to make this work from other directorys, you might want to use absolute paths, ie
```
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
``` 
instead of
```
sudo cp mozilla-firefox.png ../../usr/share/pixmaps/mozilla-firefox.png
``` 

and also (correct me if i am wrong), but i dont think renaming the files to xpm from png is a good idea. they are still png files but with a potential confusing file name.

you could install imagemagick and use
```
convert something.png something.xpm
```
check the man page, i think that syntax is right

it would be good if mozilla.org and debian could agree a way for this icon to be included, but i can't remember the reasons behind it.

---

### Post by Sionide on 2005-04-27
[QUOTE=ssam]and also (correct me if i am wrong), but i dont think renaming the files to xpm from png is a good idea. they are still png files but with a potential confusing file name.

you could install imagemagick and use
```
convert something.png something.xpm
```
check the man page, i think that syntax is right[/QUOTE]

Perhaps this is for another HOWTO...

I just tried it and the coverted .xpm didn't appear to have the same transparent areas as the renamed .png

I did it that way and haven't had any problems.

Thanks for your other point, I've made those changes..

---

### Post by ow50 on 2005-04-27
[QUOTE=Sionide]The second is the "document" icon, indicating for example, that a file has a .htm extension which opens it in Firefox.[/QUOTE]

Is the document icon actually used somewhere? 

[QUOTE=Sionide]I just tried it and the coverted .xpm didn't appear to have the same transparent areas as the renamed .png[/QUOTE]

You can do the conversion with GIMP. Just open the png and save as xpm. The result looks to me about as good as an xpm can look.

---

### Post by Sionide on 2005-04-27
[QUOTE=ow50]Is the document icon actually used somewhere? 

You can do the conversion with GIMP. Just open the png and save as xpm. The result looks to me about as good as an xpm can look.[/QUOTE]

First question: No idea, perhaps... That was just an example of where I know its used.

Second question: Yeah, could be - but as I say, I just renamed the file and it hasn't had any really detrimental effects. So for the sake of simplicity I'm inclined to leave it how it is, at least for the time being?

---

### Post by jasplund on 2005-04-27
I suppose this would work for thunderbird as well. Anyone knows where to find the TB logo?

---

### Post by thechitowncubs on 2005-04-27
[QUOTE=jasplund]I suppose this would work for thunderbird as well. Anyone knows where to find the TB logo?[/QUOTE]
 why isn't this used by default?

---

### Post by jasplund on 2005-04-27
Nope it´s a simple and ugly envelope with a really small blue bird. I found the real one here [http://nilesh.org/weblog/2004/04/new-thunderbird-logo/](http://nilesh.org/weblog/2004/04/new-thunderbird-logo/) though

---

### Post by bored2k on 2005-04-27
Nice howto Sionide. Turned out better than I imagined ;). Cheers.

---

### Post by Sionide on 2005-04-27
[QUOTE=thechitowncubs]why isn't this used by default?[/QUOTE]

It's strange, both logos are under weird licenses from the Mozilla Foundation which doesn't allow them to bundled into distributions, which I find mad but they must have their reasons. I'm fairly sure other distributions have similar issues. I can't remember the specifics though so if anyone can shed some more light on this, that would be good.

I don't use Thunderbird for email but the process of logo changing will definately be similar. Have a look on [spreadfirefox.com](http://www.spreadfirefox.com/) for the actual logos.

[quote=bored2k]Nice howto Sionide. Turned out better than I imagined ;) Cheers.[/quote]

---

### Post by bored2k on 2005-04-27
[QUOTE=Sionide]It's strange, both logos are under weird licenses from the Mozilla Foundation which doesn't allow them to bundled into distributions, which I find mad but they must have their reasons. I'm fairly sure other distributions have similar issues. I can't remember the specifics though so if anyone can shed some more light on this, that would be good.

I don't use Thunderbird for email but the process of logo changing will definately be similar. Have a look on [spreadfirefox.com](http://www.spreadfirefox.com/) for the actual logos.[/QUOTE]
 It's actually absurd IMO.
"You can use the software but you can't use my logo!". Da Vinci didn't drew it, so I don't even get the joke. It's like a small child telling his brother to use the TV and remote, but he can't touch the actual TV. Silly ^_^

---

### Post by mrbass on 2005-04-27
I say replace it with the granddaddy of all firefox icons I've seen.
[http://www.grafhp.ch/bilder/Illustration/Redaktions_Jobs/Feuerfuchs.htm](http://www.grafhp.ch/bilder/Illustration/Redaktions_Jobs/Feuerfuchs.htm)

---

### Post by Sionide on 2005-04-27
Heh, there's even *more* copyright with that one though!

You can probably use that icon in my example, heheh..

---

### Post by justaguynpc on 2005-04-27
Did I see someone asking for the Thunderbird icon?


http://images.google.com/images?q=tbn:rc7FDep4K6YJ:www.winplanet.com/img/screenshots/icon-thunderbird.gif[/url]

---

### Post by Quest-Master on 2005-04-27
> It's strange, both logos are under weird licenses from the Mozilla Foundation which doesn't allow them to bundled into distributions, which I find mad but they must have their reasons.

What a completely stupid rule. I mean, most Linux distros are spreading the same flame Firefox helped ignite; open source.

Silly Foundation.

---

### Post by thechitowncubs on 2005-04-27
Wow, what a mistake by the Mozilla Foundation.

---

### Post by ToastedToad on 2005-04-27
[QUOTE=thechitowncubs]Wow, what a mistake by the Mozilla Foundation.[/QUOTE]
 Thanks for the tip. Apreciate it:)

---

### Post by crazybill on 2005-04-28
Worked great. Thanks

---

### Post by gasparov on 2005-04-28
Few more icons and sorry but I don't remember where i got them:

[[IMG]http://img253.echo.cx/img253/6043/firefoxexperiment2019yr.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment2019yr.png)[[IMG]http://img253.echo.cx/img253/9132/firefoxexperiment2026wr.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment2026wr.png)[[IMG]http://img253.echo.cx/img253/6640/firefoxexperiment3015wt.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment3015wt.png)[[IMG]http://img253.echo.cx/img253/4863/firefoxexperiment3026zk.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment3026zk.png)[[IMG]http://img253.echo.cx/img253/6941/thunderbird1014we.th.png[/IMG]](http://img253.echo.cx/my.php?image=thunderbird1014we.png)[[IMG]http://img254.echo.cx/img254/8038/thunderbird1026vd.th.png[/IMG]](http://img254.echo.cx/my.php?image=thunderbird1026vd.png)

---

### Post by bored2k on 2005-04-28
[QUOTE=gasparov]Few more icons and sorry but I don't remember where i got them:

[[IMG]http://img253.echo.cx/img253/6043/firefoxexperiment2019yr.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment2019yr.png)[[IMG]http://img253.echo.cx/img253/9132/firefoxexperiment2026wr.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment2026wr.png)[[IMG]http://img253.echo.cx/img253/6640/firefoxexperiment3015wt.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment3015wt.png)[[IMG]http://img253.echo.cx/img253/4863/firefoxexperiment3026zk.th.png[/IMG]](http://img253.echo.cx/my.php?image=firefoxexperiment3026zk.png)[[IMG]http://img253.echo.cx/img253/6941/thunderbird1014we.th.png[/IMG]](http://img253.echo.cx/my.php?image=thunderbird1014we.png)[[IMG]http://img254.echo.cx/img254/8038/thunderbird1026vd.th.png[/IMG]](http://img254.echo.cx/my.php?image=thunderbird1026vd.png)[/QUOTE]
 Those were from gnome-look.org probably.

---

### Post by Sniffer on 2005-04-28
[QUOTE=bored2k]Those were from gnome-look.org probably.[/QUOTE]


That icons are from Weboso (DevianArt). Great Icon maker, to me one of the best i have seen.

---

### Post by Sionide on 2005-04-28
Yeah I like the middle two.

---

### Post by ignavia on 2005-04-28
Okay dude, your images are gone.

---

### Post by bored2k on 2005-04-28
Oops .. didn't know he was using my images. I'll edit his post ASAP.

**edit**- Fixed thread.

---

### Post by Gandalf on 2005-04-29
Nice HOWTO man, Greetz...

---

### Post by Josh M on 2005-04-29
Worked fine for me, thanks.

---

### Post by braveerudite on 2005-04-30
Please someone explain why they don't use the original Firefox logos.  I'm dying to know why. I always wonder

---

### Post by braveerudite on 2005-04-30
Ok I couldn't wait for you guys to give me an answer so I went into Google and found one.


So lets say debian has a few debian specific firefox bugs they'd like to patch before they compile and distribute as debian packages. The Foundation is refusing the right to let debian use the official artwork because those patches haven't been fully tested by Mozilla staff. Regardless of what you believe should be done, it's how things are. (And as funny as it is, this actually happened -- debian's firefox package manager is pissed.)

They are just trying prevent the firefox logo from being tarnished by super-ultra-mega-optimized (experimental) versions of its software horribly compiled that break all the time, by establishing a meaningful brand.

---

### Post by bored2k on 2005-04-30
[QUOTE=braveerudite]Ok I couldn't wait for you guys to give me an answer so I went into Google and found one.


So lets say debian has a few debian specific firefox bugs they'd like to patch before they compile and distribute as debian packages. The Foundation is refusing the right to let debian use the official artwork because those patches haven't been fully tested by Mozilla staff. Regardless of what you believe should be done, it's how things are. (And as funny as it is, this actually happened -- debian's firefox package manager is pissed.)

They are just trying prevent the firefox logo from being tarnished by super-ultra-mega-optimized (experimental) versions of its software horribly compiled that break all the time, by establishing a meaningful brand.[/QUOTE]
 We already discussed this on page2 .

---

### Post by randomidiot on 2005-04-30
For KDE users there is an extra step:
change the ugly, hardbodered version of your icontheme

```

sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/16x16/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/24x24/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/22x22/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/32x32/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/48x48/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/64x64/apps/firefox.png
sudo cp mozilla-firefox.png /usr/share/icons/crystalsvg/128x128/apps/firefox.png

```

please note that "crystalsvg" may has to be changed to the icontheme-name you are currently using!

---

### Post by nickless on 2005-04-30
har thx :D

---

### Post by momo66 on 2005-04-30
Worked like a charm for me.  Thanks!!!

---

### Post by artnay on 2005-04-30
For those who haven't found a nice FF icon yet: [WinCustomize](http://www.wincustomize.com/Skins.aspx?LibID=29&view=1&sortby=4&sortdir=DESC&p=1&advanced=0&searchtxt=firefox).

From there you can find the original logo and icon for the files that FF handles. My personal favourite is on the page 5, Unofficial Mozilla Firefox Abstract.

---

### Post by mellowyllw6 on 2005-04-30
Thanks! Worked the first time I tried it, and the icon looks great.

---

### Post by abowman on 2005-05-05
Here's a link to logos right from firefox:
[http://www.spreadfirefox.com/?q=node/view/3064](http://www.spreadfirefox.com/?q=node/view/3064)

---

### Post by dejitarob on 2005-05-30
[QUOTE=Sionide]Perhaps this is for another HOWTO...

I just tried it and the coverted .xpm didn't appear to have the same transparent areas as the renamed .png

I did it that way and haven't had any problems.

Thanks for your other point, I've made those changes..[/QUOTE]
convert firefox.png firefox.xpm worked for me. Looks slightly better on the kde panel too.

---

### Post by allforcarrie on 2005-06-17
Can someone tell me why none of these command ever work for me????

---

### Post by vladuz976 on 2005-07-06
The second is the "document" icon, indicating for example, that a file has a .htm extension which opens it in Firefox. (right-click -> save image as)


where is this icon i need to download? the only thing on here is the first icon.

---

### Post by Sam on 2005-07-06
[QUOTE=vladuz976]The second is the "document" icon, indicating for example, that a file has a .htm extension which opens it in Firefox. (right-click -> save image as)


where is this icon i need to download? the only thing on here is the first icon.[/QUOTE]
You can find it in [this archive](http://ubuntuforums.org/attachment.php?attachmentid=1113). If you prefer a script for doing the job, have a look [here](http://ubuntuforums.org/showthread.php?t=34354).

---

### Post by urbandryad on 2005-09-27
if you have firefox on the panel, you just have to right click firefox, click preferences(orwhatever it says) and click on the icon button, then you can search and replace the icon. ^^ I guess its not the same if you have firefox as a desktop item though.

---

### Post by MerZo on 2006-03-09
I wonder they the colors in the Xfce menu have different colors. Anybody got an answer? 

Using firefox 1.5.0.1 by following a howto.
And this one.

I think the colors should be the same? One is lighter and one is darker.

The question is that if i missed something, for example i cant find the document picture, maybe it is that.

---

### Post by urbandryad on 2006-05-18
I tried this with Xubuntu Breezy and it worked just fine. :) Just wanted to let those running Xubuntu who so they can replace their own icons. ;)

---

### Post by russellnation on 2007-07-01
agghh i did that but on the top of the screen in my shortcut its still the stupid globe icon..... wait let me check in application menu.....aghh same there..... 
any ideas
ill keep on trying
and yes i did log out/in again
oh yeah on feisty


ok upon further review its only with one icon theme package so maybe i can get in there and delete the crappy globe one and go back to original icon or the really cool replacement one....

ok re downloaded the Neu icons from gnome-look.org and then replaced each firefox icon  with a coresponding sized (22x22, 24x24...) firefox logo (.png) i chose the fresher fiercer looking replacement firefox icon from gnome-look.org instead but  eh to each his/her own.... and then re archived it  and followed install instructions provided with the icon set and wham bam thankyou maam i have no longer got to stare at a boring globe icon which was in the package.

ahh thank you linux

---

