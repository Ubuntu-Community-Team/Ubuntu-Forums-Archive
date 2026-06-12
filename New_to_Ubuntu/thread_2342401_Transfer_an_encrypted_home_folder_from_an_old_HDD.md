---
title: "Transfer an encrypted home folder from an old HDD"
date: 2016-11-06
forum: New to Ubuntu
---

### Post by sashko.taylor on 2016-11-06
Hello there.

So I recently installed the Ubuntu 16.04 to the new HDD.

Now I would like to transfer my documents and media (total of about 200GB) from another HDD i was using before. 
I connected the drive via SATA cable. But since all the files are under my home folder, I find them inaccessible now.

Could you please advise on what would be the best way to do it?

---

### Post by oldrocker99 on 2016-11-06
Grsync should be able to get your files copied without any problems. To make sure, run this on your backup folder first:
```
sudo chown yourusername:yourusername foldername
```

---

