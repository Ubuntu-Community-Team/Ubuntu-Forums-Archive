---
title: "run firefox 10."
date: 2011-12-31
forum: New to Ubuntu
---

### Post by Matrix01 on 2011-12-31
how do u run FF 10.?
i clicked start up file,
FF did not alunch.

---

### Post by 73ckn797 on 2011-12-31
Where did you get Ff 10?
Look here: [http://www.ubuntugeek.com/how-to-install-firefox-8-on-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-8-on-ubuntu-using-ppa.html) 
You can add the update channel and get the latest stable releases.

---

### Post by sammiev on 2011-12-31
I'm test 12.04 which includes FF10 at this time. Did you add it manually or did you upgrade from 11.10?

---

### Post by Matrix01 on 2011-12-31
[http://www.top10download.com/firefox-10](http://www.top10download.com/firefox-10)

> **73ckn797 said:**
> Where did you get Ff 10?
Look here: [http://www.ubuntugeek.com/how-to-install-firefox-8-on-ubuntu-using-ppa.html](http://www.ubuntugeek.com/how-to-install-firefox-8-on-ubuntu-using-ppa.html) 
You can add the update channel and get the latest stable releases.

---

### Post by Matrix01 on 2011-12-31
[http://www.top10download.com/firefox-10](http://www.top10download.com/firefox-10)
i downloaded ff 10. straight form this web page.

> **sammiev said:**
> I'm test 12.04 which includes FF10 at this time. Did you add it manually or did you upgrade from 11.10?

---

### Post by 73ckn797 on 2011-12-31
> **Matrix01 said:**
> [http://www.top10download.com/firefox-10](http://www.top10download.com/firefox-10)
For stability look into the update channel for Firefox. It will prompt for future releases through Update Manager. My system(s) are on version 9.01. I saw that v10 will release in January 2012.

---

### Post by bodhi.zazen on 2011-12-31
> **Matrix01 said:**
> how do u run FF 10.?
i clicked start up file,
FF did not alunch.

Start firefox from the command line and report any errors. We also need to know more details about how you installed FF 10

---

### Post by overdrank on 2011-12-31
Also please correct me  but the link given for the download is for the platform "Windows XP / 2003 / Vista / 2008 / 7"

---

### Post by Matrix01 on 2011-12-31
[http://www.top10download.com/firefox-10](http://www.top10download.com/firefox-10)
downloaded ff 10. from this website,

how do u start FF from terminal?

> **bodhi.zazen said:**
> Start firefox from the command line and report any errors. We also need to know more details about how you installed FF 10

---

### Post by 73ckn797 on 2011-12-31
> **bodhi.zazen said:**
> We also need to know more details about how you installed FF 10
It was a link to a download for Firefox that he posted : [http://www.top10download.com/firefox-10](http://www.top10download.com/firefox-10)

---

### Post by Matrix01 on 2011-12-31
you got that right,

> **overdrank said:**
> Also please correct me  but the link given for the download is for the platform "Windows XP / 2003 / Vista / 2008 / 7"

---

### Post by vasa1 on 2011-12-31
> **Matrix01 said:**
> you got that right,
You want to run it via Wine because those aren't Linux but MS Windows?

---

### Post by bodhi.zazen on 2011-12-31
> **Matrix01 said:**
> you got that right,

You have to run the linux version, which can be downloaded directly from mozilla.

[http://www.mozilla.org/en-US/firefox/beta/](http://www.mozilla.org/en-US/firefox/beta/)

click the download button, it automatically selects the linux version.

---

### Post by Matrix01 on 2011-12-31
make mistakes,
part of learning.

> **vasa1 said:**
> You want to run it via Wine because those aren't Linux but MS Windows?

---

### Post by Matrix01 on 2011-12-31
download completed,
will u tell me how to run it?

> **bodhi.zazen said:**
> You have to run the linux version, which can be downloaded directly from mozilla.

[http://www.mozilla.org/en-US/firefox/beta/](http://www.mozilla.org/en-US/firefox/beta/)

click the download button, it automatically selects the linux version.

---

### Post by bcschmerker on 2011-12-31
Actually, Launchpad™ has a PPA for Mozilla® Firefox® Beta that packages beta versions to load up any dependencies beyond the default version issued with any Release of Ubuntu®, as I already found to be the case with Current-Version backports to Lucid Lynx™ (ppa:mozillateam/firefox-stable).  The Mozilla Team Firefox Beta repository can be added to APT and Synaptic via:
```
sudo add-apt-repository ppa:mozillateam/firefox-next
```

---

### Post by 73ckn797 on 2011-12-31
> **Matrix01 said:**
> download completed,
will u tell me how to run it?
Is it in a "deb" extension format?

---

### Post by Matrix01 on 2011-12-31
FF 10. has downloaded.
can i still run this code?
FF8. is still on.

> **bcschmerker said:**
> Actually, Launchpad™ has a PPA for Mozilla® Firefox® Beta that packages beta versions to load up any dependencies beyond the default version issued with any Release of Ubuntu®, as I already found to be the case with Current-Version backports to Lucid Lynx™ (ppa:mozillateam/firefox-stable).  The Mozilla Team Firefox Beta repository can be added to APT and Synaptic via:
```
sudo add-apt-repository ppa:mozillateam/firefox-next
```

---

### Post by bodhi.zazen on 2011-12-31
> **Matrix01 said:**
> download completed,
will u tell me how to run it?

[http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux](http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux)

Assumint you downloaded it to Downloads


```
cd ~/Downloads
tar xjf firefox-*.tar.bz2
~/Downloads/firefox/firefox
```

You can make a custom launcher for it with alacarte

---

### Post by Matrix01 on 2011-12-31
yep,
FF10. is saved in download file.
where would u save it if u were me?

k@ubuntu:~$ cd ~/Downloads
k@ubuntu:~/Downloads$ 
k@ubuntu:~/Downloads$ tar xjf firefox-*.tar.bz2

closed FF,
and open,

k@ubuntu:~/Downloads$ ~/Downloads/firefox/firefox
k@ubuntu:~/Downloads$ 

output looks like this,
FF8. is still on.

> **bodhi.zazen said:**
> [http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux]("http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux")

Assumint you downloaded it to Downloads


```
cd ~/Downloads
tar xjf firefox-*.tar.bz2
~/Downloads/firefox/firefox
```You can make a custom launcher for it with alacarte

---

### Post by Matrix01 on 2011-12-31
how do u find that out?
> **73ckn797 said:**
> Is it in a "deb" extension format?

---

### Post by Matrix01 on 2012-01-01
here's output;
will u tell me what's going on?

k@ubuntu:~$ sudo add-apt-repository ppa:mozillateam/firefox-next
[sudo] password for k: 
You are about to add the following PPA to your system:
 Official PPA for Firefox Beta
 This PPA contains releases of Firefox from the beta channel

Please submit all crashes upstream using the crash reporter dialog which appears.
Please report all other bugs with "apport-bug firefox". Please *don't* submit bugs using the Launchpad interface.
 More info: [https://launchpad.net/~mozillateam/+archive/firefox-next]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.tiJ1f73na8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: "Launchpad PPA for Mozilla Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
















> **bcschmerker said:**
> Actually, Launchpad™ has a PPA for Mozilla® Firefox® Beta that packages beta versions to load up any dependencies beyond the default version issued with any Release of Ubuntu®, as I already found to be the case with Current-Version backports to Lucid Lynx™ (ppa:mozillateam/firefox-stable).  The Mozilla Team Firefox Beta repository can be added to APT and Synaptic via:
```
sudo add-apt-repository ppa:mozillateam/firefox-next
```

---

### Post by bcschmerker on 2012-01-05
> **Matrix01 said:**
> here's output;
will u tell me what's going on?

k@ubuntu:~$ sudo add-apt-repository ppa:mozillateam/firefox-next
[sudo] password for k: 
You are about to add the following PPA to your system:
 Official PPA for Firefox Beta
 This PPA contains releases of Firefox from the beta channel

Please submit all crashes upstream using the crash reporter dialog which appears.
Please report all other bugs with "apport-bug firefox". Please *don't* submit bugs using the Launchpad interface.
 More info: [https://launchpad.net/~mozillateam/+archive/firefox-next]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.tiJ1f73na8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 0AB215679C571D1C8325275B9BDB3D89CE49EC21
gpg: requesting key CE49EC21 from hkp server keyserver.ubuntu.com
gpg: key CE49EC21: "Launchpad PPA for Mozilla Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
The Add-APT-Repository ran just like the simulation;
```
sudo apt-get update && apt-get upgrade
```
should bring Mozilla® Firefox® 10 Beta, including dependencies, onto your system.

---

### Post by Matrix01 on 2012-01-06
thank u,
found updated FF in drop down menu,
also,
i downloaded Chrome from this website for a while ago;
[http://linux.softpedia.com/progDownl...oad-48046.html]("http://linux.softpedia.com/progDownload/Google-Chrome-Download-48046.html")

will u tell me how to run this?

> **bodhi.zazen said:**
> [http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux]("http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux")

Assumint you downloaded it to Downloads


```
cd ~/Downloads
tar xjf firefox-*.tar.bz2
~/Downloads/firefox/firefox
```You can make a custom launcher for it with alacarte

---

### Post by 73ckn797 on 2012-01-06
> **Matrix01 said:**
> thank u,
found updated FF in drop down menu,
also,
i downloaded Chrome from this website for a while ago;
[http://linux.softpedia.com/progDownl...oad-48046.html]("http://linux.softpedia.com/progDownload/Google-Chrome-Download-48046.html")

will u tell me how to run this?
Which one did you download? Chromium is in the repositories and will automatically install.
If the file is, for example: ```
google-chrome-stable_current_i386.deb
```, you can first install "gdebi", from the repositories, and it will install it. The "deb" extension designates that it is a file for a Debian based Linux OS.

---

### Post by jtarin on 2012-01-06
Try to avoid the Windows habit of downloading software from just anywhere on the web. Ubuntu/Kubuntu has one of the best software package managers available with the ability to resolve needed dependencies,to install software correctly and update your menu as needed.

---

### Post by Matrix01 on 2012-01-07
downloaded this.
	
Debian/Ubuntu DEB i386 (17.0.963.26 Beta Development)

> **73ckn797 said:**
> Which one did you download? Chromium is in the repositories and will automatically install.
If the file is, for example: ```
google-chrome-stable_current_i386.deb
```, you can first install "gdebi", from the repositories, and it will install it. The "deb" extension designates that it is a file for a Debian based Linux OS.

---

### Post by 73ckn797 on 2012-01-07
> **Matrix01 said:**
> downloaded this.
    
Debian/Ubuntu DEB i386 (17.0.963.26 Beta Development)
I assume you want cutting edge versus stability?

---

### Post by d3v1150m471c on 2012-01-07
> **overdrank said:**
> Also please correct me  but the link given for the download is for the platform "Windows XP / 2003 / Vista / 2008 / 7"

LOL that just might be the bootstrap problem

---

### Post by Matrix01 on 2012-01-20
i just find out what Wine is,

well,
My Xubuntu is on WUBI,

i did not see fine print ".....for Windows" when i download FF.



> **vasa1 said:**
> You want to run it via Wine because those aren't Linux but MS Windows?

---

### Post by Matrix01 on 2012-01-20
> **d3v1150m471c said:**
> LOL that just might be the bootstrap problem

what is bootstrap?
i looked it up, but i am not sure.


[http://en.wikipedia.org/wiki/Bootstrapping](http://en.wikipedia.org/wiki/Bootstrapping)

---

### Post by Matrix01 on 2012-01-20
will u tell me what custom launcher is?

> **bodhi.zazen said:**
> [http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux](http://support.mozilla.org/en-US/kb/Installing%20Firefox%20on%20Linux)

Assumint you downloaded it to Downloads


```
cd ~/Downloads
tar xjf firefox-*.tar.bz2
~/Downloads/firefox/firefox
```

You can make a custom launcher for it with alacarte

---

### Post by bodhi.zazen on 2012-01-20
> **Matrix01 said:**
> will u tell me what custom launcher is?

An icon in your menu to launch the new version of firefox.

---

