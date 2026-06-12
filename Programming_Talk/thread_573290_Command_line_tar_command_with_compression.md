---
title: "Command line tar command with compression"
date: 2007-10-11
forum: Programming Talk
---

### Post by tc101 on 2007-10-11
I use the following command line to put everything in the D folder into a tar file in the backup folder.  

sudo tar -cf /home/backup/D_backup$(date +"%Y%m%d").tar /home/D

However the backup file is the same size as the original folder.  How do I compress it, doing something like a zip file in windows.  I would like to do this from the command line.

Also, is there a way to encrypt it from the command line?

---

### Post by Ramses de Norre on 2007-10-11
For .tar.gz:
```
sudo tar -czf /home/backup/D_backup$(date +"%Y%m%d").tar.gz /home/D
```

For .tar.bz2 (higher compression, takes longer):
```
sudo tar -cjf /home/backup/D_backup$(date +"%Y%m%d").tar.bz2 /home/D
```

You might want to read up on gpg for the encryption.

---

### Post by tech9 on 2007-10-11
> **Ramses de Norre said:**
> For .tar.gz:
```
sudo tar -czf /home/backup/D_backup$(date +"%Y%m%d").tar.gz /home/D
```

For .tar.bz2 (higher compression, takes longer):
```
sudo tar -cjf /home/backup/D_backup$(date +"%Y%m%d").tar.bz2 /home/D
```

You might want to read up on gpg for the encryption.

cool... I was looking for a script or command by date

---

