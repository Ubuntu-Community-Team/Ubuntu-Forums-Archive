---
title: "SVN client for Linux?"
date: 2005-11-18
forum: Programming Talk
---

### Post by Faerine on 2005-11-18
[INDENT][/INDENT]I need to connect to a Subversion repository for my work. I use Netbeans, where I was not able to install proper SVN support (it doesn't find the SVN commanands, and anyway I need CVS to checkout Netbeans source etc., so maybe SVN in Netbeans is not the best idea). 
[INDENT][/INDENT]Under windows at work I use a program called TortoiseSVN, which unfortunately is windows only. What it does is add SVN menus to windows explorer right click, so I don't think it would run with Wine and Nautilus or Konqueror. Do you guys know of any good SVN client program for Linux? I tried SmartSVN, but it is closed source and the version I need is paid, and I didn't switch to Linux to use such programs. However, I wouldn't want to be stuck using SVN from the command line either. :)

---

### Post by bignate on 2005-11-18
apt-cache search svn turns up at least one gui svn program...rapidsvn, no idea how good it is.

---

### Post by DJ_Max on 2005-11-18
Netbeans probably can't find SVN commands because you need to install SVN first.

---

### Post by Faerine on 2005-11-18
I installed the Netbeans SVN plugin, and according to the instructions no separate SVN installation was needed. I only need an SVN client, the server is somewhere else. Anyway, I prefer Netbeans to stay with CVS, since it cannot use both simultaneously, and I don't want to switch all the time. 

I will try RapidSVN and see what happens. :)

---

### Post by mgor on 2005-11-19
```
sudo apt-get install subversion
```
...and you'll get the client. RapidSVN probably depends on subversion.

---

### Post by amerigo5 on 2005-11-19
You can try SmartSVN: [http://www.smartcvs.com/smartsvn/](http://www.smartcvs.com/smartsvn/)

---

### Post by majikstreet on 2005-11-19
[QUOTE=amerigo5]You can try SmartSVN: [http://www.smartcvs.com/smartsvn/](http://www.smartcvs.com/smartsvn/)[/QUOTE]
"I tried SmartSVN, but it is closed source and the version I need is paid, and I didn't switch to Linux to use such programs."

---

### Post by floam on 2005-11-19
What in the heck is wrong with the console svn client?

---

### Post by jlist on 2005-11-25
rapidsvn 9 has been out for a while. Who will be putting it in to the repository? When?

---

