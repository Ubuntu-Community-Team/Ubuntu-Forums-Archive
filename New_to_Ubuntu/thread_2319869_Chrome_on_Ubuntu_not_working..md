---
title: "Chrome on Ubuntu not working."
date: 2016-04-08
forum: New to Ubuntu
---

### Post by ahears on 2016-04-08
I am running Ubuntu 14.04 64 bit and was using Google Chrome fully  updated until last night. I guess when you have Chrome open for long  periods of time it will update in the background and then tell you your  current version is out of date  and that it "needs an update" until you  restart Chrome. Chrome wanted an update, so I restarted the browser to  make it go away as usual. Then it gave me the update message again.  Anyway I wasn't able to get this notice to go away so I un-installed it  and have re-downloaded it, the signing key, and enabled the repository  for 64 bit but to no avail. It will install/un-install no problem but  when launching I get the following error on the command line:

$ google-chrome-stable

Screen output:

```


LaunchProcess: failed to execvp:
/opt/google/chrome/chrome

```

Then I type '$ps ax | grep -i chrome' which produces the existence of a Sleeping Process and the Zombie...

```


8667 ?        Sl     0:00 /opt/google/chrome/chrome    
 8680 ?        Z      0:00 [chrome] <defunct>


```

 I removed everything with a 'apt-get purge google-chrome-stable' and  started over. I have also used 'apt-get clean', 'apt-get autoclean',  'apt-get remove', and 'apt-get autoremove' to clean up the system cache.  I installed the Signing Key with 'wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -' which gave me the -OK as expected.

```


OK


```

I checked the Signing Key: 'sudo apt-key list | grep -A1 -B1 -i google'

```


pub   1024D/7FAC5991 2007-03-08
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08


```

I have added the new 64 bit repository *_because the old 32 bitrepositories are offline as of the end of March 2016_*: 'sudo sh -c 'echo "deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)  stable main" >> /etc/apt/sources.list.d/google.list'' and finally  updated the sources list and installed the browser with: 'sudo apt-get  update && sudo apt-get install google-chrome-stable' with no  errors.

It blinks on my launcher, then does nothing...

I have removed the '~/.config/google-chrome' folder and removed the  '/opt/google/chrome' folder after a clean un-install. I have used  'apt-get install -f' to fix broken packages. I have rebuilt the packages  list by using 'sudo rm /etc/apt/sources.list' then 'sudo  software-properties-gtk' to force a rebuild. I used 'sudo apt-get remove  --purge google-chrome-stable' to remove Chrome. I used 'sudo apt-get  update && sudo apt-get dist-upgrade -y' to make everything  current...At some point I even removed the install/uninstall scripts  with 'sudo rm /var/lib/dpkg/info/google-chrome-stable*.prerm' and 'sudo  rm /var/lib/dpkg/info/google-chrome-stable*.postinst'. I've tried everything I can think of but I can't get a  fresh install of Google Chrome 64 bit to run.
 OMG Any help would be a relief please.      Thank you!

---

### Post by deadflowr on 2016-04-08
Did you try just downloading a clean fresh copy of chrome from [Google/Chrome]("https://www.google.com/chrome/browser/desktop/") web site?

---

### Post by Akimoge on 2016-04-08
Download google chrome from official site, check md5 and try install it. I'm using latest version without any problems.

---

### Post by ahears on 2016-04-11
Yes I downloaded from the official site, checked the signing key, and even installed from the .deb package using 'sudo dpkg -i google-chrome-stable.deb'. It installs/uninstalls correctly with no errors but when I launch it it dies. Seems maybe it isn't a problem with Chrome, but whatever it is it effects Chrome...I have chowned my home folder and set all permissions correctly also.

---

### Post by andreid2 on 2016-04-12
And starting it as root, did that do anything? I had troubles with chrome before, too (it froze whole Ubuntu when trying to start). Running as root fixed it. But at the end I did a re-install and suddenly it all worked well again. I installed it from the Google website.

---

### Post by ahears on 2016-04-18
Ran it as root from CLI: 'sudo google-chrome'

```

LaunchProcess: failed to execvp:
/opt/google/chrome/chrome

```

Still no luck..Is this some kind of security problem with my system? I removed all Apparmor Profiles associated with Chrome but it still didn't work.

---

### Post by dellboy56 on 2016-04-19
have you tried the open source varient of chrome ??

---

### Post by Richard_Romick on 2016-04-19
What I usually do when re-installing a program is to uninstall it using the purge command
sudo apt-get purge google-chrome-stable
and then
sudo apt-get clean

This should get rid of anything left behind chrome related.  Then try re-installing it the way you did before.

---

### Post by Impavidus on 2016-04-19
> **andreid2 said:**
> And starting it as root, did that do anything? I had troubles with chrome before, too (it froze whole Ubuntu when trying to start). Running as root fixed it. But at the end I did a re-install and suddenly it all worked well again. I installed it from the Google website.

> **ahears said:**
> Ran it as root from CLI: 'sudo google-chrome'

```

LaunchProcess: failed to execvp:
/opt/google/chrome/chrome

```

Still no luck..Is this some kind of security problem with my system? I removed all Apparmor Profiles associated with Chrome but it still didn't work.

NEVER run applications like chrome as root. Web browsers are complex programs with a large likelyhood of having security bugs. They face the web, so it's relatively easy to feed them crafted documents to exploit those security bugs. Finally they don't do anything for which root permissions would normally be required.

---

### Post by slickymaster on 2016-04-19
> **Impavidus said:**
> NEVER run applications like chrome as root. Web browsers are complex programs with a large likelyhood of having security bugs. They face the web, so it's relatively easy to feed them crafted documents to exploit those security bugs. Finally they don't do anything for which root permissions would normally be required.

This ^^^

---

### Post by grahammechanical on 2016-04-19
> I removed all Apparmor Profiles associated with Chrome

Bad thing to do. AppArmor is there to stop programs from gaining to access to areas that they have no right to access and to stop them changing things that they have no right to change. It is the apparmor profile that makes this work.

Remove an apparmor profile and you remove a vital security defence.

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Regards

---

### Post by ahears on 2016-04-21
Update:
 Apparently Google Chrome does not play well with Apparmor. After deleting the Apparmor profile I forgot to reload Apparmor with 'sudo service apparmor reload' after which Chrome loads fine. End of night, 3am, burned out, and I forgot to restart the service! I rarely reboot the machine and days later when I did Chrome worked fine. I appreciate all of your effort, especially that the Admins and Moderators stopped in to contribute:) This Thread is SOLVED.

---

