---
title: "Change launcher Icon size for standard users"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by venkinag on 2012-12-31
I have created a user in Ubuntu 12.10 using terminal.  Set a default password.

I want to change the launcher icon size to 32 for all my users.

Does anyone help me to do this?

Please note I have root privileges.  Others do not have root privilege and they are normal users.

Thanks.

---

### Post by iMac71 on 2012-12-31
the utility called "ubuntu tweak" doesn't require root privileges for changing the icons size of the launcher.
You can install that utility as follows:```
sudo apt-add-repository -y ppa:tualatrix/ppa
sudo apt-get update -y
sudo apt-get install -y ubuntu-tweak
```you can find the icon of ubuntu tweak into "System settings", but if you like to work with the terminal you can invoke the utility from it by typing```
ubuntu-tweak
```

---

### Post by venkinag on 2012-12-31
Thanks iMac71.  I want to set the launcher icon size to 32 as a default whenever I create a user instead of providing ubuntu-tweak to all users.  

Also, I want the icon size to change for the already existing users.

Is there a way to achieve this?

Thanks.

---

### Post by iMac71 on 2013-01-01
AFAIK the icon size value is stored in the %gconf.xml file which is placed in the /home/<user>/.gconf/apps/compiz-1/plugins/unityshell/screen0/options folder.
Therefore it seems that you have to set the icon size separately for each user and not globally for all users.

---

### Post by venkinag on 2013-01-02
I can only find folders upto /home/<user>/.gconf/apps

There is a zero byte file in the above path %gconf.xml

There is one more folder the in the above path called 'nm-applet'.  This has got another %gconf.xml file.  I have pasted the content of that file below.

<?xml version="1.0"?>
<gconf>
	<entry name="stamp" mtime="1356860352" type="int" value="3"/>
</gconf>

I have a few questions
1. If I modify one of these files will it meet my requirement?
2. Which file should I modify?  The one under apps or the one under nm-applet
3. What changes should I make to the file to make the launcher icon to 32? 

Thanks

---

### Post by iMac71 on 2013-01-02
open a Terminal window and paste in it this command:```
grep -a -E "(icon_size)" --include=*.xml -H -n -o -R .
```So you should be able to view all files containing the keyword "icon_size" and in what line of each file there's the keyword.

---

### Post by venkinag on 2013-01-04
Thanks a lot.  
*  I did a copy paste of the command (ignore some warnings it gave).  
*  Search displayed a file called unityshell.xml under the folder /usr/share/compiz
*  Modified all icon sizes as follows (used sudo gedit unityshell.xml after navigating to the folder mentioned above)
*  Searched for icon_size and then changed the below tags

 <option type="int" name="icon_size">
                    <short>Launcher icon size</short>
                    <long>The size of the launcher icons</long>
                    [COLOR="Red"]<default>32</default>
                    <min>32</min>
                    <max>32</max>[/COLOR]
                    <precision>1</precision>
                </option>

It worked!  :D

---

### Post by iMac71 on 2013-01-04
> **venkinag said:**
> Thanks a lot.  
*  I did a copy paste of the command (ignore some warnings it gave).  
*  Search displayed a file called unityshell.xml under the folder /usr/share/compiz
*  Modified all icon sizes as follows (used sudo gedit unityshell.xml after navigating to the folder mentioned above)
*  Searched for icon_size and then changed the below tags

 <option type="int" name="icon_size">
                    <short>Launcher icon size</short>
                    <long>The size of the launcher icons</long>
                    [COLOR=Red]<default>32</default>
                    <min>32</min>
                    <max>32</max>[/COLOR]
                    <precision>1</precision>
                </option>

It worked!  :Dtip: if you search, in the same file, the keyword "backlight_mode" and set to 1 the <min>, <max> and <default> values, you'll obtain a Quantal-like launcher.

---

