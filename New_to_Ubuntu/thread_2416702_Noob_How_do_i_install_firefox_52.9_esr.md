---
title: "Noob: How do i install firefox 52.9 esr?"
date: 2019-04-13
forum: New to Ubuntu
---

### Post by cracktor on 2019-04-13
Hello,

I am probably stupid for asking this but i can' t figure it out so just going to ask for help here.

Need to install [firefox 52.9 ESR ]("https://ftp.mozilla.org/pub/firefox/releases/52.9.0esr/") tried to do it with[ this  explanation]("https://askubuntu.com/questions/548003/how-do-i-install-the-firefox-developer-edition") but i can' t create the launchpad file as descriped in ' manually' 

Don' t really know what i' m doing too, but i can read and copy paste..

So what would be the most straightforward way to install firefox 52.9 esr on my machine?  (Linux 4.18.0-17-generic x86_64)

---

### Post by again? on 2019-04-13
Read this ... [https://superuser.com/questions/1392211/install-old-version-of-package-firefox-esr-on-ubuntu](https://superuser.com/questions/1392211/install-old-version-of-package-firefox-esr-on-ubuntu)

If you still want to install firefox 52.9 esr you can do it from this ppa ..[https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr](https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr)
The ppa has versions for bionic, xenial and trusty.

---

### Post by cracktor on 2019-04-14
> sudo add-apt-repository ppa:jonathonf/firefox-esr
sudo apt-get update

So i entered this in my terminal and the installation was succesfull but how do i launch firefox esr now??
Or maybe it' s there but how do i run it?
How do i make a launcher?

---

### Post by again? on 2019-04-14
Sorry wasn't that clear.
You need ppa:jonathonf/firefox-esr[COLOR="#FF0000"]-52[/COLOR] for firefox-esr 52.9.

Remove firefox-esr...
```
sudo apt remove firefox-esr 
```
Remove the ppa ...
```
sudo add-apt-repository -r ppa:jonathonf/firefox-esr
```


Now add the 52 repo and install 52.9....
```
sudo add-apt-repository ppa:jonathonf/firefox-esr-52
sudo apt install firefox-esr 
```

It should be available in the applications menu of whatever desktop you use, as firefox-esr.

---

### Post by cracktor on 2019-04-14
> dutchtomcruise@dutchtomcruise-pc:~$ sudo apt install firefox-esr
[sudo] password for dutchtomcruise: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox-esr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'firefox-esr' has no installation candidate



So that seems some different problem, any idea how to fix this?

---

### Post by again? on 2019-04-14
What Ubuntu release are you using?
The ppa only has packages for bionic(18.04), xenial(16.04) and  trusty(14.04)

If you are using 18.10 (which is what your kernel version indicates), try downloading and installing the 18.04 deb.
Firstly remove the firefox-esr-52 ppa and update.
```
sudo add-apt-repository -r ppa:jonathonf/firefox-esr-52
sudo apt update
```

Download the bionic(18.04) firefox-esr-52 deb....
```
cd ~/Downloads && wget https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr-52/+files/firefox-esr_52.9.0esr-1~18.04.york0_amd64.deb
```

Install...
```
sudo apt install ~/Downloads/firefox-esr_52.9.0esr-1~18.04.york0_amd64.deb
```

I have a test partition of Xubuntu 18.10 in which the 18.04 deb installation worked.
[ATTACH=CONFIG]283030[/ATTACH]

---

### Post by monkeybrain20122 on 2019-04-15
You don't need to install firefox. Just grab the tarball from [Mozilla]("https://www.mozilla.org/en-US/firefox/organizations/all/"),  extract it somewhere in your $HOME, enter the firefox folder and click firefox to launch, that is it. All the ppa and installation business just add unnecessary complexities and increase the chance of failure.

---

