---
title: "A solution that Worked for getting Frostwire to WORK in Edgy"
date: 2006-11-07
forum: Outdated Tutorials &amp; Tips
---

### Post by myke on 2006-11-07
I use the Kubuntu Edgy variant of Linux and have tried everything that was proposed here and in the gnutella forums to fix the nagging issue of my new installation of FW freezing at the "starting connection" point and detecting a firewall that wasn't there.   Here is what finally worked for me.

I started with this thread:  [http://www.frostwire.com/forum/viewtopic.php?t=666](http://www.frostwire.com/forum/viewtopic.php?t=666) that suggested dumping the hosts listed on the gnutella.net file with a new list as mentioned in the thread.  I tried that but it didn't work along with several other solutions (port forwarding, java selection, etc.).  However,  the following was suggested to me as a variant of the solution for replaces then sources in the gnutella.net file:

[quote="et voilà"]mykeCXV: then replace your gnutella.net with this one [http://mc3.electronicbox.net/gnutella.net](http://mc3.electronicbox.net/gnutella.net)[/quote]

I did this and IT WORKED.  FW is now running with an 'excellent connection' and on false detection of a non-existent firewall.  

On Linux -- go to your home folder and check "view hidden files" from the view drop down menu.   Open the .frostwire folder.  Then DELETE the gnutella.net~ file.  This one is a backup file that FW automatically creates.  It will put the deleted sources right back in on FW's restart and cause the same connection problem.  It did on mine anyway.   After deleting this file, open the gnutella.net file with a text editor.  Select all and cut or delete out the list.  Copy and paste the much much longer list of sources from the link above kindly provided by et voila.    Save the file.  FW will create a new backup file for just this list.  You should, of course, shut down FW prior to all of this and restart it afterward.  After pasting in this new and much longer list of sources, my FW started up quickly, connected quickly, and didn't detect a false firewall.  

I hope this helps another Linux user!

---

### Post by shof2k on 2006-11-09
Superb tip!  I installed frostwire on edgy and found the ~/.frostwire/gnutella.net file empty.  I replaced it with your one and it is working now.

Thanks for the tip.

---

### Post by Spano on 2006-11-09
Perfect.  Thanks for the tip.

---

### Post by disciple on 2006-11-09
worked for me as well, it would seem

---

### Post by JoeC21 on 2006-12-07
Can somebody post the list of sources that was found in this file? I am having the exact problem described but the link to the sources is down because bandwidth exceeded.

Thanks for any help,

Joe

---

