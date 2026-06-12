---
title: "Print jobs held"
date: 2015-09-17
forum: New to Ubuntu
---

### Post by eric75 on 2015-09-17
I have an HP LaserJet 1102w. It's been printing wirelessly, then was mysteriously holding jobs. I fixed it. Now it's back.

Why is it happening again, and how can I fix it for good?

---

### Post by tgalati4 on 2015-09-17
I had a similar problem with a wired printer and it turned out to be a bad power supply on a gigabit router that the printer was hung off of.  I thought the printer was going bad, but then I noticed a lot of reset flashing on the router.  The power supply was 11.48 VDC, under the 12 VDC needed to keep the router going.  Swapped in a new power supply, problem solved.  So sometimes printer problems are not really printer problems.

What did you do to fix the printer?  How long does it take to foul up?

Open *hp-toolbox* and examine the status frequently and keep track of the errors.  Print jobs will be held when there is a communication error.  With a wired printer it could be a bad network card in the printer.  With wireless, it could be simple interference.  Use *WiFi Analyzer* on a smartphone to survey your wireless neighborhood.

---

### Post by eric75 on 2015-09-19
I don't remember how I fixed it. Something with cups I think. It's been a few months.

One thing that was weird - someone's print jobs appeared on my printer.  A neighbor perhaps. I never did find out who it was...

And, since these jobs would turn on the printer, I just unplugged it. I wonder if that did something...

---

### Post by tgalati4 on 2015-09-19
It's possible that you need to clear print jobs in the printer queue.  It's also possible that you need to reset the firmware on the printer.  There should be a reset in the maintenance menu.  Try using a cable and see if the printer works reliably with a network cable.

---

### Post by dsjstc on 2015-12-14
For others stumbling on this, here's my solution:

[http://askubuntu.com/questions/250703/print-jobs-held-and-after-manually-releasing-them-they-return-to-being-held/709486#709486](http://askubuntu.com/questions/250703/print-jobs-held-and-after-manually-releasing-them-they-return-to-being-held/709486#709486)

---

### Post by Yawanathan_Israel on 2015-12-16
Hello,

If a neighbor has somehow hacked into your router to print a document, I would first check your security levels and make sure it doesn't happen again. If a print job gets hung, Usually only the person who commanded the print job can erase it. You have to be admin to override that and delete the print job. This is probably what is hanging your printer.

Turning off the router, then the printer, and turning back on the router, letting it reset and then the printer may help. But ultimately the fact that a neighbor can put a print job on your network, would be concerning, unless they came into your home, connected to your network and started a print job. Either way the print que must be cleared before anyone can print.

Thanks
Yawanathan




> **eric75 said:**
> I don't remember how I fixed it. Something with cups I think. It's been a few months.

One thing that was weird - someone's print jobs appeared on my printer.  A neighbor perhaps. I never did find out who it was...

And, since these jobs would turn on the printer, I just unplugged it. I wonder if that did something...

---

