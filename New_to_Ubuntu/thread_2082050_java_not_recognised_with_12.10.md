---
title: "java not recognised with 12.10"
date: 2012-11-08
forum: New to Ubuntu
---

### Post by jonattonyeah on 2012-11-08
Hello

I've just installed 12.10 (having used 10.04 for a while) but websites don't believe I've got java installed even though I most definitely have.

Can anyone help?

Thanks in advance!

---

### Post by cwsnyder on 2012-11-08
Website java is different from Java installed on your computer.  Website java is not the Java language, but instead is 'javascript', which is a distinct language of its own.  This is part of your browser which is not installed by installing a Java package, and can be blocked by particular security settings in the browser or browser add-ons like AdBlock.

For more help, you will have to indicate your browser (Firefox?) and any add-ons or extensions used.

---

### Post by jonattonyeah on 2012-11-08
Hello cwsnyder

It's a fresh install of 12.10 with the Firefox that came with it. There are no add-ons and it's straight out of the box as it were.

Ironically, two of the sites I'm having problems with are Firefox add-ons and Mycroft Project.

---

### Post by slickymaster on 2012-11-08
To be 100% sure Java Runtime Environment (JRE) is installed, why dont you check [this article]("http://ice.he.net/~hedden/jrelinux.html") which explains how to check whether JRE is installed, or not. Hope it will help you.

Besides that, chek what cwsnyder says. It could be something related to your browser configuration.

---

### Post by slickymaster on 2012-11-08
One thing you can do, if the problem is with browser is to enable Oracle's Java plugin. You'll do it running this script:

JAVA_HOME=/usr/lib/jvm/jdk1.7.0
MOZILLA_HOME=~/.mozilla
mkdir $MOZILLA_HOME/plugins
ln -s $JAVA_HOME/jre/lib/i386/libnpjp2.so $MOZILLA_HOME/plugins

Note that you have to change the value of JAVA_HOME so that it correctly points to your installation of the JDK.

If you don't know how to run the script, here’s how you do it:

[LIST=1]
[*]Using your editor, paste the contents of the script into a new file. 
[*]Find out where Oracle Java is installed. This location has the directories "bin", "lib", and "jre", among others. Replace the value of JAVA_HOME with the path to this folder, and save the file. This step applies if you're using the JDK. If you're only using the JRE, let JAVA_HOME point to the jre installation directory (which contains the folders "bin", "lib" and "plugin"), and modify the last line in the script to remove "jre" from the path.
[*]Make the script executable, by typing in chmod +x <filename>
[*]Run the script using the command ./<filename>
[*]Restart your browser, and confirm your installation as shown in the next section
[*]The above script will enable Java support in both Chrome/Chromium and Firefox, since they both use the ~/.mozilla/plugins directory to scan for available plugins.
[/LIST]

---

### Post by cwsnyder on 2012-11-08
For clarification, you are going to the Firefox add-ins website at [https://addons.mozilla.org/en-US/firefox/](https://addons.mozilla.org/en-US/firefox/) rather than the Firefox Add-ons Manager found by going to your Firefox menu and selecting Add-ons or Tools >> Add-ons.

By default, my Firefox installs, after I sync to get my passwords, etc., includes the NoScript/Web of Trust/BetterPrivacy/SpeedDial and DownloadHelper add-ons, so almost as soon as I invoke Firefox, my protections are in place, and I would not duplicate your condition.  Also, my Quantal installation, at this time, is a Virtual Machine under VirtualBox.

According to NoScript, the Firefox add-ins website has mozilla.net, addons.mozilla.org, and paypalobjects.com javascript components in the website, all of which could be blocked by Ubuntu Firefox modifications or Test Pilot, which are installed by default, or any other addon which you might have installed in a previous incarnation of Firefox when you did a sync.

---

### Post by slickymaster on 2012-11-08
Yet, another workaround to enable the Java browser plugin assuming that you have Java installed.

Insert the following commands at a root terminal:

[LIST=1]
[*]cd /usr/lib/mozilla/plugins (this will change you into the directory /usr/lib/mozilla/plugins, create this directory if you do not have it)
[*]mkdir -p /usr/lib/mozilla/plugins (this will create the directory /usr/lib/mozilla/plugins, make sure you are in this directory before you make the symbolic link)
[*]ln -s /usr/local/java/jre1.7.0_09/lib/i386/libnpjp2.so (this will create a symbolic link from the Java JRE plugin libnpjp2.so to your Mozilla Firefox web browser)
[/LIST]

Hopefully you'll be able to resolve your issue.

---

### Post by jonattonyeah on 2012-11-08
Hello All

I have just reinstalled 12.10 again. The first thing I did was to type in what slickymaster recommended but to no joy.

I have all the Java bits and bobs installed that come with 12.10 by default but still when I try to add a search engine from [http://mycroft.mozdev.org](http://mycroft.mozdev.org) I get told "JavaScript must be enabled to install a search plugin.
If you have installed NoScript, you will need to allow this page to run scripts."

I am currently running no add-ons whatsoever.

Thank you for all the help and advice.

This is driving me mad. I used 10.04 for years with no problems. Now I can't add a search engine. Maybe its just a mycroft thing. YouTube, for example, works fine.

---

### Post by jerome1232 on 2012-11-08
Java[B]Script
[/B]Java

Both are two very different languages.

Two things to check

Edit>Preferences (12.10 just tap alt and start typing preferences and hit enter when it's the first thing highlighted)

Goto the content tab and make sure Enable Javascript is checked.

------------------------------------------------------

Also take a look at about:plugins (click you address bar type "about:plugins" no quotes)

Make sure you see something in there for Java (which isn't javascript but this was just to see if you have something handling java) See the screenshot to see what mine looks like using the official Oracle java.

---

### Post by jonattonyeah on 2012-11-08
Hello

Thanks for all your help but nothing works. I've installed java, javascript is enabled but will it work? No.

Plus things keep freezing.

I'm loathe to say it but it might have to be a return to windows. :(

---

### Post by jonattonyeah on 2012-11-08
Perhaps it's not java or javascript per se.

Rather, it seems that I can't add search engines to Firefox whether I try via Mycroft Project (where It reckons javascript in not enabled when it is) or anything other than 'featured' search engines here: [https://addons.mozilla.org/en-US/firefox/search-tools/?sort=name&page=2](https://addons.mozilla.org/en-US/firefox/search-tools/?sort=name&page=2)

This is really annoying and is not a problem with Windows or 10.04, which I have just updated from.

Why is this happening and why can't I customise Firefox in 12.10?

Has anybody else encountered this?

Any ideas appreciated. 

Thanks.

---

### Post by slickymaster on 2012-11-08
You may have a damaged search.sqlite file. In which case that can be resolved. Try this:

[LIST=1]
[*]Locate your Profile Folder, by typing **about:support** in a new tab and press enter. Once there, click the ‘Open Containing Folder’ button
[*]Close Firefox
[*]From within your Profile Folder remove or rename the file **search.sqlite**
[*]Restart Firefox and attempt to add the new search engine again
[*]If you are still unable to add the search engine refer to this [mozillaZine KB article]("http://kb.mozillazine.org/Unable_to_search_or_add_new_engines") for additional troubleshooting steps.
[/LIST]

Just don't give up on Linux so easy!!!!

---

