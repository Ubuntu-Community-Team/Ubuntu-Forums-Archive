---
title: "HOWTO: Update Firefox to 1.5.0.1 and change the logo to the real one at the same time"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Pu7o on 2006-02-12
To change the Firefox logo and upgrade Firefox to 1.5.0.1 at the same time, execute the following commands:

```

sudo su -
apt-get install libstdc++5
cd /usr/lib
rm -rf mozilla-firefox
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-GB/firefox-1.5.0.1.tar.gz
tar xzvf firefox-1.5.0.1.tar.gz 
rm firefox-1.5.0.1.tar.gz
mv firefox mozilla-firefox
exit

```

Don't forget to restart firefox as soon as this is done!

---

### Post by Freddd on 2006-02-15
Thanks a lot, this helped me :)

---

### Post by goombah88 on 2006-02-15
i just wanted to point out that this guide doesn't work if you installed firefox 1.5 using automatix.  it installs to /opt/firefox/ not /usr/lib/ so it doesn't use the mozilla-firefox folder.  if you could provide instructions for upgrading using automiatx's install i think that would really benefit a lot of people.

---

### Post by dvrs on 2006-02-15
If I run
'whereis firefox' iI get /usr/bin as opposed to /usr/lib. Presumably this is the directory I need to use instead of /usr/lib?

dvrs.

---

### Post by m.h.shams on 2006-02-15
dear friends,

can i download firefox tar.gz file on my pc, and then install it on ubuntu ?

i the answer is true, how can i uninstall previous release ?

thanks. all

---

### Post by afx on 2006-02-15
No, the files are still (should be) in /usr/lib. whereis command finds only the executable...

Another question, I installed firefox using automatix and moved all of the data from /opt/firefox to /usr/lib/mozilla-firefox... should the update work?

---

### Post by afx on 2006-02-15
[QUOTE=m.h.shams]dear friends,

can i download firefox tar.gz file on my pc, and then install it on ubuntu ?

i the answer is true, how can i uninstall previous release ?

thanks. all[/QUOTE]
how did you install your previous version? with automatix or adept?

---

### Post by m.h.shams on 2006-02-15
[QUOTE=afx]how did you install your previous version? with automatix or adept?[/QUOTE]


i just install ubuntu, today. and firefox 1.0.7 was installed with it.

---

### Post by goombah88 on 2006-02-15
[QUOTE=afx]No, the files are still (should be) in /usr/lib. whereis command finds only the executable...

Another question, I installed firefox using automatix and moved all of the data from /opt/firefox to /usr/lib/mozilla-firefox... should the update work?[/QUOTE]


afx, i did this earlier.  and to make a long story short it hosed firefox.  i just finished restoring my computer from a backup.  gotta love those backups.

that's why i posted earlier asking for help, cause i used automatix too.

---

### Post by Gandalf on 2006-02-15
Just commenting on one thing about this tutorial, in fact, When a user begin to use ubuntu and specially if he is already a linux user and knows all about su, the command "sudo su -" will remind him of that, and he may end up using su after setting a root password, so let's forget all about su, and use "sudo -s -H" instead, it is not hard to keep it in mind and at least, the user will stay happy and will never go back to su...

-IMHO :D

---

### Post by quonsar on 2006-02-15
i simply ran 

```
sudo mozilla-firefox
```

and let firefox upgrade to 1.5.0.1 using it's built-in updater. as soon as it is done, close the browser and run it normally.

---

### Post by mstlyevil on 2006-02-16
If you used Automatix to install FF then all you have to do is update to the newest version of Automatix and then use it to update FF. It currently offers 1.5.0.1.

---

### Post by tgbp492 on 2006-02-16
Just completed the upgrade and install and everything went great, BUT (ahhhh  the inevitable but) now my Java Plugin won't work.  I have the latest Java and made sure the symbolic link exists in the plugin directory but it won't work.  I even tried to download and reinstall directly from [www.sun.com/java](www.sun.com/java) and still no joy.  I can't reinstall over from the Synaptic repos due to it already being the latest install.  Do I need to remove and reinstall?  OR  am I just hosed?  Thanks for the guide, very painless and fast otherwise :)

Big Tim

---

### Post by nikolai on 2006-02-16
Heres what I did to update my autoxatix install

```
sudo su -
apt-get install libstdc++5
cd /opt
rm -rf firefox
wget http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.1/linux-i686/en-GB/firefox-1.5.0.1.tar.gz
tar xzvf firefox-1.5.0.1.tar.gz 
rm firefox-1.5.0.1.tar.gz
exit
```

---

### Post by Spano on 2006-02-20
I used Pu7o's guide to update from Firefox 1.07 and it worked well, leaving my Java install, prefrences and bookmarks intact.  I am having one problem though - when I click a weblink from mail inside Thunderbird, Firefox won't open to display the page.
   I opened Thunderbird from terminal, clicked on an email weblink and get this:
run-mozilla.sh: Cannot execute /usr/lib/mozilla-firefox/mozilla-firefox-bin.
Any ideas how to fix?

---

### Post by Spudgun on 2006-02-20
I just installed Firefox 1.5 using Automatix, can anyone tell me how to remove the old version of Firefox I had installed?

---

