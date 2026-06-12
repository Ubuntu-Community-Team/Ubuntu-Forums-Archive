---
title: "Back-up whole system"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by HappyDormFriends on 2008-06-06
hi! i'm not a totally linux/ubuntu newbie, having used it lightly in years. 
i'm plannning to master this OS now. :guitar:

just wanna know, how can i back-up my whole system (most importantly, the installed applications), possibly in a dvd? then, i may want to use the back-up for reinstalling it (in case of crash, reformat, etc).

why? i may want to continue using my now-installed system even though i don't have an internet connection. i notice that the most-used apps are only available on-line and are not in the install cd, say VLC. correct me pls. if i'm wrong. :)

hope anyone can help! thanks a lot!

you can email me at [email]eeroxasjr@gmail.com[/email] or [email]jay11illidan@yahoo.com[/email] if it won't be a bother. :)

---

### Post by Inxsible on 2008-06-06
partimage will create a bit by bit copy of your entire drive. More like a Restore point than a backup really. There is also the dd command which does bit by bit copy. 

I am not sure if thats what you are looking for though

---

### Post by rraj.be on 2008-06-06
You can use partimage to backup your whole instalation.

try this.

```
[http://pittman.ws/articles/howto/partimage.html]("http://pittman.ws/articles/howto/partimage.html")
```

to make a package cd like what you have for windows software collection you can use Apt on cd.

You can install that by typing this on terminal

```
sudo apt-get install aptoncd
```


Try this one if you dont have internet connection to install all the above.

```
[https://help.ubuntu.com/community/PackageCDs]("https://help.ubuntu.com/community/PackageCDs")
```

for any help you can mail me.

---

### Post by mdpalow on 2008-06-06
I think you might be happy with QuickStart. It'll do back-ups in TAR and Partimage; whichever you want. You can also setup a sync or scheduled back-up.

See my signature below and good luck.

---

### Post by dje on 2008-06-08
take a look at linbaku in my sig, it backs up your entire system to a tar archive

hope that helps,
dje

---

