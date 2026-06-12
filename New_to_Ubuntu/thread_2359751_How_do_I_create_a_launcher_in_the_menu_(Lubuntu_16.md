---
title: "How do I create a launcher in the menu (Lubuntu 16.04)"
date: 2017-04-27
forum: New to Ubuntu
---

### Post by mago90 on 2017-04-27
Hello all, as per title, How do  I create a launcher in the menu on Lubuntu 16.04? I Installed the latest version of Thunderbird on my system, and it is shipped as tar.bz2. I installed it and I can run it but it did not create a launcher in the menu.  I use MenuLibre when i need to tweak the menu launcher. I created a new launcher and in the field 'command' i put: thunderbird %u and i left 'working directory' blank.  When I try to use the new launcher I get:  Invalid desktop entry file: '/home/marco/.local/share/applications/menulibre-thunderbird.desktop'  Does anyone know how I can create a launcher in the menu so that I can launch thunderbird from there?

---

### Post by vasa1 on 2017-04-27
You could be guided by this which is in */usr/share/app-install/desktop*:```
[Desktop Entry]
X-AppInstall-Package=thunderbird
X-AppInstall-Popcon=29629
X-AppInstall-Section=main

Encoding=UTF-8
Name=Thunderbird Mail
Comment=Send and receive mail with Thunderbird
GenericName=Mail Client
Keywords=Email;E-mail;Newsgroup;Feed;RSS
Exec=thunderbird %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
Categories=Application;Network;Email;
MimeType=x-scheme-handler/mailto;application/x-xpinstall;
StartupNotify=true
Actions=Compose;Contacts

[Desktop Action Compose]
Name=Compose New Message
Exec=thunderbird -compose
OnlyShowIn=Messaging Menu;Unity;

[Desktop Action Contacts]
Name=Contacts
Exec=thunderbird -addressbook
OnlyShowIn=Messaging Menu;Unity;

X-Ubuntu-Gettext-Domain=app-install-data
```You may need to provide the entire path in the various **Exec= lines** and in the **Icon=** line. And save the file in *~/.local/share/applications* as **thunderbird.desktop**. Lubuntu should then "see" thunderbird.desktop.

This is my .desktop file in *~/.local/share/applications* for Firefox which I installed from a tar.gz:```
[Desktop Entry]
Version=1.0
Name=MyFox
Comment=Firefox
Exec=/home/vasa1/MyFox/firefox/firefox %U

Icon=/home/vasa1/.local/share/applications/default16.png
Terminal=false
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;

```

---

### Post by mago90 on 2017-04-27
Thanks for the reply vasa1 I checked the .desktop file for thunderbird in /usr/share/app-install/desktop  and I have this: 

```
[Desktop Entry]
X-AppInstall-Package=thunderbird
X-AppInstall-Popcon=29629
X-AppInstall-Section=main

Encoding=UTF-8
Name=Thunderbird Mail
Comment=Send and receive mail with Thunderbird
GenericName=Mail Client
Keywords=Email;E-mail;Newsgroup;Feed;RSS
Exec=thunderbird %u
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=thunderbird
Categories=Application;Network;Email;
MimeType=x-scheme-handler/mailto;application/x-xpinstall;
StartupNotify=true
Actions=Compose;Contacts

[Desktop Action Compose]
Name=Compose New Message
Exec=thunderbird -compose
OnlyShowIn=Messaging Menu;Unity;

[Desktop Action Contacts]
Name=Contacts
Exec=thunderbird -addressbook
OnlyShowIn=Messaging Menu;Unity;

X-Ubuntu-Gettext-Domain=app-install-data

```

 Do you see something missing/wrong that could cause such error?

---

### Post by ajgreeny on 2017-04-27
You will also need to make sure the **thunderbird.desktop** file is executable for it to work.

Was there a good reason for downloading the tar.bz2 rather than using the .deb package from the repos which would have added a menu item automatically?

---

### Post by vasa1 on 2017-04-27
> **ajgreeny said:**
> You will also need to make sure the **thunderbird.desktop** file is executable for it to work.

Was there a good reason for downloading the tar.bz2 rather than using the .deb package from the repos which would have added a menu item automatically?
I'm not sure that the file need to be executable:```
08:46 PM ~/.../share/applications $ ll | grep -i fox
-rw-rw-r-- 1 vasa1 vasa1  346 Sep  1  2015 myfox.desktop
08:46 PM ~/.../share/applications $ 

```works for me.

I don't use Tbird, but I remember reading that the version in the repos lagged a bit. I don't know what the current state is.

[https://download.mozilla.org/?product=thunderbird-52.0.1-SSL&os=linux64&lang=en-US](https://download.mozilla.org/?product=thunderbird-52.0.1-SSL&os=linux64&lang=en-US)

whereas```
$ apt policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:45.8.0+build1-0ubuntu0.16.04.1
  Version table:
     1:45.8.0+build1-0ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1:38.6.0+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 
```

---

### Post by mago90 on 2017-04-27
Yes the reason why I downloaded it is because I wanted a newer one (I have to admit though that for my use TB is falling..it is becoming a chat client rather than mail/rss client..).
IMHO the fact that apps do not automatically create a menu when you install them is one of the most annoying and not user friendly things of ubuntu :/

---

### Post by vasa1 on 2017-04-27
> **mago90 said:**
> ...
IMHO the fact that apps do not automatically create a menu when you install them is one of the most annoying and not user friendly things of ubuntu :/
That's what you could see when you don't install apps from the repos.

Anyway there's always Distrowatch. Best of luck.

---

### Post by again? on 2017-04-27
If you want a newer version with menu creation, try the beta repo.
[https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next](https://launchpad.net/~mozillateam/+archive/ubuntu/thunderbird-next)

---

