---
title: "How do i install from a terminal"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Peterfc on 2008-05-09
I have installed from a terminal before but can't remember how. I have downloaded to my desktop. the program is java. Can anybody help. 

Thanks for reading this post

jre-6u5-linux-i586.bin

---

### Post by hermes0710 on 2008-05-09
Locate the folder which contains the setup application and type (I think):

./jre-6u5-linux-i586.bin

---

### Post by kesman on 2008-05-09
You can install java from apt with
```

sudo apt-get install packagename

```
the name of the package can be found with
```

apt-cache search sun java jre6

```

You can also install packages with add/remove applications or synaptic package manager.

---

### Post by jken146 on 2008-05-09
Java is in the repositories, so the best way to install it is by typing ```
sudo apt-get install sun-java6-jre
```

---

### Post by abhiroopb on 2008-05-09
Are you trying to install specifically the .bin file? Or are you asking generally how to use the terminal?

For the .bin file:
If the installer is called test.bin and is located on the user carl's desktop, you can run it inside your terminal with /home/carl/Desktop/test.bin.

But is there any reason you are trying to install java like this?

Easier way would be: 
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

Generally: 
This is very useful: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by logos34 on 2008-05-09
like they say above, get it from the repos preferably

But for future ref:

to run a .bin installer, you may need to make it executable first:

sudo chmod a+x file.bin

---

### Post by Peterfc on 2008-05-09
Thanks you all.

I have had this answered before. Is there a way to find my previous posts. This would save me and you time.  Thanks to you all.

---

### Post by billgoldberg on 2008-05-09
If you logged in, there is a brownish bar where you see "user cp" "forum hlep" ...

There is also "search", click on it and press "find all your threads".

---

