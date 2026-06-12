---
title: "Ran Windows XP after installing Ubuntu and this happened"
date: 2012-09-11
forum: New to Ubuntu
---

### Post by Vinton90 on 2012-09-11
I installed Ubuntu 12.04 with Wubi alongside (or is inside?) of Windows XP, and for the next few days I used Ubuntu only. This morning I felt like watching a movie on Netflix and booted up XP, CHDSK ran and began deleting files and I spotted "wubi" in there. I was curious and made sure that XP worked fine and then restarted. 
After booting into Ubuntu this appeared-

[LEFT]          "Gnu Grub version 1.99-21ubuntu3.1
       Minimal BASH-like line editing is supported. For the first word, TAB lists
       possible command completions. Anywhere else TAB lists possible device or file completions.
grub>"

So, I typed "TAB." That's wrong, you have to hit the tab key. Another few lines of text appeared that say 

      ". [ authenticate background_color background_image badram boot break clear
        configfile continue cutmem echo export extract_entries _configfile 
        extract_entries_source initrd insmod linux loadfont loopback ls lsfonts
       menuentry normal normal_exit probe return search search.file search.fs_label
       terminal_output test unset
       grub>"

So, I'm going to assume that I am essentially not going to be able to bring back anything that was there. That is okay because I hadn't saved much or created anything major, I'm more intrigued than anything else. I'd like to know what happened and why, if anyone knows. I appreciate anyone taking a look at it.

I did type in "linux" and received "error: no kernel specified."

Again, thank you.

[/LEFT]

---

### Post by bcbc on 2012-09-11
Chkdsk probably 'repaired' or removed the root.disk. [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by Vinton90 on 2012-09-11
That looks about right. I appreciate your insight, thank you.

---

