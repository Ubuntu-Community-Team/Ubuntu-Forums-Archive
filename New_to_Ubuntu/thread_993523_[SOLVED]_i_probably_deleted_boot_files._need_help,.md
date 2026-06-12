---
title: "[SOLVED] i probably deleted boot files. need help, don't want to lose all my files"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by JEV2 on 2008-11-25
:(  it says grub loading then says error ?? i can't remember the exacts numbers.

can any1 help , i'm really panicking knowing that my files may be lost for ever (i'm using the live cd to chat with you)

---

### Post by bumanie on 2008-11-25
Most grub errors can be fixed, but we need to know the error number. Can you boot your computer without the live cd and take note of the error number and then post back.

---

### Post by JEV2 on 2008-11-25
it says error 15.

---

### Post by caljohnsmith on 2008-11-25
Can you give us some more information? Like did you get the Grub error 15 after installing Ubuntu? Or has Ubuntu been working fine and then you just got that error for some reason? Also, do you get the Grub error 15 before seeing the Grub menu on start up? How about opening a terminal (Applications > Accessories > Terminal), and please post:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by JEV2 on 2008-11-25
it was working fine, until i used um a partition editor(forgot the name may be that).i deleted (i think boot), well, since i found out that i couldn't add anything to the boot file, i decided to delete the partition, and hopefully it would be okay, like replace itself on rescue option.(i had the total volume split into 2, mount 1/2 to boot...shouldn't have right?)

but after i deleted i was thinking maybe i should save my files(but i had school and decided just to shut down.

after that when i turned it on it gave me that error.

it doesn't give me choice of choosing, memory test, rescue, or just ubuntu.

it starts with

grub loading...
error 15

and i can't even log in. like i said it immediatly leads t that nothing else.

the terminal part, do i type that when in live cd?

---

### Post by mapes12 on 2008-11-26
> the terminal part, do i type that when in live cd?

Yes.

Boot your machine using the LiveCD then Applications>Terminal then type the code Caljohnsmith posted. Copy and paste the output back to this thread.

---

### Post by quinnten83 on 2008-11-26
Also, 
the live cd allows you to browse your harddisk, use nautilus to check if your data is still there and back it up to external harddrive or some such.

---

### Post by JEV2 on 2008-11-27
ok, thx i will do that once I'm allowed to use  the desktop again, cause i have to use sisters or brothers monitor to use it.

i browsed the hard drives and i went to it, it had the memory still, but i couldn't access my files.i had them in my desktop(but the desktop icon had a red box with a white x in it).

i'll post the info when i'm able to.

edit: it was fixed with a simple reinstall, i just mounted the usual except didn't format the disk.(i read this when searching the web for answer, was simple) although it took time, since my computer was freezing and then didn't even want to load/begin.

but it's fixed.

---

