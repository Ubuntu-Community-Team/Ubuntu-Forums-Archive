---
title: "Establishing connection"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Skimbleshanks on 2008-09-02
On an HP Pavilion PC I have already installed Xubuntu 6.06 (Dapper Drake) as a dual boot system (only 24 hours and I love Linux already!)

I have already followed these helpful instructions, posted by Vikramaditya.

>  Re: how to install gtw modem
Open terminal and cut/paste the following:
Code:

sudo apt-get install setserial

Then run this:
Code:

setserial -g /dev/ttyS[01]

If it outputs something like this:
Quote:
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: 16550A, Port: 0x02f8, IRQ: 3
Then the modem has been detected & you create a link with:
Code:

sudo ln -s /dev/ttyS0 /dev/modem

Finally, use wvdial to get connected. Hope it all works for you!

"Thanks" to forum member tinivole, whose work I have shamelessly plagiarized above.

with the result "Modem not responding"

I also found out how to use System => Networking => network-admin
to attempt to set up a connection:

"interface ppp0 is not configured"

so I selected "properties", checked "enable this connection", switched to the "Modem" tab, and clicked the "autodetect" button.

"could not autodetect".

If anybody has the patience to walk me through the necessary steps to establish an internet connection (it *will *work for Windows) I have nothing to offer but gratitude but you can have that by the dumpster-full if the idea appeals to you!

---

### Post by lucho64 on 2008-09-02
Kind of an old distribution you are using, but I use it as well on a laptop and so far since everything works so well I haven't upgraded.
The instructions you followed say:
```
sudo ln -s /dev/ttyS0 /dev/modem
```
but that assumes that the modem is the first serial port, that might not be the case. Try:
```

sudo rm /dev/modem
sudo ln -s /dev/ttyS1 /dev/modem

```

On the other hand, it might be that your modem is a "winmodem" (that is, a modem that is supposed to work only by using a software driver that comes with Windows) Do not despair, though, you might be able to make it work, but it probably is not going to be too easy. I would recommend you to drop by [_this really helpful site_]("http://linmodems.technion.ac.il/"). I actually don't know if you do have a winmodem, but even if you don't, that's a good place to start.

---

### Post by Skimbleshanks on 2008-09-02
Thank you, Lucho64. I was able to download the ScanModem file to my Windows computer, but haven't yet figured out how to mount the Windows drives (topic for another thread entirely, I think!)
Could you possibly point me in the right direction?

Thank you, again.

---

### Post by lucho64 on 2008-09-02
Chances are the following will work if your setup is standard
```

sudo mkdir /media/Windows
sudo mount /dev/hda1 /media/Windows

```

/dev/hda1 would be the partition where windows lives (usually the first partition on the first disk) You can go to System->Administration->Disks->Partitions and mount it there if you rather use a GUI.

---

### Post by Skimbleshanks on 2008-09-04
> **lucho64 said:**
> Kind of an old distribution you are using,
soz for bumping this! Dapper may be an old distribution, but I don't think it's quite as old as WinME which is my Windows alternative!
:)

---

