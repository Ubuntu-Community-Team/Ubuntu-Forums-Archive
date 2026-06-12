---
title: "HOW TO: Replace firefox with swiftfox completely (more or less)"
date: 2010-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by chaosx9 on 2010-05-15
Hi everyone! (this guide is included in the help sheet i'll be posting up in the next month or so)

Now, if any of you don't know, there's a web browser made especially for linux called swiftfox, which runs very fast (look on reviews if you don't believe me, people have said it's faster than opera!)

First, you need to install swiftfox. Go to [this page]("http://getswiftfox.com/installer.htm") and get the script for your specific processor, and save it into your userspace.

Next, install it in a terminal using

```
sudo sh install-swiftfox.sh
```After all of that has happened, you'll have swiftfox working from your menu. Now, if you're happy with that, stop here. Although you might notice that some url's still open up in firefox (for example, help pages from programs). If you want swiftfox to do this, then follow these steps, quite carefully.

Open up a root terminal by pressing Alt+F2 and typing:

```
gksu gnome-terminal
```then press enter. This will save you having to type in "sudo bash" or "sudo command1" then "sudo command2" and so on.

then, navigate to the directory where the executable for firefox is located:

```
cd /usr/bin
```and open a root file browser:

```
nautilus ./
```It's gonna take a little bit of time to list everything, but when it does, look for the file named "firefox" and rename it to something like "firefox.backup" or "firefox.bak", just not "firefox.exe" or something with an actual extension. When you've done that, close the file browser, and then select the terminal and press Ctrl+C (just in case it doesn't detect nautilus is closed)

Now, the final step, create a symbolic link to swiftfox, to replace the "firefox" file:

```
ln -s /usr/bin/swiftfox /usr/bin/firefox
```and then, to test it out, type in the command:

```
firefox
```If it's worked, you should see swiftfox has opened instead of firefox, which is what will happen when any program (or launcher) runs something using the firefox command. Don't delete the original firefox executable, just in case you need to fall back on it.

---

### Post by lovinglinux on 2010-05-20
I would do this instead:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /usr/bin/swiftfox /usr/bin/firefox
```

To revert back to firefox:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

