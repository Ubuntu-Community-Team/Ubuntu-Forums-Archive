---
title: "update problem"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-07
i tried to update through the update interface managment but...
i got an error here: 
```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  

Some index files failed to download, they have been ignored, or old ones used instead.

```

then i tried manually to update but then i got a hit here:
```

...
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release                     
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://gb.archive.ubuntu.com hardy-updates Release               
Hit http://gb.archive.ubuntu.com hardy/main Packages                
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
84% [Waiting for headers]                      


```

so what's up?

---

### Post by perlluver on 2008-05-07
> **lunaluna said:**
> i tried to update through the update interface managment but...
i got an error here: 
```

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_GB.bz2  

Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_GB.bz2  

Some index files failed to download, they have been ignored, or old ones used instead.

```

then i tried manually to update but then i got a hit here:
```

...
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release                     
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://gb.archive.ubuntu.com hardy-updates Release               
Hit http://gb.archive.ubuntu.com hardy/main Packages                
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
84% [Waiting for headers]                      


```

so what's up?

Try to select another mirror, that mirror might be down right now.

---

### Post by sharks on 2008-05-07
Yes , i also got this error today. Not solved yet.

---

### Post by lunaluna on 2008-05-07
i tried some others but i still getting a hit on the (en) English language packages 
could someone check if he also gets the same hits/or is it just me?

---

### Post by glennric on 2008-05-07
Try to open synaptic, select Settings->Repositories, and in the "Downloaded From" drop down in the "Ubuntu Software" tab select "Other...".  Then click on "Select Best Server".  This will do some tests and pick the fastest server for you.

---

### Post by Kevbert on 2008-05-07
It seems the servers were a little busy earlier today.  I just left/retried the updates and eventually they worked.

---

### Post by sharks on 2008-05-07
Yes its now working.

---

