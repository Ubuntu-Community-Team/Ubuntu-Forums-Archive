---
title: "Which OS to use?"
date: 2014-07-26
forum: Recurring Discussions
---

### Post by dchurch24 on 2014-07-26
Hi all,

Since Ubuntu went with that awful Unity interface I have been unable to use it, so stuck with 10.10 for a very long time.
Now I need certain libraries etc... that I can no longer get.

I have a laptop with Windows 8.1 on it, and that is virtually unusable, so went to install Mint - tried it on two laptops and it seems that the installer is broken.

Can someone recommend a distro that preferably has APT that works and has a window manager that is usable for someone over the age of 10?

---

### Post by sudodus on 2014-07-26
I suggest that you try Xubuntu and Kubuntu in that computer with Windows 8.1. Read up about [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295").

If you have an old computer (which I guess, because of Ubuntu 10.10), I suggest that you try Lubuntu and Xubuntu in that computer.

Start trying the version 14.04.1 LTS in the new computer and 12.04 LTS in the old one.

But before installing anything, please [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by TheFu on 2014-07-26
Ubuntu 14.04 Server + XFCE4 or LXDE or Cinnamon or .... about 20 other choices.  You can use a pure WM solution too.

Even if you provided the specific libraries and versions, those are almost certainly out-of-date.

10.10 has been unsupported since 2011 - don't care much about security, do you?

Stay LTS (14.04, 12.04) and you'll be have 4.5+ yrs of support - plenty of time to migrate to the next LTS release when it is available and mature.

Since you are asking this question on an Ubuntu forum, you shouldn't be surprised at the answer.

---

### Post by craig10x on 2014-07-26
There is nothing horrible or unusable about unity, it's really just a dock...so i would gather you can't stand to use anything with a dock (i guess you aren't very fond of apple computers for that reason too...lol)
So, as they suggested, try xubuntu or kubuntu 14.04 LTS...either one would probably be more suited to you...

I never found ubuntu's old interface to be very efficient or productive, with it's 2 (space wasting) panels and fan out apps menu, but to each his own ;)

---

### Post by dchurch24 on 2014-07-26
You assume correctly :p I don't much care for Apple OS either.

I have Xubuntu coming down as we speak. Looking at the screenshots, it looks a lot like something I could get on with.

Thanks guys.

---

### Post by TheFu on 2014-07-26
> **dchurch24 said:**
> You assume correctly :p I don't much care for Apple OS either.

+1 - I tried it for a few weeks. HATED IT!  Felt like "linux-lite" plus at the time even CIFS connections were broken.

There is no need to get a special release (Lubuntu/Kubuntu/Xubuntu) to try different GUIs. 
[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/) explains.

The horrible thing about Unity is the requirement for 3D capable GPUs.  That isn't good for VM desktops or remote desktops.

---

### Post by dchurch24 on 2014-07-26
Yeah. I thought the same.

Sadly....The Xubuntu installer crashes like the Mint one. I don't think I am going to be able to actually have a computer that actually does anything useful.

Well, that completely shagged my install of 10.10.

The home folder is now missing, and I can only boot into something called "initramfs".

---

### Post by sudodus on 2014-07-26
Is Xubuntu running live? If not, try some boot options according to this link. With nvidia graphics I would recommend **nomodeset** at least until you install a proprietary driver.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by dchurch24 on 2014-07-26
It doesn't get that far sadly.

It starts the Xubuntu screen, then goes black. If I press F1-6, I can see the terminal and a message flashing past saying "No space left on device" - which is odd.

---

### Post by sudodus on 2014-07-26
If you are trying Xubuntu 14.04 LTS, download and try 12.04 LTS and vice versa. The hardware drivers are different, and it is worth trying the other version as well. Xubuntu 12.04 LTS is only supported until April 2015, but at least you might get going and can find alternatives in the meantime.

Other alternatives are community re-spins based on Ubuntu 12.04 LTS, Bento, Bodhi, LXLE, that all promise support until April 2017 (as does standard Ubuntu).

---

### Post by pfeiffep on 2014-07-26
Possibly consider Ubuntu 14.04 and install gnome-flashback. I've installed that on both machines and it suits me just fine:p

---

### Post by sudodus on 2014-07-26
> **dchurch24 said:**
> It doesn't get that far sadly.

It starts the Xubuntu screen, then goes black. If I press F1-6, I can see the terminal and a message flashing past saying "No space left on device" - which is odd.


Did you check with md5sum that the download was good?

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by dchurch24 on 2014-07-26
I did, and it was fine.

I'm more concerned with the message about the "no space on device" - I seem to remember getting a similar message with the Mint install.

---

### Post by Bucky Ball on 2014-07-26
*Thread moved to **Recurring Discussions**.*

Perhaps download a few and see what fits your needs. All the Ubuntu flavours can be run from the LiveUSB/DVD. Good luck. ;)

---

### Post by sudodus on 2014-07-26
Did you notice my suggestions in post #10? It is worthwhile trying both of 12.04 LTS and 14.04 LTS, and also some community re-spins of 12.04 LTS

---

### Post by dchurch24 on 2014-07-26
> **sudodus said:**
> Did you notice my suggestions in post #10? It is worthwhile trying both of 12.04 LTS and 14.04 LTS, and also some community re-spins of 12.04 LTS

Will do. Cheers.

---

### Post by crl2 on 2014-07-27
> **sudodus said:**
> 

...If you have an old computer (which I guess, because of Ubuntu 10.10), I suggest that you try Lubuntu and Xubuntu in that computer.

Start trying the version 14.04.1 LTS in the new computer and 12.04 LTS in the old one...



I've rescued a few XP machines belonging to friends with Lubuntu 13.10 and 14.04. Ok with Pentium IV, too slow with Pentium III. My friends are not rich but happy.

It's easy enough to download things like LibreOffice from the repository.

Some people insist on Adobe Reader which needs a little bit of geek skill, though help is readily available. Installing an HP printer (can't remember which model) involved jumping through a few fiery hoops. Printers that are too old may not be supported (Samsung CLP-300N for example).

My own difficulties with Linux distros are related to software that only runs on Windows.  I have some ancient scientific applications, but the real show-stopper is MidiOx (music) which has nothing remotely equivalent under Linux. I'm sure lots of other people stay with their OS for reasons like that. MidiOx is a widely used commercial application that's been free and crapware-free for home use for more years than I can remember. Apart from the OS compatibility issue there would be no good reason to try to compete with it.

---

