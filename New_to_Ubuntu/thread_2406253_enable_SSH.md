---
title: "enable SSH"
date: 2018-11-18
forum: New to Ubuntu
---

### Post by tech-jeff on 2018-11-18
Hi to all members, I've started to install a new Ubuntu machine (forgot the version because it's in the office). First thing I want to setup is SSH since that's the basic is to remote for other setup. I've issued the command

sudo apt-get install openssh-server

and I've restart the service using the command

sudo service ssh restart

and checked the status using 

sudo service ssh status

I can see that service is running but for some reason I still can't ssh to the new machine. 

Am I still lacking something?

Thanks
tech-jeff

---

### Post by mitesh.agrwl on 2018-11-18
Please go through this this[ tutorial on SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").

---

### Post by tech-jeff on 2018-11-19
Hi mitesh.agrwl,

I did the steps based on the article and for some reason when I tried editing the sshd_config but gedit is not installed, so I used

sudo nano /etc/ssh/sshd_config

I see a black screen with the title named GNU nano 2.2.6

but nothing on that page

Thanks
tech-jeff

---

### Post by mitesh.agrwl on 2018-11-19
> **tech-jeff said:**
> Hi mitesh.agrwl,

I did the steps based on the article and for some reason when I tried editing the sshd_config but gedit is not installed, so I used

sudo nano /etc/ssh/sshd_config

I see a black screen with the title named GNU nano 2.2.6

but nothing on that page

Thanks
tech-jeff

The reason may be that the file does not exist on desired location and when you run the above command it is creating the file there, or it is blank (the file has no content in it). In both cases the file needs to be written.

[sshd_config (system)]("https://gist.github.com/kjellski/5940875")    [sshd_config (customized)]("ftp://ftp.iitb.ac.in/LDP/en/solrhe/chap15sec122.html")

---

### Post by The Cog on 2018-11-19
Or try these two commands to see if the file exists, how big and when it was last edited (just in case nano is playing up):
```
ls -l /etc/ssh/sshd_config
cat /etc/ssh/sshd_config
```

And you say you can't ssh into the machine: what error message do you get when you try?

---

### Post by tech-jeff on 2018-11-19
I did the command: 

ls -l /etc/ssh/sshd_config

And it showed me rw-r—r— root root

So I guess it is existing but when i used cat

It didn’t show up anything. I tried putting in the 2 lines below: 

AllowUsers <username>
Port 22

And do another 

cat /etc/ssh/sshd_config and it showed me that 2 lines.

---

### Post by tech-jeff on 2018-11-19
and it just shows server unexpectedly closed network connection or connection closed. 

I disabled the ufw firewall but still no go. 

I'm beginning to suspect this might be a bad image/install

Thanks
Jeff

---

### Post by The Cog on 2018-11-20
It certainly looks that way. There should have been a size and a date after that "root root".

Assuming that you didn't post the entire line, it still looks like the server config file is wrong - there should be quite a lot of lines there. You could try this command:
```
sudo apt-get install --reinstall openssh-server
```

---

### Post by tech-jeff on 2018-11-20
Ok, I reinstalled openssh-server and still shows me blank. Please refer to attachment

Thanks
tech-jeff

---

### Post by again? on 2018-11-22
When you install openssh-server, it creates a config at /etc/ssh/sshd_config
Permissions? The config should have been written in /etc/ssh
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] ls -al /etc/ssh**
total 600
drwxr-xr-x   2 root root   4096 Nov  7 12:02 .
drwxr-xr-x 158 root root  12288 Nov 22 04:22 ..
-rw-r--r--   1 root root 553122 Feb 10  2018 moduli
-rw-r--r--   1 root root   1580 Feb 10  2018 ssh_config
[COLOR="#FF0000"]-rw-r--r--   1 root root   3279 May  9  2018 sshd_config[/COLOR]
-rw-r--r--   1 root root   3262 Nov  7 09:54 sshd_config.ucf-dist
-rw-------   1 root root    227 May  9  2018 ssh_host_ecdsa_key
-rw-r--r--   1 root root    173 May  9  2018 ssh_host_ecdsa_key.pub
-rw-------   1 root root    399 May  9  2018 ssh_host_ed25519_key
-rw-r--r--   1 root root     93 May  9  2018 ssh_host_ed25519_key.pub
-rw-------   1 root root   1679 May  9  2018 ssh_host_rsa_key
-rw-r--r--   1 root root    393 May  9  2018 ssh_host_rsa_key.pub
-rw-r--r--   1 root root    338 May 27 12:58 ssh_import_id
```

You should find the default config which you can copy over manually at /usr/share/openssh/sshd_config
but you need to look into why it's not being copied over on install.

---

