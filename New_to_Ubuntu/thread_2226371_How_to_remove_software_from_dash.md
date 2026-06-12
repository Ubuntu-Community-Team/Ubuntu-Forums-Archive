---
title: "How to remove software from dash"
date: 2014-05-26
forum: New to Ubuntu
---

### Post by Timothy_Cota on 2014-05-26
I am running Ubuntu 14.04 on a toshiba g7 notebook with 4g RAM and 256G hard drive.  How can I remove unwanted software from the dashboard?

---

### Post by Vladlenin5000 on 2014-05-26
Uninstall them?

---

### Post by sammiev on 2014-05-26
> **Timothy_Cota said:**
> I am running Ubuntu 14.04 on a toshiba g7 notebook with 4g RAM and 256G hard drive.  How can I remove unwanted software from the dashboard?

Right click on the icon and select unpin from dashboard.

---

### Post by grumblebum2 on 2014-05-26
> **sammiev said:**
> Right click on the icon and select unpin from dashboard.

dashboard??? unpin???
Are we talking the dash or launcher here?

---

### Post by jdarby1983 on 2014-05-27
just to clarify on this post. What I think the poster wants to do is remove installed software from the unity launcher. 

The launcher and dashboard are two completely different things. The dashboard is built in to the launcher bar and by default is the located at the top, by clicking on it you will be able to search and run files/programs installed on Ubuntu. The unity launcher is by default the bar on the left hand side of the screen and this is where shortcuts to programs are located. To remove shortcuts from the launcher then its as simple as right click on the icon >> unlock from launcher. If you want to add shortcuts to new software that has not appeared on the launcher then first search in the dashboard and left click the icon of the program and drag it onto the launcher.

Hope this helps

---

### Post by sammiev on 2014-05-27
Yes I screwed the two up again.

---

### Post by Timothy_Cota on 2014-05-27
Maybe I should have mentioned that Most of these software packages I downloaded from the internet.  They are in Downloads which isin the dash but maybe is not part of it?

---

### Post by grumblebum2 on 2014-05-27
If you want to exclude the contents of a folder...
System settings > Security and Privacy > files and applications 
and add a folder to exclude.

May need to clear usage data.

---

### Post by Timothy_Cota on 2014-05-27
Thanks for the tip. I will let you know. unktim

---

### Post by Timothy_Cota on 2014-05-28
It works.  thanks!

---

### Post by monkeybrain20122 on 2014-05-28
I misunderstood OP. Basically s/he just wants to prevent some files/foldrs from showing up in the dash. I thought s/he wants to prevent some installed apps from showing up. 

Why does one want to do that? Well you may have installed something that are dependencies but you would never use it. e.g Installing many kde apps pulls in nepomuk (sp?) What the hell is nepomuk?? I don't use it and if I set up Ubuntu for inexperienced users I don't want its presence to confuse them even though k3b is nice to have. The solution is to change the name of the .desktop file (say nepomuk-backup.desktop is in /usr/share/applications/kde4, change it to something like kde-junk) then it won't show up in the dashboard anymore. As long as the software doesn't get update you won't see it again. If it get updated then the .desktop file get reinstalled so you have to repeat this procedure again.

As others have said, blacklisting the folder would do what OP wants. But I think this is a design fault, instead the system should only log files in folders that are whitelisted. For example, I cannot blacklist the whole / directory for then nothing will be logged. however there is absolutely no reason why access to system files should be logged (/etc /usr/bin/ etc) so I have to blacklist each sub directory individually. Same in /home, there are some random documents that I don't want logged, but I do want some subfoler to be logged, e.g my ebooks. There is no way I can blacklist a folder and whitelist one of its subfolders. The way Unity does it now is kind of stupid in that by default it logs a lot of stuffs which are just noise.

---

### Post by grumblebum2 on 2014-05-28
Blacklisting makes far more sense to me.

The way I understand it the dash uses zeitgeist to log and display files you access and also "locate" to find any file
when you type in a search.
When you use security and privacy to exclude a folder, it hides it from zeitgeist logging and the locate search used in the dash.
```
glen@Trusty:~$ gsettings get com.canonical.Unity.FilesLens use-locate
true
```

The dash won't show any files you have accessed from the excluded folder
and they won't show up in a dash search.
However files you access in the excluded folder will still show in nautilus recent.
You can use....
```
echo > ~/.local/share/recently-used.xbel
```
to clear recent.

You could use a logout script to clear recent and/or zeitgeist logs.

---

