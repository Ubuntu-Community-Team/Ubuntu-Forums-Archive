---
title: "Creating a symlink for firefox 27.1"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by panorain on 2014-03-05
Hi everyone, I have just downloaded and extracted firefox 27.1 to Lucid-Lynx 10.04.

Yes Yes I know it's time to upgrade BUT I have a question.

I created a .mozilla2 directory under /home/paul/ right next to the original firefox 20.0 directory named .mozilla ...... and moved the entire firefox 27.1 package into it.

How can I create a symlink or something so when I click my old firefox 20.0 launchers and menu items on the gnome2 desktop they now load up firefox 27.1?

Yes I know clicking on the firefox 27.1 .sh file if left unpackaged on desktop loads up version 27.1 but it's messy.

Thank you for your help.:p

---

### Post by ajgreeny on 2014-03-05
Right click on your gnome 2 desktop and choose "Create new launcher".  Point that to the executable called firefox in the extracted archive of firefox 27 and you're done.

If you don't like unity, which is why you have stuck with Lucid, have a look at Xubuntu or Lubuntu; there will be a new LTS version in about 6 weeks of all the *ubuntu family and it all looks great at the moment, though not ready if you can not repair any breakages that might appear as it gets near to release.

---

### Post by vanadium on 2014-03-05
A deep, system wide approach to launch your new executable could be to point usr/bin/firefox, which in reality is a symlink, to the new destination:

```

sudo mv /usr/bin/firefox /usr/bin/firefox20
ln -s <path/to/your/new/firefox.sh> /usr/bin/firefox

```

---

### Post by panorain on 2014-03-05
Thanks for your help so far. 

I ended up downloading the latest firefox28 from the firefox site extracted the .tar and copied it into /opt/firefox

Then I created a menu entry and pointed it to /opt/firefox/firefox.sh

firefox loads up with old bookmarks through the menu but

why when I do a  'locate firefox' many entries show up: 

/usr/share/ubuntu-docs/libs/img/firefox-3.5.png
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/info/firefox-branding.list
/var/lib/dpkg/info/firefox-branding.md5sums
/var/lib/dpkg/info/firefox-gnome-support.list
/var/lib/dpkg/info/firefox-gnome-support.md5sums
/var/lib/dpkg/info/firefox-locale-en.list
/var/lib/dpkg/info/firefox-locale-en.md5sums
/var/lib/dpkg/info/firefox-locale-en.preinst
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm

When I 'cd' into the /var/lib/dpkg/info and perform an 'ls -lah' no entries for firefox show up?

Also alt+F2 no longer allows me to open firefox Error stating file '/home/paul/firefox': No such file or directory

How can I get alt+F2 to open firefox or make it system wide?

I did run 'rm -r firefox' in /usr/bin after removing firefox20 via synaptic

---

### Post by panorain on 2014-03-06
.

---

### Post by panorain on 2014-03-24
Sorry to post again but I updated this post and I do not know how to delete the above post with only the .

---

### Post by panorain on 2014-03-28
What ended up more or less solving this dilema for me was the following.

**/etc/profile** -------->  systemwide initialization profile file.

Added the following line.

export PATH=$PATH:/opt/firefox

gnome-terminal window and going to Edit / Profiles - select the Default  profile and click the Edit button. On the Title and Command tab, click  the check box for Run command as a login shell. Your .bash_profile file  should be sourced the next time you open a gnome-terminal.

Was not necessary this time.

Now Alt+F2 -------->firefox works!
entering 'firefox' in the terminal also works.

I think it's kindof neat to be running Ubuntu 10.04 with the latest version of firefox installed.

The 'updatedb' command is obviously very important. 

Thanks for all your help.

---

