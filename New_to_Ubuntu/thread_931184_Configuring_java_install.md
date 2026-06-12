---
title: "Configuring java install"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2008-09-27
>  Firefox

   1. Go to the plugins sub-directory under the Firefox installation directory
      cd <Firefox installation directory>/plugins

   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Firefox is installed at this directory:
            /usr/lib/firefox-1.4/
          * And if the JRE is installed at this directory:
            /usr/java/jre1.6.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/firefox-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.6.0/plugin/i386/ns7
            /libjavaplugin_oji.so

      In the command line above, use ns7-gcc29 if Firefox was compiled with gcc2.9.

      If you install Firefox 1.5 or later, you can enable the Java Console menu item in the Tools menu. Change directories to the Firefox extensions directory, then unzip ffjcext.zip there.

      cd /usr/lib/firefox-1.4/extensions
      unzip /usr/java/jre1.6.0/lib/deploy/ffjcext.zip

   3. Start the Firefox browser, or restart it if it is already up.

      In Firefox, type about:plugins in the Location bar to confirm that the Java Plugin is loaded. If the version is Firefox 1.5 or later, click the Tools menu to confirm that Java Console is there


I'm stuck at step two.

My Termial reads
> 
Root@Autumn:/home/autumn/Desktop/firefox/plugins#

---

### Post by adult swim on 2008-09-27
edit: woops i misread
do you know where you installed JRE at?
edit again: are you just trying to install java?

---

### Post by AutumnPhoenix on 2008-09-27
i did the first part of the install.  the jre is sitting on my desktop

---

### Post by AutumnPhoenix on 2008-09-27
[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

I followed these instructions

---

### Post by adult swim on 2008-09-27
post the results of ```
which jre1.6.0
```
if that doesnt return anything try ```
which jre-1.6.0
```

---

### Post by adult swim on 2008-09-27
if you are just trying to install java, it seems like you are going about it the hard way.  have you tried going to a terminal and entering ```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
``` and then restarting firefox?

---

### Post by nowshining on 2008-09-27
okay did u creata a java folder or folder u wanted to install into?

if not - mkdir ~/nameoffolder u want

cd into it

run the java install bin,

then

cd into ~/.mozilla/plugins/

or

open up nautilus and at the top type that location or if need be change `/ to /home/username


and create a synbolic/shortcut link to libjavaplugin.so in the java folder u created:

example java folder u created - i suggest a folder in the home directory that is hidden with a dot..

anyway... the example java folder is .java - and u cd into the mozilla plugins folder already so...

ln -s <~/.java/plugin/i386/ns7/libjavaplugin_oji.so


---- note the above was for a non-system wide install meaing u will need to ls -a to each user account - if this is only one person using the computer this should work fine, and after the above - restart firefox..

---

### Post by AutumnPhoenix on 2008-09-27
I am trying to update java.  the folder is on my desktop

the which comand did nothing, however,I'm installing update 7 does that make a difference?

---

### Post by AutumnPhoenix on 2008-09-27
I have an old update that I think is stopping my update

---

