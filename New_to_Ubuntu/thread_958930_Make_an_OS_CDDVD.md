---
title: "Make an OS CD/DVD"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by emylfischer on 2008-10-25
Hi,

I have been using ubuntu for a couple of months now and I am happy with it. Now I have a small problem with my windowsXP and I may have to reinstall it. But doing that will completely remove ubuntu and I don't want to spend time installing all the addons that I installed on ubuntu already. Is there a way to completely write all my ubuntu OS onto a CD or DVD and directly install it all at one shot after I reinstall the windows?

---

### Post by Helios1276 on 2008-10-25
There are programs like Remastersys that can do it but they are pretty hit and miss , from what I've read. Tried once and failed, might give it a go again soon. Search the forums , I'm sure there is a good thread on it .

---

### Post by Girya on 2008-10-25
> **emylfischer said:**
> Hi,

I have been using ubuntu for a couple of months now and I am happy with it. Now I have a small problem with my windowsXP and I may have to reinstall it. But doing that will completely remove ubuntu and I don't want to spend time installing all the addons that I installed on ubuntu already. Is there a way to completely write all my ubuntu OS onto a CD or DVD and directly install it all at one shot after I reinstall the windows?

partimage will do the trick. Here is a link to a live cd with partimage on it. [http://http://www.sysresccd.org/Main_Page]("http://http://www.sysresccd.org/Main_Page")

---

### Post by bumanie on 2008-10-25
Unless you have a wubi install, reinstalling windows should not wipe ubuntu. You will have to reinstall grub after the windows installation, but that is not too hard. If you do have a wubi install there is a way to copy ubuntu off windows onto its own partition. Please post the output of > sudo fdisk -luthis way we can ascertain how your present installation is setup.

---

