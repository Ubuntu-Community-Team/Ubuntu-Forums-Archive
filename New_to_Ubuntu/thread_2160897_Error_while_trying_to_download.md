---
title: "Error while trying to download"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by salmanci on 2013-07-08
Hi guys,
Am using ubuntu 12.04 server. when am trying to download anything am getting error- **E: Unable to locate package**. I am getting ping to this ubuntu as well as viceversa. The ip has internet privilage, i checked it. pls help.

---

### Post by DeathByDenim on 2013-07-08
You might want to try running
```
sudo apt-get update
```

Does it work after that? Or does apt-get update fail as well?

---

### Post by salmanci on 2013-07-08
> **DeathByDenim said:**
> You might want to try running
```
sudo apt-get update
```

Does it work after that? Or does apt-get update fail as well?

I tried that too... Now the error showing, W: Failed to fetch [http://repository](http://repository) address

---

### Post by DeathByDenim on 2013-07-08
Hmm, it sounds like your sources.list got screwed up somehow. Could you check /etc/apt/sources.list ?
It should contain lines like
```
deb http://ca.archive.ubuntu.com/ubuntu/ raring main restricted
```
(but with precise instead of raring for ubuntu 12.04)

---

### Post by claracc on 2013-07-09
> **salmanci said:**
> I tried that too... Now the error showing, W: Failed to fetch [http://repository](http://repository) address

What is the http address you provide? It hasn't any software package.

Post your /etc/apt/sources.list file in order to see if you have any malformed line or any inexistent repository. 

Also, it would be good to say what are your hardware specifications.

---

### Post by salmanci on 2013-07-09
Actually it is in a vm. Please let me know how to post source.list and configuration from vm to here..

---

### Post by dannyboy79 on 2013-07-09
is your VM setup correctly? can you access the internet and or is DNS working in your VM?

---

### Post by DeathByDenim on 2013-07-09
You can copy-past the contents of the file /etc/apt/sources.list in this forum. Just put them between [ code ] and [ /code ] tags (without the spaces) for readability.

---

### Post by salmanci on 2013-07-13
Hi guys,
i found out the problem, it was because of the proxy settings..
thanks..

---

### Post by claracc on 2013-07-13
Please, mark your thread as solved in order the information can be easily found.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

