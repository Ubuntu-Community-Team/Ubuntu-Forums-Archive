---
title: "Problems with some sound software in Ubuntu"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by gleb5 on 2014-10-02
Dear Ubuntu users!

I've tried to use Play it slowly! software to slow down some backing tracks but eventually no output sound has been (I've install all plugins for midi and mp3 and has no any problems with sound besides this)
[https://apps.ubuntu.com/cat/applications/precise/playitslowly/](https://apps.ubuntu.com/cat/applications/precise/playitslowly/) 

could you suggest me how it could be possible to fix it or alternatively recommend me some another software to slow down the mp3 and tracks?

Thanks for help,

Gleb:guitar:

---

### Post by mapes1979 on 2014-10-02
Well.... For starters what all have you done? I can help but i use Bodhi Linux 12.04 and refuse the 14.04 (upgrade until its polished)way better platform that i have found. If still needing help fell free to contact me. I don't use the forums much because past exp. alot is incorrect and I know the correct methods C:

---

### Post by QIII on 2014-10-02
No.  Do not contact the responder privately.  The solution will be hidden from the rest of the community and nobody else will gain.

Furthermore, mapes1979 may not be particularly expert and there will be no feedback.  All support is to be given openly in the public areas of the forums.

Mapes1979: please make no further offers of this sort.

---

### Post by Bucky Ball on 2014-10-02
> **QIII said:**
> No.  Do not contact the responder privately.  The solution will be hidden from the rest of the community and nobody else will gain.

Furthermore, mapes1979 may not be particularly expert and there will be no feedback.  All support is to be given openly in the public areas of the forums.

Mapes1979: please make no further offers of this sort.

^^^
This. mapes is using Bodhi, which is not officially supported here in any case. :-k

To the OP, may I suggest you try Audacity? That can slow things down without de-tuning, but if you go too far, of course, the sound quality will be horrible.

Audacity can be easily installed from Software Centre and is used by professionals and hobbyists alike. Great tool. 

Just a thought: How did you install Playitslowly?

---

### Post by gleb5 on 2014-10-03
I've installed software using both software center as well as manually using python script. In the latter case I've obtained the below error when i''ve tried to load songs

root@bach-ThinkPad-T420:/home/bach/Downloads/playitslowly-1.4.0/bin# playitslowly
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)1, layer=(int)3, rate=(int)44100, channels=(int)2, parsed=(boolean)true
/usr/local/lib/python2.7/dist-packages/playitslowly/app.py:491: GtkWarning: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.MM9TMX': No such file or directory
  gtk.main()
/usr/local/lib/python2.7/dist-packages/playitslowly/app.py:491: GtkWarning: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
  gtk.main()
/usr/local/lib/python2.7/dist-packages/playitslowly/app.py:491: GtkWarning: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DMAZMX': No such file or directory
  gtk.main()

---

### Post by coffeecat on 2014-10-04
Why are you trying to run playitslowly as root? That is totally unnecessary and merely complicates things. And why did you download the playitslowly tarball (presumably) to your Downloads folder?

If you install playitslowly from the Software Centre, it will install automatically together with any needed dependencies, and the installer adds a launcher icon to the launcher bar. You then simply click on the launcher icon to run it. If by chance, you see no launcher icon, type playitslowly in the dash and you can open it from there. If you are running an Ubuntu variant other than Ubuntu, such as Xubuntu or Lubuntu, and you can't find the menu entry, post back with details of which version and release of Ubuntu you are running, and someone will be able to help you.

I installed playitslowly from the Software Centre in Ubuntu 14.04 to check this out, and it just works.

---

### Post by Bucky Ball on 2014-10-04
> **coffeecat said:**
> 

I installed playitslowly from the Software Centre in Ubuntu 14.04 to check this out, and it just works.

I installed playitslowly from Synaptics, am using a minimal install with xfce4, and ... it just works. Not running as root. No need. :-k

Very handy piece of kit, actually, for some of the things I do, so thanks for bringing it up. Never knew it existed and have always used Audacity, as I suggested previously.

---

### Post by gleb5 on 2014-10-04
have you tried to run some songs with it?
In my case I have the

bach@bach-ThinkPad-T420:/usr/bin$ ./playitslowly
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, mpegaudioversion=(int)1, layer=(int)3, rate=(int)44100, channels=(int)2, parsed=(boolean)true


it seems that I should to install smth dealing with the mpeg shouldn't it?

Gleb

---

### Post by coffeecat on 2014-10-04
playitslowly happily played an mp3 at both double and half speed for me. 

From what you posted it looks as though it won't even open, let alone play, so...

Why are you running playitslowly from the terminal? Did you find a menu entry? What flavour of Ubuntu are you using? Did you install playitslowly from the Software Centre or from a downloaded tarball? If you did install from a manually downloaded something-or-other, what did you download - link please - and how did you install it? We can't really help unless you give us relevant information. My guess is that you are missing a necessary codec, which should have been installed if you installed from the Software Centre, but rather than tell you how to install needed dependencies blind, let's have some more information.

---

### Post by Vladlenin5000 on 2014-10-04
The same for me...

Raeding this thread led me to wanting to install and test it, just to find out that I had it already installed. Don't know why and certainly never used before... What I'm certain is I had installed via the software center. Everything works as expected.

---

### Post by gleb5 on 2014-10-04
yes, I've installed it from-software center
here i run it from the terminal just to find source of error- this is happens only when I push PLay song (no errors during its starting).

---

### Post by gleb5 on 2014-10-05
the issue has been solved by means of installing GStreamer extra plugin from the command center

now regarding sound I have only difference to detect my usd sound card which has asio interface in windows. Could someone suggest me some software(like Cubase in win) for the recording of the music instruments using external sound devises?

Gleb

---

### Post by Bucky Ball on 2014-10-05
> **gleb5 said:**
> 

now regarding sound I have only difference to detect my usd sound card which has asio interface in windows. Could someone suggest me some software(like Cubase in win) for the recording of the music instruments using external sound devises?

Gleb

 This is the stuff of another thread. Please post a new thread with a descriptive title and mark this one as 'solved' to help future travelers.
 
Nice work finding a fix, thanks for sharing and good luck. ;)

(Ardour is closest to Cubase but there are a lot of others. As I say, post a new thread specific to this and you will get LOTS of ideas. Perhaps try in ***Multimedia*** sub-forum.)

---

### Post by gleb5 on 2014-10-09
Ok
regarding my issue with sound probably I've found that some problems (e.g feedback in skype ) might be due to the pulse audio- I've tried to remove it and use ALSA instead but alot of software like Guitar Pro and Skype has not option to switch to ALSA. In opposite case Audacity works very bad with PulseAudio so I can run it with guitar pro for instance :).  Could someone suggest me with some solution here?

---

