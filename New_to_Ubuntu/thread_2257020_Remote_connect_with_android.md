---
title: "Remote connect with android"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by karthikeyan98pdy on 2014-12-16
I am new to ubuntu. I was using windows 8.1 in which I used teamviewer to remote connect to my android. The application was like real slow. In fact I just need to remote control my device in the same network itself. The app I want is similar to this. [Wifi transfer ]("https://play.google.com/store/apps/details?id=com.smarterdroid.wififiletransfer&hl=en") How to do that?? By the way my device is not rooted. If it is required how am i supposed to do that?? Is that good or bad??

---

### Post by TheFu on 2014-12-16
It isn't clear to me which direction you want to go - from Android to Linux or from Linux to Android, sorry.

Seems like using teamviewer would be the best answer still.
Have you tried to install it under Linux?  Google a little to find how, I recall reading about many people doing this.

---

### Post by MartyBuntu on 2014-12-16
> **karthikeyan98pdy said:**
> The application was like real slow.

How slow?

If you're looking for real-time response with TeamViewer or any VNC client/server, you probably won't find it.

There will be *some* degree of lag, even with the most optimal settings and conditions.

---

### Post by nerdtron on 2014-12-16
ESFile Explorer (from the Google Playstore) is what I use to browse/transfer files between my android phone and windows desktop. No need to install software on the computer, all file operations will be made from ESFile Explorer.

---

### Post by TheFu on 2014-12-16
To transfer files to/from Linux FROM android, any sftp client can be used, so can rsync over ssh.  No need for a remote desktop at all.  Best to secure the ssh/scp/sftp server with keys and to run fail2ban (verify it works correctly) to prevent more than a few bogus hacking attempts daily. Of course, don't use password-based authentication for internet-facing ssh.

BotSync and ConnectBot are popular, there are others.

For remote desktops, only NX-based tools have provided acceptable performance for me, but alas, NX will probably never be ported to android.  With a netbook, the x2go client connections are extremely workable from around the world using normal wifi/ethernet connections available. Of course, that doesn't help android users.  I've given up using android devices as remote desktops (after a failed 2 week European trip where I tried) and carry a cheap 11inch netbook (8+ hrs of battery) running a minimal Ubuntu distro. The netbook solution has worked well in 5 different countries on 3 continents.  Just sayin'.

---

### Post by spiffymoo on 2014-12-16
Have you tried the app airdroid?

---

### Post by TheFu on 2014-12-17
> **spiffymoo said:**
> Have you tried the app airdroid?

Loaded Airdroid about 5 min ago - very nice.
Using FF on Ubuntu to do things on my Nexus4 over a local wifi connection.  Not so thrilled about the 3rd party internet connection option, but ... 

None of the ringtones or music will play. Oh well.  "File type not supported."

The ability to download selected, installed, APKs to a computer alone makes this nice.  No sure about the other stuff.  There's a lifehacker article about this that should be good reading.  The remote locate and wipe service could be very useful.  I've had a phone stolen when overseas - didn't have much on it and no access to anything with a complex passphrase first, but still   ... would have been nice to KNOW 100% that a remote wipe worked.

The thing that scares me about this app .... on a locked phone, a remote connection request bypasses the lockscreen and allows access to all files on the device. My phone is encrypted too - so this** bypass without knowing the passphrase is extremely concerning.**  It is also convenient, but this lack of security is frustrating.  Android OS should prevent this regardless of the application. Especially on a non-rooted device, like mine.

**Uninstalled.**

---

