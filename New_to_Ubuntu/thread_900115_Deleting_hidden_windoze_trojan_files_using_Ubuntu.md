---
title: "Deleting hidden windoze trojan files using Ubuntu"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by MO-GSer on 2008-08-25
Hi All,  

I'm new to the forum and am just installing Ubuntu on one of my PCs.  On another of my PCs (windoze) I found some trojan rootkit files using Rootkitrevealer (the sysinternals program) and I thought it would be a good experiment/learning experience to try to delete those files in windoze utilizing Ubuntu.  So I got a Hardy Heron live cd and booted it up.  

Now, I know the files are on the disk in the windoze/temp directory as I could see them in rootkitrevealer but I cannot see them in Ubuntu.  The files have names like .tt4.tmp.vbs and I have tried the ctl H and I also logged in as root and used terminal (ls -a) to look in the directory but they do not show up.  

Also, there are two files in the windoze/system32 folder that show up in rootkitrevealer.  One named lphccjjxxxxx.exe and one named blphccjjxxxxx.scr  and the .exe file shows in Ubuntu but the scr file seems to be hidden from Ubuntu.  

Long post, but my question is, is there another application other than Nautilus that I could try to see if the files are visible to me?  Or, is the fact that the files are hidden from the windoze api make them also invisible to Ubuntu???

Thanks in advance for any assistance.

Harry

P.S.  I did search the forum and found a few posts on the subject of hidden files and windoze but nothing that seemed to address my particular problem.

---

### Post by Gone fishing on 2008-08-25
Nautilus should be able to see them - the "." in ".tt4.tmp.vbs" will make the file hidden but just un hide in nautilus the options. If they are in the temp directory can't you just delete the directory and then remake it?

---

### Post by bumanie on 2008-08-25
You could install clamav with the gtk front end via synaptic and do a recursive scan of windows folders. clamav is as up to date as commercial av varieties.

---

### Post by MO-GSer on 2008-08-25
> **bumanie said:**
> You could install clamav with the gtk front end via synaptic and do a recursive scan of windows folders. clamav is as up to date as commercial av varieties.

Thanks for the suggestion.  I hadn't thought about linux having an antivirus application :)

But in the synaptic package manager, I don't see clamav.  I did a refresh of the list and searched for the word virus also but cannot see anything except amavisd-new that relates to viruses.  Do I need to "point" synaptic to another repository or something to find clamav??

thanks,

Harry

---

### Post by MO-GSer on 2008-08-25
> **Gone fishing said:**
> If they are in the temp directory can't you just delete the directory and then remake it?

Thanks for the suggestion but where's the fun in that?? :)

I'm also trying to use this "opportunity" to learn a little about linux.  I thought this might be a good way to get started learning.

thanks,

Harry

---

### Post by Ryadt on 2008-08-25
Make sure you've got everything checked in System > Admininstration > Software Sources > Ubuntu Software.
Then type in terminal```
sudo apt-get update && sudo apt-get upgrade
```
Then try to install clamav.

---

### Post by MO-GSer on 2008-08-25
> **bumanie said:**
> You could install clamav with the gtk front end via synaptic and do a recursive scan of windows folders. clamav is as up to date as commercial av varieties.

I forgot!

Love  your sig

amen to that!

Harry

---

### Post by SpaceMaster on 2008-08-25
> **MO-GSer said:**
> Thanks for the suggestion.  I hadn't thought about linux having an antivirus application :)

But in the synaptic package manager, I don't see clamav.  I did a refresh of the list and searched for the word virus also but cannot see anything except amavisd-new that relates to viruses.  Do I need to "point" synaptic to another repository or something to find clamav??

thanks,

Harry

I'm not certain, but you may need to enable "Multiverse" in System -> Software Sources -> Ubuntu Software to get Clam AV.

---

### Post by Battie on 2008-08-27
As you dig around, please let me know if you find a tdssserv.sys file in Windows\System32\drivers.  I had a computer with the first two infected files you mentioned that also had the tdss rootkit files (there are several).  I want to determine if they are the same virus, or different ones.

---

### Post by MO-GSer on 2008-08-28
> **Battie said:**
> As you dig around, please let me know if you find a tdssserv.sys file in Windows\System32\drivers.  I had a computer with the first two infected files you mentioned that also had the tdss rootkit files (there are several).  I want to determine if they are the same virus, or different ones.

I'll let you know.  Right now I had the ubuntu live cd hang so I'm in the process of installing ubuntu to the hard drive and then I'll go back to the windoze problem.  

One difficulty I have with linux in general is that I use hughes for my ISP (satellite internet) and there are restrictions on how much I can download in one 24 hour period.  And as I'm finding out, there are some serious downloads on linux for the updates depending on how many applications you install.

I think I have a "free" period like 3-4am each day that I can download as much as I want but I have to find a good linux download manager that will allow me to schedule downloads during that period only.  Otherwise I'll have to take the system downtown to my wife's office where I can hook up to DSL and do all the downloads.  

Harry

---

### Post by egalvan on 2008-08-28
> **MO-GSer said:**
> y.  Otherwise I'll have to take the system downtown to my wife's office where I can hook up to DSL and do all the downloads.  

Harry

APTonCD is a good way to go.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Also, consider purchasing a copy of the repos on DVD, they run about $30 for the four or five DVD's.

[http://www.osdisc.com/](http://www.osdisc.com/)

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu/repo.html)


ErnestG

:popcorn:

---

