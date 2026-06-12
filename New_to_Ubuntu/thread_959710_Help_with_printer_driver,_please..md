---
title: "Help with printer driver, please."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Gasfan on 2008-10-26
Hi all,

I've been spoiled, until now, by Ubuntu Hardy setting everything up so perfectly that I've hardly noticed the transition from Windows. Consequently, Ubuntu is the only O.S. on my machine.  My Epson printer recently gave up the ghost, so I treated myself to a shiny new Canon Pixma MP470 printer/scanner - which doesn't work (at all).  I discovered Linuxprint.org, and have downloaded a driver that I think *might *work, although my printer wasn't actually listed.  The file is now sat at the top of my Downloads list - but what do I do next?  I know how to open a terminal, but nothing about working from a command line.  Excuse my ineptitude; any help will be much appreciated.  I'm not immediately concerned about scanning, but need a printer ASAP.

John.

---

### Post by jmcgovern on 2008-10-26
What's the file you downloaded?  What's the extension?  Honestly, you may not be able to get it to work, unless you want to pay for Turboprint.  Canon's Linux support, frankly, sucks.  I still can't get my PIXMA ip2600 to work, so I have to reboot to Vista to print.

---

### Post by skintythe1andonly on 2008-10-26
I had a canon ip2500 last year. I got it working using the drivers they provide on their website

[http://www.canon-europe.com/Support/software/linux/]("http://www.canon-europe.com/Support/software/linux/")


One of those drivers may work with your PIXMA printer. I dont know about the scanner. They released the drivers in .rpm format which i installed using alien. Let us know how you get on. It looks like a good piece of kit.

---

### Post by wolfen69 on 2008-10-26
i read that the mp150 drivers work with your printer. also, before buying hardware blindly, you might want to check for compatibility first. HP is hands down the best printer for linux. if you can return it for a refund, i would.

---

### Post by Riffer on 2008-10-26
[http://www.canon.com.au/support/default.aspx](http://www.canon.com.au/support/default.aspx)

This the support site for canon in Australia, which for some odd reason has linux drivers for many of their printers.  The printer in the OP I couldn't find but some of the others found in the thread can find drivers on this site.

I have a mp260 and used the driver found here and it works well.

---

### Post by Gasfan on 2008-10-28
Thanks folks for your replies.  I've reached a stage where the printer winds a sheet of paper through when I klick on Print.  Not much use.I know, but at least it's a response!
The driver that I downloaded, but don't know what to do with next, is ghostscript - 8.63.tar.gz

---

### Post by wolfen69 on 2008-10-29
```
sudo apt-get install build-essential
```
put the tar.gz file in your home folder. then right click it and extract here. then ```
cd name_of_folder
``` then ```
./configure
``` then ```
make
```then ```
sudo make install
```

---

### Post by macogw on 2008-10-29
I'd second the "return it for an HP" comment.  Plug an HP in and a few seconds later, Ubuntu will announce that the printer is ready.

---

### Post by Gasfan on 2008-11-01
Thanks wolfen69 for your detailed help. I've followed it to the letter and installed the driver.  Now, when trying to print, the screen on the printer says "Printing from PC", but the machine just winds a sheet of paper through.  So near and yet so far.  Any further thoughts would be much appreciated.

John.

---

### Post by Teabicky on 2008-11-01
I've got a Lexmark and have had the same trouble, so I am just gonna get a Hp.

---

### Post by Gasfan on 2008-11-02
I've just returned from our local Comet branch, having paid £14.99 for an HPDeskjet D1460.  Took ten minutes to get it printing!  It's rather flimsy - but prints fine, so what the heck.  It's bought me some time, but I'll get the Canon machine working eventually if only to justify the expense!  Thanks for all your comments and help - if nothing else, I've learned a little about working from a terminal.

John.

---

### Post by ezramorris on 2008-11-02
You could have a look at [_this thread_]("http://ubuntuforums.org/showthread.php?t=943626"). No idea if your model work work or not.

---

### Post by Gasfan on 2008-11-05
Thanks Ezramorris.  Have followed your link and printed off the advice with my fifteen quid HP printer.  Will follow steps when I have more time, and report back.
Thanks again,  John.

---

