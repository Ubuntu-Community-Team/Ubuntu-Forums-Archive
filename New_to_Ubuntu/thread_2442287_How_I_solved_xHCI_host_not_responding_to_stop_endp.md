---
title: "How I solved xHCI host not responding to stop endpoint command"
date: 2020-05-01
forum: New to Ubuntu
---

### Post by bsmith52 on 2020-05-01
I did a new install on my new system (see below). I had not done much, except I installed libavcodec-extra, software updates, and driver updates. When I tried to insert a generic PCIe card to add 4 USB 3.0 ports (chipset VL805?), Ubuntu would not recognize my USB flash. I looked at output from dmesg and found this:

> [   39.338841] xhci_hcd 0000:04:00.0: xHCI host not responding to stop endpoint command.
[   39.354849] xhci_hcd 0000:04:00.0: Host halt failed, -110


I was unable to find a Debian based installation with the problem, though I did find a bug report and a similar problem with a Red Hat distribution. Stackoverflow was not optimistic.

Since about the only thing I did was install libavcodec-extra, I thought that I would uninstall it. Sure enough, my system is now working fine! The above error is no longer in dmesg.

Obviously, uninstalling an established software package is not a viable solution for most people. My intent here is for someone to pass this possible clue for the cause of the above problem to the Ubuntu software team and/or the Red Hat team.

I'll check this post in a day or so to see if any additional information is needed.

Cheers!

My system:
Asus TUF Gaming X570-plus MB
AMD 3700x CPU

---

### Post by bsmith52 on 2020-05-01
One more potentially important piece of info: Besides the usual software updates, I ran the following command to update drivers:

sudo ubuntu-drivers autoinstall

This is (I believe) the only thing that I did between the libavcodec-extra and the unsuccessful PCIe install (based on the history command).

---

### Post by yetimon_64 on 2020-05-01
> **bsmith52 said:**
> I did a new install on my new system (see below). ... My intent here is for someone to pass this possible clue for the cause of the above problem to the Ubuntu software team and/or the Red Hat team....
I am assuming you are using the latest stock ubuntu install and DE as you haven't noted the release you are on.

It would pay you to search on[ [COLOR=#0000ff]lauchpad.net[/COLOR]]("http://launchpad.net") for similar bug reports with libavcodec-extra and if none exist report the problem as you are the one noting it and it is showing up on your equipment (which may not necessarily be the case for all users of that package).

 I have linked to some information on bug reporting for you to look into ...
[[COLOR=#0000ff]https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en[/COLOR]]("https://help.ubuntu.com/stable/ubuntu-help/report-ubuntu-bug.html.en")

Regards, yeti.

---

