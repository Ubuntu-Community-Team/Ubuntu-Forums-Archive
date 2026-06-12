---
title: "How to copy file from server to my local computer?"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by littlewenwen on 2012-11-29
Dear All,

Suppose I am now sitting in front of my home computer, and I typed following commands to connect to the server at school:

```
littlewenwen@homemachine:~$ ssh littlewenwen@schoolserver
```

After I gave the password, I am successfully connected to the server, as shown below:

```
[littlewenwen@schoolserver ~]$
```

Now, I want to copy a file from the server to my local machine, what command can do this?

---

### Post by sandyd on 2012-11-29
> **littlewenwen said:**
> Dear All,

Suppose I am now sitting in front of my home computer, and I typed following commands to connect to the server at school:

```
littlewenwen@homemachine:~$ ssh littlewenwen@schoolserver
```

After I gave the password, I am successfully connected to the server, as shown below:

```
[littlewenwen@schoolserver ~]$
```

Now, I want to copy a file from the server to my local machine, what command can do this?
replace ssh with scp

for example, if the file is in your home directory, and is called littlewenwen.zip

```

scp littlewenwen@schoolserver:littlewenwen.zip ./littlewenwen.zip

```

The file will be created in your current directory (you can set it by changing ./littlewenwen.zip to something else)

if its not, just supply the full path.
For example, 

```

scp littlewenwen@schoolserver:/home/littlewenwen/littlewenwen.zip ./littlewenwen.zip

```

you can do it with sftp as well

```

sftp littlewenwen@schoolserver

```
you use ls, and cd to browse.

When you find your file, 
```

get *filename*

```

You can use the complete full path as well.

---

### Post by s3a on 2012-11-29
You can either ssh into the server and use scp to send it securely to your computer or you can directly use scp (without needing the ssh command) to send it directly to you.

Example with direct scp (no ssh command):
```
scp -vrC name_of_server@ip_address_of_server:/the/directory/of/file/filename.fileextension /your/computer/directory/where/you/want/the/file/saved
```

Example with ssh command (I recommend the previous option):
```
ssh littlewenwen@schoolserver
scp -vrC /directory/of/file/on/server/filename.fileextension name_of_your_computer@your_ip_address:/your/computer/directory/where/you/want/the/file/saved
```

---

### Post by SeijiSensei on 2012-11-29
One thing I like about KDE is that it supports SSH-based file access by entering a URL that uses the "fish" protocol.  Entering something like

```
fish://user[:password]@server/some/location
```

into the address bar in Dolphin opens the remote directory in a file manager window.  Depending on permissions I can drag and drop files between the local and remote machines as if they were both local.  If you have set up shared SSH keys, there isn't even a password dialog required.

I use scp and rsync from the command line quite often to move files to a remote server, but being able to do it from within a GUI file manager can sometimes be much more convenient.

---

### Post by s3a on 2012-11-29
SeijiSensei, I feel I should show you this just in case you are interested and haven't seen it before.: [http://en.wikipedia.org/wiki/SSH_Filesystem](http://en.wikipedia.org/wiki/SSH_Filesystem)

---

### Post by agillator on 2012-11-29
For a limited number of files scp (or sftp) is the way to go as described above. However, the need you describe sometimes grows to needing a number of files, more than you can do with wildcards. If you get to that point, be aware there is rsync which will transfer multiple files/directories and mirror directory trees between computers.

---

### Post by littlewenwen on 2012-11-30
Thank you all for great help!

---

### Post by SeijiSensei on 2012-11-30
> **s3a said:**
> url]http://en.wikipedia.org/wiki/SSH_Filesystem[/url]

Yes, I know what sshfs is.  I just find it convenient to be able to set one up "on-demand" from within a file manager application like Dolphin.

---

