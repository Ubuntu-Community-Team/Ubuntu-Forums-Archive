---
title: "Suspicious &quot;Untitled Folder&quot; appeared on Desktop? Should I delete it?"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by Mahnoor on 2013-03-01
Hi I've been using Ubuntu for a year, but I only know very basic stuff.
I noticed a suspicious looking "untitled folder" that appeared on my desktop, while I was working on a Word document a few days ago. I did not delete it at the time(--i figured if its normal, then i don't need to be worried, if not, deleting might aggravate the problem (the latter was a windows virus experience)). 
I know that linux is supposed to be singularly virus free, so I wasn't really worried. Today, another folder appeared while i was working. So is it normal and should i simply delete these folders?
**Each of these folders further has an untitled folder inside** that doesn't seem to open. Or rather, it only opens when I select "open in a new tab". Then it has another 'untitled folder' in it, which also opens only in a new tab, and it goes on. 
And now I *am* worried:P.
I have wine installed and working.

P.S. i just realized (thanks to google) that I have the 'newfolder.exe' virus on my flash drive, possibly from my college computer, and I have been using the usb. Could this virus affect my system?

---

### Post by the8thstar on 2013-03-01
IMO and instead of trying an antivirus through Wine, I'd rather just wipe your home folder clean of the *.wine* folder and reinstall the *wine* program.
 
From a terminal, type :

> 
rm -f .wine
sudo apt-get autoremove wine
sudo apt-get install wine

As far as your USB key is concerned, you should format it, plain and simple !

---

### Post by Bucky Ball on 2013-03-01
You're using Word through Wine?

---

