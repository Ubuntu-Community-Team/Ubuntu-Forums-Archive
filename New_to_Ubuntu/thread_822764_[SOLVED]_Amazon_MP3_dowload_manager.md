---
title: "[SOLVED] Amazon MP3 dowload manager"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by hufferd on 2008-06-08
Ok so i am trying to down load some music from Amazon.com.  Its says I need to install the download manager ......  2 things the last supported ver on their web site is 7.10 as you can see in my tag line Im running 8.04 64 bit....

So I download the client for 7.10 -- well The deb package manager will not install because why?  It is a 32 bit app on a 64 bit box. :( (Me = starting to think I need to go back to a 32 Bit system because no one seems to be supporting 64 bit..  But thats another topic)

So I go to the terminal window and force the install ........  there wweere some errors ..... now when I try to run the down load manager it wont start? 

Any ideas ..?  ....  and I really am thikning about going back to a 32 bit ver of unbuntu every time I try to install something I have to use a work around ..... No one seems to be supporting 64 bit yet....


Thanks Dan

---

### Post by cookies on 2008-06-08
You don't really NEED it. You can just download MP3s from Amazon directly. As for the install, I'm not quite sure.

---

### Post by hufferd on 2008-06-08
Ah well there must be something else wrong then cause I downloaded one mp3 file and it showed up as a text only file -- I thought it may have been because I did not use the down load manager
:(

---

### Post by HalPomeranz on 2008-06-08
Have you installed ia32-libs?  That clears a lot of problems running 32bit binaries on AMD64.

---

### Post by hufferd on 2008-06-08
Its not downloading as an MP3 file is some it has an .amz extension on it :(

---

### Post by hufferd on 2008-06-08
Yes I have installed 32bitlibs And I am running other 32bit apps


:(

---

### Post by MillDaKill on 2008-06-10
I am having the exact same problem, any help would be great.  To purchase an album at the special album price which is cheaper than buying the songs one by one, you need to have the downloader.

---

### Post by Eric Qel-Droma on 2008-06-24
Total Ubuntu Newbie posting here.  (I just installed everything yesterday, but couldn't get Internet working until today!)

I have the same questions as these other folks, and they're absolutely right:  If you want to buy an MP3 album (which gets you a discount), you need the download manager.  Now, Amazon is trying to be very helpful, Linux-wise, as they have download buttons for several distros, but they're a little behind on Ubuntu (they only have 7.10 listed).

So:

1) Can we install the 7.10 stuff "as is" straight from Amazon?
  a) Follow-up:  Why or why not?
  b) Follow-up:  If we can, should we do it this way, or is there a repository version or something somewhere else?

2) Actually, I guess I don't have a #2 here.  Oh, well.

Thanks!

Eric

---

### Post by MichiganMan on 2008-07-14
> **Eric Qel-Droma said:**
> 

1) Can we install the 7.10 stuff "as is" straight from Amazon?
  a) Follow-up:  Why or why not?
  b) Follow-up:  If we can, should we do it this way, or is there a repository version or something somewhere else?

2) Actually, I guess I don't have a #2 here.  Oh, well.

Thanks!

Eric

Just came across this as I just ran into the problem today.  Guess I haven't downloaded any albums since I upgraded to Hardy.  

Anyways, yeah, Amazon is behind and no indication of an update coming.  The downloader for Gutsy will install fine, but it won't run.  I believe there is a dependency that has been updated in Hardy, (forget the name...) and the downloader obviously doesn't like it.  Looking at the threads here on UF I see instructions on where to get the dependencies to make it work, but IMO its easier just to use the Windows version under wine while you're waiting for Amazon to realize they might want to consider supporting an LTS version of Ubuntu.

To install the Windows version just download it from Amazon.  Assuming your Wine is up and running, use it to install the downloader.  You can start the downloader from the wine menu in Gnome, but to use it on an album (which is the point) you'll have to launch it from the command line in Terminal. This is because while it runs under Wine, attempting to use a menu to point to an .amz file will bring a crash.  

So, download your *.amz file.  Lets call it Barney's Friends.amz.  Copy it to the downloader's directory.  That will be: /home/You/.wine/drive_c/Program Files/Amazon/MP3 Downloader

Now navigate there in terminal.  Remember, autocomplete (shift) is your friend.  Once in the directory, start up the downloader with the .amz file in the command:

```
 wine AmazonMP3Downloader.exe Barney's Friends.amz
```

The downloader should then start up and begin downloading the album.  It will save it in Amazon MP3 in your home directory.  

Its not perfect, but it worked for me while we were waiting for the Gutsy downloader, and it worked for me again this morning.

---

### Post by vigleik on 2008-07-23
Just be careful, wine might not work. For me it kept crashing, with this error message:

> err:ole:_jpeg_fill_input_buffer (), should not get here.
fixme:ole:OLEPictureImpl_LoadJpeg failed to read current scanline?
Application transferred too few scanlines


I managed to save my download, so I'm not desperate for help, I'm just saying you might want to have a plan B.

Edit: The error message obviously didn't include smileys, but I can't find the option to turn them off.

---

### Post by hufferd on 2008-08-13
Update:

Amazon Downloader

Downloaded and installed fine AFTER as I have posted other places here that I went back to the 32 bit OS.  The package manager downloaded it and installed it just fine and as a matter of fact I downloaded my first album tonight and things went great! :guitar:

---

