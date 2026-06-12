---
title: "grsync/rsync not excluding a volume"
date: 2016-12-15
forum: New to Ubuntu
---

### Post by escanlan on 2016-12-15
I am trying to back-up the entire OS volume (local drive, origination volume) to an external USB connected drive (destination volume).  When I attempt to exclude the USB drive (destination volume) in either grsync or rsync it does not exclude the volume and attempts to back it up to itself.  I am using Admin to perform the backup and have tried everything from excluding the volume to the actual file directory.  Is there a specific "exclude" format to prevent backing up the destination volume onto itself?

---

### Post by kpatz on 2016-12-15
You can use -x to tell rsync not to cross file system boundaries, so mounted directories will be excluded.  This will stop it from backing up the USB drive to itself, but if you have other mounted directories (such as /var or /home) that you want to include in the backup you'll have to list them separately in the command.  For example, if you want to back up / and also /home since it's in its own partition, you could use:```
rsync -avx / /home /media/yourusername/myusbdrive
```(This assumes your USB drive is mounted on /media/yourusername/myusbdrive... obviously it will be different in your case)

Alternatively, you can use an exclusions file with the directories and file patterns you don't want to backup.  So if the USB drive is mounted to /media/yourusername/myusbdrive, you could create a file that contains:
```

/media/yourusername/myusbdrive/*

```

Then use the --exclude-from option on rsync with the name of the file.  For example, if you named it exclude.txt, use a command like:```
rsync -av --exclude-from ~/exclude.txt /backup_from_here /media/yourusername/myusbdrive
```

If you go the exclusion file route, there are some other places you probably don't want to back up either, such as:
```
/tmp/*
/run/*
/var/run/*
/var/lock/*
/var/tmp/*
/home/*/.thumbnails
/home/*/.cache
/home/*/.mozilla/firefox/*.default/Cache
/home/*/.local/share/Trash
/home/*/.gvfs/
/lost+found

```

---

### Post by DuckHook on 2016-12-15
Welcome to the forums, escalan

Please post the contents of your command, else we can't tell what you tried or what may be wrong.

Also, with external USB drive connected, post output of:```
sudo blkid
``````
df -h
```

---

### Post by SeijiSensei on 2016-12-16
> **kpatz said:**
> If you go the exclusion file route, there are some other places you probably don't want to back up either, such as:
```
/tmp/*
/run/*
/var/run/*
/var/lock/*
/var/tmp/*
/home/*/.thumbnails
/home/*/.cache
/home/*/.mozilla/firefox/*.default/Cache
/home/*/.local/share/Trash
/home/*/.gvfs/
/lost+found

```

I'd add
```

/proc/
/sys/
/dev/

```
to that list as well.

---

