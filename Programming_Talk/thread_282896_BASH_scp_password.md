---
title: "BASH: scp password"
date: 2006-10-23
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-23
Hello, all.

I want to put the scp command into a script to transfer a directory to a computer over the Internet.

so, it looks something like this:

scp -r /home/directory thomasaaron@<public-ip-address>:/home

Is there a way to automatically send the password for the public ip so that I do not have to manually enter it?

I tried the -B option, but that ends up killing the connection.

Thanks,
Tom

---

### Post by -J- on 2006-10-23
You can create public ssh keys to allow a password-less login.

For instructions look at the SSHHowto:
[https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30](https://help.ubuntu.com/community/SSHHowto#head-1ff9e61cfd81e9f741920b6920af8a85f7bddb30)

---

### Post by thomasaaron on 2006-10-23
Thank you. I'll have a look-see!

---

### Post by frenchn00b on 2010-05-30
is there a program that does that automatically ?

---

### Post by frenchn00b on 2010-05-30
> Step #1: Generate DSA Key Pair

Use ssh-keygen command as follows:
$ ssh-keygen -t dsa
Output:

Enter file in which to save the key (/home/vivek/.ssh/id_dsa):  Press [Enter] key
Enter passphrase (empty for no passphrase): myPassword
Enter same passphrase again: myPassword
Your identification has been saved in /home/vivek/.ssh/id_dsa.
Your public key has been saved in /home/vivek/.ssh/id_dsa.pub.
The key fingerprint is:
04:be:15:ca:1d:0a:1e:e2:a7:e5:de:98:4f:b1:a6:01 vivek@vivek-desktop

Caution: a) Please enter a passphrase different from your account password and confirm the same.
b) The public key is written to /home/you/.ssh/id_dsa.pub.
c) The private key is written to /home/you/.ssh/id_dsa.
d) It is important you never-ever give out your private key.
Step #2: Set directory permission

Next make sure you have correct permission on .ssh directory:
$ cd
$ chmod 755 .ssh
Step #3: Copy public key

Now copy file ~/.ssh/id_dsa.pub on Machine #1 (tom) to remote server jerry as ~/.ssh/authorized_keys:
$ scp ~/.ssh/id_dsa.pub [email]user@jerry:.ssh[/email]/authorized_keys
Command to type on your remote server called jerry

Login to your remote server and make sure permissions are set correct:
$ chmod 600 ~/.ssh/authorized_keys
Task: How do I login from client to server with DSA key?

Use scp or ssh as follows from your local computer:
$ ssh user@jerry
$ ssh [email]user@remote-server.com[/email]
$ scp file user@jerry:/tmpworking

---

### Post by geirha on 2010-05-30
> **frenchn00b said:**
> is there a program that does that automatically ?

You've already made the keys, but for future reference:

Applications -> Accessories -> Passwords and encryption keys

That one will let you create a key-pair, and add it to autorized_keys on the server fairly easily.

---

### Post by ju2wheels on 2010-05-31
ssh-copy-id will automatically push your key out to any server you specify after you have generated your keys.

---

### Post by glitch323 on 2010-09-21
I wrote a simple script to transfer a tarball from one server to another.  I have also generated a key pair and tested it.  Everything works great until I put the scp command in the script, for some reason, it wants me to type a password, but when it's not in a script, it works fine.  Has anyone else had trouble with this?  
The rest of the script works, and it's set to run in the middle of the night because it needs to disable a service, backup the file, transfer the file, then restart the service.  It runs through the whole script, but when I check the other server, nothing is there.  So I've tried it during the day so I could see what's happening, and that's when it asks for a password.  I can run the same scp command outside the script and I have no problems...  Any ideas?

---

### Post by soltanis on 2010-09-21
So then everything is not working. Just a suggestion, this sounds like a thread that might want its own topic instead of resurrecting an old one -- I think it throws people off when you're reading about something from a few months/years ago and then all of a sudden someone tacks a new question on at the end.

Can you verify that when you run scp from just a terminal it doesn't ask you for a password?

---

### Post by glitch323 on 2010-09-21
> **soltanis said:**
> So then everything is not working. Just a suggestion, this sounds like a thread that might want its own topic instead of resurrecting an old one -- I think it throws people off when you're reading about something from a few months/years ago and then all of a sudden someone tacks a new question on at the end.

Can you verify that when you run scp from just a terminal it doesn't ask you for a password?
Well, everything except scp works :) - Also, sorry about bringing a thread back to life, I was reading and it was similar.  Anyways, I have verified that the scp command works (the same command that I use in the script) scp filename username@ipaddress:/destination/path

---

### Post by conundrumx on 2010-09-21
> **glitch323 said:**
> Well, everything except scp works :) - Also, sorry about bringing a thread back to life, I was reading and it was similar.  Anyways, I have verified that the scp command works (the same command that I use in the script) scp filename username@ipaddress:/destination/path

Are you calling the script as a different user than the one you generated the keypair for?

---

### Post by glitch323 on 2010-09-22
> **conundrumx said:**
> Are you calling the script as a different user than the one you generated the keypair for?
The script is run under the only account I have created, which has admin privileges using sudo.  The script does use sudo for some commands, and I have tried using the scp command with and without sudo, it still wants the remote users password.

I should also add the part of the script that fails:
[FONT=&quot]scp $FILENAME adminuser@$REMOTESERVER:/data/backup

I have set the FILENAME and REMOTESERVER variables above, they do work in other parts of the script.  I should also note that I have tried without variables to rule out me making a programming mistake.
[/FONT]

---

### Post by conundrumx on 2010-09-22
> **glitch323 said:**
> The script is run under the only account I have created, which has admin privileges using sudo.  The script does use sudo for some commands, and I have tried using the scp command with and without sudo, it still wants the remote users password.

I should also add the part of the script that fails:
[FONT=&quot]scp $FILENAME adminuser@$REMOTESERVER:/data/backup

I have set the FILENAME and REMOTESERVER variables above, they do work in other parts of the script.  I should also note that I have tried without variables to rule out me making a programming mistake.
[/FONT]

Okay, just for your information, any process run with sudo is run as root, so SSH key authentication based on your user account  would not work.

If the script is running as the same user as the command has and that worked, there's no reason for the script not to; but you already knew that.  I would suggest making a stupid simple script with only the commands "whoami" and your scp command in it to see what goes on there.

---

### Post by SeijiSensei on 2010-09-22
You're sure that the appropriate keys have been added to the authorized_keys files for the remote server's adminuser account?  If you copying to the remote's account adminuser, the contents of your id_rsa.pub file must be in the /home/adminuser/.ssh/authorized_keys file on the remote machine.  

From what you've said, the scp command isn't running with sudo but as an ordinary user.  If that's not true, and it's running as root with sudo, you'll need to create a keypair for /root and add that to the remote authorized_keys file.  Just run "sudo ssh-keygen"; it will write the results to /root/.ssh/.  Afterward, when you're copying the key to the remote authorized_keys file, you'll need to be root to view that directory as well.

---

### Post by dwhitney67 on 2010-09-22
> **glitch323 said:**
> ... The script does use sudo for some commands...
Either run the entire script as sudo, or don't use sudo at all.  In other words, never embed 'sudo' statements within a script.

Also, the term '*adminuser*' is inappropriate, since there is only one admin account per system... it is the **root** account.

A regular user may be afforded admin privileges when using sudo, but in such case, they cease to be the regular account and become root upon the successful entry of their password.

And as Conundrumx stated previously, any command run using sudo is in effect being run as root.  Be very careful as to what you are doing, and make sound judgments as to whether running something as root is necessary.

---

### Post by glitch323 on 2010-09-22
> **conundrumx said:**
> Okay, just for your information, any process run with sudo is run as root, so SSH key authentication based on your user account  would not work.

If the script is running as the same user as the command has and that worked, there's no reason for the script not to; but you already knew that.  I would suggest making a stupid simple script with only the commands "whoami" and your scp command in it to see what goes on there.
Ahh, I knew it was something simple!  I created a simple test script like you said, and it worked fine.  So I tried mine, of course it didn't work.  I checked the permissions, and changed the permissions to match my test script, and now it works!  I really appreciate your help with this, it was driving me crazy trying to figure out why it wouldn't work.  I'm assuming it wasn't working because it was calling the script as root, and the shared key was created as a regular user, not root.  So you were right Conundrumx and SeijiSensei, thanks again!

---

### Post by glitch323 on 2010-09-22
> **dwhitney67 said:**
> Either run the entire script as sudo, or don't use sudo at all.  In other words, never embed 'sudo' statements within a script.

Also, the term '*adminuser*' is inappropriate, since there is only one admin account per system... it is the **root** account.

A regular user may be afforded admin privileges when using sudo, but in such case, they cease to be the regular account and become root upon the successful entry of their password.

And as Conundrumx stated previously, any command run using sudo is in effect being run as root.  Be very careful as to what you are doing, and make sound judgments as to whether running something as root is necessary.
Good to know, I do have sudo inside the script, which I should remove.  Thanks for the tip.

---

### Post by glitch323 on 2010-09-22
Ok, I removed sudo from the script, but I need it to backup the a folder using tar.  I guess I should set the permissions on that folder so that it can be backed up without the root account.  Either that or generate a keypair under root, but that seems like a bad idea (I could be wrong though).

---

### Post by dwhitney67 on 2010-09-22
> **glitch323 said:**
> Ok, I removed sudo from the script, but I need it to backup the a folder using tar.  I guess I should set the permissions on that folder so that it can be backed up without the root account.  Either that or generate a keypair under root, but that seems like a bad idea (I could be wrong though).

You are correct; it is a bad idea.  Access to the root account should always be preceded with a challenge (ie password).

Using the 'tar' command itself does not require root privileges, unless you are attempting to access (read or write) a directory for which the regular-user does not have read/write permissions.

Can you please indicate which directory you need to backup or write to?

---

### Post by glitch323 on 2010-09-22
I have an Openfire server, so I'm backing up it's integrated database, which is a simple backup of one folder.  It will backup the embedded-db folder, and put it in my home directory under a folder named backup.  The only other issue I have is stopping and starting the openfire service without using sudo in the script.

Edit:
Just to be clear, I was having trouble with the backup folder itself in my home directory, so I changed the permissions on that folder so that tar can write to that folder.  Starting and stopping the services is the tricky part for me now, because if I run this script as root, it won't copy the backup over to the other server, because I don't have a keypair under the root account.  If I run the script as the regular user, I don't think I can stop the Openfire service to copy the database folder correctly.

---

### Post by dwhitney67 on 2010-09-22
I personally don't use OpenFire, much less know anything about it.

I do however know about file and directory permissions.  Can you be specific as to the location of the 'embedded-db' directory, and what the permissions are on such.

As for starting/stopping the server, is it necessary?  If it is, put the steps in your script.  Run your script as sudo.  The script should look something like this:
```

#!/bin/bash

# stop server
...

# create tar-ball
...

# send tar-ball to grunt-user on remote system
# This ensures that the command runs as gruntuser, not root!
#
su -c "scp /path/to/tarball.tar gruntuser@remotehost:backup" gruntuser

# start server
...

```
Run the script as:
```

sudo ./script

```

---

### Post by glitch323 on 2010-09-22
> **dwhitney67 said:**
> I personally don't use OpenFire, much less know anything about it.

I do however know about file and directory permissions.  Can you be specific as to the location of the 'embedded-db' directory, and what the permissions are on such.

As for starting/stopping the server, is it necessary?  If it is, put the steps in your script.  Run your script as sudo.  The script should look something like this:
```

#!/bin/bash

# stop server
...

# create tar-ball
...

# send tar-ball to grunt-user on remote system
# This ensures that the command runs as gruntuser, not root!
#
su -c "scp /path/to/tarball.tar gruntuser@remotehost:backup" gruntuser

# start server
...

```Run the script as:
```

sudo ./script

```
It may not be necessary because the backup occurs in the middle of the night, and no one is using the server at that time.  I just wanted to make sure I always had a good backup in place.  I added the su -c part to my script and it worked flawlessly!  I really appreciate your help on this!  The entire script works now without any errors.

---

### Post by glitch323 on 2010-09-22
Oh, the embedded-db folder was not the problem, it was my backup folder on my home folder.  I gave that folder read/write for everyone, which may not be the best solution, I just wanted to make sure it will work.  I used "sudo chmod 777 backup/", the owner and group is the user, not root.

I've fixed the permissions on that folder to 755.  Thanks again dwhitney67!

---

### Post by conundrumx on 2010-09-22
If a script needs to do things at the root level there's no reason not to run it at the root level.  Throw it in cron for root and never think about it again.  You just need to be certain that a) it won't choke and do anything bad, and b) it really does need to be root.

---

### Post by dwhitney67 on 2010-09-22
> **conundrumx said:**
> If a script needs to do things at the root level there's no reason not to run it at the root level.

What?  What you stated above makes no sense.

> **conundrumx said:**
> 
Throw it in cron for root and never think about it again.  You just need to be certain that a) it won't choke and do anything bad, and b) it really does need to be root.
Regular users can also setup cron jobs; not just root.

---

### Post by SeijiSensei on 2010-09-22
If all you want to do is image a directory to another location, either on the local filesystems or over the network, I suggest you consider rsync.  ("sudo apt-get install rsync" does the trick.) 

To maintain a mirror image of /home/me/myimportantdata on another machine you would use:

cd /home/me
rsync -av myimportantdata backupuser@backuphost:/home/backupuser/backups

and the contents of myimportantdata will be transferred and appear as ~/backups/myimportantdata in the home directory of backupuser on backuphost.  rsync uses ssh to make this transfer; you can thus avoid being prompted for a password by setting up shared keys as described earlier.  The safest solution is to make sure backupuser@backuphost has the public key for the sending user, me@localhost, in /home/backupuser/.ssh/authorized_keys on backuphost.

The destination need not be a remote system.  You could image your home directory to a local mass storage device on /media/mybigdisk like this:

cd /home
rsync -av username /media/mybigdisk/backups

This would create the backups/username directory on /media/mybigdisk if it doesn't already exist, then synchronize their contents. 

Why choose rsync over alternative solutions?  Because it's the most efficient and most versatile backup program written for the *nix command line.  After the initial transfer of the contents of /home/me/myimportantdata, rsync only sends *new or altered files*.  What's more, it many cases it can send only the differences between the local and remote files by way of the command-line tool "diff".  ("man diff" for details).  I think current versions might even be able to work the same magic on binary blobs, but don't hold me to that.

Once you install rsync, run "man rsync" and read its excellent documentation.

---

