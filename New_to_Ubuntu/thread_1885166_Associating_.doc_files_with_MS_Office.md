---
title: "Associating .doc files with MS Office"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by daithi23 on 2011-11-22
Hi I've installed MS Office using PlayOnLinux but the only way (I can see anyway) to open the .doc files is to open the Ms Word and then navigate to the file via "Open" in the menu bar. 
If I right-click on .doc files in PCManFM and select "Open With", navigate to Microsoft Word from "Wine", "Windows Programs" and checking "Set selected application as default action for this type of file" seems to do nothing. Right clicking on a .doc and selecting "Microsoft Word" shows the error "There is no Windows program configured to open this type of file"

I am running lubuntu 11.10.

Thank you!

---

### Post by BC59 on 2011-11-22
On Ubuntu I choose an Office file, then right click--properties--open with--recommended applications-->choose Word and then click at right--set as default.

You should do the same for all .doc, .xls .ppt and then for the .docx etc.

---

### Post by daithi23 on 2011-11-22
That sounds exactly like what I tried already which does nothing, thanks anyway.

---

### Post by BC59 on 2011-11-22
In that case I think you have remnants of older inactive icons, from previous Wine installations. This is an old problem.

Try to find which of the multiple icons is active.

---

### Post by daithi23 on 2011-11-22
It's the first time installing Wine and Lubuntu, however, the context menu when I right click on the .doc file shows two instances of "Microsoft Word". Clicking on either of them though gives me the "There is no Windows program configured to open this type of file" error. 

> Try to find which of the multiple icons is active.

Sorry but I don't really understand what you mean by this! :confused:

---

### Post by BC59 on 2011-11-22
> shows two instances of "Microsoft Word"

It's what I told you about multiple icons. I have 4 instances of Word!

I would try to re install the Office. Maybe the installation was not perfect. 

You can go to Home directory hit CTRL+H and see the hidden folders. The folder .wine contains the "MSWindows" and "MSOffice". So if you rename the folder to .wine1 for instance, Wine is creating automatically other Wine prefix and you can install other Office and keep the previous as backup.

You could also try to install the latest Wine:

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install wine1.3
```

---

### Post by daithi23 on 2011-11-22
Thanks, I'll give it a go tomorrow and let you know how I get on.

---

