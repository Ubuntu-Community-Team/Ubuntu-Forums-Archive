---
title: "New guy here, a few questions about software."
date: 2016-07-02
forum: New to Ubuntu
---

### Post by KageRyu on 2016-07-02
Hi so I'm a new Linux user Ubuntu 16.04

I have a few questions/problems.

1. in the ubuntu software center there are very few software that i can download (no comodo antivirus no skype no java)  . i dont really understand whether i have to add more repositories or sources. and how to add and which ones to add ... those are my questions for part 1.
[ATTACH=CONFIG]269929[/ATTACH][ATTACH=CONFIG]269930[/ATTACH][ATTACH=CONFIG]269927[/ATTACH][ATTACH=CONFIG]269928[/ATTACH]



2.example file is cav-linux_x64.deb  this file is comodo antivirus for linux when i try to install through installer i click the install button it goes grey for 10+ seconds and the i just resets so i can press install again and nothing happens . same thing happened with xdman.deb (xtreme download manager) . what is this and how to fix it?

3, i was trying to install xchat and downloaded  xchat-2.8.8-0.fc13.x86_64.rpm but cant figure out how to install it and lastly.

4.  i was downloaded Java runtime Environment from download.com link: ([http://download.cnet.com/Java-Runtime-Environment-JRE-for-Linux/3000-2213_4-75184641.html](http://download.cnet.com/Java-Runtime-Environment-JRE-for-Linux/3000-2213_4-75184641.html))
and it downloaded an archive file. when i extracted to desktop there is no setup .

so this post is asking for 4 different problems thank you for  your time.

---

### Post by howefield on 2016-07-02
Welcome,

> **KageRyu said:**
> in the ubuntu software center there are very few software that i can download (no comodo antivirus no skype no java)  . i dont really understand whether i have to add more repositories or sources. and how to add and which ones to add ... those are my questions for part 1.

Enable the Partners repository to get skype. Open the Software Centre and select Software Sources from the Edit menu, then check the Canonical Partners repository (you probably don't need the sources repository checked) - you may need to reload the software sources for it to take effect.

> example file is cav-linux_x64.deb  this file is comodo antivirus for linux when i try to install through installer i click the install button it goes grey for 10+ seconds and the i just resets so i can press install again and nothing happens . same thing happened with xdman.deb (xtreme download manager) . what is this and how to fix it?

Are you sure you need an anti virus application ? Try this page [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus) and if you still think you need one, then ClamAV anti virus is available from the Software Centre or if you want the run the the Comodo program then you could try to install via the command line, I only offer this as an option as it is likely to give you better information in the event of error than the Software Centre ever will. So, eg, if you have the Comodo deb file stored in your Downloads folder you could open the terminal and use..

```
sudo apt install ~/Downloads/cav-linux_x64.deb
```

Enter your password when prompted (you won't see it being typed) and press the enter key.

> i was trying to install xchat and downloaded  xchat-2.8.8-0.fc13.x86_64.rpm but cant figure out how to install it and lastly.

You want to use .deb files for Ubuntu, not .rpm files but with xchat already in the repository you should be able to install with the Software Centre or the command line..

```
sudo apt install xchat
```

> i was downloaded Java runtime ENvironment from download.com link: ([http://download.cnet.com/Java-Runtime-Environment-JRE-for-Linux/3000-2213_4-75184641.html](http://download.cnet.com/Java-Runtime-Environment-JRE-for-Linux/3000-2213_4-75184641.html)) and it downloaded an archive file. when i extracted to dekstop there is no setup .

Again java runtime can be installed with the Software Centre or command line. Try [this page ]("https://help.ubuntu.com/community/Java")for starters.

---

### Post by grahammechanical on 2016-07-02
Some information.

In Linux software comes in packages and that is because the code is packaged. There are different package formats. A file that ends in .rpm is in the RedHat Package Management format. A file the ends in .deb is in the Debian package format. Ubuntu is built on the Debian Linux distribution. So, packages in Ubuntu are debian or deb packages. So, that xchat.rpm file is not what you want. It cannot install on Ubuntu.

When I search Ubuntu Software for "xchat" it quickly comes up with XChat-Gnome. I have not tried installing it because I do not need that application. But it should install.

Not all software repositories are enabled by default. Go to System Settings>Software & Updates>Other Software and enable the Canonical Partners repository. But Skype is proprietary software and it will not be available through Ubuntu Software. I do not think it ever has been. This wiki page might help you.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

Is Comodo Antivirus packaged for Ubuntu 16.04? It does not seem to be. The web site lists Ubuntu 12.04 but not 16.04. That could be what is causing the problem for Ubuntu Software. One has to wonder, if the Comodo developers have not kept up with the releases of Ubuntu then how up to date are the virus scans?

[https://www.comodo.com/home/download/download.php?prod=antivirus-for-linux](https://www.comodo.com/home/download/download.php?prod=antivirus-for-linux)

Regards.

---

### Post by KageRyu on 2016-07-02
thank you guys first off instead of explaining i will show you which  options i already have turned on. 

            P\   Regarding  question 1 what is wrong here? am i missing anything?

[ATTACH=CONFIG]269931[/ATTACH][ATTACH=CONFIG]269932[/ATTACH][ATTACH=CONFIG]269933[/ATTACH][ATTACH=CONFIG]269934[/ATTACH]

2. ```
 $ sudo apt install ~/Desktop/cav-linux_x64.deb
[sudo] password for ryu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'cav-linux' instead of '/home/ryu/Desktop/cav-linux_x64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cav-linux : Depends: libssl0.9.8 (>= 0.9.8m-1) but it is not installable
E: Unable to correct problems, you have held broken packages.


```

3. found the xchat gnome version.

4. cannot find JRE or java runtime environment in the software center.

conclusion my software center has too few apps  i remember using ubuntu on another computer  a few months ago there were tooons of apps . now though i have a very limited selection and can barely find any apps still.

i'd like to restate i have barely any idea how repositories work or sources. which of these determine which apps you get . and which repos/or sources/ do you suggest i add so that i can have more software.

quick edit: i saw the JRE on the site you suggested which java should i instal JRE 6 or 7 ? im assuming 7?

---

### Post by claracc on 2016-07-03
Y recommend you to read: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) in order to know the different ways to install software in ubuntu.

---

### Post by KageRyu on 2016-07-03
@clarrac: ive read your link and i still dont have answers to my questions

can anyone answer my questions thank you very much.

---

### Post by vasa1 on 2016-07-03
Run
```
sudo apt-get update
```and post the entire output, including the command, here.

Do the same for```
sudo apt-get upgrade
``` I'm asking because of this:> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

---

### Post by Geoffrey_Arndt on 2016-07-03
After running the above, change your main mirror server also . . let the system find the fastest, select it, close out, and reload the repository.   Your download speeds will be much better.

---

### Post by mastablasta on 2016-07-05
since you want answers to the few quesitons you've made...

> **KageRyu said:**
> 
            P\   Regarding  question 1 what is wrong here? am i missing anything?


```
sudo apt-get install *packagename*
```

package name has to be correct. it could be that the package name is xchat-gnome or something.

there are other IRC clients available as well. search the software center for them


> 
i'd like to restate i have barely any idea how repositories work or sources. which of these determine which apps you get . and which repos/or sources/ do you suggest i add so that i can have more software.


you should learn how they work. repository is a warehouse where the apps are. for example on Android repository is called Google Play. there can be many repositories. some are form the OS (official ones) some are from partners and some are personal (PPA - Personal Package Archive). personal repositories can be added to software sources and then you Will be bale to Access the software that is in those repositories. 

i find the ***Playdeb ***PPA quite useful, but there are others as well. PPA can cause instability in the system. also in case of PPA you are trusting the person doing the packaging. with official repositories you trust Canonical that they are not letting any malware into software available there.

perhaps if you told us what software you are after we can help you find it and suggest the best way to install it.

you should remove all PPA's before doing system upgrade to avoid any complications. i believe the updater disables them now.

> 
quick edit: i saw the JRE on the site you suggested which java should i instal JRE 6 or 7 ? im assuming 7?

for OracleJava i use webupd8 PPA. for example: [SIZE=2][SIZE=2]http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html
[/SIZE][/SIZE]
however an opensourcejava is in the repositories.: [SIZE=2]https://help.ubuntu.com/community/Java
[/SIZE]
you are asking which Java you should install - my quesiton is - which one do you need? install the one you need.

---

### Post by oldfred on 2016-07-05
Generally only need Java if using some particular software that only works with Oracle's version.

One of the admin here suggested to me, not to use xchat but use hexchat.
Some use webchat
[http://webchat.freenode.net/?channels=ubuntuforums](http://webchat.freenode.net/?channels=ubuntuforums)

I do not use Software Center, and years ago started using synaptic. It also shows detail application name and more details on application. 
sudo apt-get install synaptic

---

