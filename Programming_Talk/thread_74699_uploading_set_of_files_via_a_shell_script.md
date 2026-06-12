---
title: "uploading set of files via a shell script"
date: 2005-10-12
forum: Programming Talk
---

### Post by oldmanstan on 2005-10-12
How would I go about uploading a group of files to an ftp server using a shell script, I am just learning more about the bash shell and realized it would be far more convenient to run a script each time I change pages around and want them uploaded to the server than having to click over to gFTP and select them with the mouse.

oldmanstan

---

### Post by Leif on 2005-10-12
look up rsync. I'd give you details, but it's been quite a while since I set my system up and I can't really remember

---

### Post by oldmanstan on 2005-10-13
[QUOTE=Leif]look up rsync. I'd give you details, but it's been quite a while since I set my system up and I can't really remember[/QUOTE]

Hmmm, gave that a look.  Seems like it would work quite well if I took the time to set it up, however, it would be sort of overkill for what I'm doing right now I think.  I was thinking more along the lines of scripting an ftp transfer, maybe using wildcards to upload the appropriate files, something like that.  I spose the smart thing to do would be to read up on it and do it myself, but maybe if someone has done it already I won't have to?? haha, yeah, lazy, thanks though, I will keep rsync in mind for the future...

---

### Post by idonthack on 2005-10-13
```
ftp ftp.url.com < ftp_commands
```

IIRC, that will read ftp_commands line by line and use it as input for your ftp session. I'll check once I get home on my comp, I used it once and I think I still have the script lying around.

---

