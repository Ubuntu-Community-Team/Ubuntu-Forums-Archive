---
title: "[SOLVED] [C#.Mono]Code does not seem to be operating as expected"
date: 2008-06-29
forum: Programming Talk
---

### Post by Jordanwb on 2008-06-29
Since I do not like Banshee or Rhythmbox, I decided to make my own program in C# using MonoDevelop to manage my music as well as to sync music to my device. I'm starting off with a class that listens for drives being added and removed (like my mp3 player). When it detected a drive, it raises the DriveDetected event (see RemoveableDriveWatcher.txt), when a drive is removed it raises the DriveRemoved event. I have fstab set up to mount one of my partitions to the /media folder (/media/sdc5) on bootup. My mp3 player is /media/disk

The Main.txt class contains a basic class to use the Drive Watcher class. It uses the Console to output when a drive has been added or removed.

Problem:

[1]Program starts (supposed to happen lol)
[2]Program outputs "/media/sdc5 inserted" (this is supposed to happen)
[3]I insert my mp3 player
[4a]Program outputs "/media/sdc5 inserted" (not supposed to happen)
[4b]Program outputs "/media/disk inserted" (supposed to happen)
[5a]I unmount /media/disk
[5b]Program outputs "/media/sdc5 removed" (not supposed to happen, supposed to say "/media/disk removed", this does not happen)

I hope I made the problem clear. Any suggestions would be appreciated.

Also whenever I call "DriveInfo.GetDrives ()", I get this console output that's not supposed to happen.

---

