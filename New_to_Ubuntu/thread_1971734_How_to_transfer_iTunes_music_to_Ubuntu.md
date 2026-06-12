---
title: "How to transfer iTunes music to Ubuntu?"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by lolzPython on 2012-05-02
Hi interwebers,

I'm pretty new to Ubuntu. I've tried it before, loved it, and plan on replacing win7 with it, just wanted to move all my music over there. The problem is, 80% of my music was bought on iTunes, meaning they're .m4a's. These are all on my current windows 7 machine. I was wanting to put all of this on Ubuntu, and I was wondering what the best way to move all of it over would be. The two problems that I am worried about is 1.) That Banshee, RythymBox, etc. will not accept .m4a's, and 2.) How to do the actual transfer part of this.

Sorry if this sounds kind of dumb, this is my first post, and if there's already a thread for this, could you please post a link to it?

Thanks

---

### Post by dgorack on 2012-05-02
You could try to install iTunes on Ubuntu with Wine, here is a link:
[http://www.youtube.com/watch?v=dnUrqcD4W_M](http://www.youtube.com/watch?v=dnUrqcD4W_M)

Then it's just a matter of moving your music from your My Music\iTunes Music folder and authorizing your ubuntu computer.

---

### Post by Zukaro on 2012-05-02
To transfer your music boot up into Ubuntu, go to your Windows partition, locate your music folder and copy it over to Ubuntu (right click, copy, then paste wherever you want).

As for converting the music (you'll want to do this before you transfer it) there's a few programs out there that I know of for Windows (not sure about Ubuntu) which can transfer songs to other formats such as mp3.


In Windows I use this to convert audio files.  You can download the entire thing or separate parts of it.
(it's free; however, only for Windows (I don't know of anything on Linux to convert audio files))

Full program:
[http://www.dvdvideosoft.com/free-dvd-video-software.htm](http://www.dvdvideosoft.com/free-dvd-video-software.htm)

Audio converter:
[http://www.dvdvideosoft.com/products/dvd/Free-Audio-Converter.htm](http://www.dvdvideosoft.com/products/dvd/Free-Audio-Converter.htm)

---

### Post by ron999 on 2012-05-02
> **lolzPython said:**
> Banshee, RythymBox, etc. will not accept .m4a's
You're sure about this?

---

### Post by lolzPython on 2012-05-03
> **dgorack said:**
> You could try to install iTunes on Ubuntu with Wine, here is a link:
[http://www.youtube.com/watch?v=dnUrqcD4W_M](http://www.youtube.com/watch?v=dnUrqcD4W_M)

Then it's just a matter of moving your music from your My Music\iTunes Music folder and authorizing your ubuntu computer.
I'm sorry, but can this really work? I tried it last time I used Ubuntu and the menu came up all glitchy and weird, no matter how I installed/ran it.

---

### Post by lolzPython on 2012-05-03
> **Zukaro said:**
> To transfer your music boot up into Ubuntu, go to your Windows partition, locate your music folder and copy it over to Ubuntu (right click, copy, then paste wherever you want).
Sorry if I wasn't super clear in my question: I am completely replacing windows with Ubuntu. There are no partitions. What I was wondering was the best way to keep my files during the installation process.

---

### Post by lolzPython on 2012-05-03
> **ron999 said:**
> You're sure about this?
no.

---

### Post by FulciLives on 2012-05-03
The itunes format is called AAC-LC or AAC for short and the files end with M4A (that's the file extension). 

This format is a form of lossy audio compression. That means it has been compressed in such a way that quality was lost in the process. Granted it can (and often does) sound very good but it was already compressed with some quality loss.

Now if you try to convert it to another lossy audio format (such as MP3 or OGG etc.) then the file will be compressed yet again and will again lose audio quality.

So you do NOT want to convert it to anything lossy. You could convert it to a lossless format like FLAC but that is frowned upon because 1.) FLAC is supposed to be from a CD quality or better source that hasn't been lossy compressed 2.) Converting lossy to lossless does NOT make the quality better (it stays the same actually) but will increase the file size by a large factor.

I suppose you COULD convert to FLAC if AAC is NOT supported but the good news is that AAC is in fact supported as long as you install the proper "restricted" codecs.

So there is NO need to convert and converting just doesn't make sense anyway.

Now ... You said that you will be installing Ubuntu and getting rid of Windows 7 and yet I suspect you only have one hard drive (from your explanation). This makes it slightly harder because you have to do one of the following:

1.) Install Ubuntu without deleting your Windows 7 install. Then copy everything you need from your Windows install (like music, pictures, videos, documents, etc.) to your Ubuntu install. Then delete the Windows install and expand the Ubuntu install so it now takes up the entire hard disk drive space.

2.) Back-up your Windows data (like music, pictures, videos, documents, etc.) to some form of external media. This could be copying them to a USB thumb drive, or a USB HDD or copying them to DVD discs (as data discs) etc. and once you have done that then you can safetly "blow out" your Windows install while installing Ubuntu (then copy everything back from the external media to your Ubuntu install).

Assuming you only have one HDD (hard disk drive) then I suggest method 2 and the easiest way to go about it is having ONE external source that is big enough for all your files. This usually means getting an external USB HDD since USB thumb drives probably can't hold everything (they are limited in capacity and not exactly cheap when you get into very large sizes). Then again an external HDD isn't exactly cheap either. However it is always a good idea to have a back-up of your data so really if you only have one HDD internally you should (ideally) get an external USB HDD that is the same size (or larger) and use it to back up your data (making it not only useful for this Windows to Linux translation but also making it useful in the future since you can do full back-ups of your new install).

---

### Post by FulciLives on 2012-05-03
Just wanted to post a follow up to what I said above:

Please note that I just tested this and it works :)

Copy your iTunes folder from it's location in Windows (under My Music) to an external HDD or USB Thumb drive.

After you have Ubuntu installed you need to install Banshee because 12.04 comes with Rhythm Box by default. In my case I also installed ALL of the Banshee add-on's listed under Banshee in the Ubuntu Software Center. You also should install (from the Software Center) the Ubuntu Restricted Codecs (it's called UBUNTU RESTRICTED EXTRAS).

OK after all that is done go ahead and fire up Banshee and select (from the top) EDIT then under that select PREFERENCES

Checkmark the option called, "Copy Files to media folders when importing". The only other thing I checkmarked on this page was the "Update file and folder names" (everything else is optional)

After you do that select (from the top) MEDIA then under that select IMPORT MEDIA

Now change the selection to read, "iTunes Media Player"

It will now let you browse to your iTunes folder and select the XML file. The file is under the iTunes folder (it's easy to find). Select it and click "open" and then "import"

Banshee will now add the iTunes songs to itself BUT (and this is the important part) it will also copy all your music to your Ubuntu MUSIC folder.

After it is done your music is in your Ubuntu MUSIC folder and you can continue to use Banshee or use Rhythm Box or any other Linux based music player.

Hope this helps!

---

### Post by Zukaro on 2012-05-03
> **lolzPython said:**
> Sorry if I wasn't super clear in my question: I am completely replacing windows with Ubuntu. There are no partitions. What I was wondering was the best way to keep my files during the installation process.

Backup your music and other files you want to keep to an external hard drive or if they'll fit to a USB/CD.  Then copy them over.  If you need to convert them do it in Windows first (unless you can find a tool for Ubuntu for converting audio files).

---

### Post by Ms. Daisy on 2012-05-03
> **Zukaro said:**
> Backup your music and other files you want to keep to an external hard drive or if they'll fit to a USB/CD. Then copy them over. If you need to convert them do it in Windows first (unless you can find a tool for Ubuntu for converting audio files). Just curious, did you read the posts in this thread? You just said the same thing as FulciLives except he provided very detailed instructions.

---

### Post by Zukaro on 2012-05-03
> **Ms. Daisy said:**
> Just curious, did you read the posts in this thread? You just said the same thing as FulciLives except he provided very detailed instructions.

*didn't read all of them* :V

---

### Post by lolzPython on 2012-05-11
> **FulciLives said:**
> Just wanted to post a follow up to what I said above:
 
Please note that I just tested this and it works :)
 
Copy your iTunes folder from it's location in Windows (under My Music) to an external HDD or USB Thumb drive.
 
After you have Ubuntu installed you need to install Banshee because 12.04 comes with Rhythm Box by default. In my case I also installed ALL of the Banshee add-on's listed under Banshee in the Ubuntu Software Center. You also should install (from the Software Center) the Ubuntu Restricted Codecs (it's called UBUNTU RESTRICTED EXTRAS).
 
OK after all that is done go ahead and fire up Banshee and select (from the top) EDIT then under that select PREFERENCES
 
Checkmark the option called, "Copy Files to media folders when importing". The only other thing I checkmarked on this page was the "Update file and folder names" (everything else is optional)
 
After you do that select (from the top) MEDIA then under that select IMPORT MEDIA
 
Now change the selection to read, "iTunes Media Player"
 
It will now let you browse to your iTunes folder and select the XML file. The file is under the iTunes folder (it's easy to find). Select it and click "open" and then "import"
 
Banshee will now add the iTunes songs to itself BUT (and this is the important part) it will also copy all your music to your Ubuntu MUSIC folder.
 
After it is done your music is in your Ubuntu MUSIC folder and you can continue to use Banshee or use Rhythm Box or any other Linux based music player.
 
Hope this helps!
 Thanks for taking the time to do this, sorry about the late reply my computer broke. I'm using a school laptop to post this but when (and if) my  computer gets fixed I'll try this out. Now I can list this as [Solved].

---

### Post by lolzPython on 2012-05-11
> **Zukaro said:**
> Backup your music and other files you want to keep to an external hard drive or if they'll fit to a USB/CD. Then copy them over. If you need to convert them do it in Windows first (unless you can find a tool for Ubuntu for converting audio files).
 Thanks, I'll do this as well when my computer gets back.

---

