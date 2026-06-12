---
title: "Howto: Read Only SSHFS file share"
date: 2008-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kuja on 2008-03-05
Well, I decided to figure out a way to do things and went through a rollercoaster ride trying to figure out how to do things right, and what to do them with. I didn't want to use SMB, and NFS seemed unwieldly and complicated to set up, so I looked for other options. I decided to try to force SSH to work for me. Here's what I came up with, and even though its a bit lengthy I hope it proves useful to somebody. 

First you'll need to create a new user and group, for purpose of example we'll call the user and group share, while we're at it, lets install openssh-server also.For purpose of example we'll call your main user bob, and his computer bob-desktop. 

```
sudo adduser --uid 5555 share
sudo adduser bob share
sudo apt-get install openssh-server sshfs
```

Next you'll want to move the files you want to have shared into the newly created homefolder. After moving the files to the share (probably requiring root privileges to do so), you'll need to change some permissions on the files.

```
sudo chmod 750 /home/share
sudo chown -R bob:share /home/share/*
sudo find /home/share -type d -execdir chmod 750 {} \+
sudo find /home/share -type f -execdir chmod 640 {} \+

```

Now that we have the files in place and their permissions straight, we can get to work on the ssh end of the setup. 

First thing you'll need to do is generate keys for connecting to the share user on the **guest** computer(s) To keep things straight, we'll call the guest computer joe-desktop, and the user (....) joe.

```
ssh-keygen -t dsa
``` When it asks you where you want to put the file, put it at ~/.ssh/id_share
When it asks for the passphrase, leave it blank, this comes into play later.

Now, you need to make it so share@bob-desktop recognizes your key, so you do this:
```
ssh-copy-id -i ~/.ssh/id_share share@bob-desktop
```
Now try logging in and see if it requires a password or passphrase, if it fails or requires a password then something is definitely **wrong**. Otherwise, you're free to continue.
```
ssh share@bob-desktop
```

Now, you need to make sure sshfs is installed on joe-desktop. 
```
sudo apt-get install sshfs
```

And to create the mountpoint:
```
sudo mkdir /media/bobs_share
```
and add this line to your /etc/fstab file:
```
sshfs#share@bob-desktop: /media/bobs_share fuse ro,nosuid,nodev,max_read=65536,allow_other,IdentityFile=/home/joe/.ssh/id_share 0 0
```
and turn on keep alive:
```
sudo su -c 'echo "ServerAliveInterval 120" >> /etc/ssh/ssh_config'
```

Mount it 
```
sudo mount /media/bobs_share
```

and you should be set.

---

### Post by panki on 2008-03-13
I think if you type fish://<user>@<server-ip>:<port>/ on konqueror it will give you access to any folder on the remote machine (permissions controlled)

---

### Post by kuja on 2008-03-13
Of course you can, but you can't use fish:// to mount it like an ordinary file system (for transparent access by all programs, and anytime access without any sort of manual login every time you need to access something, also permissions controlled).

---

