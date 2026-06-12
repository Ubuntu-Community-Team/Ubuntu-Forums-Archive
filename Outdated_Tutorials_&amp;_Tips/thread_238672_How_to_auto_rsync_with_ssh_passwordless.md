---
title: "How to auto rsync with ssh passwordless"
date: 2006-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by patsissons on 2006-08-18
This HOWTO is designed to help those who are looking to backup a directory from their local computer to a remote computer using the power of rsync, the security of ssh, and the ease of automation.  Your local computer will make use of a cron job that will execute the backup as often as you want, behind the scene so that you don't have to worry about your data's saftey.

There will be a quick-start rundown of the steps at the end of this howto.

First we start off by making a public key on the local machine
```
ssh-keygen -t rsa
```
use **-t rsa** unless you plan on accessing a older machine, or rather a machine whose version of openSSH is older.  In most cases you will not have a problem with **-t rsa**.  However, if you do have a problem you can try leaving it out, this will create a **DSA** key instead.  **ssh-keygen** will ask you first where to store the public key.  The default location is usually fine, that is unless you want to manage multiple public keys.  Unless multiple public keys is what you need, simply hit enter to accept the default location.  Next you will be asked for a password.  You must hit enter twice without typing in a password or else every time you use this public key you will have to enter *that* password instead.  This should result in the creation of the key and the public key pair.  If you chose the default values, **~/.ssh/id_rsa** and **~/.ssh/id_rsa.pub**.

Now we need to copy our public key to the remote machine so the remote machine can add it to its list of authorized keys.
```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote_host
```
Of course, you should use your custom public key if you did not use the default name in the previous step.  Also as you would expect, username and remote_host should be replaced by their respective values.  After executing this, it will ask you for your password, this is just the ssh password to the remote machine for the username that you used.  Upon completion, there should be a file on the remote machine **~/.ssh/authorized_keys** that contains the public key that you just generated.

You can test out if you were successful now by ssh'ing to the remote machine, you should no longer be asked for a password.  If this is the case, you are in the clear, otherwise, something has gone wrong.

To setup rsync you will need to make a script that looks something like this.
```

#!/bin/sh
rsync -e 'ssh -p 22' -avzp /some/dir remote_host:/var/backups/some_host

```
The **-e 'ssh -p 22'** is not completely necessary (in fact its very redundant), however, if you are connecting to ssh on a non standard port, you will need to change the **22**.  Otherwise, you can just use **-e ssh** instead.  Again, remember to change the remote_host to the actual hostname of the remote server.  Now depending on how often you want to run this backup, you can either setup a specific entry in the **/etc/crontab** file (this is a little more complicated), or you can just use the pre-built cron directories in ubuntu (cron.hourly, cron.daily, cron.weekly, cron.monthly).  I recommend the second option, since it makes for a very easy setup.  Simply save the script you created inside the desired cron directory, then **chmod +x** the filename that you save it as.  If you wish to test it out, simply execute the script from the console.

Finally, make sure that the directory that you are sending your backups to on the remote server actually exists, otherwise rsync will error out and you will not backup anything.


_Quick-Start_
**On the local machine:**
```

ssh-keygen -t rsa
# hit return three times

ssh-copy-id -i ~/.ssh/id_rsa.pub username@remote_host
# enter your password for username on remote_host

cat > /etc/cron.daily/remote_backup
#!/bin/sh
rsync -e 'ssh -p 22' -avzp /some/dir remote_host:/var/backups/some_host
^D

chmod +x /etc/cron.daily/remote_backup

ssh username@remote_host mkdir /var/backups/some_host

```



**_Final Thoughts_**
I am no rsync expert, nor ssh or cron.  Actually, I learnt most of this stuff in the last couple of hours.  But since there was no tutorial on ubuntu forums, I decided to make my own.  This means that there may very well be a better way to do this.  I wouldn't doubt it for a second.  Also, there may be better flags to include in the rsync script.  If anyone knows anything better to add, please do so as I think this is a somewhat important topic to understand.  To everyone else, I hope this how to is helpful in making your backup automations a breeze :)


--
Pat

---

### Post by JonRohan on 2006-08-30
Just what im after. Thanks :)

---

### Post by claypole on 2006-09-09
Thanks, this is exactly what I needed too! :D

---

### Post by carlossousa on 2006-09-11
hello,

I noticed your nice rsync how-to but I wonder if you could help me out with something. I have 3 servers, pc1, pc2 and pc3.
pc1 has the data, pc2 has a rsync of pc1 done at 11pm every night and I wanted pc3 to only have a "update" of what happens to be different from pc1 and pc2 every night.
What rsync option do I have to activate on pc3 to allow me to store, on a directory name basis of the type "home[dayN-monthM-yearO]" so I would have the likes of a "incremental" daily backup of pc1?

Can you help?
Thanks,

Carlos Sousa

---

### Post by plusbryan on 2008-04-17
My remote server is running on another port, and ssh-copy-id uses a somewhat unintuitive format for specifying ports:

# ssh-copy-id -i ~/.ssh/id_rsa.pub "-p 222 root@server"

---

### Post by novakyu on 2008-11-17
BTW, I just wanted to say that this setup is potentially very insecure, especially if you created a passwordless private key. 

With a passwordless private key, if anyone ever gets a hold of the private key, he will have complete root access to your other server as well.

There's no way to make a passwordless backup completely secure, but at the very least, you should limit the key on the remote server end to allow connection from only the IPs that need to use the key and limit it to only the command it needs to use (rsync). Check the ssh manpage for authorized_keys for more information.

---

### Post by CodeAlias on 2008-12-09
Great post,

I would like to point out to this howto :
[B][URL="http://www.codealias.info/technotes/synchronizing_cvs_repositories_with_rsync"]
Rsync configuration for password-less mirroring over ssh[/URL][/B]

that also describes server side setup.

wrt security issues, I agree with novakyu. An alternative and a bit more secure way to perform password-less rsync would be through kerberized ssh connections.
Instead of using public keys, kerberos allows the rsync client to use renewable tickets to authenticate its self to the rsync server. If an attacker steals the ticket, he will be able to use it only for a short period of time (depending on your configuration), also he will not be able to use it from another machine.

---

### Post by dbrine on 2009-06-27
great guide but I'm getting error (password prompts actually). I followed the guide and created keys on the local and copied the pub key to the server. this is the error I get. Where am I going wrong???

[HTML]dbrine@VM-UServer2:~/.ssh$ sudo ssh-copy-id -i ~/.ssh/id_rsa.pub dbrine@192.168.1.107
dbrine@192.168.1.107's password:
Now try logging into the machine, with "ssh 'dbrine@192.168.1.107'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

dbrine@VM-UServer2:~/.ssh$ ssh dbrine@192.168.1.107
Enter passphrase for key '/home/dbrine/.ssh/id_rsa':
dbrine@192.168.1.107's password:
[/HTML]

---

### Post by Antronin on 2010-03-12
For me it seems, the private key file has to be named .ssh/identity instead of .ssh/id_rsa to work on Ubuntu.

---

### Post by baddnady23 on 2010-03-12
I have actually recently been tinkering with rsync and cron to back up to a remote computer on the local network and have gotten it to successfully run at 2:30 AM every night.  Just some other stuff to throw out there for others:

I am using the 
```
--delete
``` 
option, which is nice depending on what your trying to accomplish.  It will automatically delete anything in the "backup directory" that has been deleted in the directory that your backing up.  Some users may like this, others may not.  

Also, an FYI to others, for some reason I had to use the 
```
--exclude'/.gvfs/'
```
option when backing up /home.  Otherwise rsync seemed to be caught in an endless loop.

I also like having the output saved into a log file in designated directory so that if I want at a later time, I can review what was actually copied or removed.  

My actual command which I have saved to a .sh script is:

```
rsync -av --delete --exclude='/.gvfs/' --log-file=/home/andrew/Logs/rsync/$(date +%Y%m%d)_rsync.log /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_laptop
```

You'll notice the --log-file argument.  It will output it to a file named today'sdate_rsync.log where the today'sdate is in the format 20100311 for easy cataloging.

I also don't have to specify it to use ssh -e because, if I am not mistaken, by telling rsync to copy to a remote location, it defaults to ssh with port 22.  I may be wrong but this is what works for me.

Also be aware that rsync pays particular attention to the / at the end of a path.  If it is there, it will copy only the contents of that directory into the desired location.  If it is not there, it will copy the the actual directory and its contents.  For example:
```
rsync -av [COLOR="Red"]/home/andrew/[/COLOR] andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_laptop
```
copies the contents of my /home to the desired location.  Whereas
```
rsync -av [COLOR="Red"]/home/andrew[/COLOR] andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_laptop
```
copies the actual /andrew folder and its contents to the desired location.

To quickly show my crontab file, I would enter
```
crontab -e
```
which opens my crontab file, looking something like this:
```
# m h  dom mon dow   command

```.  
Explaing the use of CRON is beyond the scope of this thread but for those who are curious about mine, it is:
```
# m h  dom mon dow   command
30 02 * * * /home/andrew/Scripts/backup.sh
```
which allows me to run the backup script above at 2:30 AM everyday when I am soundly sleeping and the computer isn't doing anything else.  

Great tutorial and I hope my two cents will help someone else down the road in return for all the help that I have gotten over the years!

---

### Post by Maverickprowls on 2010-05-04
I'm trying to set up a passwordless backup server for a small number of users.  It's quite important that it runs without any human intervention, so I'm trying to avoid using ssh-agent.  What I'd like to know is, provided I can transport the public keys of the machines physically (i.e. take them to a user's location and copy them from a USB stick), am I right in believing that the connection will still be as secure, end to end, as it would be with password-protected keys?

---

### Post by osomphane on 2010-05-12
I tried this method on lucid 10.04 and it is still asking me for a password. Any ideas? The authorized_keys file on the remote machine appears to have the key copied over correctly.

---

### Post by osomphane on 2010-05-12
nvm it worked... it just generated & copied the server's pub key to the server . go figure ;)

---

### Post by Simon Cropper on 2010-05-25
> **osomphane said:**
> nvm it worked... it just generated & copied the server's pub key to the server . go figure ;)

osomphane,

can you publish steps that you carried out I have tried everything to get the process to work on 10.04 but like your first post I keep getting prompted for passwords.

I have read and implemented multiple solutions to when this three step procedure does not work but none work. What do you mean "it just generated & copied the server's pub key to the server . go figure"?

Are you saying the *.pub file contents need to be in the authorized_keys2 file on both the server and client?

I have found that the authorized_keys file on the server is the one updated with the key. Isn't this the Protocol 1 key file?

Anyone know what to do if you have another key on the server? I run nxmachine and it has stuffed a key in the authorized_keys2 file.

Simon

---

### Post by frenchn00b on 2010-06-02
the solution is interesting ... but is it possible to leave open the SSH connection and to upload using scp ? 

well for a webcam image uplaoding every 1 seconds , for instance ...

---

### Post by listerr on 2011-04-14
This is exactly what I needed to do. The security implications need thinking about though to stop anyone who has the key, or can access the login, from just being able to SSH in to the remote host no questions asked. (If somebody managed to break my account at box A, the would be able to jump across to box B (and potentially others) with no problem.)

The following HOWTO (see link) and the man page for [FONT="Courier New"]authorized_keys[/FONT] is very useful and details ways you can lock down the authorized_keys file to only allow access from a given IP(s) and prevent the login from getting a shell or being able to setup SSH forwarding etc:

[http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html](http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html)

You can add options on the server (target) machine into the [FONT="Courier New"]authorized_keys[/FONT] file:

> from="x.x.x.x",no-port-forwarding,no-pty ssh-rsa AAAAB3NzaC1...

To lock access down to a particular IP address and prevent getting a shell prompt. Now I can't just SSH in, and only from the IP address specified in the authorized_keys file. So not only do I need the private key, I also need to be coming from the right host.

> robl@nix:~/bin$ ssh -l rsync -i ~/.ssh/ssh_backup_key remote.host.here
PTY allocation request failed on channel 0

To be extra paranoid, For my purposes I created a separate user account on the server machine (The private key file for this user lives in my account's ~/.ssh directory) The only slight downside is that rsync may not be able to set the same file ownerships etc. on the remote machine, but for my purposes, this does not matter. (If I cared, I could tar up the files first as the .tar file preserves these attributes, but maybe not so efficient for rsync's purposes.)

I also set this user account to have no password in the shadow file (vipw -s)  

> rsync:*:15078:0:99999:7:::

This makes sure that login is only possible for this user with the SSH key, and not by password. (Or, basically, just useradd this user and never give it a password.)

However, one weakness with this setup is that it is possible to subvert the rsync copy command to obtain a copy of the remote users's authorized_keys file:

> /usr/bin/rsync -rave '/usr/bin/ssh -p 22 -i /home/robl/.ssh/backup_key' [email]rsync@remote.host.here:/home/rsync/.ssh[/email]/authorized_keys /tmp/rsync_auth


Then I can mess with this file, remove all the security options, and copy it back to the server:

> /usr/bin/rsync -rave '/usr/bin/ssh -p 22 -i /home/robl/.ssh/backup_key' /tmp/rsync_auth [email]rsync@remote.host.here:/home/rsync/.ssh[/email]/authorized_keys


Now, I can SSH in unrestricted again.

The way round this seems to be to set the permissions on the remote .ssh directory **and** the file, so that [FONT="Courier New"]authorized_keys[/FONT] cannot be overwritten:

> dr-x------ 2 rsync rsync      4096 2011-04-14 11:34 .ssh

([FONT="Courier New"]chmod 500 .ssh[/FONT])

And then within that directory, authorized_keys needs to be readonly: 

> -r-------- 1 rsync rsync  439 2011-04-14 11:30 authorized_keys

([FONT="Courier New"]chmod 400 authorized_keys[/FONT])

This prevents somebody from remotely replacing it:

> robl@nix:~/bin$ /usr/bin/rsync -rave '/usr/bin/ssh -p 22 -i /home/robl/.ssh/ssh_backup_key' /tmp/rsync_auth [email]rsync@remote.host.here:/home/rsync/.ssh[/email]/authorized_keys 
sending incremental file list
rsync_auth
rsync: mkstemp "/home/rsync/.ssh/.authorized_keys.uEwz7q" failed: Permission denied (13)


Of course, I thought that setting the remote user's home directory to something less obvious than [FONT="Courier New"]/home/user[/FONT] may make it a bit more difficult to for somebody to locate the remote authorized_keys file, but it is possible to specify "~" in the command meaning "the user's home directory" so... [FONT="Courier New"]~/.ssh/authorized_keys[/FONT].

Of course, there may be a way round this again, by trying to rsync the entire .ssh directory or similar... I haven't managed it yet....

The other possibility is that if your hosts are ntp sync, and your backup jobs run at known cron times, you could possibly include another cron on the server machine to enable the account only at the times it is needed.

This would be okay, but I imagine difficult to maintain if you had lots of hosts (If you wanted to change the time, you would have to go round and change them all!) or the job runs frequently.

([FONT="Courier New"]usermod -L[/FONT] is not enough as it only changes the passwd, but still allows SSH key access)

So.. perhaps a cron that moves the authorized_keys file in and out, or changes the shell to [FONT="Courier New"]/bin/false[/FONT] or some such, so that the account cannot be used at odd times, only when your cron job kicks off.

---

