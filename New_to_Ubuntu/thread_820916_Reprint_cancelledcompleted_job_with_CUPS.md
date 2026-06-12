---
title: "Reprint cancelled/completed job with CUPS"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by H.Callahan on 2008-06-06
Ok, this is probably a totally newbie question.

Last night I had 4 print jobs submitted to my Ubuntu box from a Windows laptop on the network.  The printer errored out at the start of the first job.  I put the 3 other jobs on hold and had to cancel the first job so that I could attach a Windows laptop to the printer to see what problem was (I can't get any sort of actual status of the printer from within Ubuntu).  After I replaced an empty printer cartridge, I released the 3 held jobs and they printed normally.  I saw the job that I had to cancel in the completed jobs list, but I could not find any way to resubmit it to the printer.  I could not resubmit any OTHER completed job to the printer either.

So my question is, how does one do that?  I saw the option for the 3 held jobs and for the jobs while they were actually printing (although why one would want to reprint a job that had not yet printed in the first place is beyond me -- I would think one would want to reprint a job that had been canceled or completed).

BTW, this is with 7.10, if that is a difference.

---

### Post by cmnorton on 2008-06-07
Using CUPS' web interface at [http://localhost:631](http://localhost:631), you should be able to restart the jobs from that interface.

---

### Post by H.Callahan on 2008-06-07
From where within the interface?  No control buttons appear in the completed jobs as they do with jobs in progress.  Nor is there any way to select a completed job to do anything with.  See the attached screen shot of the interface.  The one job that does have control buttons is one that is currently printing.

---

### Post by cmnorton on 2008-06-07
Please assume I am wrong, and please accept my apology. I answered you from memory having used a CUPS interface on a Red Hat EL system, which does not help you on Ubuntu.

I will stop one of my printers on Monday (so stuff cannot print), and see what my CUPS interface does from Kubuntu 7.10. I'll post what I find here. I'll also stop another printer on a RH system, and try that as well. If I find something different, I'll post that information.

---

### Post by H.Callahan on 2008-06-07
No need to apologize.  I appreciate all the suggestions that I get.  I am very new to Linux, so please feel free to assume that I am doing something stupid.

I just find it strange that you would get an option to reprint a job that is either currently printing or not yet printed (what is the point?) and NOT have the option to reprint a completed job.

---

### Post by cmnorton on 2008-06-09
I looked at a cups display -- [http://localhost:631](http://localhost:631) -- on a Red Hat Enterprise Linux 4 system this morning. On the far right of the display for jobs completed, there is a restart button, but there is none on my Uubntu system.

---

### Post by H.Callahan on 2008-06-11
Anyone have any clues?

(a.k.a. -- Bump)

---

### Post by H.Callahan on 2008-06-13
No one?

---

### Post by H.Callahan on 2008-06-25
Still looking for an answer to this...

---

### Post by linuxpenguin on 2008-07-01
The unfortunate answer is that you're lost.  The jobs are gone - you can't get them back.  At least that's my understanding.

For the future. . .

You need to set up CUPS to keep your jobs by basically following the instructions here: [http://www.macworld.com/article/40847/2004/11/decgeekfactor.html](http://www.macworld.com/article/40847/2004/11/decgeekfactor.html)

(it's for a Mac but it should basically be the same).  Just add any lines they tell you to change that aren't already there and you should be set.  Also note that the CUPS syntax seems to have changed since them (2004! it looks like) - use "On"/"Off" instead of "Yes"/"No" (respectively).

I came across this because I did kinda the same thing on my Debian PC. . . printed some stuff, then closed out, and when I went downstairs to the printer I found a nice big streak where the cartridge ran out of toner. . .

---

### Post by stoian on 2012-09-23
I found an answer here:
[http://forums.opensuse.org/english/get-technical-help-here/applications/411134-how-reprint-jobs-cups.html]("http://forums.opensuse.org/english/get-technical-help-here/applications/411134-how-reprint-jobs-cups.html")

Basically, you should edit the file /etc/cups/cups.conf:

```

PreserveJobFiles On

```

Then, restart the cups daemon/service. On my CentOS 6 server (you have to see how it is on Ubuntu):
```

service cups restart

```

This way, after a job is completed, you'll get a button to "Reprint Job" in the rightmost column, when you look at the completed jobs page.

What I did, actually, I made the completed jobs last for 31 days, and also limited the number of jobs per user, and per printer, like this:

```

PreserveJobFiles 31d
MaxJobsPerUser 20
MaxJobsPerPrinter 50

```

More to read here: [http://www.cups.org/documentation.php/ref-cupsd-conf.html]("http://www.cups.org/documentation.php/ref-cupsd-conf.html")

Hope this helps.

---

