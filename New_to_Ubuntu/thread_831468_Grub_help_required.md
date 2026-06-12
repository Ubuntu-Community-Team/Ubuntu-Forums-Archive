---
title: "Grub help required"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by TMcMahon51 on 2008-06-16
I'm usually pretty decent when it comes to computers, but I only just recently got into dual booting Ubuntu, instead of just XP. My problem now is, after reinstalling Ubuntu, whenever Grub starts up, Windows XP shows up twice, while previously, it would only be there once. I would like to know, is it safe to remove one of the XP entries from Grub, or did the second entry get made when I decided to import my accounts from XP, or what? I really do not want to lose anything, but I also don't want to have to see XP show up more than it needs to be.

Any input would be greatly appreciated.



EDIT: Here is what is what is in the menu.lst, if it helps any.

```
default 4
fallback 0
timeout 60

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1772820d-3639-4965-ba02-4c268efee97a ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=1772820d-3639-4965-ba02-4c268efee97a ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive

title Microsoft Windows XP Professional
root 
chainloader +1
savedefault
```

---

### Post by powerpleb on 2008-06-16
Delete the bottom entry. It doesn't look like it will work anyway because it doesn't specify a partition.
Also, under where it says 'other operating systems' delete the line that says 'root', that shouldn't be there

---

### Post by bill516 on 2008-06-16
There are folks on this forum a whole lot smarter than I am, but here is what I would do.  (No, I have not seen this problem.)

First I would copy your existing menu.lst and rename the copy "menu.old", or some-such thing.

Then I would open the menu.lst and eliminate that second Windows XP entry, which I suspect was placed there erroneously.

Then I'd restart your machine and see how many times WinXP appears.  I am going to bet you will see it once.

Now imagine the "awful of awfuls" happens and GRUB won't find or run your file!  (Not sure why that would happen, but ....)  At that point use your live CD to go in and delete the misbehaving modified Menu.lst.  Then rename menu.old back to menu.lst.

Granted, you are back to your double listing problem, but the experiment will not have cost you very much.

Luck!

I do think the fix will work.

---

### Post by TMcMahon51 on 2008-06-16
Just curious, but what would be the issue if I didn't remove root from under Other Operating Systems? I only restarted the PC once since reinstalling Ubuntu (was using Dapper, and a clean install of Hardy was the quickest way to update).

/is a noob with this kind of stuff



EDIT: I did that, and it's fine now. I also guess I figured out my question on my own. After removing "root" from Other Operating Systems, it just got rid of the text or whatever that said "Other Operating Systems". Thanks for the help, even though it's something I likely should have figured out on my own, given how obvious it was. >.<

---

### Post by powerpleb on 2008-06-16
The 'Other operating systems' is a title entry, it does nothing but separate the Linux options from the Windows ones. You could delete it altogether if you really wanted to (if you do don't forget to change the default entry at the top to 3). Root specifies which partition the system should boot from. 
There wouldn't be an issue unless you selected it, then you might get an error message and get bumped back to the menu. If you got rid of the root line, when you selected it nothing would happen. It's not a big deal.

---

