---
title: "Please help with rsync (CLI)"
date: 2011-09-24
forum: New to Ubuntu
---

### Post by vasa1 on 2011-09-24
I would be grateful for comments, advice or corrections for what I'm doing.

I'm on Ubuntu 11.04 (Unity).
I'm using rsync (CLI) to learn how to back up just my files. I tried grsync but prefer using plain rsync for now.
I have made a list of files (and folders) that I want to back up.
```

/home/vasa1/.config/google-chrome/Default/databases/chrome-extension_fjnbnpbmkenffdnngjfgmeleoegfcffe_0/1
/home/vasa1/.config/google-chrome/Default/Local Storage/chrome-extension_cfhdojbkjhnklbpkdaibdccddilifddb_0.localstorage
/home/vasa1/.config/google-chrome/Default/User StyleSheets/Custom.css
/home/vasa1/.mozilla/firefox/3sq6w9a2.default/permissions.sqlite
/home/vasa1/.mozilla/firefox/3sq6w9a2.default/SimpleBlock.ini
/home/vasa1/.mozilla/firefox/3sq6w9a2.default/stylish.sqlite
/etc/privoxy/config
/etc/privoxy/user.action
/home/vasa1/.themes
/home/vasa1/Documents
/home/vasa1/Downloads
/home/vasa1/Music
/home/vasa1/Pictures
/home/vasa1/Public

```

The first eight items are files and the rest are folders, some of them with more levels of nested folders.

For learning purposes, I'm backing up to an NTFS partition on the same hard drive (/media/EC82B9BF82B98E98/Testing).

After a bunch of dry runs and Googling, this is the "command" I'm using:
```

rsync -r -t -p -g -v --delete -s --files-from=/home/vasa1/Desktop/Include / /media/EC82B9BF82B98E98/Testing 

```
where Include is the file on my Desktop that has the list of files/folders I want to back up.

After running the command, I get a long output (since there are a lot of files) but at the end there is this:
```

sent 270341759 bytes  received 35864 bytes  7407606.11 bytes/sec
total size is 270182539  speedup is 1.00
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]

```

How do I capture the output of the rsync command to a file that I can read later?
How can I know which "**files/attrs were not transferred (see previous errors) (code 23) at main.c(1060)**"?
Where are/were the "previous errors" for me to look at?
What is code 23: "Partial transfer due to error"? If it's important, how can I know more about it?
What is main.c (1060)? Does it refer to the lines that flew past on the screen while rsync was working?
Does "1060" refer to line number?

By looking at the destination, I get the feeling that all I wanted to transfer has been transferred so the errors are confusing me!

---

### Post by papibe on 2011-09-25
A few pointers:
[LIST]
[*]The option -a implies -rlptgoD so you can save arguments.
[*]--files-from deactivate the -r option so you need to add it explicitly.
[*]Just to comply with documentation I would add a trailing / at the end of the directories you want to copy. For example:
```
/home/vasa1/Documents**/**
```
[/LIST]
With that in mind you can run something like this:
```
rsync -avrs --delete --files-from=/home/vasa1/Desktop/Include / /media/EC82B9BF82B98E98/Testing/
```

Since you loose several Linux attributes when copying files from an ext3/4 filesystem to a ntfs, you have to except at least a warning (ntfs doesn't support permissions, ownership and some filename sensitive issues).

To redirect all output from the command to a file (including errors), add this at the end of the command:
```
 &> rsync.log
```
When re syncing your files to the external disk, you may encounter a situation in which all files are copied again, even though they hasn't been modified. This is because ntfs handles the modification times a little more relax.

To deal with this add the option --modify-window=1 to adapt to ntfs' system.

I hope this helps,
Regards.

---

### Post by vasa1 on 2011-09-25
> **papibe said:**
> ...
I hope this helps,
Regards.

Very helpful indeed :)

I'm marking this as Solved but I have one additional question ... since you mentioned the difference between ntfs and ext3/4, what about FAT32, which I presume is the default format of a pendrive?

Edit: got the answer here:
> --modify-window
When comparing two timestamps, rsync treats the timestamps as being equal if they differ by no more than the modify-window value. This is normally 0 (for an exact match), but you may find it useful to set this to a larger value in some situations. In particular, when transferring to or from an MS Windows FAT filesystem (which represents times with a 2-second resolution), --modify-window=1 is useful (allowing times to differ by up to 1 second).

---

### Post by papibe on 2011-09-25
FAT has 2 more issues:
[LIST]
[*]Absolute case insensitive, so you may loose files while copying. For example, if you have files in the same directory named:
```
Hello.txt
hello.TXT
```
One of them will be overwritten and lost. Although I haven't tried it, I think the option --backup can help in this case, since instead of overwrite the files creates backup copies. In this example, would be:
```
HELLO.TXT~
```
[*]4Gb file size limit.
[/LIST]
Good Luck!
Regards.

---

### Post by vasa1 on 2011-09-25
> **papibe said:**
> FAT has 2 more issues:
[LIST]
[*]Absolute case insensitive, so you may loose files while copying. For example, if you have files in the same directory named:
```
Hello.txt
hello.TXT
```
One of them will be overwritten and lost. Although I haven't tried it, I think the option --backup can help in this case, since instead of overwrite the files creates backup copies. In this example, would be:
```
HELLO.TXT~
```
[*]4Gb file size limit.
[/LIST]
Good Luck!
Regards.

Thanks again! I hope I don't have to worry about the first because I'm the only user. But now I'll be doubly careful about how I name things and I don't do multimedia stuff so the 4GB file size also won't be a concern.

---

