---
title: "Firerox will not update"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by jcats on 2012-01-01
I am running Ubuntu 11.10 on a HP dv9500 laptop. I have Firefox 4.0 Beta 6 installed. 
Despite my best efforts, I cannot get Firefox to update.
Here is what I have done:
-deleted every file and folder I can find, related to Firefox 
-uninstalled and reinstalled Firefox from both the software center and the Synaptic Package  manager.
-auto update has run several times, saying it updates Firefox
-installed the latest PPA (This says that Firefox 9 is already installed)

I spent hours on Google, trying to find some solution.

Any help would be most appreciated.
Happy New Year

jcats

---

### Post by Ertai87 on 2012-01-01
I appear to be having the same problem.  When I go to update my blog, I'm being told that I should update FFX (it doesn't force me to, which is good, but it says that I don't have the latest version) but according to apt I have the latest version installed already.  For reference, according to Firefox --version, I have 8.0 installed, and according to apt there is no newer version.

---

### Post by lovinglinux on 2012-01-01
Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Ertai87 on 2012-01-01
> **lovinglinux said:**
> Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

```
Ubuntu Architecture

Linux Rath 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-8.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
mozillateam-firefox-stable-oneiric.list

```

---

### Post by 2F4U on 2012-01-01
The problem may simply be due to the fact that the latest version of Firefox released by Mozilla is 9.0.1, which is unfortunately not available in the regular Ubuntu repositories.

---

### Post by Ertai87 on 2012-01-01
> **2F4U said:**
> The problem may simply be due to the fact that the latest version of Firefox released by Mozilla is 9.0.1, which is unfortunately not available in the regular Ubuntu repositories.

According to the sticky at the top of this forum, it should be available in the regular repos.

---

### Post by jcats on 2012-01-01
Here is my firefox report:


Linux jcats-laptop 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-10.0/firefox.sh'

Sources

dropbox.list
dropbox.list.save
mozillateam-firefox-next-oneiric.list
mozillateam-firefox-next-oneiric.list.save
mozillateam-firefox-stable-natty.list.distUpgrade
mozillateam-firefox-stable-natty.list.save
mozillateam-firefox-stable-oneiric.list
mozillateam-firefox-stable-oneiric.list.save
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.save
ubuntu-mozilla-daily-ppa-maverick.list.distUpgrade
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-mozilla-daily-ppa-natty.list
ubuntu-mozilla-daily-ppa-natty.list.distUpgrade
ubuntu-mozilla-daily-ppa-natty.list.save
ubuntu-mozilla-daily-ppa-oneiric.list
ubuntu-mozilla-daily-ppa-oneiric.list.save

---

### Post by 2F4U on 2012-01-01
I installed it right now by adding a (to me new) repository

```

sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

I tried updating through the regular repositories (main server) but Firefox 9 is not available.

---

### Post by jcats on 2012-01-01
Thanks 2F4U, but no go.
it says that it failed to fetch anything.  (404 not found)
This is the response every time I have tried to update through the terminal.
I'll be happy just to get it to update, regardless of the version

---

### Post by LinuxFan999 on 2012-01-01
How do you have Firefox 4.0 beta 6 installed in Ubuntu 11.10?
Ubuntu 11.10 came with Firefox 7.0.1.

---

### Post by lovinglinux on 2012-01-01
> **Ertai87 said:**
> ```
Ubuntu Architecture

Linux Rath 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-8.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

google-chrome.list
google-chrome.list.distUpgrade
google-chrome.list.save
mozillateam-firefox-stable-oneiric.list

```

Please do not hijack the thread. Your problem is not the same. According to your report, you have Firefox 8. There is nothing indicating otherwise. The real problem is that your blog doesn't recognize the user agent properly. Use [User Agent RG](https://addons.mozilla.org/en-US/firefox/addon/user-agent-rg/) or [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59/).

---

### Post by lovinglinux on 2012-01-01
> **jcats said:**
> Here is my firefox report:


Linux jcats-laptop 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-10.0/firefox.sh'

Sources

dropbox.list
dropbox.list.save
mozillateam-firefox-next-oneiric.list
mozillateam-firefox-next-oneiric.list.save
mozillateam-firefox-stable-natty.list.distUpgrade
mozillateam-firefox-stable-natty.list.save
mozillateam-firefox-stable-oneiric.list
mozillateam-firefox-stable-oneiric.list.save
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
tualatrix-ppa-oneiric.list
tualatrix-ppa-oneiric.list.save
ubuntu-mozilla-daily-ppa-maverick.list.distUpgrade
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-mozilla-daily-ppa-natty.list
ubuntu-mozilla-daily-ppa-natty.list.distUpgrade
ubuntu-mozilla-daily-ppa-natty.list.save
ubuntu-mozilla-daily-ppa-oneiric.list
ubuntu-mozilla-daily-ppa-oneiric.list.save


You have made a big mess with multiple Firefox installations and multiple ppa.

First, you need to revert a divertion to a manually installed version under /opt folder, which is probably Firefox 4.

```
sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
```

Then you need to remove all those ppa you have:

```
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-next-oneiric.list
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-next-oneiric.list.save
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-stable-natty.list.distUpgrade
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-stable-natty.list.save
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-stable-oneiric.list
sudo rm -f /etc/apt/sources.list.d/mozillateam-firefox-stable-oneiric.list.save
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list.distUpgrade
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-maverick.list.save
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list.distUpgrade
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list.save
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list
sudo rm -f /etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-oneiric.list.save
```

Then update:

```
sudo apt-get update
```

Then reinstall Firefox:

```
sudo apt-get install --reinstall firefox
```

At this point, you will have Firefox 8, which is the current version available in the official repos. If you want Firefox 9, then you must be patient and wait for it to become available in the official repos. Firefox 9 is already under testing and should be in the repos soon. If you can't wait, you can use the *ubuntu-mozilla-security* ppa. See [Firefox 9 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247). If you do, do not install multiple ppa repositories. Pick only the one you need.

---

### Post by jcats on 2012-01-01
I have had Ubuntu installed on this lap top since 7.04. I have updated through the update manager for every version. Once Firefox got to version 4, it just stopped updating.
It runs just fine, but I would like to update it and also know why it is not updating.
But according to LovingLinux, Ive messed things up. 
I'm off to try your suggestions,LovingLinux.
Thanks everyone for your help so far:)

LovingLinux, it didn't work
when I put in "sudo apt-get install --reinstall firefox", the return was 
Reinstitution of firefox is not possible, it cannot be downloaded

when I have tried to update from the terminal before, it also says it cannot be downloaded.
Yes, I do have Internet :) , and everything I have tried to update works correctly

---

### Post by lovinglinux on 2012-01-01
> **jcats said:**
> I have had Ubuntu installed on this lap top since 7.04. I have updated through the update manager for every version. Once Firefox got to version 4, it just stopped updating.
It runs just fine, but I would like to update it and also know why it is not updating.
But according to LovingLinux, Ive messed things up. 
I'm off to try your suggestions,LovingLinux.
Thanks everyone for your help so far:)

The reason appears to be because you have downloaded Firefox 4 beta 6 from Mozilla, installed in the /opt folder and created a divertion for the firefox binary. That's why you can't update. Actually it does update, but you can't see it, because the divertion makes your system launch Firefox 4 from the opt folder, instead of the updated Firefox 8.

Just run those commands I gave you and you will be fine.

---

### Post by jcats on 2012-01-01
Now, no version of firefox will start.
Software center says Firefox is installed, and there is an icon in applications. But when I click on it-"failed to execute child process "firefox" (no such file or directory).

LovinLinux, I ran your commands twice, same response, both times

when I put in "sudo apt-get install --reinstall firefox", the return was
Reinstitution of firefox is not possible, it cannot be downloaded

Still, its all good, I'm learning as we go

---

### Post by lovinglinux on 2012-01-01
> **jcats said:**
> Now, no version of firefox will start.
Software center says Firefox is installed, and there is an icon in applications. But when I click on it-"failed to execute child process "firefox" (no such file or directory).

LovinLinux, I ran your commands twice, same response, both times

when I put in "sudo apt-get install --reinstall firefox", the return was
Reinstitution of firefox is not possible, it cannot be downloaded

Still, its all good, I'm learning as we go

Try these:

```
sudo apt-get remove firefox
sudo apt-get clean
sudo apt-get update
sudo apt-get install firefox
```

---

### Post by Johnny3 on 2012-01-01
Try uninstalling Firefox in the software center then do a restart then go to SPM and click on status I don't known the name of it but the 5th one down will say something like not installed residual left over chick on everything for complete removal. Then reinstall Firefox for the software center.
Good Luck and God Bless Johnny3 65++
PS you might want to back up your files and do a fresh install of 11.10.

---

### Post by jcats on 2012-01-01
Sweet! We have scored!!!
I now have Firefox 8 and it installed all the add ons I had before, same home page, everything.
You may be right, Johnny3, a fresh install might be in the works.

Thank you LovingLinux and everyone who took the time to help out.

Now if someone will tell me how to mark this as solved, I'll be all set.

Thanks again;
jcats

Ok, I figured out how to mark this thread as solved. Thanks

---

### Post by fractalman on 2012-01-01
i have firefox v 9.0.1 installed in natty (11.04)  i added the following ppa

[HTML]http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu[/HTML]

---

### Post by lovinglinux on 2012-01-01
> **jcats said:**
> Sweet! We have scored!!!
I now have Firefox 8 and it installed all the add ons I had before, same home page, everything.
You may be right, Johnny3, a fresh install might be in the works.

Thank you LovingLinux and everyone who took the time to help out.

Now if someone will tell me how to mark this as solved, I'll be all set.

Thanks again;
jcats

Ok, I figured out how to mark this thread as solved. Thanks

You are welcome.

> **fractalman said:**
> i have firefox v 9.0.1 installed in natty (11.04)  i added the following ppa

[HTML]http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu[/HTML]

That ppa is currently providing Firefox 10.0b1.

---

### Post by GhodMode on 2012-01-21
I'm using Ubuntu 11.10 and I can't update to FF9 either.  I think that I found the reason, though.  They found a security flaw, so they removed FF9 from the repository:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/906389](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/906389)
[http://www.ubuntu.com/usn/usn-1306-1/](http://www.ubuntu.com/usn/usn-1306-1/)
[http://www.ubuntu.com/usn/usn-1306-2/](http://www.ubuntu.com/usn/usn-1306-2/)

UbuntuUpdates also says that the package was deleted: [http://www.ubuntuupdates.org/packages/show/375013](http://www.ubuntuupdates.org/packages/show/375013)

--
Ghodmode
[http://www.ghodmode.com](http://www.ghodmode.com)

---

