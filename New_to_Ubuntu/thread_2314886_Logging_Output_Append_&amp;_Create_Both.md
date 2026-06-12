---
title: "Logging Output: Append &amp; Create Both"
date: 2016-02-24
forum: New to Ubuntu
---

### Post by kazz2 on 2016-02-24
I'm creating a backup log for the two rsync commands I'm using to backup my two shares to an external drive. The rsync command is working fine. I just want it to output to a text file. I'd like it to append to the file if it exists or to create it if it doesn't exist.

From my very brief research I need something akin to ' >>/var/log/dirname/filename' appended (after a space) after the rsync command. However, when I run that it tells me that the file I'm outputting to doesn't exist. I'm using sudo for the rsync, so it's not a matter of rights. Something tells me that I need an additional parameter/symbol in order to tell the system to create the file if it doesn't exist.

Input? Thanks!

---

### Post by mcgess on 2016-02-24
Hi kazz2

Does the directory "/var/log/dirname/" which is to contain the output file "filename" already exist?
rsync will not create new directories for the redirected >> output

Martin

---

### Post by kazz2 on 2016-02-24
Yes, the folder exists. Are you saying the >> append will create the file if it doesn't exist? Or am I looking at a different command line option or even a conditional statement?

---

### Post by mcgess on 2016-02-24
The >> should create the file if it doesn't exist and you have the permissions, I'm not sure if the sudo applies also to the redirected output. You could try piping to tee

```
sudo rsync ... | sudo tee -a /var/log/directory/file
```

To log warning and error output as well use 2>&1 to have those piped to the tee command as well

```
sudo rsync ............ 2>&1 | sudo tee -a /var/log/directory/file
```

---

### Post by kazz2 on 2016-02-25
Sorry but life interrupted my sysadmin work/training!

Yes, I tested this and found that >> will create the file if it doesn't exist. So perhaps you're correct that the sudo won't apply to the output. Thanks for the tip on tee! I'll look into this further later today.

---

