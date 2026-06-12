---
title: "Issue: Installation of Utopia-Documents (universe repository)"
date: 2016-01-07
forum: New to Ubuntu
---

### Post by schwobi on 2016-01-07
I am running Ubuntu 15.10 (64-bit), GNOME desktop interface on the following machine: Lenovo-ThinkPad-L450, Intel® Core&#8482; i5-5200U CPU @ 2.20GHz × 4, Intel® HD Graphics 5500 (Broadwell GT2).  

I would like to install **Utopia-Documents** (universe repository), which is an scientific .pdf-reader with advanced interaction/reserach possibilities. 
To do so, I followed the instructions given on [http://utopiadocs.com/linux/](http://utopiadocs.com/linux/) , which included the following: 
> I enabled the universe repositories using the respective settings in the Software-Updater. 
> I downloaded and installed the updated keyring using the Ubuntu Software Center: [http://utopiadocs.com/apt/pool/main/u/utopia-keyring/utopia-keyring_2014.06.16_all.deb](http://utopiadocs.com/apt/pool/main/u/utopia-keyring/utopia-keyring_2014.06.16_all.deb) 
>  I entered the terminal commands: ```
(echo "deb http://utopiadocs.com/apt $(lsb_release -cs) main"; echo "deb-src http://utopiadocs.com/apt $(lsb_release -cs) main") | sudo tee /etc/apt/sources.list.d/utopia.list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install utopia-keyring && sudo apt-get --quiet update && sudo apt-get install utopia-documents
``` 

, wherein either ```
sudo apt-get  --quiet update
``` or  ```
sudo apt-get update
``` returned the following errors: > W: Failed to fetch [http://utopiadocs.com/apt/dists/wily/main/source/Sources](http://utopiadocs.com/apt/dists/wily/main/source/Sources)  404  Not Found  
W: Failed to fetch [http://utopiadocs.com/apt/dists/wily/main/binary-amd64/Packages](http://utopiadocs.com/apt/dists/wily/main/binary-amd64/Packages)  404  Not Found  
W: Failed to fetch [http://utopiadocs.com/apt/dists/wily/main/binary-i386/Packages](http://utopiadocs.com/apt/dists/wily/main/binary-i386/Packages)  404  Not Found  
E: Some index files failed to download. They have been ignored, or old ones used instead. 

 Because of the encountered issues, the ```
sudo apt-get install utopia-documents
``` command was not executed as part of the echo-string.  Nevertheless, therefore I tried to install Utopia documents using both, either manually typing in this command, or via the Ubuntu Software Center. Either resulted in the application to install (seemingly?) successfully, but left me unable to launch the application: ```
utopia documents
``` returned the following error: > Segmentation fault (core dumped).       


Since I am not able to reach [http://utopiadocs.com/apt/dists/wily/main/](http://utopiadocs.com/apt/dists/wily/main/)... via Firefox Webbrowser, it seems the server is down.(?)   
Does anyone have an idea where to get a working copy of this package and its dependencies?  
Thank You very much in advance. :)

---

### Post by sergio53 on 2016-01-07
try sudo apt-get remove --autoremove utopia-documents
or sudo apt-get remove --purge utopia-documents
and install again
mine works ok.

~Kali Linux with LXDE

---

### Post by claracc on 2016-01-07
The server is not down, I copy the url in firefox: [http://utopiadocs.com/apt/dists/wily/main/source/Sources](http://utopiadocs.com/apt/dists/wily/main/source/Sources) and I obtain the 404 error not found, since the software package is not in the server:

```
Not Found

The requested URL /apt/dists/wily/main/source/Sources was not found on this server.
Apache/2.2.22 (Debian) Server at utopiadocs.com Port 80
```

[http://utopiadocs.com/linux/](http://utopiadocs.com/linux/) page, explicitily says that ubuntu 12.04 and 14.04 are supported but they don't mention ubuntu 15.10, so I think you cannot install it in the esy and common way but you probably will have to use source code compiling and installing.

---

### Post by schwobi on 2016-01-07
> **sergio53 said:**
> try sudo apt-get remove --autoremove utopia-documents
or sudo apt-get remove --purge utopia-documents
and install again
mine works ok.

~Kali Linux with LXDE

I allready tried this; does unfortunately not seem to have any effect.


> **claracc said:**
> The server is not down, I copy the url in firefox: [http://utopiadocs.com/apt/dists/wily/main/source/Sources](http://utopiadocs.com/apt/dists/wily/main/source/Sources) and I obtain the 404 error not found, since the software package is not in the server:

```
Not Found

The requested URL /apt/dists/wily/main/source/Sources was not found on this server.
Apache/2.2.22 (Debian) Server at utopiadocs.com Port 80
```

[http://utopiadocs.com/linux/](http://utopiadocs.com/linux/)  page, explicitily says that ubuntu 12.04 and 14.04 are supported but  they don't mention ubuntu 15.10, so I think you cannot install it in the  esy and common way but you probably will have to use source code  compiling and installing.

If I got You right, You suggest to configure/install a .tar file; i.e. one of the ones found at [http://utopiadocs.com/files/linux/](http://utopiadocs.com/files/linux/) ?
Maybe I am too incompetent, but there does not seem to be a README or INSTALL file to be included in those packages, so I am struggling a little with configuration...

---

