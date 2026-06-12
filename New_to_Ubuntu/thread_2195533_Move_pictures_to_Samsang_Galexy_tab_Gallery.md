---
title: "Move pictures to Samsang Galexy tab Gallery"
date: 2013-12-24
forum: New to Ubuntu
---

### Post by bob brazie on 2013-12-24
I have been working to try and find out how to move my pictures from my 13.10 install to the gallery in my new tab 10.1.

I moved some pictures into the "pictures" folder in the tab. They show up in that file/folder but I can't seem to find a way to move them or have them show in the gallery app.

I cannot find a folder on the tab for "gallery".

I have tried several Google searches and looked for a specific Galaxy help site but came up empty,

Thanks in advance. Bob.

---

### Post by ajgreeny on 2013-12-24
I'll be surprised if you can't find something at [https://www.google.co.uk/search?q=samsung+galaxy+forum&ie=UTF-8](https://www.google.co.uk/search?q=samsung+galaxy+forum&ie=UTF-8)

---

### Post by tgalati4 on 2013-12-24
I went the other way using ES File Manager on the phone to move gallery photos to Ubuntu, so I guess you could reverse the process.

Gallery photos are stored in a directory that is not accessible when simply plugged in to Ubuntu.

Load ES File Manager onto your phone.  Go to External SD Card, DCIM, Camera and your photos will show up.  Then Go to Tools, Remote Manager, Turn On.

It gives you an address:  [ftp://192.168.1.100:3721](ftp://192.168.1.100:3721).  Put that in Nautilus or your browser.  You can dump photos from Ubuntu into a directory (such as Download).  Then go on your phone and copy (or cut) photos into the Camera directory.  Because the Camera directory is owned by "root" you don't have direct access through ftp.  I'm sure there is a better, more elegant way to do this, but I haven't found it.

A Haiku of Samsung frustration:

Samsung runs Android.
Android is like linux, but,
You can not move files!

---

### Post by bob brazie on 2013-12-25
Thanks for the information. Where do I find ES File manager?

---

### Post by kostkon on 2013-12-25
> **bob brazie said:**
> Thanks for the information. Where do I find ES File manager?
[In the Play store]("https://play.google.com/store/apps/details?id=com.estrongs.android.pop"). It's by far the best file manager on Android AFAIK.

---

