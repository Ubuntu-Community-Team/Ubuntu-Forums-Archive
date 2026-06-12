---
title: "Ubuntu 12.04 Softwares Update Problem (-5 - No address associated with hostname)"
date: 2012-10-13
forum: New to Ubuntu
---

### Post by kronomia on 2012-10-13
**Problem Description:**

Each time i try to download the updates for my operating system (Ubuntu 12.04) i get the following list of error messages: 

```
    W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
    , W:Failed to fetch [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
    , W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
    , W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
    , W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
    , E:Some index files failed to download. They have been ignored, or old ones used instead.
```

**The Contents of (/etc/apt/sources.list) File:** 

   ```
 # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
    
    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    # newer versions of the distribution.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
    
    ## Major bug fix updates produced after the final release of the
    ## distribution.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    
    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    ## team. Also, please note that software in universe WILL NOT receive any
    ## review or updates from the Ubuntu security team.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    
    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    ## team, and may not be under a free licence. Please satisfy yourself as to 
    ## your rights to use the software. Also, please note that software in 
    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    ## security team.
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    
    ## N.B. software from this repository may not have been tested as
    ## extensively as that contained in the main release, although it includes
    ## newer versions of some applications which may provide useful features.
    ## Also, please note that software in backports WILL NOT receive any review
    ## or updates from the Ubuntu security team.
    
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    
    ## Uncomment the following two lines to add software from Canonical's
    ## 'partner' repository.
    ## This software is not part of Ubuntu, but is offered by Canonical and the
    ## respective vendors as a service to Ubuntu users.
    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    
    ## This software is not part of Ubuntu, but is offered by third-party
    ## developers who want to ship their latest software.
    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```


**The Files inside of (/etc/apt/sources.list.d) directory: **

    ```
-rw-r--r-- 1 root root 136 Oct 10 16:30 deluge-team-ppa-precise.list    
    -rw-r--r-- 1 root root 136 Oct 10 16:30 deluge-team-ppa-precise.list.save         
    -rw-r--r-- 1 root root 285 Oct 10 16:30 medibuntu.list        
    -rw-r--r-- 1 root root 285 Oct 10 16:30 medibuntu.list.save          
    -rw-r--r-- 1 root root 132 Oct 10 16:30 tualatrix-ppa-precise.list         
    -rw-r--r-- 1 root root 134 Oct 10 16:30 tualatrix-ppa-precise.list.save          
    -rw-r--r-- 1 root root 148 Oct 10 16:30 yannubuntu-boot-repair-precise.list       
    -rw-r--r-- 1 root root 148 Oct 10 16:30 yannubuntu-boot-repair-precise.list.save
```  


**I have tried to research online for ways to solve the issue but i failed to figure out the real reason why i am getting those errors. Any suggestions, ideas or solutions that might aid me to solve this issue are greatly appreciated.**

---

### Post by Gone fishing on 2012-10-13
Something wicked happened resolving ....

Makes me think that the problem is not in your box but your connection to the internet.

If you try to follow one of your sources such as [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg) in a web browser can you get there or do you get a page not found? If so the problem is your connection to the internet - probably unless you have a bizare hosts file or something.

---

### Post by kronomia on 2012-10-13
> **Gone fishing said:**
> Something wicked happened resolving ....

Makes me think that the problem is not in your box but your connection to the internet.

If you try to follow one of your sources such as [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg) in a web browser can you get there or do you get a page not found? If so the problem is your connection to the internet - probably unless you have a bizare hosts file or something.

My Internet connection is working perfectly without any problems. In addition to that, the link of [http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/deluge-team/ppa/ubuntu/dists/precise/Release.gpg) is opening perfectly in all of my web browsers.

I have been using Ubuntu for years and this is the first time to experience something like that.

I would really appreciate any further ideas or suggestions. Thanks

---

### Post by Gone fishing on 2012-10-13
OK a little research suggests that you arn't the only person to have this problem but it is probably to do with name resolution when connecting to the internet.

> 

This worked for me ! Thanks for posting

I was experiencing a similar problem myself.

Unless you've already changed one of these settings, what's basically happening is that NetworkManager is setting your router up as the DNS server, and the router should use your ISP's DNS server to resolve addresses. Somewhere in there, addresses aren't all being resolved correctly, hence "no address associated with hostname". If you want to see what's being used to resolve addresses, open /etc/resolv.conf

NetworkManager can easily be set up to always use a manually-specified DNS server when using a given network. Under "Edit Connections..." select the network where the issue is occurring (selecting the proper tab at the top, if necessary), and click Edit. Under the "IPv4 Settings" tab, set the Method to "Automatic (DHCP) addresses only" and enter a third-party DNS server (e.g., Google's 8.8.8.8 ).

With any luck, this should solve your problem.

[http://ubuntuforums.org/archive/index.php/t-1475399.html](http://ubuntuforums.org/archive/index.php/t-1475399.html)

and

[http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating](http://askubuntu.com/questions/142508/how-to-fix-5-no-address-associated-with-hostname-error-while-updating)

---

### Post by kronomia on 2012-10-13
Thanks so much! You were right.
The solution to this problem goes as follows:

**Step 1:** Go to System –> Preferences –> Network Connections.

**Step 2:** Next, select your default Network Interface (eth0) and click ‘Edit’.

**Step 3:** Then select ‘IPv4 Settings’ and choose ‘Automatic (DHCP) addresses only’.

**Step 4:** Next, enter the new DNS server addresses in the ‘DNS servers’ box. Use commas to separate multiple addresses and click ‘Apply’ to save.

**Step 5:** Choose your preferred DNS details

```
OpenDNS           --->  208.67.222.222, 208.67.220.220              
Google Public DNS --->  8.8.8.8, 8.8.4.4                 
Comodo Secure DNS --->  156.154.70.22, 156.154.71.22
```

After configuring, check to make sure it is working by going online.

For full step-by-step tutorial for solving similar problems please check:
[http://www.liberiangeek.net/2010/08/change-dns-information-ubuntu-10-04-lucid-lynx/]("http://www.liberiangeek.net/2010/08/change-dns-information-ubuntu-10-04-lucid-lynx/")

The above link explains how to change the DNS Settings in Ubuntu.

---

### Post by Gone fishing on 2012-10-13
Cheers - can you mark as solved.

---

