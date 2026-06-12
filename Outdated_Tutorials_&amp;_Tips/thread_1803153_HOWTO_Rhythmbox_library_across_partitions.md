---
title: "HOWTO: Rhythmbox library across partitions"
date: 2011-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Jalaska13 on 2011-07-12
Say you're dual-booting, and Ubuntu is a secondary partition.  You've got music on your other partition (perhaps Mac or Windows) that you'd like to have access to in Ubuntu.  Besides the permissions issue (which I won't cover), you need a way to not have duplicates of your music library so that maintenance is minimal.  There are a few requirements:
-Be able to access your main music library from Rhythmbox
-Be able to add music to your main music library and play it from Rhythmbox without having to manually add it
-Be able to add music directly to Rhythmbox that doesn't conflict with your main music library.

First, you need to make sure that your main partition is always mounted when booted in Ubuntu.  I suggest making a startup script something like this (you need to create /mnt/sda1/ ahead of time):

sudo mount /dev/sda1 /mnt/sda1/

The second step is the key.  Rhythmbox can accept a single directory as its library directory.  It will add new music to this, keep it sorted, and monitor the directory for new music.  However, we can't use the main partition's music directory for this because Rhythmbox would then add new music there, which would be in a file structure incompatible with your main OS's media manager.  Thus, I suggest the following startup script that will essentially create a portal to the main music library in Ubuntu's /home/user/Music/ folder so that you can both add music and autodetect music that's been added to your main partition.  The folder /home/user/Music/OtherOS/ needs to be created ahead of time:

sudo mount --bind /mnt/sda1/.../Music/ /home/user/Music/OtherOS/

This way, Rhythmbox will keep ~/Music organized and add new music to it, and will also see when music has been added to ~/Music/OtherOS/, thus autoimporting music you add while in your main OS.

---

### Post by sudodus on 2013-06-09
It has the (pad)lock symbol, that it is locked, and we'll soon find out if I can post

---

