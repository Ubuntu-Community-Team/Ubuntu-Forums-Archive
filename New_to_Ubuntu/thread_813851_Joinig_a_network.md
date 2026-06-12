---
title: "Joinig a network"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-05-31
Good day to all!:)

Another begginer's question..

How can i see my ubuntu station from my windows station? from ubuntu im able to view windows pc's but i cannot view my ubuntu from windows..

should i edit smb.conf? also i want this ubuntu to be a member of our domain?

Thanks in advance! God Bless you all!:):):)

---

### Post by hyper_ch on 2008-05-31
you need to install samba and configure the smb.conf appropriately...

Here's my config, very simple one:
```
[global]
workgroup = ARBEITSGRUPPE
hosts deny = 10.0.0.1

[exchange]
comment = Exchange
path = /home/hyper/Exchange
force user = hyper
force group = hyper
read only = No
[appz]
comment = Appz
path = /home/hyper/Appz

```

---

### Post by ajmorris on 2008-05-31
to see your ubuntu partition from windows, you can use an application called ext2ifs: [http://www.fs-driver.org/](http://www.fs-driver.org/)

This will allow the mounting, reading and writing of your ubuntu ext partition (there are other methods if you do not use ext)

As for adding ubuntu to your domain... any particular reason for doing this? you can access windows shares without doing this, even if you are not on the domain with which the shares are on.

EDIT: LOL, sorry, ignore me,  mis-read your post didnt realise the machines were different :P
You can also mount your samba shares permanently using smbclient

AJ

---

### Post by jerryheavyarms on 2008-05-31
Thanks for the reply!

Isnt samba already installed?

I already configured smb.conf, however, still I cant see my ubuntu. 

A couple of months ago, i was able to configure a CentOs station to be seen in a windows network. But i already forgotten how i did that..

Thanks!

---

### Post by jerryheavyarms on 2008-05-31
Thanks AJ!:)

I want to migrate to ubuntu from my win2k station. I want this ubuntu to be easily accessed by other staff especially my boss.
Also, would there be a problem with regards to our company email?
A while ago I configured Evolution. I was able to send messages but unable to retrieve them in evolution. Ive read them usimg outlook express in win2k. Is that a domain issue?

Thanks and sorry for being so ignorant..:)

---

### Post by hyper_ch on 2008-05-31
```

sudo apt-get install samba

```

and then, depending on the configuration, you'll have to add users to samba

---

### Post by jerryheavyarms on 2008-05-31
thanks hyper!:)

By the way guys, I have ubuntu studio 8.04. if that helps..

and i know samba is already installed

---

### Post by ajmorris on 2008-05-31
if you go to the windows run dialog and type \\<ubuntu ip>\<share name> and press enter
that should take you to your share, or you can just do \\<ubuntu ip> to display all shares. Then you can do for example:
net use k: \\<ubuntu ip>\<share name>  (share name is optional)  from the command line in windows, to map the ubuntu share.

however, you should be able to see your samba machine from windows by default....

Also, in your share options in /etc/samba/smb.conf, make sure the share is set to browseable=yes

---

### Post by jerryheavyarms on 2008-05-31
Ive tried it but still no luck..

Maybe i have errors in configuring smb.conf..:(

---

