---
title: "Failed to download package files"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by archangel2003 on 2012-04-02
I have a 64 bit computer running the 11 version of Ubuntu
Update manager said there were 13 updates ready for me.

I clicked yes and entered my authorization and it started to do it's thing.

When it tried to do it's usual update it said one security update did not download but still showed all 13 as ready to go.

Here is what it tells me when I try to install.

                                  Failed to download package files
  
                                  Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20110912ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20110912ubuntu3.1_all.deb) 404  Not Found [IP: 91.189.92.166 80]
  
Any Ideas?

---

### Post by santosh83 on 2012-04-02
> **archangel2003 said:**
> I have a 64 bit computer running the 11 version of Ubuntu
Update manager said there were 13 updates ready for me.

I clicked yes and entered my authorization and it started to do it's thing.

When it tried to do it's usual update it said one security update did not download but still showed all 13 as ready to go.

Here is what it tells me when I try to install.

                                  Failed to download package files
  
                                  Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20110912ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20110912ubuntu3.1_all.deb) 404  Not Found [IP: 91.189.92.166 80]
  
Any Ideas?

Hi,
Did you try refreshing the package lists and re-fetching information by entering
```
sudo apt-get update
```
once more?

---

### Post by kazztan0325 on 2012-04-02
Hi archangel2003,

I also received and updated the package **"ca-certificates-java"** as one of security updates from 'security.ubuntu.com' on my 11.10 x64 machine a few days ago.
But its version is '_20110912ubuntu**3.2**_', not '_20110912ubuntu**3.1**_'.

Since its latest version is '3.2', it is no wonder there is not the previous version of package on the server anymore.

I also don't know why did you encounter with the happening...

What about trying to re-install the package?

---

### Post by archangel2003 on 2012-04-03
[SIZE=3]I tried several times that same day and it did not work, but the next day (today) it showed 13 updates again and it worked this time.

With Ubuntu 10 there were various packages that had something that was unsuccessful with regards to installation, but the rest seemed to install fine.  [/SIZE]
[SIZE=3]
Thanks for the help.[/SIZE]

---

### Post by kazztan0325 on 2012-04-03
You are welcome, archangel2003!

I'm glad to hear you have solved the problem.

See you again someday somewhere in this Forums.

---

