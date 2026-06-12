---
title: "subversion client help"
date: 2009-12-02
forum: Programming Talk
---

### Post by MrStill on 2009-12-02
I am working on a project for school and my group insists that we use Codeplex. (Microsoft) Codeplex only offers tutorials for Windows subversion clients. 

I have installed both Subversion 2.0.0 and TkCVS 8 (which does subversion as well as CVS). I am new to this type of collaboration and don't know much about version control; and, I haven't been able to find any good tutorials on how to do set up on either of these programs. 

I am curious if anyone has an suggestions on good tutorials and/or subversion clients that might be more desirable.  

Thanks

---

### Post by jpkotta on 2009-12-02
[http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

I usually use the command line svn, sometimes dsvn.el for Emacs.  My coworker uses kdesvn, but it always seems buggy.

---

### Post by cpetercarter on 2009-12-02
Subversion is not difficult to run from the command line. The most-used tutorial is [http://svnbook.red-bean.com/en/1.5/index.html]("http://svnbook.red-bean.com/en/1.5/index.html").

---

### Post by The Cog on 2009-12-03
[http://www.google.com/search?q=subversion+svn+tutorial](http://www.google.com/search?q=subversion+svn+tutorial)

For Windows, try the tortoise-svn client.
For Linux, I use rapidsvn which is in the Ubuntu repositories.

---

### Post by MrStill on 2009-12-03
> **The Cog said:**
> [http://www.google.com/search?q=subversion+svn+tutorial](http://www.google.com/search?q=subversion+svn+tutorial)

For Windows, try the tortoise-svn client.
For Linux, I use rapidsvn which is in the Ubuntu repositories.

I have read through several subversion tutorials, even before I posted this thread, including the Subversion manual. My partner is using tortoise which is an easy install and use; while all the clients I have been using so far have not worked. He is using it as an opportunity to bash Linux. 

I am beginning to think that there is an issue with my machine/set up as all clients seem to stall at the same point, adding a repository URL to check out. I have installed rapidSVN and I am going to try it now.

---

### Post by Can+~ on 2009-12-03
There's a plugin for nautilus:

[http://rabbitvcs.org/](http://rabbitvcs.org/)

(Name likely comes as a parody of "TortoiseSVN")

---

### Post by The Cog on 2009-12-04
> **Can+~ said:**
> There's a plugin for nautilus:

[http://rabbitvcs.org/](http://rabbitvcs.org/)

(Name likely comes as a parody of "TortoiseSVN")

I tried to view the screenshots but I get a page saying I don't have permission. Following the "fix it yourself" link takes me to a page pushing Microsoft anti-malware stuff. Not veryu impressive.

---

### Post by ib.lundgren on 2009-12-04
> I tried to view the screenshots but I get a page saying I don't have permission. Following the "fix it yourself" link takes me to a page pushing Microsoft anti-malware stuff. Not veryu impressive.

Site works fine for me. Use this to install it on Karmic...

```
wget http://rabbitvcs.googlecode.com/files/rabbitvcs_0.12.1-2%7Ekarmic_all.deb
sudo dpkg -i rabbitvcs_0.12.1-2~karmic_all.deb
```

Then logout and back in.

---

### Post by The Cog on 2009-12-05
Ah. Got it thanks. The web site works fine from home, just not from work. Now I have the installer, I can try it out next time I'm at work.

---

### Post by MrPok on 2010-01-14
> **ib.lundgren said:**
> Site works fine for me. Use this to install it on Karmic...

```
wget http://rabbitvcs.googlecode.com/files/rabbitvcs_0.12.1-2%7Ekarmic_all.deb
sudo dpkg -i rabbitvcs_0.12.1-2~karmic_all.deb
```

Then logout and back in.

Alternatively, 

You can install rabbitvcs via ppa as [described]("http://wiki.rabbitvcs.org/wiki/download") on their website.

Go to **System** >> **Administration** >> **Software Sources** 
then switch to tab "Other Software" and click **+Add**...
at this point paste the 
```
ppa:rabbitvcs/ppa
```
and click **Add source**.

After adding the ppa source, you need to install the program via **System** >> **Administration** >> **Synaptic Package Manager**. Do a "Search" for 'rabbit' and you will see it in the list. Select for install and click **Apply** in the top bar.

:!: Logging out and back in did not work for me: right-clicking in Nautilus didn't show any context menu options related to rabbitvcs (as shown in [screenshots]("http://wiki.rabbitvcs.org/wiki/about/screenshots")).
I needed a full restart to get the context menu options there.

:!: Also note that if you want to see icons in the context menu, from Karmic (which has a new gnome version) you have to enable this option; it is disabled by *default*. 
A quick way to do this right-clicking on the desktop background, selecting "Change Desktop Background", then switching to the "Interface" tab and there ticking the checkbox "Show icons in menus".

---

