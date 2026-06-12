---
title: "encountering error while using :sudo apt-get install ubuntu-restricted-extrals"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by Sec Expert on 2008-09-29
hello dear guys & gals!
while I try to perform the mentioned command I receive some errors](*,) as followings(by the way I wanna do this becasue I can't listen to music):

khh@khh-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for khh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 281 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kpkeerthi on 2008-09-29
Try reinstalling the package
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install ubuntu-restricted-extras

```

---

### Post by DougieFresh4U on 2008-09-29
Try:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by Elfy on 2008-09-29
I think you are maybe behind a proxy - check System -> Preferences -> NetworkProxy

Set to direct connection and see if it works then, set it back afterwards if that is how you normally have it set

---

### Post by Knot_Sharpe on 2008-09-30
> **DougieFresh4U said:**
> Try:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

Hello!  thanks for the suggestion, I have similar probs with msttcorefonts errors. I tried your command suggestion above and this was the result:

gary@gary-ibm:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gary@gary-ibm:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
gary@gary-ibm:~$ 


How do I unlock or stop or identify this "process"?

Much thanks!

---

### Post by kpkeerthi on 2008-10-01
> **Knot_Sharpe said:**
> Hello!  thanks for the suggestion, I have similar probs with msttcorefonts errors. I tried your command suggestion above and this was the result:

gary@gary-ibm:~$ sudo apt-get -f install
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gary@gary-ibm:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process
gary@gary-ibm:~$ 


How do I unlock or stop or identify this "process"?

Much thanks!

You can have only one package manager (apt-get/aptitude/dpkg/synaptic/update manager) running at a time. Close the one you have opened in the background. Or reboot, if the problem persists.

---

### Post by Sec Expert on 2008-10-01
> **kpkeerthi said:**
> Try reinstalling the package
```

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install ubuntu-restricted-extras

```

It takes a long time I can't do this by my 128 kb connection!I also have a limited download bandwidth.Isn't there another way.

> **DougieFresh4U said:**
> Try:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

you see it leads to the same result:

khh@khh-desktop:~$ [COLOR="Red"]sudo apt-get -f install[/COLOR]
[sudo] password for khh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

                       --------------------------------
khh@khh-desktop:~$ [COLOR="Red"]sudo dpkg --configure -a[/COLOR]
[sudo] password for khh: 
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts

> **forestpixie said:**
> I think you are maybe behind a proxy - check System -> Preferences -> NetworkProxy

Set to direct connection and see if it works then, set it back afterwards if that is how you normally have it set

no I checked the sttings for "Network Proxy".I use direct internet connection.
](*,)](*,)](*,)

---

### Post by kpkeerthi on 2008-10-01
You seemed to have configured your system to use proxy server but the proxy host name appears to be blank. However, the proxy port is specified as 8080.

Can you post a screenshot of System -> Preferences -> Network Proxy ? (* I will not be able to view if you upload the screenshot to online image hosting services like imageshack. Upload along with your post to ubuntuforums server)

Also post the output of below command:
```
cat /etc/apt/apt.conf.d/proxy.conf
```

---

### Post by rybaxs on 2008-10-01
do you multi-installation process or downloads? for example " your downloading something in the synaptic P.M. and then "sudo apt-get install ****" on the terminal or any installation method. 

like "kpkeerthi" > You can have only one package manager (apt-get/aptitude/dpkg/synaptic/update manager) running at a time. Close the one you have opened in the background. Or reboot, if the problem persists.

---

### Post by Sec Expert on 2008-10-01
> **kpkeerthi said:**
> You seemed to have configured your system to use proxy server but the proxy host name appears to be blank. However, the proxy port is specified as 8080.

Can you post a screenshot of System -> Preferences -> Network Proxy ? (* I will not be able to view if you upload the screenshot to online image hosting services like imageshack. Upload along with your post to ubuntuforums server)

Also post the output of below command:
```
cat /etc/apt/apt.conf.d/proxy.conf
```

The screenshot is attached.


The output:

khh@khh-desktop:~$ cat /etc/apt/apt.conf.d/proxy.conf
cat: /etc/apt/apt.conf.d/proxy.conf: No such file or directory
khh@khh-desktop:~$ 

> **rybaxs said:**
> do you multi-installation process or downloads? for example " your downloading something in the synaptic P.M. and then "sudo apt-get install ****" on the terminal or any installation method. 

like "kpkeerthi"

no I don't think so.

---

### Post by kpkeerthi on 2008-10-01
If you look closely in the screenshot, you see 8080 specified against the Port number. I'm guessing it is causing apt-get to misbehave. You may want change that to 0. Also click on the **Details** button to make sure everything looks OK there.

---

### Post by SupaSonic on 2008-10-01
Seeing as how installing ms fonts is the issue and this happens in the setup phase, I'm thinking the site with the fonts is down. AFAIK, the fonts are pulled from some 3rd party site in the setup phase, just like flash player is pulled from adobe.

Have a look here - [http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

Try to apt-get everything except the fonts

---

