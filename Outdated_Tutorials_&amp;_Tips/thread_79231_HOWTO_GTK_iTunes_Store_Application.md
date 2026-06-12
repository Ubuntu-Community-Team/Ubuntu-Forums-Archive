---
title: "HOWTO: GTK iTunes Store Application"
date: 2005-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by idn on 2005-10-19
This tutorial is for anyone who wants to access the iTunes music store on their breezy install, but doesn't want to go through the bother of installing iTunes through wine or crossover linux.

**Features:**
[LIST]
[*]Preview songs 
[*]Signup for an account 
[*]Buy songs and albums 
[*]Redownload songs that you bought with SharpMusique 
[*]Redeem Pepsi caps 
[*]Redeem gift certificates
[/LIST]
[B]
Dependencies:[/B]
[LIST]
[*].NET runtime
[*]Gtk#
[/LIST]

Get the deb from this location:

*[http://nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb](http://nanocrew.net/sw/sharpmusique/sharpmusique_1.0-1_i386.deb)*

Then:

```
sudo dpkg -i sharpmusique_1.0-1_i386.deb
```

Goto Applications -> Sound and Video -> Sharp Musique iTMS Client

**You do not need an account to preview the songs.**

To buy the songs you will need to create an account, to do this you will need to provide you credit card details

*** This is done at your own risk! ***

Or you can sign in with your existing account. I signed up over sharpmusique and it worked fine, I got an email through from iTunes confirming my account.

This is my first how to so please be kind :)


**Links of interest:**

[LIST]
[*][http://nanocrew.net/software/sharpmusique/](http://nanocrew.net/software/sharpmusique/)
[/LIST]

---

### Post by majikstreet on 2005-10-19
I never knew there was such a thing!

I can't say that many of us pay for music though ;)

---

### Post by idn on 2005-10-19
:)

Well, hopefully this will be a wake up call for the music industry. Its been around for a while though, I only found out about it today.

I just downloaded my first, it plays fine in Totem, although the filename was a little bit screwed up.

---

### Post by wellery on 2005-10-27
do you also get this error when you try to view an album:

Unhandled Exception: System.InvalidCastException: Cannot cast from
source type to destination type.
in <0x00024> SharpMusique:ViewAlbumThread (System.Object State)
in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object
(object)

---

### Post by Manny C on 2005-11-23
[SharpMusique]("http://nanocrew.net/software/sharpmusique/") has some odd quirks. In particular the download available on the nanocrew website does not correctly write the filename of the m4a file. [JJ]("http://nanocrew.net/about/") [does not have time]("http://nanocrew.net/2005/11/15/itunes-6/") to update the program at the moment.

Following the [hacks in the comments]("http://nanocrew.net/2005/09/17/sharpmusique-10/#comments") of the JJ's blog, I have hacked up a deb that correctly writes the filenames. 

1. Download the [source package]("http://nanocrew.net/sw/sharpmusique/sharpmusique-1.0.tar.gz") from nanocrew and download and install JJ's [snd123 package]("http://nanocrew.net/sw/snd123/snd123_1.0.2-1_i386.deb"):
```
 sudo dpkg -i snd123_1.0.2-1_i386.deb 
```
2. Unpack the SharpMusique archive:
```
 tar zxvf sharpmusique-1.0.tar.gz 
```
3. Install the mono C# compiler and other assorted packages:
```
 sudo apt-get install mono-mcs binfmt-support libglade2-0 mono-common mono-jit libglade2.0-cil libglib2.0-cil libgtk2.0-cil mono-classlib-1.0 libgtk1.2-common libglib1.2 libgtk1.2 liba52-0.7.4 libaa1 libdvbpsi3 libtar liblircclient0 libwxgtk2.4-1 vlc wxvlc libvlc0-dev  
```
4. Save/overwrite the SharpMusique.cs file in the folder sharpmusique-1.0/src folder with the file in the attached archive.
5. Copy the libvlc.so file from /usr/lib/snd123 to the sharpmusique/libvlc folder. Run the following command in the sharpmusique-1.0 folder 
```
 ./configure --prefix=/opt && make
```
[Hattip: [RAOF]("http://www.ubuntuforums.org/member.php?find=lastposter&t=93523")]
6. Then issue the following command:
```
 sudo checkinstall 
```
When it asks you for a package description enter the following:
```
 SharpMusique for iTunes 6.0 
```
Press enter twice. Then change the package information as per your preferences.

For some reason (I don't know why), you need to run sharpmusique with a strace prefix. Otherwise Sharpmusique hangs on login [Hattip: [RAOF]("http://www.ubuntuforums.org/member.php?find=lastposter&t=93523")] 
```
 strace sharpmusique 
```
You may still get an error on logging in. Ignore this and login again (without exiting).

Hope this helps.

---

### Post by wellery on 2005-11-23
Thanks for all your work. I'll try it tonight.

---

### Post by veloct on 2005-11-23
[QUOTE=Manny C][SharpMusique]("http://nanocrew.net/software/sharpmusique/") has some odd quirks. In particular the download available on the nanocrew website does not correctly write the filename of the m4a file. [JJ]("http://nanocrew.net/about/") [does not have time]("http://nanocrew.net/2005/11/15/itunes-6/") to update the program at the moment.

Following the [hacks in the comments]("http://nanocrew.net/2005/09/17/sharpmusique-10/#comments") of the JJ's blog, I have hacked up a deb that correctly writes the filenames.

Find the file attached. Here are the installation instructions. First install the following packages:
```
 sudo apt-get install binfmt-support libglade2-0 mono-common mono-jit libglade2.0-cil libglib2.0-cil libgtk2.0-cil mono-classlib-1.0 
```

Then install the *.deb package that I have attached.
```
 sudo dpkg -i sharpmusique_1.0-1_i386_mannyc.deb 
```

You may have trouble logging into your account every so often. I don't know why. If you experience difficulties, simply run sharpmusique prefixed with strace:
```
 strace sharpmusique 
```

This will run heaps of code. Don't worry about that. You will then get a dialogue box advising of some Init error. Ignore it. Try logging in again and it should work.[/QUOTE]

I don't see a file.

---

### Post by Manny C on 2005-11-23
Check my revised How-To.

---

### Post by angrykeyboarder on 2005-11-25
[quote=idn]:)

Well, hopefully this will be a wake up call for the music industry. Its been around for a while though, I only found out about it today.

I just downloaded my first, it plays fine in Totem, although the filename was a little bit screwed up.[/quote] 
It began life as [PyMusique]("http://en.wikipedia.org/wiki/PyMusique") and created [quite a buzz in the tech media]("http://www.theregister.co.uk/2005/03/18/itunes_pymusique/"). It was brought to us in part, courtsey of "[DVD Jon]("http://www.google.com/search?num=50&hl=en&lr=lang_en&safe=off&q=%22DVD+Jon%22&btnG=Search")"

---

### Post by dude2425 on 2005-11-25
Wouldn't it be possible to just apt-get install sharpmusique? I could have sworn I saw it in synaptic.

---

### Post by angrykeyboarder on 2005-11-25
[quote=dude2425]Wouldn't it be possible to just apt-get install sharpmusique? I could have sworn I saw it in synaptic.[/quote]

If you saw it there it wasn't from an official repository.  It's legality is along the lines of libdvdcss and w32codecs.

---

### Post by dude2425 on 2005-11-25
Whelp, just took another look, it appears it was only there becuase I downloaded the deb once before and it never got removed from synaptic.

---

### Post by Dr Gonzo on 2005-12-29
[QUOTE=Manny C]Check my revised How-To.[/QUOTE]
For some reason, the site with the patched version of SharpMusique.cs is missing.  Could somebody post the file someplace?  Or, at least the patch you used to patch the source?  I can't seem to make a well-formed patch out of the stuff on Jon's blog.

[EDIT] Never mind, I hand patched it.  I can now purchase albums!  Schweet!

---

### Post by Manny C on 2005-12-31
And the patched SharpMusique.cs is now attached.

---

### Post by chrismurf on 2006-01-15
I've attached a breezy .deb of sharpmusique with the requisite fixes.  It's definitely in "Works for Me" status, but if it works for others please let me know.

It should allow for album purchasing, as well as having the metadata fixes.
It sometimes makes me login twice before working, but it eventually works.

I didn't make this .deb the right way (mainly because I don't know how and help is hard to find), so don't come crying to me if it break stuff.

 - chris

---

### Post by meisterjohann on 2006-01-15
I have tried both compiling patched sources and installing your .deb package. Unfortunatly neither works for me. Well, searching and preview of songs works great but purchase just doesnt seem to work. I get error message saying 
"Buy failed (This item requires a later version of iTunes to purchase.)"

Any ideas?

---

### Post by chrismurf on 2006-01-16
Sorry - the patched version allows me to buy single songs and albums... Not sure how to fix it for you and probably won't put much more energy into it, but you can find the patches on nanocrew.net and apply them one by one to the source - it takes some digging through comments, but that's all I did...
 - c

---

### Post by berserker on 2006-01-17
[QUOTE=meisterjohann]I have tried both compiling patched sources and installing your .deb package. Unfortunatly neither works for me. Well, searching and preview of songs works great but purchase just doesnt seem to work. I get error message saying 
"Buy failed (This item requires a later version of iTunes to purchase.)"

Any ideas?[/QUOTE]

Have you used iTunes 6.0 for Windows previously with the same account?  I've seen posts where some accounts work but others don't with SharpMusique.  I'm wondering if the ones that work have never logged on using iTunes 6.0 under Windows...

---

### Post by brainkilla on 2006-01-23
@meisterjohann

Songs bought via iTunes are DRM-plagued. SharpMusique removes the protection, and you have files that are free as in freedom, so any player can play them. That is why we the software (not only SharpMusique but almost everything we also know as 'open source') is called free - it restores your freedom to use your computer the way you want...

---

### Post by brainkilla on 2006-01-23
Songs bought via iTunes are DRM-plagued. SharpMusique removes the protection, and you have files that are free as in freedom, so any player can play them. That is why we the software (not only SharpMusique but almost everything we also know as 'open source') is called free - it restores your freedom to use your computer the way you want...

---

### Post by o_fortuna on 2006-01-23
[QUOTE=brainkilla]SharpMusique removes the protection[/QUOTE]
Just a quick note, SharpMusique doesn't *remove* the protection, it simply doesn't add it -- it takes advantage of the fact that FairPlay is added after the purchase by the iTunes application itself.
[QUOTE=Cysman]Howdy,

I tried this and this is what I got back:

kenoutten@ubuntubedroom:~$ sudo dpkg -i sharpmusique_1.0-1_i386.deb
dpkg: error processing sharpmusique_1.0-1_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
sharpmusique_1.0-1_i386.deb

What am I missing?

Ken[/QUOTE]
Try
```
cd Desktop
sudo dpkg -i sharpmusique_1.0-1_i386.deb
```
if the package is on the Desktop (it probably is).

---

### Post by Cysman on 2006-01-23
Howdy,

I tried this and this is what I got back:

kenoutten@ubuntubedroom:~$ sudo dpkg -i sharpmusique_1.0-1_i386.deb
dpkg: error processing sharpmusique_1.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sharpmusique_1.0-1_i386.deb

What am I missing?

Ken

---

### Post by meisterjohann on 2006-01-23
Yes, I previously did buy some songs from Windows on the same account. Thanks to your comment I now created a new account from within SharpMusique. It turns out that your suspicion was a direct hit. With this new account I purchase songs without problem! :D Thanks berserker!

Downloaded songs get the extension .m4p same as songs downloaded from windows. One thing is very different though. Songs from SharpMusique plays without problem in my totem (ubuntu installation). Songs downloaded from windows plays ok in iTunes (windows) only.

---

### Post by angrykeyboarder on 2006-01-26
[quote=majikstreet]I never knew there was such a thing!

I can't say that many of us pay for music though ;)[/quote]

I guess I missed your survey...

---

### Post by rune on 2006-01-28
> One thing is very different though. Songs from SharpMusique plays without problem in my totem (ubuntu installation). Songs downloaded from windows plays ok in iTunes (windows) only.

Thats becasue pymusique download the song, saves it.
itunes (for windows) downloads, puts on FairPlay DRM, saves it.

---

### Post by dalani on 2006-01-31
I tried this and got this: 

```
@ubuntu:~/Desktop$ sudo dpkg -i sharpmusique_1.0-1_i386.deb
Selecting previously deselected package sharpmusique.
(Reading database ... 65949 files and directories currently installed.)
Unpacking sharpmusique (from sharpmusique_1.0-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing sharpmusique_1.0-1_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/sharpmusique/libvlc.so')
Errors were encountered while processing:
 sharpmusique_1.0-1_i386.deb
```

BTW I'm using Hoary. Can anyone tell me what's gone wrong?

---

### Post by gpeck157 on 2006-03-30
[QUOTE=Cysman]Howdy,

I tried this and this is what I got back:

kenoutten@ubuntubedroom:~$ sudo dpkg -i sharpmusique_1.0-1_i386.deb
dpkg: error processing sharpmusique_1.0-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sharpmusique_1.0-1_i386.deb

What am I missing?

Ken[/QUOTE]

Download the file, then:
```
sudo dpkg -i /path/you/saved/the/file/sharpmusique_1.0-1_i386.deb
```

Good luck,
Glen

---

### Post by Jott on 2006-07-22
Hi -

I'm trying to follow you're instructions on building sharpmusique from source for itunes 6.0.  The instructions are clear and I'm fairly certain that I'm folling them correctly.  Everything appears to be working, but when I try to run sharpmusique - with or without the strace command - nothing happens.  I'm a bit of a newbie, though I do have some experience - but not enough to know which error logs to check or how to interpret what I'd find there.  The one bit of salient information that might provide a clue is that I'm running dapper.

Any suggestions as to how I can go about identifying the problem and fixing it?  Anyone else got this to work in dapper? A forum search for sharpmusique dapper turned up nada...help is appreciated!

Thanks!

---

### Post by mali2297 on 2006-08-07
Hej.

I'm using Dapper and I installed Chrismurf's package without problem. These three commands should be enough:

gunzip sharpmusique-breezy-patched.deb.gz
sudo dpkg -i sharpmusique-breezy-patched.deb
sudo apt-get -f install

There are still some minor bugs in the program, but it works.

---

### Post by Jott on 2006-08-08
Hey, that worked!  I was trying to follow the instructions on the first page, manually adding the file and all.

Thanks!

---

### Post by quicktime1 on 2006-08-09
With me anytime I try to re-download a song already bought with SharpMusique it waits a little and it just dissapears. I'm not sure if anybody else has this problem. I bought 2 songs, but because of the naming thing there was only one file, and only one song. I would even buy it again, but it doesnt let me.

---

### Post by petersjm on 2006-09-22
I get a 404 when trying to download the deb for this. Does it still exist somewhere? Is there another way?

---

### Post by darkteckno on 2006-09-23
Same here!

---

### Post by alfsborg on 2006-10-04
i have a copy but am unable to upload to this forum ](*,)

---

### Post by sbassett on 2006-10-04
> **alfsborg said:**
> i have a copy but am unable to upload to this forum ](*,)

Throw it up on here.

[My Downloads]("http://simon.doesntexist.com/upload.php")

I should have it available this afternoon sometime (EST Time).

---

### Post by alfsborg on 2007-05-22
sorry for the tardiness, i have a j o b and a w i f e

---

### Post by russell.h on 2007-05-22
Does this still work? Last I heard they had changed something up to lock out third party clients.

---

### Post by jdramer on 2008-08-05
It seems that Sharpmusique no longer works with the latest iTunes.

[http://www.linux.com/articles/114269]("http://www.linux.com/articles/114269")

[http://en.wikipedia.org/wiki/PyMusique]("http://en.wikipedia.org/wiki/PyMusique")

---

### Post by mali2297 on 2008-08-05
I think Sharpmusique stopped working a long time ago.

This thread contains my very first post in these forums; it brings back memories...

---

### Post by eugenevdm on 2009-03-08
Since it appears SharpMusic stopped working, is there any other way apart from using Wine to run iTunes on Ubuntu?

---

