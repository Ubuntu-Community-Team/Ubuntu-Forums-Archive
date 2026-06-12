---
title: "No wireless internet after 2.6.24-18 upgrade"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by tstack77 on 2008-06-08
I can connect to the router/internet when wired with no problems, but if wireless I can connect to the router but get no internet. I am assuming it's from the kernel upgrade but have no idea what to do beyond what I have already tried (deleting saved network from keyring and starting fresh).

Any ideas?

---

### Post by collapsing wave on 2008-06-08
this seems really cheeky to ask a question rather than answering yours. But I think I'm after the 2.6.24-18 upgrade that you are having trouble with. My post is headed no way forward no way back if you can help. I can see you've got your own problems though and may not have the time

---

### Post by bumanie on 2008-06-08
Try booting with the previous kernel, if it still works with everything, remove the latest kernel via synaptic. That's why it is good to have an old kernel or two around - just in case this happens.

---

### Post by tstack77 on 2008-06-08
The older kernel works...hmmm.

Why???


Wave: It installs with the update manager.

---

### Post by shifty_powers on 2008-06-08
make sure you've got the kernel restricetd modules installed for that kernel as well.

this happens somteimes, you get a kernal update, but your wireless driver is contained in the restricted module.

worst comes to the worst, just use the previous kerne, won't make any real difference to you ;)

---

