---
title: "Brother HL-5240 Printer"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Glkanter on 2012-05-18
I was given this printer the other day.

It sure *seems* like it's set up right, but nothing at all happens:

The status light is green.

It shows up, looking just fine, under System->Administration->Printing.

Test Jobs go to the print queue.


The "cancel" button on the printer even works!! It cancels the jobs backing up in the queue.

But there are no sounds, and no output.


Thanks!!

---

### Post by Fraoch on 2012-05-18
How did you set it up?

Brother has pretty extensive support for Linux:  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

I see your printer is there.  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5240](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5240)

Are you using the drivers on their site or something built-in?  Use their drivers.

There's also a HOWTO here: [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by Glkanter on 2012-05-18
Thanks. 

I did nothing but plug in the power and plug in the usb cable.

I didn't even see any configuration activity on screen, like you would see with Windows.

Can you recommend one of those links over any others? It can be intimidating having too *many* places to look.

Thanks so much!

Garry

---

### Post by Fraoch on 2012-05-18
> **Glkanter said:**
> 
Can you recommend one of those links over any others? It can be intimidating having too *many* places to look.

Just follow the directions on the Brother site for your particular printer:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5240](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-5240)

Download the cupswrapper deb (don't bother with the LPR driver).  I guess the ppd would also work, but as it's not available for my Brother printer I've never tried it.

Follow the instructions.  Note this is all on the command line, but you more or less just have to cut-and-paste.

*If* you get stuck then go to the HOWTO:

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

---

### Post by Glkanter on 2012-05-19
Thanks.

I'm getting nowhere fast. I just don't have the skills to interpret what they are trying to convey.

---

### Post by plucky on 2012-05-19
> **Glkanter said:**
> Thanks.

I'm getting nowhere fast. I just don't have the skills to interpret what they are trying to convey.

Your printer has the drivers packaged in synaptic package manager.

Open Synaptic Package Manager and search for **HL-5240** and it should find brother-cups-wrapper-laser and brother-lpr-drivers-laser.

Select both and install.

Then open **System Settings > Printers** and Add a new printer and you can now select the driver for your printer.

Good Luck

---

### Post by Glkanter on 2012-05-19
For the record, I'm not lazy. After all these years of tussling with PCs and stuff, I just know when I'm spinning my wheels without benefit or progress.

I could really use some help here, along the lines of, "Step 1 - do this, Step 2 - type this, Step 3..."

Thanks to anyone who is willing to help a frustrated, but needy, fella out of a jam.

Sincerely,

Garry Kanter

---

### Post by Glkanter on 2012-05-19
plucky,

I had not seen your response when I posted the above plea.

I will give that a try.

Thank you!!!

---

### Post by Glkanter on 2012-05-19
You guys are the best!!

Now for the rest of the story...

There was some user error involved. Despite a green "Status" indicator, I had replaced the toner cartridge improperly.

But my problem has been solved, thanks to you guys!!!

As always, many thanks to each of you that took the time to help me out!!

Sincerely,

Garry Kanter

---

