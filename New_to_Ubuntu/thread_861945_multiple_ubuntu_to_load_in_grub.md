---
title: "multiple ubuntu to load in grub"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by catroaring on 2008-07-17
8.04

i get about 10+ ubuntu options.  is this normal?

chad

---

### Post by mcduck on 2008-07-17
It's normal. When you get a kernel update the old kernel won't be removed. This allows you to saaly test the new kernel, and if it causes troubles just selet the old one from Grub menu and still have a working system.

When you are sure the latest kernel is working fine you can just uninstall the old one(s) with Synaptic. This will also automatically remove the entry from Grub menu.

---

### Post by iaculallad on 2008-07-17
> **catroaring said:**
> 8.04

i get about 10+ ubuntu options.  is this normal?

chad

Yes, that's just normal. Ubuntu updates your GRUB menu file whenever new Kernels are downloaded and installed to you system.
You still could trim down the list by uninstalling OLD kernel files using your Synaptics w/c will in return re-update your GRUB menu file.

---

### Post by catroaring on 2008-07-17
how do i unistall the old Synaptic?

---

### Post by iaculallad on 2008-07-17
> **catroaring said:**
> how do i unistall the old Synaptic?

Open you Synaptics: System->Administration->Synaptics Package Manager, click on "Search". Input "linux-image" (w/o quotes) as search string. Kernel files will be displayed, right-click on an OLD kernel and select "Mark for Complete Removal". Do the same process to other OLD kernels. Once finish marking for complete removal, Click on Apply.

NOTE: It's best to keep at least 1 OLD kernel just in case.

---

### Post by catroaring on 2008-07-17
2.6.64.19

i should keep?

---

### Post by kansasnoob on 2008-07-17
Just go to synaptic and install

> startupmanager

then go to System > Administration > StartUp-Manager and you'll see this:

[ATTACH]78006[/ATTACH]

then click on the Advanced tab and you'll see this:

[ATTACH]78007[/ATTACH]

Where you see Number of Kernels to keep make it 1 or 2 or 3, whatever!

I prefer 2 because if a Kernel update breaks something I can still choose to boot the previous Kernel until I get the issue figured out.

But it does not REMOVE any previous Kernels, they're still there if you ever need them.

---

### Post by mcduck on 2008-07-17
> **kansasnoob said:**
> Just go to synaptic and install



then go to System > Administration > StartUp-Manager and you'll see this:

[ATTACH]78006[/ATTACH]

then click on the Advanced tab and you'll see this:

[ATTACH]78007[/ATTACH]

Where you see Number of Kernels to keep make it 1 or 2 or 3, whatever!

I prefer 2 because if a Kernel update breaks something I can still choose to boot the previous Kernel until I get the issue figured out.

But it does not REMOVE any previous Kernels, they're still there if you ever need them.

They are still there, wasting the disk space, and accessing them is rather hard for beginners as you'd need to edit the boot options directly from Grub's command line. Rather useless, in my opinion, as I've never even heard of a working kernel suddenly breaking.

Just keep one old kernel fo a while, and remove eveything else.

Actually I don't even keep the one older kernel for more than a day or two. If the new kernel works fine, it works fine and that's not going to change.

Oh course if you have massive amounts of extra disk space you have no better use for you can keep as many outdated kernels as you wish, it's just that they are hardly useful for anything and after removing them from the menu rather hard to use as well..

---

