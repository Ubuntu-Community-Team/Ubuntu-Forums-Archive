---
title: "[SOLVED] Dual boot with Vista help!"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by MadsRH on 2008-05-23
I know there are about 500 post about this, but non of them helped me :confused:

I really messed up the installation of Vista. By reading all the post's I now have both OS's running, but I would like to replace the WindowsBootLoader with my good old Grub!

I have no idea what my harddrive partitions are called!

Can anyone help me??? :(
**MadsRH**

---

### Post by Paqman on 2008-05-23
How did you install Ubuntu? If you used Wubi then you're stuck with the Windows bootloader, i'm afraid.

---

### Post by MadsRH on 2008-05-23
No, Ubuntu first.
I tried to follow this guide, but I couldn't get Vista to install to the drive, so I formated it to NTFS and then it installed fine.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

So I tried the part "Dualboot Option 2 - GRUB bootloader" typing ```
root (hd0,0)
``` from the liveCD, but I got some kind of error (can remember now!)

---

### Post by kansasnoob on 2008-05-23
I assume you installed or reinstalled Vista after having Linux up and running. Regardless this should help you:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

Both methods work. I've done it!

Just breathe easy and bust out a spiral notebook to keep track of what you've done.

I'll be taking off soon for most of the evening but you can do this.

---

### Post by kansasnoob on 2008-05-23
Oops, overlapped.

Let me think.

---

### Post by Paqman on 2008-05-23
Ah, ok. Just to confirm, you did
```

sudo grub
root (hd0,0)
setup (hd0) 
quit

```

In the terminal from the LiveCD? Can you please post the actual error message you got?

---

### Post by MadsRH on 2008-05-23
No I only wrote "root (hd0,0)"

Well, I can't remember it!!! I could boot from the LiveCD and try it again?

---

### Post by Paqman on 2008-05-23
Yeah, you need the "sudo grub" to get into the grub setup, from there you can specify the partition. I didn't think the guide you linked to was 100% clear about that, which is why I asked.

Btw, "root (hd0,0)" is only right if Ubuntu is installed on the first partition. You might need to change that to reflect where it actually is.

---

### Post by MadsRH on 2008-05-23
Okay, I hope I did it right now then!

I]m on the liveCD and just did the ```
sudo grub
root (hd0,0)
setup (hd0) 
quit
```

So what now! I guess there\s no sign of Vista or how does it works

---

### Post by kansasnoob on 2008-05-23
Just FYI the reason I thanked PAQMAN was his simple and prophetic words, "In the terminal from the LiveCD?"

While it may not apply here my most frequent early failures with Ubuntu were related to using "MY" Ubuntu installation to make adjustments that could only be made using the live CD.

It's a different world for long time Windows users.

---

### Post by Paqman on 2008-05-23
> **MadsRH said:**
> 
So what now! I guess there\s no sign of Vista or how does it works

If that worked you'll get Grub up when you reboot. Since you installed Ubuntu first you won't have Vista on the list. You can add it by editing the Grub menu:
```

gksu gedit /boot/grub/menu.lst

```

You'll want to add an entry for Windows that looks like:
```

title		Windows Fista
root		(hd0,**insert correct partition here**)
savedefault
makeactive
chainloader	+1

```

So you'll need to know what partition Windows is on for that. Grub numbers the partitions starting at zero, so if Windows was on sda4, that would be (hd0,3)

---

### Post by MadsRH on 2008-05-23
Thanks Paqman! It worked great, but I still ****** up again :confused:

I just wanted to do a little finttuneing by removing the WindowsBootLoader. So I pressed the Uninstall Bootloader (inside Vista). 
So now I get this

```
NTLDR is missing error
```

can I just do the

```
sudo grub
root (hd0,0)
setup (hd0) 
quit
```

from the liveCD again?

---

### Post by Paqman on 2008-05-23
No, you need NTLDR. You can't boot Windows without it. Does Vista have a "Whoops, please reinstall NTLDR" button?

---

### Post by MadsRH on 2008-05-23
Crap! You're funny - it was the EasyBCD that had that option. Okay maybe I should just get Ubuntu running again and forget Vista for the a few days ](*,)

or run a repair with the Vista CD?

---

### Post by msidhard on 2008-05-23
hey man just download super GRUB disk [SGD] from net . its just 1.44 mb . u will get it as iso file write it with nero in a blank cd. so that if u r installing the windows again u can fix it easily. download it from here :- [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by MadsRH on 2008-05-23
I really just want to get Ubuntu working again

---

### Post by MadsRH on 2008-05-24
can anyone help?

---

### Post by MadsRH on 2008-05-24
Okay, I got it working :)

I did a repair with the Vista CD and booted on the Ubuntu LiveCD and did the 

```
sudo grub
root (hd0,0)
setup (hd0) 
quit
```

Then it worked!!! Thanks for all the help ):P

**MadsRH**

---

