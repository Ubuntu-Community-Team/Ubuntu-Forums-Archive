---
title: "How do I enable my printer?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Bigpom on 2008-07-16
G'day All.I have just installed Ubuntu 8.04 as a duel boot with Windows XP and I cannot get my printer to work. I was advised to download z600 drivers from Lexmark to my Desktop which I have now done,. How do I install it. If I have to alter command lines, how do I do that? My printer is a Lexmark 1100 all in one(USB Connection) and my computer has the following specs:-
           130 GB HDD-2GB Ram-Pentium 4 2.5 ghz processor-Radeon 9550 Video card..........Regards...........Bigpom
PS The printer works fine in XP

---

### Post by L Campbell on 2008-07-16
> **Bigpom said:**
> G'day All.I have just installed Ubuntu 8.04 as a duel boot with Windows XP and I cannot get my printer to work. I was advised to download z600 drivers from Lexmark to my Desktop which I have now done,. How do I install it. If I have to alter command lines, how do I do that? My printer is a Lexmark 1100 all in one(USB Connection) and my computer has the following specs:-
           130 GB HDD-2GB Ram-Pentium 4 2.5 ghz processor-Radeon 9550 Video card..........Regards...........Bigpom
PS The printer works fine in XP

I'm really no whiz with setting up printers but this link was helpful to me:-

[http://localhost:631/](http://localhost:631/)

---

### Post by sub2007 on 2008-07-16
It needs quite a bit of effort but I managed to get my old Lexmark z600 series set up  using this guide: [http://finebushpeople.net/LexmarkZ600](http://finebushpeople.net/LexmarkZ600) I don't have a Lexmark at the moment so can't help you too much.

Before you start you'll have to run this command in Terminal:

```
sudo apt-get install alien
```

And enter your password when prompted.

Then just follow the instructions in the guide, pasting each line they give you into Terminal. For step 8 you will need to put sudo in front of the command.

Once you've followed those steps you'll need to add the printer. Go to Add Printer in Settings (I don't have a GNOME box so can't remember where it is in Ubuntu) and you'll need to click to "Specify a PPD file". Then locate the PPD file (which should be called z600 something)

---

