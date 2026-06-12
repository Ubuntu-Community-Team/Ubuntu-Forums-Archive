---
title: "Screensaver Doesn't Always Start"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by safetycopy on 2008-08-04
Hi,

This is more of an irritation than a real problem...

I am running 8.04 (no updates so far as I'm on dial-up).

Sometimes, my screen will fade as if the screensaver is about to start, but then brightens up again and the screensaver doesn't start. Why does this happen and is there anything I can do to fix it?

---

### Post by perlluver on 2008-08-04
> **safetycopy said:**
> Hi,

This is more of an irritation than a real problem...

I am running 8.04 (no updates so far as I'm on dial-up).

Sometimes, my screen will fade as if the screensaver is about to start, but then brightens up again and the screensaver doesn't start. Why does this happen and is there anything I can do to fix it?

Is this a laptop, or a PC?

---

### Post by safetycopy on 2008-08-04
Desktop PC...

---

### Post by perlluver on 2008-08-04
> **safetycopy said:**
> Desktop PC...

You said you haven't updated, have you at least installed the video drivers?

---

### Post by safetycopy on 2008-08-04
Yes - I have the nvidia-glx drivers installed...

---

### Post by perlluver on 2008-08-04
> **safetycopy said:**
> Yes - I have the nvidia-glx drivers installed...

I'm not really sure what is going on, it sounds like the computer is older.  Could you post the output of lspci?

---

### Post by safetycopy on 2008-08-04
Yeah - the machine is definitely older... 1.2Ghz, 512Mb RAM, 264Mb GeForce4... But it's all I've got and I love it :-)

Here's the output from lspci:

```
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 02)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)
01:0d.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

```

---

### Post by Fuzztrek on 2008-08-13
I also have this problem.  I'm on a new desktop running 8.04 with all updates (including nvidia drivers), however the screensaver doesn't start with compiz enabled.  The screen will fade to black, and then clear immediately as if nothing ever happened.  If I use Metacity instead, the screensaver works fine.  I might also add that all screensavers preview perfectly in the Screensavers preference dialog.

I've searched high and low for someone with a comparable problem, and this thread is the closest I've come.  Googling "screensaver" and "compiz", or "gnome-screensaver" and "compiz", results in lots of people complaining about another issue with screensavers, one that involved compiz locking the user out of their keyboard and mouse when the screensaver started.  I do not have this problem, however. Or maybe I will, once I get the screensaver working! Hah.

I will continue scouring the forums for related problems, and update if I come across anything.  To the OP, does the screensaver work if you switch to metacity (```
metacity --replace
```, or from the Compiz Fusion Icon, select the Metacity window manager)?

Update: Perhaps I lied. My screensaver isn't even working with Metacity now (although I'm certain it did once before, earlier today.)  Very odd.

Update: Hmm. Metacity sometimes works.  Also, my monitor never shuts off, though I have it set to after 10 minutes in both the Power Management and Screenshot - Power Management dialogs (possibly the same thing?)

Very strange. From my searches, it seems many people have this problem or have had this problem, but there don't seem to be any solutions so far or even clues as to what is causing the problem.  I suppose it's a pretty minor issue, but it's still disconcerting to not know what the problem is.

---

### Post by Too Late on 2008-08-31
> **safetycopy said:**
> Hi,

This is more of an irritation than a real problem...

I am running 8.04 (no updates so far as I'm on dial-up).

Sometimes, my screen will fade as if the screensaver is about to start, but then brightens up again and the screensaver doesn't start. Why does this happen and is there anything I can do to fix it?
I'm having exactly the same problem. I would estimate that the probability of this bug is about 35 %.

I saw this bug first time right after fresh install (ubuntu-8.04.1-desktop-i386), when everything was set to defaults. The screensaver theme doesn't matter. I'm not sure if the timout matters (default is 10 which I've used). Reinstalling OS doesn't help. The problem doesn't exist on other operating systems.

My computer: Athlon XP 1700+, GeForce3 Ti 200, Asus A7V600-X, 512 MB, wired ball mouse.

---

### Post by cek on 2008-09-25
> **Too Late said:**
> I'm having exactly the same problem. I would estimate that the probability of this bug is about 35 %.

I saw this bug first time right after fresh install (ubuntu-8.04.1-desktop-i386), when everything was set to defaults. The screensaver theme doesn't matter. I'm not sure if the timout matters (default is 10 which I've used). Reinstalling OS doesn't help. The problem doesn't exist on other operating systems.

My computer: Athlon XP 1700+, GeForce3 Ti 200, Asus A7V600-X, 512 MB, wired ball mouse.

Same thing here....  It was working fine with Edgy (32bit), but after an upgrade to Hardy (64bit) it stopped working.  Screensavers ALL preview properly but when idle the screensaver doesn't work -- screen goes blank and monitor NEVER goes to standby.

I'll try tonight to run WITHOUT compiz and see if that makes a difference.

---

### Post by fastfret79 on 2008-10-04
I'm having an almost identical problem - the screen fades to black and just as the screensaver is about to kick in, the screen comes back to normal.

I've been trying to self-diagnose what is happening but i haven't got to the bottom of it yet.

I had the same problem with Hardy and now with the Intrepid Beta. Both have the nVidia driver enabled and compiz but disabling them seems to have no effect.

I think it may be due to a conflicting app or task running as the screensaver will mostly work when the system is first booted, but after a couple of hours of uptime and a few apps open, it seems to stop. I used to think it was MythTV as that should disable the screensaver while I am watching TV, but sometimes this happens before I even run MythTV. The other apps I mainly use are Evolution, Firefox and Amarok,  but I'm still at a loss as to what actually causes it.

Logging out and back in again doesn't seem to work either - the system has to be completely restarted for the screensaver to work again. 

I guess I'll keep looking....

---

### Post by mikeize on 2008-10-10
Same problem here.  Screensaver worked fine in Hardy, but since I upgraded this week to Intrepid, it will fade to black... and then snap back to normal without ever showing even a second of the screensaver.  So weird.

*EDIT* FIXED IT *EDIT*

install compizconfig-settings-manager and uncheck "unredirect fullscreen windows"  (system>preferences>compizconfig settings manager>general options>4th one from the bottom)

many thanks to BwackNinja for this solution.

---

### Post by Bucky Ball on 2011-06-22
This bug still exists in 10.04. Anyone on this thread get to the bottom of it?

---

### Post by hillhotel on 2011-06-26
> **safetycopy said:**
> Hi,

This is more of an irritation than a real problem...

I am running 8.04 (no updates so far as I'm on dial-up).

Sometimes, my screen will fade as if the screensaver is about to start, but then brightens up again and the screensaver doesn't start. Why does this happen and is there anything I can do to fix it?

I just fixed it on my machine running 10.04 LTS.  Here's what I did: Go to:

[http://portland.freedesktop.org]("http://portland.freedesktop.org/")

 And download the xdg-utils 1.0.2 file.  Extract it to an empty folder in your home user directory.  Open the README text file and read how to install the scripts.  You need to use a root terminal command line to do this.  Here's a quote: "You can optionally choose to install the scripts
to a target directory.  To do this, you could issue
the following commands:
         ./configure [--prefix=<your-place-here>]
        make install
that would cause the scripts to be installed to
  <your-place-here>/bin

<your-place-here> is found by a search (Nautilus File Manager) for the original file named: xdg-utils.

Mine was in: /usr/share/doc

Then, using the root terminal commandline, navigate into the folder where you unpacked (extracted) the downloaded folder.  Folder also=subdirectory depending on the PATH variable

Then do the ./configure make install routine.  Make sure you add the --prefix=<location-of-original-folder>

And wait between commands for the processes to finish and return the prompt.  Good luck.:popcorn:

---

### Post by hillhotel on 2011-06-26
root@a8n-la-pb:/usr/share/doc/xdg-utils# ls -l
total 32
drwxr-xr-x 2 root root 4096 2011-06-26 03:29 bin
-rw-r--r-- 1 root root 2696 2011-04-14 13:07 changelog.Debian.gz
-rw-r--r-- 1 root root 1257 2006-11-04 01:31 changelog.gz
-rw-r--r-- 1 root root 1450 2011-04-14 13:07 copyright
drwxr-xr-x 3 root root 4096 2011-06-26 03:29 man
-rw-r--r-- 1 root root 3865 2006-10-06 16:48 README
-rw-r--r-- 1 root root 2819 2007-06-24 15:54 RELEASE_NOTES
-rw-r--r-- 1 root root  731 2006-11-04 01:32 TODO

---

