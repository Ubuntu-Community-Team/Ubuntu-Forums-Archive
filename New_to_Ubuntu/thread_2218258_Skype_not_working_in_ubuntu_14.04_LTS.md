---
title: "Skype not working in ubuntu 14.04 LTS"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by plabon2 on 2014-04-20
I installed skype using several process in my newly installed Ubuntu  14. 04 64 bit... it shows a skype icon in dash... but when I click on  it, nothings happens. What can I do?
  
I tried almost everything found in net. Every time it installed quite  normally and found skype icon in dash. But not opening, when I click on  it.

  
I downloaded skype 4.2 version from their website and installed using  software centre and also tried installing via command line. But still  not working.

  
When I  tried to run skype using terminal it produce following output--


skype: symbol lookup error: /usr/lib/i386-linux-gnu/libQtOpenGL.so.4: undefined symbol: _ZNK14QWidgetPrivate17hasHeightForWidthEv

---

### Post by monkeybrain20122 on 2014-04-20
[http://ubuntuforums.org/showthread.php?t=1764127](http://ubuntuforums.org/showthread.php?t=1764127)

I am curious though, how did you install Ubuntu, is it an upgrade? I installed skype on 14.04 64 bit (clean install) yesterday from the partners' repo then skyped my parents. Worked perfectly.

---

### Post by pdc on 2014-04-20
If you google on this 

> skype: symbol lookup error: /usr/lib/i386-linux-gnu/libQtOpenGL.so.4: undefined symbol: _ZNK14QWidgetPrivate17hasHeightForWidthEv

you find various threads: [http://community.skype.com/t5/Linux/Ubuntu-11-10-Skype-symbol-lookup-error/m-p/218214/highlight/false#M382](http://community.skype.com/t5/Linux/Ubuntu-11-10-Skype-symbol-lookup-error/m-p/218214/highlight/false#M382)

[http://askubuntu.com/questions/69187/skype-throws-a-symbol-lookup-error-after-upgrade-to-11-10](http://askubuntu.com/questions/69187/skype-throws-a-symbol-lookup-error-after-upgrade-to-11-10)

.........we leave it to you what you do ..................

> I installed skype using several process .........you might like to tell folks exactly; or as near exactly as you can; what you did

---

### Post by nns2006 on 2014-04-20
I was also getting this symbol problem but after restart everything work fine. Skype is working fine.

---

### Post by ccbmailroom on 2015-01-11
> **pdc said:**
> If you google on this 



you find various threads: [http://community.skype.com/t5/Linux/Ubuntu-11-10-Skype-symbol-lookup-error/m-p/218214/highlight/false#M382](http://community.skype.com/t5/Linux/Ubuntu-11-10-Skype-symbol-lookup-error/m-p/218214/highlight/false#M382)

[http://askubuntu.com/questions/69187/skype-throws-a-symbol-lookup-error-after-upgrade-to-11-10](http://askubuntu.com/questions/69187/skype-throws-a-symbol-lookup-error-after-upgrade-to-11-10)

.........we leave it to you what you do ..................

 .........you might like to tell folks exactly; or as near exactly as you can; what you did

Just jumping in here too, I tried installing skype via 

sudo apt-get purge skype 

...then...

sudo apt-get install libqt4-dbus:i386 libqt4-network:i386 libqt4-gui:i386 libqtwebkit4:i386 libxss1:i386 libxv:i386

...then...

sudo dpkg -i /path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb

...but I get...

dpkg: error processing archive /path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb


...  Trying to get a 32 bit set of software to work on a 64 bit system I'm told is difficult.  Is there a solution?  Or...is there another thread that has a solution for this?

---

### Post by mörgæs on 2015-01-11
> **ccbmailroom said:**
> 
dpkg: error processing archive /path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb (--install):
 cannot access archive: [COLOR=#ff0000]No such file or directory[/COLOR]


It's trying to tell you that *path/to/*... is not a real path but a placeholder. 

> **ccbmailroom said:**
> 
Trying to get a 32 bit set of software to work on a 64 bit system I'm told is difficult.
Where did you see that?

---

### Post by Mike_Walsh on 2015-01-11
> **plabon2 said:**
> I downloaded skype 4.2 version from their website and installed using  software centre and also tried installing via command line. But still  not working.

Correct me if I'm wrong, but as I understand it, version 4.2 of Skype no longer works correctly with Linux...

[http://www.linuxquestions.org/questions/slackware-14/skype-4-2-for-linux-retired-4175513647/](http://www.linuxquestions.org/questions/slackware-14/skype-4-2-for-linux-retired-4175513647/)
[http://askubuntu.com/questions/505581/skype-cant-connect](http://askubuntu.com/questions/505581/skype-cant-connect)
[https://bbs.archlinux.org/viewtopic.php?id=185113](https://bbs.archlinux.org/viewtopic.php?id=185113)

Regards,

Mike.

---

### Post by ccbmailroom on 2015-01-11
I cannot no matter how hard I try find the page I looked at last night.  This would be a "Botch" fail.

Anyway,  I personally had always been under the assumption that installing  something that is 32 bit in a 64 bit system was an okay thing to do.   The page that said that it was difficult...I just can't it.  

Are  there steps to get Skype to work in Ubuntu 14.04 that I can't find?   This laptop I'm using will probably have this OS until early 2019 when  Ubuntu 14.04 support ends and I want the usability (which for the most  part I have) but miss Skype tremendously.  

([{ unrelated note:  last night I found my Jaunty Jackalope Ubuntu disk from 2009!!! }])

---

### Post by Ko_Char on 2015-01-11
The problem is not about 32bit in a 64bit. 
The problem is that the command you typed is wrong. 

```
sudo dpkg -i /path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb
```

/path/to/skype-ubuntu-precise_4.3.0.37-1_i386.deb means where your downloaded skype package exists. 
If it is in the Downloads folder, the command is 

```
sudo dpkg -i ~/Downloads/skype-ubuntu-precise_4.3.0.37-1_i386.deb
```

If you're new to dpkg, it is recommended to use Software Center or gdebi instead. 
```
sudo apt-get update
sudo apt-get install gdebi
```

Right-click the skype-ubuntu-precise_4.3.0.37-1_i386.deb, and choose gdebi. 
Follow the instructions. 

If you used dpkg, there could be broken packages. Fix it by
```
sudo apt-get install -f
```

---

### Post by ccbmailroom on 2015-01-11
Currently, as of today (January 11, 2015), the available releases of Skype are

1.  Ubuntu 10.04 32-bit
2.  Ubuntu 12.04 (multiarch)
3.  Debian 7.4 (multiarch)
4.  Fedora 16 32-bit
5.  OpenSUSE 12.1 32-bit
6.  Dynamic

Which version would best be suitable for Ubuntu 14.04?

---

### Post by Bucky Ball on 2015-01-11
The version that's in the repositories. Enable the partner repository in your Software Sources (Software & Updates? and under the 'Other Software' tab), go to Software Centre, search for and install Skype with a couple of clicks.

The version I have from the repos is 4.3. It works flawlessly. Good luck.

---

### Post by newb85 on 2015-01-11
+1 to Bucky Ball's recommendation.  I've used it (contacting my family in the U.S. from Tokyo) with no problems, as well.

---

