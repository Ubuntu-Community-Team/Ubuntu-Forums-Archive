---
title: "Unable to install Google Chrome in Ubuntu 11.10"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by akshankumar on 2012-04-20
I downloaded google chrome debian file and now i am unable to install it. 
please help me with that

---

### Post by Kodeine on 2012-04-20
> **akshankumar said:**
> I downloaded google chrome debian file and now i am unable to install it. 
please help me with that

Why exactly can't you install it? You should be able to simply double click the file and gdebi or ubuntu software centre should open the package up. What happens when you double click it?

---

### Post by Ghil on 2012-04-20
you should install chromium instead. It's the same thing, without the Google branding and the data check. It's in the repos and is up to date, so it would be far easier for you to install.

(either check the ubuntu software center, or type sudo apt-get install chromium in a terminal)

---

### Post by IWantFroyo on 2012-04-20
```
sudo apt-get install chromium-browser
```

Same thing. Just not as branded.

If you really want to install the Googlized version:
```
cd ~/Downloads
```
```
sudo dpkg -i chrom*
```
Switch out chrom* with the beginning of the download. I don't remember what it's called.

---

### Post by ezzy25 on 2012-04-21
> **akshankumar said:**
> I downloaded google chrome debian file and now i am unable to install it. 
please help me with that
Consider it a blessing in disguise and install Opera instead :)

---

