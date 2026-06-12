---
title: "frustrated with the Ubuntu 11 series- 11.4 + 11.10"
date: 2011-10-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by SE7EN-LOCSTA on 2011-10-04
the issue: backlight

I have a laptop (aspire 5734z) and it has had an issue that was reported in the 11.04 beta testing but never fixed. it is still an issue in the 11.10 beta, leaving alot of people such as myself unable to use my laptop as a portable machine (cant close the lid and suspend/hibernate and reopen at a later time). this is not specific to this model, or even brand of laptops.
 It is almost certainly a kernel issue, as it affects unity, gnome 3, and kubuntu.. perhaps others too. the only solution i have been able to use is to set acpi_os=linux for boot, otherwise you can't see to install or boot up. this leaves the brightness controls unusable, giving either all or nothing, and if it goes to nothing by way of screen dim (which in 11.10 now happens after an hour [the setting says an hour, but it usually dims after ~5-10 minutes], as setting it to 'never' dim makes it instantly dim), suspend, or hibernate.. the screen brightness will not return without a reboot. 

 i wish they would make a definite, feasible fix for this, as it is annoying to be forced to reboot if i don't press a button for 5 minutes.

---

### Post by madjr on 2011-10-04
yes, its a pain.

is there any bug report open for this?

---

### Post by SE7EN-LOCSTA on 2011-10-04
i am not really sure. i don't know where all the bug reports even go. i only know they had it all the way back to 11.04's beta testing-- i stumbled on it when trying to fix the backlight issue when natty first came out.

---

### Post by cariboo on 2011-10-04
All Ubuntu bugs are reported on [https://bugs.launchpad.net](https://bugs.launchpad.net), you need to create an account to report bugs.

---

### Post by madjr on 2011-10-05
yea, its pretty easy to report and follow up on bugs (and some feature requests) for ubuntu:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[http://www.ubuntu.com/community/report-problem](http://www.ubuntu.com/community/report-problem)

---

### Post by SE7EN-LOCSTA on 2011-10-06
sorry took so long to respond, i have been busy with downgrading back to 10.10.

there is open bug reports of this, and as far as i can tell, it is under 'status: confirmed' back to 11.04. 

some people have had luck with boot commands such as acpi_backlight=vendor, but i have not.

---

### Post by proxy.qtz on 2011-10-06
Have you tried this with Gnome Shell or KDE?

---

### Post by nrundy on 2011-10-06
@[SE7EN-LOCSTA]("http://ubuntuforums.org/member.php?u=1248759")

This happens when you just close the lid?

Can't you use an FN keyboard shortcut to suspend and then close the lid? Does this fix the problem?

---

### Post by SE7EN-LOCSTA on 2011-10-06
the problem does exist in gnome3 shell, tested on ubuntu11.04 and 11.10. it also happens in kde, tested on backtrack 5 and 5r1 kde. 

as far as closing/not closing the lid... it matters not. if the light goes out at all (suspend, hibernate, timed dim) it will not come back on.

---

