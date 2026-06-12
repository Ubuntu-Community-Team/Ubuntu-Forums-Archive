---
title: "Ubuntu in Virtual Box on OSX"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Xarok on 2008-08-09
I have some questions about running Ubuntu 8.4 in Virtual Box 1.6.2 on OSX 10.5.

- How can I easily transfer files to and from Ubuntu and OSX?

- With a normal live CD Boot on the computer the special effects seem to work fine, but do not in Vitual Box. Any idea why?

- The internet was working previously, but doesn't seem to be any more. Any ideas why?

Much thanks all. :)

---

### Post by SlalomMan on 2008-08-10
> **Xarok said:**
> I have some questions about running Ubuntu 8.4 in Virtual Box 1.6.2 on OSX 10.5.

- How can I easily transfer files to and from Ubuntu and OSX?

- With a normal live CD Boot on the computer the special effects seem to work fine, but do not in Vitual Box. Any idea why?

- The internet was working previously, but doesn't seem to be any more. Any ideas why?

Much thanks all. :)

I'm no pro with OSX but I have used VirtualBox a bit, mostly to emulate Windows under Ubuntu. But here's what I think.

Transfer files: In Ubuntu, VirtualBox has a menu where you can specify folders that appear as "network folder" in XP. I'm assuming you can do the same with OSX-Ubuntu. It's under the Devices menu, called "Shared Folders." They may or may not appear in Ubuntu automatically, I had to do some configuring to make them work in XP. Hope that helps.

Special Effects: VirtualBox has a few limitations, and graphics is one of them. For instance, the Zune software runs fine on my XP partition but in the XP virtual machine, it has to run in low graphics mode. This is also why you can't play games in VirtualBox, or at least 3d-heavy ones.

Network: I've never had trouble with this; you may have to "bridge connections." Again, I don't have OSX experience, so you should probably either google around a bit or ask on an OSX forum; I'm sure someone here will be able to help though.

Hope this helps you.

---

### Post by DGortze380 on 2008-08-10
> **Xarok said:**
> I have some questions about running Ubuntu 8.4 in Virtual Box 1.6.2 on OSX 10.5.

- How can I easily transfer files to and from Ubuntu and OSX?

- With a normal live CD Boot on the computer the special effects seem to work fine, but do not in Vitual Box. Any idea why?

- The internet was working previously, but doesn't seem to be any more. Any ideas why?

Much thanks all. :)

- There are a number of tutorials on this, a quick google search will yield tens of results. Haven't tackled this myself yet.

- Not surprising as virtual machines tend not to support 3d graphics very well.

- Need more info. Internet on the VM? Just choose NAT connection from the settings menu in virtual box. Should work by default in OS X.

---

