---
title: "Update (Upgrade) from a different PPA"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by czgirb on 2013-09-13
I see a news [http://www.webupd8.org/2013/09/avidemux-video-editor-reaches-version.html](http://www.webupd8.org/2013/09/avidemux-video-editor-reaches-version.html) , which said that there was **AVIdemux 2.6.5**.
So, I do an Update ... yesterday is the Third update (upgrade) ... but after every update (upgrade) I did, my **AVIdemux** is still **2.5.4**.
I don't remember what PPA that I used when I install an **AVIdemux**.
So, in order to have 2.6.5 ... is it possible for us to change/shift a PPA?
Please guide me ...
[B]Thanks.

PS:
[/B]The question is not limited on AVIdemux only
Let's say ... it was for all Apps

---

### Post by Mephisto Pheles on 2013-09-13
you can find the ppa you're using in the sources list.
 yes you can add other ppa's to your sources list, manually or using aptitude (but beware what you add make sure it won't deliver any surprises so check them out first)

---

### Post by czgirb on 2013-09-13
> **JkbrrLJ said:**
> you can find the ppa you're using in the sources list.
 yes you can add other ppa's to your sources list, manually or using aptitude (but beware what you add make sure it won't deliver any surprises so check them out first)

... can add other ppa's to your sources list,
* manually
* using aptitude
> How? (Both) Would you mind to guide me, please?

  ... but beware what you add make sure it **won't deliver any surprises** so  **check them out first**
> What it means by **won't deliver any surprises**?
> Sorry! I am new to Ubuntu. So, please guide me **how to check it out** and **what point that I should be aware**?

**Thank you**

**Sorry for my English**

---

### Post by plucky on 2013-09-13
> To add the GetDeb repository, download and install THIS deb.

From the page you linked to, if you click on **This** link, it will download a .deb file.

If you navigate to the **Downloads** directory and click on the file,it will open the Software Centre and install the PPA.

You should then be able to install Avidemux after you run ```
sudo apt-get update
``` to update the index files.


Good Luck

---

### Post by Mephisto Pheles on 2013-09-13
oops sorry my fault, please take your time to read this
Repositories/Ubuntu
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

As long as you add trusted repositories you should be OK.
Just don't add everything you might see on a blog or on a forum somewhere or you might end up installing malware or other things that might corrupt your system etc.
Always look around first to try and determine whether the source, the ppa, can be trusted.

With **Trusted** I don't necessarily mean only those that ubuntu calls trusted. 
For example I use the gimp and wine ppa's because the versions on my release (12.04) are too old and not updated fast enough. 
Knowing plenty of people use those ppa's I take them to be "trustworthy".

---

### Post by su:bhatta on 2013-09-13
As Pointed out by Plucky : that link only downloads the repository, which you can be able to view in Sources.list, after you have Installed it through Ubuntu Software Center.

This is the link that is opening from that webup8 page : [http://www.getdeb.net/welcome/](http://www.getdeb.net/welcome/) which has more instructions linked here: [http://www.getdeb.net/updates/Ubuntu/13.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/13.04#how_to_install)  This page lists some bug with Kubuntu, if you are on Kubuntu that can be the problem, I didn't check what that Bug was about.

The Avidemux website ([http://avidemux.sourceforge.net/download.html](http://avidemux.sourceforge.net/download.html)) is also listing that Deb as way of installing or you have to install the application from tarball that is compile it from source.

In case you cannot get that particular ppa/version of Avidemux to work, perhaps you will be better off to remove it with ppa purge.

Its a bit strange, today only I installed Avidemux with Synaptic and the latest version for both QT & GTK is 1.2.5.4ubuntu13 !!

Using Gnome Saucy Beta, the repositories are so backdated?

---

### Post by grahammechanical on 2013-09-13
You are misunderstanding things a little bit. A developer may bring out an upgraded version of his software but that those not mean that the software will be updated when we run Update Manager in Ubuntu. To get upgraded versions of software including Ubuntu itself we have to upgrade to a newer version of Ubuntu.

For example, what version of Libreoffice do you have? I am assuming that you are using Ubuntu 12.04, Then you have Libreoffice version 3. But when Ubuntu 13.10 is released it will have Libreoffice 4. It is possible to install these upgraded applications in our existing Ubuntu version. We can download them from the developer's web site or use a PPA if one is provided.

The link to Webupd8 that you provided says

> Unfortunately Ubuntu (even Saucy) still has Avidemux 2.5.x available in its repositories,

Saucy is the code name for Ubuntu 13.10. So, to install Avidemux version 2.6 we need to do this

> but you can install the latest 2.6.x by using GetDeb.

and follow the instructions on that website. It might be best to remove Avidemux 2.5 first. Did you install it through the Ubuntu Software Centre? Then the Software Centre will remove it for you. Then follow the instructions to install Avidemux 2.6

Did you notice the warnings in that link about problems running Avidemux? That is why there is a delay in putting upgrade versions into the Software Centre and why these updates/upgrades to applications do not come to us when we update Ubuntu.

Regards.

---

