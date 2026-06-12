---
title: "HOWTO install fonts using dfontmgr (GUI for defoma, Debian Font Manager)"
date: 2005-10-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Bill Statler on 2005-10-05
This is an incomplete HOWTO about dfontmgr.
As a new Linux user I was rather confused by how to properly install fonts, so I was happy to discover a GUI application, dfontmgr, that acts as a user-friendly(ish) interface for defoma, the Debian Font Manager.  I've written some instructions on how to install and use dfontmgr, but I could use some help from the experts to complete this "HOWTO".  (More on that later.)
Anyway, here's how to use dfontmgr to install fonts:
First, install (or upgrade) the following packages, using your favorite "apt"-type software (aptitude, apt-get, Synaptic, etc.) with "sudo" or logged in as root:
defoma  [Debian Font Manager, installed by default with Ubuntu, but you may wish to upgrade]
defoma-doc  [puts doc files in /usr/share/doc/defoma-doc/]
dfontmgr  [from "universe" -- graphical interface to defoma]
psfontmgr  [from "universe" -- needed if you're planning to add Postscript fonts (I haven't tested this)]
Create a directory /usr/share/fonts/truetype/custom/ (or whatever name you like) and copy your .ttf (TrueType) font files into it.  (Postscript Type 1 fonts should probably go in /usr/share/fonts/type1/custom/, but I haven't tried installing any yet myself.)
Start up dfontmgr (as root or with "sudo"), click on "Register Font", and use the file selector to navigate to /usr/share/fonts/truetype/custom/ and select a font to register.  (Dragging-and-dropping is supposed to work here, but it's buggy: if it works at all, it produces a font filename with extra slashes in front, so I don't recommend using it.)
(You'll probably find it helpful to also open the font with the Gnome Font Viewer, so you can see what you're installing and verify that your font file is readable.  Just double-click the font from the Nautilus file manager.)
The dfontmgr font registration wizard will try to identify what category the font is (e.g., TrueType, Type 1, etc).  For fonts it can't identify (which seems to be all of them!) you can select the appropriate category manually.  Next, the hints generator will lead you through creating hints file information (Family, Subfamily, FontName, Foundry, Location, Charset, GeneralFamily, Weight, Width, Shape(s), Alias(es), and Priority).
Note that "hints files" have NOTHING to do with the "hinting" or "autohint" features used in font rendering, so don't let the similar name confuse you.  For more details about hints, open up the following link in your browser (this is one of the help files installed by the defoma-doc package):
file:///usr/share/doc/defoma-doc/developers.html/ch1.html
This process is not nearly as intimidating as it appears, because dfontmgr proposes reasonable default choices for most of the hints, so you can just keep clicking "Next" if they look satisfactory.  The "Family" and "Shape" hints need some extra instructions:
If dfontmgr discovers that your font's "Family" name contains blanks, it will replace the blanks with dots (e.g., "Maiandra GD" becomes "Maiandra.GD").  This may be technically okay but it will confuse OpenOffice.org and you'll see two versions of each font name in the font selector.  Use hyphens instead (like this: "Maiandra-GD").  The easiest way to do this is to accept the default name (with dots), and edit it later (see below).
The "Shape" entry is a bit confusing.  You can select more than one value here.  Typically you'd want to select either Serif or NoSerif, AND ALSO either Upright or Oblique or Italic to indicate the amount of slant.  You can also add Condensed or Expanded for fonts that are squeezed or stretched in the horizontal dimension.
After the hints generator has finished prompting you for all the hints file information, you'll have an opportunity to hand-edit the file before it becomes "official".  (This is the time to fix the "Family" name if it contains dots: replace the dots with hyphens.)  If you mess up, you can always click "Change Hints" to fix things.
That's all!  Repeat "Register Font" for all your other new fonts.
Okay, what's the point of going through all this, rather than just dropping the font files in an existing font directory and waiting for them to be automatically found?
This is where I could use some expert assistance with this HOWTO.  I only have a vague understanding of why I should install fonts this way.  I think it ought to make the fonts available to more applications.  Can someone please contribute a better explanation?
I also thought that some of the hints file data could make the fonts more useful.  For example, I noticed that one of the available hints is "Transform", which is supposed to control whether the font can be transformed into slanted and/or bold forms.  AHA!  Does this mean we can take a font like Kristen ITC, which only has a regular version (no bold or italic), and automatically generate slanted or boldized forms of it?  Unfortunately, adding "Transform = Slant Boldize" to the hints file seems to have no effect (at least, not in OpenOffice.org 1.1.3).
So I'd also appreciate some expert advice on how to make best use of the hints files.
Thanks in advance to anyone who helps to complete this HOWTO!

---

### Post by deepclutch on 2008-01-02
gtk1.2 looks ugly and buggy!i hope they rewrite the application with gtk2+ :D

---

### Post by granny6989 on 2008-04-02
So - I'm somewhat new at Linux, trying to work this out, needed some postscript fonts.... etc,etc.. Finally after a good long search came up with this how-to, and thought I'd throw in what I did to get a majority of them (fonts) to work and get recognized.
   First off, I'm running Gutsy on an AMD64 with 32 bit code (don't ask). Nvidia card if it matters (pro'ly not). Mostly just trying to get some options for Inkscape and the Gimp, along with some dabbling in Xara.

   I started by making sure I had the three files mentioned above - Defoma, psfontmgr and dfontmgr. Got those all installed and set in Synaptic. Quick and easy.
   Next, I went into terminal and got into /usr/share/fonts/type1, which was already existing. I then added a new subfolder, which I called postscript, although I'm sure you can name it whatever you want. I then copied my entire CD of postscript fonts into this directory. (I ended up using cp with the -r flag to get all the subfolders and  etc to keep it organized). Double checked and all the font folders and files were there.
   I decided to just try updating the font cache at that point to see what would happen. Used:

       code:  $sudo fc-cache -f -v

  Waited a few seconds for that to finish and then exited the terminal. I checked my programs and most all of the fonts showed up. Definitely not the entire set, but quite a few of them. I assume at this point I need to maybe go into dfontmgr and try to see if the rest can be used, or maybe it's just that certain programs don't like to 'see' all of them. Not sure just yet. I will work at that tomorrow and get back to you. Just wanted to post this for anyone that may be looking...:)

S*

---

### Post by granny6989 on 2008-04-02
So, got back at it and tried dfontmgr from terminal, just to see. Seems like it only wants to edit installed files? Not sure, I only messed with it briefly. Not much to say about that right now....:confused:

Anyways, final install was to add all my postscript fonts into the usr/share/fonts/type1/gsfonts-other folder, leaving them in their appropriate subfolders. updated the font cache again, and now I have all my fonts in all my programs! So, a few fonts seem to be eluding me still, but for the most part they are all there. 

As I stated before, I am somewhat new to this, and this may not be the end all fix or exactly most proper of installs. However, if you need to get a pile of ps fonts installed and functional, this worked for me. I am using them for graphics and not really saving them as text, so ultimately they are just shapes for my applications. I have not tried saving them in text files or printing them as of yet. When I get to that point I will come back to fill you in. Good luck with any of that, and if you have more fixes or ideas for this HowTo, feel free to add in or edit the steps!

S*

---

### Post by Bill Statler on 2008-05-31
Thanks for reincarnating this old thread, granny6989.

It looks like your solution (copy the fonts into an appropriate directory, then run [COLOR="DarkRed"]fc-cache -f -v[/COLOR]) is the way most people handle font installations.

Maybe I was the only person in history to have ever used dfontmgr!  And I'm still wondering exactly what use (if any) was made of all the information I manually entred for each font.

Well, dfontmgr is about to become obsolete, due to the elimination of libgtk-perl.  (More info here: [Debian Bug #282225 -- dfontmgr: still depends on gtk1 libraries - libgtk-perl and libglade-perl]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=282225"))

I'm setting up a new Ubuntu Hardy system for my wife this week (yay, another convert!), and I will probably use the fc-cache method to install fonts.  But if anyone is looking for a GUI font installer, here are two that I haven't tried:

[Fonty Python]("http://fontypython.webfactional.com/").  Here is [a review of a much earlier version]("http://www.linux.com/articles/114270").

[Fontmatrix]("http://fontmatrix.net/").  And [a review]("http://www.linux.com/feature/122156").

---

### Post by mpathy on 2009-01-21
Use fontypython - altough the source code of the program looks ugly, it is the best program out there for me.

You can use it via command line or via graphical user interface.

You work something similar like "Suitcase" - putting fonts into virtual font folders, which you can activate or deactivate.

Altough fontmatrix has the much better GUI, fontypython has the better commandline support.

But perhaps fontmatrix is more for gui people, it also has a tray icon..

---

### Post by ben2talk on 2009-02-12
sorry - software is out of date now!

Really what's needed is a way to copy fonts to the /usr/share/fonts folder automatically creating folders and dropping them in - can I do that?

---

### Post by granny6989 on 2009-07-18
Just added some fonts easily by changing permissions of my fonts folder, so that I can just drag and drop from the desktop. After that you open terminal and run the fc-cache command once, and you're all set.

Open terminal and type:

**sudo chown (user name) /usr/share/fonts**

or if you just use truetype, then:

**sudo chown (user name) /usr/share/fonts/truetype**

replace (user name) with your login name.
After that, just navigate to that folder on the desktop, and make folders, drop in files to your hearts content. Once you are all filled up, open terminal and use fc-cache. If you are worried about permission issues, then you can also change the ownership back to root when you're done.
S*

---

### Post by EricZartan on 2009-07-18
I found fonty python also ridiculously easy to use!
simple install with synaptic or apt-get and off you go!

E.:D

---

