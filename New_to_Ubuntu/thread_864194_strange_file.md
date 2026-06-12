---
title: "strange file"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by Rmullin on 2008-07-19
in my /home/[username] folder is a folder: ".gvfs"
cannot delete it
type ls -la, to list permissions and so forth,
permissions are shown as ?????????
attempt to enter folder refused with "permission denied"

What's going on?  Why is this file there and what does it do?

Looks strangely like Microsoft crap that is controlled by a group of folks in Seattle rather than by me . . . paranoid after all these years of abuse by Micropole . . . 

Thanks in advance for a reply.

---

### Post by sisco311 on 2008-07-19
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)

---

### Post by coffeecat on 2008-07-19
Any file/folder with a filename with a leading dot is a hidden one - hidden for a good reason, such as to stop people who don't know their system from deleting it. :wink: The hidden files and folders in your home directory are configuration ones for various apps and the Gnome desktop itself.

> **Rmullin said:**
> cannot delete it

Kindly word of advice: if you delete stuff you don't understand you are going to **break your system**.

---

### Post by bumanie on 2008-07-19
.gvfs is something to do with the virtual filesystem now used in gnome. coffeecat is correct, leave it alone if you want your system to continue working.

---

### Post by Rmullin on 2008-07-20
ok.  thanks for the information.  perfectly answered all my questions.  unmounted it, then deleted it.  on reboot, it reinstalled itself.

i want to be able to delete everything . . . if I choose to do so.    even if it brings the system down . . . I will have learned something . . . just will reinstall from image and go back to where i was . . . 

at any rate, thanks for the information . . . i'm sure i'll be back with further questions as this "dual-boot" drama continues . . . there's no turning back now . . . a month or two more with the bloatware, and its out the "window" . . . 

ciao, 
robert

---

