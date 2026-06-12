---
title: "Error when moving files"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by gustasonfrever on 2008-07-30
I just downloaded a torrent onto my desktop. I tried moving it into my music folder and for some reason I was given an error message:

Error while moving "Queen".
There was an error moving the file into /home/justin/Music/My Music.
>Show more details
      Error moving file: Permission denied

Any suggestions?

---

### Post by iaculallad on 2008-07-30
> **gustasonfrever said:**
> I just downloaded a torrent onto my desktop. I tried moving it into my music folder and for some reason I was given an error message:

Error while moving "Queen".
There was an error moving the file into /home/justin/Music/My Music.
>Show more details
      Error moving file: Permission denied

Any suggestions?

On your terminal, issue the command below to give you permission on moving/copying files.

```
gksudo nautilus
```

---

### Post by gustasonfrever on 2008-07-30
justin@justin-laptop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6915): WARNING **: Unable to add monitor: Operation not supported




      
--- Hash table keys for warning below:
--> file:///

(nautilus:6915): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6915): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown


What does this mean?

Now when I move the file I get another error message

Error while copying.
There was an error creating the folder "Queen".
Operation not supported by backend

---

### Post by neurostu on 2008-07-30
You can try moving the files in the terminal...
```

sudo mv <sourcedir>/file <destdir>/file

```
that should do it.

---

### Post by iaculallad on 2008-07-30
Try installing samba/smbfs, as it will probably eliminate the message that prompts when accessing nautilus as a privilege user.

```
sudo apt-get install samba smbfs
```

You might be needing this if you want to share files with windoze.

EDIT: Then after the installation, redo the command below:

```
gksudo nautilus
```

---

### Post by unutbu on 2008-07-30
Sorry, I don't know much about Samba, but this thread might point you in the right direction:
[http://ubuntuforums.org/showthread.php?p=5165646](http://ubuntuforums.org/showthread.php?p=5165646)

---

### Post by gustasonfrever on 2008-07-30
I'm still getting the error message when I move the file however, I am now able to move the file to other places but I can't get it into the my music folder. Is it important that the "my music folder" has a little lock icon in the right hand corner?

---

### Post by cariboo on 2008-07-30
You might want to change the permissions on the folder. Just right click on it and go to permissions and change them so that you can read and write to the directory.

---

