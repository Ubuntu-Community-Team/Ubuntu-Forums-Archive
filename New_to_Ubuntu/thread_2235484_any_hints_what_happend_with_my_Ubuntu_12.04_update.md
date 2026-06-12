---
title: "any hints what happend with my Ubuntu 12.04 update?"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by fenghc on 2014-07-21
Dear All, 

I have a trouble to updating Ubuntu system (12.04). I got these messages as following, 

Anyone can help me?  Thanks a lot in advance. 

>>>>>>>>>>>>>>>>>>

```
$ sudo apt-get update -d
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg
Hit [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Release.gpg    
Hit [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Release        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg
Hit [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release
Ign [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Translation-en_US
Ign [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-security/universe Translation-en
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Impavidus on 2014-07-21
Thi is all refering to quantal, which is Ubuntu 12.10 (not 12.04 LTS) and is unsupported. Did you try upgrading to the next release instead of to the next LTS release?

---

### Post by plucky on 2014-07-21
You seem to be running 12.10 which has reached EOL and so the repositories have closed.

12.04 is codenamed Precise Pangolin whereas 12.10 is Quantal Quetzel which are the repositories you are trying to access.

If you just tried to do a distribution upgrade from 12.04 to 14.04,you need to specify in Software Sources to upgrade to LTS releases only or it will try to upgrade to 12.10.

 > sudo apt-get update -d


The -d with apt-get means download only.

Is that the command that you wanted to run?

If your sources.list is pointing to Quantal instead of Precise you will get the 404 errors.

Exactly what were you trying to do?

---

### Post by fenghc on 2014-07-21
Yes. You're right. I'd like to upgrade to next LTS version. What should I do next?  Thanks a lot.

---

### Post by plucky on 2014-07-21
I am not sure if it is possible to backtrack,but since quantal is no longer there,you might be able to change your sources.list back to precise.

The command to use is ```
sudo sed -i 's/quantal/precise/g' /etc/apt/sources.list
```

Not sure if this will work as you also have **Hit [http://cran.rstudio.com](http://cran.rstudio.com) quantal/ Packages** which, if it is not in your sources.list file, will not be changed with the above command.

Then run ```
 sudo apt-get update && sudo apt-get upgrade
``` to see if it goes back to precise.

If that works,open Software Sources and change the Release upgrades to LTS only (see attachment).

Then wait until 14.04.1 is released and you should then be offered the upgrade path.

Good Luck

---

