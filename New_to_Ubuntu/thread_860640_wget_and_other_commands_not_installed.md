---
title: "wget and other commands not installed?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by citrustree on 2008-07-15
Hi all,

I recently got my hands on an ubuntu VPS.

When I log into my server using SSH I can't seem to do anything that I normaly do on my other server. Some listing:

bash-3.1$ wget
bash: wget: command not found
bash-3.1$ tar
bash: tar: command not found
bash-3.1$ man
bash: man: command not found
bash-3.1$ install
bash: install: command not found
bash-3.1$ apt-get
bash: apt-get: command not found


What am I doing wrong? :(

---

### Post by kevdog on 2008-07-15
When you log in what does you PATH variable read?

echo $PATH

---

### Post by citrustree on 2008-07-16
Thank you so much for your reply.

The command you mention outputs:

```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```

Thanks again.

---

### Post by houbysoft.xf.cz on 2008-07-16
Hi, that's pretty strange, because for example wget usually IS in /usr/bin, which is in your path... Try running for example
which wget
or
whereis wget, what does it ouput?

---

### Post by citrustree on 2008-07-16
Oh dear:

bash-3.1$ which wget
bash: which: command not found
bash-3.1$ whereis wget
bash: whereis: command not found

---

### Post by houbysoft.xf.cz on 2008-07-16
Oh. And have you tried manually navigating to for example /usr/bin to find out if the files are really there?

---

### Post by citrustree on 2008-07-16
I did try to navigate there manualy. the usr directory exists, but not bin... (Well not that I can access anyway, and I'm told I have admin rights). I can't see it via FTP either. I was told by my VPS provider that wget etc are installed, very weird...

---

### Post by houbysoft.xf.cz on 2008-07-16
Very strange... if the directory bin doesn't exist, I would ask your VPS provider about this... really strange.

---

### Post by citrustree on 2008-07-16
I will do that, thank you.

---

### Post by citrustree on 2008-07-16
Doh, I was logging in as a sub-user. Back I go to newbie corner.

Thanks all for your help.

---

