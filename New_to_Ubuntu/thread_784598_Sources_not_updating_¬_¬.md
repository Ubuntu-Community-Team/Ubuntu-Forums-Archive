---
title: "Sources not updating ¬_¬"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by skymera on 2008-05-06
Ok this is the output of apt-get update..

```
 <cut here>
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Hit http://archive.ubuntu.com hardy-backports/main Packages                    
Hit http://archive.ubuntu.com hardy-backports/restricted Packages              
Hit http://archive.ubuntu.com hardy-backports/universe Packages                
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages              
Hit http://archive.ubuntu.com hardy-security/main Packages                     
Hit http://archive.ubuntu.com hardy-security/restricted Packages               
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages               
Hit http://archive.ubuntu.com hardy-proposed/main Packages                     
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages               
Hit http://archive.ubuntu.com hardy-proposed/universe Packages                 
Fetched 1B in 11s (0B/s)                                                       
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
scott@scott-desktop:~$ 

```

Err why basically? it was running fine.

---

### Post by Grishka on 2008-05-06
switch to the repos for your country in software sources.

---

### Post by zveox on 2008-05-06
> **Grishka said:**
> switch to the repos for your country in software sources.
I am having same issue..every time i update the repo or try to download any package it fails...i tried switching to both main server and the country one but still no luck...

---

### Post by skymera on 2008-05-06
Changed server and i get the same error. =X

---

### Post by GoodWizard on 2008-05-06
same here, it always take me a long time to make the connection with the server. and often times it gave me a error of saying certain file was not downloaded or such...

---

### Post by philinux on 2008-05-06
There's been a few updates I think the servers are taking a bashing. Try again later.

---

### Post by skymera on 2008-05-06
I've gone to WinXP for stability and Ubuntu doing my head in >_<

---

### Post by Nunslaughter on 2008-05-08
I just helped someone on the Dutch forum who had the same problem. It appeared that he had the word "web" after some sources in his sources.list.

example:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted web
```

Check your sources.list, and remove the word "web" if it is there. Then try again to sudo apt-get update.

---

### Post by skymera on 2008-05-08
I removed all my sources and ran the sources-admin thing and it replaces my list.

Thanks anywhoo =D

---

### Post by diegomedaglia on 2008-05-11
> **Nunslaughter said:**
> I just helped someone on the Dutch forum who had the same problem. It appeared that he had the word "web" after some sources in his sources.list.

example:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted web
```

Check your sources.list, and remove the word "web" if it is there. Then try again to sudo apt-get update.
That did it for me as well. Thanks!

---

