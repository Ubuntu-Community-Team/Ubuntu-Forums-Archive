---
title: "Downloading updates and software"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by Brewbum on 2008-09-02
So, I finally got this thing connected to the internet and was trying to download the updates and add some programs.  I went through the add/remove and update manager and let it be for a day almost, nothing happened.  I tried again in the evening, nothing.  

Is there a trick to downloading?  I have internet access and I am connected so can't figure out what else to do.

---

### Post by drs305 on 2008-09-02
If you aren't getting updates, you might want to check your settings and preferences via either Synaptic or System, Administration, Software Sources. Check the Updates tab and make sure you have checked the options you desire. Normally you should at least have the 'important security updates' selected. 'Recommended updates' would be a normal selection, while the 'proposed' and 'backports' are for those who wish to receive updates which have not been fully tested and released for general distribution.

If you believe you are having server issues, in Synaptic go to Settings, Repositories and click on Download From. Select 'Other' and choose another server to try. In Sofware Sources, same procedure but under the Ubuntu Software tab. You can let the system find a server for you by selecting the 'Select Best Server' tab.

---

### Post by Brewbum on 2008-09-02
I bet it is the server issue.  I will try that.  

I did read that when adding programs it is supposed to ask for my admin password and it never did so not sure what might be wrong there.  

I will test your suggestions at lunch.  Thanks.

---

### Post by abhishek.malhotra35 on 2008-09-02
Execute following command from terminal.
sudo apt-get update
This will install all the updates.
If you want to download and install any software type following command.
sudo apt-get install <software-name>

---

### Post by Brewbum on 2008-09-02
> **drs305 said:**
> If you aren't getting updates, you might want to check your settings and preferences via either Synaptic or System, Administration, Software Sources. Check the Updates tab and make sure you have checked the options you desire. Normally you should at least have the 'important security updates' selected. 'Recommended updates' would be a normal selection, while the 'proposed' and 'backports' are for those who wish to receive updates which have not been fully tested and released for general distribution.

If you believe you are having server issues, in Synaptic go to Settings, Repositories and click on Download From. Select 'Other' and choose another server to try. In Sofware Sources, same procedure but under the Ubuntu Software tab. You can let the system find a server for you by selecting the 'Select Best Server' tab.

So, I can't even get into Synaptic or software sources, it never comes up when I click on it.  It thinks for a bit and then nothing happens?  Thoughts?

---

### Post by philinux on 2008-09-02
In a terminal use this and post back any errors. Copy and paste the command.

sudo apt-get update && sudo apt-get upgrade

---

### Post by jrlii on 2008-09-02
Synaptic will not start?

You need to be logged in with a user ID which has administrative access in order to run Synaptic.

While it is a good idea to do most things while logged in as a non-administrative user, to do installs & upgrades you have to have admin permissions.

Before Synaptic will start, it will ask for your password (as administrator.) The update manager on the other hand will not ask for a password 'till you tell it to install updates.

---

### Post by philinux on 2008-09-02
Be aware that running System>Admin>update manager will nearly always tell you your system is up to date.

You have to click the check button at which point it will ask for your password.

---

### Post by Brewbum on 2008-09-02
The only error that came back was

sudo: unable to resolve host Garage

It looks like it updated everything but I still can't get into Sypatic or software manager.  I assumed I am logged in as admin.  how do I know?

---

### Post by philinux on 2008-09-02
Copy and paste this command and then paste the output back.

cat   /etc/hosts

---

### Post by Brewbum on 2008-09-02
I will have to do that after work, back to work and away from my linux pc at home.  

I went to the network settings and found that I had a host in there as Garage and deleted it.  I doubt that has anything to do with my inability to get into synaptic or software manager.

---

