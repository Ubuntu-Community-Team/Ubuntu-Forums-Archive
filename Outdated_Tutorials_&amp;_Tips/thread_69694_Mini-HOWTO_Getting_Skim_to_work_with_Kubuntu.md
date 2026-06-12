---
title: "Mini-HOWTO: Getting Skim to work with Kubuntu"
date: 2005-09-27
forum: Outdated Tutorials &amp; Tips
---

### Post by GoldBuggie on 2005-09-27
I am writing this because I want to share the result I got after fiddeling for many days. Skim finally completly work on my system now. All KDE apps and firefox/OpenOffice(and others) works with the japanese input system.

For you that don't know: Skim/Scim is an input system for other languages like japanese or chinese. This little helper is for japanese, but easy to change into any other system.

First install ```
sudo apt-get install scim scim-gtk2-immodule scim-uim scim-tables-ja
```. This will be the input system that with some easy tweaking will work for firefox.

Secondly we need to download and compile "Skim". The latest version of skim doesn't work with the version of scim that ubuntu provides so I downloaded "*skim-1.0.2.tar.bz2*". If you want later version you will have to dl and compile them yourself.

Untar the file and in the untar:d directory do a:
```
 ./configure --prefix="/usr"
 make
 sudo make install
``` 
(Note: i use the prefix since otherwise it will install into */usr/local* but ubuntu uses */usr* as its apps directory)

Now you should have everything that is needed to get it to work. You just need to set some enviorment variables.

Before we set them I would test if it all works. Start ```
scim-panel-kde -d -f
``` Do some configuring and then _restart KDE_.

Now in the konsole do a ```
scim -d
``` then afterwards a ```
LC_CTYPE=ja_JP.UTF-8 XMODIFIERS="@im=SCIM" kate
``` This should startup kate and you should have japanese input(after a **ctrl-space** press that is).

Now to make skim/scim work always.

In **~/.bashrc** enter these lines

```
 LC_CTYPE=ja_JP.UTF-8
 export LC_CTYPE

 XMODIFIERS="@im=SCIM"
 GTK_IM_MODULE="scim"
 XIM_PROGRAM="scim -d"
 QT_IM_MODULE="scim"

 export XMODIFIERS GTK_IM_MODULE XIM_PROGRAM QT_IM_MODULE  
``` 
After this you should have a nice Skim&Scim working enviorment. Hope this helps.

(I did install the anthy module that came from scim-im.org but I do not think this will effect the installation in any way so i left that part out. This howto may need some cleaning up. But I'll leave that for later. I'm going to Japan in 3 days.)

---

### Post by BdON003 on 2005-10-04
Is there any way to get this to work in Ubuntu? I'd really like to know.  Thanks

---

### Post by GoldBuggie on 2005-10-05
In gnome you only need scim not skim i'm gussing. But doing this without installing skim should work if its the input engine you are looking for.

---

### Post by TheRealCryss on 2005-10-07
Hi.


I'have added the above code to my user-bashrc and even in the /etc/.basrc
but it doesn't work.

If i start kate in kde (ubuntu) from a console with the command "LC_CTYPE=ja_JP.UTF-8 XMODIFIERS="@im=SCIM" kate" it works.

I don't understand this.  :confused:

---

### Post by GoldBuggie on 2005-10-07
Wish I knew directly why is doesn't work otherwise. But what you haev to make sure of is that the code that i worte for **~/.bashrc **is executed. You do not have to make it into bashrc. Other files will work as well as long as you are sure it is executed.

that kate works with the command prooves that you have everything installed correctly. Now you only need to make the setup of the export variables to work. Try playing around with it.

---

### Post by SnEptUne on 2005-10-08
Putting environment variables in ~/.bashrc will only works for applications that start within bash.  If you want it take effect globally, perhaps you should put it in /etc/environment.

**/etc/enviroment**
```
QT_IM_MODULE="scim"
```

On the other hand, compiling skim requires many other additional library and dev files that are no installed on Kubuntu by default.  Before running ./configure, apt-get install the following dev and libs.

```
sudo apt-get install libqt3-mt-dev xlibs-dev kde-core kdelibs4-dev scim-dev
```

I know it is a lot of packages.  But you can remove them after you installed skim.  I don't mind package up my skim binary as a deb file; however, I don't have any webspace to host the file.  Hope my suggestions help.

If you want to compile scim and the rest, I would recommend using this guide (it is in Simplified Chinese, but surely you can figure it out):  [http://www.ubuntu.org.cn/support/documentation/doc/deb-scim](http://www.ubuntu.org.cn/support/documentation/doc/deb-scim).

However, it seems like scim/skim would not work properly for QT applications because the QT that comes with (k)ubuntu has not been patched with qtimm, the there are no scim-qtimm support for the binary scim.

It is possible to compile them all, but it would be a lot of work.

Has anyone been able to get skim working in konsole, openoffice, or other QT applications?

---

### Post by GoldBuggie on 2005-10-09
>  Has anyone been able to get skim working in konsole, openoffice, or other QT applications?

I got it to work on all apps by doing the above. Done it on 2 computers now.

But as I said before...if you don't want to use bashrc you can use other preexecuting files.

---

### Post by knockey on 2005-10-16
[QUOTE=SnEptUne]
```
sudo apt-get install libqt3-mt-dev xlibs-dev kde-core kdelibs4-dev scim-dev
```

I know it is a lot of packages.  But you can remove them after you installed skim. [/QUOTE]

Is there a convenient way to remove those packages? I have no idea anymore what the names of those other 80-odd packages were.

---

### Post by Shadow Slasher on 2006-05-05
Hi Gold Buggie,

Thanks for your post.

I have a question, since I am a Linux noob and know very little.

You said, 

Untar the file and in the untar:d directory do a:
Code:

./configure --prefix="/usr" make sudo make install


But I have no idea how to do this.  Under the "untar:d directory do a:....."

Can you help?

Thanks!

(I too have been searching for how to setup Japanese input in Linux, and unfortunately it is REALLY difficult to come up with quality info.)

- Shadow Slasher

---

### Post by Shadow Slasher on 2006-05-05
Hi Gold Buggie,

Thanks for your post.

I have a question, since I am a Linux noob and know very little.

You said, 

Untar the file and in the untar:d directory do a:
Code:

./configure --prefix="/usr" make sudo make install


But I have no idea how to do this.  Under the "untar:d directory do a:....."

Can you help?

Thanks!

(I too have been searching for how to setup Japanese input in Linux, and unfortunately it is REALLY difficult to come up with quality info.)

- Shadow Slasher

(Dupe post - sorry)

---

