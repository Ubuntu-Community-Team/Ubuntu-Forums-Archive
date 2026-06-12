---
title: "KHotKeys or: How I Learned to Stop Worrying and Love the Windows Key"
date: 2006-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Parkotron on 2006-01-20
It's probably safe to say that at least eighty percent of you are sitting in front of a keyboard with a "Window key" on it. It's also probably safe to say that the majority of you never touch it.

In Windows, the Window key is pretty much a waste of space. Who actually navigates the start menu with the keyboard? It's used in a couple of handy shortcuts (win+D, win+R), but that's pretty much it. Often times it's nothing more than a curse when pressed accidentally. Some even go so far as to physically remove the key from the keyboard all together.

In Linux however, the Window key can finally blossum to it's full potential. KDE has KHotKeys and I'm sure that Gnome must have something equivalent. These daemons allow users to define the custom global keyboard shortcuts to oft used applications. I'm sure many of you are already familiar with these programs. If not they're described by several other threads on this forum, so I won't get into specifics here. 

My goal is simply to advocate the use of the Window key above all others for global hotkeys. I often see posts where people discuss how they assign their favourite calculator app to ctrl+alt+C. Why not try win+C instead? The reasons why the Window keys are ideal for global keyboard shortcuts are numerous:
[LIST]
[*]Linux apps don't assume it exists and therefore don't assign shortcuts to it, allowing one to "reserve" the Window key for global hotkeys. ctrl+alt, ctrl+shift or (God forbid) ctrl+alt+shift combinations can often cause conflicts with application shortcuts. amaroK is the only Linux app that I know of that uses the Window key for shortcuts, but it uses it for its own global shortcuts anyway.


[*]Dual modifier shortcuts often use two hands (one for the modifiers, one for the keystroke) or require dexterity testing finger acrobatics to pull off. By using just the Windows key without other modifiers, all almost combinations are easily reachable with a single hand.


[*]They're usually closer the centre of the keyboard than ctrl, which results in less stretching.


[*]Some may find pleasure in the fact that the Window key (a Microsoft invention) is actually fifty times more useful under Linux.


[*]It just makes sense to use different modifiers for different types of shortcuts.[LIST]
[*]alt => Accelerator shortcuts
[*]ctrl => Application shortcuts
[*]**win** => **Global shortcuts**
[*]ctrl+alt => Important system shortcuts
[/LIST]


[*]It greatly increases the possiblilities for ridiculously complex shortcuts. Who wouldn't want to assign a terminal window to win+ctrl+alt+shift+scrolllock?


[*]There are two of them just sitting there. What else are you going to do with them?
[/LIST]

Oh, and of course those of you on a Macintosh or an IBM type-M or a laptop (which may not have a Window key or may have it in a bizarre location) can feel free to tell me to mess off.

---

### Post by BobSongs on 2006-02-08
Ha!

Y'know: you're right, **Parkotron**, you're right. That cannot be argued. You've made a good and clear point.

Now how do I make use of it? What application do I use to create hotkeys? (N00b here.)

Thanks!

---

### Post by Heliode on 2006-02-08
I found it sort of ironic to bind the left Windows-key to Gnome-terminal, and the right one to Nautilus.

Ironic, and useful.

---

### Post by helmet on 2006-02-08
argh where is this khotkeys!? i can't find it to do anything with it and i just want my windows key to do something

---

### Post by xtacocorex on 2006-02-08
The Window key has become increasingly useful on my laptop:
Win+Left Arrow: Previous song in Amarok
Win+Right Arrow: Next song in Amarok
Win+Up Arrow: Turn music on
Win+Down Arrow: Turn music off
Win+P: Show/Hide Amarok
Win+F1: Firefox
Win+F2: Open Amarok (initial call)
Win+F3: Gaim (initial call)
Win+F4: Kate

There are some more, but I forgot them.

Helmet:
Khotkeys should be installed by default in KDE. There is a module for it in kcontrol (KDE's Control Center) or I think it's in System Settings, but I don't use that nor do I know where it's at.

---

### Post by Parkotron on 2006-02-09
Firstly, KHotkeys is a default component of KDE. You may be having trouble finding KHotkeys because it's been labelled "Input Actions" in latest releases of KDE. You can find it under "Regional & Accessibility" in either System Settings or the KDE Control Centre. It's a pretty powerful tool, so it might take you a while to figure out how to correctly set it up. If anyone is having considerable difficulty using KHotkeys, let me know and I might write a separate HOWTO.

For those individuals using Gnome, it may or may not be possible for you to install KHotkeys. I, however, have no idea of how one would go about doing that. I had always assumed that there was a Gnome equivalent to KHotkeys, but from a look at the complexity of [this tread]("http://http://www.ubuntuforums.org/showthread.php?t=27039"), I would have to guess that there's no simple, one-stop hotkey solution for Gnome. If anyone knows a better way, please let us know.

---

### Post by Parkotron on 2006-02-09
Since xtacocorex did, I guess I'll include my personal set of Windows key shortcuts.

**win+?** : Show Amarok OSD
**win+C** : Launch KDE Control Centre
**win+D** : Show/Hide desktop
**win+E** : Launch KMenuEdit
**win+F** : Launch Find Files/Folders
**win+G** : Launch the GIMP
**win+H** : Launch KDE Help Centre
**win+I** : Launch Inkscape
**win+J** : Launch KJots
**win+Q** : Launch Konqueror
**win+R** : Show/hide Amarok (I use multimedia keys for Play/Pause, Next and Previous)
**win+V** : Launch KDevelop
**win+Y** : Launch Synaptic
**win+Z** : Launch Konsole
**win+space** : Start XScreensaver
**win+alt+space** : Configure XScreensaver
**win+up** : Increase volume with KMix
**win+down** : Decrease volume with KMIX
**win+`** : Enable/Disable Kompmgr (KDE compositing manager)
**win+print screen** : Launch KSnapshot
**win+menu** : Show the minicli (a.k.a. alt+F2 "Run Command" dialogue)

The last one is by far my favourite. On most keyboards the Windows and Menu keys are side by side on the bottom row. Hitting win+menu is way quicker, easier, and more comfortable than pressing alt+F2. I recommend you give it a try.

Until I compiled this list I hadn't realised that I have a shortcut assigned to every letter from C to J. Most surprisingly, I have nothing assigned to win+K, which is hard to believe seeing that I'm a KDE user. I guess when 75% of the programs one uses start with a 'K' it's hard to associate any one of them with win+K.

---

### Post by Jenda on 2006-05-06
I used the Super (win key) to create a four layer keyboard.
I started with a regular dvorak, then added czech characters instead of top row numbers, but soon realised I need more - french characters, things, such as | and many more come in handy.
So I used xmodmap (file attached) to make the super be a mode_switch, which means it will behave like a second shift key. This way I can have four characters per key, eg. e = e, shift+e = E, super+e = &#951; and super+shift+e = €
Now I have Czech, French, linux (|&#@[]{} etc.) and... greek & geek on my keyboard:
&#367;š&#269;&#345;žýáíé[]~!@#$%|({}°1234567890[]~¹²³&#8834;&#8835;&#8743;&#8744;&#8745;&#8746;&#8734;¥&#966;&#947;©&#961;&#955;/±·&#928;¥&#934;&#915;¢®?&#8800;æ&#12484;&#951;&#965;&#953;&#948;&#952;&#964;&#957;&#963;¬°Æ&#12484;€&#933;&#8747;&#916;&#920;&#932;&#925;&#931;&#8730;¦ø&#967;&#954;×&#946;&#956;&#969;þ&#950;¶Ø&#935;&#922;÷ß&#924;&#937;&#918;&#8592;&#8593;&#8594;&#8595;
and lots of space to add more...

---

### Post by clay on 2006-05-06
haha there is a linux show that we have in san antonio and i have a laptop well for like a dollar you can get a replacement key to what ever you want... i got the linux icon! its cool and now i have it open my email. lol ill see if i can get a pic. 

late.:razz:

---

### Post by enopepsoo on 2006-05-06
any news on what the package is called for Gnome?  I have wanted something like this for a while!  (The only thing I miss about windo$e is win-m to minimize all)

---

### Post by rejser on 2006-05-07
Have alot of hotkeys, but mostly use the win+F1... to switch desktops (desktop1, desktop2 ....)

---

### Post by BitTorrentBuddha on 2006-05-07
[QUOTE=enopepsoo]any news on what the package is called for Gnome?  I have wanted something like this for a while!  (The only thing I miss about windo$e is win-m to minimize all)[/QUOTE]
I believe the easiest way would be to follow instructions on [this thread](http://ubuntuforums.org/showthread.php?t=79560), combined, the programs sound rather close to the KHotkeys in KDE.

---

