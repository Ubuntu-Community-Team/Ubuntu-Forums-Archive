---
title: "Cannot execute files on Windows Share without lockups"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by JHXG7xN on 2013-09-01
I've been making the switch over to lubuntu from xp and am 99% there re apps, custom keyboard shortcuts etc but there is one roadblock that ive tried to find a solution for but haven't had any luck.

I can connect to the share on my Win 7 PC through smb and even drag and drop files from it onto my Lubuntu desktop but if i try to run the file via smb connection by double clicking it locks up what ever program it runs. It does this with both video and audio i even installed a couple of different media players but it locks them all up the same.

When it locks up the program it is unkillable even using task manager it just say "Killing" in the title of the window but it never disappears.

I can open some filetypes though including PDF CBZ TXT. Jpg/png is iffy sometimes it is ok and other times it locks up image viewer.

I also noticed that if i drag and drop via smb a file with spaces in the name it will add %20 where the spaces should be i dunno if that is normal or not.

I should also point out that if i boot in XP the shares work flawlessly so i dont think it is bandwidth issue. I also tried the ubuntu-desktop before lubuntu and that also streamed flawlessly but the whole desktop was very sluggish when doing anything, else hence why i installed a more lightweight alternative for my older laptop.

My Win7 shares are read only for safety due to me accidentally deleting some files once in XBMC.

I hope that is enough info

thanks

---

### Post by TheFu on 2013-09-01
Lots of details, but I'm not clear.
Which OS is the server and which OS is the client?
When you say "smb" - specifically, which program are you using?
Have you considered just mounting the shares with the "mount" command?  Using the GUI tools to access remote files is convenient, but doesn't really "mount" them for the entire OS.  I stream constantly using remote mounts with an XMBC/Ubuntu setup. Never any issue.  BTW, do not use wifi.

---

### Post by JHXG7xN on 2013-09-02
Thanks for the reply

I solved the problem by monitoring the network in system monitor and killing off processes in task manager. It appears during my initial tinkering i installed the file manager nautilus after reading a post elsewhere and incorrectly thinking it would auto mount network drives.

I double clicked a remote mp3 to get the error and noticed that the network speed was stuck at the max 3MBps my wifi seems to be able to handle despite the file being a 128kbps mp3. I killed nautilus and the media player unlocked but didn't play so i tried it again and it played flawlessly.

I uninstalled nautilus and rebooted and now it plays video/music fine although pictures still lock up the picture viewer.

I'm going to have a look further into trying to sort out mounting the network drive later but right now im not at home

Regarding your questions

Windows 7 is Server version is Windows 7 Home Premium 64-bit (6.1, Build 7601) Client us lubuntu latest build as of 3 days ago
SMB - I typed the url in the address bar of PCManFM ie smb://my-pc/users/myusername/music/
Mounting - I have tried since reading your reply but it wouldn't work i got either time outs or asked for a password when i tried using the IP instead of server name even though there is no password.
WiFi - It works fine in XP as long as it's not a 1080p mp4 and since i sorted out the problem with nautilus i did watch a full 90 minute movie on it last night which played fine in vlc.


> **TheFu said:**
> Lots of details, but I'm not clear.
Which OS is the server and which OS is the client?
When you say "smb" - specifically, which program are you using?
Have you considered just mounting the shares with the "mount" command?  Using the GUI tools to access remote files is convenient, but doesn't really "mount" them for the entire OS.  I stream constantly using remote mounts with an XMBC/Ubuntu setup. Never any issue.  BTW, do not use wifi.

---

### Post by TheFu on 2013-09-02
> **JHXG7xN said:**
> Thanks for the reply

I solved the problem by monitoring the network in system monitor and killing off processes in task manager. It appears during my initial tinkering i installed the file manager nautilus after reading a post elsewhere and incorrectly thinking it would auto mount network drives.

I double clicked a remote mp3 to get the error and noticed that the network speed was stuck at the max 3MBps my wifi seems to be able to handle despite the file being a 128kbps mp3. I killed nautilus and the media player unlocked but didn't play so i tried it again and it played flawlessly.

I uninstalled nautilus and rebooted and now it plays video/music fine although pictures still lock up the picture viewer.

I'm going to have a look further into trying to sort out mounting the network drive later but right now im not at home

Regarding your questions

Windows 7 is Server version is Windows 7 Home Premium 64-bit (6.1, Build 7601) Client us lubuntu latest build as of 3 days ago
SMB - I typed the url in the address bar of PCManFM ie smb://my-pc/users/myusername/music/
Mounting - I have tried since reading your reply but it wouldn't work i got either time outs or asked for a password when i tried using the IP instead of server name even though there is no password.
WiFi - It works fine in XP as long as it's not a 1080p mp4 and since i sorted out the problem with nautilus i did watch a full 90 minute movie on it last night which played fine in vlc.

* Nautilus is simple for mounting, but it seems to interfere with **real** mounts. Just helped someone else work through this issue TODAY. Using nautilus for anything more than trivial uses isn't good.   PCManFM has never mounted much for me - I think both of these are based on gvfs - which is a FUSE mount manager. Avoid.
* Streaming video over wifi is not good. Wifi is great for sporadic traffic, but not when you need a constant stream with lots of bits, like video demands. This lack of constant bandwidth, can be overcome by larger caching.
* Streaming audio over almost any connection should be fine. The bitrates are tiny.

Suggest that you plug into a wired ethernet connection for all testing until you get this solved, then try with wifi.  The method is to simplify, get it working, then add 1 complexity back, retest, continue.

The real mount command is not FUSE. It runs at kernel level with much less overhead that FUSE mounts.

Don't confuse audio bitrates with network bitrates.  Very few people/services actually stream audio files, they download and playback. For large files, the playback might start before the entire file is local.

Windows7 is NOT a server OS.

I use LXDE too. Excellent choice.

---

### Post by JHXG7xN on 2013-09-03
I managed to get it all working ok using the ip address in the the mount command instead of the server name. Ive also set them up to auto mount on boot in etc/fstab (after backing up the file for safety)

thanks for the help/suggestions

---

