---
title: "Automatic visual changes to ubuntu desktop"
date: 2015-12-14
forum: New to Ubuntu
---

### Post by oskar10 on 2015-12-14
Hello,

I have some knowledge of using Ubuntu. I am a web developer and i have my own VPS running the LAMP stack so i know the basics of using the operative system.
I have never got that into using Ubuntu as my desktop operative system because it feels like i cannot control it. I have recently anyway decided that its time to use a Linux operative system on my desktop and i choose Ubuntu.

I installed Ubuntu yesterday and i already face something strange happening to me. The only applications i have been using is Nautilus, Nginx, MySQL and Mozilla. And after tabbing out from the browser my terminal just changed color from the standard purple color to black background and black text. Later today the whole desktop has changed the theme color and i now went into settings and changed the theme to "High Contrast".

While this is not something big i just feel like i want to know what causes such things to happen, I'm here to learn so would be happy if someone could bring some advice of how to prevent unwanted changes happening to the operative system.

Best Regards
Broken Programmer

---

### Post by Bucky Ball on 2015-12-14
Welcome. Which release are you using and what are the specs of your computer?

---

### Post by oskar10 on 2015-12-14
Hello,

Thanks for the welcome!

I am using Ubuntu 14.04.3 LTS.

As for specs this is in the System Settings-> Details
Memory: 5,8 GB
Processor: Inter Core i7-4510U CPU @ 2.00GHz x 4
Graphics: Intel® HD Graphics 4400 (In The settings details it says "Intel Haswell Mobile")

Best Regards
Broken Programmer

---

### Post by Bucky Ball on 2015-12-14
Let's make sure you are fully up to date. These commands will update/upgrade the software you have installed, NOT upgrade 14.04 LTS to a newer release. :)

Open a terminal and:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You will be asked for your password. It will be invisible when you type it. That is normal. 

Please report back any errors between [noparse]```

```[/noparse] tags (see last link in my signature).

(Normally you can use the Software Updater for this chore but the terminal gives us more detail of errors.)

---

### Post by oskar10 on 2015-12-14
Hello,

Yeah it just responds with my system is up to date.
This is the message dist-upgrade gave me, i translated my text into English,

```

Following packet has been installed automatically and is no longer required:
  adium-theme-ubuntu ubuntu-mono ubuntu-wallpapers
Use 'apt-get autoremove' to remove them.
 
```

To me its just intresting to know what kind of things that could be the cause of Ubuntu changing colors without me asking for it.

---

### Post by Bucky Ball on 2015-12-14
```
adium-theme-ubuntu ubuntu-mono ubuntu-wallpapers
```

Looks like there's been some tweakage with themes and wallpapers and something's been removed, but not completely. What were you doing prior to this? Only experimenting with the themes and wallpapers or desktop environment also?

Try this:

```
sudo apt-get autoremove adium-theme-ubuntu ubuntu-mono ubuntu-wallpapers
```

... then update again. You might want to reboot again after that and see if it behaves itself.

---

### Post by grahammechanical on 2015-12-14
Have you removed Empathy? I ask because apt-get is saying that adium-theme-ubuntu is no longer required. On my install of 16.04 (development version) it has both Empathy and adium-theme-ubuntu installed by default. And I am not getting the effects that you are getting. In fact I have never experienced anything like that in all the years I have been using Ubuntu desktop edition.

Also, I cannot understand why apt-get is saying ubuntu-wallpapers is no longer required. I am guessing that you are not using a default installation of Ubuntu. Is this a server OS with ubuntu-desktop installed on to it?

Regards.

---

### Post by Bucky Ball on 2015-12-14
@grahammechnical: That fills in some gaps. Thanks.

---

### Post by oskar10 on 2015-12-14
Hello,

Previously to this i had installed nginx and i did nothing which has anything to do with the themes. What first happend was that i was working and when i tabbed to the terminal it just had changed background to black. After changing the background color and continue working as usual i reboot the computer and then my Ubuntu theme is suddenly semi-transparent and i went into System Settings -> Appearance and changed the theme to "High Contrast". 

Only commands i have used in the terminal has to do with Nginx, as well as "grep" and "ps aux". I did nothing which has to do with appearance.

The install is a Ubuntu Desktop install, its not on a server its alongside with Windows on my home computer. I doubt this should be the reason for the themes to change.

I will try the commands you mentioned and reboot.

EDIT:
I rebooted and nothing much happen, the only theme available is still "High Contrast", but i guess its still selected because i switched to it after the UI started getting weird.
I'm mostly interested in why problems like this occur and how to prevent them in the future.

---

### Post by buzzingrobot on 2015-12-14
> **oskar10 said:**
> ...the only theme available is still "High Contrast"...

The dropdown menu in Systems Settings ->  Appearance does not list Ambiance and Radiance?

---

### Post by oskar10 on 2015-12-14
> **buzzingrobot said:**
> The dropdown menu in Systems Settings ->  Appearance does not list Ambiance and Radiance?

No the only theme available is "High Contrast".

---

### Post by buzzingrobot on 2015-12-14
OK.  Ambiance and Radiance are in the "light-themes" package.  Let's see if it's installed:

In a terminal, execute this:

> dpkq-query -s light-themes

If light-theme is installed, you should see several lines displayed, and the top two lines should read:

> Package: light-themes
Status: install ok installed


If it is not installed, you should see:

> dpkg-query: package 'light-themes' is not installed and no information is available

The light-themes package also has a few dependent packages:

1. gtk2-engines-murrine
2. gtk3-engines-unico
3. humanity-icon-theme
4. ubuntu-mono

If light-themes shows as installed, run the same "dpkg-query -s..." query with each of those packages.

Ideally, this is just a matter of a package somehow being uninstalled.  If one of them is, then, install it with "sudo apt-get install <package_name>. (Caveat:  If an install command produces a large list of packages that will be installed and uninstalled (especially uninstalled) cancel out and post all that here between quotes.)

---

### Post by CantankRus on 2015-12-14
@buzzingrobot... Just reading this.
You have a typo in your first command...written dpk**q** instead of dpk**g**

---

### Post by oskar10 on 2015-12-15
Hello, 

Running 
```
 
dpkq-query -s light-themes

```
Gave me the information that the package is not installed.

I also ran the command through all of theese and the only ones which was not installed was gtk2-engines-murrine and gtk3-engines-unico.
1. gtk2-engines-murrine
2. gtk3-engines-unico
3. humanity-icon-theme
4. ubuntu-mono

I went ahead and installed them both and after i did that i also installed light-themes and the terminal said nothing about packages that had to be deleted just installed.
After finished i now have the standard themes back in my Settings menu.

So i guess everything is back to working again. 
Still curious what is the two gtk packages i installed?
and what does the dpkg-query command do? Just check if packages is available?

Best Regards

---

### Post by buzzingrobot on 2015-12-15
> **oskar10 said:**
> 


I also ran the command through all of theese and the only ones which was not installed was gtk2-engines-murrine and gtk3-engines-unico.
1. gtk2-engines-murrine
2. gtk3-engines-unico
3. humanity-icon-theme
4. ubuntu-mono

I went ahead and installed them both and after i did that i also installed light-themes and the terminal said nothing about packages that had to be deleted just installed.
After finished i now have the standard themes back in my Settings menu.

So i guess everything is back to working again. 
Still curious what is the two gtk packages i installed?
and what does the dpkg-query command do? Just check if packages is available?

Best Regards

GTK2 and GTK3 are toolkits and components used to build and display GUI's and GUI apps. gtk2-engines-murrine and gtk3-engines-unico are packages many themes are dependent on, i.e., they contain code and components that those themes require to display and function correctly.

"dpkq-query" is a variant of the "dpkg" command, which is one piece of the package management system used by Ubuntu. "Package management" covers a lot of territory. But, basically, software offered and supported by Canonical is maintained on a collection of servers, aka repositories.  Each Ubuntu installation contains a list of the official repositories from which that user can locate and install software packages. Each system maintains a local database of the packages that have been installed. Packages eligible for updating are handled by comparing the packages already installed with packages in the repositories.

A variety of programs can be used to add, delete, and otherwise manipulate packages. The Software Center is one. apt-get is a command line package management tool.  dpkg is another.  It's important to know that all of these tools use the same list of repositories and get software from those same repositories.

Adding software that is not packaged for Ubuntu and does not come from a repository that your system knows about means that software will be invisible to the package management system, leaving the user responsible for updating it, resolving conflicts, etc.

See the "Add and Remove Software" section in your system's Help program.  More here: [URL="https://help.ubuntu.com/lts/serverguide/package-management.html"]https://help.ubuntu.com/lts/serverguide/package-management.html


[/URL]

---

### Post by oskar10 on 2015-12-16
Hello,

Thanks alot for the help.
It's great to get to learn more and at the same time fix problems that occur.

Best Regards

---

### Post by Bucky Ball on 2015-12-16
If it's all to your satisfaction, please see the first link in my signature. Enjoy. :)

---

