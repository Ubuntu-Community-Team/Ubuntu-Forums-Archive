---
title: "Software Center - unmet dependencies"
date: 2013-08-30
forum: New to Ubuntu
---

### Post by charl2 on 2013-08-30
Hi, I have recently installed ubuntu 13.04. 

In my first couple of minutes I decided to check the Software Center just to see what applications were available.  It seemed to work fine, and if I wanted to, it seemed that I could install anything. But, ubuntu then prompted me to download an update(god knows what it was for), of aproximately 200mb. I automatically accepted, but after realising it was downloading at around 5B/s, I just cancelled the download.

Now, here my problem started. When I ran the Software Center, it would open as usual, but would not load or display any apps. The window would only display this:

[IMG]http://i.imgur.com/3pA30LO.png[/IMG]

Now, when I close this window, I get an error message on the top right corner:

[IMG]http://i.imgur.com/0rArc6F.png[/IMG]

Is there anything I can do to get my software center working again?

PS. I have been looking for a solution for 3 hours. And sorry for my bad english.

---

### Post by bkline on 2013-08-30
Perhaps your selected repository is having problems.  Try opening Ubuntu Software Center again; from the Edit menu choose "Software Sources...."  In the dialog pane which appears select the "Ubuntu Software" tab.  From the "Download from" dropdown list choose "Other" and when the new dialog box appears click "Select Best Server."  The software will test to see which of the available sources gives you the best performance.

Good luck.

---

### Post by charl2 on 2013-08-30
When I click on "Software Sources...", this happens:

"Failed to load the package list"
details:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/za.archive.ubuntu.com_ubuntu_dists_raring-security_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.

---

