---
title: "[SOLVED] Flash problems (Youtube not always working)"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by sqrooup on 2008-11-26
Since upgrading from Hardy to Intrepid I cannot seem to get many of the videos on YouTube to display (some do work).

I have looked in some of the previous postings and have been to Synaptic Package Manager; have found both "adobe-flashplugin" (the videos that did work used this version) and "flashplugin-nonfree", tried both, but to no avail.

I wonder if there are any codes to use to get them working?

---

### Post by doctorbighands on 2008-11-26
I've never had much luck with the flash player codecs available in the repos. My advice is to get the flash player from the Adobe website (if you Google "flash player" it'll take you there). Follow the instructions for installation (it's really simple), and you should be good to go!

---

### Post by gandaran on 2008-11-26
adobe-flashplugin and flashplugin-nonfree are just the same thing, they are  empty packages, they both download the same flash from the adobe website and install it, that's what these packages are for, only install scripts!

now about your flash problem, did you install any other flash package?
like gnash or swfdec? you should only have one type of flash installed and only one adobe package
check in synaptic for that or if you cant find anything post the output of **locate libflash** (type in terminal)
also the output of
```
about:plugins
```
type in firefox url bar

---

### Post by sqrooup on 2008-11-26
The output of locate libflash is;

sqrooup@hal-desktop:~$ locate libflash
/home/sqrooup/Documents/Stuff I might not need anymore/install_flash_player_9_linux/libflashplayer.so
/home/sqrooup/Documents/Stuff I might not need anymore/install_flash_player_9_linux/install_flash_player_9_linux/libflashplayer.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

as to the other "about:plugins";

sqrooup@hal-desktop:~$ about:plugins
bash: about:plugins: command not found

---

### Post by gandaran on 2008-11-26
the about:plugins thing you type in firefox url bar and post the full output here.
so far I can see you have only the correct adobe flash 10 package installed.

---

### Post by sqrooup on 2008-11-26
I have edited it to remove what I believe to irrelevant to this section:

Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 9.0 r999. Gnash 0.8.4, the GNU SWF Player. Copyright © 2006, 2007, 2008 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 9.0 r999.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No

...

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by gandaran on 2008-11-26
you have two flash packages installed you have to remove if you want adobe flash to work! gnash and swfdec!
open synaptic and look for the gnash and mozilla swfdec plugin, mark them for complete removal and click the apply button

---

