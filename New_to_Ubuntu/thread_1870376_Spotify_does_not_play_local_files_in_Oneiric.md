---
title: "Spotify does not play local files in Oneiric"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by WonderStivi on 2011-10-27
I've recently upgraded to Oneiric, and I've noticed that Spotify no longer plays local files.

I've found that the reason for this is that "[...]Ubuntu has changed the Qt media backend from libavcodec to gstreamer. Now, gstreamer is capable of playing mp3 files just fine (and about any other audio file format too), but spotify refuses to play any of them and complains about audio decoder problems." and that the solution is to do as following: "I copied the following libraries from Ubuntu Natty to Oneiric: libavcodec.so.52 libavformat.so.52 libavutil.so.50 libQtWebKit.so.4 libsndfile.so.1 libx264.so.106 and used LD_LIBRARY_PATH environment variable to point spotify binaries to use them. Voila, spotify started to play mp3 files again just as before. And none of those libraries is an actual mp3 decoder!"

[http://getsatisfaction.com/spotify/topics/spotify_mp3_decoding_on_ubuntu_oneiric_11_10](http://getsatisfaction.com/spotify/topics/spotify_mp3_decoding_on_ubuntu_oneiric_11_10)

Now, this just got a bit too technical for me. Anyone care to explain where to move these libraries, and how to link using LD_LIBRARY_PATH?

---

### Post by petronell on 2011-10-27
Hi I have this problem as well, can anyone help with the instructions. I have downloaded the mentioned libraries, just need to know what to do with them?

Thanks.

DDR

---

### Post by wolfen69 on 2011-10-27
Make a new folder in Home called *spotify-libs* and put all of those files into it. Then in a terminal do:
```
LD_LIBRARY_PATH=$HOME/spotify-libs spotify
```

---

### Post by beew on 2011-10-27
Why would anyone want that piece of DRM crap? Installing Spotify would remove all your medibuntu libraries and replace them with the vanilla ones that don't play a lot of media files. It is a malware by any reasonable definition.

If you must use this DRM malware try install the Windows version with WINE, that way it wouldn't screw up your system.

---

### Post by WonderStivi on 2011-10-28
Because I find 99% of the music I listen to in Spotify, it's a small minority of mp3. In addition to Spotify, I use XBMC, so I'm not familiar with the problem you are referring to.

Edit: This fix didn't work for me on my x64 Oneiric. Oh well, no hassle.

---

### Post by petronell on 2011-10-28
WonderStivi,

Are you using 32-bit or 64-bit ubuntu?

I have fixed the issue on my system. I will attach the files you need and give you step by step instructions.

DDR

---

### Post by petronell on 2011-10-28
Hi,

This solution has worked for me, and Spotify is working fine again.

Firstly I have prepared two tar files one for 32 bit ubuntu, and one for 64 bit ubuntu. Download the appropriate tar for your installation.

32 Bit Packages

[https://docs.google.com/open?id=0B7zekYZwRKjRZjIyZWU2NDEtMDEzNC00MjgxLThjYjEtNTAxZGM4MTE4YzI1](https://docs.google.com/open?id=0B7zekYZwRKjRZjIyZWU2NDEtMDEzNC00MjgxLThjYjEtNTAxZGM4MTE4YzI1)

64 Bit Packages

[https://docs.google.com/open?id=0B7zekYZwRKjRZjNiZDFiNzYtMzg4ZC00MTI2LThhYzctZDg4NmJmZTZiMzgy](https://docs.google.com/open?id=0B7zekYZwRKjRZjNiZDFiNzYtMzg4ZC00MTI2LThhYzctZDg4NmJmZTZiMzgy)

Then decompress the tar back to the deb packages by right clicking the tar file and choosing "Extract Here" from the short cut menu.

Now open a terminal window and navigate to the directory where you have de-compressed the tar. In the example below I have assumed this will be Downloads.

[INDENT][/INDENT]cd Downloads

Next we need to install the three deb packages, so the next command at the prompt to type is:

[INDENT][/INDENT]sudo dpkg -i *.deb

next command is 

[INDENT][/INDENT]sudo apt-get install -f

It should have now installed the packages. Exit terminal. Re-load spotify and it should now play local files.

DDR:popcorn:

---

### Post by WonderStivi on 2011-10-28
Oh yes, worked like a charm. Thanks man. Btw, I'm on 64 bit.

---

### Post by zwarte_piet on 2011-11-01
Petronell your my hero! I listen alot of mixed playlists (Local and spotify) thats why i needed this or else i would only hear half of the playlist...

---

### Post by thewump on 2011-11-06
Rockstar! Thanks

To all the DRM cynics, that's just dumb.  There is so much more to this music client than DRM protected music.. even as a playlist manager for multiple devices it rocks.

K

---

### Post by beew on 2011-11-06
> **thewump said:**
> Rockstar! Thanks

To all the DRM cynics, that's just dumb.  There is so much more to this music client than DRM protected music.. even as a playlist manager for multiple devices it rocks.

K

No but thanks, there are many FOSS music managers and they are just fine and best, they don't mess up my system by trying to remove libraries that supposedly violate DRM (medibuntu stuffs). Of course it has to have some desirable features than just DRM, you need bait to catch fish. How would they get people to swallow DRM if they don't sweeten it up a bit?

---

### Post by yugnip on 2011-11-07
Hmm, You might be missing the point of the thread here. Spotify hasn't replaced anything. In fact it wants libs that have been upgraded. The desired codec is libavcodec52, and Oneiric is using libavcodec53. As far as I know, Spotify hasn't touched any Medibuntu offering.

And thanks for this fix petronell, it works perfectly. My only concern is for future updates... will these packages need to be locked/pinned?

---

### Post by beew on 2011-11-07
> **yugnip said:**
> Hmm, You might be missing the point of the thread here. Spotify hasn't replaced anything. In fact it wants libs that have been upgraded. The desired codec is libavcodec52, and Oneiric is using libavcodec53. As far as I know, Spotify hasn't touched any Medibuntu offering.

And thanks for this fix petronell, it works perfectly. My only concern is for future updates... will these packages need to be locked/pinned?

Actually if you add medibuntu and install the non free codecs you would have libavcodec-extra52, libavformat-extra52 etc (or 53 depending on your Ubuntu release) instead of libavcodec52, libavformat52  etc. The key here is the "extra" part, without which many multimedia functionalities would be crippled. If you install Spotify, all the packages in the screenshot would be replaced by the crippled ones without the 'extra' tag.

That's why, I said that if you must have this crap install it in WINE, that way at least it won't mess with your system libraries.

---

### Post by veroslav on 2011-11-08
Hi beew,

if these packages are indeed replaced by corresponding crippled versions by Spotify, how can we revert to the ones used by Medibuntu? 

Thank you in advance!

---

### Post by beew on 2011-11-08
Just reinstall those packages and it will remove the non "extra" versions and Spotify. If you reinstall Spotify it will reinstall the non extra packages and remove the extra ones etc. It should be reversible both ways.

---

### Post by veroslav on 2011-11-08
Thank you very much for the advice, beew, I will do that, because I really did not liked what spotify did there. It makes me angry.

Thanks again.

---

### Post by yugnip on 2011-11-08
Ah. Thanks for the clarification beew. The 'extra' codecs are indeed not installed. I haven't noticed any adverse effects yet, but that doesn't mean I won't. I am willing to live with however as I do enjoy the service Spotify provides. 

Thanks again, and sorry to have doubted you.

---

### Post by fazeoff on 2011-11-24
> **petronell said:**
> Hi,

This solution has worked for me, and Spotify is working fine again.

Firstly I have prepared two tar files one for 32 bit ubuntu, and one for 64 bit ubuntu. Download the appropriate tar for your installation.

32 Bit Packages

[https://docs.google.com/open?id=0B7zekYZwRKjRZjIyZWU2NDEtMDEzNC00MjgxLThjYjEtNTAxZGM4MTE4YzI1](https://docs.google.com/open?id=0B7zekYZwRKjRZjIyZWU2NDEtMDEzNC00MjgxLThjYjEtNTAxZGM4MTE4YzI1)

64 Bit Packages

[https://docs.google.com/open?id=0B7zekYZwRKjRZjNiZDFiNzYtMzg4ZC00MTI2LThhYzctZDg4NmJmZTZiMzgy](https://docs.google.com/open?id=0B7zekYZwRKjRZjNiZDFiNzYtMzg4ZC00MTI2LThhYzctZDg4NmJmZTZiMzgy)

Then decompress the tar back to the deb packages by right clicking the tar file and choosing "Extract Here" from the short cut menu.

Now open a terminal window and navigate to the directory where you have de-compressed the tar. In the example below I have assumed this will be Downloads.

[INDENT][/INDENT]cd Downloads

Next we need to install the three deb packages, so the next command at the prompt to type is:

[INDENT][/INDENT]sudo dpkg -i *.deb

next command is 

[INDENT][/INDENT]sudo apt-get install -f

It should have now installed the packages. Exit terminal. Re-load spotify and it should now play local files.

DDR:popcorn:

this worked great, thanks.....

---

### Post by h3hound on 2011-12-20
cool...

you rock now that i may rock.:KS

---

### Post by octane_olga on 2011-12-23
Works like a charm. Thanks. :)

---

### Post by bdombro on 2012-03-15
@petronell:  Worked you rock!

---

### Post by geneticdrifter on 2012-09-10
amazing -- worked perfectly. Thanks so much.

---

