---
title: "new CD burner burns ISOs but not mp3s"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-27
ok, i recently replaced my ATAPI cd ROM drive with an IDE CD-RW drive, and am able to burn distros (i just got done with a DSL Live CD session) but for some reason i can't burn music. k3b supposedly won't burn mp3s but will burn wav files (or so it tells me in the error message) Brasero doesn't detect the CD-R and gnome baker will only accept 6 or 7 mp3s before it tells me that "media is too large to fit on the rest of the medium". yet i can burn a 700 MB ISO just fine, any clue here guys? thanx a load in advance



phil

---

### Post by shifty_powers on 2008-05-27
how long have you had ubuntu and what version?

---

### Post by rockerphil on 2008-05-27
i've been using Ubuntu for about 6 months now, and i'm currently running a custom built variant built on the 7.1 Gutsy Gibson minimal CD that i insalled a CLI from and then installed the x windows system, IceWM as my Window Manager and of course Firefox as my browser

---

### Post by rockerphil on 2008-05-27
bumpin it back up, could really use some help guys, i've been workin on this for the past 3 days

---

### Post by rockerphil on 2008-05-27
anybody?

---

### Post by stchman on 2008-05-27
> **rockerphil said:**
> ok, i recently replaced my ATAPI cd ROM drive with an IDE CD-RW drive, and am able to burn distros (i just got done with a DSL Live CD session) but for some reason i can't burn music. k3b supposedly won't burn mp3s but will burn wav files (or so it tells me in the error message) Brasero doesn't detect the CD-R and gnome baker will only accept 6 or 7 mp3s before it tells me that "media is too large to fit on the rest of the medium". yet i can burn a 700 MB ISO just fine, any clue here guys? thanx a load in advance



phil

If you use hardy Heron you need an additional package to burn MP3s to make an audio CD.

```

Gutsy and earlier
sudo apt-get -y install k3b libk3b2-mp3

Hardy
sudo apt-get -y install k3b libk3b2-extracodecs
```

This will allow you to create audio CDs from MP3s usgin K3b.

---

