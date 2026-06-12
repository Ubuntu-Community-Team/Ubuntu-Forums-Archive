---
title: "HOWTO: Install ttf-fonts"
date: 2005-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by keron on 2005-11-01
Sometimes stupid-looking fonts are needed, and quality can take a second place. That's when you need those ttf-fonts for Windows that availible all over the web. 

To install a ttf from your ~/ :

```
cd /usr/share/fonts/truetype
sudo mkdir myfonts
cd myfonts
sudo cp ~/*.ttf .
sudo chown root.root *.ttf
sudo mkfontdir
cd ..
fc-cache
```
(taken from [http://www.inference.phy.cam.ac.uk/saw27/notes/adding-truetype-font-to-debian-or-ubuntu.html](http://www.inference.phy.cam.ac.uk/saw27/notes/adding-truetype-font-to-debian-or-ubuntu.html) 

Dont have any fonts to install? Take a look at 1001freefonts.com. They doesnt have 1001 fonts though. I counted 2875... 

But its not fun to navigate all those fonts. So I have pictures of them gziped [http://jensann.mine.nu/ubuntu/fontsdisplay.tar.gz](http://jensann.mine.nu/ubuntu/fontsdisplay.tar.gz)

And, since I had important stuff to do this evening, I also made a script that given the name of a font in that archive tries to download and install it. 

The script is [http://jensann.mine.nu/ubuntu/freefonts.sh](http://jensann.mine.nu/ubuntu/freefonts.sh) . 
```
wget http://jensann.mine.nu/ubuntu/freefonts.sh 
chmod +x freefonts.sh
sudo mv freefonts.sh /usr/local/bin/freefonts 
```

Extract the images to a folder and view the thumbnails. If you find a font you like, try

```
sudo freefonts fontname
```

and hopfully it will work. The fonts are not allways consistant, and I havent tried them all. Start a program, perhaps OpenOffice Writer and see if the font is there. It should be, if no error were reported...

Hopefully this will be of some use. It shouldnt be impossible to have a program such as the gnome art-fetcher for fonts.... You should make one :p

If anybody knows how to add .ttf files localy without the need for sudo, please let me know, or even better, extend the script....

---

### Post by wylfing on 2005-11-01
I'll admit I am not a font expert, but this seems like overkill to me. How about this:

1. From any Nautilus window, press Ctrl-L.
2. Type fonts:/// in the Location box and click Open.
3. A window will pop open. Drag your new fonts onto this window.

Done!

---

### Post by sciurus on 2005-11-02
Alternatively, simply move the font files into ~/.fonts

---

### Post by wylfing on 2005-11-02
Yep, that's where fonts:/// takes you :)

---

### Post by esperantisto on 2005-12-06
There's a font intaller coming with OpenOffice.org. Does it work with Linux?

---

### Post by erdalronahi on 2006-04-23
[QUOTE=wylfing]I'll admit I am not a font expert, but this seems like overkill to me. How about this:

1. From any Nautilus window, press Ctrl-L.
2. Type fonts:/// in the Location box and click Open.
3. A window will pop open. Drag your new fonts onto this window.

Done![/QUOTE]

Doesn't work for me in Dapper. I started Nautilus with sudo, but nothing happens when I drag the .ttf files into the font folder. Not even an error message.

---

### Post by geetarista on 2006-06-15
For me in Dapper, I can sometimes copy the file into fonts:///, but I can't preview it and it has some weird characters for the name.  It only "works" when I open nautilus/konqueror as root--If I don't open it in root, nothing happens.

---

### Post by Matchless on 2006-06-16
In Kubuntu Dapper you can just use the font installer in "settings" point it to the folder extracted from the downloaded fonts and install!

---

### Post by altonbr on 2006-09-04
> **wylfing said:**
> I'll admit I am not a font expert, but this seems like overkill to me. How about this:

1. From any Nautilus window, press Ctrl-L.
2. Type fonts:/// in the Location box and click Open.
3. A window will pop open. Drag your new fonts onto this window.

Done!

I can verify that this works in Dapper Drake (6.06). Thanks! I REEEAAAAALLLY needed this.:)

---

### Post by stalefries on 2006-09-05
I've used the fonts:/// thing for a while, and I've noticed that the fonts that I add there don't appear until I log out or shut down.

---

### Post by finferflu on 2006-09-05
Hi guys,

What about Xubuntu? I couldn't find any way to get the fonts installed... 

Thanks...

---

### Post by Paul133 on 2006-09-05
Does this work with Fontifier? [http://www.fontifier.com](http://www.fontifier.com)
I'm not sure if they're tff's, but they might be!

---

### Post by el_itur on 2006-10-03
I've got over 4000 fonts that I use for design. It would help for one or two but imagine that I surf over my 4000 fonts and find the one that my client logo is using, and I already had 400 fonts on my sistem I have to get rid of one or two to not overload my system. I have to manually remove and install every little font. 
That's not a good solution, at least for me, that's why windows have plenty font managers around (don't wanna start a flame war, it's just a comparison). 
I've heard about dfontmngr or something like that. But I didn't tested it. Would it help? is it user friendly (it doesn't matter if it's hard to understand I just need the job done)?

I tell this becouse I have spend a lot of time reading the synaptic's packages list and sourceforge's projects and none is for linux and none is a good GUI.

---

### Post by RocketScientist on 2006-10-29
RTFM (Read The FINE Manuals)
[https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html](https://help.ubuntu.com/ubuntu/desktopguide/C/desktop-tips.html)
Be sure to install the MS True Type Core fonts first if you are attempting to use *.ttf's
Do this after copying fonts into fonts:///
Fire up a terminal and type (or copy and paste):
sudo fc-cache -f -v

---

### Post by el_itur on 2006-10-31
RocketScientist, thanks for your response, I've been using that for managing my fonts. But if you ever worked on a design studio you should know that that's not the finest way.

The thing I need is a font manager with a nice interface for previewing and installing/removing fonts from my .fonts directory.

I've belived that this was the place for asking such thing.

---

### Post by stchman on 2007-04-12
If you want the Microsoft fonts then type this in a terminal:

sudo apt-get install msttcorefonts

If you have some custom font then do the following in a terminal:

(this assumes you have the terminal open in the folder where your fonts are located)

sudo cp *.ttf /usr/share/fonts/truetype 

then type 

sudo fc-cache -f -v

This will make them available to your applications.

---

### Post by stchman on 2007-04-12
If you want the Microsoft fonts then type this in a terminal:

sudo apt-get install msttcorefonts

If you have some custom font then do the following in a terminal:

(this assumes you have the terminal open in the folder where your fonts are located)

sudo mkdir /usr/share/fonts/truetype/customttf

sudo cp *.ttf /usr/share/fonts/truetype/customttf

then type 

sudo fc-cache -f -v

This will make them available to your applications.

---

### Post by dkuncer on 2008-02-02
> **wylfing said:**
> I'll admit I am not a font expert, but this seems like overkill to me. How about this:

1. From any Nautilus window, press Ctrl-L.
2. Type fonts:/// in the Location box and click Open.
3. A window will pop open. Drag your new fonts onto this window.

Done!

THANK YOU very much!! It was easy. I installed the font I needed...
Thanks.

---

### Post by GamingMazter on 2008-02-02
WOO! Great thanks...been trying loads of new stuff on Ubuntu lately :D

---

### Post by nilanath on 2008-06-18
So, all being very nice and sweet, either I am doing something wrong or what, but those fonts aren't showing up in the OpenOffice.org writer font listing. Anyone got an answer to that?:confused:

N.

---

### Post by arubislander on 2008-07-04
Call me simple, but isn't it enough for most applications to just install msttcorefonts from the the multiverse repository? That worked for me on Hardy. The fonts:/// url in nautilus did not.

---

### Post by roaddummy on 2008-11-29
I tried the ctrl-l and got the little box.  I typed in fonts:/// and got an error message.  I am either doing something wrong or I have a different version.  If there is anyone who can  maybe simplify this for me, then I would greatly appreciate it!!

Melanie

---

### Post by Hexagrapher666 on 2009-01-04
> **nilanath said:**
> ...those fonts aren't showing up in the OpenOffice.org writer font listing. Anyone got an answer to that?:confused:

I did a slight variation on Stchman's earlier recommendation and it worked beautifully.  (I am running Ubuntu 8.10, with OpenOffice.org 2.4.)

(Via Synaptic I found that msttcorefonts was already installed.)

I recommend closing any instance of OpenOffice.org that you have running.  In the terminal window I navigated to the directory where my downloaded .TTF file resided.  Then I typed:

[COLOR="Blue"]sudo mv *.ttf /usr/share/fonts/truetype/openoffice[/COLOR]

Then, as per Stchman's recommendation, I typed:

[COLOR="Blue"]sudo fc-cache -f -v[/COLOR]

When I launched OpenOffice.org Writer the new font did indeed appear in Writer's font list.

---

### Post by m4lte on 2009-01-07
> **stchman said:**
> If you want the Microsoft fonts then type this in a terminal:

sudo apt-get install msttcorefonts

If you have some custom font then do the following in a terminal:

(this assumes you have the terminal open in the folder where your fonts are located)

sudo cp *.ttf /usr/share/fonts/truetype 

then type 

sudo fc-cache -f -v

This will make them available to your applications.

Works fine for me on Ubunutu 8.10. Fonts appear in OpenOffice. Thanks!

---

### Post by SKhan on 2010-04-24
> **wylfing said:**
> I'll admit I am not a font expert, but this seems like overkill to me. How about this:

1. From any Nautilus window, press Ctrl-L.
2. Type fonts:/// in the Location box and click Open.
3. A window will pop open. Drag your new fonts onto this window.

Done!
didn't work for me in Ubuntu 9.10, it gives this error "Nautilus can not handle fonts location"

---

