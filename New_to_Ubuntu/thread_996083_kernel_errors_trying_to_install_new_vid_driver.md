---
title: "kernel errors trying to install new vid driver"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Spiffyguy on 2008-11-28
This seems to happen to me every time I upgrade versions of Ubuntu.  Main reason I don't use it all the time. I spend more time trying to get it to work that actually doing things on the computer.  going from gutsy to hardy I actually had to reinstall because I could not figure the problem out.  So please let me know what I need to do.

After the upgrade I get the bad vid driver going in to low graphic mode.  So I try to install new drivers.  EnvyNG tells me this via the GUI or command line.

EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed

Using synaptic it says I a have two options for restricted drivers, 173 or 177 which is recommended.  I click one and reboot.  same error about low graphics pops up, seems the request to use a driver is not sticking.  I try to install the .run file from nvidia via terminal and it starts crying about the wrong version of gcc that doesn't match my kernel because it is a new version.

So what the heck do i have to do to get a decent graphic driver?  in the mean time I will just boot into Vista and get work done.

Thanks

---

### Post by oldos2er on 2008-11-28
Go to System, Administration, Software Sources, and make sure the box next to "Source Code" is checked.

---

### Post by Spiffyguy on 2008-11-29
I just got a chance to look and the source code is UNchecked.  I do not have internet access for my laptop right now so I will fire it up in the morning and do an update with that checked.  Is this were kernel updates come from? 

Thanks for the help.

---

### Post by Spiffyguy on 2008-11-29
I made sure that was checked and ran my update again.  EnvyNG still gives an error about a kernel problem.  I have everything checked on the ubuntu tab of the software sources.  under ubuntu update I have security and recommended checked.  under release upgrade I have normal upgrades.  It seems if there is a mismatch on the kernel it is not getting the update.

Suggestions?

---

### Post by oldos2er on 2008-11-29
> **Spiffyguy said:**
> I made sure that was checked and ran my update again.  EnvyNG still gives an error about a kernel problem.  I have everything checked on the ubuntu tab of the software sources.  under ubuntu update I have security and recommended checked.  under release upgrade I have normal upgrades.  It seems if there is a mismatch on the kernel it is not getting the update.

Suggestions?

 I don't know much about EnvyNG, but have you tried going to System, Administration, Hardware Drivers, and enabling it from there?

---

### Post by Spiffyguy on 2008-11-29
yes I have.  there is the two entries, the 173 and the 177 drivers.  Either one is not selected.  So I select one and reboot.  Get a start up message about having to run in low graphic mode and such.  once i get back to the desktop i check the drivers on the restricted list they are unchecked again.  Last time I actually upgraded I looped this behavior numerous times until I gave up and just reinstalled Heron from disc.  But I have actually used the OS since that install and have data and software configured that I don't want to blow out.

---

### Post by Spiffyguy on 2008-12-02
any other suggestions on this problem?  Not sure what to do.  So reason I just can't get the drivers to install.

Thanks

---

