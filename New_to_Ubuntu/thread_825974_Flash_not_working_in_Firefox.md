---
title: "Flash not working in Firefox"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Checkhovian on 2008-06-11
Hello, just put Ubuntu onto my Dell laptop, and can't get my flash to work in firefox. When I access a page with flash, I see a lovely gray "play" button, but nothing happens when I click it.

I'm running Firefox 3.0b5, and have added the macromedia flash plugin in "add/remove programs".

How can I get my flash working?

---

### Post by wolfen69 on 2008-06-11
try removing the flash you installed.then:```
sudo apt-get clean
```then ```
sudo apt-get install flashplugin-nonfree
```

make sure to update your computer. firefox 3 beta5 is now final.

---

### Post by cariboo on 2008-06-11
Using sudo apt-get clean only removes archived packages from /var/cache/apt/archives it does not remove any programs from the computer.

The link for this file doesn't seem to be working any more so I've attached to this post. Use it to install flash 10 this should cure all your problems.

To use it, save the file in your home directory. In a terminal make it executable:

```
chmod +x install_flash10.sh
```

Then run it as root in a terminal:

```
sudo ./install_flash10.sh
```

Take some time to read the script and it will tell what it will do.

Jim

---

