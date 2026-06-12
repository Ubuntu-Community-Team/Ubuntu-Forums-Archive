---
title: "HOWTO: Open copy and open irc links into Xchat"
date: 2005-04-10
forum: Outdated Tutorials &amp; Tips
---

### Post by gflores on 2005-04-10
On some sites, like in ircspy, there are irc links that when you click on them, will copy the command and open it in the default irc client. 
irc://irc.something.com/foo  is a typical link and a typical command is   /ctcp foobot xdcc send #1

A few changes need to be done in Firefox in order for this function properly.
I assume you are using Firefox as your web browser and Xchat as your IRC client. 

**To make Firefox copy the irc links (like from ircspy)**
Open up Firefox.
Type  about:config  in Firefox location bar.
Then, in the filter box, type **signed.applets**
Double click the entry that appears so that it reverts to true.

**Make the links open up in Xchat**
Next, in the about:config window, right click on an area there, and select New -> String
In the preference name dialog that pops up, type in  **network.protocol-handler.app.irc**
Then for the string value, type in  **/usr/bin/xchat**

You don't have to restart Firefox. Now go to a site and click on an irc link and a dialog will appear saying if it's ok for the link to launch xchat. Just select ok.

Hope that helps.
El Fin.

---

### Post by Sionide on 2005-05-24
Useful, always found it handy that mIRC supported the irc:// protocol. Did you know if you make an irc:// link in a wiki it makes a little chat icon appear instead of a normal link. Same with mailto: links but it's a little email symbol. Quality

---

### Post by nomad311 on 2005-07-24
hmmm it works ...but not very well 

is it possible to have it open in the same xchat?

but useful all the same!

thnx
-nomad311

---

### Post by zeroverse on 2005-10-11
Very useful indeed.  Would also like it to open in a new tab in the same xchat if possible. Thanks

---

### Post by zandrame on 2007-05-31
Can this also be done with firefox/konversation? Setting "network.protocol-handler.external.irc = true" and "network.protocol-handler.app.irc = /usr/bin/konversation" does not work. 

If you know how to make it work, thanks!

---

### Post by Morientes on 2007-06-27
I cant get it to work. xchat launches, but it does not connect to the irc server. Any ideas what I am doing wrong?

---

### Post by roderic on 2007-06-29
I had the same problem, only solution that i saw was making a little script to open the irc chanell in an existing xchat, and pass that to firefox. Just make a file in /usr/bin called xchat-firefox and put in it:

```
#!/bin/bash
xchat --existing --url=$@
```

and chmod +x the file. Now in about:config put /usr/bin/xchat-firefox in network.protocol-handler.app.irc. I hope that helps.

---

### Post by Morientes on 2007-07-03
..and that worked perfectly! Thanks a lot!

Do have an idea of a script that would do something similar but in konversation instead?

By the way, it seems that if I connect to some networks using xchat, the networks ban me and say that "it seems you have a mirc virus" ? Does anyone know what that means?

---

### Post by Morientes on 2007-07-03
I have made a script that works partially with konversation. It works if konversation is not started. But if it is already running, it does not work. Does anyone know what could be changed to make it work also when it's running. The script can be seen below.
```

#!/bin/bash

#Storing the input string
input_string=$@

#Removing /channel-name
network_filter1=${input_string%/*}

#Removing irc://
network=${network_filter1#*//}

#Removing irc://network-name/
channel=${input_string#*//*/}

#Starting konversation with the network and channel name
konversation --server=$network --channel=#$channel

```

---

### Post by taisao on 2007-08-31
it's late, but here is a solution

use:

/usr/bin/konversationircprotocolhandler

instead of:

/usr/bin/konversation

---

### Post by iDelimar on 2007-11-22
I'm wondering what the solution is to the problem beneath because I'm having it too. Firefox launches Xchat but doesn't connect with the server.

> **Morientes said:**
> I cant get it to work. xchat launches, but it does not connect to the irc server. Any ideas what I am doing wrong?

Grtz M.

---

### Post by johnnylavah on 2008-02-23
> **iDelimar said:**
> I'm wondering what the solution is to the problem beneath because I'm having it too. Firefox launches Xchat but doesn't connect with the server.

Grtz M.

seems to work fine for me....still looking for a xdcc browser though...

---

### Post by sagara on 2008-03-09
> **iDelimar said:**
> I'm wondering what the solution is to the problem beneath because I'm having it too. Firefox launches Xchat but doesn't connect with the server.



Grtz M.

iDelimar, I had the same problem as you.  Based on the suggestion given on roderic's post ([#7]("http://ubuntuforums.org/showpost.php?p=2937198&postcount=7")) I did the following:

Create  a scripts directory in your home folder:
```
mkdir scripts
```
Create the script that will launch xchat
```
gedit irc.bash
```
Inside gedit paste the following code:
```
#!/bin/bash
# wrapper script for launching xchat from firefox (patch)


/usr/bin/[COLOR="Red"]xchat-gnome[/COLOR] --existing --url=$@
```
The command that I highlited in red might be different.  If it is not [COLOR="Red"]xchat-gnome[/COLOR] it will be [COLOR="Red"]xchat[/COLOR].
Give the script executable permissions
```
chmod u+x irc.bash
```
In firefox about:config page, I set the option **network.protocol-handler.app.irc** to **/home/[COLOR="Red"]YOUR_USERNAME[/COLOR]/scripts/irc.bash**

With this xchat opens and connects to the corresponding server/channel.  I'm a bit dissapointed that all this manual work is required to get this to work...

---

### Post by Miroku on 2008-06-13
thx sagara! i would thank you but there is no thank you button. makes gettin new anime that much easier. thx alot.

---

### Post by paniwani on 2009-05-25
I still can't get it to work. After clicking the packet number on packetnews.com the trigger is on my clipboard but xchat does not start...

---

### Post by Daeluin on 2009-06-13
I'm having the same problem - created the script and tested it with ./script irc://irc-url and it opens in an existing xchat intance as expected. awesome.

but firefox does nothing when I click on a irc url. I can set the prefs-apps irc handler to always ask, and then whenever I click it asks if I'd like to open with my script, and I say yes. So I imagine firefox is running the script, or trying to... is there something in jaunty that would prevent firefox from running the script? apparmor? I've looked around but who knows... script is executable and all that.

Edit: ok, ran firefox from the command line and when I clicked on the irc link it basically yelled at me that pidgin wasn't running.... so I was able to find that gnome wanted to do it's own thing with this link, and running gconf-editor and browsing to desktop/gnome/url-handlers irc let me change that. sheesh.

---

### Post by sagara on 2009-06-20
> **Daeluin said:**
> I'm having the same problem - created the script and tested it with ./script irc://irc-url and it opens in an existing xchat intance as expected. awesome.

but firefox does nothing when I click on a irc url. I can set the prefs-apps irc handler to always ask, and then whenever I click it asks if I'd like to open with my script, and I say yes. So I imagine firefox is running the script, or trying to... is there something in jaunty that would prevent firefox from running the script? apparmor? I've looked around but who knows... script is executable and all that.

Edit: ok, ran firefox from the command line and when I clicked on the irc link it basically yelled at me that pidgin wasn't running.... so I was able to find that gnome wanted to do it's own thing with this link, and running gconf-editor and browsing to desktop/gnome/url-handlers irc let me change that. sheesh.

hey Daeluin, I currently upgraded to Jaunty with a fresh install.  I will let you know how I do once I try to apply this script with firefox.

---

### Post by printfw on 2010-09-08
Bump this thread. Maybe someone knows how to open irc links into xchat from Google Chrome / Chromium?

**UPD**: I found out that chromium calls *xdg-open* for irc links. So the question is how to configure MIME type for irc links.

---

### Post by volkerbradley on 2010-11-19
> **printfw said:**
> Bump this thread. Maybe someone knows how to open irc links into xchat from Google Chrome / Chromium?

**UPD**: I found out that chromium calls *xdg-open* for irc links. So the question is how to configure MIME type for irc links.
Here is how I did this:
Wrote another mime type, by going to /home/username/.local/share/mime/packages and created an irc.xml file
Into this file I put:
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
<mime-type type="application/irc">
    <comment>irc url</comment>
    <magic priority="50">
      <match value="%irc://-" type="string" offset="0"/>
    </magic>
    <alias type="application/x-chat"/>
  </mime-type>
</mime-info>

Then I ran update-mime-database ~/.local/share/mime/ to update the database
then I added the following line:
Mime type=application/x-chat
to the /usr/share/app-install/desktop/xchat.desktop and /usr/share/applications/xchat.desktop files

Then:
mkdir ~/scripts
cd scripts
vi irc.bash
Put the following into this file:
#!/bin/bash
# wrapper script for launching xchat and the desired channel from Chrome
/usr/bin/xchat --existing --url=$@

Saved the file and then did chmod u+x irc.bash
Then, clicked on Applications -> System Tools -> Configuration Editor -> desktop -> gnome -> url-handlers -> irc
edited the "command" key and changed it to /home/username/scripts/irc.bash
Now clicking on the irc://... url in Chrome opens xchat with the desired channel

If someone knows how to get Chrome pass the command to glipper, I sure would appreciate it.

---

### Post by vinman_sv on 2011-01-28
This worked for me and I've tried everything on this post WORKING UBUNTU 10.10 (SOLVED)

read this post


[http://linux.byexamples.com/archives/318/how-to-trigger-xchat-from-firefox/#comment-100027](http://linux.byexamples.com/archives/318/how-to-trigger-xchat-from-firefox/#comment-100027)

---

### Post by volkerbradley on 2011-04-23
This works very well with Firefox.
Thanks for the tip.
Anyone figure how to do this with Google Chrome?

---

