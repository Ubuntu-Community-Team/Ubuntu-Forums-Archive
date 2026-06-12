---
title: "[SOLVED] Giving permissions to Apache"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by ub007 on 2008-09-08
Hi,

I'm trying to ssh using php on a ubuntu machine.I have setup key based authentication on both the machines and it works perfectly fine from the terminal command line.The ssh2_auth_pubkey_file php function throws me an error 'Warning ssh2_auth,.......'Public Key Authentication Failed',


> Most probably the problem is that Apache can't read my  ssh key.
 .ssh folders are usually readable only by their owners.How do i give Apache permission to read the .ssh folder?

Thanks in advance
David

---

### Post by ggaaron on 2008-09-08
```

chmod 0711 ~
chmod 0711 ~/.ssh
chown yournamehere.apachenamehere(wwwdata on ubuntu I think) ~/.ssh/pathtokey
chmod 0640 ~/.ssh/pathtokey

```

Above code should work. Alternatively you can instead of last two lines use
```

chmod 0644 ~/.ssh/pathtokey

```
but this will grant anyone access to your key

Are you sure that apache looks for keys in your home folder, not his? (might be a stupid question as I have never done this)

---

### Post by ub007 on 2008-09-10
> chown yournamehere.apachenamehere(wwwdata on ubuntu I think) ~/.ssh/pathtokey

Its www-data on ubnuntu. And I assume i have to give my system name instead of yournamehere.So it would be
chown david.www-data ~/.ssh/pathtokey  ,Am i right?

I saw ur reply late,tried something in the morning like

chown www-data ~/.ssh/
chown www-data ~/.ssh/*
chmod 755 ~/.ssh/
chmod 755 ~/.ssh/*

Then
su - www-data
$cd ~/.ssh
It gives no such dir or file
ls gives only var/www

Just hoping your method
> chmod 0711 ~
chmod 0711 ~/.ssh
chown yournamehere.apachenamehere(wwwdata on ubuntu I think) ~/.ssh/pathtokey
chmod 0640 ~/.ssh/pathtokey works

---

### Post by ggaaron on 2008-09-10
You are right about david, but when you do this chmod ~/.ssh and so on you alter .ssh in you home directory, probably /home/david/.ssh, when you su - www-data, your home changes to /var/www.

You should create a symlink if you want it to work like this:
'sudo ln -s /home/david/.ssh/ /var/www/.ssh'

---

### Post by ub007 on 2008-09-10
Yes,i will need to specify the full path for .ssh .To sum up, i will need to do the foll:

> chmod 0711 ~
chmod 0711 ~/.ssh
chown yournamehere.apachenamehere(wwwdata on ubuntu I think) ~/.ssh/pathtokey
chmod 0640 ~/.ssh/pathtokey
'sudo ln -s /home/david/.ssh/ /var/www/.ssh'

Initially i thought this alone would work;but from your reply assume it will not

> chmod 0711 ~
chmod 0711 ~/.ssh
chown yournamehere.apachenamehere(wwwdata on ubuntu I think) ~/.ssh/pathtokey
chmod 0640 ~/.ssh/pathtokey

---

### Post by ggaaron on 2008-09-10
I haven't used this mod_ssh, but from your posts I assume that you have a key in you user's home directory, but apache runs as a different user and can't find it's own key as you haven't made any for him. Just came to my mind that instead of this all chmods you could copy this key from your home to apache's home.

---

### Post by ub007 on 2008-09-10
> I assume that you have a key in you user's home directory, but apache runs as a different user and can't find it's own key as you haven't made any for him.

Yes exactly,i have the private & public rsa keys-id_rsa,id_rsa.pub in my .ssh directory -/home/david/.ssh ,owned by user david..

but apache runs as a diff user,.....

> Just came to my mind that instead of this all chmods you could copy this key from your home to apache's home.

That would make it incredibly insecure,wouldnt it?

i was thinking of having it in /home/david/.ssh & giving both user david & www-data access to it.....how would i accomplish that?

> chmod 0711 ~
chmod 0711 ~/.ssh
chown david.www-data ~/.ssh/pathtokey
chmod 0640 ~/.ssh/pathtokey   would this give permissions to both david & www-data...or does it have something to do with gids & uids?

---

### Post by ggaaron on 2008-09-10
chmod 0711 ~
give owner right do do everything and others to enter this directory, but not list it's contents

chmod 0711 ~/.ssh
the same as above

chown david.www-data ~/.ssh/pathtokey
change owner to david and group to www-data (this are the uids and gids)

chmod 0640 ~/.ssh/pathtokey 
let owner to read and write and group to read

So it should work, but remember to do the symlink, so your key will appear in two places in the file system (your's home and apache's home).

---

### Post by ub007 on 2008-09-11
thanks mate,got it working...:guitar:

---

### Post by ggaaron on 2008-09-11
I'm glad that it works for you,
happy hacking;)

---

