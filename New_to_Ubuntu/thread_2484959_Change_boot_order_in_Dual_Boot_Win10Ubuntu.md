---
title: "Change boot order in Dual Boot Win10/Ubuntu"
date: 2023-03-15
forum: New to Ubuntu
---

### Post by lwalper on 2023-03-15
I know this is probably a common question, but I looked at several relevant threads and really didn't find anything that seemed to work. The GRUB menu in my dual boot Win10/Ubuntu system has the first boot OS listed as Ubuntu. Since I'm not 100% converted to that OS I 'd like to change that first boot order to the Win10 option. I ran
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
which echoed "UEFI mode."

I tried changing the UEFI boot order, which did work, but took away the GRUB menu -- so changed that back to Ubuntu as the first in the list (which restored the GRUB menu).

Isn't there file which can be edited to change that boot order? I looked at /boot/grub/grub.cfg which warned "don't edit this file." so I left it alone. I also looked in /usr/bin and found several grub*.* files that didn't look like anything I should mess with.

How do I change the boot order?

---

### Post by ajgreeny on 2023-03-15
Edit /etc/default/grub by changing line ***GRUB_DEFAULT=0*** to probably ***GRUB_DEFAULT=2***.

You will have to do this as root, best done with command ```
sudoedit /etc/default/grub
``` which will open the file with nano.  If you do not know nano you can now use ```
sudo -H gedit /etc/default/grub
``` with greater safety than used to be the case but I would advise you to learn nano via sudoedit for such system file edits.

All this assumes your grub menu normally shows Ubuntu at the top followed by Ubuntu recovery mode second, and then Windows 10 below those, but without seeing your grub menu it is not easy to be totally certain of the number needed.
Remember that for this purpose grub counts from zero, so the third entry in the menu is not 3 but 2

There is a very detailed thread at [https://ubuntuforums.org/showthread.php?t=1195275](https://ubuntuforums.org/showthread.php?t=1195275) which gives a lot of information which is mostly still current so have a look and bookmark that as it may help you a lot in future.

---

### Post by lwalper on 2023-03-15
OK, thanks. NANO is pretty neat!

Here are my boot options -
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291896&stc=1[/IMG]

By that I'm assuming that the Win10 option is #3 (entry #2 boots into recovery mode), so I edited the GRUB file to the following:
```
GRUB_DEFAULT=3
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
which still boots directly into Ubuntu.

And, whats the entry to enable seeing the timeout clock? I just like to watch stuff happen -- instead of hidden

---

### Post by tea for one on 2023-03-15
> **lwalper said:**
> which still boots directly into Ubuntu.
Did you run ```
sudo update-grub
```
> And, whats the entry to enable seeing the timeout clock? I just like to watch stuff happen -- instead of hidden
```
GRUB_TIMEOUT_STYLE=menu
```
Always run [COLOR="#0000FF"]sudo update-grub[/COLOR] so that the complete grub configuration is executed.

---

### Post by lwalper on 2023-03-15
Oops!! I failed to run ```
sudo update-grub
```
It seems that I read on the nano instructable that running that command was sort of pointless since OS updates may overwrite the file (or maybe it was the grub.cfg file??)

Anyhow, after running update-grub all seems to work as desired. Thanks again!

---

### Post by MAFoElffen on 2023-03-15
Updates do not overwrite the '/etc/default/grub file'. Those changes will persist after updates.

---

### Post by tea for one on 2023-03-15
> **lwalper said:**
> Anyhow, after running update-grub all seems to work as desired.
Splendid - that's good news.
In order to help other forum members/searchers, it is a nice gesture to mark the thread as solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ajgreeny on 2023-03-16
Yes, it's the ***grub.cfg*** file that is overwritten when grub is updated, and I think it says that at the top of the file (it's not a file I look at very often).

You may already have found this but to always show the timeout etc etc edit that **/etc/default/grub** file as follows, then again run command ***sudo update-grub***
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=2
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_DISTRIBUTOR="Xubuntu-22.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```
The line **GRUB_DISTRIBUTOR="Xubuntu-22.04"** is simply my way to show exactly what version of Ubuntu is being booted; Xubuntu is simply another Ubuntu to grub and I prefer to see what is really booting but you can ignore this if you are using Ubuntu. Anything between the quotation marks is what shows in the grub menu.

---

