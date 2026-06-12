---
title: "SSH and: Rsync, VNC (Remmina), FTP"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by wdavro on 2013-10-19
I apologize in advance, I don't know if this is the right forum section for this, and I don't know if this should be split into two or more separate threads.

I have a 12.04 laptop (it dual boots with Win7 for my job) and a 12.04 desktop and a yet to be built offsite computer of my own makeup (probably also 12.04). All using gnome not the new thing.
My goal: to be able to use ssh for all my 'remote access' needs and methods (currently: rsync, vnc, ftp).
FTP and VNC already work.  FTP not using ssh, VNC both with and without SSH (as I haven't figured out how to tell the vnc server to only respond to requests made via ssh).

I'm very confused about setting up rsync (and ssh as well).  I've read through several posts and google search results about configuring individual items, but haven't found anything that mentions using multiple functions together.
And some of the articles are pretty dated as well (like 2009) so I don't know how reliable they are.

ssh:
On my first attempt (a couple months ago) at using ssh (on a non-standard port), I  setup an ssh public key with a passphrase.  I then setup a vnc connection (on  a different non-standard port) in Remmina using ssh which I use to  connect from the laptop to the desktop.  It works.  I start the vnc connection and it connects after I type the passphrase.  So that's done.

rsync and vnc:
I need to sync some folders between the desktop and laptop, and I'm going to need to setup (using cron) to backup folders from my desktop to an offsite server (that I haven't built yet).  I was planning to use rsync for both functions.  My questions:
Q1: If I'm going to run the rsync command (again, on a non-standard port) on my laptop to sync to the desktop (also on a non-standard port), does that mean the laptop has to be setup as an rsync server?
Q2: Since I'm also going to run the rsync command on my desktop to backup to the offsite server (using cron), does the desktop also need to be setup as an rsync server?

I'm also trying to use rsync via ssh.  But since I need to cron one of these rsyncs, I've read I need to do ssh with a key but without a passphrase.  So on the laptop I issued the same command as I did initially
```
ssh-keygen -t rsa -b 4096
```
but did not enter a keyphrase this time, I just pressed Enter.  Then I copied the key file to the desktop and on the desktop cat'd it into authorized_keys with:
```
cat id_rsa.pub >> authorized_keys
```

I then tried to vnc (using Remmina as before) from the laptop to the desktop to see if it still works, but now it doesn't.  It gives me:
> SSH automatic public key authentication failed: None method rejected by server 
On the desktop I cat'd the authorized_keys file and there appear to be two keys in the file.
So my questions are:
Q3: What does the above error indicate I did wrong?

More generally:
Q4: Does ssh allow me to use multiple keys (a no-passphrase key for rsync and a passphrase key for vnc)?  I understand I 'could' use the same key/no-key for both rsync and vnc, but I ask this for the sake of understanding ssh better).
Q5: Does it matter on which computer I issue the ssh-keygen command?  Provided I copy the public and private key to the appropriate folders on the appropriate machines?  Or are the generated keys machine specific? 
Q6: Trying to Keep my public exposure to a minimum as much as possible, do I need to have separate non-standard ports for all the above mentioned functions?  Or can they share the same port number (as long as I don't ftp at the same time I VNC or rsync)?

Ultimately I plan to use ssh for my ftp server on the desktop as well (when I have the time to work through that setup).

Thanks in advance.

---

### Post by Lars Noodén on 2013-10-20
ssh needs to be told  which key to use when you initiate your connection.  The path can be absolute or relative, but must point to the specific key that the server is expecting.  The **public** key goes on the server in authorized_keys and the **private** key stays on the client.  

```

ssh -i /home/wdavro/.ssh/some_key_rsa  server.example.org

```

rsync is about the same.  It uses ssh by default, but needs to be told which key to use, if you are not using an agent.

```

rsync -e 'ssh -i /home/wdavro/.ssh/some_key_rsa'  /home/wdavro/  server.example.org:/home/wdavro/

```

Another way would be to use an agent.  It is good for the duration of your desktop session (unless you changed something) and can hold up to six keys.  

```

ssh-add /home/wdavro/.ssh/some_key_rsa 
ssh server.example.org

```

With the agent you only add the key once, then you can keep logging in to the remote server as many times as you want using that same key.

When generating keys with [ssh-keygen](http://manpages.ubuntu.com/manpages/raring/en/man1/ssh-keygen.1.html) you can use the -f option to specify a particular file name for the key and the -C option to append a comment to the public key.  The comment can be something about the purpose of the key and will help you figure out which is which when you have a server account with more than one key.

---

### Post by Lars Noodén on 2013-10-20
The same goes for picking a non-standard port.  

```

rsync -e 'ssh -p 8080 -i /home/wdavro/.ssh/some_key_rsa'  /home/wdavro/  server.example.org:/home/wdavro/

```

But if you are on your LAN it saves a lot of hassle to just use the standard port.  If you are worried about brute-force attacks when you are off your LAN, then disable password login and use keys only.  Also turn off remote root login.  

```

PermitRootLogin no
PasswordAuthentication no

```

Picking a non-standard port doesn't add a whole lot, you'll still get the occasional probe or a whole slew of them.

---

