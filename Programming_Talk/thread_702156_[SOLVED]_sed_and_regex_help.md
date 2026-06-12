---
title: "[SOLVED] sed and regex help"
date: 2008-02-20
forum: Programming Talk
---

### Post by datakid on 2008-02-20
I noticed the other day that my /var/log/apache2 folder was filling up with heaps and heaps of logs (>1500)

I am not going to stop logging, so please don't offer that as an answer :)

All of my log files are well named (in my mind) eg:

site1-error.log
site1-error.log.0
site1-error.log.1.tgz

site1-access.log
site1-access.log.0
site1-access.log.1.tgz

site2-error.log
site2-error.log.0
site2-error.log.1.tgz

site2-access.log
site2-access.log.0
site2-access.log.1.tgz

etc

So what I wanted to do was to break them into smaller chunks, based on sitename:

/var/log/apache2/site1/error.log
/var/log/apache2/site1/access.log
/var/log/apache2/site2/error.log
/var/log/apache2/site2/access.log

etc

This requires editing a lot of /etc/apache2/sites-available files...

sed '/ErrorLog/ s/\/.*-error.log/&\/error.log/g' bashtest.txt

almost works but gives me:

ErrorLog /var/log/apache2/webalizer-error.log/error.log
ErrorLog /var/log/apache2/wiki-error.log/error.log

instead of the desired

ErrorLog /var/log/apache2/webalizer/error.log
ErrorLog /var/log/apache2/wiki/error.log

I have tried replacing the & with \1 (as I read somewhere), $1 (common in this regard), $0, $@ but none seems to work?

Any ideas? Am I even using the right language? should I be using perl?

---

### Post by datakid on 2008-02-20
Actually, I am aware of the problem with perl:

s/\/.*-error.log/&\/error.log/g'

willl match the whole line (greedy) not just that one little bit....

---

### Post by ghostdog74 on 2008-02-20
what is in bashtest.txt?

---

### Post by datakid on 2008-02-20
it's just a list of parts of my vhosts files:

ErrorLog /var/log/apache2/site1-error.log
Errorlog /var/log/apache2/site2-error.log
ErrorLog /var/log/apache2/site3-error.log

CustomLog /var/log/apache2/site1-access.log combined
CustomLog /var/log/apache2/site2-access.log combined
CustomLog /var/log/apache2/site3-access.log combined

I was just using it for testing, later, I do the wrapping script :)

for $i in *
<change text in $i>

then I apply the script to my /etc/apache2/sites-available folder :)

---

### Post by ghostdog74 on 2008-02-20
> **datakid said:**
> 
sed '/ErrorLog/ s/\/.*-error.log/&\/error.log/g' bashtest.txt

almost works but gives me:

ErrorLog /var/log/apache2/webalizer-error.log/error.log
ErrorLog /var/log/apache2/wiki-error.log/error.log

instead of the desired

ErrorLog /var/log/apache2/webalizer/error.log
ErrorLog /var/log/apache2/wiki/error.log


I am still not sure what you wish to do, but anyhow, i will just assume you want this
```

ErrorLog /var/log/apache2/webalizer-error.log/error.log

```

 to become this
```

ErrorLog /var/log/apache2/webalizer/error.log

```

You could just substitute -error.log with blank
```

# sed 's/-error.log//' file
ErrorLog /var/log/apache2/webalizer/error.log
ErrorLog /var/log/apache2/wiki/error.log

```

---

### Post by datakid on 2008-02-21
of course - thanks for the help.

---

