---
title: "[SOLVED] Problem with chmod - Permissions won't stick on enclosed files!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-10-20
When I execute the command

```


sudo chmod -R 755 * /home/www


```

Only the parent directory changes permission, all the contents are still set to root.

I have also tried right click in gksudo nautilus > properties > permissions then changing to rw/rw/r and Apply Permmisions to Enclosed Files but still only the parent directory changes.

Any ideas on what is wrong or what I'm doing wrong?

It's probably something little but I'm really confused:confused:

---

### Post by jerome1232 on 2008-10-20
Well I'm not sure what that asterisk is doing, this ought to work, throw a -v in so it's verbose and you can see what it's doing. (and post the output if it still didn't work)

```
sudo chmod -Rv 755 /home/www
```

---

### Post by roelpeeters on 2008-10-20
What filesystem are you using under /home/www ? In case it is a mapping to a network drive through samba, you will not be able to set the permissions. Otherwise, is /home/www a symbolic link?

---

### Post by northern lights on 2008-10-20
It's only the use of the star/asterisk that is weird - right now, you're syntax is *chmod [OPTIONS] Numeric_Mode file path/to/file* while it should be *chmod [OPTIONS] Numeric_Mode [path/to/]file* so in essence, you can either use```
chmod -R 755 /home/www/
```or```
chmod -R 755 /home/www/*
```or cd to folder and then chmod```
cd /home/www/
chmod -R 755 *
```If things still don't work, get a verbose output (v Option) and post it here```
chmod -Rv 755 /home/www/
```

---

### Post by PierreDeKat on 2008-10-20
Yeah, the verbose thing should tell you what's going on.

But is your username "www"? Because if it is, I believe there are a couple files inside your /home/UserName/ directory that you don't actually want to change the permissions on. I think I tried that once, and there were some unexpected consequences.

Other than that, just make sure you have the path correct. It should be something like /home/YourUserNameGoesHere/YourFolderGoesHere/YourSubfolderGoesHere/.

---

### Post by northern lights on 2008-10-20
> **PierreDeKat said:**
> But is your username "www"?Very good point.

*~/www/* is usually used as a folder to store a website on a private/testing home based webserver. Could it be that you're trying to change permissions on */home/USER/www/* where *USER* your username?

---

### Post by pluckypigeon on 2008-10-20
> **PierreDeKat said:**
> Yeah, the verbose thing should tell you what's going on.

But is your username "www"? Because if it is, I believe there are a couple files inside your /home/UserName/ directory that you don't actually want to change the permissions on. I think I tried that once, and there were some unexpected consequences.

Other than that, just make sure you have the path correct. It should be something like /home/YourUserNameGoesHere/YourFolderGoesHere/YourSubfolderGoesHere/.

nope that's not my user name it's just where I practice my php stuff

---

### Post by pluckypigeon on 2008-10-20
Thank you all for your quick replies they all took me by surprise.

I tried cd /home/www/ then
```
chmod -R 755 *
```

I tried 
```
chmod -R -v 755 /home/www/*
```

On the verbose output i got this output on all the files
```

mode of `/home/www/file.html' retained as 0755 (rwxr-xr-x)

```

everything all still belongs to root though

---

### Post by jerome1232 on 2008-10-20
chmod doesnt' change ownership of files, it changes permisisions, you can chmod for years it'll still be owned by root.

If you want your user to have ownership, you can copy and paste this command.

```
sudo chown -R $USER:$USER /home/www
```

---

### Post by pluckypigeon on 2008-10-20
> **jerome1232 said:**
> chmod doesnt' change ownership of files, it changes permisisions, you can chmod for years it'll still be owned by root.

If you want your user to have ownership, you can copy and paste this command.

```
sudo chown -R $USER:$USER /home/www
```

Wicked:). Thanks a lot. I'm sure you have helped me before to!

---

