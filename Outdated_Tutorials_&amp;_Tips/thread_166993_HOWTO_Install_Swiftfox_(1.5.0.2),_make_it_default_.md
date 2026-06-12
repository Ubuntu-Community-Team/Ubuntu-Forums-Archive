---
title: "HOWTO: Install Swiftfox (1.5.0.2), make it default browser &amp; work with thunderbird"
date: 2006-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jms830 on 2006-04-27
**This HOWTO is based on information from pgmario's howto at **[http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798) 
Thanks to him for bringing swiftfox to my attention.
-------------------------------------------------------------------

I think the best way to make swiftfox your **default browser** AND permanently allow **thunderbird to open links** in it is as follows:

If you have any Firefox windows open, close them.

**1.** Download swiftfox 1.5.0.2 from [http://getswiftfox.com/](http://getswiftfox.com/)


**2.** Extract the swiftfox .tar.bz2 to the location of your choice. For the purposes of this HOWTO I will use 
**/home/[username]/swiftfox **
[COLOR="Green"](replace [username] with your own)[/COLOR]


**3. **open a terminal and type the following lines
```
cp /home/[username]/swiftfox/swiftfox-bin /home/[username]/swiftfox/firefox-bin
cd /usr/bin
sudo mv firefox firefox_backup
sudo ln -s /home/[username]/swiftfox/swiftfox /usr/bin/firefox
```

**4. **Go to System> Preferences> Preferred Applications
and select Firefox, or if it is not an option click Custom and enter the command 
```
firefox %s
```


**_[SIZE="3"]To make Thunderbird use swiftfox permanently:[/SIZE]_**


**5.** Open nautilus and navigate to **/home/[username]/.mozilla-thunderbird/[profilename] **
[COLOR="Green"]([profilename] will be something like odzd2tlp.default or something unless you have otherwise specified)[/COLOR]

**6. **Find or create the file called **user.js** and open it with a text editor (ex: gedit) by right clicking

**7. **add the following lines and save
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox"); 
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
```


from pgmario's howto:

**8.** To enable all plugins (flash, etc.) from your original Firefox installation do (make sure to enter that trailing dot):
```

cd /home/[username]/swiftfox/plugins/
sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
```

[COLOR="Blue"]And you're done, enjoy![/COLOR]



[B]
Attention: [/B]If you use one of the branch or trunk builds instead of that of the recent release (1.5.0.1), some of your extensions might not work.
To re-enable them after you have switched back to 1.5.0.1 go to Tools>Extensions, right-click on the disabled extensions and select "enable".
You could also create **a new profile for testing purposes:** In a terminal, change to the Swiftfox folder and launch the profile manager with the following command (make sure to enter that dot in front of the slash):

```
 ./firefox -ProfileManager

```

You can test speed at [http://scragz.com/tech/mozilla/test-rendering-time](http://scragz.com/tech/mozilla/test-rendering-time)
Also recommended: the fasterfox extension, at [http://fasterfox.mozdev.org/](http://fasterfox.mozdev.org/)

**_Notes:_**
Swiftfox may continue to ask you to be default browser, you can ignore it as it is now.


_**If you ever want to undo this HOWTO type in terminal:**_

cd /usr/bin
sudo rm firefox
sudo mv firefox_backup firefox

and remove the two lines from user.js

---

### Post by no1wantdthisname on 2006-04-28
Small note:  Instead of manually moving the original firefox out of the way you can just do
```

sudo dpkg-divert --divert /usr/bin/firefox.old --rename /usr/bin/firefox

```
Normally when you upgrade firefox, the /usr/bin/firefox gets replaced.  Using dpkg-divert leaves it unaffected since it'll only change the diverted /usr/bin/firefox.old.  Otherwise you have to move /usr/bin/firefox everytime there's an update for firefox.

To undo you'll just need to do:
```

sudo dpkg-divert --remove /usr/bin/firefox

```

Also, I'm using swiftfox right now, and when I tried using regular firefox it kept crashing.  I created a new profile and it seems to work fine.  Swiftfox seems to do something with the user profile that is not compatible with regular firefox.  So, you should probably backup your firefox profile if you ever decide to switch back.

---

### Post by Ensnared on 2006-04-28
Thunderbird uses x-www-browser to figure out which browser you use. So all you have to do to change it is```
sudo update-alternatives --config x-www-browser
```...and enter the number that represents /usr/bin/firefox.

Also, adding a symlink named firefox pointing to swiftfox in the swiftfox-directory seems to solve the browser always asking if it should be default.

Additionally, I believe the swiftfox executable (which is a script) ends up executing "./$0-bin", which means it will try to execute firefox-bin if it was launched with the /usr/bin/firefox symlink. If that happens, just make a symlink in the swiftfox-dir named "firefox-bin" and point it to "swiftfox-bin" in the same directory.

---

### Post by jms830 on 2006-05-01
Oops! I forgot one very important step
```
cp /home/[username]/swiftfox/swiftfox-bin /home/[username]/swiftfox/firefox-bin
```
I added this to the guide now. Sorry for any confusion, it should all work now.

---

### Post by migraineboy on 2006-05-01
Ok. It worked here but now it's in english (it was portuguese BR before) and flash isn't working anymore. I can stay with it in english but I would like to have flash working again. Can you help me?

---

