---
title: "default programs for removable media: CDs. Does it work correctly?"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-08-31
Hi Community:

I need help getting the default programs correctly for removeable media: CDs.

:)

I've set Sound Juicer to be the default program for removable media when those media are CDs by using:

System settings > Details > Removable Media > CD Audio and then selecting Audio CD Extractor (Sound Juicer) from the pull down list. Also, the checkbox "Never start programs on media insertion" remains UNCHECKED.

However, when I insert a CD, Rhythmbox pops up. 

:-k

I don't like or use Rythmbox (it is too 'heavy' and has alot of "missing data" like unfindable CD covers. I use Media Player). However, I know that if I remove Rhythmbox, the audio level adjuster (speaker icon in the top panel) gets removed with alot of other stuff that my audio programs depend on.

#-o

[COLOR="DarkOrange"]**Is there a way to "tame" Rythmbox and get only Sound Juicer to pop up when I insert a CD?**[/COLOR]

Thanks!
Barnacled Old Jimma

---

### Post by GreatDanton on 2012-08-31
Well it's not exactly what you are looking for, but maybe it will help you: [http://superuser.com/questions/187440/set-default-ubuntu-video-player-as-vlc](http://superuser.com/questions/187440/set-default-ubuntu-video-player-as-vlc)

Look for the last solution.> According to: [http://wiki.videolan.org/How_to_make_VLC_the_default_player](http://wiki.videolan.org/How_to_make_VLC_the_default_player)
  You can do the following:
  
[LIST=1]
[*]Go to /usr/share/applications/ and find  the following two files
[LIST]
[*]defaults.list
[*]mimeinfo.cache
[/LIST]
 
[*]Change all "totem.desktop" to "vlc.desktop"
[/LIST]
  I personally copied all the totem.desktop lines to ~/.local/share/applications/mimeapps.list and then search and replaced all to "vlc.desktop". 
  Please note that the format to copy is:
  [MIME Type]=[Name of the Desktop Entry file]  
If that's not working you can still purge Rhytmbox (I assume you don't need it).


Regards.

---

