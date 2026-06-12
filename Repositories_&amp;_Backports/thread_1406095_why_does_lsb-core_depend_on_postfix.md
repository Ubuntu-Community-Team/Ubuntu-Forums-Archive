---
title: "why does lsb-core depend on postfix?"
date: 2010-02-13
forum: Repositories &amp; Backports
---

### Post by felixnine on 2010-02-13
karmic, up-to-date.

kernel: 2.6.31-20
lsb-core: 4.0-0ubuntu5
postfix: 2.6.5-3

i mean, why is it required that i have postfix on my laptop? am i missing something?

```
andrew@octagon >> sudo aptitude purge postfix                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  bsd-mailx lsb-core 
The following packages will be REMOVED:
  postfix{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3,248kB will be freed.
The following packages have unmet dependencies:
  bsd-mailx: Depends: postfix but it is not installable or
                      mail-transport-agent which is a virtual package.
  lsb-core: Depends: postfix but it is not installable or
                     mail-transport-agent which is a virtual package.
```

---

### Post by miklcct on 2010-02-14
Mail functionality is required in LSB?

---

### Post by felixnine on 2010-02-14
well, sure, but an email server? considering pretty much everything depends on lsb-core, i find this odd. 

when i try to purge postfix, aptitude's available solutions include installing either nbsmtp or ssmtp. i feel like this is new because i have never explicitly installed postfix.

---

### Post by Zyonin on 2010-02-18
Hmm, I wondering the same thing myself.   Update Manager popped up this morning with it's usual weekly updates.   I told it to do its thing.   Sometime during the installation,  I get this box for setting up "Postfix".   As I did not know what Postfix was. I pushed the cancel button.   Then Update Manager coughed up an error related to lsb-core.   

Since my machine is a home machine AND I use web based mail, I have never installed any type of mail server as that is a waste of disc space (for me) and a potential security headache (since I don't know anything about running a mail server).      For the time being, I have I have allowed Postfix to install with "No Configuration" however if this can get cleared up (aka lsb-core not being dependent on Postfix) then I can remove Postfix in the future.

The only reason why lsb-core was being installed in the first place is the current Chrome-beta seems to rely on it now (which it did not or was not noticed by me previously)

Thus the question, why does lsb-core depend on postfix?   I have no need for a mail server of any kind as this is a home PC.

---

### Post by Bachstelze on 2010-02-18
> **Zyonin said:**
> 
Thus the question, why does lsb-core depend on postfix?   I have no need for a mail server of any kind as this is a home PC.

miklcct already answered this. The LSB specifications require the [font=monospace]sendmail[/font] commant to be present, and Postfix is the default package that provides it in Ubuntu.

If Postfix is too heavy for your liking, you can install ssmtp instead, which also provides the [font=monospace]sendmail[/font] command, and is much lighter.

---

### Post by felixnine on 2010-02-18
> **Bachstelze said:**
> miklcct already answered this. The LSB specifications require the [font=monospace]sendmail[/font] commant to be present, and Postfix is the default package that provides it in Ubuntu.

If Postfix is too heavy for your liking, you can install ssmtp instead, which also provides the [font=monospace]sendmail[/font] command, and is much lighter.

ok, this makes sense. but what changed?

---

### Post by Bachstelze on 2010-02-18
> **felixnine said:**
> ok, this makes sense. but what changed?

Nothing changed. lsb-core has always depended on Postfix (or some other MTA) [ever since Dapper](http://packages.ubuntu.com/dapper/lsb-core).

---

### Post by felixnine on 2010-02-18
well **** on my dick. i just find it odd that a few days ago i got a postfix configuration screen for the first time (i think).

thanks for the info.

---

### Post by Bachstelze on 2010-02-18
You probably installed a package that depended on lsb-core, which in turn pulled Postfix in. You could try removing lsb-core, and see what other packages Apt wants to remove.

---

