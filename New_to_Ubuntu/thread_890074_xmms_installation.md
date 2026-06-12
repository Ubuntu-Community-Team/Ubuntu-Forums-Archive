---
title: "xmms installation"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-08-14
i downloaded it via synaptic and i dont have any form of gui. however when i type xmms in the terminal it comes up as a terminal program.

---

### Post by tangibleorange on 2008-08-14
how do you mean 'form of gui'? do you mean a shortcut? if so, you need to create a launcher:

[LIST]
[*]right click anywhere on the desktop and select 'Create Launcher'
[*]give the shortcut a name
[*]for the command, type 'xmms' (no quotes)
[*]you don't need to enter a description
[/LIST]

now when you click the launcher, it should launch xmms!

---

### Post by WinterMadness on 2008-08-14
> **tangibleorange said:**
> how do you mean 'form of gui'? do you mean a shortcut? if so, you need to create a launcher:

[LIST]
[*]right click anywhere on the desktop and select 'Create Launcher'
[*]give the shortcut a name
[*]for the command, type 'xmms' (no quotes)
[*]you don't need to enter a description
[/LIST]

now when you click the launcher, it should launch xmms!

i did that and i got an error something about failing to load child process? I guess that would be the interface.

and what i mean by no gui, i mean that the only way i can use xmms is in the terminal. i dont have a typical application that would not be in the terminal. Its all text based.

---

### Post by tangibleorange on 2008-08-14
did you add an extra repository to download xmms? i tried using apt-get and it couldn't find it...

---

### Post by WinterMadness on 2008-08-14
> **tangibleorange said:**
> did you add an extra repository to download xmms? i tried using apt-get and it couldn't find it...

i went through synaptic and just downloaded the file, and all the other files it recommended.

---

### Post by tangibleorange on 2008-08-14
hmm. that's weird. i'm afraid I've no idea other than reinstalling it via synaptic. when you type 'xmms' at a terminal, do you see any error messages at all?

---

### Post by WinterMadness on 2008-08-14
> **tangibleorange said:**
> hmm. that's weird. i'm afraid I've no idea other than reinstalling it via synaptic. when you type 'xmms' at a terminal, do you see any error messages at all?

heres what i get. its "xmms2" btw i didnt see just xmms in synaptic

ghost@laptop:~$ xmms
bash: xmms: command not found
ghost@laptop:~$ xmms2
Available commands:
  add - adds a URL to the playlist
  addarg - adds one URL with arguments to the playlist
  addid - adds a Medialib id to the playlist
  insert - inserts one URL at a specific position
  insertid - inserts one Medialib id at a specific position
  radd - adds a directory recursively to the playlist
  clear - clears the playlist
  shuffle - shuffles the playlist
  sort - sort the playlist; use a space delimiter for multiple properties
  remove - removes something from the playlist
  list - lists the playlist
  addpls - Adds the contents of a playlist file to the playlist
  play - starts playback
  stop - stops playback
  toggleplay - toggles playback status between play/pause
  pause - pause playback
  next - play next song
  prev - play previous song
  seek - seek to a specific place in current song
  jump - take a leap in the playlist
  move - move a entry in the playlist
  volume - set volume for a channel
  volume_list - list volume levels for each channel
  mlib - medialib manipulation - type 'xmms2 mlib' for more extensive help
  playlist - playlist manipulation - type 'xmms2 playlist' for more extensive help
  coll - collection manipulation - type 'xmms2 coll' for more extensive help
  browse - browse server file lists
  status - go into status mode
  info - information about current entry
  current - formatted information about the current entry
  config - set a config value
  config_list - list all config values
  plugin_list - list all plugins loaded in the server
  stats - get statistics from server
  quit - make the server quit
  help - print help about a command
ghost@laptop:~$

---

### Post by tangibleorange on 2008-08-14
OK try pressing Alt+F2 and then typing xmms2 into the box that appears.

If that doesn't work, try with a re installation of package xmms2 via synaptic.

---

### Post by WinterMadness on 2008-08-14
> **tangibleorange said:**
> OK try pressing Alt+F2 and then typing xmms2 into the box that appears.

If that doesn't work, try with a re installation of package xmms2 via synaptic.

unfortunately neither worked

---

### Post by cariboo on 2008-08-14
I think he downloaded xmms2 as xmms is not available from the repositories any more. For a frontend for xmms2 search synaptic package manager for xmms2 client.

Jim

---

### Post by cozmicharlie on 2008-08-14
If you want to install xmms - follow this tutorial.
[http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)

> did that and i got an error something about failing to load child process?

This means you do not have all the dependencies.  The tutorial shows how to install them.

Enjoy

---

