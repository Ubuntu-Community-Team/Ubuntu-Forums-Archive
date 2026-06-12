---
title: "Sudo Update Error"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by boomz on 2012-10-19
I tried to update my ubuntu, because I wanted to install gnome-shell extensions for theme installation. But everytime I update I always get this error:

```
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
```

A long list follows then and it ends with:

```
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I hope I have answers to this. :) Thank you so much!

---

### Post by SlugSlug on 2012-10-19
follw steps here

[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by BlastXng on 2012-11-30
In terminal put the following in..

gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783      
gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -

Replace the key "2EBC26B60C5A2783" with the key you get in your error message..

---

### Post by monkeybrain2012 on 2012-11-30
> **BlastXng said:**
> In terminal put the following in..

```
gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783      
gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -
```

Replace the key "2EBC26B60C5A2783" with the key you get in your error message..

Or install the script launchpad-getkeys

and run 

```
sudo launchpad-getkeys 

```
whenever encounter a gpg error


[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)


Since I can't remember these commands (I doubt that many people can) and I find it very cumbersome to have to look them up everytime when I get an error, launchpad-getkeys is less hassle for me.

---

