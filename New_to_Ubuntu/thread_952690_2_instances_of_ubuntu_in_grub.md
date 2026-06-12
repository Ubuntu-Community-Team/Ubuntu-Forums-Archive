---
title: "2 instances of ubuntu in grub"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by kingdonerkebab on 2008-10-19
I've noticed on booting my laptop up when I get to GRUB, the following options come up:

Ubuntu 8.04.1, kernal 2.6.24-21-generic
Ubuntu 8.04.1, kernal 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernal 2.6.24-19-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery mode)
Ubuntu Memtest86+
Other operating systems
Windows Vista/longhorn (loader)

I'm wondering why there are two instances of ubuntu there. I click on either of them and it gives the same results. Are there supposed to be two there? If not, is this likely to be taking up an extra resources in any way? Is there any way I can get rid of the extra options?

Not really a problem as such, just ever so slightly annoying. And I've found that I managed to fix all my other problems on Ubuntu completely and if I can clean this up I'd be pleased! :) Just slightly anal I suppose. With Vista, many months have passed and I still put up with constant error messages about my damn graphics driver and although it doesn't cause me any specific problems it drives me MENTAL every time I see it. 

Thanks

Chris

---

### Post by buccaneere on 2008-10-19
That's normal.

---

### Post by billgoldberg on 2008-10-19
> **kingdonerkebab said:**
> I've noticed on booting my laptop up when I get to GRUB, the following options come up:

Ubuntu 8.04.1, kernal 2.6.24-21-generic
Ubuntu 8.04.1, kernal 2.6.24-21-generic (recovery mode)
Ubuntu 8.04.1, kernal 2.6.24-19-generic
Ubuntu 8.04.1, kernal 2.6.24-19-generic (recovery mode)
Ubuntu Memtest86+
Other operating systems
Windows Vista/longhorn (loader)

I'm wondering why there are two instances of ubuntu there. I click on either of them and it gives the same results. Are there supposed to be two there? If not, is this likely to be taking up an extra resources in any way? Is there any way I can get rid of the extra options?

Not really a problem as such, just ever so slightly annoying. And I've found that I managed to fix all my other problems on Ubuntu completely and if I can clean this up I'd be pleased! :) Just slightly anal I suppose. With Vista, many months have passed and I still put up with constant error messages about my damn graphics driver and although it doesn't cause me any specific problems it drives me MENTAL every time I see it. 

Thanks

Chris

Just two different linux kernels.

The two versions are different, but you will most likely never notice it.

You can safely remove the -19 kernel if you want.

---

### Post by robalcorn on 2008-10-19
> **billgoldberg said:**
> Just two different linux kernels.

The two versions are different, but you will most likely never notice it.

You can safely remove the -19 kernel if you want.


A great tool for this is called " Start-up manager" just download and you can configure grub to your liking including the number of kernels. Also has the option to restore if something gets messed up.

---

### Post by ugm6hr on 2008-10-19
> **buccaneere said:**
> That's normal.

Indeed.

And they are not strictly the same - it just appears that way.

Your GRUB options are stored in /boot/grub/menu.lst

So if you don't want the older kernel option, just delete the entries that refer to it in that file.

Of course, it can be helpful to have the older kernel available, just in case the new kernel misbehaves with your specific hardware, which has been described before.

---

### Post by OutOfReach on 2008-10-19
Yes, this is normal. When ever you update to a new kernel it will be added to your grub list. You can remove these extra entries by either hand editing the /boot/grub/menu.lst or installing Startupmanager and deleting the entries from there. The updated kernels will stay installed, but their entries will be gone

---

### Post by roger_1960 on 2008-10-19
Hi

To add to what has been said - its a good idea to leave the last version (in this case 19) which worked + the current one in grub.  Then, if it all goes wrong - when you try to reboot just after you upgraded to a new kernel for example, you can boot into the 'old version' which does work and sort out the problem........

---

### Post by WWSmith36 on 2008-10-19
I would not remove the the older kernel from the list until you are completely sure everything is working perfectly.  The new kernel upgrade has been giving may users some fits.  I always suggest keeping one older kernel in you grub menu just so you have the option to boot into a stable kernel if you need to.

You can limit the number of kernels that will appear in your grub menu by modifying this line in your menu.lst

```
# howmany=all
```

I typically set mine to 2 to keep the list from getting too long.

---

