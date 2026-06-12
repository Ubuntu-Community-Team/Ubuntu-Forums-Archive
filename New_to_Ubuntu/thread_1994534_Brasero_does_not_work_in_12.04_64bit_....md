---
title: "Brasero does not work in 12.04 64bit ..."
date: 2012-06-02
forum: New to Ubuntu
---

### Post by cwmoser on 2012-06-02
Trying to burn a DVD data disk using Brasero but during
the burning process I get an error and the disc is 
not readable nor mountable.

Bugs in Brasero?

Ubuntu 12.04 64-bit version.

Carl

---

### Post by drs305 on 2012-06-02
don't know what's happening on your system but I've burned about half dozen LiveCD's of various Ubuntu releases using Brasero in 12.04 64-bit without problems.

Brasero  3.4.1-0ubuntu1

---

### Post by traditionalist on 2012-06-02
> **cwmoser said:**
> Trying to burn a DVD data disk using Brasero but during
the burning process I get an error and the disc is 
not readable nor mountable.

Bugs in Brasero?

Ubuntu 12.04 64-bit version.

Carl

Works fine for me now, but I did have some problems burning system disks which turned out to be faulty.  Hung up the program and the burner. Couldn't find/create a checksum.

---

### Post by cwmoser on 2012-06-02
Tried it a different way.

[B][U]
This way does not work for me:[/U][/B]
Insert DVD, get prompt to open with CD Creator, dismiss, 
and click on Brasero to burn.
[B][U]
This way does work for me:[/U][/B]
Insert DVD, get prompt to open with CD Creator, OK, 
DVD burns OK.  

In both instances, the software cannot not eject the disc.
It puts up a message box telling me to eject the disc.

Carl

---

### Post by mapes12 on 2012-06-03
You could try K3B for burning discs. I prefer it.

---

### Post by edeneen on 2012-06-03
Brasero did not work for me either,  gave a data error message.

---

### Post by Curtis6767 on 2012-06-03
> **mapes12 said:**
> You could try K3B for burning discs. I prefer it.

2nd K3b.

---

### Post by cwmoser on 2012-06-03
Glad to hear that others are having issues with Brasero and its
not all my incompetence.

Going to give k3b a go.

Thanks

Carl

---

### Post by wrknight on 2012-08-21
Likewise, Brasero no longer works like it used to.  It only recognizes one drive and it won't read faster than 1.4x.  These are brand new drives and the old Brasero would read CDs at more than 20x.  

Also in the box that says select disc to copy, I get the stupid message "my CD:58 min" that stays there only so long as you hold the down arrow with the mouse.

I have 3 64 bit computers all now upgraded to 12.04 and Brasero isn't working right on any of them.

---

### Post by wrknight on 2012-08-21
Installed k3b and it worked beautifully "right out of the box".  1 minute, 45 seconds to copy a 58 minute audio CD.True "plug and play".  It's nice to know some people can get it right.

---

### Post by newb85 on 2012-08-21
Out of curiosity, with this chorus of complaints on the issue, has anyone filed a bug report for Brasero?

---

### Post by jwillar on 2013-05-20
I just wanted to add my two cents worth.  Yes newb85 lot of bug reports have been filed for Brasero.  However having spend several hours researching this issue I have gotten Brasero to work.  Can someone verify this solution?

Two systems running Xubuntu 13.04 and Mint 13 (Mate); both using Brasero 3.6.1.
Problem, Brasero burns images and data cDs but failes to make a copy; error out.

I found that if I install the following, Brasero would make a copy of an audio cd.
> cdrdao
> cue2toc

---

### Post by MZ250Supa5 on 2013-06-02
It would seem that Brasero has been causing problems for the past 3 years, since 10.04 was launched. Whether this issue is related to a seemingly general one of rushed releases with packages that are included by default that just don't work I don't know.  I haven't until today tried copying CDs but I'm having problems in that Brasero gets to the point where there is a window with a progress bar and the words. 'preparing to copy...' but no action at all, it just remains stuck on this.   This is extremely frustrating when it's a package included by default, it should just work, or it shouldn't be included as a default application.

I have now downloeded and installed cue2toc, as suggestrd by jwillar, so I shall now go and try again.

Strangely, I can copy DVDs with no problems whatsoever.

---

### Post by ibjsb4 on 2013-06-02
K3b is an excellent choice, but if you want something light then take a look at xfburn.

---

### Post by Buntu Bunny on 2013-06-02
This seems to be an ongoing problem with Brasero with several years' worth of bug reports for various versions. I see lots of suggestions  here for K3b, but I find Xburn has consistently met my needs.

---

### Post by thotz on 2013-06-06
If you want to you are invented to raise a bug. Please see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for more information.

---

### Post by VMC on 2013-06-06
I've had a lot of trouble using Brasero, and quite using it. Maybe cdrtools is the answer. Here is a [link]("http://askubuntu.com/questions/142674/brasero-12-04-precis-cdrecord-instead-of-wodim-cdrtools-instead-of-cdrkit-plu") that may help explain why.

---

