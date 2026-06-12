---
title: "deleting new problem kernel"
date: 2018-07-03
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-07-03
is it advisable to delete the new problem kernel?  if good idea - how does one do it?  it seems i have to go into grub menu advanced settings at startup each time to pick the older kernel.  thought this might be away to not have to do this or hold the shift key down all the time too

---

### Post by bodhin2 on 2018-07-03
i found this:

**.deb based distro &#8211; Debian or Ubuntu Linux**

Again find out all installed kernel version:
$ dpkg --list | grep kernel-image
Output:
ii  kernel-image-2.4.27-2-386   2.4.27-10sarge1             Linux kernel image for version 2.4.27 on 386
ii  kernel-image-2.6.8-2-686    2.6.8-16sarge1              Linux kernel image for version 2.6.8 on PPro
Now remove kernel-image-2.4.27-2-386 with apt-get command itself:
# apt-get remove kernel-image-2.4.27-2-386
OR
$ sudo apt-get remove kernel-image-2.4.27-2-386
If you have custom compiled kernel you need to remove following files/dirs:

[LIST]
[*]/boot/vmlinuz*KERNEL-VERSION*
[*]/boot/initrd*KERNEL-VERSION*
[*]/boot/System-map*KERNEL-VERSION*
[*]/boot/config-*KERNEL-VERSION*
[*]/lib/modules/*KERNEL-VERSION*/
[*]Update grub configuration file /etc/grub.conf or /boot/grub/menu.lst to point to correct kernel version.
[/LIST]
[COLOR=#FF0000]Caution:[/COLOR] Removing working kernel may result into unstable / non- bootable Linux server system.


sound legit????



p.s. there is a new kernel and a recovery mode one and an older version and a recovery mode one.  so what would you do with the recovery mode new one?  if this is at all possible.

---

### Post by mc4man on 2018-07-03
What is the 'problem' kernel version?
As far as that command you're asking about, probably would return nothing.

---

### Post by bodhin2 on 2018-07-03
that was the example used on the internet - i would have to plug int thecorrect info.

i believe it was 4.25 or some such thing - the older one is 4.20

sorry - thought it was obvious i copied from an article on the internet - it was just an example.

---

### Post by Dennis N on 2018-07-03
If you have a problem with the newest kernel, you can set up the previous one as default. Then you don't have to select it from grub menu each time. Study the answer to this askubuntu question:
[https://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry](https://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry)
OR study this method using number references:
[https://www.calazan.com/how-to-set-an-older-kernel-version-as-the-default-in-grub-during-bootup-ubuntu-12-04/](https://www.calazan.com/how-to-set-an-older-kernel-version-as-the-default-in-grub-during-bootup-ubuntu-12-04/)
I hope these help!

---

### Post by mc4man on 2018-07-03
> **bodhin2 said:**
> that was the example used on the internet - i would have to plug int thecorrect info.

i believe it was 4.25 or some such thing - the older one is 4.20

sorry - thought it was obvious i copied from an article on the internet - it was just an example.
I understood it was an example, what I was saying was the command is useless in Ubuntu, likely won't return any info.

---

### Post by bodhin2 on 2018-07-03
OK thanks to both of you.

i do not think i could do all of that without messing stuff up so i will have to wait until ubuntu fixes this or install another distro that may have this kernel bug fixed.  i was very happy until this happened.  oh well.  i will wait and see.

---

### Post by tea for one on 2018-07-04
Do you have kernel 4.15.0-23 installed?

If you can boot into that kernel, then open up synaptic and search for 4.15.0-24 and remove it together with the linked packages.

If I remember correctly, there were 8 packages approx 335MB in total.

Kernel -24 gave me a long boot time so I removed it via synaptic and am currently a happy user of 4.15.0-23.

After removing the kernel, i also ran

```
sudo update-grub
```

---

### Post by Impavidus on 2018-07-04
As tea for one says, you can remove 4.15.0-24 and fall back to 4.15.0-23 or 4.15.0-20 or whatever version you have installed. This will force the removal of some metapackages that are used to pull in the latest kernels and associated packages, so to get automatic kernel upgrades again in the future you'll have to reinstall those metapackages when a fixed kernel is available.

Kernel 4.15.0-25 is already in proposed. You could enable the proposed repository (software sources->developer options->enable the bionic-proposed repository) and update the kernel packages. That should install 4.15.0-25, which may (or may not) fix your problem. I suggest you only update those packages and not all the other stuff in proposed and then disable proposed again, or you'll end up with a lot of experimental stuff.

You don't really have to run sudo update-grub manually. It's run automatically as part of every kernel installation or removal through the package manager. But it won't harm either.

---

### Post by bodhin2 on 2018-07-04
Thanks but after a day of trying and panic - because i hate when my systems are broken and generally are not - i am living with it until they fix it.  it shouldn't be this way in this day and age not ubuntu arty ardvark 1.1.1  heh heh heh

---

### Post by monkeybrain20122 on 2018-07-04
> **Impavidus said:**
> 
Kernel 4.15.0-25 is already in proposed. You could enable the proposed repository (software sources->developer options->enable the bionic-proposed repository) and update the kernel packages. That should install 4.15.0-25, which may (or may not) fix your problem. I suggest you only update those packages and not all the other stuff in proposed and then disable proposed again, or you'll end up with a lot of experimental stuff.

You don't really have to run sudo update-grub manually. It's run automatically as part of every kernel installation or removal through the package manager. But it won't harm either.

I don't think it is a good idea to enable proposed as it might mess up your dependencies beyond repair if you are not careful. Also i think 4.15.0-25 is also bad (haven't tried it, but have tried 4.16.18 from mainline and 4.17.4 self compiled, all bad. Might be[ this bug]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897572"))

---

### Post by oldos2er on 2018-07-05
> **bodhin2 said:**
> i do not think i could do all of that without messing stuff up

There is a GUI grub editor available called grub-customizer, see [https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/ubuntu/grub-customizer)
It's basically point and click.

I wonder what internet cellar you were digging in to find a kernel 2.4 command?   :) At any rate you can use *apt* in place of *apt-get* these days. And as a general rule, you want to check the date, distro, and version of any info you're searching for/ Things change rapidly in the open source world.

---

### Post by bodhin2 on 2018-07-05
thanks - i did a search.  came up maybe #2 or 3 on the search.  yes i realize that the relevant version is important - just a starting point for info.  Monkeybrains actually helped me out this AM so that there is no need to try to delete kernels etc.  I am most thankful to him and whoever else it was that came up with the fix/workaround for the issue.

---

### Post by monkeybrain20122 on 2018-07-05
Your life would be a lot easier if you install the synaptic package manager. 

```
sudo apt install synaptic
```

You can then search for linux-image and linux-headers and see what is installed and what is available at a glance. To remove is just right click and choose remove then apply. Don't need to update grub as that would be taken care of too.

The problem I had as a beginner with this apt apt-get gibberish is that I didn't know the exact names of the packages and versions I wanted to install or remove, old posts and tutorials I dug up from the forums or the internet usually didn't work (because of version change) There are ways to find out with the command line but why do it the hard way? Not everyone has good memory for obscure syntax.

---

### Post by bodhin2 on 2018-07-05
synaptic was one of the first i installed.  

can you explain this a bit more - not sure i follow!

---

### Post by monkeybrain20122 on 2018-07-05
> **bodhin2 said:**
> synaptic was one of the first i installed.  

can you explain this a bit more - not sure i follow!

Tea for one and mc4man (screenshot) described it here [https://ubuntuforums.org/showthread.php?t=2395529](https://ubuntuforums.org/showthread.php?t=2395529), remember? :)

---

### Post by bodhin2 on 2018-07-05
ok - man there were too many threads to follow i forget about it or did not see the response.  old age...

---

