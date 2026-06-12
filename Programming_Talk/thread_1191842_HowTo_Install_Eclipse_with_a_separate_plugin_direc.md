---
title: "HowTo: Install Eclipse with a separate plugin directory"
date: 2009-06-19
forum: Programming Talk
---

### Post by elektronaut on 2009-06-19
[Edit on 2011/01/02: Updated path '/usr/local/' to '/opt/' and corrected some glitches.]

This is useful if you want to keep the plugin directory apart from the Eclipse installation directory. This allows you to have several installations of Eclipse using the same plugins, and also alleviates switching to a new version without going through the hassle of installing all the plugins again. 

I assume you already have installed Java.

This HowTo comes in four parts:

1. Installation of Eclipse
2. How to configure and use a central plugin directory
3. How to avoid remembering unnecessary command line stuff
4. How to share manually downloaded plugins

[SIZE="2"]**1. Installation of Eclipse**
[/SIZE]
As the Eclipse version in the repository is outdated, we install Eclipse manually. Download the version you prefer from the official website, untar it and move it to '/opt':
```
$ sudo mv eclipse-xy /opt/
```
Actually, I prefer to have a directory structure like 
```
/opt/eclipse-3.5-galileo
/opt/eclipse-3.6-helios
```
and so on for different versions, but that's up to you. For simplicity, everything below assumes you chose '/opt/eclipse-xy' (where 'eclipse-xy' stands for the actual version) as the program directory.

Assuming you didn't change the directory name like I did, we care for the permissions:
```
$ cd /opt
$ sudo chown -R root:users eclipse-xy
$ sudo chmod -R +r eclipse-xy
$ sudo chmod -R g+w eclipse-xy
$ sudo chmod +x `sudo find eclipse-xy -type d`
```

Once we are doing directory stuff, we also prepare the central plugin directory and in the 'real' eclipse installation directory another directory which will be used for the links to the central plugin directory:
```
$ sudo mkdir -p eclipse/extensions
$ sudo mkdir eclipse-xy/links
```

As we want to be able to write to these directories as a normal user, we have to do two things. First, change the group the directory is belonging to and also it's permissions:
```
$ sudo chgrp users eclipse-xy/links
$ sudo chmod 2775 eclipse-xy/links
$ sudo chgrp users eclipse/extensions
$ sudo chmod 2775 eclipse/extensions
```

You might not have seen a permission setting like *2775* yet. The "2" simply says that all files which will be put into that directory will have the same group like the directory - not the one of the user as normally.

Second thing to do is adding the user(s) who shall be able to install plugins to the group "users".
```
$ sudo vim /etc/group
```
Look for the line with group users. Afterwards, it should look like this:
```
users:x:100:my_user
```

Now we need an executable in the PATH:
Save this
```
#!/bin/sh
export ECLIPSE_HOME="/opt/eclipse-xy"
$ECLIPSE_HOME/eclipse $* 
```
as '/opt/eclipse/bin/eclipse-xy'
and make it executable:
```
$ sudo chmod +x /opt/eclipse/bin/eclipse-xy
```

If you have multiple Eclipse installations, you simply save different bash scripts like /opt/eclipse/bin/eclipse-1, /opt/eclipse/bin/eclipse-2, or whatever, with the different appropriate paths to the Eclipse executables.

Finally an (or multiple) application starter(s):
```
$ sudo vim /usr/share/applications/eclipse.desktop
```
with this content:
```
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse IDE
Exec=eclipse
Icon=/opt/eclipse/eclipse.svg
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true
```
As you can see, there is a path to an icon. As Eclipse doesn't seem to provide an icon anymore, I searched the net and simply downloaded the icon. Don't remember now where I got it from. As I have my different Eclipse installations in subdirectories, as described above, having the icon in the central super directory is convenient, so it can be used for all the different application starters.

Before I go on I have to give credits to Ivar Abrahamsen, who described most of the manual installation process on [**this site**](http://flurdy.com/docs/eclipse/install.html).

[SIZE="2"]**2. How to configure and use a central plugin directory**
[/SIZE]

This time I will give the credits first because I don't feel like repeating what Michael Scharf wrote [**in his blog**](http://michaelscharf.blogspot.com/2009/02/p2-how-i-install-plugins-in-extension.html). It boils down to starting Eclipse with a parameter each time you want to install a plugin. This requires some discipline, because you shouldn't install two plugins during the same run of Eclipse, as the concept is to use a separate directory for each plugin.
Michael only wrote about Windows. Here is an Eclipse call we would use for example:
```
$ eclipse -configuration  /opt/eclipse/extensions/testng/eclipse/configuration
```
This way, all plugins will be saved in subdirectories of '/opt/eclipse/extensions/'. The last call was for installing the TestNG plugin. The second thing that has to be done is adding a link to the installed plugin in the link directory of the Eclipse installation directory (or in all the link directories of the different Eclipse installations you might have):
```
$ echo "path=/opt/eclipse/extensions/testng" > /opt/eclipse-xy/links/testng.link
```
Now, after restarting Eclipse, the plugin can be used even though it's not in the Eclipse program directory.

[SIZE="2"]**3. How to avoid remembering unnecessary command line stuff**[/SIZE]

As I found it tedious to remember this cryptic command line stuff for installing new plugins, I devised a simple GUI solution. Save my script 'plgi-eclipse.sh' (plgi = plugin installation) somewhere in your PATH (I usually use ~/bin, so I don't forget to migrate my scripts when moving on to a new computer or Ubuntu installation):
```
#!/bin/bash
# plgi-eclipse.sh (for plugin-installation-eclipse)
# starts Eclipse for installation of a certain plugin into a central plugin directory
# see http://michaelscharf.blogspot.com/2009/02/p2-how-i-install-plugins-in-extension.html
# for more information about this way of handling plugins.
# uses zenity for Gnome, if you want to use it in KDE, you got to replace that with kdialog.

pluginName=$(zenity --entry --text "Please enter a name for the plugin you wish to install")
eclipse -configuration  /opt/eclipse/extensions/$pluginName/eclipse/configuration
# here you might want to change the path(s) to the "links" directories on your system.
echo "path=/opt/eclipse/extensions/$pluginName" > /opt/eclipse-xy/links/$pluginName.link 
touch /opt/eclipse/extensions/$szAnswer/eclipse/.eclipseextension
exit 0
```
If this script is called, it will ask you for a name for the plugin you want to install and will call Eclipse with the correct parameter as well as adding the link in the link directory.
Last thing needed is an application starter, so it's really GUI only. Save the following as '/usr/share/applications/eclipse-plugin-install.desktop':
```
[Desktop Entry]
Encoding=UTF-8
Name=Plugin Install For Eclipse
Comment=Start Eclipse for central plugin installation
Exec=plgi-eclipse.sh
Icon=/opt/eclipse/eclipse.svg
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true
```

That's it. Try it and tell me how it works for you. This is easily expandable. For example, you could come up with a dialog where the user can decide for which Eclipse installations links should be added. At the moment, I simply add the needed links directories directly in 'plgi-eclipse.sh', so there are multiple calls to 'echo':
```
echo "path=/opt/eclipse/extensions/$szAnswer" > /opt/eclipse-3.5-galileo/links/$szAnswer.link
echo "path=/opt/eclipse/extensions/$szAnswer" > /opt/eclipse-3.6-helios/links/$szAnswer.link
```

[SIZE="2"]**4. How to share manually downloaded plugins**[/SIZE]

All the above is for plugins which you download using Eclipse's update mechanism. But you might have already downloaded some plugins which you don't want to download again. There's also a solution for sharing those plugins (though I'm not sure if it's advisable - I think plugins which were downloaded manually outside of Eclipse won't benefit from the update mechanism. Take a look at [**this link**](http://www.ibm.com/developerworks/opensource/library/os-eclipse-equinox-p2/index.html#N1007A). All you have to do is adding this line to your eclipse.ini (and creating the directory 'dropins'):
```
-Dorg.Eclipse.equinox.p2.reconciler.dropins.directory=/opt/eclipse/dropins
```

Have fun :p

---

### Post by elektronaut on 2009-10-18
For those subscribed to this thread: I updated it, the procedure works if the permissions are set as described now.

---

### Post by siva.shanmukh on 2009-11-25
Awesome!

I installed the newest version of eclipse now. Can you kindly explain how to add PDT 2.2 to this installation. If it is already explained somewhere else, please post the link.

Thanks in advance.

---

### Post by elektronaut on 2011-01-02
Hi Siva,

sorry for not noticing your post for so long. I haven't been here in the ubuntu forums for a long time, my current employer forced me to use Windows...

Anyway, I haven't tested the PDT plugin yet, but it should just work as described.

---

### Post by crazy ivan on 2011-02-11
Hey, great idea!
Since every ubuntu update (10.4, 10.10) keeps destroying all the extensions and Galileo is out of date, I wanted to go the same direction.

There are two things of background-knowledge I do not understand about your solution:
1) how does eclipse know to look in the manually created directory "links"
2) how do you choose the names of the exension links/directories .. Does it matter?
3) the ubuntu eclipse stores all custom configurations in ./eclipse, which I had to erase some times when things get out of hand. Now the "p2" "configurations" "features" "plugins". If I empty those folders, will it still find the plugins??

I managed to install Texlipse manually, after from your script I found out that one has to add the ".eclipseextension" file to the "extension/$ext_name/eclipse" folder. Please add that info to the manual install section.

Anyways, thanks a lot.. And just as a comment: 
Since I work on many single user machines, the home folder of which I sync from time to time, I use "/home/$user/apps/eclipse (xy)" as my installation directory and it works great across different machines.

---

### Post by crazy ivan on 2011-02-11
Also the "$answer" variable in your script is unclear..

---

### Post by crazy ivan on 2011-02-11
Wow, I'm done installing the most important extensions using your script on Ubuntu 10.10, with eclipse 3.6.1:

* texlipse 1.4.1: [http://texlipse.sourceforge.net/](http://texlipse.sourceforge.net/)
* Pydev 1.6.5: [http://pydev.org/updates/](http://pydev.org/updates/)
* Subversive Team Provider 0.7.9: [http://download.eclipse.org/releases/helios](http://download.eclipse.org/releases/helios)
* SVN Connector 2.2.2: gets chosen by Subversive when you try to open a new SVN project (so before that you should also start the script and name the new extension "connector" or something of the like).

Not working properly until now is
* Photran: [http://download.eclipse.org/releases/helios](http://download.eclipse.org/releases/helios)

right click on projects will not work, CDT is missing, even though v7.0 was installed during photran installation.

---

