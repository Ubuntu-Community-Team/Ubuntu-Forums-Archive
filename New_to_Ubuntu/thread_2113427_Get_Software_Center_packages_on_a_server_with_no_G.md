---
title: "Get Software Center packages on a server with no GUI"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by dbrossard on 2013-02-07
Hi all,

I am building a new server that I would like to get Perforce Server installed on. Rather than going with a source tarball I noticed that it is available in the Ubuntu Software Center. Seeing as deb packages are much easier to install, find dependencies, and upgrade I would like to use the packages from the software center. However, since this is a server, I do not want to install all the GTK and Xorg packages to run a GUI.

How can I install these packages or repos on a server using only the CLI? Perforce Server is cleary designed to run on a server based system with no GUI installed so it would seem odd that it is available to Ubuntu only via a GUI application.

Thanks!

---

### Post by Impavidus on 2013-02-07
```
sudo apt-get update
sudo apt-get install <package name>
```

---

### Post by ibjsb4 on 2013-02-07
There is a list of all packages offered.

[http://packages.ubuntu.com/precise/](http://packages.ubuntu.com/precise/)

---

### Post by dbrossard on 2013-02-07
I have tried these ideas and also checked via [http://packages.ubuntu.com](http://packages.ubuntu.com) but the package perforce-server is not listed in any repo. It is only available via the Software Center. 

After installing on my workstation I see these packages:
/var/cache/apt/archives/perforce-client-cli_2012.3+1-0ubuntu1_amd64.deb
/var/cache/apt/archives/perforce-server_2012.3+1-0ubuntu1_amd64.deb
/var/cache/apt/archives/perforce-version-management_2012.3+1-0ubuntu1_amd64.deb

Am I missing a special repo?

Thanks

---

### Post by dbrossard on 2013-02-07
After querying the package installed via the Software Center I see this:

[INDENT]dbrossard@pdx-it-db:~$ sudo apt-cache policy  perforce-server
perforce-server:
  Installed: 2012.3+1-0ubuntu1
  Candidate: 2012.3+1-0ubuntu1
  Version table:
 *** 2012.3+1-0ubuntu1 0
**        500 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/perforce-version-management/ubuntu/](https://private-ppa.launchpad.net/commercial-ppa-uploaders/perforce-version-management/ubuntu/) quantal/main amd64 Packages**
        100 /var/lib/dpkg/status[/INDENT]

However I do not see the repo bolded above in my sources.list. On closer examination though I did find it in /etc/apt/sources.list.d

I will try using this repo on the server also.

---

### Post by dbrossard on 2013-02-07
After copying 
[INDENT]/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders...[/INDENT]
and
[INDENT]/etc/apt/auth.cfg[/INDENT]
and then 
[INDENT]sudo apt-get install apt-transport-https[/INDENT]
and importing the private key:
[INDENT]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E131728675254D99[/INDENT]

Now the package is available. Not a lot of work but there should probably be some easier way in the future.

---

