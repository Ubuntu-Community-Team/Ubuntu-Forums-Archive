---
title: "Terminal Location ???"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by Greg Mueller on 2011-10-25
When I start the terminal now it is at location....

greg@greg-desktop:~$ 

It never used to have that address.

What's up with that?

Do I need to change it?

How?

---

### Post by ViperChief on 2011-10-25
You're in your home directory. You're good. That address is 'your user name' at 'your computer name'

---

### Post by Greg Mueller on 2011-10-25
The reason I ask is that I am trying to install software (HP printer software) from the desktop where I have downloaded it to. The terminal says it can't open it.

---

### Post by WasMeHere on 2011-10-25
It is at your home directory which is the normal place to start.

**~** means **/home/greg** and **$** is the prompt.

Where do you want to start?

Have fun finding out about Ubuntu :-)
Olle

---

### Post by WasMeHere on 2011-10-25
Run the command ```
ls
``` and you will see if the desktop is called Desktop or something else depending on your locale. Then simply change directory to the desktop using its name
```
cd Desktop    # or
cd Skrivbord  # in Swedish or ...
```

---

### Post by nothingspecial on 2011-10-25
> **Greg Mueller said:**
> The reason I ask is that I am trying to install software (HP printer software) from the desktop where I have downloaded it to. The terminal says it can't open it.

Hi Greg,

You need to go to your Desktop

```
cd ~/Desktop
```

Then type ```
ls
``` to view the contents of your Desktop.

You should see it in there.

---

### Post by Greg Mueller on 2011-10-25
Well I'm trying to figure out why it can't open that file to install it, so I guess I thought I might have to be on the desktop where the file it.

The instructions say run

**sh hplip-3.10.9.run**

in the terminal. But when I do I get

**sh: Can't open hplip-3.10.9.run**

---

### Post by lisati on 2011-10-25
Did you save the file in the "Downloads" folder? If so, you might need to use this before running it:
```

cd ~/Downloads

```

---

### Post by Greg Mueller on 2011-10-25
It is not showing in the Downloads, but it is showing in the desktop

---

### Post by haqking on 2011-10-25
> **Greg Mueller said:**
> It is not showing in the Downloads, but it is showing in the desktop

so change to the desktop as suggested above

```
cd ~/Desktop
```

---

### Post by lisati on 2011-10-25
> **Greg Mueller said:**
> It is not showing in the Downloads, but it is showing in the desktop

What happens when you type in this from the terminal:?
```
cd ~/Desktop
```

---

### Post by nothingspecial on 2011-10-25
It has to be a capital D

Desktop

not

desktop

---

### Post by Greg Mueller on 2011-10-25
Progress!

That worked and the install started to run but I get the message

INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 6 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: python-devel (Python devel - Python development files)
warning: This installer cannot install 'python-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

---

### Post by decoherence on 2011-10-25
try running

sudo apt-get install python-dev

then try running the hp installer again

---

### Post by Greg Mueller on 2011-10-25
More progress. 

It installed them and I retried the HP install and this time it says......


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: This installer cannot install 'cups-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

---

### Post by haqking on 2011-10-25
> **Greg Mueller said:**
> More progress. 

It installed them and I retried the HP install and this time it says......


INSTALL MISSING REQUIRED DEPENDENCIES
-------------------------------------
warning: There are 5 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: cups-devel (CUPS devel- Common Unix Printing System development files)
warning: This installer cannot install 'cups-devel' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

same as before

```
sudo apt-get install cups-dev
```

and same for other messages if you get the drift ;-)

---

### Post by Greg Mueller on 2011-10-25
Thank god for experts...

Did that and got the message....
**E: Unable to locate package cups-dev**

---

### Post by haqking on 2011-10-25
> **Greg Mueller said:**
> Thank god for experts...

Did that and got the message....
**E: Unable to locate package cups-dev**

mmm actually that was wrong.

I found this on launchpad at [https://answers.launchpad.net/ubuntu/+source/cups/+question/156826](https://answers.launchpad.net/ubuntu/+source/cups/+question/156826)

```
sudo apt-get install -y libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
```

---

### Post by Greg Mueller on 2011-10-25
I went looking with google for that search string and found a topic where they used this string

sudo apt-get install -y libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

I did that and it chugged away for a while and then said it was done and I reran the HP install and it seems to have taken this time. 

Still fighting with it, but at least I have the HP install logo baloon on my tray

---

### Post by haqking on 2011-10-25
> **Greg Mueller said:**
> I went looking with google for that search string and found a topic where they used this string

sudo apt-get install -y libcups2 cups libcups2-dev cups-bsd cups-client libcupsimage2-dev libdbus-1-dev build-essential ghostscript openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit-1 policykit-1-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane

I did that and it chugged away for a while and then said it was done and I reran the HP install and it seems to have taken this time. 

Still fighting with it, but at least I have the HP install logo baloon on my tray

cool, that string you posted is the same command i posted, it essentially installed the dependencies required for you to do your install.

Good luck.

---

### Post by Greg Mueller on 2011-10-25
Wah-hoo!

It works again.
Now if it will just come back when I re-boot


Thanks everyone!

What an ordeal

---

### Post by haqking on 2011-10-25
> **Greg Mueller said:**
> Wah-hoo!

It works again.
Now if it will just come back when I re-boot


Thanks everyone!

What an ordeal

cool glad its working.

peace

---

### Post by philinux on 2011-10-25
> **Greg Mueller said:**
> Wah-hoo!

It works again.
Now if it will just come back when I re-boot


Thanks everyone!

What an ordeal
It would be interesting to know why you needed an older version of hplip rather than the later version that is installed by default in natty which is 3.11.1

---

### Post by Greg Mueller on 2011-10-25
You are right
The older version did not work and I had to use the latest version.

---

