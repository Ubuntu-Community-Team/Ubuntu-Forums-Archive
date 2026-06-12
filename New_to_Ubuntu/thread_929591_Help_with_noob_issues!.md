---
title: "Help with noob issues!"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kenny99 on 2008-09-25
Hi there, right - apologies in advance for the noob questions but I've just been convinced to drop Windows and go with Linux as my OS. So I've downloaded the most recent version of Ubuntu and have come some of the way to getting things up and running. 

I do have some teething problems, however, which I'm hoping you guys can help me with! 

[LIST]
[*]There seems to be no way just to double click things to make them run, everything has to be done in command line, which I was dreading. for example -
trying to extract .rar files. I have gone into synaptic package manager and installed "unrar", try to open an archive "using unrar" and nothing happens, looked it up and it looks like I have to write 100 lines of code to make it happen!

[*]not even attempted to install nero but it looks a nightmare

[*]have downloaded java but not installed yet (see above)

[*]The sound drivers seem an bit low powered. Also if you play music while a browsers open then when you pause it and play a youtube video, the sound doesn't work, you have have to restart firefox. a small complaint but irritating.

[*]i occasionally get an error when trying to open firefox, it says already running - close or restart system, the fixes i have read so far do not work so i have to reboot, v annoying.

[*]external drives automatically unmount when you shut down so shortcuts to folders etc on them appear as broken next time you log in.

[*]still can't mount one of my flash drives even though i am entering the suggested code (which worked for the other drives).

[*]Also the packaged torrent manager wont open some torrent files, says not a valid file, but I've got them from the same site i've always used and never seen that before.

[*]the media player is a bit buggy, sometimes sticks or crashes when you try to search within a track.
[/LIST]

Let me know if you need more info on any of the above, thanks in advance for any help

---

### Post by collinp on 2008-09-25
> **kenny99 said:**
> 

[LIST]
[*]There seems to be no way just to double click things to make them run, everything has to be done in command line, which I was dreading. for example -
trying to extract .rar files. I have gone into synaptic package manager and installed "unrar", try to open an archive "using unrar" and nothing happens, looked it up and it looks like I have to write 100 lines of code to make it happen!
[*]not even attempted to install nero but it looks a nightmare
[*]have downloaded java but not installed yet (see above)
[*]The sound drivers seem an bit low powered. Also if you play music while a browsers open then when you pause it and play a youtube video, the sound doesn't work, you have have to restart firefox. a small complaint but irritating.
[*]i occasionally get an error when trying to open firefox, it says already running - close or restart system, the fixes i have read so far do not work so i have to reboot, v annoying.
[*]external drives automatically unmount when you shut down so shortcuts to folders etc on them appear as broken next time you log in.
[*]still can't mount one of my flash drives even though i am entering the suggested code (which worked for the other drives).
[*]Also the packaged torrent manager wont open some torrent files, says not a valid file, but I've got them from the same site i've always used and never seen that before.
[*]the media player is a bit buggy, sometimes sticks or crashes when you try to search within a track.
[/LIST]
 
[LIST=1]
[*]Alot of things still have to be done in terminal. There probably is a GUI way, but it takes far longer.
[*]Nero for Windows? You need wine for linux.
[*]Java should be easy to install
[*]That is a bug with the audio system, PulseAudio is possibly the most buggy i have seen.
[*]That error should stop after you try to open a few times (It happens to me)
[*]the Linux Kernel automatically unmounts everything, excluding internal hard drives.
[*]have you tried to run "mount (your flash drive)" in terminal?
[*]there are hundreds of other torrent managers around, google
[*]dont know
[/LIST]

---

### Post by muteXe on 2008-09-25
Who convinced you to drop windows?
Did you even try linux/ubuntu on a live cd before installing it?
Did you research anything about linux/ubuntu before installing just to see if it was for you or not?

This is a good place to start:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

That will show you how to mount external drives etc etc

Posting your machine specs may help with the other problems.
Typing "unrar <filename>"  should unpack your files.

When you installed, did you get all of the updates from the update manager?  That might help with the FF bugs.

You can double-click stuff if it's on your desktop.  Else you pick it from the menus or use the command line.  You will learn to love the command line :)

Which media player do you use?  Check out this:

[http://en.wikipedia.org/wiki/Category:Linux_media_players](http://en.wikipedia.org/wiki/Category:Linux_media_players)


mute

---

### Post by robert shearer on 2008-09-25
You really don't need Nero.
 Use the default burning app Brasero.
Applications=>Sound & Video=>Brasero disc burning.

and if you want an alternative then open Synaptic Package Manager and use its search box to find and install  k3b. 
and once installed then..
Applications=>Sound & Video=>k3b

They are both easy to use and have good Help options.

---

### Post by Ryadt on 2008-09-25
- Unrar a file in terminal is only a one line command: ```
unrar -x.file.unrar
```. You can also just right-click and choose 'extract here'.
- You don't need Nero. There are linux alternatives that you can use like K3b.
- Just install java through the synaptic package manager.
- This a problem with pulseaudio. Change the settings to alsa in Preferences > Sounds. Or do ```
killall pulseaudio
```.
- Try ```
killall firefox
``` when you get this issue.
- Try mounting with the terminal.
- Try other torrents' client.
- Which media player are you using? Try vlc.

---

### Post by kenny99 on 2008-09-25
Thanks guys for the quick replies! Just to be clear, I wasn't wanting to come across negative, I'm enjoying the learning curve but I was looking for some help with the issues i listed, which you've all provided. A friend recommended Linux and I was quite happy to dive in and give it a try, if i don't dig it i can always revert to windows, which i definitely can't see happening! 

Anyway, loads of good tips here so thanks again, very much appreciated.

Edit: will check out everyone's suggestions and will no doubt report back here if i'm still having issues

---

### Post by LunatikOwl on 2008-09-25
Also you might want to install ubuntu-restricted-extras package to add a lot of potentially non-free but somewhat convenient software to Ubuntu. It contains among others unrar(embedded in gnome archive manager), Java, Flash, and some 'non-free' font you'll probably need. Hope you'll enjoy using this great distro:)

---

### Post by onero on 2008-09-25
> **kenny99 said:**
> Hi there, right - apologies in advance for the noob questions but I've just been convinced to drop Windows and go with Linux as my OS. So I've downloaded the most recent version of Ubuntu and have come some of the way to getting things up and running. 

I do have some teething problems, however, which I'm hoping you guys can help me with! 

[LIST]
[*]There seems to be no way just to double click things to make them run, everything has to be done in command line, which I was dreading. for example -
trying to extract .rar files. I have gone into synaptic package manager and installed "unrar", try to open an archive "using unrar" and nothing happens, looked it up and it looks like I have to write 100 lines of code to make it happen!

[*]not even attempted to install nero but it looks a nightmare

[*]have downloaded java but not installed yet (see above)

[*]The sound drivers seem an bit low powered. Also if you play music while a browsers open then when you pause it and play a youtube video, the sound doesn't work, you have have to restart firefox. a small complaint but irritating.

[*]i occasionally get an error when trying to open firefox, it says already running - close or restart system, the fixes i have read so far do not work so i have to reboot, v annoying.

[*]external drives automatically unmount when you shut down so shortcuts to folders etc on them appear as broken next time you log in.

[*]still can't mount one of my flash drives even though i am entering the suggested code (which worked for the other drives).

[*]Also the packaged torrent manager wont open some torrent files, says not a valid file, but I've got them from the same site i've always used and never seen that before.

[*]the media player is a bit buggy, sometimes sticks or crashes when you try to search within a track.
[/LIST]

Let me know if you need more info on any of the above, thanks in advance for any help

Ok, first to clear up some misconceptions: people give terminal commands a lot, but most of the time, they aren't necessary and there's an equivalent GUI for the action. It's just easier (and unambiguous) to give one-line terminal commands than saying click Applications > System > Preferences, etc.

Case in point: you don't need to do anything in the terminal to unrar files. Right click > Extract here or double clicking the rar file to open File Roller (which is the name of the archive program) should be sufficient. 

Another example: if you want to kill processes from a GUI instead of a terminal (say, Firefox), you can just put the System Monitor applet on your panel and click it and go to the Processes tab. You can look for the process there, right click, and choose end process. (Phew, that was a long explanation compared to just giving the killall command. See, this is why people like giving terminal commands. It's much more complicated explaining steps via the GUI.)

Another thing: you seem to be aware of Synaptic and know how to use it, so here's a hint: most of the stuff you need can be found in there. Why would you download Java? Just install it from Synaptic.

If the built-in programs aren't up to par, I can recommend some alternatives; I use Deluge as my torrent program, it's really good. For music, I use Exaile but it may be a bit buggy and they're undergoing a major code rewrite so I guess I wouldn't recommend it for everyone; Banshee is also pretty popular. Make sure to use the Banshee repositories to get an updated version. If you don't know what third-party repositories are or how to add them. take a look at the Sticky about installation or search the forums.

Similarly, there's no need for Nero, since Ubuntu comes built-in with most utilities. You can use Brasero for CD burning. If you really want to install Nero though, there is a Linux version. Just download a deb file from the Nero site. A .deb file is just like an installer; you just double-click it to install (it will just be a local install, and won't be auto-updated like other programs installed through Synaptic). For movies and DVD playback, just install VLC.

The sound issue is due to Pulseaudio and Flash problems. Follow this post: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by billgoldberg on 2008-09-25
> **kenny99 said:**
> Hi there, right - apologies in advance for the noob questions but I've just been convinced to drop Windows and go with Linux as my OS. So I've downloaded the most recent version of Ubuntu and have come some of the way to getting things up and running. 

I do have some teething problems, however, which I'm hoping you guys can help me with! 

[LIST]
[*]There seems to be no way just to double click things to make them run, everything has to be done in command line, which I was dreading. for example -
trying to extract .rar files. I have gone into synaptic package manager and installed "unrar", try to open an archive "using unrar" and nothing happens, looked it up and it looks like I have to write 100 lines of code to make it happen!

[*]not even attempted to install nero but it looks a nightmare

[*]have downloaded java but not installed yet (see above)

[*]The sound drivers seem an bit low powered. Also if you play music while a browsers open then when you pause it and play a youtube video, the sound doesn't work, you have have to restart firefox. a small complaint but irritating.

[*]i occasionally get an error when trying to open firefox, it says already running - close or restart system, the fixes i have read so far do not work so i have to reboot, v annoying.

[*]external drives automatically unmount when you shut down so shortcuts to folders etc on them appear as broken next time you log in.

[*]still can't mount one of my flash drives even though i am entering the suggested code (which worked for the other drives).

[*]Also the packaged torrent manager wont open some torrent files, says not a valid file, but I've got them from the same site i've always used and never seen that before.

[*]the media player is a bit buggy, sometimes sticks or crashes when you try to search within a track.
[/LIST]

Let me know if you need more info on any of the above, thanks in advance for any help

You seem to be confused on how to install stuff in Ubuntu.

Ubuntu works with software repositories. These repositories contain thousands of programs. Those programs can be install in a few ways.

The easiest way (but not good for advanced stuff) is by going to "applications -> add/remove".

A better way is by going to "system -> administration -> synaptic".

The rest are cli ways.

1. Unrar integrateds with fileroller. Fileroller is the standard archive manager. I myself use the superior "p7zip-full" program and I can just right-click any archive and extract it.

2. At this point, I suggest you just run this command.

Besides java and flash, it will install loads of media codecs. I'm sure you'll need them some day.  Go to "applications -> accessories -> terminal" and copy/paste this:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

Watch the terminal while it progresses. You might have to press enter of "y" a few times.

3. There is no reason to buy for Nero burning software. That standard installed software (brasero) is more than capable to burn all kind of things. 

4. Go to "system -> preferences -> sound". Switch everything to ALSA in the dropdown menu's.

That will fix your problem with the sound in firefox.

Now install the package "gnome-alsamixer" either using "synaptic" or by copy/pasting this in a terminal:

```
sudo apt-get install gnome-alsamixer
```

Afterwards, the program will be in "applications -> sound & video".

Open it and max everything out. This will fix your low volume complaint.

5. You'll need to mount then (double click on the icon) before the links will work.

However you can make it so they automount on startup. So the links will always work.

I suggest you google "*automount drive ubuntu hardy*".

6. If you insert a flash drive into your computer, it will automatically open in nautilus. No need to go into the CLI to mount it.

*(who the hell has been feeding you this nonsense?)*

7. If you aren't happy with Transmission (I am), I suggest you use Deluge. 

It's in the repo's, but a newer version can be downloaded from their site.

I don't know exactly in what format it will be available, but I think it will be a .deb package. Those are installed by double clicking them.

8. I don't have any problem with Totem, but I prefer VLC media player.

Again, it's in the repo's, so download it using Add/Remove or Synaptic.

--

Things in Ubuntu are done differently than on other platforms.

But that doesn't mean it's harder.

---

