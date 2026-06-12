---
title: "Bookmarks bar font size in Chromium &amp; Firefox Ubuntu 18.04"
date: 2018-07-26
forum: New to Ubuntu
---

### Post by herjo on 2018-07-26
I installed Ubuntu v18.o4 64bit  and i have not found a way to reduce the large fonts in the Bookmarks bar of either Firefox or Chromium.
Coming from windows, these fonts look way-out of proportion the the icons.
can any one help please?

---

### Post by Holger_Gehrke on 2018-07-26
I don't know a thing about Chrom(e|ium), but in Firefox everything and anything can be customized. Do you mean the horizontal Bookmarks-toolbar or the vertical Bookmarks sidebar ?

Create a file named  'userChrome.css' in the directory 'chrome' in your profile's directory (that's a subdirectory of '~/.mozilla/firefox'; if your profile is the default profile it's name will be a random looking string of characters ending with '.default'); if the directory 'chrome' does not exist, create it.

The first line of that file **must** be
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
```
The rest of the file are css-declarations.

For the sidebar you could write something like
```
treechildren.sidebar-placesTreechildren {font-size:12pt !important}
```
(replace the '12pt' with any size you think fitting)

Similarly for the toolbar you'd write:
```
toolbar#PersonalToolbar .toolbarbutton-text {font-size:12pt !important}
```

To find the IDs and classes of elements in the UI of Firefox for use in CSS-selectors you can use the Browser tools found in the menu 'Extras->Web-Developer->Browser Tools'. Changes to userChrome.css will be picked up on the next start of Firefox.

Holger

---

### Post by herjo on 2018-07-26
Thanks, I am talking about the the "horizontal"  bookmarks bar.
 I posted this in the Beginners for good reason--> 
I am supposed to create a css file??  I know how to do this in windows, but not in ubuntu.
 The  file hierarchy here does not make any sense eg no "tree" , how to do a global search for a file of folder??
In 'other locations', searching for " ~/.mozilla/firefox " shows no result.

---

### Post by Holger_Gehrke on 2018-07-27
It's a rather advanced question -- taking out the specifics, it ends up as "how do I change the look of arbitrary elements in the browser's UI" -- so I assumed a lot of background knowledge. You also mentioned neither version nor flavour (mainline Ubuntu, KUbuntu, XUbuntu, LUbuntu, Ubuntu Studio, ...) you're using, so it's rather difficult to give step by step instructions.

The '~' at the beginning of the path I gave is a shell abbreviation for your home directory. If your user name in Ubuntu is 'herjo', that would be '/home/herjo/'. 

The dot at the beginning of '.mozilla' by convention means the file or directory is hidden and will not be shown in the file manager or the shell unless you specifically tell the program to show hidden files.

If your file manager has an address bar, you can just cut-and-paste '~/.mozilla/firefox/' there. 

The left sidebar in all file managers I've used (nautilus in Ubuntu, Thunar in XUbuntu, PCmanFM in Lubuntu, konqueror in KDE back when I used SuSE Linux) can be set to either show places (also called bookmarks in some of them) or the filesystem tree. For searching for files or directories there's a tool named 'catfish' that can be integrated with the file manager as a user-defined action, but I usually use the command line tool 'find' for that.

Experienced users of Ubuntu are often very fond of the command line because the commands and options are always the same, no matter what "flavour" and version of Ubuntu you're using (actually, the majority of commands will work on most Linux distributions, not just Ubuntu) or what language you've set your system to. 

So let's try it that way.

Open a terminal.You'll get a window with a prompt (probably something like "username@machinename:~$"). Depending on what Desktop Environment you have, you'll have a different terminal program; especially cut-and-paste to and from a terminal is somewhat unusual and there's more than one way to do it. Since the keys normally used for cut and paste (ctrl-x,ctrl-c,ctrl-v) have a special meaning to the shell, no terminal-program uses those. You can either use the normal keys but with shift held additionally, or select paste from either the menu "edit" or from a context menu you get when right-clicking somewhere in the work-area of the terminal. If neither of those work, you can just mark the text you want to paste to the terminal (no need to copy, just mark it), switch to the terminal and click the middle mouse button (usually the mouse wheel; if you have a very old mouse or a touchpad with only two buttons hitting both of those at the same time usually works). You can either type in the commands or paste them and be sure to get no typos but mine ;-)
```
cd ~/.mozilla/firefox/*.default
```
This will **c**hange the working **d**irectory to the directory of the default profile of firefox (the prompt changes to reflect this). Now let's change to the directory 'chrome':
```
cd chrome
```
if the directory is already there, a change in the prompt is all the feedback you might get. If the directory doesn't exist, you'll get an error telling you so. In that case enter
```
mkdir chrome
```
to create the directory (you won't get any message announcing success, that's standard behaviour on the command line - no news is good news; if you do get a message from 'mkdir' then you probably have a bigger problem than just a slightly wrong font size ...) and try to change into it again.
Next we'll start an editor to create the css-file and put the needed directives in it.
```
nano userChrome.css
``` Linux is case-sensitive, so that capital 'C' is important. If the file already exists, it will be opened, otherwise a new (empty) file will be created. Now put the lines from my previous post into the file. Hit ctrl-o to save, enter to use the file name it shows. You have to close and restart Firefox to see the result. If it's not the right size, switch back to the terminal and the editor in it and change the values for 'font-size' until you get it right. Then you can hit ctrl-x to exit the editor and type 'exit' in the shell to close the terminal.

Holger

---

### Post by herjo on 2018-07-28
Thank you for the Linux lessons.
I did what you suggested. Initially I left the font size as per your command lines eg 12pt
Than I changed it to 10pt --> no change
Than changed to 8pt --> still no change
To make it a little  clearer..........
The current font size, has the same physical  height as the "google icon" in the toolbar  or the same size as the text (file- edit- view History etc) in the menu bar.
It is all way out of proportions.
I tried  **layout.css.devPixelsPerPx ** ( to 0.8-0.9)  in** about:config  **(This just pushed the boxes closer together)Nogo either**  , ** nor does** ^- 0r ^+** have any influenceI am getting 11 bookmarks across in Firefox & Chrome, while windows 7 & 10 (Firefox & Chrome show 16 (using the same bookmarks .html[B])

[/B]My guess is, that it is a setting in Linux somewhere(not in firefox or chrome). 
As last month, I ran Debian stretch  32 & 64 bit, both versions had very large font sizes for both Firefox & Google chrome also,( which was the reason for installing Ubuntu 18.04 64bit now) It also all showed up as totally out of proportions.

So far, for me anyway, the only Linux versions showing _**normal **_font sizes are Puppy Linux and Lucid puppy.

Maybe the large distro Linux stuff is allergic to my laptops??  Lenovo T60. T61 & T410, all have max Ram & run on SSD, all dual boot with Win 7 & 10  
???

---

### Post by Holger_Gehrke on 2018-07-28
Attached: 4 screenshots with the font at 12pt,10pt, 8pt and 6pt. The difference is obvious and visible.

Did you close and restart Firefox when trying your changes ? Just starting a new FF while  FF is already running will just open a new window and will not read the changes in userChrome.css. You might also want to take a look at [userchrome.org]("https://www.userchrome.org/"), perhaps their explanation makes more sense to you than mine ...

Also, if the number of entries in the toolbar is important, you might want to change not only the (mainly vertical) size of the font but also switch to a different, more narrow font - perhaps an "Ubuntu Condensed" or "Roboto Condensed" - by adding a "font-family" property.

Holger

---

### Post by herjo on 2018-07-28
Your screenshot #1 12pt looks like  what I have got currently.
#3 screenshot  8pt is what I want
There is no need to change the font type, just the size will do fine.

OK..
I deleted the .css file , rebooted laptop.
Than I started again.
 I followed all your instructions to the letter(double checked)

The new css file reflects 8pts font size
Reboot laptop
Checked if the css file is still there and showing 8pt font->Confirmed
Started FF-- >No visual change. no font change

I am just wondering why Ubuntu & Debian  FF (& Chrome)  show 12Pt font sized by default, while Puppy Linux & lucid show "normal"  font size(around 8pt) by default... just a thought

Thank you for all your time and effort spent 
Grüß gott Holger

---

### Post by Holger_Gehrke on 2018-07-28
Okay, I'm slowly running out of ideas ...

just two more:
[LIST=1]
[*]Perhaps you've got more than one profile in Firefox and we're putting the changes into the wrong profile. Check the contents of the file '~/.mozilla/firefox/profiles.ini' (use either 'cat ~/.mozilla/firefox/profiles.ini' or 'less ~/.mozilla/firefox/profiles.ini' in a terminal; cat just dumps the file to the terminal, less allows you to scroll though it, search it etc; to leave less and return to the shell hit the letter 'q'). The file has the usual ini-file-format: headings in brackets followed by lines consisting of an option name, an equal sign and the value for the option. If you have more then one heading 'Profile' with a number at the end then look for the one under which there is a line "Default=1'. That's the profile that gets loaded if you don't explicitly choose a profile. If that's not the one with a line 'Path=some-random-characters.default', then that's the problem. You'd need to move or copy the 'chrome' directory from the folder of the profile called default to the one that actually is default.
[*]Firefox uses GTK. In XFCE there is a tool in the settings menu called simply Appearance, which sets the theme, the icon-set and the** default font** to use in GTK applications. There should be a similar tool in Gnome. When I set the default font from the Noto 9pt I set after XUbuntu installation to 12pt using this tool, I had the large text you describe. So if you can live with having a smaller font **everywhere**, this would solve your problem.
[/LIST]

Holger

---

### Post by herjo on 2018-07-29
[COLOR=#ff0000]**[SIZE=3]_You're a genius_[/SIZE]**[/COLOR]

The problem was, like you suggested, that I had 2 profiles-> deleted one and put the css file in the actual default. that worked just fine.-> 8pt fonts in Firefox toolbar. Great!

Regarding default fonts globally. -> I found an app called "  Gnome Tweak tool "
Here one can do all sorts of settings incl  default font sizes. ->had a play around with this and actually working also. 

So All good
Many thanks for your help and patience Holger 
 :KS

---

