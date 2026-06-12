---
title: "ImportError: No module named 'netifaces'"
date: 2017-11-14
forum: New to Ubuntu
---

### Post by afestivedolphin on 2017-11-14
Hey everyone, I'm extremely new here and I apologize if this question has been asked before (I searched already posted but it kept 404ing me when I tried to look in the posts) But I have sort of a weird error I can't figure out what to do. I know it has to do with python.

My code: 
```
python3 -u phillip/train.py --load saves/Fox_Vs_Any --gpu
```

Error:
```
Traceback (most recent call last):
  File "phillip/train.py", line 12, in <module>
    import netifaces
ImportError: No module named 'netifaces'


```
I've tried a couple of different fixes such as ```
sudo python setup.py install
``` and ```
sudo pip install netifaces
``` I just get ```
Requirement already satisfied: netifaces in /usr/local/lib/python2.7/dist-packages/netifaces-0.10.6-py2.7-linux-x86_64.egg

```



If you want some context on what I'm doing it's installing a silly AI for a game I like: [https://www.youtube.com/watch?v=hxzpK719wV4&feature=youtu.be&](https://www.youtube.com/watch?v=hxzpK719wV4&feature=youtu.be&)

If you need more information just let me know :)

Thanks in advanced for your guy's help I'm really enjoying the system so far!

---

### Post by Holger_Gehrke on 2017-11-15
Python 2.x and 3.x are rather different from each other. You've got a netifaces module for Python 2.7 but are running your program with python3. You need a netifaces module for Python3. I don't know how to do this with pip, but on current Ubuntus there is a package python3-netifaces in the repositories, so "apt install python3-netifaces" should help.

Holger

---

