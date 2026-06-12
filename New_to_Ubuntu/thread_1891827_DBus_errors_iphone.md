---
title: "DBus errors iphone"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by fattyz on 2011-12-06
Hi I am trying to get my iphone so I can drag and drop music files from ubuntu 10.04. whilst trying to update ipeth-utils via the following I get asked for the install cd?[http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/iphone-tethering-on-ubuntu-9-10-karmic.html)

I've had it working before but im stumped right now.

Thanks 

FattyZ

---

### Post by fattyz on 2011-12-07
oops!  got it.

Fattyz

---

### Post by fattyz on 2011-12-11
I thought I had this but no.  It seems I don't really remember if I had the iphone correctly working in any of my Ubuntu installs.  So far I have done everything I can find.

pmcenry repo installed 
libimobiledevice is newest
ipheth-utils is newest

I still get dbus errors when i plug in the usb cable, the phone mounts and appears on the desktop and I can transfer pictures from it to the pc but if I try to copy music files to it from rhythmbox I get the following


Error while getting peer-to-peer dbus connection: The name :1.59 was not provided by any .service files

If I drag and drop music from the desktop to the phone it looks like its working and you can see the file on the phone but the phone never displays "sync in progress" and the file never actually gets to the phone.

I've been reading a lot about this and I thought I got it before by using

idevicepair and etc but it is not working

Thanks

---

### Post by fattyz on 2011-12-11
This is crazy, there has to be a better way, we need an iphone sticky thats for sure.

I killed the dbus process (sudo /etc/init.d/dbus restart).  Restart once, no network manager, you have to restart again.  Then dragged a file to the iphone and got a status bar, so I knew something was different.  (This is using rhythmbox)

Then I drag and drop to a folder in itunes control and sync in progress came on.  It was slow but it worked.  

If you are searching for a solution to getting your iphone to work in 10.04 (or I think any version of ubuntu)  you are probably in for an arduous slog. I hope you find this more quickly than I did.  It's hardly what I'd call native or out of the box support.  

(Next time I have to do a clean install I'll have this to look at and remember how I did it)

---

### Post by fattyz on 2011-12-13
DBus error org.freedesktop.DBus.Error.InvalidArgs: Mountpoint Already registered

Ok this is ongoing so I thought I's try another question, I can get the phone to sync in spite of this error, but I have to restart the dbus daemon.  (sudo /etc/init.d/dbus restart)i

This is fine but not really.  Is it possible that I have to do this and restart the computer twice just to copy and mp3 file to the iphone?

---

### Post by fattyz on 2011-12-13
I meant to ask if anyone knew if an update to 10.10 would do anything about this problem, I honestly can't remember.  I don't want to go up to  11.xx because I got a black screen on this laptop after an upgrade and I'm not risking that again.

Everything is up and running now and I'm going to have to have a good reason to do ANY version upgrade for awhile given what's involved in getting everything working after each upgrade.

Thanks

---

### Post by fattyz on 2011-12-21
Today after update manager I get a new message each time i plug the iphone in.  It says I plugged in a messed up ipod and would i like to initialize and if I do ill lose all my songs! (nice) Two boxes at the bottom of the dialogue.  

First (greyed out) select ipod model
Next Name.

I just close it and it's business as usual.

---

### Post by cheatos on 2012-01-07
> **fattyz said:**
> 
This is fine but not really.  Is it possible that I have to do this and restart the computer twice just to copy and mp3 file to the iphone?


Is it true, that you can copy mp3s to the iPhone and it will work?

Some people on here and other forums always told me, that the iPhone will not be able to play the mp3s as it only works if they are registered in some kind of database on the phone via iTunes.

(I already have seen how iTunes saves the music and I believe that there has to be such a DB, but if it also works with mp3s just copied, could you explain me how?)

---

### Post by jmyette on 2012-01-09
> **cheatos said:**
> Is it true, that you can copy mp3s to the iPhone and it will work?

I remember being able to play mp3s (and even oggs) that were copied from Linux to my iPhone. But this was under iOS 4. Since I've upgraded to iOS 5, this doesn't work anymore so I now use iTunes from Windows to transfer the files (only mp3s work now).

---

### Post by cheatos on 2012-01-12
I'm still on iOS 4.3.3, so do you still know how you did that?
Would be pretty awesome...

---

### Post by fattyz on 2012-01-14
I have only gotten it to work marginally by stopping the dbus process and rebooting.

All over the net everyone seems to be able to get native support by upgrading libimobiledevice from pmecenry repo but I can't make it work.  Now that I upgraded to ios 5 my iphone won't mount at all and I have to go back to winblows to load songs on it.

In my experience ubuntu never really worked as well at transferring music to the iphone as windows. It still dosen't.  In particular because there is no music on the file sharing programs.  If I want 4 or five songs quick I go to windows and use Ares, then use Media monkey or itunes to drag and drop onto my iphone.  This only takes a few minuets.  You just can't do that on Ubuntu.

FattyZ

---

