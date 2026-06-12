---
title: "HOWTO: Run Winamp with iPod Support"
date: 2006-02-09
forum: Outdated Tutorials &amp; Tips
---

### Post by talkingwires on 2006-02-09
I've been frustrated with iPod support in Linux. The dedicated tool, GTKpod, is pretty terrible (it thinks every file is a duplicate, and if you aren't careful it will paste the text of the path into the track name instead of transferring the file over). The iPod offers playcounts and track ratings, but what good are they if they can't be synced with your media player and used to create Smart Playlists? 

Enter [Winamp]("http://winamp.com") and it's iPod plugin, [ml_ipod]("http://mlipod.sf.net"). Together, they offer a full media library, tag editing, playcounts, Smart Playlists, and all the other features you'd expect from a modern music manager. With a little bit of work, I've got them running happily on Linux.[LIST=1]
[*]You'll need to install [Wine]("http://www.winehq.com/"). Fortunately, the developers offer a repository with the latest version. Add this to you /etc/apt/sources.list:```
deb http://wine.sourceforge.net/apt/ breezy/
```You can then install Wine with a simple command:```
sudo apt-get update && sudo apt-get install wine
```
[*]With Wine installed, you can [download and install Winamp]("http://winamp.com/player/free.php"). Grab the "Full" version, as you'll need the Media Library plugin. Open the executable with Wine (right-click and select "Open with Wine Windows Emulator"). During the installation, deselect the options for "Modern Skin Support" (it works, but you'll have much better results with Classic Skins), "User Interface Extensions", "Video File Support" (it's a little flaky), and "Winamp Agent".
[*]Now you can [install ml_ipod]("http://sourceforge.net/project/showfiles.php?group_id=106528"). Launch the executable, and install.
[*]Okay, you've got Winamp and ml_ipod, but they won't recognize your iPod if you plug it in. We need to create a Windows Drive for Wine to mount the iPod. If your iPod is mounted at /media/ipod, then you'd use:```
cd ~/.wine/dosdevices
ln -s /media/ipod "j:"
```
[*]One last step! Launch Winamp (it's installed at ~/.wine/drive_c/Program Files/Winamp/winamp.exe), right-click on the main window and select Options/Preferences. Click on "iPod Support". Finally, in the "Misc" options, check the box for "Look for iPods on network drives and fixed drives (not recommend)". Ignore the recommendation. ;) Restart Winamp. After a few seconds, your iPod should be detected. Huzzah!
[/LIST]With any luck, you should now have great media player with excellent support for iPods. A little further hacking, and you could probably link your copies of Window in Windows and Linux, and share the same music database. Wouldn't *that* be something?

---

### Post by justutkarsh on 2008-05-04
Does media library shows up in winamp before ipod plugin is installed
which winamp and wine version are you using

---

### Post by talkingwires on 2008-06-03
> **justutkarsh said:**
> Does media library shows up in winamp before ipod plugin is installed
which winamp and wine version are you using
This guide was written for Breezy, which is an old, old release that isn't even supported anymore. I think Winamp was an early release on the 5.0x series, probably 5.02, and Wine may have been one of the first in the 0.9x series.

This guide should be rewritten for more modern software, because I'm sure things have changed in the past two years...

---

