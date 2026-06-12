---
title: "Software Center Hanging"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by mindtravel3r on 2012-06-24
Hi Folks, 

I am running ubuntu 12.04 and am having a problem with my Software Center Hanging.  I was attempting to install Dropbox, and the Software Center Hung up while installing.  Now upon reboot, the software Center is hanging with the item "Searching Applying Changes."  When I attempt to cancel it just hangs on "Canceling."  I found this thread:

[http://ubuntuforums.org/showthread.php?t=1578949&highlight=Software+Center+Hanging](http://ubuntuforums.org/showthread.php?t=1578949&highlight=Software+Center+Hanging)

which seems to be similar to my situation and have been attempting to run the command:

  	 	 	 	 	 	   sudo apt-get update && sudo apt-get safe-upgrade
  
which I got from the above thread.  When I run this, I am receiving the following error:

  	 	 	 	 	 	   E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock directory /var/lib/apt/lists/ 
 E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable) 
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
  
Am I taking the correct course of action using the above command?  If yes, how do I go about unlocking the process so it can run to completion.  

Any help you can provide is greatly appreciated.

Have a great day, 

David

---

### Post by nipunshakya on 2012-06-24
Hello... Please run the following commands in your terminal
```
sudo apt-get install -f
```
if that doesnt work out, try the following
```
sudo apt-get purge nautilus-dropbox
```
after that type```
sudo apt-get autoremove
```
and then follow the following link:
[http://www.liberiangeek.net/2012/04/install-dropbox-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/install-dropbox-in-ubuntu-12-04-precise-pangolin/)

However, there is a bug about dropbox hanging the software center here:
[http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99](http://askubuntu.com/questions/154671/dropbox-fails-to-install-stuck-at-99)

 So be careful to choose dropbox for installation

---

### Post by mindtravel3r on 2012-06-24
I am still getting the locked resource errors:

root@velocitymicro:/home/david# sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@velocitymicro:/home/david# sudo apt-get purge nautilus-dropbox
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@velocitymicro:/home/david# sudo apt-get autoremoveE: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@velocitymicro:/home/david#

---

### Post by nipunshakya on 2012-06-24
somebody just got tired of dropbox errors and reinstalled whole OS himself... see the following:
[http://ubuntuforums.org/showthread.php?t=2008815](http://ubuntuforums.org/showthread.php?t=2008815)
You can try the codes suggested there too..

---

### Post by jmfal on 2012-06-24
If that link didn't help try this one

[http://askubuntu.com/questions/154671/dropbox-install-stuck-at-99-how-do-i-fix-it](http://askubuntu.com/questions/154671/dropbox-install-stuck-at-99-how-do-i-fix-it)

---

### Post by slayer^_^ on 2012-06-24
I confirm, the method works:

```
gksu gedit /var/lib/dpkg/updates/0003
```

then delete all the lines with #padding

then again

```
sudo dpkg --configure -a
```

then to clean-up

```
sudo apt-get update
```

---

### Post by mindtravel3r on 2012-06-24
Thank you for the links to the various sites and the code, looking at a combination of these sites lead me to a solution.  

I was able to finally clear Dropbox from my Software Center.  It appears that processes associated with the Software Center were loading when the GUI was loading.  This was resulting in the errors I posted above not allowing me access to /var/lib/dpkg/.  

So, what I did was login without loading the GUI (Ctrl-Alt-F1 at the initial login window) -- I am not sure what you call it when you log in with the text interface. 

From there I ran:

sudo dpkg -r nautilus -dropbox

and this removed Dropbox without running into the resource conflict.  

Thank you all for your help and support on this.  I could not have resolved this without your assistance.

---

### Post by nipunshakya on 2012-06-24
Please mark this thread as [SOLVED] from the top right 'Thread Tools' so others can find solution similar to your problems too. There are many people having trouble with software center too....

---

