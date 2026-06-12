---
title: "Discover source code?"
date: 2005-08-21
forum: Programming Talk
---

### Post by debackerl on 2005-08-21
Hi,

Could someone tell me where is the source code of 'discover'? I think that it is that software I want to look at. In fact I look the scripts that detects the graphics card used, and keyboard layout then write X.org config file. I'm a FreeBSD user, therefore after a look at the way the Ubuntu Live CD boots didn't helped me much (way too obscure for me right now).

Also does 'discover' have any link to 'discovery' of Progreny Debian?

I looked for documentation about the internals of Ubuntu, the boot process, how to browse the repository, but did not found anything. Only user-related stuffs.

Thank you  :grin:

---

### Post by Dogmeat on 2005-08-21
Hello, getting the source of packages is an easy process.

```
1. Open a terminal and type 'cd ~/Desktop'
2. Type 'apt-get source discover'
```

The tarball containing the source should now be in your desktop. You can extract it to ~/src for example :)
The above method works for all ubuntu packages (probably debian too).

---

### Post by debackerl on 2005-08-21
Thank you Dogmeat!

Final solution:

Start Live CD, launch System\Administation\Synaptic Package Manager to update packages list.

Then open terminal and type:

apt-get source discover1
apt-get source discover1-data

Now use the file browser to look in your home folder ;)

BUT: Discover does not seem to handle keyboard layout detection. I searched for all files containing "Please press one of these keys" in the downloaded source codes, and found no results.  ](*,)

---

