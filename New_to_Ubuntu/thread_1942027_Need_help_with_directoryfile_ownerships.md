---
title: "Need help with directory/file ownerships"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by ixtok on 2012-03-16
I am running Ubuntu 11.10 on a HP netbook. My system crashed and I can not log in. I wish to do a fresh install after I retrieve my home directory, which is in the root partition. I am now on a usb live and can see all the files I wish to retrieve but the home directory is owned by root and I am not allowed to copy it to my other memory stick. How do I do this?

---

### Post by coffeecat on 2012-03-16
If your home directory is owned by root, then something has gone very wrong. Your problem more likely is that the UID of the "ubuntu" user (999) in the live session is different from the UID (probably 1000) of your files in your home directory on the hard drive, and this is why you are prevented from copying.

In the live session, open a root nautilus with:

```
gksu nautilus
```

It will open in the root account folder of the live session, so you will have to navigate to your mounted hard drive root partition to copy your files. Post back if you need any help with the details of this.

**EDIT**: oops - should have added: use the root nautilus to copy from and an ordinary nautilus window for the memory stick to copy to.

---

### Post by jerome1232 on 2012-03-16
This will open a root nautilus session so you can do your recovery.

```
gksu nautilus
```

Before you copy it back into a real installation, be sure to chown the files to your regular user. Just in case.

```
sudo chown -R $USER:$USER /path/to/those/files
```

edit: Out typed!

---

### Post by ixtok on 2012-03-16
Entering the first command gksu nautilus produced some errors


ubuntu@ubuntu:~$ gksu nautilus

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> l17
--> root
--> inode/directory

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-gdu extension

Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2012-03-16
A bit like the little boy who cried wolf, "gksu nautilus" *always* produces errors in the live session, which usually do not matter. Did a root nautilus window open? The ubuntu@ubuntu prompt at the end of the output you posted suggests not, but you may have closed the window yourself.

**EDIT**: no I get the same set of warnings from "Hash table.." line in my permanent installation on shutting down the root nautilus. I suggest to just use the root nautilus and ignore the messages.

---

### Post by ixtok on 2012-03-16
> **coffeecat said:**
> A bit like the little boy who cried wolf, "gksu nautilus" *always* produces errors in the live session, which usually do not matter. Did a root nautilus window open? The ubuntu@ubuntu prompt at the end of the output you posted suggests not, but you may have closed the window yourself.
.


the root nautilus window did not open, I got a small error window instead.

---

### Post by jerome1232 on 2012-03-16
out of curiosity does the below work, in practice you should always use gksu instead of sudo for a graphical application, but this is a live cd, it won't screw anything up that a reboot won't fix, doesn't hurt to try (odd that nautilus is quiting)

```
sudo nautilus
```

---

### Post by ixtok on 2012-03-16
> **jerome1232 said:**
> out of curiosity does the below work, in practice you should always use gksu instead of sudo for a graphical application, but this is a live cd, it won't screw anything up that a reboot won't fix, doesn't hurt to try (odd that nautilus is quiting)

```
sudo nautilus
```

This is what I get with the above command


ubuntu@ubuntu:~$ sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by coffeecat on 2012-03-16
> **ixtok said:**
> This is what I get with the above command


ubuntu@ubuntu:~$ sudo nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

I've not seen that before and, apart from the warnings, I've never had a problem with "gksu nautilus" in the live session. I suggest you create a new live USB or live CD. The one you are using could be faulty.

---

### Post by ixtok on 2012-03-16
I shut down and re booted the live usb, and tried again. Half the files copied, shut down and re booted again and got the reamining files to copy.

Something is strange but thanks for all your help

---

