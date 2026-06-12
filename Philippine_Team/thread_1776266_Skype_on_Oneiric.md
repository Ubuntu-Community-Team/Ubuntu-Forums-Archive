---
title: "Skype on Oneiric"
date: 2011-06-05
forum: Philippine Team
---

### Post by antoniomiguel on 2011-06-05
Is skype taken off from the repository?  I'm having problem installing

---

### Post by Script Warlock on 2011-06-05
sigurado sangkatutak na bugs pa yan. subukan mo na lang install sa site nila tapos at dpkg -i file.deb parang di ko na din namalayan sa natty repo ang skype.

---

### Post by antoniomiguel on 2011-06-06
I did try to install from the deb file from skype site, unsuccessful due to some dependency issues.  Well, the deb file says is for 10.04 so that explains the reason :)

---

### Post by Script Warlock on 2011-06-06
pero pwede mo naman install skype sa natty so i think walang pinagkaiba sa 11.10. kung sakaling may error apt-get -f install lang.

---

### Post by donut123 on 2011-06-06
Go to skype site and download from there..it should work.

---

### Post by antoniomiguel on 2011-06-06
> **Script Warlock said:**
> pero pwede mo naman install skype sa natty so i think walang pinagkaiba sa 11.10. kung sakaling may error apt-get -f install lang.

It did work, thanks!

---

### Post by donut123 on 2011-06-07
> **antoniomiguel said:**
> It did work, thanks!
yeah Man no problem :KS

---

### Post by krippa on 2011-09-02
Are you guys installing on 64-bit? I am using beta 1 64-bit and I installed skype from the web page. It seems install is fine even though it almost seems to install too fast. When i run it I get the following: 

skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

---

### Post by Script Warlock on 2011-09-02
> **krippa said:**
> Are you guys installing on 64-bit? I am using beta 1 64-bit and I installed skype from the web page. It seems install is fine even though it almost seems to install too fast. When i run it I get the following: 

skype: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

[this]("http://askubuntu.com/questions/59703/skype-error-while-loading-shared-libraries-libxss-so-1-cannot-open-shared-obje") might help you...

---

### Post by krippa on 2011-09-05
It did, after testing different ways I have now got the 32-bit working. It seems this is what you "should" install even though you are running 64-bit Ubuntu. Also seems it'll be added to the partner repos in a week or 2 which is good...

---

### Post by jepong on 2011-09-06
this multiarch thingie looks nice... i hate ia32-libs, its huge!

[Installing the Correct Skype package]("https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Beta1#Installing_the_correct_skype_package")

---

### Post by mayeulk on 2011-11-09
Hi,
Downloading the 32bits skype .deb from skype website, this works for me:

```
sudo dpkg --force-all  -i skype-ubuntu_2.2.0.35-1_i386.deb
sudo apt-get install libqt4-dbus libqt4-network libqtcore4 libqtgui4 libxss1. libxv1.
sudo apt-get -f install
sudo dpkg --force-all  -i skype-ubuntu_2.2.0.35-1_i386.deb
```

mayeulk

---

### Post by jhune_arao on 2011-11-09
nandoon pa rin ang skype sa repository.nag install nga ako ok nman.:popcorn:

---

### Post by antoniomiguel on 2011-11-10
Guys, this thread has been marked "solved" since June 7th.  Of course the problem raised before is not applicable anymore now, so refrain from commenting so as not to confuse others.

I wonder how to close a thread hmmn.

@mayeulk, you might want to look at [this]("http://bit.ly/uSWekT"). It's a nice refinement of Skype integration to Unity.

---

### Post by sumix on 2012-03-18
Hi, I've used Skype on a fresh Ubuntu 11.10 x64 installation for something like 3 months, but when I wanted to run it a few hours ago, it didn't start. When I run it in terminal, the error with missing "libXss.so.1" library occurred. It's quite strange, just because it worked fine before.

I googled for some solutions, but none of them worked for me. There's one left for me:
```
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386
sudo apt-get install libqtgui4:i386
```
Adding the i386 architecture was OK, but I didn't finish the attempt to install the required packages - just because apt-get wants to remove libc-bin package (and install libc-bin:386 and of course tons of other packages) and I'm not sure at all whether this is what I really want... What's your opinion on that? At this point, I think it's far better to have non-working skype than possibly the whole system... Thanks.

---

