---
title: "&quot;Program Files&quot; and executables equivalents?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by lavadisco on 2008-08-30
Hi,

I'm really starting to get the hang of Ubuntu now after using it for awhile, I really like it. One thing that is still mystifying me is when I try to specify an alternate program to open a file. Ubuntu asks me what application I'd like to use instead, asking me to find the executable on my machine. 

Here's the problem. I have no idea where all the app executables are, and if I did I wouldn't know which file to pick. So can anybody tell me what the Ubuntu equivalent of the "Program Files" directory is, and what is the Ubuntu equivalent of an "exe" file?

Thanks!

---

### Post by firekool on 2008-08-30
As a example what type of file are you trying to open?

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by Elephantman5 on 2008-08-30
Program information is stored in hidden files in the Home directory.
They all start with dots. .mozilla

"executables" are stored in etc.
Not executable, but the equivalent of program files

---

### Post by jerome1232 on 2008-08-30
/bin

/usr/bin

are the two common places to put binaries, You might want to look at this [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Generally binary files don't have extensions in linux, they are just given the execute permission, sometimes they have a .sh or .bin extension

---

### Post by nothingspecial on 2008-08-30
> **jerome1232 said:**
> /bin

/usr/bin

are the two common places to put binaries, You might want to look at this [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Generally binary files don't have extensions in linux, they are just given the execute permission, sometimes they have a .sh or .bin extension

This is correct, but for beginners here is an example.

You download a (legitimate) torrent and firefox asks you what it should do with this file, you want to use deluge but it`s options are -

Open with Transmission
          Down Them All
          Save To disk 

Depending on how you have your Ubuntu configured.

Next to the first option is a dropdown menu that might list a couple of things but at the bottom of it is the option "other"

A-ha you think, I`ll click on "other" and select deluge. But hang on, when I do it just opens my file browser.
 Well, if like the previous poster says you click on "file system", click "usr", click "bin" and finally "deluge", Then click "ok" the torrent will open with deluge. 

So /bin and /usr/bin are where "program files" are stored - sometimes it`s hard to make that information work though.

---

