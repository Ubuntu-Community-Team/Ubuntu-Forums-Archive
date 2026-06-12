---
title: "File won't copy"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by StrangerSa on 2012-11-23
Hi Guys

I installed Ubuntu onto a PC with a new HD, Installation was fine everything went smooth.

I now try to copy files from the server and all goes well until it actually try's to copy, then it just hangs and the file don't come over.

Any help appreciated

thanks.

---

### Post by singedwings on 2012-11-23
Have you tried using the terminal to copy, it will give you a better idea what is not working. If the permissions are wrong you will need to use sudo```
sudo cp -v -R /path/to/file/* /path/to/copy/to
```This will try and copy everything, including subfolders and contents. The '-v' will tell you if each file is successfull or not!

---

### Post by slickymaster on 2012-11-23
Are you trying to copy the files from a remote server? If so, just run this command: 

```
scp username@server:/home/username/file_name /home/local-username/file-name
```

---

### Post by StrangerSa on 2012-11-23
Thanks guys will give these a try. it is a bit weird as I can do it from this PC but not the new install.

Here are the screen shot of what I want to copy. It is the whole cabinet that I want

---

### Post by slickymaster on 2012-11-23
There is no file size limitation in Linux, so that's not the problem.

Maybe your system administrator imposed limitation on your account for file size creation. Just run ulimit command to find out file size limitation.

```
$ ulimit -a
```

_**Output:**_
```
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
max nice                        (-e) 0
file size               (blocks, -f) 5000
pending signals                 (-i) unlimited
max locked memory       (kbytes, -l) unlimited
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) unlimited
max rt priority                 (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 2047
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
```

The above output clearly stat that this user can create file size upto 5MB limit. To change this limit or if you do not wish to have a limit you can edit your **/etc/security/limits.conf** file 

(login as the root):
```
# vi /etc/security/limits.conf
```

Look for your username and fsize parameter. Delete this line or set new parameter. For example consider following entry where I am setting new file size limit to 1 GB:

```
vivek       hard  fsize  1024000
```

Save the changes. Log out and log back in for the changes to take effect.

Now your limit is 1GB file size. If you do not want any limit remove fsize from /etc/security/limits.conf.

---

### Post by StrangerSa on 2012-11-26
Thank you, I tried that, it reported unlimited. Maybe I must try to sync instead of copy.

---

### Post by dannyboy79 on 2012-11-26
its irrelevant whether you're "syncing" or "copying". What directory are you trying to save to on your local machine? Also, how are you logged into the remote server? Over ftp, ssh or how? What is the command you used to mount the remote share?

---

### Post by slickymaster on 2012-11-26
It's weird and I can't imagine what could be causing this.

Try to sync and see what happens. You may get some clues about what may be causing this.

---

