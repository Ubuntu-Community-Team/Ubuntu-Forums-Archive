---
title: "Finding Gecko-mplayer plugin"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Horomancer on 2008-08-31
I used [this]("http://ubuntuforums.org/showthread.php?t=766683&highlight=mplayer") excellent installation guide today, hoping to solve some media playback troubles.
So far everything is great except WMV format files in Firefox. In firefox> Edit> Preference> Applications my options for playing Windows Media Video are Mplayer and Mplayer-plugin. I can view the files with Mplayer, no trouble, but it dls the video first then opens a new window. I removed Mplayer-plugin as instructed in the linked guide and replaced it with Gecko mplayer. Other video formats have the option to use gecko, just not WMV. I can select 'other' and choose an app, but I have no clue where gecko-mediaplayer is on my computer.
Thanks for the help

---

### Post by nothingspecial on 2008-08-31
I don`t have geko but I would look in /usr/bin or just /bin

---

### Post by Horomancer on 2008-08-31
hmmm I don't see a 'gecko' in either of those areas.
The icon for the gecko-mediaplayer plugin in firefox isn't an App icon like Mplayer, but looks like a little notepad. Not sure what that means.

---

### Post by nothingspecial on 2008-08-31
Clutching at straws without installing it but what about -

/usr/share/mplayer

If not directly in there, there might be a plugins directory.

---

### Post by ajgreeny on 2008-08-31
If you type about:plugins in the firefox address bar you will see a page with all the plugin files shown with their full paths to the files used.  You can deal with it from there and rename it if you wish to disable it, or delete it, but be careful.  You can just disable it from the Tools>>Add-ons menu.

---

### Post by lovinglinux on 2008-08-31
The correct option for "Windows Media Video" in the Applications Tab is actually "Window Media Player Plugin (in Firefox)". That is the option that you should select, because the underlying engine is provided by gecko-mediaplayer.

If you open Firefox > Tools > Add-ons > Plugins and select "Windows Media Player Plugin" it should have the following description:

"Gecko Media Player 0.6.0 Video Player Plugin for QuickTime, RealPlayer and Windows Media Player streams using MPlayer".

The same description applies to "DivX Browser Plugin", "QuickTime Plug-in 6.0 / 7" and "RealPlayer 9". They are all provided by gecko, even if they have different plugin names.

If you still need to open the standalone player, you can create a menu entry with the "gnome-mplayer" in the command field.

---

### Post by Horomancer on 2008-08-31
Thanks for the info.
So my poor playback is do to something other than the wrong plugin being used.
I had this problem before i installed gecko where WMV files in firefox would load, but only play the first 2~3 secs of a video then stop. Played with the various buttons and refreshed the page, but nothing has worked.

---

### Post by lovinglinux on 2008-08-31
I don't know if it is your case but I use a streaming service that is not Linux friendly and streams Windows video format. If I have more than one plugin for WMV installed it won't work. I had to uninstall all plugins following the tutorial you mentioned and install gecko again, then the video played without severe issues.

---

### Post by Horomancer on 2008-08-31
i know that the mplayer plugin is removed, what other plugins are there? I don't recall having installed any aside from mplayer.

---

### Post by lovinglinux on 2008-08-31
> **Horomancer said:**
> i know that the mplayer plugin is removed, what other plugins are there? I don't recall having installed any aside from mplayer.

This is my plugin list. I have no issues so far.

[[IMG]http://img515.imageshack.us/img515/2328/screenshotaddonspluginsfp1.th.png[/IMG]](http://img515.imageshack.us/my.php?image=screenshotaddonspluginsfp1.png)

Please notice that DivX, QuicktTime, RealPlayer and Windows Media Player plugins are all part of the gecko-mediaplayer package.

---

### Post by alienexplorers on 2008-08-31
Why don't you use the mediaplayerconnectivity extension which allows mplayer to work.  You first have to download the player from the medibuntu repositories.

---

### Post by Horomancer on 2008-08-31
My plugin list is the same except i do no have Itunes and do have Adobe reader 8.0

I haven't heard of mediaplayerconnectivity extension. Is it just the mozilla-mplayer file in Synaptic?

---

### Post by lovinglinux on 2008-08-31
> **Horomancer said:**
> My plugin list is the same except i do no have Itunes and do have Adobe reader 8.0

I haven't heard of mediaplayerconnectivity extension. Is it just the mozilla-mplayer file in Synaptic?

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by David-IT on 2009-04-25
ok first do:
> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
then do:
> sudo apt-get install gnome-mplayer gecko-mediaplayer
hope i helped ty :D

---

