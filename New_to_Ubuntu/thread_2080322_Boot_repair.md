---
title: "Boot repair"
date: 2012-11-03
forum: New to Ubuntu
---

### Post by Tomelirolla on 2012-11-03
I was trying to run a boot-repair coz im having trouble installing updates. I am trying to install it from a Ubuntu live-usb as seen in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Everything goes ok till I type ```
sudo apt-get install -y boot-repair
``` When I do it i get a load of msgs such as this: ```
libutouch-frame1 : Depends: libc6 (>= 2.7) but it is not going to be installed
``` and in the end ```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` Then I try typing 'apt-get -f install' and I get ```
A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libc-2.15.so.dpkg-tmp'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
That pretty much it. I don't know if what im doing will solve the problem or if I posted to much info coz i'm a utter newbie.

---

### Post by newb85 on 2012-11-03
Welcome to the forums.

Boot Repair isn't in the main repositories (although I've heard there are plans to include it in future releases).

You can add Yann's Boot Repair PPA with the following command. (Yann is Boot Repair's developer.)
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
```

Then you should be able to install boot-repair.

[s]Note: if you're using 12.10, it's been changed to apt-add-repository instead of add-apt-repository.[/s]
*Apparently, this was only the case for beta versions.*

---

### Post by Tomelirolla on 2012-11-03
And how can I run the boot repair?

---

### Post by newb85 on 2012-11-03
Pull it up from the Dash.

---

### Post by Tomelirolla on 2012-11-03
It's not showing the boot-repair, just the iso used to make the live-usb

---

### Post by critin on 2012-11-03
> **Tomelirolla said:**
> It's not showing the boot-repair, just the iso used to make the live-usb

I don't see where you ran both of these codes completely in post #1.  In the link you used, did you enter both codes?  Add repository, update repository, install boot repair.  Copy and pasting the codes is always best.  They must be absolutely correct or won't work.  Spaces & all.

```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by Tomelirolla on 2012-11-03
The codes are correct. Everything goes alright till ```
sudo apt-get install -y boot-repair && boot-repair
``` when I get ```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
``` When I try ```
sudo apt-get -f install
``` I get ```
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...

A copy of the C library was found in an unexpected directory:
  '/lib/x86_64-linux-gnu/libc-2.15.so.dpkg-tmp'
It is not safe to upgrade the C library in this situation;
please remove that copy of the C library or get it out of
'/lib/x86_64-linux-gnu' and try again.

dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Dreamer Fithp Apprentice on 2012-11-04
I may misunderstand what you are doing and trying to do. If so, just ignore this. It sounds like you have a non bootable partition on a hard disk and you are trying to repair it by installing boot repair on the virtual file system of a live disk.

If that is correct, you might want to try a different approach: Burn a Rescuatux CD. If you have a CD burner and an additional CD drive you should be able to do this while booted from some live disk. Otherwise you'll want to do it on another machine. If no other machine and no second CD drive are available you can actually boot from the iso but you'll have to edit grub from the live disk and that gets pretty hairy. Rescuatux can serve as a kind of external boot loader and let you boot your normal HD bootable partition. Once you get it booted, install boot repair THERE, in the normal HD system. Do not reboot or you are likely to need Rescuatux again if you do. NOW run boot repair from the normal system. This has worked for me several times.

To summarize:
Rescuatux to get the HD based system booted.
Install boot repair on the now running HD based system.
Run boot repair before rebooting to actually fix the problem so you won't need to boot via Rescuatux.

Good luck.

P.S. added by editing: You can probably use a usb thumb drive instead of a second CD drive but I haven't tried that.

---

### Post by Tomelirolla on 2012-11-04
> If that is correct, you might want to try a different approach: Burn a Rescuatux CD. If you have a CD burner and an additional CD drive you should be able to do this while booted from some live disk. Otherwise you'll want to do it on another machine. If no other machine and no second CD drive are available you can actually boot from the iso but you'll have to edit grub from the live disk and that gets pretty hairy. Rescuatux can serve as a kind of external boot loader and let you boot your normal HD bootable partition. Once you get it booted, install boot repair THERE, in the normal HD system. Do not reboot or you are likely to need Rescuatux again if you do. NOW run boot repair from the normal system. This has worked for me several times.

To summarize:
Rescuatux to get the HD based system booted.
Install boot repair on the now running HD based system.
Run boot repair before rebooting to actually fix the problem so you won't need to boot via Rescuatux.
Sorry but I don't know what's a Rescuatux and I couldn't find on google. Anyway, I found this thread ([http://ubuntuforums.org/showthread.php?t=2075635&highlight=libc6](http://ubuntuforums.org/showthread.php?t=2075635&highlight=libc6)) and I think it's pretty much the same problem and that boot-repair won't be able to fix it.

---

### Post by newb85 on 2012-11-04
> **Tomelirolla said:**
> It's not showing the boot-repair, just the iso used to make the live-usb

You're saying that if you pull up the Dash and start typing Boot Repair, the program doesn't show up, but your .iso file does?  The .iso file shouldn't be available in a Live session, unless you've mounted the HDD where it's stored.

---

### Post by Dreamer Fithp Apprentice on 2012-11-04
> **Tomelirolla said:**
> Sorry but I don't know what's a Rescuatux and I couldn't find on google. Anyway, I found this thread ([http://ubuntuforums.org/showthread.php?t=2075635&highlight=libc6](http://ubuntuforums.org/showthread.php?t=2075635&highlight=libc6)) and I think it's pretty much the same problem and that boot-repair won't be able to fix it.
Google saith:

Did you mean: [rescatux]("http://www.google.com/search?hl=en&client=ubuntu&hs=F9U&channel=fs&biw=928&bih=419&spell=1&q=rescatux&sa=X&ei=ifOWUJTjBeOq2gXrtYGgAg&sqi=2&ved=0CBsQBSgA")?

Yeah, that's what I meant. Darn robot spells better than I do.

[http://www.supergrubdisk.org/rescatux/](http://www.supergrubdisk.org/rescatux/)

---

### Post by Tomelirolla on 2012-11-04
Thanks!
:)
I won't be able to do it today but when I manage to run Ill post the results

---

