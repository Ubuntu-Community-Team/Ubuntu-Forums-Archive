---
title: "[SOLVED] exracting RAR files"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by leemajors on 2008-07-04
OK. So, I downloaded a RAR file, but once it had finished downloading I couldn't extract it.

So I go and install 7Zip, which has been my go-to compression tool on windows for years.

Still no luck -- "archive type not supported"

So I go to Synaptic again and look for other things -- there's a non-free RAR add-on for 7Zip so I install that -- no luck. There's a GTK archive front end thing, cause maybe I'm getting the commands wrong -- still no luck.

In desperation, I boot to Windows (which I *really* try hard not to do), install 7Zip because it's a fresh install and lo and behold, the RAR just unzips, no problems.

What, in the world, could I use to unzip RAR files on Ubuntu (8.04) that just works?

---

### Post by dominiquec on 2008-07-04
```
sudo apt-get install unrar
```

and then

```
unrar myfile.rar
```

---

### Post by aquavitae on 2008-07-04
As above. And I think once you've installed unrar the archive manager will handle it as well.

---

### Post by leemajors on 2008-07-04
indeed it does :)

thank you both. 

any ideas why unrar would work where 7zip doesn't, even when it says it handles RAR files and even releases a special un-RARing add-on?

---

### Post by aquavitae on 2008-07-07
7zip uses unrar to handle rar files. In windows, its all bundles together in the way of windows packages. In linux, you need to install the packages you want separately.

---

