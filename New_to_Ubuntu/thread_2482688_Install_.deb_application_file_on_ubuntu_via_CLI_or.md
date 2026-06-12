---
title: "Install .deb application file on ubuntu via CLI or any medium"
date: 2023-01-08
forum: New to Ubuntu
---

### Post by electricmax on 2023-01-08
I'am tying to install one browser. I have downloaded the application but i am unable to install via CLI. Please guide me how to install an aplication via CLI like .deb or tar.gz (Note: Here CLI(Command Line Interface) means terminal)

---

### Post by ajgreeny on 2023-01-08
Without knowing more about the .deb package you wish to install it is impossible to give you any assurances that this will work but in general terms you need to 
1- 
cd to the folder where the .deb package is sitting, eg ***cd Downloads***.
2-
Run command ***sudo apt install ./packagename.deb*** changing the package name to whatever you downloaded and do not omit the ./ prefix.
Be aware that this is not the usual way to install packages; normally we use the repositories so tell us more about this package you want to install and use.

---

### Post by joshua123456 on 2023-01-08
There are various ways of doing it. I prefer to use the apt command, it will also install any missing dependencies.

in this example, the .deb file is located in the folder Downloads, and the program you are trying to install is skype.
```
sudo apt install ~/Downloads/skype*.deb
```

---

### Post by electricmax on 2023-01-08
@ajgreeny Unsuccessful.

---

### Post by ajgreeny on 2023-01-08
> **electricmax said:**
> @ajgreeny Unsuccessful.

Show us the full terminal content including the command you entered as that output does not make much sense to me.

Please use Code-Tags for all terminal output. Do not add images as they are often confusing and unhelpful.
See my signature below for a How-To.

---

### Post by electricmax on 2023-01-08
> **ajgreeny said:**
> Show us the full terminal content including the command you entered as that output does not make much sense to me.

Please use Code-Tags for all terminal output. Do not add images as they are often confusing and unhelpful.
See my signature below for a How-To.

Yes, The .deb files are installing now but tar.gz is not installing how to install tar.gz files? Is there any other command for installing tar.gz files. If yes please help me to install tar.gz application on my ubuntu. I tried but unsucessful.```
i dont find the option to tag the screenshots as code but i found this option wrap code, i think this is not the option to tag CLI screenshot images but i don't have any choice. If i found option to tag images in future then i will tag images as coding imges #codingimages, first help me to install tar.gz or xz files then you can write me regarding tagging screenshot images. I hope you will reply to this thread and you will write me solution for tar.gz or xz files so thank you for everything. 
```

---

### Post by tea for one on 2023-01-08
Open the terminal
Enter your command
Allow the command to succeed or fail

Copy the relevant text from the terminal output.
Open Adv Reply editing screen (i.e not Quick Reply)
Click on the code tag icon and paste.
The text should now be within code tags.

Preview post to double check content.

---

### Post by joshua123456 on 2023-01-08
> **electricmax said:**
> 
Yes, The .deb files are installing now but tar.gz is not installing how to install tar.gz files? Is there any other command for installing tar.gz files. If yes please help me to install tar.gz application on my ubuntu. I tried but unsucessful.

You can't directly install a tar.gz file. You need to extract the tar.gz file first. 

```
tar -xvzf /path/to/filename.tar.gz
```

---

### Post by MAFoElffen on 2023-01-08
But... You were asked what it was for, and what you were trying to install, so that they knew, at least a bit of what you were trying to do...


That is like saying: How do you open a box? And it is Pandora's Box. Or how do you erase a directory? And the directory is Root... 

You are not giving anyone any context or details. Please help the people who are trying to help you.

---

### Post by ajgreeny on 2023-01-08
Why are you messing around with a **tar.gz** archive of hexchat when it is available in the normal repositories and can therefore be installed with command ```
sudo apt install hexchat
``` or using a GUI package manager.

I wonder if you are still using the Windows method of installing applications by first searching for them on the web, then downloading them and finally installing, or trying to install what you downloaded.

That is not the way software is managed in Ubuntu (nor in most, if not all other Linux distros) where we nearly always install applications directly from the repositories using ```
sudo apt install packagename
``` or using one of the several GUI package managers available.
I very seldom use the GUI versions but if I do use one it is synaptic, never one of the other GUI Package managers.

Packages that you find and download as .tar.gz archives are not directly installed but need to be extracted first and the file or files it contains can then be investigated. The contents could be a single file, perhaps even a .deb package but is more likely to be either source code files which have to be compiled and built into a package, or perhaps a script and other data files that will install a package if the script is executed.  As a new user I suggest you do not bother with these methods, but wherever possible use the Ubuntu repositories.

Before you again start a search for a package to install in Ubuntu please search the repositories using one of the GUI software managers or ask here in the forum if you are having problems finding something that you want. There are also command line search facilities for finding applications but once again, as a new user you may find this more difficult than a GUI.

---

### Post by electricmax on 2023-01-10
> **ajgreeny said:**
> Why are you messing around with a **tar.gz** archive of hexchat when it is available in the normal repositories and can therefore be installed with command ```
sudo apt install hexchat
``` or using a GUI package manager.

I wonder if you are still using the Windows method of installing applications by first searching for them on the web, then downloading them and finally installing, or trying to install what you downloaded.

That is not the way software is managed in Ubuntu (nor in most, if not all other Linux distros) where we nearly always install applications directly from the repositories using ```
sudo apt install packagename
``` or using one of the several GUI package managers available.
I very seldom use the GUI versions but if I do use one it is synaptic, never one of the other GUI Package managers.

Packages that you find and download as .tar.gz archives are not directly installed but need to be extracted first and the file or files it contains can then be investigated. The contents could be a single file, perhaps even a .deb package but is more likely to be either source code files which have to be compiled and built into a package, or perhaps a script and other data files that will install a package if the script is executed.  As a new user I suggest you do not bother with these methods, but wherever possible use the Ubuntu repositories.

Before you again start a search for a package to install in Ubuntu please search the repositories using one of the GUI software managers or ask here in the forum if you are having problems finding something that you want. There are also command line search facilities for finding applications but once again, as a new user you may find this more difficult than a GUI.

Thank you so much for the brief description @greenyaj. I am trying to install the softwares which i have downloaded. For now i have downloaded hexchat package so i wan't to install through the package this time next time i ask in the forum before downloading the package whether it is available with ubuntu repositories or not.

---

### Post by electricmax on 2023-01-11
> **ajgreeny said:**
> Why are you messing around with a **tar.gz** archive of hexchat when it is available in the normal repositories and can therefore be installed with command ```
sudo apt install hexchat
``` or using a GUI package manager.

I wonder if you are still using the Windows method of installing applications by first searching for them on the web, then downloading them and finally installing, or trying to install what you downloaded.

That is not the way software is managed in Ubuntu (nor in most, if not all other Linux distros) where we nearly always install applications directly from the repositories using ```
sudo apt install packagename
``` or using one of the several GUI package managers available.
I very seldom use the GUI versions but if I do use one it is synaptic, never one of the other GUI Package managers.

Packages that you find and download as .tar.gz archives are not directly installed but need to be extracted first and the file or files it contains can then be investigated. The contents could be a single file, perhaps even a .deb package but is more likely to be either source code files which have to be compiled and built into a package, or perhaps a script and other data files that will install a package if the script is executed.  As a new user I suggest you do not bother with these methods, but wherever possible use the Ubuntu repositories.

Before you again start a search for a package to install in Ubuntu please search the repositories using one of the GUI software managers or ask here in the forum if you are having problems finding something that you want. There are also command line search facilities for finding applications but once again, as a new user you may find this more difficult than a GUI.

I replied to this post before but i think it's not delivered so i am sending you replay again, "Hello, good afternoon, as you mentioned in this post to go for synaptic i checked the application i found one useful or you can say i want to try the feature so i tried to download .deb file which is easy to install from terminal but i failed. Then i downloaded gpg file of tar.gz package, i tried to install gpg file but failed. I'm sending you the code, please solve this error.
```
udo apt install ./classicmaenu-indicator-0.11.tar.gz.gpg
[sudo] password for electricmax: 
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is heWaiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 16876 (synaptic) 
```

---

### Post by deadflowr on 2023-01-11
Close synaptic.

---

### Post by electricmax on 2023-01-12
> **deadflowr said:**
> Close synaptic.
Done.

---

### Post by electricmax on 2023-01-13
> **ajgreeny said:**
> Why are you messing around with a **tar.gz** archive of hexchat when it is available in the normal repositories and can therefore be installed with command ```
sudo apt install hexchat
``` or using a GUI package manager.

I wonder if you are still using the Windows method of installing applications by first searching for them on the web, then downloading them and finally installing, or trying to install what you downloaded.

That is not the way software is managed in Ubuntu (nor in most, if not all other Linux distros) where we nearly always install applications directly from the repositories using ```
sudo apt install packagename
``` or using one of the several GUI package managers available.
I very seldom use the GUI versions but if I do use one it is synaptic, never one of the other GUI Package managers.

Packages that you find and download as .tar.gz archives are not directly installed but need to be extracted first and the file or files it contains can then be investigated. The contents could be a single file, perhaps even a .deb package but is more likely to be either source code files which have to be compiled and built into a package, or perhaps a script and other data files that will install a package if the script is executed.  As a new user I suggest you do not bother with these methods, but wherever possible use the Ubuntu repositories.

Before you again start a search for a package to install in Ubuntu please search the repositories using one of the GUI software managers or ask here in the forum if you are having problems finding something that you want. There are also command line search facilities for finding applications but once again, as a new user you may find this more difficult than a GUI.

Hello,good morning @greenaj, i replied to this post twice because i thought you didn't received the post but later i came to know that only 10 post are viewed on one page and my reply was on the next page. I didn't received any reply to this thread i think you are irritated with my question's which are relevant to this thread i think. Thank you for all the support i am closing this thread. Have a good day!

---

