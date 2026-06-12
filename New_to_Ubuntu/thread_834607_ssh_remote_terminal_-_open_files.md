---
title: "ssh remote terminal - open files"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by jcr1 on 2008-06-19
Hi all,

just got remote control working using terminal and ssh. This is fantastic, can browse and control whole system remotely.

BUT, lets say I am using it to look thru files, say images or text files or music files, how can I remotely just 'open' these files?

eg I am remote controlling my server over the internet, I can cd to a directory that contains an image... how would i view that image?

I know i can use an ftp client to download stuff, but was just wondering if it could be done from command line, if i just wanted to edit a text file without having to download via ftp, edit locally then reupload.

---

### Post by wormser on 2008-06-19
To edit a text file in the shell use nano or vi.  Nano is easier to use.  

```
nano filename
```

---

### Post by RomeReactor on 2008-06-19
> **jcr1 said:**
> eg I am remote controlling my server over the internet, I can cd to a directory that contains an image... how would i view that image?

Hi. Haven't used this with ssh, but try zgv:
```
sudo aptitude install zgv
```
then navigate to the folder containing the image and:
```
zgv FILENAME
```

---

### Post by bodhi.zazen on 2008-06-19
> **jcr1 said:**
> Hi all,

just got remote control working using terminal and ssh. This is fantastic, can browse and control whole system remotely.

BUT, lets say I am using it to look thru files, say images or text files or music files, how can I remotely just 'open' these files?

eg I am remote controlling my server over the internet, I can cd to a directory that contains an image... how would i view that image?

I know i can use an ftp client to download stuff, but was just wondering if it could be done from command line, if i just wanted to edit a text file without having to download via ftp, edit locally then reupload.

Method 1 :

You have to have a viewer / player application installed on the server.

You then use -X to forward X apps :

```
ssh -X user@server
```

You then user the application to open the file or image.

For text files, nano or vim as suggested by wormser

for images, say you use eog :

```
eog image.jpg
```

I am not sure you can forward audio directly over ssh..

================

Method 2 :

The other option is to mount a remote directory with sshfs

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

[http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/](http://ubuntu-tutorials.com/2007/01/02/mount-remote-directories-securely-with-ssh-ubuntu-6061-610/)

you can then view / edit / play files as if they were on a local drive.

---

### Post by Dr Small on 2008-06-19
> **bodhi.zazen said:**
> 
I am not sure you can forward audio directly over ssh..

You are correct, but I would love to be able to do this! ;)

---

### Post by glotz on 2009-02-05
Isn't that possible now with pulse audio? (the audio part)

---

