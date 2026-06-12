---
title: "[SOLVED] How to install Helvetica.ttf"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-10-07
I need the Helvetica ttf font for OpenOffice.

Now I have helvetica.ttf

i copied it over to /usr/share/fonts/truetype/freefont
and to fonts:///

Then I issued fc-cache

but still no helvetica appearing in openoffice writer...

---

### Post by billgoldberg on 2008-10-07
> **WitchCraft said:**
> I need the Helvetica ttf font for OpenOffice.

Now I have helvetica.ttf

i copied it over to /usr/share/fonts/truetype/freefont
and to fonts:///

Then I issued fc-cache

but still no helvetica appearing in openoffice writer...

Create a folder in your home directory.

Name it 

.fonts

Put it in there.

*(notice the dot before "fonts")*

---

### Post by WitchCraft on 2008-10-07
> **billgoldberg said:**
> Create a folder in your home directory.

Name it 

.fonts

Put it in there.

*(notice the dot before "fonts")*

just wanted to do so, but the folder .fonts already exists, and helvetica.ttf is the only font in there...

---

### Post by LowSky on 2008-10-07
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

that should help

---

### Post by billgoldberg on 2008-10-07
Well, I don't know then.

Are you sure you don't have the font available in openoffice?

Maybe look around the openoffice hidden folder in /home to see if you can place fonts in there some where.

---

### Post by bhadotia on 2008-10-07
Whenever I download any .ttf , I put them in /usr/share/truetypes and they become available system wide.

The wiki you were pointed to above gives the same guidelines (although, I found this way experimentally:popcorn:)

---

### Post by WitchCraft on 2008-10-07
Not very helpful.

Now I have installed ALL windows fonts, and they show up, except helvetica...

---

### Post by snova on 2008-10-07
Capitalization? Perhaps it needs to be **H**elvetica.ttf.

Just a guess.

---

### Post by PierreDeKat on 2008-10-07
Just double checking, you do have msttcorefonts installed, right?

---

### Post by unutbu on 2008-10-07
Please post the output of 
```

sudo find / -iname "Helvetica.ttf" -exec ls -l {} \;

```
It might take a minute or two for this command to complete. 

If you have more than one Helvetica.ttf, I recommend removing all but one.
Since each of the directories in /usr/share/fonts/truetype is related to a package, I think it is probably best not to "pollute" those directories by adding files to them that those packages don't expect to be there.

Instead use "gksu nautilus" or 
```

sudo mkdir /usr/share/fonts/truetype/myfonts
```

to create a directory for fonts not associated with any package.

Then move Helvetica.ttf into /usr/share/fonts/truetype/myfonts and remove all other copies of Helvetica.ttf that the "sudo find" command found.
 
Then do a sanity check:
```

ls -l /usr/share/fonts/truetype/myfonts/Helvetica.ttf
```

Make sure the permissions look like this:

```
  -rw-r--r--  1 root root 26860 2008-04-13 20:04 Helvetica.ttf
```
Also run
```


ls -ld /usr/share/fonts/truetype/myfonts/
```

to check that the permissions on the parent directory allow everyone to read the directory:
```

drwxr-xr-x 2 root root 4096 2008-04-13 20:04 /usr/share/fonts/truetype/myfonts/
```

Finally, do a sanity check on Helvetica.ttf:
```

gnome-font-viewer /usr/share/fonts/truetype/myfonts/Helvetica.ttf
```

A screen should pop up showing a rendering of the Helvetica characters.

If all the above does not catch the problem, try this again:
```

sudo fc-cache -f -v /usr/share/fonts/truetype/myfonts/
```

The last command I believe should scan /usr/share/fonts/truetype/myfonts/ and make any fonts it finds accessible to the rest of the system.

Now try openoffice again. If it still does not work, please post the output of
```

ls -l /usr/share/fonts/truetype/myfonts/Helvetica.ttf
ls -ld /usr/share/fonts/truetype/myfonts/
sudo fc-cache -f -v /usr/share/fonts/truetype/myfonts/
fc-list | grep -i Hel
```

---

### Post by Kellemora on 2008-10-08
Hi WitchCraft

Something that has worked for me with no problems so far was to completely rename the files.  This does NOT affect the Embedded Name within the font, but makes it accessible if you select it.

I place all of my fonts in /usr/share/fonts/truetype and Create a Folder for that group of fonts.  The name I choose to use does not seem to matter one Iota either as far as Open Office finding and using the fonts.

Of course I do name them so I know what they are, because 118379625I.ttf, 118379625B.ttf and 118379625N.ttf means nothing to me.

In this case I made the Folder they are in read ttf-quickfont-roller and renamed each of the font files rolleritalic.ttf, rollerbold.ttf and rollernormal.ttf

Their real full name comes up in Open Office font names window as embedded in the font itself.

I did not INSTALL the fonts, just copied them to the folder named above in /usr/share/fonts/truetype/  I did this from Root using Nautilus so I could just cut n paste.  I have about 9 font's I've done this way and they all work just fine.  Just remember to get ALL of the fonts associated with a font name else it may generate the other font upon usage.

Hope this helps you out a little?

TTUL
Gary

---

### Post by Krupski on 2008-10-08
> **WitchCraft said:**
> Not very helpful.

Now I have installed ALL windows fonts, and they show up, except helvetica...

OK... here you go:

Use a TERMINAL to do this. Obviously enter your root password for "sudo".

(1) Make a new directory for your new font(s):

```

sudo mkdir /usr/share/fonts/truetype/ttf-extrafonts

```

(the example uses "ttf-extrafonts", use whatever YOU like).


(2) Next, copy your Truetype font(s) to the proper directory:

```

sudo cp Helvetica.ttf /usr/share/fonts/truetype/ttf-extrafonts/

-- or --

sudo cp *.ttf /usr/share/fonts/truetype/ttf-extrafonts/

```

(3) Next, update your font cache:

```

sudo fc-cache -fv

```

Every new font you installed should now be available.

Good luck!

-- Roger

---

### Post by WitchCraft on 2008-12-09
No no no, that all doesn't help.

But I found the culprit: if I install OpenOffice 3 Beta, Helvetica shows up... not so in OpenOffice 2.X...

The problem seems to be OpenOffice 2.x censoring Helvetica...

---

### Post by Kellemora on 2008-12-09
Hi WC

I'm using Open Office Writer 2.4.1 and ALL SEVEN of my helvetica fonts show up just fine.

I just pasted them into the /usr/share/fonts/truetype folder.
In my case I made a new folder inside of the /truetype folder named /ttfHelvetica and installed all the Helvetica fonts inside of that folder.

Have you tried just copy n paste from your stored fonts file or windows machine over to /usr/share/fonts/truetype?

TTUL
Gary

---

### Post by WitchCraft on 2008-12-09
> **Kellemora said:**
> Hi WC

I'm using Open Office Writer 2.4.1 and ALL SEVEN of my helvetica fonts show up just fine.

I just pasted them into the /usr/share/fonts/truetype folder.
In my case I made a new folder inside of the /truetype folder named /ttfHelvetica and installed all the Helvetica fonts inside of that folder.

Have you tried just copy n paste from your stored fonts file or windows machine over to /usr/share/fonts/truetype?

TTUL
Gary

sure i did. But no reaction on OpenOffice 2.4, but works with OpenOffice 3 beta...

---

### Post by unutbu on 2008-12-09
What happens if you rename ~/.openoffice.org2: 

```

mv .openoffice.org2 .openoffice.org2_old
```

Then when you launch OpenOffice 2.4, perhaps it will regenerate ~/.openoffice.org2 to the default configuration.

---

### Post by Kellemora on 2008-12-09
Hi WC

Are you SURE that your Helvetica fonts are "Display & Printing" fonts?????  Not all font's are for both!  Font's that are for Printing Only will NOT show up on the display or in the font listing in OOo programs drop down lists.

Fonts for Display will show up on the screen, but won't print properly, often another font is substituted.

The way around this is to install the .afm file in the same folder with the printer only fonts.  Or in a subdirectory in the fonts folder named afm.

It might be easier just to find a newer version of your fonts that are constructed normally, if that's the problem that is.

You might try going to the OOo web site and looking for the Helvetica made by Bitstream, those work in OOo just fine.

TTUL
Gary

---

