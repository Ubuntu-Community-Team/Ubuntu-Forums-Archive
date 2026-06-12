---
title: "HOWTO: Emacs &amp; LaTeX"
date: 2005-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by Manny C on 2005-10-22
This is for all the lonely people, thinking that life has passed them by...
 _**EMACS**_[LIST=1]
[*]Download the attached emacsconf.tar.gz archive to your home directory. Then extract the attached .emacs and .Xresources file to ~/ ```
 tar zxvf emacsconf.tar.gz 
```
[*]Install emacs and associated packages:
```
sudo apt-get install emacs21 emacs-extra emacs-goodies-el emacs auctex preview-latex xfonts-jmk
``` (JMK Neep fonts are optional, but really good looking).[/LIST]**_LATEX_**[LIST=1]
[*]Install LaTeX
```
sudo apt-get install tetex-base tetex-extra
```
[*]Install dvi viewers (can install only one - use kdvi if you have kubuntu, o/w use xgdvi)
```
sudo apt-get install kdvi xgdvi 
```
[*]Read [The Not So Short Introduction to LaTeX]("http://ctan.unsw.edu.au/info/lshort/english/lshort.pdf")[/LIST]**_FINALISE_**
 Apply the .Xresources settings:
 ```
xrdb -merge .Xresources
``` **_LaTeX AWAY!_**
 Open Emacs, and TeX away.

(From Hoary Customisations & Tricks)

---

### Post by Zanza on 2005-10-22
[QUOTE=Manny C]Download the attached emacsconf.tar.gz archive to your home directory. Then extract the attached .emacs and .Xresources file to ~/ [/QUOTE]

I'm most likely missing something here, but I cannot find the attached file :confused:

---

### Post by Manny C on 2005-10-22
No. Actually, I forgot to attach this file. Thanks and fixed ;)

---

### Post by Zanza on 2005-10-22
I tried this procedure, but got the following error.

root@ubuntu:~/Desktop/Zanza# sudo apt-get install emacs21 emacs-extra emacs-goodies-el emacs-extra-goodies-el emacsauctex preview-latex xfonts-jmk
Reading package lists... Done
Building dependency tree... Done
Package emacs21 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs21 has no installation candidate

Any suggestions?

---

### Post by Manny C on 2005-10-22
Try
```
 sudo apt-get clean 
```
and then
```
 sudo apt-get update 
```

emacs21 should be in the main repositories.

---

### Post by LaserJock on 2005-10-22
Couple quick comments. First of all,> Restart your computer (I think this is necessary)
I don't see how that could be necessary. All you are doing is installing emacs. All you should need to do is ```
xrdb -merge .Xresources
``` to get the new .Xresources to take effect. At most, you should maybe logout and re-login.
Also,
- xfonts-jmk is optional (you should at least say that)
- emacs-goodies-el replaces emacs-extra-goodies-el (you have emacs-extra-goodies-el) so you should just have it.
- auctex instead emacsauctex
- instead of xdvi use xgdvi
- dvi2ps will convert dvi files to postscript files and is pretty important if you want to print or share your TeX output.

-LaserJock

---

### Post by Manny C on 2005-10-22
Ok. Thanks Laserjock.

---

### Post by Manny C on 2005-10-22
Oh. Incidentally, you don't need dvi2ps. You can use dvips command to convert dvi to ps if you so desire.

Never used dvi2ps.

---

### Post by samusz on 2005-10-22
Hi, 
if you want or need a more Wysiwyg way you can also use LyX et TeXmacs. Theses are great alternative to Emacs+AucTeX + preview-LaTeX, but not so much pur LaTeX:D
Cheers

---

### Post by Manny C on 2005-10-23
[quote=samusz]Hi, 
if you want or need a more Wysiwyg way you can also use LyX et TeXmacs. Theses are great alternative to Emacs+AucTeX + preview-LaTeX, but not so much pur LaTeX:D
Cheers[/quote] Or use whizzytex with advi viewer + emacs :0

This is a HOWTO for another day.

---

### Post by Gandalf on 2005-10-23
Why dont you use [texmaker](http://www.xm1math.net/texmaker/)? :roll:

---

### Post by Manny C on 2005-10-23
[quote=Gandalf]Why dont you use [texmaker]("http://www.xm1math.net/texmaker/")? :roll:[/quote]

Looks suspiciously like [Kile]("http://kile.sourceforge.net/").

And whats the fun of the fancy editor that is TeXmaker and Kile if you can use the power of Emacs? I guess I am just used to emacs.

---

### Post by Gandalf on 2005-10-23
[QUOTE=Manny C]Looks suspiciously like [Kile]("http://kile.sourceforge.net/").

And whats the fun of the fancy editor that is TeXmaker and Kile if you can use the power of Emacs? I guess I am just used to emacs.[/QUOTE]
What more powerfull in emacs you find other than it doesn't need X to run :roll:?

---

### Post by Manny C on 2005-10-23
The keybindings are awesome. C-c = gives me a table of contents so that I can easy navigate through a large file. C-c C-c allows be to either/and compile, view or bibtex. Almost never need a mouse. Labelling and referencing is supercool. All of these features come with auctex.

Doesn't use much ram and that I am used to it.

---

### Post by monkeyking on 2005-10-23
[QUOTE=Gandalf]What more powerfull in emacs you find other than it doesn't need X to run :roll:?[/QUOTE]
I have to agree with manny on this one.
There are only two widely available editors on this planet, and since emacs is one of them. It is reason enough to learn it.

---

### Post by dada1958 on 2005-10-25
[QUOTE=Manny C]No. Actually, I forgot to attach this file. Thanks and fixed ;)[/QUOTE]

There's still no emacsconf.tar.gz to download here :confused:

---

### Post by Manny C on 2005-10-26
[quote=dada1958]There's still no emacsconf.tar.gz to download here :confused:[/quote] Click on the filename on the bottom right hand corner of my original post ;)

---

### Post by dada1958 on 2005-10-26
[QUOTE=Manny C]Click on the filename on the bottom right hand corner of my original post ;)[/QUOTE]

Tnx...
When I want to start emacs21, I get this error:

:~$ emacs21
No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'

---

### Post by dada1958 on 2005-10-26
After logging in again emacs is running :)

---

### Post by Manny C on 2005-10-26
How do you like it?

---

### Post by benguin on 2005-10-30
Hey Manny,
Glad to see emacs/latex lovers are still around. I do need a few tips about using emacs+auctex. How do you (if you can) make a list of references from a bib file popup when you need to do a \cite? Similar question for \ref. 

Emacs still rocks, and by the looks of it will rock on for years.
-J-

---

### Post by Manny C on 2005-10-30
[quote=benguin]Hey Manny,
Glad to see emacs/latex lovers are still around. I do need a few tips about using emacs+auctex. How do you (if you can) make a list of references from a bib file popup when you need to do a \cite? Similar question for \ref. 

Emacs still rocks, and by the looks of it will rock on for years.
-J-[/quote] 
Great question and one that bothered me for a while until I read [this]("http://www.gnu.org/software/auctex/manual/auctex.pdf").

For \cite: Use the following keybinding: 
```
 C-c [ 
``` 
For \ref: Use the following keybinding:
```
 C-c ) 
``` 
You may need to parse the document every so often as auctex only scans the document once in a blue moon. To do this you need to do: Ref>Parse Document>One File.

Hope that helps.

---

### Post by rajan on 2005-11-20
i'm sure this post is stupid not only because i'm replying to a subject from 4 weeks ago, but also because of the question in general, but who cares -- i'll still ask.

 i tried the above instructions and i can't get the emacs command to work. there were two errors... first apparently the emacs extras wasn't found, and second the latex extras weren't found either. i don't see how these would have to anything to do with actually executing a command though (since extras should ostensibly be extra). no other errors came up.

i don't see any command when i type "which emacs" and i don't see any emacs files in the correct directories when i type "locate emacs". anyone know what i'm doing wrong? it still beats the hell out of windows though.

---

### Post by LaserJock on 2005-11-20
[QUOTE=rajan]i'm sure this post is stupid not only because i'm replying to a subject from 4 weeks ago, but also because of the question in general, but who cares -- i'll still ask.

 i tried the above instructions and i can't get the emacs command to work. there were two errors... first apparently the emacs extras wasn't found, and second the latex extras weren't found either. i don't see how these would have to anything to do with actually executing a command though (since extras should ostensibly be extra). no other errors came up.

i don't see any command when i type "which emacs" and i don't see any emacs files in the correct directories when i type "locate emacs". anyone know what i'm doing wrong? it still beats the hell out of windows though.[/QUOTE]

Make sure that you have them installed. Try :
```
sudo apt-get install emacs21 tetex-extra preview-latex
```
You should definently see something if you type "which emacs" and "which latex".

-LaserJock

---

### Post by rajan on 2005-11-20
Laserjock

tried that and the same thing happened. i do get a file in the /usr/bin for the latex command but still nothing for the emacs. i'm thinking it's prob the gzipped file, but it seems that i'm the first one to have a problem with this file. "whereis emacs" gives me 

emacs: /etc/emacs /usr/share/emacs

(i didn't do "whereis emacs" before, but i think nothing has changed)

EDIT: i'm a jackass. use synaptic. jesus. there are a few probs still, but it's better than trying to install everything manually.

---

### Post by Patsoe on 2005-11-23
Hi, thanks for listing all the interesting stuff associated with the tex-thing. I'm moving from a MikTex/WinEdt setup... haven't been on a Linux-based system for six years...

Just a question: the config files you list for download are optional, right? I can see what the .Xresources file does (it's short ;) ) - it sets window dimensions and font for Emacs, and that's about it, I believe?
The .emacs file is rather lengthy - could you perhaps summarize what it does that is not standard behaviour in Emacs/auctex?

(I know, I'm a bit neurotic about executing customizations...)

Thanks!

---

### Post by Manny C on 2005-11-27
[QUOTE=Patsoe]Hi, thanks for listing all the interesting stuff associated with the tex-thing. I'm moving from a MikTex/WinEdt setup... haven't been on a Linux-based system for six years...

Just a question: the config files you list for download are optional, right? I can see what the .Xresources file does (it's short ;) ) - it sets window dimensions and font for Emacs, and that's about it, I believe?
The .emacs file is rather lengthy - could you perhaps summarize what it does that is not standard behaviour in Emacs/auctex?

(I know, I'm a bit neurotic about executing customizations...)

Thanks![/QUOTE]
Config files are optional. But they make working with LaTeX much easier. You hit it straight on with regard to the .Xresources file. The .emacs file was shamelessly taken from a friend who got it from a friend, who got it from a friend, etc etc. I don't understand emacs lisp, so I don't know that I can help you there. Try looking through [Emacs Wiki]("http://www.emacswiki.org/cgi-bin/wiki") website and the [AucTeX]("http://www.gnu.org/software/auctex/") website for some great documentation on Emacs.

Rajan, what is in your /etc/apt/sources.list file? Please post it here.

---

### Post by baraider on 2005-11-27
thanks for the guide.

the fonts look a bit small for me on a dell 2005fpw screen (1680x1050) so i increase the font size and the emacs window size...

Here is what i have on my .Xresources file. I was able to increase the font on emacs text but not the menubar.... even at size 16, it was very difficult to see....what other fonts we can use instead of iso8859-1?

  xpdf*Geometry: 750x680+30+20
xpdf*initialZoom: width
Emacs*geometry: 100x64
*.font: -jmk-neep alt-medium-r-*-*-15-*-*-*-c-*-iso8859-1
Emacs.pane.menubar.font: -jmk-neep alt-medium-r-*-*-16-*-*-*-c-*-iso8859-1

---

### Post by Manny C on 2005-11-28
Run xfontsel. You can toy with X font settings.

---

### Post by Patsoe on 2005-11-28
[QUOTE=Manny C]...Try looking through [Emacs Wiki]("http://www.emacswiki.org/cgi-bin/wiki") website and the [AucTeX]("http://www.gnu.org/software/auctex/") website for some great documentation on Emacs...[/QUOTE]

Thanks, I'll do that!

---

### Post by rajan on 2005-12-03
[QUOTE=Manny C]
Rajan, what is in your /etc/apt/sources.list file? Please post it here.[/QUOTE]


deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe




sorry to muddy up the otherwise clear waters of this forum, but i'm still learning this OS. incidentally is there a reason that when i try to reinstall the OS from scratch using the same disk in good condition that i can't get past the part where you select a normal installation or server installation? finally is it bad to post questions that aren't on the subject of the thread?

rajan

Chuck Norris doesn't sleep. He waits.

---

### Post by Manny C on 2005-12-03
Hi Rajan

Since you are starting, some excellent online resources include:
[LIST=1]
[*][Ubuntu Document Storage Wiki]("http://doc.gwos.org/index.php/BreezyCust")   
[*][URL="https://wiki.ubuntu.com//FrontPage"]Official Ubuntu Wiki
    [/URL]   
[*][The Search Facility]("http://www.ubuntuforums.org/search.php") on this forum ;) [/LIST] With regards to your sources.list file, please see [this guide]("http://doc.gwos.org/index.php/Sources.list") on Doc Storage. 

With regard to your installation issue, I recommend that you post that on the [Installation and Upgrade Help Section]("http://www.ubuntuforums.org/forumdisplay.php?f=94") of the Forum.

Answering your last question in a word, yes. In full, see the [posting guidelines]("http://www.ubuntuforums.org/faq.php?faq=new_faq_item_gp#faq_new_faq_item").

---

### Post by rajan on 2005-12-03
great. thanks for the tips, Manny. i checked a lot of those things already (in addition to google and other web searches) but i think i'm going to completely reinstall and then use the synaptic manager. then hopefully i can get my system to resemble a problem that somebody has already had (instead of the horrible anomaly that it is now). thanks again for the tips.

---

### Post by Manny C on 2005-12-04
Thanks rajan.

---

### Post by rajan on 2005-12-06
GREAT!!! emacs works after installing via synaptic after a clean install!! not that anyone cares about this or anything, but i just thought i'd let everyone know. 

keep on rockin in the free world

---

### Post by jdk_ on 2005-12-20
hi, you can count one more happy user!
thanks a lot!

---

### Post by John.Michael.Kane on 2005-12-23
Thoes who want to install all this in one shot try this.. 
```
sudo apt-get install emacs21 emacs-extra emacs-goodies-el auctex preview-latex xfonts-jmk tetex-base tetex-extra preview-latex xgdvi

```

adjust to fit your needs

---

### Post by perthi on 2006-02-17
I tried all the above, but its not working for me. I cannot install emacs.
I always get this.

perthi@perthi-ubuntu:~$ sudo apt-get install emacs emacs-extra emacs-goodies-el emacs auctex preview-latex xfonts-jmk
Reading package lists... Done
Building dependency tree... Done
Package emacs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package emacs has no installation candidate


any suggestions

---

### Post by dada1958 on 2006-02-17
I had the same thing so I'm working with TeXMaker at this moment. I'm also working with TeXLive 2005 instead of the not so recent teTeX 2 that is still in the Ubuntu repositories.
You can find a HOW TO [here](http://www.ubuntuforums.org/showthread.php?p=744425#post744425).

---

### Post by John.Michael.Kane on 2006-02-22
This howto confirmed to work in dapper as of flight4... just a heads up for those who want to use it..

---

### Post by sherlock-holmes on 2006-06-06
could some one please tell me how to use emacs with texlive installation rather than the tetex/auctex thing?

---

### Post by dada1958 on 2006-06-06
I would be very pleased too, the development of teTeX has been terminated, there will be no next release...

---

### Post by Ferio on 2007-05-28
Auctex keeps working with TeXLive, all you've gotta do is uninstall old TeTeX and install TeXLive. If there's any problem, try uninstalling Auctex too, and then re-install it with TeXLive, I dunno if there are some dependencies changing.

---

### Post by ahrs19 on 2007-09-07
Thanks a lot for the very nice and clear instructions. It worked for me without any hassle:)

---

### Post by netimen on 2007-10-19
Auctex depends on tetex, so I can't install it with texlive. is there any way to do this?

---

### Post by bkelly on 2008-01-27
First, I did not see how to mark Manny C's post with a Thanks.  This is a couple of years old, but continues to be usefull to newbies.

This is in regards to installing Emacs version 22.1.1 into Gutsy 7.10 in an X 86 architecture, 64 bit.
During the install, my system popped up with the message:
.......................
you must run "apt-get install 10 emacs-extra/select-modes doesn't exist" to install theses languages support   

long description here...
........................
I find this odd on several counts.  Within the quoted command is the phrase "doesn's exist"   Would that really be part of a command?

What can I do with the phrase "long description here..."  I did not see how to get that long description.

A bit later in the install a window popped up containing a bunch of options to select.  One of them was Templates. I did not take the time to write them down and forgot the remainder.  Each option line began with a pair of brackets such as [ ] and the cursor could be moved up and down.  But I pressed Enter before figuring out how to enable the options.  How do I enable those options and how do I get back to the point of activating those options? 

Thanks for your time

---

### Post by qns8dn3 on 2008-11-04
I followed the first post and emacs (emacs-snapshot, which is emacs version 23.0.60.1) somehow got white text on black background and the *Messages* buffer says an error occured duging loading .emacs. I used the file .emacs from this post.

```
An error has occurred while loading `/home/la/.emacs':

Symbol's function definition is void: hscroll-global-mode
```

---

### Post by qns8dn3 on 2008-11-04
Ok i found a solution to black background problem. 

If you install emacs-extra as this HOWTO suggest, then emacs gets white text on black background destroying your emacs color customization. Uninstall emacs-extra.

There is another problem. Before following this HOWTO, I set up [my emacs to have antialiased fonts (Monospace-10)](http://psung.blogspot.com/2008/03/emacs-in-ubuntu-hardy-now-has-anti.html). After following this HOWTO, emacs fonts changed to something else. This problem persisted even after removing emacs-extra. Anybody with the same problem, add the following line to ~/.emacs :
```
(set-default-font "Monospace-10")
```
Add that line at the beginning, not at the end of .emacs file. That is because emacs won't read lines after the error line.

---

### Post by nikhil17 on 2009-05-05
Hi,

Not really sure if I am posting this in the right place but any help would be much appreciated......

I am fairly new to linux. I was trying to use emacs as editor for latex and so followed instructions in the tutorial here.

Everything seems to be alright so far but my fonts in emacs have become very small now (i.e after installations suggested above). I can change it for the session using options-set font but would appreciate a permanent fix.

I am using ubuntu 8.10

Thanks,
Nikhil

---

### Post by qns8dn3 on 2009-05-06
To change the font size of emacs, run it with -fn option:

```
$ emacs -fn 'Monospace-10'
```
or
```

$ emacs -fn 'Monospace-11'
```
or
```

$ emacs -fn 'Monospace-12'
```

'10,11,12' are sizes and 'Monospace' is the font name.

Or, add a line like the following to the file ~/.Xresources
```
Emacs.font: Monospace-10
```
, then either reboot the computer or just run the following command:

```
$ xrdb ~/.Xresources
```

---

### Post by nikhil17 on 2009-05-06
Thank you for offering to help. 
The first option gives this...

nikhil@nikhil-laptop:~$ emacs -fn 'Monospace-11'
No fonts match `Monospace-11'

And I am not sure how I would go about opening ~/.Xresources file or even the previous suggestion to add line to ~/.emacs (would it be etc/emacs )


nikhil@nikhil-laptop:~$ whereis emacs
emacs: /usr/bin/emacs /etc/emacs /usr/lib/emacs /usr/share/emacs /usr/share/man/man1/emacs.1.gz /usr/share/man/man1/emacs.1emacs22.gz /usr/share/man/man1/emacs.1emacs21.gz

---

### Post by nikhil17 on 2009-05-06
Now I really need help!
I tried the second option and get this .....

nikhil@nikhil-laptop:~$ nano  ~/.Xresources
nikhil@nikhil-laptop:~$ xrdb ~/.Xresources
nikhil@nikhil-laptop:~$ 
nikhil@nikhil-laptop:~$ emacs &
[1] 8361
nikhil@nikhil-laptop:~$ No fonts match `Monospace-10'

Additionally Emacs did not open.
My Xresource looks like:
xpdf*Geometry: 750x680+30+20
xpdf*initialZoom: width
Emacs*geometry: 100x98
*.font: -jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1
Emacs.pane.menubar.font: -jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1
Emacs.font: Monospace-10


Nikhil

---

### Post by qns8dn3 on 2009-05-07
I think Ubuntu have two kinds of font system.

The first system uses cryptic-looking font names like -jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1, and this is what's compatible with the current Emacs version (that is, emacs 22) in Ubuntu (which is installed by installing 'emacs' package). You can check emacs version by entering the following on the command line.

```
$ emacs --version
```

I am not really familiar with the first system. But this system also has very short font names like 6x13, 8x13 and 9x15. I believe the numbers stand for the font size.

To check how those fonts look, run xfd command like:

```
$ xfd -fn 6x13
```
```
$ xfd -fn 9x15
```

To see how emacs would look with those fonts, run emacs like:

```
$ emacs -Q -fn 9x15
```
```
$ emacs -Q -fn 8x13
```

The option -Q is there to tell emacs to skip loading the dotemacs file (~/.emacs) and some other.

If you decide you like the 8x13 font, then you can run

```
$ emacs -fn 8x13
```
or you can add the following to ~/.Xresources
```
Emacs.font:8x13
```

(BTW, you can edit ~/.Xresources and ~/.emacs with **Application > Accesories > Text Editor** or with Emacs by clicking on **File > Open...** and then typing **~/.Xresources** on the location bar that is on the Open Files window. Or open your Home Folder and press Control+H to reveal all hiddens files like **.emacs** and **.Xresources**)



The second font system uses font names like Monospace, Arial, Times New Roman, ... names you see in the usual font chooser windows. This is compatible with the new coming emacs version (emacs23), which can be installed by installing emacs-snapshot package. (then you open emacs23 by clicking on **Application > Accesories > Emacs-snapshot** or running the command ```
emacs-snapshot &
```) But the second system is incompatable with emacs22. What's good about using emacs23 with the second font system is that if you use Monospace-10 the font in Emacs23 will look the same as that in Text Editor.

```
$ emacs-snapshot -fn 'Monospace-10'
```

---

### Post by nikhil17 on 2009-05-10
Thanks... it seems these call different versions of emacs. The version command gives this:
GNU Emacs 22.2.1
Copyright (C) 2008 Free Software Foundation, Inc.

When I do just emacs or emacs & on the terminal emacs open in black background while when I use any of your commands (with - Q) it opens in white background and correct font. Additionally with your command dired is functional but I would like to open emacs independent of the terminal window. 
Would appreciate pointers.

Nikkhil

---

### Post by qns8dn3 on 2009-05-12
For the black background problem, see post #48 in this thread.

> **nikhil17 said:**
> ... Additionally with your command dired is functional but I would like to open emacs independent of the terminal window. 
Would appreciate pointers.

1. The terminal can be closed by entering Ctrl+D on the command line. So if you enter **emacs -fn blahblah &** and then enter Ctrl+D, the terminal window is closed and the emacs window is still there, on the other hand, if you closed the terminal by pressing the X button, the emacs would have crashed.

2. Or press Alt+F2 and enter **emacs --any-long-option**

3. Or you can use a launcher. To create a launcher, right click on the top panel, click 'Add to Panel...', select 'Custom Application launcher', click 'Add' button, type your command in the command field. A related screenshot is at the end of my [rdesktop tutorial](http://ubuntuforums.org/showthread.php?t=824710)

4. Or right click on **Applications Places System** and click on **Edit menus** and add a launcher there.

---

### Post by nikhil17 on 2009-05-12
Thanks, those help. To work the dired (bad idea) I tried uninstalling everything and reinstalling again followed directions on the first page here....but now on terminal emacs & gives this:

nikhil@nikhil-laptop:~$ emacs &
[2] 7292
nikhil@nikhil-laptop:~$ No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'[

Any suggestions, why emacs won't load up directory now even with your suggested command to open emacs?

Although as you can see from [2] I can open emacs as per your suggestion but dired not working.

Thank you again for your time.

---

### Post by qns8dn3 on 2009-05-12
I have no clue why dired is not working in your case. 

Running emacs with -Q option means not loading ~/.emacs and site startup files. Site startup files comes from emacs related packages installed from Synaptic or apt-get (such as AUCTeX). 
Running emacs with -q option means not loading ~/.emacs

By running emacs with -Q option and then with -q option, you can guess whether the problem comes from ~/.emacs or from some site starup file.

If the problem is from ~/.emacs, you can find which part of the ~/.emacs is responsible by running emacs with -q option and opening ~/.emacs and then evaluating/executing each elisp line one by one.

---

### Post by nikhil17 on 2009-05-12
Well, as I mentioned the only way emacs runs is if I do: $emacs -fn 8x13 &
.....not if I do either $emacs -Q or $emacs -q. Incidentally they both give same message:  
nikhil@nikhil-laptop:~$ emacs -Q
No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'
nikhil@nikhil-laptop:~$ emacs -q
No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'
nikhil@nikhil-laptop:~$ 

Moreover, $nano ~\.emacs shows empty file though not $nano \.emacs , in case that gives you any idea about resolving this. Irrespective of that, thanks...you have been great help.

---

### Post by qns8dn3 on 2009-05-13
> $nano ~\.emacs shows empty file though not $nano \.emacs , in case that gives you any idea about resolving this.

You mean ~/.emacs and /.emacs not ~\.emacs and \.emacs?
The symbol ~ represents your home directory. (see [Files Directories Commands](https://help.ubuntu.com/8.04/basic-commands/C/files-directories-commands.html) and [Linux Filesystem and paths](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)). So **~/.emacs** is the file named **.emacs** in your home directory, which can be found by going to **Places -> Home Folder** and pressing Ctrl+H to reveal all hidden files with their name starting with a dot. **/.emacs** is the file named **.emacs** in your Root directory, the first / in a path means the root directory, which you can access by entering / in the Location bar in your File Browser. 

**~/.emacs** is the one you should use, this is your configuration file for your Emacs, Emacs users usually google for dotemacs (they call ~/.emacs dotemacs) and find out what others have put on their dotemacs and copy & paste some back into their own dotemacs files. The [online AUCTeX manual](http://www.gnu.org/software/auctex/manual/auctex/index.html) will often tell you to put some code to your dotemacs file to configure AUCTeX in some way. So you usually copy some code and open the file **~/.emacs** in your Emacs and paste the code there and execute the part you've just pasted by selecting the part (with mouse) and clicking on **Emacs-Lisp -> Evaluate Region** in order to check the code actually works, and then save the file.


> Well, as I mentioned the only way emacs runs is if I do: $emacs -fn 8x13 &
.....not if I do either $emacs -Q or $emacs -q. Incidentally they both give same message:  
nikhil@nikhil-laptop:~$ emacs -Q
No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'
nikhil@nikhil-laptop:~$ emacs -q
No fonts match `-jmk-neep alt-medium-r-*-*-11-*-*-*-c-*-iso8859-1'
nikhil@nikhil-laptop:~$ 


Maybe these will work then.
```
$ emacs -Q -fn 8x13
```
```
$ emacs -q -fn 8x13
```

---

### Post by nikhil17 on 2009-05-13
Thanks.
Yes I do mean / but was surprised to find no difference in output even if it put "\"?
$emacs -Q -fn 8x13 and $emacs -q -fn 8x13 worked and allows me to load dired but could not detect the problem.

About evaluating the command using evaluate region.....was trying with my current problematic .emacs file. How would I go about evaluating it? I tried doing so but the output in the echo area did not give anything 'unusal' for my untrained eyes! Suggestions?

---

### Post by GrouchoMarx on 2009-05-13
If Xresources is too much trouble, you can also set your font in your .emacs file with the following two lines:
> 
(setq default-frame-alist (append '((font . "Bitstream Vera Sans Mono-10")) default-frame-alist))
(setq initial-frame-alist (append '((font . "Bitstream Vera Sans Mono-10")) initial-frame-alist))

The first line sets the default font for all frames, while the second line sets the font for the initial frame. There are many other parameters that you can set using alists.

---

### Post by qns8dn3 on 2009-05-14
Let's consider the following example of dotemacs file.

```

;; ~/.emacs start

(defun smart-beginning-of-line ()
  "Move point to first non-whitespace character or beginning-of-line.

Move point to the first non-whitespace character on this line.
If point was already at that position, move point to beginning of line."
(interactive)
(let ((oldpos (point)))
(back-to-indentation)  ; alternative behavior here : (beginning-of-line-text).
(and (= oldpos (point))
(beginning-of-line))))

(global-set-key [home] 'smart-beginning-of-line)

  (dolist (hook '(erc-mode-hook
  emacs-lisp-mode-hook
  text-mode-hook))
  (add-hook hook (lambda () (abbrev-mode 1))))

(setq 'sodisjdf sodfijaodf)

;; make % go to the matching paren
(global-set-key "%" 'match-paren)
(defun match-paren (arg)
  "Go to the matching paren (like vi) if on a paren; otherwise insert %."
  (interactive "p")
  (cond ((looking-at "\\s\(") (forward-list 1) (backward-char 1))
	((looking-at "\\s\)") (forward-char 1) (backward-list 1))
	(t (self-insert-command (or arg 1)))))

;; ~/.emacs ends here.

```

Open emacs with -q option.
$ emacs -q -fn 8x13

Then open the dotemacs file (C-x C-f ~/.emacs)

Before evaluating it, see that the last code chunk of the example dotemacs, which is

```

;; make % go to the matching paren
(global-set-key "%" 'match-paren)
(defun match-paren (arg)
  "Go to the matching paren (like vi) if on a paren; otherwise insert %."
  (interactive "p")
  (cond ((looking-at "\\s\(") (forward-list 1) (backward-char 1))
	((looking-at "\\s\)") (forward-char 1) (backward-list 1))
	(t (self-insert-command (or arg 1)))))

```

, looks properly indented while the rest of the code is not well indented, which is usually the case if you paste some code from a blog post.


This part
```

  (dolist (hook '(erc-mode-hook
  emacs-lisp-mode-hook
  text-mode-hook))
  (add-hook hook (lambda () (abbrev-mode 1))))

```
have all lines indented with two spaces, and that's not a good indentation. emacs will run this part of code fine without error because emacs code interpreter doesn't care about bad indentation. On the other hand, humans find it hard to read such badly indented code. To properly indent this part of code, select it (with mouse) and then indent the region (**Emacs-Lisp -> Indent Region**).

The result should be like this
```

(dolist (hook '(erc-mode-hook
		emacs-lisp-mode-hook
		text-mode-hook))
  (add-hook hook (lambda () (abbrev-mode 1))))

```

If you indent the entire code properly (**Edit -> Select All** and then indent region), you will have this

```

;; ~/.emacs start

(defun smart-beginning-of-line ()
  "Move point to first non-whitespace character or beginning-of-line.

Move point to the first non-whitespace character on this line.
If point was already at that position, move point to beginning of line."
  (interactive)
  (let ((oldpos (point)))
    (back-to-indentation)  ; alternative behavior here : (beginning-of-line-text).
    (and (= oldpos (point))
	 (beginning-of-line))))

(global-set-key [home] 'smart-beginning-of-line)

(dolist (hook '(erc-mode-hook
		emacs-lisp-mode-hook
		text-mode-hook))
  (add-hook hook (lambda () (abbrev-mode 1))))

(setq 'sodisjdf sodfijaodf)

;; make % go to the matching paren
(global-set-key "%" 'match-paren)
(defun match-paren (arg)
  "Go to the matching paren (like vi) if on a paren; otherwise insert %."
  (interactive "p")
  (cond ((looking-at "\\s\(") (forward-list 1) (backward-char 1))
	((looking-at "\\s\)") (forward-char 1) (backward-list 1))
	(t (self-insert-command (or arg 1)))))

;; ~/.emacs ends here.

```

Now this looks better and now you can see which lines belongs which chunk and you know where not to divide the code. In the following code, I've divided the code into five parts from PART 1 to PART 5.

```

;; ~/.emacs start

;; BEGGINING OF PART 1
(defun smart-beginning-of-line ()
  "Move point to first non-whitespace character or beginning-of-line.

Move point to the first non-whitespace character on this line.
If point was already at that position, move point to beginning of line."
  (interactive)
  (let ((oldpos (point)))
    (back-to-indentation)  ; alternative behavior here : (beginning-of-line-text).
    (and (= oldpos (point))
	 (beginning-of-line))))
;; END OF PART 1

;; BEGGINING OF PART 2
(global-set-key [home] 'smart-beginning-of-line)
;; END OF PART 2

;; BEGGINING OF PART 3
(dolist (hook '(erc-mode-hook
		emacs-lisp-mode-hook
		text-mode-hook))
  (add-hook hook (lambda () (abbrev-mode 1))))
;; END OF PART 3

;; BEGGINING OF PART 4
(setq 'sodisjdf sodfijaodf)
;; END OF PART 4

;; BEGGINING OF PART 5
;; make % go to the matching paren
(global-set-key "%" 'match-paren)
(defun match-paren (arg)
  "Go to the matching paren (like vi) if on a paren; otherwise insert %."
  (interactive "p")
  (cond ((looking-at "\\s\(") (forward-list 1) (backward-char 1))
	((looking-at "\\s\)") (forward-char 1) (backward-list 1))
	(t (self-insert-command (or arg 1)))))
;; END OF PART 5

;; ~/.emacs ends here.

```

This example actually contains a line causing an error, i.e. if your dotemacs file is this and you start emacs without -q option, it will say something like
```

Warning (initialization): An error occurred while loading `/home/fj/.emacs':

Symbol's value as variable is void: sodfijaodf

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

```

The error message mentions sodfijaodf, so the problematic line is **(setq 'sodisjdf sodfijaodf)**, but let's pretend that we didn't see such descriptive error message, how should I find which part from PART 1 to PART 5 is responsible?

I select PART 1 and evaluate region, I see no error, and then I select PART 2 and evaluate region, and so on, ... when I select PART 4 and evaluat region, it beeps (or it flashes if you disabled beeping), and in the minibuffer at the bottom it says: 
**Symbol's value as variable is void: sodfijaodf**
, so I see that PART 4 is what I need to fix or delete.

If your dotemacs file is pretty big (like 2000 lines of code), the above way of selecting and evaluating task will take a lot of time. In that case, you should divide the code to bigger chunks and then divide the problematic chunk into smaller chunks and so on. Suppose your dotemacs file contains 2000 lines of code, and you suspect the first 1000 line is not responsible for the error but you don't know which of the last 1000 line is responsible. You first evaluate the first 1000 lines. Then evaluate the next 100 lines and then the next 100 lines and so on. (Actually since you should know where not to cut the code, it'll be more like "next 103 lines, next 94 lines, next 110 lines, ...") 

Suppose you found the part (consisting of about 100 lines) causing error. To find out which part among the 100 lines of code is responsible, restart emacs again with -q option, open dotemacs again, and select the region starting from the first line of the entire dotemacs code and ending just above the start of the problematic 100 lines of code. Evaluate that region. It should cause no error. Now evaluate the next 10 lines of code and then the next 10 lines of code and so on.

In your case, is your problem doing **M-x dired** and nothing happening? If that's the case, I would evaluate the first half of dotemacs and try **M-x dired**. If dired loads, then the problem is in the last half of dotemacs, then I would proceed to evaluate the first half part of the last half of dotemacs and try M-x dired again.

---

### Post by nikhil17 on 2009-05-15
Thank you for very clear instruction. Unfortunately, I was not able to find the problems....actually I found two but more of that later. I am pasting below my faulty .emacs file with some extra comments where I get errors (was hesitent about pasting so much stuff!). However, even in portions that I do not get any error (for instance take the first two lines), C-x d still will not load dired!

In addition when closing using C-x C-c it always asks:
Delete excess backup versions of /home/nikhil/.recenf? (y or n)

Thank you for your patience and help.

My .emacs file:
;; Red Hat Linux default .emacs initialization file
(setq load-path (cons "/usr/share/emacs-snapshot/site-lisp/" load-path))
;; Are we running XEmacs or Emacs?
(defvar running-xemacs (string-match "XEmacs\\|Lucid" emacs-version))

;; Set up the keyboard so the delete key on both the regular keyboard
;; and the keypad delete the character under the cursor and to the right
;; under X, instead of the default, backspace behavior.
(custom-set-variables
  ;; custom-set-variables was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 '(case-fold-search t)
 '(current-language-environment "English")
 '(default-input-method "rfc1345")
 '(global-font-lock-mode t nil (font-lock))
 '(recentf-max-saved-items 80)
 '(show-paren-mode t nil (paren))
 '(text-mode-hook (quote (turn-on-auto-fill text-mode-hook-identify)))
 '(transient-mark-mode t))


 '(text-mode-hook (quote (turn-on-auto-fill text-mode-hook-identify)))
 '(transient-mark-mode t))

;; Turn on font-lock mode for Emacs
(cond ((not running-xemacs)
       (global-font-lock-mode t)
))

;; Visual feedback on selections
(setq-default transient-mark-mode t)

;; Always end a file with a newline
(setq require-final-newline t)

;; Stop at the end of the file, not just add lines
(setq next-line-add-newlines nil)

;; Preload AucTex
(load "tex-site")

;; save-history
;;(load "save-history")

(require 'recentf)
(recentf-mode 1)

(add-hook 'dired-load-hook
          (lambda () (require 'dired-sort-menu)))

(fset 'yes-or-no-p 'y-or-n-p)

(cond ((fboundp 'global-font-lock-mode)
       ;; Turn on font-lock in all modes that support it
       (global-font-lock-mode t)
       ;; Maximum colors
       (setq font-lock-maximum-decoration t)))
;; save-history
;;(load "save-history")

(require 'recentf)
(recentf-mode 1)

(add-hook 'dired-load-hook
          (lambda () (require 'dired-sort-menu)))

(fset 'yes-or-no-p 'y-or-n-p)

(cond ((fboundp 'global-font-lock-mode)
       ;; Turn on font-lock in all modes that support it
       (global-font-lock-mode t)
       ;; Maximum colors
       (setq font-lock-maximum-decoration t)))
(setq column-number-mode t)
(setq line-number-mode t)


(c-set-offset 'case-label '+) ;; switch indenting in C
(hscroll-global-mode t)

;;;;;;########get error above:Symbol function's definition is void:hscroll-global-mode	

;;;(define-key global-map [menu-bar mule] nil)
(custom-set-faces
  ;; custom-set-faces was added by Custom -- don't edit or cut/paste it!
  ;; Your init file should contain only one such instance.
 )
;(setq-default auto-fill-function 'do-auto-fill)
;(global-set-key "\C-co" 'other-frame)
;(add-to-list 'auto-mode-alist '("\\.pm\\'" . cperl-mode))
;(add-to-list 'auto-mode-alist '("\\.pl\\'" . cperl-mode))
(dynamic-completion-mode)

;(desktop-load-default)
;(desktop-read)

(setq visible-bell t)
(put 'upcase-region 'disabled nil)

(put 'downcase-region 'disabled nil)
;(global-set-key "\C-xb" `buffer-menu)
;(global-set-key [(C-TAB)] `ispell-complete-word)

; get rid of the toolbar with graphical file save/open/etc/buttons
(tool-bar-mode -1)

; get rid of the menu bar
;(menu-bar-mode -1)
;;;;	Problem above section-get this message: Symbol's section definition is void:hscroll-global-mode

;;; Emacs/W3 Configuration
;(setq load-path (cons "/c/mproper/.elisp/" load-path))
;(condition-case () (require 'w3-auto "w3-auto") (error nil))

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;; LATEX  ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;; AUCTEX-11.14
(require 'tex-site)
(setq TeX-auto-save t)
(setq TeX-parse-self t)

;; preview-latex
(load "/usr/share/emacs/site-lisp/preview-latex/preview-latex.el" nil t t)
(add-hook 'LaTeX-mode-hook #'LaTeX-preview-setup)
(autoload 'LaTeX-preview-setup "preview")
(load "tex-site")
;;;;;;;;######### get error with this section of preview-latex !
;;;;;;;; problem in the above section (where ;;;;;;LATEX;;;;;;; starts)
;;;;;;;; gives this error message: Cannot open load file: /usr/share/emacs/site-lisp/preview-latex.el

;; whizzytex
;;(setq load-path (cons "/usr/local/share/whizzytex/lisp" load-path))
;;(autoload 'whizzytex-mode
;;  "whizzytex"
;;  "WhizzyTeX, a minor-mode WYSIWIG environment for LaTeX" t)

;; bib-find
;;(autoload 'bibfind "bibfind" "Search for BibTeX entries on the web" t)

;; RefTeX
(autoload 'reftex-mode    "reftex" "RefTeX Minor Mode" t)
(autoload 'turn-on-reftex "reftex" "RefTeX Minor Mode" nil)
(add-hook 'LaTeX-mode-hook 'turn-on-reftex)   ; with AUCTeX LaTeX mode
(setq reftex-enable-partial-scans t)
(setq reftex-save-parse-info t)
(setq reftex-use-multiple-selection-buffers t)
(setq reftex-plug-into-AUCTeX t)
(setq bib-cite-use-reftex-view-crossref t)


(add-hook 'LaTeX-mode-hook 'LaTeX-math-mode t)
;; bib-cite
;;(autoload 'turn-on-bib-cite "bib-cite")
;;(add-hook 'LaTeX-mode-hook 'turn-on-bib-cite)
;;(setq bib-novice nil)

(add-hook 'LaTeX-mode-hook 'whizztex-mode t)
(autoload 'reftex-mode    "reftex" "RefTeX Minor Mode" t)
(autoload 'turn-on-reftex "reftex" "RefTeX Minor Mode" nil)
(add-hook 'LaTeX-mode-hook 'turn-on-reftex)   ; with AUCTeX LaTeX mode
(setq reftex-enable-partial-scans t)
(setq reftex-save-parse-info t)
(setq reftex-use-multiple-selection-buffers t)
(setq reftex-plug-into-AUCTeX t)
(setq bib-cite-use-reftex-view-crossref t)


(add-hook 'LaTeX-mode-hook 'LaTeX-math-mode t)
;; bib-cite
;;(autoload 'turn-on-bib-cite "bib-cite")
;;(add-hook 'LaTeX-mode-hook 'turn-on-bib-cite)
;;(setq bib-novice nil)

(add-hook 'LaTeX-mode-hook 'whizztex-mode t)
;; bib-cite
;;(autoload 'turn-on-bib-cite "bib-cite")
;;(add-hook 'LaTeX-mode-hook 'turn-on-bib-cite)
;;(setq bib-novice nil)

(add-hook 'LaTeX-mode-hook 'whizztex-mode t)

(add-hook 'TeX-mode-hook   'turn-on-auto-fill)
;;(load 'font-latex)

(add-hook 'TeX-mode-hook   'turn-on-auto-fill)

;; (add-hook 'LaTeX-mode-hook 'flyspell-mode)
;; (add-hook 'TeX-mode-hook 'flyspell-mode)

---

### Post by qns8dn3 on 2009-05-15
```

;; AUCTEX-11.14
(require 'tex-site)
(setq TeX-auto-save t)
(setq TeX-parse-self t)

;; preview-latex
(load "/usr/share/emacs/site-lisp/preview-latex/preview-latex.el" nil t t)
(add-hook 'LaTeX-mode-hook #'LaTeX-preview-setup)
(autoload 'LaTeX-preview-setup "preview")
(load "tex-site")
;;;;;;;;######### get error with this section of preview-latex !
;;;;;;;; problem in the above section (where ;;;;;;LATEX;;;;;;; starts)
;;;;;;;; gives this error message: Cannot open load file: /usr/share/emacs/site-lisp/preview-latex.el

```

The error message indicates the error line is:
```

(load "/usr/share/emacs/site-lisp/preview-latex/preview-latex.el" nil t t)

```

Now need to see what (load ...) is supposed to do.

The Emacs manual, which can be read [on the web (HTML)](http://www.gnu.org/software/emacs/manual/html_node/emacs/index.html) or from **Help -> Read The Emacs manual**, has section named Help explaining how to get Help within emacs, and one of the things it mentions is **C-h f**.

So enter **C-h f load** to read about what the function "load" does and you can see that the problem is probably that the file /usr/share/emacs/site-lisp/preview-latex/preview-latex.el doesn't exist. 

If you search preview-latex in Synaptic Package Manager, you'll find that preview-latex is part of auctex and you've already installed auctex, havent' you? If auctex is installed, then preview-latex is also installed. So the file preview-latex.el must be somewhere on your system, though it's definitely not on the path specified in the error line. To find where it is, you can enter following in the command line:

```
$ locate preview-latex.el
```

But for a minute let's pretend that we don't know the command **locate**.

To find how to fix it, we should first find and read Introduction of preview-latex manual or AUCTeX manual, HTML version of which can be found on the AUCTeX homepage. Introduction of preview-latex manual says that one should use
```
(load "preview-latex.el" nil t t)
```
to activate preview-latex. So you need to replace the problematic line with that line. In this way, you don't have to specify the full path of the file preview-latex.el.

```

(hscroll-global-mode t)

;;;;;;########get error above:Symbol function's definition is void:hscroll-global-mode

```

Googling hscroll-global-mode, you will find that **hscroll.el** must be installed to use hscroll-global-mode. The file hscroll.el contains a line saying:
```
;; This file is part of GNU Emacs.
```
which usually means that the emacs package (in this case, hscroll) comes built-in with GNU emacs so that you don't have to install it yourself, and that you just need to add the line ```
(require 'hscroll)
``` before/above the line ```
(hscroll-global-mode t)
``` in your dotemacs file. 

But that doesn't work. If you evaluate (require 'hscroll), emacs says "cannot open load file: hscroll". So it turns out hscroll is not built-in. Confusing.

Nevertheless, the hscroll's feature seems to be already in Emacs (at least in emacs version 23, which is what I use.). So you can delete the line ```
(hscroll-global-mode t)
``` without losing anything.

BTW you might want to toggle-truncate-lines a lot (many emacsers do), the following line will assign toggle-truncate-lines to the key **C-c w**.
```
(global-set-key (kbd "\C-c w") 'toggle-truncate-lines)
```


```

;; Red Hat Linux default .emacs initialization file
(setq load-path (cons "/usr/share/emacs-snapshot/site-lisp/" load-path))
;; Are we running XEmacs or Emacs?
(defvar running-xemacs (string-match "XEmacs\\|Lucid" emacs-version))

```

Let me see if I am getting this right.

1. If you start emacs with -q option and open your dotemacs and then press **C-x d**, emacs DOES load dired

2. If you start emacs with -q option and then evaluate the line **(setq load-path (cons "/usr/share/emacs-snapshot/site-lisp/" load-path))**, then **C-x d** does NOT load dired.

Both 1 and 2 are true?

---

### Post by nikhil17 on 2009-05-15
I made the changes you suggested above (and spent some time on the online manual as well)....now emacs evaluation doesn't give any errors but the original problems persist namely:

1. emacs will not open with $ emacs &
   I still have to give it -fn option
2. C-x d does NOT load dired in any case. In the previous reply I meant even if I use the top two lines of .emacs and try C-x d, it does not work. Basically under no circumstance does dired open!

Obviously the latter is more of an issue for me.
Thanks.

---

### Post by qns8dn3 on 2009-05-16
> 
1. emacs will not open with $ emacs &
   I still have to give it -fn option


**Help -> Emacs Known Problems** contains this item
> 
* Emacs startup failures

** Emacs fails to start, complaining about missing fonts.

A typical error message might be something like

  No fonts match `-*-fixed-medium-r-*--6-*-*-*-*-*-iso8859-1'

This happens because some X resource specifies a bad font family for
Emacs to use.  The possible places where this specification might be
are:

  - in your ~/.Xdefaults file

  - client-side X resource file, such as  ~/Emacs or
    /usr/X11R6/lib/app-defaults/Emacs or
    /usr/X11R6/lib/X11/app-defaults/Emacs

One of these files might have bad or malformed specification of a
fontset that Emacs should use.  To fix the problem, you need to find
the problematic line(s) and correct them.
 

I would settle on using -fn (or specifying it on ~/.Xresource) because fixing it as suggested looks like a  complicated job. I use emacs-snapshot with -fn 'Monospace-8' option.


> 
2. C-x d does NOT load dired in any case. In the previous reply I meant even if I use the top two lines of .emacs and try C-x d, it does not work. Basically under no circumstance does dired open!


Is dired installed? Ubuntu package emacs-goodies-el contains a lot of emacs add-ons and one of them is dired.

---

### Post by nikhil17 on 2009-05-18
I would settle on using -fn (or specifying it on ~/.Xresource) because fixing it as suggested looks like a  complicated job. I use emacs-snapshot with -fn 'Monospace-8' option.
[/QUOTE]

Yes, -fn 8x13 is good enough for me.

Is dired installed? Ubuntu package emacs-goodies-el contains a lot of emacs add-ons and one of them is dired.[/QUOTE]

Well, I know emacs-goodies-el is installed. I am assuming dired should then be installed. Is there a way to check if dired is?

Thanks

---

### Post by qns8dn3 on 2009-05-18
> Well, I know emacs-goodies-el is installed. I am assuming dired should then be installed. Is there a way to check if dired is?



Maybe using the locate command can help.

My result for locate dired.el is 

```

$ locate dired.el
/usr/share/emacs/23.0.60/lisp/dired.el.gz
/usr/share/emacs/23.0.60/lisp/dired.elc
/usr/share/emacs/23.0.60/lisp/epa-dired.el.gz
/usr/share/emacs/23.0.60/lisp/epa-dired.elc
/usr/share/emacs/23.0.60/lisp/find-dired.el.gz
/usr/share/emacs/23.0.60/lisp/find-dired.elc
/usr/share/emacs/23.0.60/lisp/image-dired.el.gz
/usr/share/emacs/23.0.60/lisp/image-dired.elc
/usr/share/emacs/23.0.60/lisp/wdired.el.gz
/usr/share/emacs/23.0.60/lisp/wdired.elc
/usr/share/emacs/23.0.60/lisp/gnus/gnus-dired.el.gz
/usr/share/emacs/23.0.60/lisp/gnus/gnus-dired.elc
/usr/share/emacs/23.0.60/lisp/url/url-dired.el.gz
/usr/share/emacs/23.0.60/lisp/url/url-dired.elc
/usr/share/emacs/site-lisp/emacs-goodies-el/wdired.el
```

And ascii is another emacs package included in emacs-goodies-el. My result for locate ascii.el is

```

$ locate ascii.el
/usr/share/emacs/23.0.60/lisp/international/iso-ascii.el.gz
/usr/share/emacs/23.0.60/lisp/international/iso-ascii.elc
/usr/share/emacs/site-lisp/emacs-goodies-el/ascii.el
/usr/share/emacs-snapshot/site-lisp/emacs-goodies-el/ascii.el
/usr/share/emacs-snapshot/site-lisp/emacs-goodies-el/ascii.elc
```


If dired is installed properly, emacs should be able to evaluate the following without error

```
(require 'dired)
```

To check if it's just dired or if ascii emacs package is also broken:
```
(require 'ascii)
```

If locate command finds dired.el (or dired.elc) and **(require 'dired)** fails, then the relevant path is not in the emacs variable **load-path**. You can check the value and the description of the variable by pressing **C-h v** and entering **load-path**.

If locate command does not find dired.el nor dired.elc, then check (to be sure) if locate command itself is broken by entering **locate xorg** on the command line. The result should be a very long list if locate is working.

---

### Post by nikhil17 on 2009-05-19
Locate does find both so I guess I need to add the path in my .emacs but which ones or should it be the directory? Like your output my output for locate gives several and emacs documentation says to add using...
(setq load-path (cons "/dir/subdir/" load-path))

My output for locate was:
/usr/share/emacs/22.2/lisp/dired.el.gz
/usr/share/emacs/22.2/lisp/dired.elc
/usr/share/emacs/22.2/lisp/find-dired.el.gz
/usr/share/emacs/22.2/lisp/find-dired.elc
/usr/share/emacs/22.2/lisp/image-dired.el.gz
/usr/share/emacs/22.2/lisp/image-dired.elc
/usr/share/emacs/22.2/lisp/wdired.el.gz
/usr/share/emacs/22.2/lisp/wdired.elc
/usr/share/emacs/22.2/lisp/gnus/gnus-dired.el.gz
/usr/share/emacs/22.2/lisp/gnus/gnus-dired.elc
/usr/share/emacs/22.2/lisp/url/url-dired.el.gz
/usr/share/emacs/22.2/lisp/url/url-dired.elc
/usr/share/emacs/23.0.60/lisp/dired.elc
/usr/share/emacs/23.0.60/lisp/epa-dired.elc
/usr/share/emacs/23.0.60/lisp/find-dired.elc
/usr/share/emacs/23.0.60/lisp/image-dired.elc
/usr/share/emacs/23.0.60/lisp/wdired.elc
/usr/share/emacs/23.0.60/lisp/gnus/gnus-dired.elc
/usr/share/emacs/23.0.60/lisp/url/url-dired.elc
/usr/share/emacs/site-lisp/emacs-goodies-el/wdired.el

---

### Post by qns8dn3 on 2009-05-19
In your case, dired is in the following two directories

/usr/share/emacs/22.2/lisp/
/usr/share/emacs/23.0.60/lisp/

The latter is for emacs version 23.0.60, if you use emacs22, then you want to add the former. So the code should be

```
(setq load-path (cons "/usr/share/emacs/22.2/lisp/" load-path))
```

---

### Post by nikhil17 on 2009-05-19
I added the above command and it evaluates fine but still can not make dired work (after restarting as well)! Any suggestions?

---

### Post by qns8dn3 on 2009-05-19
What if you add **(require 'dired)** as well?



```

(setq load-path (cons "/usr/share/emacs/22.2/lisp/" load-path))
(require 'dired)

```

---

### Post by nikhil17 on 2009-05-19
Yes it works! Great thanks for pointing that out. Thanks a ton for all the help!

---

### Post by beefinit on 2009-07-09
This made the default font size in my emacs redonculously small and I can't see it! How do I increase the font size (menus too)?

Answered my own question: went to .Xresources file and changed the defaults

---

### Post by mnajem on 2009-10-05
Hello,

I want to know how to create split emacs screen for real time Latex ouput, which
is something like this:

[http://www.emacswiki.org/pics/static/LaTeXMathPreviewScreenshot.png](http://www.emacswiki.org/pics/static/LaTeXMathPreviewScreenshot.png)

I tried:
Auctex - this one using internal output
Whizzytex- this use ADVI output
Yatex - plan to use latex-math-preview (using default install in Ubuntu apt-get
install yatex), but can't managed to get it work.

Can you guys lead me?

Also can emacs with -nw flag append that in its screen? Since currently I'm
using plain console.

---

### Post by unutbu on 2009-10-05
mnajem, I do not know of a real-time LaTeX previewer within emacs, but who knows? one may exist. However, there is a way to have Linux monitor a directory so that whenever a (tex) file is modified latex is run. Given such a setup, you could simply organize your screen to have "emacs -nw" running in a terminal on one half, and "xdvi" or some other viewer running on the other half. 

Would you be interested in this?

---

### Post by mnajem on 2009-10-05
> **unutbu said:**
> mnajem, I do not know of a real-time LaTeX previewer within emacs, but who knows? one may exist. However, there is a way to have Linux monitor a directory so that whenever a (tex) file is modified latex is run. Given such a setup, you could simply organize your screen to have "emacs -nw" running in a terminal on one half, and "xdvi" or some other viewer running on the other half. 

Would you be interested in this?

Currently for DVI viewing (almost realtime, since I realized it use background compiling)

Emacs + Whizzytex -> I have to enter whizzytex mode.. this is is marvellous :: similar with what you did suggest.

Emacs + AucTex -> The view done within the Tex inline.. however if I want to view the Arabtex it does not work.

:-)

I found VIM workaround has been done too (I also used to VI, but since Emacs offering such facility for Latex which I can't resist).

---

### Post by philipple on 2010-01-01
> **sherlock-holmes said:**
> could some one please tell me how to use emacs with texlive installation rather than the tetex/auctex thing?

I'm on karmic, but I think this works for you too: Just install auctex via synaptic, and it will also install the complete TeX-system (tetex with karmic is out, they use TeXlive now). So no need to install TeX separatetely. BTW: If you want avoid all the hassle with xrdb and .Xresources to get decent fonts, just install emacs-snapshot-gtk (via synaptic).

Good luck!

---

### Post by st0nes on 2010-03-01
> **Manny C said:**
> Try
```
 sudo apt-get clean 
```
and then
```
 sudo apt-get update 
```

emacs21 should be in the main repositories.

Nope, doesn't work:-
```
mark@addy-laptop:~$ sudo apt-get update
Err http://archive.canonical.com karmic Release.gpg                                                                                                         
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://linux.dropbox.com karmic Release.gpg                                                                                                             
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://www.geekconnection.org karmic/ Release.gpg                                                                                                       
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://za.archive.ubuntu.com karmic Release.gpg                                                                                                         
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://ppa.launchpad.net karmic Release.gpg                                                                                                             
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://deb.torproject.org karmic Release.gpg                                                                                                            
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://download.virtualbox.org karmic Release.gpg                                                                                                       
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://packages.medibuntu.org karmic Release.gpg                                                                                                        
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://dl.google.com stable Release.gpg                                                                                                                 
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
Err http://download.skype.com stable Release.gpg                                                                                                            
  Could not connect to 196.5.234.34:3142 (196.5.234.34). - connect (111: Connection refused)
```

Like everything else in this distro from hell..

---

