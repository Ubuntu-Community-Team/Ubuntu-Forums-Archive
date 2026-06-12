---
title: "Error 203!!!"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by theRightNee on 2008-04-27
hey all,
i did a clean install of hardy heron today, and i have to say it is amazing!
i got suspend to work...but successive attempts have been....less satisfactory, but that is not the issue
my biggest issue, as of now, is that i cannot install firefox addons, due to some Error 203. I have looked around for hours now, and nothings seems to work. I used the psychocats installer to install Firefox 2.0.0.14, moving away from the standard firefox 3 beta..could this be the problem, and if so how do i solve it? thanks!

---

### Post by frup on 2008-04-27
Are you using firefox 3 or firefox 2? check in the about menu of firefox. Then make sure the addons you are using are for the correct version

error 203 seems to be a firefox error and I am googling to find out the problem now and will edit this if I find a solution

EDIT:

according to: [http://forums.zotero.org/discussion/247/installation-fails-console-log-for-issues-error-203-firefox-2001--linux/](http://forums.zotero.org/discussion/247/installation-fails-console-log-for-issues-error-203-firefox-2001--linux/)

it could be a permission error. Basically, as I understand it, it's possible the location extensions are installed in to could be owned by root (if you installed in opt for example) and firefox can't install the addon.

---

### Post by JohnGalt131 on 2008-04-27
I am having the same problem. Even when run as root, firefox (2.0.0.14) will not allow me to install extensions.

---

### Post by ricanelite on 2008-04-27
yup I am having the same issues.

---

### Post by JohnGalt131 on 2008-04-27
I got mine to work. under ~/.mozilla, there is only one directory. Open that, and inside there should be a file called extensions.rdf. Delete that and run firefox as root and you should get it to work. Mine did.

---

### Post by huntwell on 2008-04-27
I am also having this error resulting in the inability to use addons. I have read in more than one place if I delete the extensions.rdf file, and then run firefox, it should fix the problem. My problem is that I am new to linux and don't know where to find the folder ~/.mozilla on my computer. 

If someone wouldn't mind providing a step by step process of where to find it, I would really appreciate it.

Thanks,
Huntwell

---

### Post by JohnGalt131 on 2008-04-27
> **huntwell said:**
> I am also having this error resulting in the inability to use addons. I have read in more than one place if I delete the extensions.rdf file, and then run firefox, it should fix the problem. My problem is that I am new to linux and don't know where to find the folder ~/.mozilla on my computer. 

If someone wouldn't mind providing a step by step process of where to find it, I would really appreciate it.

Thanks,
Huntwell

Click Applications>Accessories>Terminal. Once in the terminal type "sudo nautilus ~/.mozilla/firefox". That should bring up the firefox directory. inside that directory there should, I think, be only one folder. Open that folder and inside will be extensions.rdf. Delete that and then launch the terminal again. Now type "sudo firefox-2".
Hope that helps.

---

### Post by huntwell on 2008-04-27
It worked perfectly! Thank you very much John. I have both Firefox 2 and 3 because I found firefox 3 still a little buggy yet. 

The step by step was very helpful and easy to follow, but I am wondering if there is a way to find those kinds of files by going to my home folder or the filesystem under the places menu. Any suggestions?

Again, thanks for helping me out.

---

### Post by JohnGalt131 on 2008-04-27
> **huntwell said:**
> It worked perfectly! Thank you very much John. I have both Firefox 2 and 3 because I found firefox 3 still a little buggy yet. 

The step by step was very helpful and easy to follow, but I am wondering if there is a way to find those kinds of files by going to my home folder or the filesystem under the places menu. Any suggestions?

Again, thanks for helping me out.
You can navigate to the folders through the places tab, but to modify files you need to "own" them. If the file is owned by root, then you need to access it as the root (sudo). If you're not sure where something is exactly, but know you need to have root permissions, type "sudo nautilus" in the terminal and it's the same as navigating normally. What I've done to save time is add a "custom application launcher" to the top pannel. For the "command" just add "gksudo nautilus". Now each time you need to navigate with root permissions, just click that button and type the admin password.

---

### Post by balaoko on 2008-04-30
Thanks, John! It also works in my ff3!

---

### Post by kujaabi on 2008-06-12
same problem. your solution worked perfectly for me too!!  Thanks!!!

---

### Post by cariboo on 2008-06-12
For those of you new to Ubuntu Open Places-->Home Folder and type **Ctrl-h** to see hidden files and folders in your home directory

Jim

---

### Post by twisted_hick on 2008-06-13
Hi John thanks a million  you got it working for me  now to get the nautilus problems licked and everything will be great  thanks agian Ubuntu community

---

