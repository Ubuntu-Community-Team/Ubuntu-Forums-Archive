---
title: "How to tell flac bit resolution?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Ansible on 2008-09-07
I have some flac files, and I'd like to know if they are 16 bit or 24 bit resolution files.  The file properties in nautilus don't say, and the flac commandline tool doesn't have anything obvious that reports this.  If I decode the file to WAV, it comes out as 16 bit/44.1khz.  This seems to imply that the flac file is 16 bit audio.  However, its possible that the decoder is set to create 16 bit wav files by default.  How do I tell for sure what the bit resolution is?

---

### Post by Vivaldi Gloria on 2008-09-07
Use one of the commands

```
metaflac --list music.flac
```

```
file music.flac
```

---

### Post by Ansible on 2008-09-07
Cool, the 

file music.flac 

command worked.  The metaflac command hex-dumps the file to the console.  Anyway, got what I wanted, thanks!

---

### Post by Vivaldi Gloria on 2008-09-08
> **Ansible said:**
> Cool, the 

file music.flac 

command worked.  The metaflac command hex-dumps the file to the console.  Anyway, got what I wanted, thanks!

You're welcome. Weird that "metaflac --list" doesn't work for you. Anyway. Have fun.

---

