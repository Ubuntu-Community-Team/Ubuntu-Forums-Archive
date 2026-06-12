---
title: "Newly migrated to Linux - Few problems"
date: 2017-03-02
forum: New to Ubuntu
---

### Post by dunya on 2017-03-02
I have migrated to Linux a week ago and after jumping from one distro to another, xubuntu seems to be the least problematic for my laptop. However I have some problems that makes me really exhausted. Would really appreciate if I can get a helping hand.

1) No matter how much I try, I could not make Keepass2 with KeeFox or Passifox work. Keepassxc works fine, but the autocomplete and some other functions are not as good as Keepass2+Keefox combination. Installing keepasshttp is also a big pain, can someone explain me step by step on how to make Keepass2+Keefox (or Passifox) combination work?

2) I can't make some applications to automatically start after the boot. How can I make apps to autostart with xubuntu?

3) Dropbox is installed, but it does not show any icon or something, though on the terminal it says that dropbox is already running. 

4) I installed an app called "Kaku", but can't uninstall it. Add or remove programs via software center is easy, but when I manually install something from termina (with copy/paste from manuals or forums) it is nearly impossible to uninstall as with this specific case of "Kaku" app. Any idea how can I get rid of it? Couldn't even find the folder of this app.

5) How can I have full control over all folders and files on the system? Whenever I need to copy or move some folder to somewhere, most of the times it does not allow me to move, paste or delete folders in specific (probably important) directories. However I really want to minimize terminal usage and want to have full control over graphic interface. How can I do it?

I was able to solve many other minor problems, but the above mentioned five problems are really sucking my time and I am really trying to use Ubuntu as my daily OS. If I can't solve those problems I am really afraid that I have to move Windows again as I lack time for googling hours and hours just for uninstalling an app.

---

### Post by howefield on 2017-03-02
> **dunya said:**
> 4) I installed an app called "Kaku", but can't uninstall it. Add or remove programs via software center is easy, but when I manually install something from termina (with copy/paste from manuals or forums) it is nearly impossible to uninstall as with this specific case of "Kaku" app. Any idea how can I get rid of it? Couldn't even find the folder of this app.

Is that the music player and installed with the appimage package ?

> How can I have full control over all folders and files on the system? Whenever I need to copy or move some folder to somewhere, most of the times it does not allow me to move, paste or delete folders in specific (probably important) directories. However I really want to minimize terminal usage and want to have full control over graphic interface. How can I do it?

Precede the terminal command with sudo to gain elevated privileges over the system. Or to use the graphical file manager with elevated permissions, run it from the terminal with

```
sudo -H nautilus
```

Goes without saying that with full rights over the file system it is easy to do damage.

PS. It is usually better to stick to one question per thread, makes it easier for others to follow and assist.

---

### Post by dunya on 2017-03-02
Thanks for the quick reply.

"Is that the music player and installed with the appimage package ?"

---Exactly it is, have no clue how to remove it. When I simply delete that file still I can see Kaku icon on the menus.

---When I write the command you have mentioned it returns with the error  sudo: nautilus: command not found. What am I doing wrong?

---

### Post by Impavidus on 2017-03-02
**2) I can't make some applications to automatically start after the boot. How can I make apps to autostart with xubuntu?**

Open the settings tool from the menu, go to "session and startup", then "automatic start of application" (or something like that, I'm translating from my version).

**4) I installed an app called "Kaku", but can't uninstall it. Add or remove programs via software center is easy, but when I manually install something from termina (with copy/paste from manuals or forums) it is nearly impossible to uninstall as with this specific case of "Kaku" app. Any idea how can I get rid of it? Couldn't even find the folder of this app.**

If you follow complicated instructions to install something, you need to follow equally complicated instructions to uninstall. If you used an install script, try using the uninstall script that hopefully was supplied along with it. If there is no uninstall script, carefully analyse what the install instructions did, then undo it. There's no standard way.

**5) How can I have full control over all folders and files on the system? Whenever I need to copy or move some folder to somewhere, most of the times it does not allow me to move, paste or delete folders in specific (probably important) directories. However I really want to minimize terminal usage and want to have full control over graphic interface. How can I do it?**

Once you've properly configured your system, you rarely need root permissions for anything. Even upgrades can be left unattended. As howefield wrote, you can use the file manager with root permissions On xubuntu, the file manager is know as thunar. It's not the safest way to do things, as humans are known to make mistakes. Best is to fall in love with the terminal.
```
sudo -H thunar
```

---

### Post by howefield on 2017-03-02
> **dunya said:**
> ---Exactly it is, have no clue how to remove it. When I simply delete that file still I can see Kaku icon on the menus.

I'll take a look at it. Could simply be the .desktop files that remain.

> ---When I write the command you have mentioned it returns with the error  sudo: nautilus: command not found. What am I doing wrong?

Apologies, I "forgot" you said that you were using Xubuntu.. the file manager in Xubuntu is thunar, so same command except substitute nautilus with thunar.

---

### Post by dunya on 2017-03-02
**Open the settings tool from the menu, go to "session and startup", then  "automatic start of application" (or something like that, I'm  translating from my version).**

Some apps really do start automatically, but some fail to start, such as the app of my VPN provider or Dropbox. Is it possible to determine what is blocking the autostart of specific apps?

[B]If you follow complicated instructions to install something, you need to  follow equally complicated instructions to uninstall. If you used an  install script, try using the uninstall script that hopefully was  supplied along with it. If there is no uninstall script, carefully  analyse what the install instructions did, then undo it. There's no  standard way.


[/B]This one is a huge problem for newbies like me I suppose. Many times I simply copy and paster the instructions to terminal, sometimes it works and sometimes not, but 90% the times the uninstall instructions does not work out. For beginners it is really painful to understand the instructions or how and where does the app gets installed.

[B]Once you've properly configured your system, you rarely need root  permissions for anything. Even upgrades can be left unattended. As  howefield wrote, you can use the file manager with root permissions On  xubuntu, the file manager is know as thunar. It's not the safest way to  do things, as humans are known to make mistakes. Best is to fall in love  with the terminal.

[/B]
I really hope that I can have a stable and working system this week. Most of the things work fine compared to other distros that I tried. Love it more than windows even now, but wish install/uninstall phase was easier. 

sudo -H is the exactly I asked for, now I can easily move files and folders.

---

### Post by howefield on 2017-03-02
> **dunya said:**
> ---Exactly it is, have no clue how to remove it. When I simply delete that file still I can see Kaku icon on the menus.

Getting back to this.. as I understand it appimage packages come complete with everything you need to run the software and do not install to your system, other than your /home folder. So nothing to uninstall as such. 

Presumably you have clicked yes to intergrating with the menus when prompted.

I'm using Ubuntu with Unity so may be a little different to Xubuntu but try deleting the folder..

```
~/.config/Kaku
```
and the file
```
~/.local/share/applications/kaku
```

You may need to check the menu editor and logout/back in.

---

### Post by dunya on 2017-03-02
[B]Getting back to this.. as I understand it appimage packages come  complete with everything you need to run the software and do not install  to your system, other than your /home folder. So nothing to uninstall  as such. 

Presumably you have clicked yes to intergrating with the menus when prompted.

I'm using Ubuntu with Unity so may be a little different to Xubuntu but try deleting the folder..


[/B]Deleted both, seems that it is uninstalled for good. Thank you very much for the support and explaining appimage packages.

---

### Post by howefield on 2017-03-02
> **dunya said:**
> Deleted both, seems that it is uninstalled for good. Thank you very much for the support and explaining appimage packages.

Cool, glad it worked for you, using software from the Ubuntu repositories is by far the easiest way of installing and uninstalling software. Third party deb packages are likewise generally easily enough managed but when you start using different package formats, eg snaps or in this case appimage things get a little more involved, still easily enough managed but requires more/different knowledge. 

Can I ask you to use [noparse]> [/noparse] tags when quoting others, it helps others to help you by making your posts more readable and familiar. The reply with quote button should do it, if you need to break up others posts then insert extra tags either by typing them or using the quote icon on the toolbar.

If you still need help on your outstanding queries, please start fresh threads.

---

### Post by Impavidus on 2017-03-03
> **howefield said:**
> 
Can I ask you to use  tags when quoting others, it helps others to help you by making your posts more readable and familiar. The reply with quote button should do it, if you need to break up others posts then insert extra tags either by typing them or using the quote icon on the toolbar.

You can blame me for that. As I wanted to quote a few short bits I though it would be better (more compact) to just bold it, but generally quote tags are indeed better.

---

### Post by cariboo on 2017-03-04
> **Impavidus said:**
> You can blame me for that. As I wanted to quote a few short bits I though it would be better (more compact) to just bold it, but generally quote tags are indeed better.

If you are going to bold something, it's just as easy to use quote tags, especially if you click the icons in the editor.

---

