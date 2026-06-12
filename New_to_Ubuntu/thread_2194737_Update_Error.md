---
title: "Update Error"
date: 2013-12-20
forum: New to Ubuntu
---

### Post by ram.gunnerforever on 2013-12-20
I am not able to install any new softwares through Ubuntu Software Center. 

When I do sudo apt-get update 
I get this as an error -[FONT=arial, sans-serif] 
[/FONT]W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


What do I do?

---

### Post by fantab on 2013-12-20
From Terminal [Ctrl+Alt+T], and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
```

Close all other applications that may be running before you run the code. If you still see errors post back....

---

### Post by ram.gunnerforever on 2013-12-21
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/quantal/Release.gpg)  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mörgæs on 2013-12-21
Have you tried changing software mirror?

---

### Post by ram.gunnerforever on 2013-12-22
how do I do that?

---

### Post by nothingspecial on 2013-12-22
You open the software centre then click edit > software sources. Then choose Download From > Other and select a mirror.

---

