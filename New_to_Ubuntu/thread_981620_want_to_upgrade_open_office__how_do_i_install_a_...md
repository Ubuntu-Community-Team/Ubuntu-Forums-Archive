---
title: "want to upgrade open office  how do i install a ...tar.gz"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by zippytex on 2008-11-13
I just went through the rather long process of upgrading to 8.10.  No problems.   I want to upgrade open office to 3.0.  I downloaded the ...tar.gz file.  However, I do not know how to install it.  I opened it up and upacked it, but then what?

I am hoping there is some "command-line" code that I can enter to install it.  The exact name of the file is:  00o-3.0.0_LinuxIntel_install_wJre-en-US.tar.gz

Thanks very much.:confused:

---

### Post by wookiehangover on 2008-11-13
The easiest way to upgrade open office in 8.10 is to follow this guide:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

It worked perfectly for me.

If yr really set on doing it with the command line, you first need to uncompress the file with:

tar xvfz filename.tar.gz

Then manually install with:

./configure
make
sudo make install

Just a caveat: you have a much better shot at actually getting it installed by following the guide above. Manual installs tend to get a little sticky because they don't automatically resolve dependencies and such for you. Srsly, just use the guide.

---

### Post by randy78 on 2008-11-13
If you selected the tar.gz.deb package, just right click on it and select Extract Here...

Make sure the extracted folder is in the extracted directory, move it there.

Open a terminal and type: cd /home/YourUserName/OOO300_m9_native_packed-1_en-US.9358/DEBS

Then type: sudo dpkg -i *.deb

Once it completes, type: cd desktop-integration && sudo dpkg -i openoffice.org3.0-debian-menus_3.0-9354_all.deb

---

### Post by Viranh on 2008-11-13
There should be .debs available for open office 3.0. They will be much easier to install. 

You can also add these sources and update using apt/update manager
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

Here is a decent tutorial for it:
[http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/](http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/)

---

### Post by starcannon on 2008-11-13
+1 to Viranh's suggestion, that method will also keep it updated.

Otherwise the absolute easiest way to install 3.0 is to just download the .deb from this page:
[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

double click the file when download is finished, and let the package manager do the rest.

---

### Post by zippytex on 2008-11-13
Thanks.  I did as you said and it downloaded some upgrades and has just about finished installing them.  You are right, it is easier.  I worked in MS DOS for years.  I love the simplicity of the command line, but this is easier.  It just finished and is working fine!  Thanks.

---

