---
title: "Installing libusb"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by alien_sporez on 2013-03-28
Before I begin, yes, I searched. I found a few threads relating to the installation of libusb however I have one problem: I have no clue what they're talking about.

It has probably been 20 yrs since I've done any Unix command line, so essentially I have zero experience.

I ran this

```
[COLOR=#000000][FONT=Consolas]sudo apt-get install libusb-1.0-0-dev[/FONT][/COLOR]
```

Appeared to install the libusb package, however the software I've installed (Windows program installed with Wine) says "Unable to find WinUSB or libusb on the system. Please re-install the application" So I don't think I did the installation right.

Now, the big problem I has is that when I find what appear to be relevant solutions, I can't try them because I have zero experience in the command-line (anymore... 25 years ago, sure. Now... not so much).

So, if anyone can help me I would appreciate it. If you could also step me through the entire process; as if you're talking to a 5 yr old... that's retarded.

Thanks

---

### Post by oldos2er on 2013-03-28
Which version of Ubuntu are you running? What Windows app are you trying to run?

libusb-1.0-0-dev is development files you'd need if you were going to compile something. If you want the library file, try ```
sudo apt-get install libusb-1.0-0
```

---

### Post by alien_sporez on 2013-03-29
Thanks for the reply, Ann. 

I'm running Ubuntu 12.10. The Windows app I'm trying to run is Cobb AccessPort Manager which is an application that allows me to upload and download tuning maps to my Cobb AccessPort. It's used for fuel tuning on my car (which is modified).

I have two possibilities: Download the Windows version ([http://accessecu.com/support/accessport/apmanager/APManagerSetup.exe](http://accessecu.com/support/accessport/apmanager/APManagerSetup.exe)), or the OSX version ([http://accessecu.com/support/accessport/apmanager/APManager.dmg](http://accessecu.com/support/accessport/apmanager/APManager.dmg)). Whichever one will work is the one I'll use.

I tried the code you provided, and I get the following error messages: "Unable to locate package linusb-1.0-0" and "couldn't find any package by regex 'linusb-1.0-0"

---

### Post by oldos2er on 2013-03-29
[FONT=Arial]It's li[COLOR=#ff0000][FONT=Ubuntu Mono]b[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]usb-1.0-0, not linusb.[/FONT][/COLOR][/FONT]

---

### Post by alien_sporez on 2013-03-29
Ok, apparently I already installed that one because I get "libusb is already the newest version."

And I still get the same [COLOR=#000000] "Unable to find WinUSB or libusb on the system. Please re-install the application" error when starting up my AccessPort application.

Am I supposed to something other than just install the library file?[/COLOR]

---

### Post by steeldriver on 2013-03-29
Have you tried posting on NASIOC to see if anyone has ever got the AccessPort to work under wine?

I've never really used wine but I think USB support is still limited

---

### Post by alien_sporez on 2013-03-29
> **steeldriver said:**
> Have you tried posting on NASIOC to see if anyone has ever got the AccessPort to work under wine?

I've never really used wine but I think USB support is still limited
That is actually a really good idea. It's for a Mazdaspeed, so I think I'll also try mazdaspeedforums.org too.

---

### Post by squakie on 2013-03-29
It could also be telling you it needs the Windows version of libusb loaded in Wine, not the Linux version loaded in Linux.  I had to install it to Windows itself when I was doing cross-platform development with some special USB devices.

See:  [http://sourceforge.net/apps/trac/libusb-win32/wiki](http://sourceforge.net/apps/trac/libusb-win32/wiki)

---

