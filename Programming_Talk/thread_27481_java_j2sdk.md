---
title: "java j2sdk?"
date: 2005-04-16
forum: Programming Talk
---

### Post by lmellen on 2005-04-16
If you want the java j2sdk, do you have to go to sun and download it??
I wanted to use apt-get, but it doesn't look like it's in the database??
                                                                                  Larry :smile:

---

### Post by p!=f on 2005-04-16
You may ask backports developers for adding it to the repository.
There's a quick guide if you want to create a Debian package by your own:
[http://ubuntuforums.org/showpost.php?p=85019&postcount=4](http://ubuntuforums.org/showpost.php?p=85019&postcount=4)

---

### Post by i-tech on 2005-05-09
Try out these in your source.list
 > deb [http://debian.innovationsw.com/debian]("http://debian.innovationsw.com/debian") unstable/i386/ 
deb [http://debian.innovationsw.com/debian]("http://debian.innovationsw.com/debian") unstable/all/   it will work,enjoy!

---

### Post by defkewl on 2005-05-09
I think using the ones from sun is a good choice.

---

### Post by i-tech on 2005-05-09
the ones i said are sun's by the way .. :)

---

### Post by moser on 2005-05-10
[QUOTE=i-tech]the ones i said are sun's by the way .. :)[/QUOTE]
 How to install j2ee?

---

### Post by i-tech on 2005-05-10
Dont have any idea about Enterprise Edition. sorry :|

---

### Post by vague- on 2005-05-10
[QUOTE=moser]How to install j2ee?[/QUOTE]

I just unzipped J2EE (1.3.1) into /opt.  Then I added the J2EE_HOME environmental variable into my /etc/bash.env - it all works fine.  You might also wish to add $J2EE_HOME/bin to your PATH.  There is nothing complicated in the installation of J2EE...unless I did it wrong, but it works fine for me...

EDIT:  Forgot to mention, I also have $J2EE_HOME/lib/j2ee.jar in my classpath.  I am not sure if I found this necessary, or if I just did it during the setup for fun.

---

