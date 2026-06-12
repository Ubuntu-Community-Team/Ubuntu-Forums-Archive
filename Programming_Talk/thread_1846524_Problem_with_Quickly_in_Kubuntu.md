---
title: "Problem with Quickly in Kubuntu"
date: 2011-09-19
forum: Programming Talk
---

### Post by PeteAsdf on 2011-09-19
Hi,

Total noob to programming under Ubuntu and Quickly.
I tried to create my 1st app using Quickly:

The create and design phases went OK
However when I then run 'quickly edit' to edit the Python code, I'm getting an error message (see attached).

I have both Python 2.7 and 3.2 installed.

Can you pls let me know what is wrong? i really have no idea...

Thanks a lot

---

### Post by Smart Viking on 2011-09-19
Post the source code of your program. In CODE tags.

---

### Post by PeteAsdf on 2011-09-19
Hi,

My source code would be just the system generated code, I did not touch anything in the code yet, i.e. I do the following:

quickly create ubuntu-application new_app_name
cd new_app_name
quickly edit

... and that's when I'm getting that error message, before I touch anything.

Do you really want me to send the source code (I guess it doesn't make much sense since it should be the default Quickly new app code)?

Thanks

---

### Post by Smart Viking on 2011-09-20
Do you use KDE?

It seems like you need to have "yelp" installed, maybe that's the problem.

run:
```
sudo apt-get install yelp
```


[https://bugs.launchpad.net/quickly/+bug/559565](https://bugs.launchpad.net/quickly/+bug/559565)

---

### Post by BadOmen on 2012-01-20
Hi, I got the same problem but I solved it by installing gedit. quickly is using it as default editor. 

yelp was already installed so I don't know if I needed it or not.

---

