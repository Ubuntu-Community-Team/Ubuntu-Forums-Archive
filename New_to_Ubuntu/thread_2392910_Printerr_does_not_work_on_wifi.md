---
title: "Printerr does not work on wifi"
date: 2018-05-27
forum: New to Ubuntu
---

### Post by plymouth532 on 2018-05-27
Hello,
I am running Ubuntu 17.10 on a HP Laptop. A couple months ago the laptop and printer would not work on wifi. I ran the hp check on the Ubuntu printer drivers. It came back with a lot of packages missing. I have downloaded hplip 3.18.5. My question is how do I remove the old hplip. 

Thanks for your help,
Ed

---

### Post by bijayalaxmi1808 on 2018-05-27
I think the below command will give you the hplip package details of installed package:
```
apt list --installed | grep hplip
```

If it is installed then you can remove that by the below command:
```
apt remove hplip (or the exact package name)
```

---

### Post by david1222 on 2018-05-30
Did you solve your problem?

---

### Post by plymouth532 on 2018-06-01
> **david1222 said:**
> Did you solve your problem?
I removed the file.I used the install script that is on the page, but comes back unstable and will not load.  I added sudo  and copied the file.

Thanks for your help, I have been under the weather, so a little slow.
 .

Ed

---

### Post by rsteinmetz70112 on 2018-06-01
How did you install HPLIP? 
What Printer model are you trying to install? I assume it is a HP printer with WIFI. If not please provide additional information.

You should also be using one of the automated install packages like **apt** from the command line or if you want a graphic interface **Synaptic** or the **Ubuntu Software Center.**

If the system is unstable I'd try to fix that before going any further. Open terminal and run:
```
sudo  dpkg --configure -a 
sudo apt install -f 
```
This will check to see if all of your packages and their dependencies are installed and configured. If you get any error messages try to resole them before proceeding. IF yous system is clean the dpkg command will run with no messages at all.

Next I would run an update to make sure everything is up to date
```
sudo apt update
sudo apt upgrade
```
Or you can use the **Update Manager** or **Synaptic **

Then I would try reinstalling HPLIP and the HPLIP GUI

```
sudo apt install --reinstall hplip hplip-gui
```

After that you should run 
```
sudo apt autoremove  
sudo apt autoclean  
```
to find and remove any obsolete/unused packages? or you could use **Synaptic**

You should then be able to open the System Settings and add the printer. HP network printers a usually discovered automatically and the drivers identified.

I hope this helps.

---

