---
title: "Issues with Flash in Chromium"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by boris6 on 2014-06-27
So here's the deal : I'm using Xubuntu and I know flash is built-in for Firefox, so i install Chromium (my browser of choice) which i assume has all the necessary plugins also built in(one of the things i like about it). So i come across i video that i need flash to see and it tells me i need to install a the plugin, i click on the link and it redirects me to [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash)

Step 1 works so i go to Step 4 as the guide says, i entered the command "**sudo update-pepperflashplugin-nonfree --install",**it asked me for my password, i entered it and nothing happened. It just started a new line, i entered the command again and nothing happens (it didn't even ask for my pass) - it just goes to a new line...


Flash works great in Firefox, but i can't seem to fix this. Help?

---

### Post by deadflowr on 2014-06-27
Get the installer first
```
sudo apt-get install pepperflashplugin-nonfree
```
Then run the command you tried before.

Also, firefox does not have flash built in.
It uses the flash installed on your system.
Google-Chrome has flash built in, that's the pepperflash plugin.
Chromium is the basis for chrome and needs the same pepperflash plugin.
It no longer works with the flash on the system.

---

### Post by Dennis N on 2014-06-27
To see if the installation succeeded, type in the address bar:

```
chrome://plugins
```

You should see:

```
Adobe Flash Player - Version: 13.0.0.206
Shockwave Flash 13.0 r0
```

> It just started a new line, i entered the command again and nothing happens (it didn't even ask for my pass)
Your sudo from the first try was still in effect. It is not necessary to re-enter it. Terminal commands don't usually give feedback that they succeeded, except results of the command. Often there is none, such as with rename or copy commands.

---

