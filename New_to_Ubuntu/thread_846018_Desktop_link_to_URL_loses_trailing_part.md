---
title: "Desktop link to URL loses trailing part"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-01
When I find a URL in Firefox that I wish to refer to again later in the day, I drag the link from the address bar to the desktop.

This creates a "Link to ..." launcher (I think it's called a launcher) with the URL on the desktop.

If I double-click the launcher (or right-click it and select "Open"), it opens in Firefox.

However, if the link contains a question mark, the trailing bit is omitted.

For example, if the link icon contains the link:
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)
Then Firefox opens:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)
without the question mark and its parameters.

What can I do to fix this problem?

---

### Post by nowshining on 2008-07-01
have u tried using the firefox bookmarks instead, ctrl+d in firefox :)

alas we need to know ur Ubuntu version.

---

### Post by Paddy Landau on 2008-07-01
> **nowshining said:**
> have u tried using the firefox bookmarks instead, ctrl+d in firefox :)
Yes, I use bookmarks when I want to keep a URL long-term or permanently.

For temporary links, such as something I'm researching for a day or two, I use the desktop. It works a treat in Windows, and (as I want to migrate from Windows to Ubuntu), I was hoping that I could do something similar in Ubuntu.

> **nowshining said:**
> alas we need to know ur Ubuntu version.
I'm using the latest version, 8.04.

---

### Post by cpetercarter on 2008-07-01
Yes, its a pain. I have a "temporary" folder in my Firefox bookmarks toolbar, and drag and drop urls there for sites that I need only for the next few days.

---

### Post by Paddy Landau on 2008-07-01
> **cpetercarter said:**
> Yes, its a pain. I have a "temporary" folder in my Firefox bookmarks toolbar, and drag and drop urls there for sites that I need only for the next few days.
Thanks, I'll do that too.

---

### Post by Paddy Landau on 2008-07-01
Hmm...

I've just discovered that Firefox 3 has an easy-to-use "Unsorted Bookmarks" folder that could be used just for this purpose.

See [Bookmarks]("http://support.mozilla.com/en-US/kb/Bookmarks") in the FF3 help.

---

### Post by heykev on 2008-09-07
It's been a couple months since this thread was touched and I was wondering if anybody's had any luck with this.

I can consistently recreate the problem: a link on the Ubuntu 8.04 Hardy desktop will only pass part of the URL to the preferred app (Firefox, Epiphany, whatever).  Anything after the "?" in the URL is truncated.  Does that make it a Nautilus problem?

The workaround in the posts above is cool, but is there an actual solution?  I find links placed temporarily on the desktop to be more natural than bookmarks buried deep in a menu.

Thanks

---

### Post by Paddy Landau on 2008-09-07
> **heykev said:**
> The workaround in the posts above is cool, but is there an actual solution?  I find links placed temporarily on the desktop to be more natural than bookmarks buried deep in a menu.
I agree, it's more natural.

However, as we have the problem, I just use the "[Star Bookmark]("http://support.mozilla.com/en-US/kb/Bookmarks#Bookmark_Star")" as described in the FF3 help, always keeping my Bookmarks Sidebar open.

If it's important to you, raise a bug report for this (and please post the link here if you do).

---

### Post by heykev on 2008-09-07
Thanks, paddylandau.  I'll try keeping that Bookmarks Sidebar open.

I've never raised a bug report before.  What's the most useful (and socially acceptable) way to do that?  I'm grateful to the Ubuntu developers -- wish I was cool enough to contribute by fixing the bug myself -- so I want to report the bug as usefully as possible.

---

### Post by egalvan on 2008-09-07
> **heykev said:**
> 
I can consistently recreate the problem: a link on the Ubuntu 8.04 Hardy desktop will only pass part of the URL to the preferred app (Firefox, Epiphany, whatever).  Anything after the "?" in the URL is truncated.  Does that make it a Nautilus problem?

The workaround  above is cool, but is there an actual solution?
  I find links placed temporarily on the desktop to be more natural than bookmarks buried deep in a menu.
Thanks

I agree with the "more natural", not to mention easier.

This happens under Ubuntu 8.04.1, and is very annoying when using it with these Forums.
Whenever I want a link to a specific message, i drag the icon to the folder with the text. But when I try to launch it with FF3.01, it gets cut off at the "?".

Under Kubuntu 8.04.1, the link becomes a "dropped content" file, just text.

Must be Ubuntu-Linux-related, because the same links work under FF3.01 in Win-XPsp2.

---

### Post by kaibob on 2008-09-07
> **heykev said:**
> Thanks, paddylandau.  I'll try keeping that Bookmarks Sidebar open....

The Unsorted Bookmarks Folder extension is an alternative for those who dislike keeping the bookmarks sidebar open:

[https://addons.mozilla.org/en-US/firefox/addon/7269](https://addons.mozilla.org/en-US/firefox/addon/7269)

This very simple extension creates an entry under the Bookmarks menu entry. I use it constantly--especially for creating temporary bookmarks for Ubuntu forum threads.

---

### Post by Paddy Landau on 2008-09-08
> **heykev said:**
> I've never raised a bug report before.  What's the most useful (and socially acceptable) way to do that?

[LIST]
[*]Go to Launchpad's Ubuntu section: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)
[*]Select [Bugs]("https://bugs.launchpad.net/ubuntu").
[*]Search to check whether it's been reported before (I've searched and found nothing on this, but you may find one if you use different search terms).
[*]If you don't find a bug, select [Report a bug]("https://bugs.launchpad.net/ubuntu/+filebug"). (I think you need to create an account first.)
[*]Optional: Select [Advanced reporting options]("https://bugs.launchpad.net/ubuntu/+filebug-advanced").
[*]Fill in the details.
[/LIST]
If you do this, please post the link to the new bug here.

---

### Post by Bill_MI on 2008-09-26
Hi folks, It's been awhile so I went looking for status of this thing.  Such a basic function is taking a long time.  Take a look at the dates in the bug reports (it's a GNOME/Nautilus bug):

[https://bugs.launchpad.net/ubuntu/+bug/214170](https://bugs.launchpad.net/ubuntu/+bug/214170)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233913](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233913)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/214170](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/214170)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/240424](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/240424)

My post here was totally unanswered...
[http://ubuntuforums.org/showthread.php?t=770556](http://ubuntuforums.org/showthread.php?t=770556)

Glad to see I'm not the only one that considers it very very broken.  So much for quick fixes. :mad:

---

### Post by Paddy Landau on 2008-09-26
> **Bill_MI said:**
> It's been awhile ...  So much for quick fixes.
My guess is that this is considered a low priority. For a free product maintained partly by volunteers, I guess we can't complain.

Thanks for posting all those bug links; it helps to know about them.

---

### Post by Bill_MI on 2008-09-26
Hi, Paddy.  You're right of course.  What bugs me is that there wasn't more complaints.  Especially when messages in THIS forum are part of the problem.  Go figure. :confused:

I wonder if the forum admins could see how many error hits they get on:
[http://ubuntuforums.org/showthread.php](http://ubuntuforums.org/showthread.php)

...it would give an idea how widespread the problem is. :)

---

