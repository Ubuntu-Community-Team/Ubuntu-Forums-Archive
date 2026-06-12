---
title: "Reading and Writing Permissions"
date: 2018-11-25
forum: New to Ubuntu
---

### Post by alejandro202 on 2018-11-25
Hello Ubuntu Community.

I recently started to use Ubuntu and I'm getting the hang of it. But I keep having the same problem with my USB flash memories. So basically my flash memories are mounted correctly. But for example when I access them through an application like GIMP it doesn't allow me to do so. An error pop ups that discusses the reading permissions. How can I give applications reading and writing permissions of my flash memories. Pleas help.

---

### Post by Morbius1 on 2018-11-25
This is just a guess since I don't use GIMP but I suspect it's not GIMP but how you installed it. If you went through "Ubuntu Software" you had 2 choices. The top one is a "snap" package. The bottom one comes from the repository proper. The new user would have to be very attentive to know which is which because it is not at all obvious.

Snap packages are restricted whereas the real package is not. Please see this to see if it matches your symptom: [https://askubuntu.com/questions/1054893/gimp-2-10-doesnt-have-permission-to-access-a-usb-drive-why-how-to-resolve-1](https://askubuntu.com/questions/1054893/gimp-2-10-doesnt-have-permission-to-access-a-usb-drive-why-how-to-resolve-1)

---

### Post by alejandro202 on 2018-11-25
Thanks! It worked. This happens to other applications to, like KeePass, PyCharm and more. The folder /media displays empty. Is there also a command to give these applications permission?

---

### Post by TheFu on 2018-11-25
Snaps are designed to be self-contained and secured by limiting where they can access files on the system.
The easy answer to having programs allowed access to random storage is not to install snaps.  But there are liabilities in doing this.

If you want to restrict access, but still have control, you can setup each application to run inside a container with restricted access to the file system that you control. This is non-trivial.  Or you could try to use a sandbox too like firejail.

For my needs, I've decided to accept the added risks and avoid using any snap packages.  Really, does a calculator need to be self-contained?  Some of the choices for which programs need to be snaps doesn't make sense to me.  Tools that are actively used on the internet probably should be snaps - email programs and web browsers, but programs that only use local files?  Probably not much of a risk.

---

### Post by alejandro202 on 2018-11-25
Thanks, from the "ubuntu software" application I'm able to edit the preferences of each snap I've downloaded. Very useful. Thanks for your reply.

Cheers!

---

