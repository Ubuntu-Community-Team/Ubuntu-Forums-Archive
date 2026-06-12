---
title: "Web Searches on the X Selection"
date: 2008-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by light50 on 2008-03-20
Kia-ora! This is my first tutorial.

[COLOR="RoyalBlue"]**Testbed**[/COLOR]

I have used this on [Firefox]("http://www.mozilla.com/en-US/firefox/firefox.html"), versions 3.0.3 through 3.5.7 as well as [Google Chrome]("http://www.google.com/chrome"), version 5.03 and Ubuntu **[COLOR="Sienna"]Feisty[/COLOR]** through [COLOR="Sienna"]**Karmic**[/COLOR] including Ubuntu Netbook Remix, and Mint Linux 6 [COLOR="Green"]**Felicia**[/COLOR].

The aim is to create simple keyboard short cuts that will perform various web searches on the currently highlighted text, from any application on the desktop.

There are two methods given here. If you have Compiz and CompizConfig Settings Manager installed, skip down to the **[COLOR="RoyalBlue"]The CompizConfig Method[/COLOR]**, otherwise read on for [COLOR="RoyalBlue"]**The xbindkeys Method**[/COLOR].

An alternative method given below by simon_w is to attach the function to a panel launcher via a script.

[COLOR="RoyalBlue"]**The xbindkeys Method**[/COLOR]

*I have a quick one-liner if you are the impatient type skip ahead to - **[COLOR="RoyalBlue"]The Quick and Dirty Method[/COLOR]**

[LIST=1]
[*][COLOR="RoyalBlue"]**Install the tools**[/COLOR]
The method I use combines 3 small tools. This tutorial assumes that you have none of them installed. To install them, open the Terminal and enter the following commands:

```
sudo apt-get install xbindkeys xbindkeys-config xsel
```

In brief, **xbindkeys** is a small but powerful command line application that assigns commands to user defined key combinations. Incidentally, it is hugely useful for customizing or enabling multimedia keyboards or multi-button mice.

**xbindkeys-config** provides a graphical user interface for assigning these keyboard short cuts. I have experienced errors with this tool when starting without first creating a configuration file - (*~/.xbindkeysrc*). Create an ~/.xbindkeysrc file with the command:

```

xbindkeys --defaults > ~/.xbindkeysrc
```

It shouldn't surprise you that configuration changes can be achieved by editing the *~/.xbindkeysrc* file by hand. If you want to edit the configuration by hand or examine it more closely, have a look at the [COLOR="RoyalBlue"]**'MANUAL CONFIGURATION'**[/COLOR] section below.

Aside from making sure an *~/.xbindkeysrc* file has been created in advance, I have found **xbindkey-config** to be a very useable application.

**[COLOR="Red"]Note:[/COLOR]**

**xbindkeys** has to be running before **xbindkeys-config** will start. In addition **xbindkeys** has to be running before your short cuts will work. I start xbindkeys automatically on session startup using the following method:


[LIST]
[*]From the Desktop, Go to System > Preferences > Session, (In Jaunty this has been changed to System >Preferences > Startup Applications)
[*]Select Startup Programs, click "Add", and type in xbindkeys in the Name and Command fields. Click Add and close the Startup dialogue.
[/LIST]


**xsel** is a flexible and extremely useful command line application. Among other uses, **xsel** can output the contents of the text currently highlighted (sometimes referred to as the X Selection), into another command.

These three applications are all in the software repositories for **[COLOR="Sienna"]Dapper[/COLOR]** through [COLOR="Sienna"]**Karmic**[/COLOR].


[*][COLOR="RoyalBlue"]**Create the keyboard short cut**[/COLOR]
In this example we will create a basic Google search. 

To configure xbindkeys manually, skip forward to **[COLOR="RoyalBlue"]'Manual xbindkeys Configuration'[/COLOR]**, else continue:

In a Terminal, enter the following command to start the xbindkeys-config application:

```
xbindkeys
xbindkeys-config
```

This should open the xbindkeys-config application. You should see a list box to the left, some controls to the bottom and fields and controls to the right, similiar to this:
[IMG]http://lh5.google.com/smithy/R-JwkgCcV3I/AAAAAAAAAuA/VElkde8JJ7E/s400/550x550-Capture-Xbindkeys%20Config%20Version%20%3A%200.1.3.png[/IMG]


To create the shortcut, click **'New'** at the bottom.


[*]Give the short cut a suitable name in the **'Name:'** field.


[*]Click **'Get Key'**. A small blank window will open. Key in your chosen keyboard short cut. (I have used '*Ctrl G*')

After you have selected your short cut, the small blank window will close and a new string of text will appear in the **'Key:'** field. In my '*Ctrl G*' example I get the string:

[INDENT]*'Control+Mod2 + g | m:0x14 + c:42'*[/INDENT]

but you may get something different.


[*]Lastly in the **'Action:'** field, enter the command you would like assigned to the short cut. To search **[www.google.co.nz](www.google.co.nz)**, enter:

[INDENT]*firefox http://www.google.co.nz/search?q=`xsel -p|perl -pe 'tr/ /+/'`*[/INDENT]

or in the case of Google Chrome:

[INDENT]*google-chrome http://www.google.co.nz/search?q=`xsel -p|perl -pe 'tr/ /+/'`*[/INDENT]

[*]Save your short cut and close the application by clicking **'Save & Apply & Exit'**

[*]Test your short cut by highlighting some text and keying your short cut combination.

[/LIST]

Another excellent tip by simon_w below is to use gconftool to find the default browser with:

```

gconftool-2 --get '/desktop/gnome/url-handlers/http/command'

```

**[COLOR="RoyalBlue"]'Manual xbindkeys Configuration'[/COLOR]**

This section describes a more hands-on configuration method. Dispense with the steps above, ensuring only that you have xbindkeys and xsel installed on your system:

```
sudo apt-get install xbindkeys xsel
```

xbindkeys includes a nifty control flag '--keys' (or '-k' for short), which allows the capture of keyboard commands. It prints the actual key code required in the xbindleys configuration file ~/.xbindkeysrc. If that sounds confusing, try these instructions:

[LIST=1]

[*]Ensure xbindkeys is running and you have created a file ~/.xbindkeysrc. If not, start xbindkeys and create a default configuration file in a terminal with the command:

```

xbindkeys --defaults > ~/.xbindkeysrc
```

[*]Open this file for editing. I use gedit in this example because emacs isn't available to me on a vanilla install :):

```

gedit ~/.xbindkeysrc &
```

[*]Scroll down to the last entry, which should look something like this:

```

## Control + mouse button 2 release event starts rxvt
#"rxvt"
#  Control + b:2 + Release
```

[*]Insert a suitable title. I will use the example 'Super + G performs a Google search of highlighted text':

```

## Super + G performs a Google search of highlighted text
```

[*]Next you will insert the required configuration for your keyboard shortcut. Return to the terminal and bring up the keyboard capture dialog, with the command:

```

xbindkeys -k
```

[*]Key your desired shortcut. Once you have selected one the terminal will print the required configuration. We are only interested in the last 3 lines. In my example:

```

"(Scheme function)"
    m:0x40 + c:40
    Mod4 + d

```

[*]Copy these three lines into your edited ~/.xbindkeysrc, below your new title:

```

## Super + G performs a Google search of highlighted text
"(Scheme function)"
    m:0x40 + c:40
    Mod4 + d

```

[*]Next we will insert our desired command. Replace '(Scheme function)' with your desired command. In my example this is *firefox http://www.google.co.nz/search?q=`xsel -p|perl -pe 'tr/ /+/'`*:

```

## Super + G performs a Google search of highlighted text
"firefox http://www.google.co.nz/search?q=`xsel -p|perl -pe 'tr/ /+/'`"
    m:0x40 + c:40
    Mod4 + d

```

[*]Save ~/.xbindkeysrc, exit your text editor and you're done!

[*]Test your short cut by highlighting some text and keying your short cut combination.
[/LIST]

[COLOR="RoyalBlue"]**Websearch X?**[/COLOR]

Setting other short cuts is as simple as repeating steps 2 through 7 using the appropriate url search string.

eg. to search [www.torrentz.com](www.torrentz.com), set the xbindkeys **'Action:'** to:

[INDENT]*firefox http://www.torrentz.com/search?q=`xsel -p|perl -pe 'tr/ /+/'`*[/INDENT]

And assign an appropriate short cut.

Thanks simon_w for your suggestion to replace

```

`xsel -p|perl -pe 'tr/ /+/'`

```

with

```

`xsel -p | tr [:space:] +`

```

Other searches I use include:

[INDENT][I][http://mycroft.mozdev.org/download.html?name=](http://mycroft.mozdev.org/download.html?name=)
[http://video.google.com/videosearch?q=](http://video.google.com/videosearch?q=)
[http://reviews.cnet.com/4244-5_7-0.html?query=](http://reviews.cnet.com/4244-5_7-0.html?query=)
[http://www.chordie.com/index.php?q=](http://www.chordie.com/index.php?q=)
[http://www.last.fm/music/?q=](http://www.last.fm/music/?q=)
[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=](http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q=)
[https://addons.mozilla.org/en-US/firefox/search?q=](https://addons.mozilla.org/en-US/firefox/search?q=)
[google-chrome http://www.google.co.nz/search?q=`xsel -p | tr [:space:] +`+in+nzd](google-chrome http://www.google.co.nz/search?q=`xsel -p | tr [:space:] +`+in+nzd)[/I][/INDENT]

I have found this desktop-wide search ability enormously useful. Error messages that pop up on Gnome or Ubuntu or even in the Terminal can be 'Googled' in a flash. I am using Wikipedia searches to help me with a Management essay I am plagiarising at the moment. :) . Translations, currency and unit conversions, searches of the repository, image search, Google Desktop search...

There are other ways to achieve this functionality but hopefully someone out there will save a little of the time I spent trying to get this working.

[COLOR="RoyalBlue"]**References**[/COLOR]

[X Window System]("http://en.wikipedia.org/wiki/X_Window_System")
[xbindkeys]("http://hocwp.free.fr/xbindkeys/xbindkeys.html")
[Configuring Startup Applications]("https://help.ubuntu.com/community/AddingProgramToSessionStartup")

**[COLOR="RoyalBlue"]The Quick and Dirty Method[/COLOR]**

I use this command to save myself time (I back-up my ~/.xbindkeysrc file remotely at dotfiles.org):

```
sudo apt-get install xbindkeys xsel curl && xbindkeys --defaults > ~/.xbindkeysrc && curl -N http://dotfiles.org/~light50/.xbindkeysrc > ~/.xbindkeysrc && xbindkeys
```

**[COLOR="RoyalBlue"]The CompizConfig Method[/COLOR]**


[COLOR="RoyalBlue"]**Install xsel**[/COLOR]
[LIST=1]
[*]
```
sudo apt-get install xsel
```

**xsel** is a flexible and extremely useful command line application. Among other uses, **xsel** can output the contents of the text currently highlighted (sometimes referred to as the X Selection), into another command.

xsel is in the software repositories for **[COLOR="Sienna"]Dapper[/COLOR]** through [COLOR="Sienna"]**Karmic**[/COLOR].
[/LIST]

[COLOR="RoyalBlue"]**Create the keyboard short cut**[/COLOR]
[LIST=1]
[*]Select Preferences then CompizConfig Settings Manager.
[*]Select General Options.
[*]Select the Commands tab then the Commands drop down section.
[*]To search **[www.google.co.nz](www.google.co.nz)**, insert the following command into a free Command line space:

[INDENT]*firefox http://www.google.co.nz/search?q=`xsel -p|perl -pe 'tr/ /+/'`*[/INDENT]

[*]Open the Key bindings drop down section.
[*]Activate the Edit the Run command dialog that corresponds with your command.
[*]Select Grab key combination.
[*]Key your desired shortcut.
[*]Select OK.
[*]Exit the CompizConfig Settings Manager.
[*]Test your short cut by highlighting some text and keying your short cut combination.

[/LIST]

I have Firefox set to open new tabs where ever possible as I prefer them.

So for me at present if Firefox is open, each xsel search I perform will open in a new tab.

If you have used Firefox for a while you will appreciate that the short cut may behave a little differently depending on your Firefox tab and window settings.

[COLOR="RoyalBlue"]**Edits**[/COLOR]

10:40 AM Friday, March 21 2008 - Tidied up readability
11:05 AM Friday, March 21 2008 - Added note on running and automatically starting xbindkeys
12:11 PM Sunday, March 23 2008 - Added note on successful install on Hardy
3:46 AM Sunday, June 1 2008 - Corrected typo '...steps 2 through 9 using...' to '...steps 2 through 7 using...'
8:47 AM Saturday, October 25 2008 - Updated testbed conditions
8:23 AM Sunday, March 8 2009 - Added note on successful install on Intrepid
11:59 AM Sunday, April 26 2009 - Added note on successful install on Jaunty
12:14 PM Sunday, April 26 2009 - Updated reference to 'Configuring Startup Applications'
10:19 PM Friday, May 15 2009 - Corrected typo '...torrentx.com...' to '...torrentz.com...'
10:28 PM Friday, May 15 2009 - Added instruction to create an ~/.xbindkeysrc file
12:17 PM Saturday, May 16 2009 - Added 'Manual xbindkeys COnfiguration' section
12:29 PM Saturday, May 16 2009 - Tidied up format
7:38 PM Tuesday, May 19 2009 - Added 'The Quick and Dirty Method'
2:37 PM Saturday, May 31 2009 - Added 'CompizConfig Settings Manager Method'
6:23 PM Monday, January 25 2010 - Added note on successful install on Karmic and UNR
6:43 PM Monday, January 25 2010 - Added suggestions by simon_w
5.23 PM Tuesday January 26 2010 - Updated Firefox version to 3.5.7
8.10 AM Thursday April 15 2010 - Updated Firefox version. Added Google Chrome Compatibility. Added Currency COnversion function

---

### Post by wieman01 on 2008-03-20
Nice one! Thank you.

---

### Post by light50 on 2009-05-15
*bump*

Hi. I have made a few additions to this tut and would be keen to get any feedback. Have fun. Thanks.

---

### Post by simon_w on 2009-11-17
this is cool :)

if you want to use the default browser as specified in the Gnome settings, you can use this:

```
$(gconftool-2 --get '/desktop/gnome/url-handlers/http/command' | awk '{print $1}')
```

also, I reckon `xsel -p | tr [:space:] +` is an improvement on `xsel -p|perl -pe 'tr/ /+/'` since it will cope with tabs and newline chars.

Here is a short script I wrote which I use in panel launchers.  it can also be bound to hotkeys using System -> Preferences -> Keyboard shortcuts, which is less hassle than messing with xbindkeys.  still need xsel though.

```

#!/bin/bash
#
# by simon, Nov. 08
#
# Requirements:
#
#  assumes the Gnome Desktop environment (because that's what I use!),
#   but could be extended easily enough
#  xsel (sudo apt-get install xsel)
#
# some suggestions for use:
#
#  google.co.uk:
#    xsel_to_web.sh http://www.google.co.uk/search?q=
#
#  dictionary.com:
#    xsel_to_web.sh http://dictionary.reference.com/browse/
#
#  Wikipedia (en):
#    xsel_to_web.sh http://en.wikipedia.org/wiki/
#
#

# get the user's chosen browser (assumes Gnome)
BROWSER=$(gconftool-2 --get '/desktop/gnome/url-handlers/http/command' | awk '{print $1}')

# get website to link to from command line, or default to google
if [ -z "$1" ]
then
    LINK="http://www.google.com/search?q="
else
    LINK=$1
fi

# get the search term from the X selection
SEARCHTERM=$(xsel -p | tr [:space:] +)

# go!
${BROWSER} "${LINK}${SEARCHTERM}"

```

thanks!

---

