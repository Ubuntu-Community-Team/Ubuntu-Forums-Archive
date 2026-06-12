---
title: "No luck in printing in Canon LBP 6000"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by mmasroorali on 2012-07-28
Dear All,
I did not think that this will be this frustrating.

Today I procured a Canon LBP 6000. As is told in [https://help.ubuntu.com/community/CanonCaptDrv190](https://help.ubuntu.com/community/CanonCaptDrv190), this printer has been successfully used in Ubuntu 12.04.

I followed the instructions in that page to the letter. However, nothing comes out of the printer when I try to print a test page.

Eventually, I see a status, Idle - "ccp send_data error, exit".

At one point, I saw a system error message related to c3pldrv.

In the output of sudo ccpdadmin, my FIFO path is //localhost:59787, instead of //localhost:59787 as mentioned in the above page.

The radu script ([http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)) was no luck.

captstatusui says,
Communication Error
Check the following:
- Is the printer turned on?
- Is the cable properly connected?

Both answers are yes, since the printer is actually on, and gets detected in cups.

I do not know what I can do now. 

Any suggestion will be appreciated.

---

### Post by mmasroorali on 2012-07-28
The printer finally printed after following the comment at [http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/#comment-578224454](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/#comment-578224454)

---

