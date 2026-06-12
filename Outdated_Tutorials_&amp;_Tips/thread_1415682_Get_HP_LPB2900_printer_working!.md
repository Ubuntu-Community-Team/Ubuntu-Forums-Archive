---
title: "Get HP LPB2900 printer working!"
date: 2010-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by herophuong on 2010-02-25
I have a tips to get this popular printer to work on my ubuntu karmic system.
After following very many tutorials ([UNIXMEN]("http://www.unixmen.com/linux-distributions/ubuntu/229-installation-canon-lbp2900-on-linux"), [Wiki Ubuntu]("https://wiki.ubuntu.com/Canon_LBP_2900_HowTo"), [Ubuntu Community]("https://help.ubuntu.com/community/CanonCaptDrv190")) on the web to set up this printer, you are so angry because it doesn't work (or works for the first time and after restarting your computer it doesn't print anymore) !!! Arghh.....
However, I find an interesting thing about it!!!
If you follow the guide on this forum (or any guides I provided above), at the end you should enter a command in the terminal:
> captstatusui -P LBP2900
Then you see a windows with blank message. Nothing here, right?
We will begin from here:
> gksudo gedit /etc/ccpd.conf
Change the tag <Printer LBP2900> to <Printer LBPxx00> (like 2000 or 5000, etc)
Then:
> sudo /etc/init.d/ccpd stop
> sudo /etc/init.d/ccpd start
If it does nothing, restart your computer.
Now we enter the first command once again. We should see the message "No specified printer". Don't worry! We will re-edit the ccpd.conf (change LBPxx00 to LBP2900).
Notice that: We don't restart the machine now! Open the terminal and enter two command below:
> sudo /etc/init.d/ccpd stop
> sudo /etc/init.d/ccpd start
To make sure we are successful, enter this command again:
> captstatusui -P LBP2900
Now, our printer are "Ready to print".
(Sorry, if you see any grammar mistakes in my post please let me know. Thanks)

---

### Post by bluelightav on 2010-03-01
Are you talking here about the Canon LPB2900 or HP?

---

### Post by herophuong on 2010-03-06
I don't know if it works with other HP's printers because I don't have them here. But I hope it would works.

---

### Post by bluelightav on 2010-03-07
> **herophuong said:**
> I don't know if it works with other HP's printers because I don't have them here. But I hope it would works.

Did you read my question?

---

### Post by herophuong on 2010-03-11
Sorry, I had a mistake. It should be "Canon LBP2900".

---

