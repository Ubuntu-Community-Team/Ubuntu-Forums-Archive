---
title: "Another  error when trying apt-get update?"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by wSsos on 2012-06-18
> **sisco311 said:**
> Open a terminal (Applications -> Accessories -> Terminal)
and:



```
gpg --keyserver keyserver.ubuntu.com --recv 8670a035
``````
gpg --export --armor 8670a035 | sudo apt-key add -
```


```
gpg --keyserver keyserver.ubuntu.com --recv 6e80c6b7
``````
gpg --export --armor 6e80c6b7 | sudo apt-key add -
```
Both of you: 
```
sudo apt-get update
```

Sorry but i have to include this here,
surely will help

For me, I got to use subkeys.pgp.net to work
gpg --keyserver subkeys.pgp.net --recv 8670a035
gpg --export --armor 8670a035 | sudo apt-key add -

In fact for me what happened was, I added the
[**Automatic PPA adder script**]("http://ubuntuforums.org/showthread.php?p=7737482#post7737482") from [Vermind]("http://ubuntuforums.org/member.php?u=264656")
Then I got the gpg error 
There's something wrong with Vermind's script?

Again, I know this is a OLD thread, but it's the first google link related with such Ubuntu key.

---

### Post by cariboo on 2012-06-18
Moved from a three year old thread, to a thread of it's own.

---

