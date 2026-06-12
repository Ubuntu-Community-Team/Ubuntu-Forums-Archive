---
title: "[SOLVED] sudo does not work - unable to resolve host"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by cairnsww on 2008-08-07
I seem to be in a corner. First I tried to run Synaptic and it ended without starting. I looked at the log file and saw: 

unable to resolve host <hostname>

So, on advice from a post on ubuntuforums, I tried to have a look at /etc/hosts by

gksudo gedit /etc/hosts

But that does not work either. The same messsage appears on the log file.

In fact, just typing sudo brings up the message on the terminal.

Way out?

Thanks

---

### Post by snowpine on 2008-08-07
Just try rebooting, see if that works--only one process can have sudo privilages at a time, perhaps your aborted Synaptic still has the sudo "key"?

---

### Post by eightmillion on 2008-08-07
I recently had this problem too. Rebooting fixed it though. If that doesn't work you can boot a live cd and edit your hosts file.

---

### Post by cairnsww on 2008-08-07
No, I tried rebooting first thing. Same situation.

---

### Post by drs305 on 2008-08-07
> **cairnsww said:**
> I seem to be in a corner. First I tried to run Synaptic and it ended without starting. I looked at the log file and saw: 
unable to resolve host <hostname>
So, on advice from a post on ubuntuforums, I tried to have a look at /etc/hosts by
gksudo gedit /etc/hosts
But that does not work either. The same messsage appears on the log file.
In fact, just typing sudo brings up the message on the terminal.
Way out?
Thanks

Run "groups" and see if you are listed in admin. If you are not listed, (can't sudo anything) boot to the recovery mode (root) and run this to get you back in the admin group to be able to use sudo:
```
adduser *username* admin
```

If you are still listed in 'admin' and you do have a 'hosts' problem, again boot to the root prompt and open up /etc/hosts and see if your computer name has changed.

You should see something like this in hosts, with nothing added to the end of the computer name (such as computername.web):
```

127.0.0.1 localhost
127.0.1.1 computername

```

---

### Post by Elfy on 2008-08-07
Can you open aterminal and post the outputs of these

```
cat /etc/hostname
cat /etc/hosts
```

Don't worry - drs305 in on the case  -but if you get lost

[https://answers.launchpad.net/ubuntu/+question/32783](https://answers.launchpad.net/ubuntu/+question/32783)

---

### Post by cgkades on 2008-08-07
> **snowpine said:**
> Just try rebooting, see if that works--only one process can have sudo privilages at a time, perhaps your aborted Synaptic still has the sudo "key"?

i really dont think that statement is true. Though you can only use the package installer one process at a time. Meaning you cant do apt-get install while running add/remove app. But you can do sudo as with as many running process as needed. ( i just tried it )

---

### Post by cairnsww on 2008-08-07
Groups:

bill@Lawrence:~$ groups
bill adm dialout cdrom floppy audio dip video fuse lpadmin admin vboxusers sambashare plugdev

---

### Post by cairnsww on 2008-08-07
bill@Lawrence:~$ cat /etc/hostname
Lawrence
bill@Lawrence:~$ cat /etc/hosts

127.0.0.1 localhost
127.0.1.1 Lawrence.Bandari

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Hmm - where does the ".Bandari" come from? Bandari is my wireless network. Is this the problem?

---

### Post by cairnsww on 2008-08-07
"If you are still listed in 'admin' and you do have a 'hosts' problem, again boot to the root prompt and open up /etc/hosts and see if your computer name has changed."

How do I "boot to the root prompt?" I have automatic login enabled?

---

### Post by bobnutfield on 2008-08-07
> bill@Lawrence:~$ cat /etc/hostname
Lawrence
bill@Lawrence:~$ cat /etc/hosts

127.0.0.1 localhost
127.0.1.1 Lawrence.Bandari

The hostname must be the same.  Change:

127.0.1.1 Lawrence.Bandari

to:

127.0.1.1 Lawrence

Reboot, and that should fix it.

---

### Post by jerome1232 on 2008-08-07
You'll need root access to do that though, when grub loads select recovery mode, then you'll select drop to root shell run
```
nano /etc/hosts
```
change it hit ctrl+x type 'y' then hit enter, type reboot and you should be fine

---

### Post by bobnutfield on 2008-08-07
> **jerome1232 said:**
> You'll need root access to do that though, when grub loads select recovery mode, then you'll select drop to root shell run
```
nano /etc/hosts
```
change it hit ctrl+x type 'y' then hit enter, type reboot and you should be fine

You are correct.  Sorry, I gave an incomplete answer.

---

### Post by drs305 on 2008-08-07
> **cairnsww said:**
> How do I "boot to the root prompt?" I have automatic login enabled?

As you computer boots (usually after you hear a beep) start hitting the ESC key. The grub boot menu will appear and you can select the Recovery mode. It will run for a bit and then present you with several choices. Select the one that mentions 'root' and it will immediately open up a prompt, from which you can run nano, vim, or other text editor. You want to open and edit /etc/hosts and change the name back to only your computer name, as several have mentioned.

---

### Post by cairnsww on 2008-08-07
Hooray! I figured it out for myself.

(You have to hit <Esc> at the appropriate moment during the boot process and then you get a menu that allows you into a terminal with root privileges. Not the most secure, but I didn't want the most secure!)

I had an instant self taught lesson in nano (quite a neat little editor) and removed the ".Bandari" from my host name and my sudo problem was solved.

I have no idea how it got there in the first place - I have been trying to get Samba going but did not think that I had been there.

Many thanks you guys for the help.

---

### Post by gjoellee on 2008-08-07
I tried for fun ```
sudo apt-get install sudo
``` and it appeared to be a package or something, maybe you can reinstall sudo..?

(I have no idea if I am even helping here or not)

---

### Post by cairnsww on 2008-08-07
Thanks Bob and Jerome1232 and drs305 - if I had just hung on a little bit longer, I could have just followed your advice. 

But then perhaps I would not have learned it for myself and would not feel so self satisfied :)

---

### Post by bobnutfield on 2008-08-07
Learning it yourself will be the best for you anyway.  You do not forget how you repaired something when you have to figure it out for yourself.  Well done.

---

### Post by ben2talk on 2011-03-24
> **drs305 said:**
> Run 
You should see something like this in hosts, with nothing added to the end of the computer name (such as computername.web):
```

127.0.0.1 localhost
127.0.1.1 computername

```

That's what happened to mine - for some reason they were commented out with a note that the hostname would be managed directly via dns... 

I uncommented the localhost line, copy/pasted it and edited localhost to read 'Serenity' - my computer name - and terminal didn't complain.

Now to reboot and see if it survives...

---

