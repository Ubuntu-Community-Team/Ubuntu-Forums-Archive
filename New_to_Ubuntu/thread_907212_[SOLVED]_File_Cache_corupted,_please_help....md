---
title: "[SOLVED] File Cache corupted, please help..."
date: 2008-09-01
forum: New to Ubuntu
---

### Post by GutsyRabbit on 2008-09-01
After installing some apps with Synpatics i get this error: file cache corupted.
Is there a way to correct this?

---

### Post by drs305 on 2008-09-01
Without a bit more information, it's hard to say what the specific problem is. Try running this. It will backup the current dpkg status file and restore the previous one.
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

---

### Post by GutsyRabbit on 2008-09-01
i just need to rebuild the cache. but forgot the commands needed for that.

---

### Post by WRDN on 2008-09-01
You can remove all cached files by opening the Terminal and typing:

```
sudo apt-get clean
```

Alternatively, remove partially downloaded files by typing:

```
sudo apt-get autoclean
```

---

### Post by drs305 on 2008-09-01
> **GutsyRabbit said:**
> i just need to rebuild the cache. but forgot the commands needed for that.
Or were you looking for:
```
sudo apt-cache gencaches
```

---

### Post by GutsyRabbit on 2008-09-01
Yups those where the commands i was looking for but i got another error when i used "sudo apt-get update" :
E: Type 'ftp.de.debian.org/debian' is not known on line 6 in source list /etc/apt/sources.list
But there is no such repository in my repositoy list.

---

### Post by drs305 on 2008-09-01
> **GutsyRabbit said:**
> Yups those where the commands i was looking for but i got another error when i used "sudo apt-get update" :
E: Type 'ftp.de.debian.org/debian' is not known on line 6 in source list /etc/apt/sources.list
But there is no such repository in my repositoy list.
Are you absolutely sure? Sometimes apps amend the sources.list without your knowledge. Running "cat /etc/apt/sources.list" only takes a few seconds.

---

### Post by GutsyRabbit on 2008-09-01
Yes i am sure about that, i used the command ans showed me this:
ftp.de.debian.org/debian

Now i remember putting something in the "Software Sources"  and then deleted it, somehow it remained in the /etc/apt/sources.list .
I deleted it mannualy from the list , everything works fine now.

THANKS ALLOT FOR THE HELP! "hugs and kisses"-i'm so happy :)

---

