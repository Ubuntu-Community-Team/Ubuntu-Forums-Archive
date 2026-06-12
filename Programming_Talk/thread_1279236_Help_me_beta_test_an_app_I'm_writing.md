---
title: "Help me beta test an app I'm writing?"
date: 2009-09-30
forum: Programming Talk
---

### Post by jeremykross on 2009-09-30
So, I'm tragically unemployed, as I suppose more than a handful of us are at the moment.  But I've been whittling the hours on a project that I'm quite proud of and I think its at a point where it might be useful to someone.  

I've written a new kind of web browser.  If you look at the link, I'm sure you'll get the gist of it.  The screenshot says it all, I think.  You do have to go through a signup process, eventually I'll check to make sure the email you  provide is valid. But for now, please feel free to type any rubbish you want in.  Just remember the email address and password you make up so you can sign in.  

I've put up an Ubuntu deb file, in addition to the obligatory Windows and OS X versions.  Feel free to pick your poison, although I suppose most people will grab the Ubuntu version.  

You're the first bunch of people, in the world, to see this.  So, it might be a a little lonely at the moment.  But, having been my program's only denizen for the past six months, I think its time for some company.

Get it here: [http://www.jeremykross.com]("http://www.jeremykross.com")


EDIT:

I've taken everything down for the night.  I'm going to try it again tomorrow after I get everything in place.

---

### Post by ibuclaw on 2009-09-30
As probably the first user to download and install it, I just have one thing to say ...

[LIST=1]
[*]There is a file named **.deb** that somehow made its way into the package, I don't think it should be there.
[*]No 64bit?
[*]No Open Source?
[/LIST]

OK, that is three things... But, nice job. :)

edit:
[LIST]
[*]Added Screenie
[*]Note to self, the avatar is stalking me...
[*]Note to self, lack of javascript popup support means had to upload screenie in the firefox browser.
[/LIST]

Regards
Iain

---

### Post by jeremykross on 2009-09-30
Issue 1 is fixed.  I dunno how that stray .deb got in there.
 
I'll compile a 64 bit version when I get a free second.

The icon isn't stalking you, it moves where you click.  Everyone else on the site will see it move to roughly the same spot on their screen.

---

### Post by jeremykross on 2009-09-30
Dear Everyone, apparently there was a mix up, I had to take the system down for a few.  Please bear with me?

---

### Post by NoaHall on 2009-09-30
Tried to run it, but came up with the error "trek: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory"

I have the lib installed though.

---

### Post by ibuclaw on 2009-09-30
> **NoaHall said:**
> Tried to run it, but came up with the error "trek: error while loading shared libraries: libQtWebKit.so.4: cannot open shared object file: No such file or directory"

I have the lib installed though.

On 32 or 64 bit Ubuntu?

The package you need is: libqt4-webkit

If you are in doubt, paste the output of the following:
```
ldd /usr/local/bin/trek
```

Regards
Iain

---

### Post by NoaHall on 2009-09-30
As I have said, I have it.

On 32 bit debian.

---

### Post by jeremykross on 2009-09-30
Nobody can access anything atm because I've taken the server down for a quick fix.  I'm on that now.. then I'm going to compile a 64 bit version and get that up.  I'll let everybody know when its going.  I can't thank everyone enough for the interest, please hang in there.

---

### Post by ibuclaw on 2009-09-30
> **NoaHall said:**
> As I have said, I have it.

On 32 bit debian.

OK, but I'd still like to see the any output, as I will be able to confirm with you just why it is not working.

```
dpkg -S libQtWebKit.so.4
ldd /usr/local/bin/trek | grep libQtWebKit

```
Regards
Iain

---

### Post by NoaHall on 2009-09-30
```
 noah@noah-desktop:~$ dpkg -S libQtWebKit.so.4
libqt4-webkit: /usr/lib/libQtWebKit.so.4
libqt4-webkit: /usr/lib/libQtWebKit.so.4.5
libqt4-webkit: /usr/lib/libQtWebKit.so.4.5.0
noah@noah-desktop:~$ ldd /usr/local/bin/trek | grep libQtWebKit
noah@noah-desktop:~$ 

```

Used sudo ldconfig also - still not there.

After copying the file over to trek, I get segmentation fault.

---

### Post by ibuclaw on 2009-09-30
> **NoaHall said:**
> ```
 noah@noah-desktop:~$ dpkg -S libQtWebKit.so.4
libqt4-webkit: /usr/lib/libQtWebKit.so.4
libqt4-webkit: /usr/lib/libQtWebKit.so.4.5
libqt4-webkit: /usr/lib/libQtWebKit.so.4.5.0
noah@noah-desktop:~$ ldd /usr/local/bin/trek | grep libQtWebKit
noah@noah-desktop:~$ 

```

Used sudo ldconfig also - still not there.

After copying the file over to trek, I get segmentation fault.

hmm, that is not right at all.
And what is the FULL output of 'ldd /usr/local/bin/trek' ?
Does it say that anything is "**not found**" ?

If so, you can search package contents for all files in Debian here: [http://packages.debian.org/search?mode=path&suite=lenny&section=all&arch=any&searchon=contents&keywords=libQtWebKit.so.4](http://packages.debian.org/search?mode=path&suite=lenny&section=all&arch=any&searchon=contents&keywords=libQtWebKit.so.4)

---

### Post by NoaHall on 2009-09-30
```
 noah@noah-desktop:~$ ldd /usr/local/bin/trek
	linux-vdso.so.1 =>  (0x00007fffed7ff000)
	libsqlite3.so.0 => /usr/lib/libsqlite3.so.0 (0x00007ff6e41b8000)
	libphonon.so.4 => /usr/lib/libphonon.so.4 (0x00007ff6e3f69000)
	libQtGui.so.4 => /usr/lib/libQtGui.so.4 (0x00007ff6e332a000)
	libQtNetwork.so.4 => /usr/lib/libQtNetwork.so.4 (0x00007ff6e3006000)
	libQtCore.so.4 => /usr/lib/libQtCore.so.4 (0x00007ff6e2bb9000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007ff6e299c000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007ff6e268f000)
	libm.so.6 => /lib/libm.so.6 (0x00007ff6e240a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007ff6e21f1000)
	libc.so.6 => /lib/libc.so.6 (0x00007ff6e1e7f000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007ff6e1c7b000)
	libQtDBus.so.4 => /usr/lib/libQtDBus.so.4 (0x00007ff6e1a03000)
	libaudio.so.2 => /usr/lib/libaudio.so.2 (0x00007ff6e17ea000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007ff6e15c3000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007ff6e133c000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007ff6e10f6000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007ff6e0eed000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007ff6e0cd1000)
	libz.so.1 => /lib/libz.so.1 (0x00007ff6e0ab9000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007ff6e07f4000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007ff6e05e9000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007ff6e03b7000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007ff6e01a5000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007ff6dfe9d000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0x00007ff6dfc98000)
	librt.so.1 => /lib/librt.so.1 (0x00007ff6dfa90000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ff6e56e6000)
	libQtXml.so.4 => /usr/lib/libQtXml.so.4 (0x00007ff6df847000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007ff6df5e1000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007ff6df3b0000)
	libuuid.so.1 => /lib/libuuid.so.1 (0x00007ff6df1ab000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007ff6def81000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007ff6ded7d000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007ff6deb61000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007ff6de95b000)

```


This is now on 64 bit ubuntu - same problem. ia32-libs and ia32-libs-dev are installed.

---

### Post by jeremykross on 2009-09-30
Oh, my.  Okay.. As always happens when you're debuting a new piece of code, something little goes wrong at the last minute, and you're trapped at a coffee shop with a dog slow connection.  Everything is back up and running.  I've fixed the stray .deb file.  I've got a 64 bit version available.  

Please, NoaHall, try downloading the appropriate deb for your system and installing it again. 

I'll be waiting on google.com for anyone who decides to give it a try.

---

### Post by NoaHall on 2009-09-30
64 bit version works on 64 bit(32 bit on 32 bit doesn't work still though)

Ideas -

Add a tooltip to the "chat detach" button on the bottom right.
Stop the avatar flying to the mouse when you click - it's annoying.
Automatic login 
Make the address bar smaller - I think it's a little too big.
Allow closing of a tab so you can have no tabs with webpages open - it can be done by the way, just open a new tab, then close the other one with a webpage in.
On the new page, you should have something about what your "friends" are up to, and links to your favourites.

Nice interface, it all looks really good and impressive.

---

### Post by jeremykross on 2009-09-30
Gah.  Well, day one of Trek's public life is a thorough failure.  In my haste to fix things, I screwed other stuff up. 

anyway, I'm calling it a day.  I need some time to get everything in order.  I thought I was prepared for a public showing but you never really know until.  I'll give it another go tomorrow once I get everything in place. 

Sorry for wasting your time.  do stay tuned though, yeah?

---

### Post by NoaHall on 2009-09-30
It's fine, it's almost there - I'd say call it alpha. Unless you mean the chat isn't working?

---

### Post by jeremykross on 2009-09-30
> **NoaHall said:**
> 64 bit version works on 64 bit(32 bit on 32 bit doesn't work still though)

Ideas -

Add a tooltip to the "chat detach" button on the bottom right.
Stop the avatar flying to the mouse when you click - it's annoying.
Automatic login 
Make the address bar smaller - I think it's a little too big.
Allow closing of a tab so you can have no tabs with webpages open - it can be done by the way, just open a new tab, then close the other one with a webpage in.
On the new page, you should have something about what your "friends" are up to, and links to your favourites.

Nice interface, it all looks really good and impressive.

I'm glad you got it running, although I just pulled everything down again.  Thanks for the persistence.  Very good/thoughtful advice.

One inquiry, the avatar flies to where you click for everyone else too.  So, it gives a spacial element to the chat -I think that's important.  But how else do you propose I handle movement?

---

### Post by NoaHall on 2009-09-30
I'm not sure how that's useful - if you're clicking on a link, you're not trying to chat. Maybe you could make the avatar do something to show the progress of the page loading and if there's a new message.

---

