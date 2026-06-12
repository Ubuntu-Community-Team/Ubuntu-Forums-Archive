---
title: "[SOLVED] Wine stopped working?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by dsurge on 2008-11-05
Hi guys, I'm still new but I decided to try to play with Ubuntu to optimize it. I followed these guides:

[http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html](http://yoten.blogspot.com/2007/04/speed-up-ubuntu.html)

[http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml](http://news.softpedia.com/news/Optimize-Ubuntu-8-04-for-Speed-86405.shtml)

but now my Microsoft Office (which used to open perfectly) won't run... When I go to wine and try to open Word, it says Starting Microsoft Office in my toolbar, then it disappears. When I try to fix the installation by putting in the cd and typing wine /media/cdrom/setup.exe, whatever I try to run gets "Installation ended prematurely because of an error" in the office console and 

```
err:msi:ITERATE_PublishAssembly Failed to copy temporary assembly: 5
err:msi:ITERATE_Actions Execution halted, action L"InstallExecute" returned 1627
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1627
```

in terminal.

I've uninstalled wine, deleted the .wine partition, removed it in synaptic and reinstalled it... but I cant get office 2003 to work anymore... 

help anyone?


P.S. T61, T7300, Nvidia NVS 140m (177 proprietary driver installed), 2 gigs ram, 1 gig swap, ubuntu 8.10 64 bit, compiz enabled, and the hardware test looked good.

---

### Post by LowSky on 2008-11-05
seems to be a wine issue, those system tweaks had nothing to do with it from what I looked into

I did a google seach on the code you got back and found this

[http://bugs.winehq.org/show_bug.cgi?id=14993](http://bugs.winehq.org/show_bug.cgi?id=14993)


I found this page [http://www.codeweavers.com/support/tickets/browse/?ticket_id=110846;s_subject=prematu](http://www.codeweavers.com/support/tickets/browse/?ticket_id=110846;s_subject=prematu) 
and it suggest running this command

/opt/cxoffice/bin/wine /mnt/cdrom/setup.exe

note the command is for code weaver, not wine, but something simular should work

---

### Post by Kellemora on 2008-11-05
Hi DS

You might be better off using Crossover Office if you insist on using msOffice........

I couldn't get it to work in Wine either, so opted to move everything over to Open Office, and honestly, I'm VERY GLAD I did.  Our production levels increased considerably using OOo.  And we just save the files as .doc files for those who need copies on their computers.

Have never had a problem going from OOw to msWord yet.  But going from msWord to OOwriter can sometimes cause a problem since OOwriters available workspace is like 6 pixels less than msWords available workspace.
Once we figured that out, it was a simple matter to reconvert all the files that did cause us problems without having to reformat each one.

TTUL
Gary

---

### Post by dsurge on 2008-11-05
I looked at cross over but isn't it a trial? So will I only have office for a week?

---

### Post by Kellemora on 2008-11-05
HiDS

I think you're right that it is a purchased program.  I've never used it myself since OOo handles everything we do, tri-fold full color pamphlets, school yearbooks, newsletters, bottle and carton labels, etc. and of course documents.

We do have to keep an XP machine here for our accounting program and it still has msOffice on it, but after getting used to OOo all of my employee's prefer it over msOffice.  It's faster, images don't hop around on the pages at print time, or while editing, and we can adjust the format more tightly, especially on those darn tri-fold pamplets so they come out just right.

We send a lot of printing directly to a printer via e-mail, since we have switched to OOo, he has not had to tell us to make adjustments because when queued to their printers it just don't mess up like msOffice did quite often.  He just updated his program too for color separation so I can just send the .odt files.  He said they run a whole lot faster too!

Can I ask what it is your doing that you need msOffice for?
And have you tried OOo yet?  It's free you know!

TTUL
Gary

---

### Post by dsurge on 2008-11-06
It's more of a thing I'm used to. I've been using it for a long time and I just feel comfortable in it... at least for now.

Anyways, I fixed the problem, but I have no idea what the issue was. I did a clean boot for an unrelated reason and reinstalled it. Now it works fine. Thanks guys:)

---

