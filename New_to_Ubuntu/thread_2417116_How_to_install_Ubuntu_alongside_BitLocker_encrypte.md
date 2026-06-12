---
title: "How to install Ubuntu alongside BitLocker encrypted Windows10?"
date: 2019-04-20
forum: New to Ubuntu
---

### Post by debofsky on 2019-04-20
How to install Ubuntu alongside BitLocker encrypted Windows10?

If it's impossible to rely on TPM, I don't mind switching to password.

My first question is can I install Ubuntu second, on a computer with already installed W10 with BitLocker, or do I need first install Ubuntu, and then Windows?

---

### Post by TheFu on 2019-04-20
I haven't dual booted in over a decade, but the normal Ubuntu installer takes the entire HDD when "encryption" is enabled.  What that means is that you'll need to perform a manual install which is not something someone with less than a year of Linux experience in the shell should attempt.  Regardless of who you are, make a backup of anything you can't afford to lose.  

Ok, so Paddy wrote a guide about manually installing encrypted Ubuntu. Check the "Security" subforum for it and links.  Read through Paddy's guide to see if you are comfortable with all the steps.
 
I've never seen Win10, much less installed it. Sorry.

---

### Post by Rubi1200 on 2019-04-20
As TheFu correctly mentioned, make backups before attempting anything.

Here is the link you need written by forum member Paddy Landau: [https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)

---

### Post by debofsky on 2019-04-21
It turns out it just works.
1. On Windows reduce size of system partition
2. Install Ubuntu on free space (installer refers to it as "replace partition")
3. After installation is finished there will be a wall of errors, just shutdown laptop/pc with power switch
4. If you choose to boot Windows it'll ask for BitLocker code, input it.
Done
I rebooted to Linux, did something, rebooted to Windows, it doesn't ask for code, boots normally

---

### Post by TheFu on 2019-04-21
Glad it worked.  I was thinking you wanted an encrypted Ubuntu install as well.

If this is solved, please help out the community and use the 'thread tools" button near the top to mark it that way.

---

