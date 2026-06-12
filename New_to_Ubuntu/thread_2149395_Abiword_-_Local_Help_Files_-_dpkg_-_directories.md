---
title: "Abiword - Local Help Files - dpkg - directories"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by Xpinguin on 2013-05-28
Hi,

I'm sorry if this is not the right forum to post this, I did my best. I don't even
 know if my problems are more Abiword or Xubuntu related, or if the following
 symptoms have a single cause or several. So here it is.

Abiword's local (my hard drive) Help files are either missing or misplaced.

This is a fresh Xubuntu Desktop 64-bit install, with Abiword pre-installed as
 default word processor.

I just did "apt-get update" and "apt-get upgrade".

"apt-cache show abiword" gives me: Version: 2.9.2+svn20120213-1

When I click on (main menu) -> Help -> Help Contents (F1) I get my web
browser telling me "File not found" pointing to
/usr/share/abiword-2.9/help/en-GB/interface/dialogplugins.html.

It can't find it because it is not there.

At the level of /help/ the following directories are present:
1. certs
2. clipart
3. strings
4. templates
5. ui
6. xsltml

There is no /help/ directory.

The command "dpkg -L abiword" does not even show
/usr/share/abiword*/,
but as stated above, I do have a directory called:
/usr/share/abiword-2.9.

Why is this directory not present in the list presented by "dpkg -L abiword" ?

I tried to access the help from the menu a second time and this time I was
sent to [http://www.abisource.com/help/en-US/index.html](http://www.abisource.com/help/en-US/index.html).

At the top of the page (AbiWord Help):
"Thank you for installing AbiWord! This documentation is normally
 installed with your AbiWord distribution package, however, if you are
 viewing this on-line, you can usually update both your AbiWord
 version and your copy of the manual by visiting
 http://www.abisource.com/."

Then, on that page:
- latest stable release version: 2.8.6
- latest development release version: 2.9.4

I got some info from "Ubuntu › xubuntu-devel" about the discrepency
([http://ubuntu.5.x6.nabble.com/xubuntu-devel-f1723848.html](http://ubuntu.5.x6.nabble.com/xubuntu-devel-f1723848.html)).

I don't see any link to download/install the help files on my hard drive.
Essentially they direct me to the Ubuntu repositories.

QUESTION: Should I explore this currently installed version to try to
install or move the Help files to the proper place, and what good first
step would be ? Or should it reinstall Abiword, or replace this version
with another ? In general, to sort out malfunctions should I include
multiverse, Canonical partners, and Independents repositories to
update/upgrade/downgrade packages ?

Since I'm learning to use Xubuntu, for package management, I'd rather
at first stick with using the "Ubuntu Software Center", or maybe Synaptic,
and fetch from "Cannonical-supported (main)", "Community-maintained",
and "Canonical Partners" sofware only until I am more at ease with Linux
in general, unless there is a specific reason to go elsewhere. I'm slow
working with the console but don't mind it, in fact I kind of like it and
think it's a good way to learn more, and I want to write shell scripts
eventually.

Thanks in advance.

---

### Post by ajgreeny on 2013-05-28
Just out of interest, can you manage to run that version of abiword successfully?

Many people find that it is totally unusable; impossible to type anything in its window, and also impossible to scroll.  In order to use abiword at all I have added a ppa from [https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise).  That gives me version **2.9.2+svn20120213really2.8.6-0ubuntu0.1~ppa1 **which is actually the previous version, the most up to date stable one available, and that works superbly in precise.

This does not, unfortunately answer your question as I don't think I have ever had a local help system for abiword

---

### Post by Xpinguin on 2013-05-28
OK I'll try your ppa1.  That's version 2.8.6-0, latest stable version, right ?
That's what the Abiword web site had to offer, but at the same time saying
that it's better to go through your disto's repositories to get packages.  I
don't remember Canonical (through Ubuntu Software Center) offering other
versions besides 2.9.2.  In fact I think they only offer one version, that is
the latest stable (normally, but not in the case of Abiword) release, of any
of their applications/packages.  I'm not sure about that.

Anyway, to answer your question, yes I have worked with Abiword 2.9.2,
but it hasn't been smooth.  In two weeks it crashed on me at least three
times and for apparently different reasons.  Also I'm not given the option
to open .odt files, which I need.  I'm having a hard time getting good
documentation.  Let's say at this time I wish I had a simple rtf editor
similar to Wordpad.  Maybe I'll install Jarte or Angel and see.

Bottom line is I would like to make Abiword work, and really work with
it, for a few weeks before I give up and try another program.  I haven't
been able to get more than a couple of pages in a document with some
formatting before something happened, like inexistent help files.  Also
I don't want to work a lot in a document and save it in the native Abiword
format if I may decide to ditch it eventually.  I know I can get it the
Abiword online help but I also know that it's defective and right now
I don't want to work "defective".  I'm trying to learn to use Linux.
Learning in a broken environment is not good for me.

I'll reply later about my experience your ppa.

Thanks.

---

