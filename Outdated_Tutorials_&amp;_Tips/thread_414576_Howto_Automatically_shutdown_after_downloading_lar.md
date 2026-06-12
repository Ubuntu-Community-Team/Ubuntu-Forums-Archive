---
title: "Howto: Automatically shutdown after downloading large files (ex fiesty iso)"
date: 2007-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by taipoh on 2007-04-20
Simple and hopefully helpful:

Open up a text editor.

Copy and paste this into it:
> sudo -s; wget [http://www.theaddress.com/fiesty.iso](http://www.theaddress.com/fiesty.iso); shutdown -h +1

Replace "http://www.theaddress.com/fiesty.iso" with your file's URL:

Then copy and paste into the console and you're set.

This will shutdown your box 1 minute after the file download completes.  Useful for downloading large files while you sleep :).


TOO CANCEL A SHUTDOWN:
Open a console and run
> sudo shutdown -c

---

