---
title: "gaining &quot;permission&quot; to access my old files"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by hardknocks on 2012-09-03
Hi all,
  
I’m totally new to Linux and to the forum. I’m using Ubuntu 12.04.1 as a way to boot a failing hard drive on a Macbook Pro.  I hope to be able to use the Ubuntu interface to backup some important files on the old hard drive before installing a new one. The problem is that when I go the folders where my data is I cannot open the folders because I “don’t have permission.”  (Obviously I know my Mac OS X password, but I’m running Ubuntu to bypass the corrupted OS X. As a result the system doesn’t know I’m the same person). Any suggestions to this problem?

  Also, I should mention that I am just running Ubuntu off the cd drive. I don’t want to install it because I don’t want to overwrite some of the files I’m trying to recover. So whatever possible solution I pursue has to be doable from the cd. 
  
Thanks for any assistance you might be able to provide.

---

### Post by NikTh on 2012-09-03
Hello , 
open a terminal (ctrl+alt+t) and open nautilus file manager with administrative privileges 

```
gksudo nautilus
``` 

Hopefully you will gain permissions to all of your files.

Thanks

---

### Post by hardknocks on 2012-09-03
NikTh,
Thanks for the response. However, it brings to mind some other questions. 
1) Should I first create a username and password in ubuntu? (After all, won't the program prompt me for my password after entering the "gksudu nautilus" command?
2) Can I create a username and password in ubuntu when I am just running it off the disk and not installing it?
Thanks again.

---

### Post by HermanAB on 2012-09-03
...or you can do chown -R on the old disk.

---

### Post by MG&amp;TL on 2012-09-03
> **hardknocks said:**
> NikTh,
Thanks for the response. However, it brings to mind some other questions. 
1) Should I first create a username and password in ubuntu? (After all, won't the program prompt me for my password after entering the "gksudu nautilus" command?
2) Can I create a username and password in ubuntu when I am just running it off the disk and not installing it?
Thanks again.

1) You should, normally, but from the live cd you should be fine. Possibly. It might give you a prompt, in which case type nothing, or it might not prompt you and just open the window.

2) I don't think so, no. At least not permamently.

Strange that you're having this problem. From a live cd you should have permission to do everything to any filesystems.

---

### Post by hypnot0ad on 2012-09-03
Off the livecd you should already be root.

---

### Post by MG&amp;TL on 2012-09-03
> **hypnot0ad said:**
> Off the livecd you should already be root.

```
ubuntu@ubuntu:~$
```

Although "sudo" doesn't ask for a password, if that's what you mean.

---

### Post by hardknocks on 2012-09-03
Thanks for the advice everyone. I tried "gksudo nautilus" and it allowed me to see the contents of the folders (which I could not do before), but it did not allow me to copy the folder to a backup drive because I still don't have permission. 

So I thought I'd try the "chmod" command. 

Question: if the folder I want to change permissions on is called "desktop" (located at Macintosh HD/Users/Carmen/Desktop) what would the exact command be?
  

Would this work?
  chmod -R /Macintosh HD/Users/Carmen/Desktop /*
  

Again, all I’m trying to do is backup some files on a failing hard drive. Thanks for your advice and patience.

---

### Post by NikTh on 2012-09-03
Hello , 

chmod will allow you to set permissions in a folder / file . Permissions such Read - Write - Execute. 

To set permissions to a folder I think you must be the owner of the folder. (or file) . 

Why nautilus doesn't allow you to copy ?  Maybe is not allow to copy TO the destination folder ? 

Try to create a new folder with mkdir command 

```
sudo mkdir /destination/folder/for backup/ 
```then try to copy everything with rsync command 

```
sudo rsync -avS /target/folder/ /destination/folder/for backup/ 
```give here any errors . 

Thanks

---

### Post by hypnot0ad on 2012-09-03
> **MG&TL said:**
> ```
ubuntu@ubuntu:~$
```

Although "sudo" doesn't ask for a password, if that's what you mean.

My apologies, obviously mistaken

---

