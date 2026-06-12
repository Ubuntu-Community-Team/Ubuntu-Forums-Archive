---
title: "Chmod and Chown"
date: 2014-09-14
forum: New to Ubuntu
---

### Post by iBabin on 2014-09-14
Hello, 

I tried to understand myself before asking but it doesn't work :(

What I did wrong ?

1 - I created 2 Users  : userA  and UserB
2- I created a group
  ```
 sudo addgroup media
```
3- I add userA and UserB to that group media

```
sudo adduser userA media
sudo adduser userB media

```

4- I want to give access the the directory media to the group media
This is where I'm lost

is it 

```
sudo chgrp -R media /media

```
thank for your time

---

### Post by Impavidus on 2014-09-14
I don't think it's such a good idea to change the group of /media or any other directory existing by default as there are programs expecting those directories to have certain properties, but other than that, the command is correct. Also note that file systems mounted under /media may not always support users, groups and permissions. Usually they don't. If they don't, then those properties are set by the mount options instead of chown, chgrp and chmod.

---

