---
title: "Ubunutu and Google Chrome"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by mr best buy on 2014-01-17
When ever I open Google Chrome, I get a message to enter the  key ring default  password.  I do not have any idea what that password is or how to change it.  This is a different notice that I get when I am making changes to software or updating.  
I click on cancel and it goes away.
How do I stop this or how do I find what the password is?
Latest version of Ubuntu

---

### Post by Frogs Hair on 2014-01-17
Chrome will display the option to login to Google Services when you install and open it.  Below the login box there is an option to ignore and if you select ignore the box shouldn't appear anymore. Unless you are launching Chrome as root from the terminal you shouldn't be getting a key-ring password prompt so you may want to add some information about how you installed.

---

### Post by mr best buy on 2014-01-17
I installed Chrome from the software package that you click on and it displays all the software for Ubunutu. The exact wording is:
Unlock Keyring
Enter  password for  keyring "default" to unlock
an application wants to access to the kiyring "Default" but it is  locked
Password........................
cancel  unlock



I did not use the terminal to install chrome.
I used the Ubunutu software center

---

### Post by Frogs Hair on 2014-01-17
Chromium or Chrome ?  Chrome is Google Chromium is not .

---

### Post by mr best buy on 2014-01-17
It says Google Chrome.

---

### Post by Frogs Hair on 2014-01-17
I haven't seen that before , I download from the Google site and use the software-center or gdebi to install. For some reason Chrome is wanting elevated permissions to open.    
I would delete the profile and reinstall . To get rid  of the old profile open the home folder press Ctrl + H to show hidden folders . Open .config and delete the google-chrome folder located there. If the problem is profile related that should solve it.

---

### Post by mr best buy on 2014-01-17
[ATTACH=CONFIG]249548[/ATTACH]

---

### Post by mr best buy on 2014-01-17
Thank you. it only happens when I use yahoo.com as my home page.  I need another home page.  any  suggestions?

---

### Post by vasa1 on 2014-01-17
> **mr best buy said:**
> When ever I open Google Chrome, I get a message to enter the  key ring default  password.  I do not have any idea what that password is or how to change it.  This is a different notice that I get when I am making changes to software or updating.  
I click on cancel and it goes away.
How do I stop this or how do I find what the password is?
Latest version of Ubuntu
I and others have seen this. If I find links to older threads I'll post here. For whatever Google Chrome has this issue whereas Firefox doesn't.
I seem to remember the solution is to enter your actual login password each time or to just press enter. On pressing enter, you'll be warned about how insecure you're going to be but after that this keyring stuff won't bother you.

---

### Post by vasa1 on 2014-01-17
Here are just some of the older threads in no particular order:
[http://ubuntuforums.org/showthread.php?t=1712871](http://ubuntuforums.org/showthread.php?t=1712871)
[http://ubuntuforums.org/showthread.php?t=1917430](http://ubuntuforums.org/showthread.php?t=1917430)
[http://ubuntuforums.org/showthread.php?t=1933904](http://ubuntuforums.org/showthread.php?t=1933904)
[http://ubuntuforums.org/showthread.php?t=2146659](http://ubuntuforums.org/showthread.php?t=2146659)

I searched google with "google chrome keyring site:ubuntuforums.org"

---

### Post by dannyboy79 on 2014-01-17
i get this as well, it's because most likely you stored your login info to yahoo so in order to keep your login safe, a keyring is used. it's not a big deal and you can expand the bottom and tell it to not use a keyring i believe

---

### Post by Frogs Hair on 2014-01-17
Sorry, I don't use a home page and haven't kept track of what search engines offer personalized login pages.

---

### Post by vasa1 on 2014-01-17
Also see [http://ubuntuforums.org/showthread.php?t=2200097&p=12903252#post12903252](http://ubuntuforums.org/showthread.php?t=2200097&p=12903252#post12903252)

---

