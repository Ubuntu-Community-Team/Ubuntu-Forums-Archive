---
title: "&quot;Double install of googleearth&quot; ? how to remove"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by hovzio on 2008-06-30
Hi, I want to thank in advance for even reading this bulk, please bare with me. I've got a few question concerning the googleearth update. (cause I kinda screwed things up.)I'm running ubuntu 7.10 and installed googleearth via apt from the medibunto repos. Google runs well and all is fine and then this popup: "hey! Its time for updates click here.." or something to the extent of that.(Not the update manager but from within the program.) I eventually decided to check it out and I end up downloading a .bin file from the google site. (I thought this was an update? Was it?) After a while I ran it in the terminal sudo ./GoogleEarthLinux.bin. An installer (gui) popped up and I proceded with ok. Yes my original googleearth was still installed, thought this was an update. Now assume it was'nt.(It was like 2 in the morning, long day)

Google does not really work after this. (lol) I have 2 google entries in my applications menu. Google does indeed look "newer" but is in no manner useable. Both links in apps menu call up the "newer" google. So I sudo apt-get purge googleearth googleearth-data knowing that this will not solve anything. Now only one entry in the apps menu. 

I asumme that I installed a complete new version of googleearth in full. (meaning not an update) How can I remove it? I'm finding all kinds of files:

/opt/google-earth/googleearth
/opt/google-earth/googleearth-mimetypes.xml
/opt/google-earth/googleearth-icon.png
/usr/share/applnk/Google-googleearth.desktop
/usr/share/gnome/apps/Google-googleearth.desktop
/usr/local/bin/googleearth 

There is a .googleearth/ in each users Home/ and quite a great many more files throughout.. I'm assuming its not good to just go in there and erase all the stuff that slocate kicks out. I'm not certain what took place so if anyone could confirm whether or not this was an update or an install I'd be grateful. Then, if I can't uninstall can I manually erase menu entries, config. files etc? I have also tried reinstalling GE with apt but no difference hence I removed it again. Appreciate any help, thanks :)

---

### Post by stoneybroke on 2008-06-30
You should be able to remove all files using synaptic package manager I know the new google earth-4.3 won't work on Ubuntu-8.04 you must use google earth-4.2 so it might be the same for Ubuntu-7.10

you can install google earth by sudo apt-get install googleearth-4.2 and it will work.

Hope that helps

---

### Post by hovzio on 2008-07-01
> **stoneybroke said:**
> You should be able to remove all files using synaptic package manager I know the new google earth-4.3 won't work on Ubuntu-8.04 you must use google earth-4.2 so it might be the same for Ubuntu-7.10

you can install google earth by sudo apt-get install googleearth-4.2 and it will work.

Hope that helps

hi, sorry to point this out but like I mentioned I've tried removing them with apt.(synaptic) I installed a .bin file which has little to do with the package manager, hence it cannot be removed with it! I had google 4.2 installed with apt (running well it was) and next to that I installed the new 4.3.bin file. After this neither worked. I have removed google with apt, how can I uninstall the .bin version. In /opt/googl* there is an unistall script (and the program itself). I ran it as root and it said there was no uninstall program. 

Is it safe to just remove all the googleearth files from the system, /opt/google and the rest.(mentioned above)
Thanks for any help.:)

---

### Post by mikewhatever on 2008-07-01
Safe in what sense? It wouldn't break the system, just GoogleEarth, getting its files deleted. Simply deleting the files is also offered as a solution in this guide [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by hovzio on 2008-07-16
> **mikewhatever said:**
> Safe in what sense? It wouldn't break the system, just GoogleEarth, getting its files deleted. Simply deleting the files is also offered as a solution in this guide [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

Yes, safe in the sense of damaging the system. Thanks I'm getting ready to install hardy (running gutsy) and I'll try rm'ing anything that find and slocate spite up. There are quite a few things I've been meaning to try :lolflag: So green light till I get hardy installed!!

---

### Post by Foster Grant on 2008-07-16
> **mikewhatever said:**
> Safe in what sense? It wouldn't break the system, just GoogleEarth, getting its files deleted. Simply deleting the files is also offered as a solution in this guide [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

The uninstall method on this page (listed below) works with no ramifications so long as you had installed Google Earth via the installation instructions on that page.

```
user@computer:~$ sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth

user@computer:~$ rm -rf ~/.googleearth
```

---

