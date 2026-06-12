---
title: "Opinions on wysiwyg html editor for creating simple Doc"
date: 2013-08-16
forum: New to Ubuntu
---

### Post by Traxster on 2013-08-16
Hello to all,

I know this question has been asked before, however, all the threads i saw were old. Looking for an html editor that does not require me to know html. I just need to create some simple web documents that I will be using for personal use. Although I know a little about html, I just don't have time to dig into a book at this time. By the way, I have found some on synaptic like tynymce, gwrite, and blogilo. I did not see kompozer on there ? Your opinions would be greatly appreciated.





traxster

---

### Post by NM5TF on 2013-08-16
I have been using Kompozer for a while now & like it lots....very easy to use...
there are many others out there, but for your casual use go with Kompozer...

you can check out my webpage here:

[http://users.gilanet.com/~tfrost](http://users.gilanet.com/~tfrost)

YMMV

Tommy

---

### Post by Traxster on 2013-08-17
> **NM5TF said:**
> I have been using Kompozer for a while now & like it lots....very easy to use...
there are many others out there, but for your casual use go with Kompozer...

you can check out my webpage here:

[http://users.gilanet.com/~tfrost](http://users.gilanet.com/~tfrost)

YMMV

Tommy

sounds good, I downloaded kompozer, and extracted it. what is the command to install it now? I can't seem to find it anywhere. 

thanks

traxster

---

### Post by howefield on 2013-08-17
> **Traxster said:**
> sounds good, I downloaded kompozer, and extracted it. what is the command to install it now? I can't seem to find it anywhere. 

thanks

traxster

There may be better options than kompozer...

> Latest stable version: 0.7.10 (2007-08-30)
Warning: this version does NOT work with recent GNU/Linux distros.
KompoZer 0.7 is not compatible with GTK &#8805; 2.14 — expect crashes. If you’re using a Linux distro that ships KompoZer 0.7.10 with GTK &#8805; 2.14, please inform the package maintainers about this. 

Latest development version: 0.8b3 (2010-02-28)

---

### Post by Lars Noodén on 2013-08-17
Manual downloads are messy.  Use the Software Center or Synaptic if you can.  Same goes for any other package.  That way the package manager can take care of updates and any dependencies there might be.  It also makes it easy to uninstall packages after you have tried them.  It looks like Ubuntu stopped including Kompozer though. 

If you manually download packages to your system it will get messy and may eventuall stop working.  It's really best to let the package manager do all that work if you have the option.

Back to the main question, in addition to Kompozer, you might also want to look at Bluefish.  It's there in the repository and so will install with a click or two.

---

### Post by Lars Noodén on 2013-08-17
If you roll down to the bottom of this page you can see the link to the Kompozer PPA:

[http://www.kompozer.net/download.php](http://www.kompozer.net/download.php)

PPAs require a little setup but do give you the advantages of using the package manager.  

[http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu)

---

### Post by NM5TF on 2013-08-17
HOWEFIELD....


I am using Kompozer v 0.8b3 20081229.....it works great with Precise 12.04 LTS...

don't know what version of GTK I have tho...how do I find that???

Tommy

---

### Post by howefield on 2013-08-17
> **NM5TF said:**
> HOWEFIELD....


I am using Kompozer v 0.8b3 20081229.....it works great with Precise 12.04 LTS...

don't know what version of GTK I have tho...how do I find that???

Tommy

If you read the post, it is the stable version that has trouble with earlier versions of gtk, the development version doesn't have this issue.

I'm only saying that using a stable version that is 6 years old or a development version that is 3.5 years old doesn't seem a great couple of options to me.  :)

I'm glad it does what you need.

---

### Post by vasa1 on 2013-08-17
> **Traxster said:**
> ... I just need to create some simple web documents that I will be using for personal use. ...
Another option is to use something like **ReText**: you do the writing in markdown and get a preview in html in a sidepane or you can export to html.
Currently, I'm using **gedit** with a [markdown preview plugin]("http://www.jpfleury.net/en/software/gedit-markdown.php") to see my markdown notes as html.

---

### Post by Traxster on 2013-08-17
> **Lars Noodén said:**
> Manual downloads are messy.  Use the Software Center or Synaptic if you can.  Same goes for any other package.  That way the package manager can take care of updates and any dependencies there might be.  It also makes it easy to uninstall packages after you have tried them.  It looks like Ubuntu stopped including Kompozer though. 

If you manually download packages to your system it will get messy and may eventuall stop working.  It's really best to let the package manager do all that work if you have the option.

Back to the main question, in addition to Kompozer, you might also want to look at Bluefish.  It's there in the repository and so will install with a click or two.

I agree, I always choose the repositories first if tha package is available.

I looked for kompozer in synaptic and in the Ubuntu repository, by typing  ```
sudo apt-get install kompozer
``` both times package was not found. I can try Bluefish, but I heard that it is not a WYSIWYG editor?

---

### Post by Traxster on 2013-08-17
> **Lars Noodén said:**
> If you roll down to the bottom of this page you can see the link to the Kompozer PPA:

[http://www.kompozer.net/download.php](http://www.kompozer.net/download.php)

PPAs require a little setup but do give you the advantages of using the package manager.  

[http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu](http://www.omgubuntu.co.uk/how-to-add-a-ppa-to-software-sources-in-ubuntu)

  Apparently, this ppa works only with older versions of ubuntu. I am on 13.04 (amd64). Below are my steps for how I installed it and the response from terminal.

```
root@hades:~# apt-add-repository ppa:giuseppe-iuculano/ppa
You are about to add the following PPA to your system:
 At this moment you can find:

- Freemat (intrepid, hardy)
- Kompozer (hardy, intrepid,jaunty)
- amsn
 More info: https://launchpad.net/~giuseppe-iuculano/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpt4100b/secring.gpg' created
gpg: keyring `/tmp/tmpt4100b/pubring.gpg' created
gpg: requesting key 623C928A from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpt4100b/trustdb.gpg: trustdb created
gpg: key 623C928A: public key "Launchpad PPA for Giuseppe Iuculano" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
root@hades:~# apt-get install kompozer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kompozer
root@hades:~#
```

**NOTE** also typed ```
 apt-get update
``` and ```
 apt-get install kompozer
``` again but it still did not work.


however, I went directly to kompozer.net downloaded the latest linux package to ~/Downloads then extracted it.
there is one final command in terminal to install the package. How do I install the package? Below is what is inside the extracted package from downloaded package. 

```
martin@hades:~/Downloads/kompozer$ ls
bloaturls.txt       kompozer-config    libplds4.so             plugins
chrome              libfreebl3.chk     libsmime3.so            regxpcom
components          libfreebl3.so      libsoftokn3.chk         res
defaults            libgfxpsshar.so    libsoftokn3.so          run-mozilla.sh
dependentlibs.list  libgkgfx.so        libssl3.so              shlibsign
dictionaries        libgtkembedmoz.so  libxpcom_compat.so      TestGtkEmbed
elf-dynstr-gc       libgtkxtbin.so     libxpcom_core.so        updater
extensions          libjsj.so          libxpcom.so             updates
greprefs            libmozjs.so        libxpistub.so           xpcshell
icons               libnspr4.so        LICENSE                 xpicleanup
install.log         libnss3.so         mangle                  xpidl
kompozer            libnssckbi.so      mozilla-xremote-client  xpt_dump
kompozer-bin        libplc4.so         nsinstall               xpt_link
martin@hades:~/Downloads/kompozer$ 

```

I want to try kompozer before I rule it out.

thanks again,

traxster

---

### Post by Lars Noodén on 2013-08-17
Bluefish is not quite wysiwyg but many I've spoken with praise it.   Given how hard Kompozer is (at the moment) to install, it might be your better option.   Myself, I tend to use Emacs but that only has a preview mode that launches the page being edited in a web browser.

The Kompozer site does provide the source so it might be possible to install all the dependencies and then build it as a custom package.  

Though it does not help here and now, I put in a bug request that Kompozer be packaged:

[https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/1213459](https://bugs.launchpad.net/ubuntu/+source/kompozer/+bug/1213459)

It's a useful enough app that it should have a place in the repository.

---

### Post by Lars Noodén on 2013-08-17
Here are some notes on installing Kompozer on recent versions of Ubuntu:

[http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/](http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/)

I haven't had a chance to verify them but the comments seem positive and the instructions clear.

---

### Post by 3rdalbum on 2013-08-17
Kompozer doesn't need to be "installed". Just double-click the Kompozer application in the folder you downloaded and it will run.

Personally I use Bluegriffon, it is based on Kompozer and has some good additional features. It also runs in-place with no installation necessary.

---

### Post by Traxster on 2013-08-17
> **3rdalbum said:**
> Kompozer doesn't need to be "installed". Just doubleIs-click the Kompozer application in the folder you downloaded and it will run.

Personally I use Bluegriffon, it is based on Kompozer and has some good additional features. It also runs in-place with no installation necessary.
 
I tried double clicking and right click then run on the kompozer-bin file. Both menthods failed to launch the file.

Is Bluegriffon available from the respositories?

---

### Post by Traxster on 2013-08-17
> **Lars Noodén said:**
> Here are some notes on installing Kompozer on recent versions of Ubuntu:

[http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/](http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/)

I haven't had a chance to verify them but the comments seem positive and the instructions clear.


Finally! The instructions in the above link worked!! I will evaluate and will report back.


thanks, 


traxster

---

### Post by Traxster on 2013-08-17
O.k.

Got kompozer installed finally and I love it. It's perfect for what I want it for and the WYSIWYG interface works well. I will, in time, be reviewing other software and plan on learning more about HTML. 

Thank-You to ALL who posted on this thread.


traxster

---

### Post by NM5TF on 2013-08-19
if you're interested in learning HTML or CSS, then you might want to look at [www.codeacademy.com](www.codeacademy.com) for 
some FREE interactive lessons....also offer JavaScript, PHP, Ruby, and jQuery lessons.....

Tommy

---

### Post by Traxster on 2013-08-19
> **NM5TF said:**
> if you're interested in learning HTML or CSS, then you might want to look at [www.codeacademy.com]("http://www.codeacademy.com") for 
some FREE interactive lessons....also offer JavaScript, PHP, Ruby, and jQuery lessons.....

Tommy

I will take a look thanks;


traxster

---

