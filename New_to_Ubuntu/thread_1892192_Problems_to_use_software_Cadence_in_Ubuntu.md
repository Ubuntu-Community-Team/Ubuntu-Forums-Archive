---
title: "Problems to use software Cadence in Ubuntu"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by lunar_torrific on 2011-12-07
For using a software named [Cadence]("http://www.cadence.com") I stared to use linux Ubuntu-11.04 a few days ago. Altouhgh the use of linux is lillte beat diffcult but I have got some extra advantages in using linux. For example: the speed of PC increases, no threat of viruses etc. So I have stated to love linux operating system.

But althought for using the software Cadence i started to use linux its a matter of sorrow that i cant use cadence in linux yet. After installing Cadence when I went to open a new Cell view i have got this error message always: 

(deLicense-5) Could not get the license for Schematics. Open aborted.

But I have make the procedure of licencing at the time of installation. For checking the condition of license i used the command: 
lmli.

The output of this commnd in sheel script is: 

lunar@Lunar:~/Software/Cadence$ icfb
*WARNING* Unable to find font name: "-*-courier-medium-r-*-*-12-*".
*WARNING* Cannot find textFont.  Trying font "fixed".
*WARNING* Unable to find font name: "-*-helvetica-medium-r-*-*-12-*".
*WARNING* Using the text font to present labels.
*WARNING* Unable to find font name: "-*-helvetica-medium-r-*-*-14-*".
*WARNING* Using the text font for Help dialogs.
*WARNING* Unable to find font name: "-*-helvetica-medium-r-*-*-12-*".
lunar@Lunar:~/Software/Cadence$ lmli
lunar@Lunar:~/Software/Cadence$ 20:13:07 (lmgrd) -----------------------------------------------
20:13:07 (lmgrd)   Please Note:
20:13:07 (lmgrd) 
20:13:07 (lmgrd)   This log is intended for debug purposes only.
20:13:07 (lmgrd)   In order to capture accurate license
20:13:07 (lmgrd)   usage data into an organized repository,
20:13:07 (lmgrd)   please enable report logging. Use Macrovision's
20:13:07 (lmgrd)   software license administration  solution,
20:13:07 (lmgrd)   FLEXnet Manager, to  readily gain visibility
20:13:07 (lmgrd)   into license usage data and to create
20:13:07 (lmgrd)   insightful reports on critical information like
20:13:07 (lmgrd)   license availability and usage. FLEXnet Manager
20:13:07 (lmgrd)   can be fully automated to run these reports on
20:13:07 (lmgrd)   schedule and can be used to track license
20:13:07 (lmgrd)   servers and usage across a heterogeneous
20:13:07 (lmgrd)   network of servers including Windows NT, Linux
20:13:07 (lmgrd)   and UNIX. Contact Macrovision at
20:13:07 (lmgrd)   [www.macrovision.com]("http://www.macrovision.com") for more details on how to
20:13:07 (lmgrd)   obtain an evaluation copy of FLEXnet Manager
20:13:07 (lmgrd)   for your enterprise.
20:13:07 (lmgrd) 
20:13:07 (lmgrd) -----------------------------------------------
20:13:07 (lmgrd) 
20:13:07 (lmgrd) 
20:13:07 (lmgrd) "Lunar": Not a valid server hostname, exiting.
20:13:07 (lmgrd) Valid license server system hosts are: "computer" 
20:13:07 (lmgrd) Using license file "/home/lunar/Software/Cadence/share/license/license.dat"


Probably there is something wrong in the licensing but canot detect where is the problem. Could anyone please tell me where is the problem?

---

### Post by Diametric on 2011-12-07
I might check with the vendor that gave/sold/licensed the software to you.  See if they have specific instruction for an Ubuntu/Linux installation.

Good Luck!

---

### Post by lunar_torrific on 2011-12-07
> **Diametric said:**
> I might check with the vendor that gave/sold/licensed the software to you.  See if they have specific instruction for an Ubuntu/Linux installation.

Good Luck!

I follow the instructions according to [this instructions]("http://getglitched.com/?page_id=143"). But cannot understand the problem is in my process or in my license file.

---

