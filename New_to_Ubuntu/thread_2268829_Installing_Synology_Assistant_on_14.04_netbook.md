---
title: "Installing Synology Assistant on 14.04 netbook"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by oerWouter on 2015-03-11
hi 

Relative beginner here testing Ubuntu 14.04 on Acer netbook 32bit. Downloaded Synology Assistant to access my Synology NAS on my netbook. Followed all advices on how to install a tar.gz but no success. Extracted to home/sa/ Directory contains no readme file. So I went to /sa in terminal (as admin) and ./configure sais: no such file or directory. Directory contains 3 files: SynologyAssistant SynologyAssistant.bin and dcraw_LNX.sh. Also 7 directories.

- So whats next?
- Does it go like this anytime you want to install software thats not included in the repositories?

Thanks
Wouter

---

### Post by sandyd on 2015-03-12
> **oerWouter said:**
> hi 

Relative beginner here testing Ubuntu 14.04 on Acer netbook 32bit. Downloaded Synology Assistant to access my Synology NAS on my netbook. Followed all advices on how to install a tar.gz but no success. Extracted to home/sa/ Directory contains no readme file. So I went to /sa in terminal (as admin) and ./configure sais: no such file or directory. Directory contains 3 files: SynologyAssistant SynologyAssistant.bin and dcraw_LNX.sh. Also 7 directories.

- So whats next?
- Does it go like this anytime you want to install software thats not included in the repositories?

Thanks
Wouter

./configure is only used when you need to compile applications.

Try running
```

cd ~/sa
bash SynologyAssistant #From what i've seen, this seems to install SynologyAssistant
SynologyAssistant
```

Side Note: For future readers who are using x64/amd64, you will require some 32bit libraries to run this.

---

### Post by oerWouter on 2015-03-12
Works, great thanx!

---

