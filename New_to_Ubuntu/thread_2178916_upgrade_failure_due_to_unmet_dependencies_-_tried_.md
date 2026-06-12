---
title: "upgrade failure due to unmet dependencies - tried every fix I can find"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Midemeanor on 2013-10-05
Hi first post so sorry if any rules are broken here
I have searched ubuntu forums, askubuntu, laucnpad and everywhere else for a fix and tried all of the fixes I could find but my problem remains unresolved 

i am using ubuntu 12.04 lts but have tried to upgrade to 12.10 and the latest 13 something both failed due to unmet dependencies 

occasionally I get system error messages saying ubuntu 12.10 has experienced and internal error so I guess the system has an identity problem due to a failed upgrade from 12.04 to 12.10 

I have the unmet dependencies as listed below - I have tried all the apt-get -f options ( update, install, upgrade, clean), synaptic package manager does not fix broken packages, ubuntu software centre report broken cache and tries to fix the catalogue over and over again that fails due to the dependency issues ,  I even tred to edit the staus file following a remedy in another link to fix the initramfs problem, I have also tried to manually install matching versions of initramfs-tools and iniramfs-tools bin but no success, I have also tried to remove old kernels which wont go.

if anyone else knows something eske to try I will be grateful thanks
  



**on trying to upgrade this is the results **

dpkg: dependency problems prevent configuration of initramfs-tools:
 klibc-utils (2.0.1-1ubuntu2) breaks initramfs-tools (<< 0.103) and is installed.
  Version of initramfs-tools to be configured is 0.99ubuntu13.1.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on mountall (>= 2.28); however:
  Package mountall is not configured yet.
dpkg: error processing initscripts (--configure):
 No apport report written because MaxReports has already been reached
           No apport report written because MaxReports has already been reached
                     No apport report written because MaxReports has already been reached
  No apport report written because MaxReports has already been reached
            No apport report written because MaxReports has already been reached
                      No apport report written because MaxReports has already been reached
   No apport report written because MaxReports has already been reached
             dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on initscripts; however:
  Package initscripts is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of passwd:
 passwd depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
dpkg: error processing passwd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of module-init-tools:
 module-init-tools depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
dpkg: error processing module-init-tools (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 plymouth
 mountall
 initscripts
 upstart
 passwd
 module-init-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by heir4c on 2013-10-05
> dpkg: dependency problems prevent configuration of initramfs-tools:
klibc-utils (2.0.1-1ubuntu2) breaks initramfs-tools (<< 0.103) and is installed.
Version of initramfs-tools to be configured is 0.99ubuntu13.1.


Can you open the SoftwareCenter (or Synaptic if it's installed)?
Search for klibc-utils and initramfs-tools.
When you find that you click on it and than click the button with "more info" (or "more information" Don't now what it is in the English version, I use Dutch version)
It open and you can find there the version of the packages.

---

### Post by Midemeanor on 2013-10-05
hi using ubuntu software centre the klibc-utils version is 

klibc-utils 2.0.1-1ubuntu2

let me know if that tells you anything helpful? 
thanks

---

### Post by heir4c on 2013-10-05
Not at the moment, but I try to find something (or somebody else can help)
What version is initramfs-tools
This 2 packages conflict with each other, I believe it is klibc-utils "breaks" the initramfs-tools because that is a older version.

What you maybe can do is open 'Software & Updates" (that take a while) and in the third tab you disable the backports.
Than on the first tab: change the server for download the repo's.
And try again to update (just update, no upgrade for now).
If that give you no errors you can upgrade.

---

### Post by whitesmith on 2013-10-05
Just to satisfy my curiosity, why did you upgrade from 12.04 (a stable LTS good for another 4 years) for 12.10 for which support will expire in April, 2014--just 7 months from now? See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) for more info. You don't appear to be doing yourself any favors unless you are motivated by factors I don't understand.

---

### Post by heir4c on 2013-10-05
I find something.
klibc-utils is now in your system version 2.0.1-1ubuntu2 and that breaks every version of initramfs-tools that is older than the 0.103 versions. On your system I think (from what I see in the error message) the version of initramfs-tools is now a 0.99 version. 
So, there is a problem. 
klibc-utils version 2.0.1-1ubuntu2 needs a 0.103 vresion of initramfs-tools.

Info:
In the link below you can find the package who belong to every Ubuntu version. And when you click on it you see the packages it depends on:
[http://packages.ubuntu.com/search?lang=en&suite=default&arch=any&searchon=names&keywords=initramfs-tools](http://packages.ubuntu.com/search?lang=en&suite=default&arch=any&searchon=names&keywords=initramfs-tools)
Look at precise and precise-updates and quantal and raring. And see the difference in the versions of the packages initramfs-tools (on top) and the klibc-utils (in the list)

So what you can do is uninstall the initramfs-tools version on your system now (Maybe you get errors/messages of depending package they will remove to, so be very careful with removing.)
Or download the right package of initramfs-tools from that page (the quantal or raring version) and install it on the system yourself and do than an update.
But of that solved the problem or give more (because of the other packages in the error message, I don't now. 
You can try,but give it too much trouble you can do a totally new install of 13.04.

Edit:  
I see now what whitesmith write and maybe he is right. The versions between the LTS version have now less support than in the past. So, maybe you can do a new install but with 12.04 again. (Yes return to the LTS)

---

### Post by squakie on 2013-10-05
It sounds like your updates partially worked.  By that I mean it sounds to me like you have some of the newer libs, etc., from you failed updates and they are conflicting with what you have left of 12.04.   As to whether you stay at 12.04, go to 12.10 or to 13.04, that is you decision.  Either way around, you would probably be best off to backup what you need, then do a complete clean install of whatever version.  Right now the mix is messing things up for you, and I don't think there is any simple way out.

---

