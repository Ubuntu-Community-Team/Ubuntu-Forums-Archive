---
title: "Want to Restore Grub (after performing fixboot &amp; fixmbr)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by dvarsam on 2008-04-27
Hello!

My case is long...
On a single hard drive I had installed:
1. Windows XP Pro
2. Ubuntu v7.10
3. swap file

When Ubuntu v8.04 came out, I decided to try it out...
I had no option to install it over v7.10, so I ended up having 4 partitions:
1. Windows XP Pro
2. Ubuntu v7.10
3. Ubuntu v8.04
4. swap file

Today I decided I wanted to dump Ubuntu v7.10
So, from within the Windows OS, I deleted the Ubuntu v7.10 Partition...
I ended up with a Grub Error during boot - i.e. "Error 17".
I couldn't find something relevant in the forums, so I decided to perform a "fixboot" & "fixmbr" from the Windows XP Pro CD Rom.

Currently, during boot, I can get to the Windows XP Desktop, but I am given no option to boot to my Ubuntu v8.04.
I would have deleted that Partition too (& perform a re-install), but I need to backup some files that rely on my Ubuntu v8.04 Desktop first...

So, the question is:

How can I get back the "Boot Option Menu" to boot on Ubuntu v8.04?
Thanks.

---

### Post by bodhi.zazen on 2008-04-27
You will need to restore grub from a live CD. You can use supergrub or follow this guide :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

