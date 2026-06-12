---
title: "HOWTO: Use Mac fonts on Linux"
date: 2006-12-08
forum: Outdated Tutorials &amp; Tips
---

### Post by 3rdalbum on 2006-12-08
A tremendous number of fonts were created for Macintosh when it was king of typesetting. So how do you get those fonts going on Ubuntu, assuming you still have a Mac available?

1. Download the Fontforge program:
```
sudo apt-get install fontforge
```

2. On a Macintosh, download a program that will create BixHexes* (if you haven't done so already). The original BinHex program (you can get it from [http://www.pure-mac.com]("http://www.pure-mac.com")) works fine on OS 9. Don't use Stuffit Lite - we want the file .hqx'ed, not .sit.hqx'ed.

3. Use your program to create a .hqx of your existing font suitcase. "Loose" fonts will probably work too. In BinHex 4.0, you go File > "Application -> Upload" and choose the font and the destination file.

4. Put the .hqx file onto a flash drive or some other thing that you can access from within Ubuntu. If it's a removable drive, unmount it and stick it into your Ubuntu machine.

5. Copy the file to your Ubuntu home directory. Press Alt-F2 and type "fontforge", and press Enter.

6. You will be prompted for a file. Double-click on your .hqx file; after a short pause Fontforge will open and display it.

7. Go into Element > Font Info... and click the General tab. In the "Em-Size" popup, choose "1000".

8. Dismiss that dialog. Now go File > Generate Fonts...   Choose "PS Type 1 (binary)" as the type, now save it. You will get a warning about the first 256 characters... ignore this and hit Yes.

9. Now you will have ~/fontname.pfb. Open a root file browser and navigate to /usr/share/X11/fonts/Type1/. Drag and drop your font from the home directory into there, restart your word processor or The Gimp, and your font will be available! Happy typesetting!

* Apparantly, Fontforge can also work with MacBinary-encoded (.bin) font files. I haven't tried this.

---

### Post by Sukarn on 2006-12-08
If you no longer have access to a mac, is there no way to get mac fonts?
I mean like you can still get the windows fonts going without having access to a windows machine.

---

### Post by 3rdalbum on 2006-12-09
Sukarn, there may be a way but I don't know how it would be done.

The reason why you can use Windows fonts in Linux without dramas is because Windows files only have one part to them - the data fork. Mac files often have two parts - the data fork, and the resource fork. The actual font information is stored in the resource fork. Unfortunately, as Windows and Linux files don't ever have more than one fork, they always destroy a Mac file's resource fork if they come in contact.

Thus, the reason for the BinHexing (which wraps both forks up into one fork). If you tried to put the Mac font file directly onto Linux, it would destroy the resource fork and therefore destroy the font.

There *may* be some kind of kernel extension that can deal with Mac files properly, but you'd still have to Binhex them so you could convert them to Type1/Truetype fonts with Fontforge. X can't deal with Mac fonts directly, for obvious reasons.

If anyone does know of a way to preserve the resource fork, please let me know - it may help me get Marathon Aleph One working with my Mac map files :-)

---

### Post by blackmh on 2006-12-09
There are Mac fonts available for download at [http://www.osx-e.com/downloads/misc/macfonts.html](http://www.osx-e.com/downloads/misc/macfonts.html).

I adjusted them to look as much as possible as fonts on real Mac and I'm satisfied

When I fire up pear pc with panther I will post screenshot to compare

---

### Post by bodhi.zazen on 2006-12-12
Nice How-to

This thread has been added to the UDSF wiki.

[Mac_fonts_on_Linux](http://doc.gwos.org/index.php/Mac_fonts_on_Linux)

---

### Post by Unterseeboot_234 on 2006-12-21
Thank you for a wonderful Christmas present. I just want to comment as a former typesetter I paid too much for the Mac version and later the PC version of a similar program to make/convert fonts. FontForge is superior and it fixed a very quirky font. Made it perfect. I had to fumble through the program without knowing exactly what I was doing, but selecting the T & X option for Generating a new font was the answer. Now, if I could just find the dude that I gave my old Mac away to... 7,000+ fonts on it.  :-?

---

### Post by komputes on 2008-05-24
Using Hardy and .hdx (Aladdin/Stuffit) compressed fonts from multiple sources and I keep getting the following error.

---

### Post by DrKay on 2010-03-16
The best way I have found to install Mac fonts on Ubuntu is to use Fondu. It is in the repositories. Here is a link to a tutorial that will show you how. I've tried Fondu and FontForge, and Fondu saved me a lot of time over FontForge. If you only have a few fonts to convert, then FontForge would be OK, but for many fonts, Fondu is the way to go.

[http://ubuntu-tutorials.com/2006/12/13/convert-mac-based-fonts-for-use-on-ubuntu-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/13/convert-mac-based-fonts-for-use-on-ubuntu-ubuntu-6061-610/)

---

