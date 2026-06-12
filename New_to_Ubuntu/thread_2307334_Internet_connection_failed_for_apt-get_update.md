---
title: "Internet connection failed for apt-get update"
date: 2015-12-24
forum: New to Ubuntu
---

### Post by mic3 on 2015-12-24
I entered `sudo apt-get update` but got error messages saying 

```
index failed download.
```

I then typed "gksu software-properties-gtk" and had ubuntu choose the best regional server. It made sense because the university for that server is about an hour's drive from my residence. After I chose it I got a message saying 

```
the information about available software is out of date
```

When I clicked "reload", it attempted to update the cache and download some stuff until it showed the error saying 

```
the internet connection failed
```

That can't be right because my internet access is clearly working because I can surf the internet with no problems on this laptop, my phone, and another laptop. 

Does anyone know why this is happening?

---

### Post by Vladlenin5000 on 2015-12-24
Hi and welcome.

After changing the server did you run sudo apt-get update again? If so, what happened? If you noticed errors please post the complete error message.

---

### Post by mic3 on 2015-12-24
yes after changing the server I got the same error with sudo apt-get update. Here is the error output

```

Ign http://www.stats.bris.ac.uk wily/ Translation-en                           
Ign http://mega.nz ./ Translation-en_US                                        
Ign http://mega.nz ./ Translation-en                                           
Err http://ppa.launchpad.net wily/main amd64 Packages                          
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages                           
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US                       
Ign http://ppa.launchpad.net wily/main Translation-en                          
Err http://ppa.launchpad.net wily/main amd64 Packages                          
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages                           
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_US                       
Ign http://ppa.launchpad.net wily/main Translation-en                          
Fetched 6,543 B in 9s (684 B/s)                                                
W: Failed to fetch http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/marutter/rdev/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/marutter/rdev/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Vladlenin5000 on 2015-12-24
All I see are errors regarding third party PPAs and those are to be expected considering neither PPA has support for 15.10 so you should remove them. After that the errors will go away. And, in spite of those errors, you can update/upgrade/dist-upgrade just fine.

---

