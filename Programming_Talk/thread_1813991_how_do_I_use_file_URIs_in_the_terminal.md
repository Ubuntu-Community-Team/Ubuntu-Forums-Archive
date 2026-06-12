---
title: "how do I use file URIs in the terminal?"
date: 2011-07-28
forum: Programming Talk
---

### Post by jobsonandrew on 2011-07-28
if I have a file URI like this:
```
smb://<server>;<user>@<domain>/public/file.jpg
```
or
```
file:///some/file/path
```
how can I use them in the terminal (or script) with commands like mv and cp?

---

### Post by Bachstelze on 2011-07-28
You can't. mv and cp work on filesystems, and on nothing else. What you can do is mount the Samba share as a fiesystem with smbfs, then you can use mv and cp on it, but you will use the filesystem paths, not the smb:// addresses.

---

### Post by AlphaLexman on 2011-07-28
smb:// file:// http:// ftp:// are ALL types of communication protocols. Most web browsers and many file managers can translate the protocols. Unfortunately, your shell interpreter cannot.

---

### Post by jobsonandrew on 2011-07-28
ok, so are you saying the only way to use a file URI in the terminal would be to parse that URI and find the equivalent folder in:
```
~/.gvfs/share_name/file_name
```
?? seems a bit long winded....

---

### Post by AlphaLexman on 2011-07-28
Take a look at 'man scp' it is a secure copy command that can handle ports.

You really don't want to move 'mv' files across different filesystems, it is just too risky.

---

### Post by jobsonandrew on 2011-07-29
I found the answer

```
sudo apt-get install gvfs-bin
```

then

```
gvfs-copy "source" "destination"
```

quotes around the source and target so bash doesn't parse the ';' if present

:)

---

