---
title: "&quot;Failed to download repository information.&quot;"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by Mentiroso on 2013-09-24
I am running Ubuntu 12.04.

The package information was last updated 58 days ago, per the Update Manager.

When I click 'check'... it gives me "Failed to download repository information" and advises me to check my internet connection.

However, as far as I can tell, my internet connection is working just fine.

(The 'details' gives me a lot of '404 not found')

Help?

I mean, I'd like to be up to date, but that's apparently impossible since my OS cannot update its package files.

---

### Post by ibjsb4 on 2013-09-24
Probably will get the same thing in terminal, but try it anyhow.

```
sudo apt-get update
```

Also try a different download source.

---

### Post by UltimateCat on 2013-09-26
You could also edit your sources.list and add any repository that you want-
To view your sources.list in the terminal run:
```
cat /etc/apt/sources.list

```

And to edit your sources.list in the terminal "as root" run:
```
nano /etc/apt/sources.list

```
Nano is just one of the text editors you could use Gedit or another one of your choice-

I stay away from certain backports and 3rd party stuff. Just a suggestion--

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)
[http://mixeduperic.com/downloads/org-files/ubuntu/etcaptsourceslist-ubuntu-12041-default-file.html](http://mixeduperic.com/downloads/org-files/ubuntu/etcaptsourceslist-ubuntu-12041-default-file.html)

---

### Post by Mentiroso on 2013-09-30
That was the solution!
I got rid of backports and the error messages went away.

---

