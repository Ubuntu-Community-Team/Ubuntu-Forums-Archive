---
title: "Teamviewer Issue"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by serverman2 on 2013-10-11
Hi all this is my first time post here. Looking for help for using teamviewer 8 on ubuntu lts 12.04
Ive got to the stage where i can get it running with teamviewerd running. but it doesnt give me a teamviewer id.

It says Teamviewer ID: not found

I want to be able to use this remotely

Thanks in advance

---

### Post by The Spectre on 2013-10-12
Are you running the 64 bit or 32 bit version of Ubuntu 12.04?

And do you have the correct 64 bit or 32 bit version that matches your OS and is it the latest version of TeamViewer installed?

[http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)

---

### Post by serverman2 on 2013-10-12
Hi there ,

Both are 64 bit , teamviewer is fully working execept its not giving out an ID for connection.

If you need any specific info ill get it over to you. Hope you can help.

---

### Post by The Spectre on 2013-10-13
Confirm that you have the latest version TeamViewer installed which is currently v8.0.20931.

If it isn't try installing the the latest version, it might be a known issue that has been fixed.

If you are running the latest version already then you might want to try removing it from your computer and then re-installing it in case something did not get configured proberly when it was originaly installed... 

To remove TeamViewer from your computer run this command in Terminal...
```
sudo apt-get purge teamviewer
```

Then Download the latest version of TeamViewer and re-install...
[http://download.teamviewer.com/download/teamviewer_linux_x64.deb](http://download.teamviewer.com/download/teamviewer_linux_x64.deb)

---

### Post by serverman2 on 2013-10-14
> **The Spectre said:**
> Confirm that you have the latest version TeamViewer installed which is currently v8.0.20931.

If it isn't try installing the the latest version, it might be a known issue that has been fixed.

If you are running the latest version already then you might want to try removing it from your computer and then re-installing it in case something did not get configured proberly when it was originaly installed... 

To remove TeamViewer from your computer run this command in Terminal...
```
sudo apt-get purge teamviewer
```

Then Download the latest version of TeamViewer and re-install...
[http://download.teamviewer.com/download/teamviewer_linux_x64.deb](http://download.teamviewer.com/download/teamviewer_linux_x64.deb)


reinstalled it this is what i get :( 


TeamViewer                      8.0.20931 


 teamviewerd status              teamviewerd start/running, process 2336 


TeamViewer ID: not found
Try restarting the TeamViewer daemon (e.g. teamviewer --daemon restart)

---

### Post by The Spectre on 2013-10-15
> **serverman2 said:**
> reinstalled it this is what i get :(

When you re-installed did you remove TeamViewer first?

That way if there are any setting that is causing the problem it should put TeamViewer back to default settings when it is re-installed. 


The other thing that that might be causing the problem is if you have TeamViewer's access being blocked by a Firewall either by your Router or in Ubuntu or both.

---

