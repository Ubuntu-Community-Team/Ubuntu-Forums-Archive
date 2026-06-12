---
title: "[SOLVED] OpenOffice 3 troubles"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-28
I have just downloaded and installed the .debs for openoffice3 and everything went without a hitch. Well, almost. The program didn't register any mime-types nor did it add menu entries. I can do each of these by myself...but there are numerous file types for each of the numerous apps (writer,calc,base,draw,etc). My question is does anyone know why this installed this way and is there a way to forgo adding my own menu items and mime-types/icons and so forth?

Thanks guys

---

### Post by TenPlus1 on 2008-10-28
If you&#8217;re running Ubuntu (or another .deb-based OS) then you&#8217;re in luck. Debian versions of OOo are now available on most download sites (SA-based users check out these mirrors for a download) and installing OOo 3.0 is fairly straightforward. We explain:

First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*

Next, download a copy of OpenOffice.org 3.0 (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz worked for us) and extract the download:

tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

That will create a directory called something like OOO300_m9_native_packed-1_en-US.9358.

Switch into the DEBS directory in that directory:

cd OOO300_m9_native_packed-1_en-US.9358/DEBS/

Now all you need to do is install all of those .deb packages:

sudo dpkg -i *.deb

That will do the trick. Once you&#8217;ve given your password your system should install all of the required files.

With that done you should have just one thing left to do: Install the desktop integration package. That should be in the DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

If everything works out you should be able to open OpenOffice.org 3.0 from the Applications menu on your desktop.

---

### Post by JohnGalt131 on 2008-10-28
> **TenPlus1 said:**
> If you’re running Ubuntu (or another .deb-based OS) then you’re in luck. Debian versions of OOo are now available on most download sites (SA-based users check out these mirrors for a download) and installing OOo 3.0 is fairly straightforward. We explain:

First, remove your existing version of OpenOffice.org:

sudo apt-get remove openoffice*.*

Next, download a copy of OpenOffice.org 3.0 (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz worked for us) and extract the download:

tar -zxvf OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

That will create a directory called something like OOO300_m9_native_packed-1_en-US.9358.

Switch into the DEBS directory in that directory:

cd OOO300_m9_native_packed-1_en-US.9358/DEBS/

Now all you need to do is install all of those .deb packages:

sudo dpkg -i *.deb

That will do the trick. Once you’ve given your password your system should install all of the required files.

With that done you should have just one thing left to do: Install the desktop integration package. That should be in the DEBS folder:

cd desktop-integration

From that folder install the package:

sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

If everything works out you should be able to open OpenOffice.org 3.0 from the Applications menu on your desktop.

Excellent! Thanks.

---

### Post by Eric Qel-Droma on 2008-10-28
Why is it that OpenOffice.org 3.0 is not in the "official" Ubuntu repositories yet?

---

### Post by brandoncolorado on 2008-10-28
This is why:

[http://www.tectonic.co.za/?p=3447](http://www.tectonic.co.za/?p=3447)

---

### Post by Eric Qel-Droma on 2008-10-28
> **brandoncolorado said:**
> This is why:

[http://www.tectonic.co.za/?p=3447](http://www.tectonic.co.za/?p=3447)

That's why it's not in 8.10.  I'm using 8.04.  Aren't they two different things using different repositories?

I guess a better question from me is this:  Will we get 3.0 in 8.04 using Synaptic, or will I have to download tar.gz stuff and do all the command line stuff?  I *can* do it, but it always makes me nervous to do things manually, as I don't have time to break my box and take three hours to fix it like I did when I was 18.

In any case, thanks for the link.  Interesting reading.

Eric

---

### Post by stackoverflow on 2008-10-29
I found this article describing exactly that.


[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

---

