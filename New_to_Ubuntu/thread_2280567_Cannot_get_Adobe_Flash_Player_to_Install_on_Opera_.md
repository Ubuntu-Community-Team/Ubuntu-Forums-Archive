---
title: "Cannot get Adobe Flash Player to Install on Opera Ubuntu 14.04"
date: 2015-05-31
forum: New to Ubuntu
---

### Post by Caleb_Jefferies on 2015-05-31
HI,
I have a Dell XPS 15 L502X running Ubuntu 14.04.  I have done a lot of research on this and read other threads but I cannot figure out how to install Adobe Flash Player on Opera to make it work.  I mostly would like it to watch Youtube videos with it but when I do I get and error.  As far as I know I am running the latest version of Opera as I installed it recently.  I have the .rpm version downloaded but it always won't work or the terminal can't find it and opera just can't find it to use it.  Any help would be greatly appreciated!;)
God bless,
Caleb Jefferies

---

### Post by QIII on 2015-05-31
.rpm packages are used with distributions that use the RedHat Package Manager or other package managers that can handle them.  Ubuntu is derived from Debian, so it uses .deb packages.

Although you can do some gymnastics to get .rpm packages installed, in this case there is no need.

Just do 

```
sudo apt-get install flashplugin-installer
```

Whether that will cause Opera to use it I don't know.

Adobe has abandoned further development of Flash for Linux and only provides security updates (for a bit longer) for Linux.  That means you will get a dated version of Flash, which may cause problems on some websites.

The Google Chrome browser (not the Chromium browser) uses a current Google version of Flash, called PepperFlash.  Chromium will use it, but it has to be installed.

---

### Post by mc4man on 2015-05-31
Opera will use google-chrome's pepperflash if it finds it. Typically google-chrome installs to /opt/google/chrome/
So install google-chrome.
or if you don't want google-chrome installed - 
If only the PepperFlash folder is present in above location it will use it. (may be other locations..?
One ex., -  installed google-chrome, copied out the PepperFlash folder, removed google-chrome, recreated folder structure & put PepperFlash folder back in
> :~$ ls -R /opt/google
/opt/google:
chrome

/opt/google/chrome:
PepperFlash

/opt/google/chrome/PepperFlash:
libpepflashplayer.so  manifest.json


---

### Post by deadflowr on 2015-06-01
> **mc4man said:**
> Opera will use google-chrome's pepperflash if it finds it. Typically google-chrome installs to /opt/google/chrome/
So install google-chrome.
or if you don't want google-chrome installed - 
If only the PepperFlash folder is present in above location it will use it. (may be other locations..?
One ex., -  installed google-chrome, copied out the PepperFlash folder, removed google-chrome, recreated folder structure & put PepperFlash folder back in

Wouldn't it be better/easier to use the pepperflashplugin-nonfree package?
Which downloads google-chrome, then extracts and installs only the pepperflash plugin. 

But I think if you install it without installing chrome, for either method mentioned, you then need to manually updated.
Where as with chrome fully installed, it'll be updated automatically(or automatically as things go) along with chrome itself.

If that makes sense.

---

### Post by mc4man on 2015-06-01
> **deadflowr said:**
> Wouldn't it be better/easier to use the pepperflashplugin-nonfree package?
Which downloads google-chrome, then extracts and installs only the pepperflash plugin. 

But I think if you install it without installing chrome, for either method mentioned, you then need to manually updated.
Where as with chrome fully installed, it'll be updated automatically(or automatically as things go) along with chrome itself.

If that makes sense.
Seems a better idea, never did know (or pay attention) to the pepperflashplugin-nonfree package's existence.

---

### Post by Caleb_Jefferies on 2015-06-02
Thanks for all the help guys!  I think I will install Chrome since I am a learning web developer and would like to use it anyhow for testing.
God bless,
Caleb Jefferies

---

