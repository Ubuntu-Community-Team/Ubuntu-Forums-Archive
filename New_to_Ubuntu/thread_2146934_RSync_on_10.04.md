---
title: "RSync on 10.04"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by rockymin on 2013-05-20
Hello,
I have been tasked with setting up a backup of an Ubuntu 10.04 server to another Ubuntu 10.04 server. The second would be used in the event the first one fails. 
I really don't know or understand that much with Linux, I use Webmin on both servers to administer them. In my research, I see that RSync is what people use to accomplish this. I've been reading about rsync but don't understand how to set up the servers to talk to each other. I've never used SSH.
Is there an easy (and easy to understand) way to get this running? I'm a longtime Windows engineer, and I am having a very hard time trying understand Linux. And I am very nervous about using all these commands, I fear making a typo and wiping the system and not know how to fix it.

Thanks in advance for any help,
Rockymin

---

### Post by sudodus on 2013-05-20
Welcome to the Ubuntu Forums :-)

I'm helping people with the desktop flavours of Ubuntu, but I'm not a server guy. Anyway, I can help you get started, because I use ssh and rsync myself (in simple ways). I think you can find good tutorials on the internet, if you search for ***ssh tutorial*** and ***rsync tutorial***.

You can also read the manual pages

```
man ssh
``` and ```
man rsync
```

The rsync manual is well written and contains several examples. Read the following link to learn how to set up an ssh server.

[https://help.ubuntu.com/10.04/serverguide/openssh-server.html](https://help.ubuntu.com/10.04/serverguide/openssh-server.html)

---

### Post by dan08 on 2013-05-20
Do you want to backup the files to a folder so you have them if the other drives fail? Or are you trying to basically make a clone of the server so you can switch over seamlessly?

---

### Post by rockymin on 2013-05-20
> **dan08 said:**
> Do you want to backup the files to a folder so you have them if the other drives fail? Or are you trying to basically make a clone of the server so you can switch over seamlessly?

Pretty much just trying to make a clone.  I'm trying to sync the www directories and mysql backups.  I have been testing out with a test directory on each server.  I am running sudo rsync -r /rtemp/* user@remote:/rtest

That seemed to work ok, copied everything over no problem.  The only thing was the password prompt for the remote server.  I want to run this nightly, so is there a way to add the password to the command with a switch or something?  The rsync is between two local servers, not going over the internet, so I don't want to use ssh or anything like that.  Just a simple copy job.

Thanks again.

---

### Post by dan08 on 2013-05-20
That automated password prompt gave me trouble for the longest time when doing a similar thing. If you are going to put this in a bash script, you can put the password in there somehow but it's frowned upon. Can you run the script from the remote server, so you are pulling the data instead of pushing it, if that makes sense? I think if you do it that way, you won't need a password for the machine you are reading from. You can run the script from sudo's crontab on the destination server to automate it nightly.

Your new command would simply swap the machines ```
 sudo rsync -r user@remote:/rtest/* /rtemp/
```

Also look in the -delete option for rsync. It sounds a little scary, like you might wipe out data, but this option allows rsync to delete files in destination that were deleted at the source.

---

### Post by rockymin on 2013-05-20
> **dan08 said:**
> That automated password prompt gave me trouble for the longest time when doing a similar thing. If you are going to put this in a bash script, you can put the password in there somehow but it's frowned upon. Can you run the script from the remote server, so you are pulling the data instead of pushing it, if that makes sense? I think if you do it that way, you won't need a password for the machine you are reading from. You can run the script from sudo's crontab on the destination server to automate it nightly.

Your new command would simply swap the machines ```
 sudo rsync -r user@remote:/rtest/* /rtemp/
```

Also look in the -delete option for rsync. It sounds a little scary, like you might wipe out data, but this option allows rsync to delete files in destination that were deleted at the source.

Nope, still came up with the prompt.

---

### Post by dan08 on 2013-05-20
Did it prompt for the local machine's password or the remote machine?

---

### Post by rockymin on 2013-05-20
It was a prompt for the remote password.

---

### Post by dan08 on 2013-05-20
Sounds like you want to set up ssh between the two machines so that you don't need use a password. Maybe this with help: [http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/](http://www.thegeekstuff.com/2008/11/3-steps-to-perform-ssh-login-without-password-using-ssh-keygen-ssh-copy-id/) .

I have been meaning to do this myself, but never had a good reason or the time to play around with it. Good Luck.

---

### Post by supremedalek on 2013-05-20
I believe that you want to use public/private key pair authentication instead of password. You create the pair (using ssh_keygen), then copy the public key to the machine you are rsyncing to. Then you can do stuff like

> rsync -r -e 'ssh -i /path/to/private/key' user@remote:/rtest/* /rtemp/ 

---

### Post by rockymin on 2013-05-20
> **supremedalek said:**
> I believe that you want to use public/private key pair authentication instead of password. You create the pair (using ssh_keygen), then copy the public key to the machine you are rsyncing to. Then you can do stuff like

Nope, still prompted for a password, as well as a passphrase for ssh, even though I didn't set a passphrase.

---

