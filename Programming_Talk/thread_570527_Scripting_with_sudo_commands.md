---
title: "Scripting with sudo commands"
date: 2007-10-08
forum: Programming Talk
---

### Post by swoosh on 2007-10-08
Hi,

I wish to do these commands in a script

```
sudo mount //servername/shared ~/mount -o dmask=777,fmask=777
cp /home/user/document.pdf ~/mount
sudo umount ~/mount
```

I have tried to make the script runnable without password in sudoers but still it is prompting me for password for the commands.

Have I missed out something?

---

### Post by Tomosaur on 2007-10-08
> **swoosh said:**
> Hi,

I wish to do these commands in a script

```
sudo mount //servername/shared ~/mount -o dmask=777,fmask=777
cp /home/user/document.pdf ~/mount
sudo umount ~/mount
```I have tried to make the script runnable without password in sudoers but still it is prompting me for password for the commands.

Have I missed out something?

Try removing the sudo statements within the script, and just running the script as sudo. When you use the cp statement, just add another line chmodding the document.pdf file to the correct owner and permissions.

---

### Post by Ramses de Norre on 2007-10-08
If you add the script with NOPASSWD to /etc/sudoers you can run the script with sudo without given a passwd but the commands that use sudo inside the script still need one. But because you run the whole script with sudo and thus as root, you can leave out the sudo statements in the script then.

---

### Post by swoosh on 2007-10-08
Hi guys,

Thanks for the reply.

I think removing sudo inside script is working but I am still getting a password response that is willing to accept anything I typed in.

Could it be a Samba setting on my server side?

---

### Post by swoosh on 2007-10-08
Hi,

I could not explain the password when doing a manual run on the script but everything works when I tried the crontab on the script. 

Thank you for the help.

---

