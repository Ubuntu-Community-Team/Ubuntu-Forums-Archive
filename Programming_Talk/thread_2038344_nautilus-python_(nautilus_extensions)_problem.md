---
title: "nautilus-python (nautilus extensions) problem"
date: 2012-08-06
forum: Programming Talk
---

### Post by hakermania on 2012-08-06
I am planning to include to Wallch a nautilus right-click function which will let you, for example, 'Start Wallch with this Folder', 'Start Wallch with this Album' etc.

The package python-nautilus has to be installed for this functionality to take place.

Then, I have to place a python script at ~/.local/share/nautilus-python/extensions/ and just restart nautilus.

This fits my needs perfectly, but, the thing is that if a user selects to unistall Wallch, then the python script will remain there and the user will have to remove it manually so as to stop having this (useless if Wallch is uninstalled) functionality.

So, I would prefer a system directory for the python script (the script will be installed automatically when Wallch is installed and this function will be enabled by default) and have the user give the password for once so as to enable/disable the function (add/remove the script from there).

I've read that a system directory where you could keep such scripts was /usr/lib/nautilus/extensions-2.0/python/ . But, inside /usr/lib/nautilus I have only extensions-3.0, and, if I create inside it the folder 'python' and place inside it my python script (and restart nautilus), it doesn't seem to work.


So, does anybody know where do I have to place this script? [The documentation]("http://projects.gnome.org/nautilus-python/documentation/html/nautilus-python-overview-example.html") talks only about ~/.local/share/nautilus-python/extensions but I've read multiple times about the /usr/lib/nautilus directory, without a success.

Any ideas? 

PS: remember that when a DEB is being installed the system tracks only the files that are placed under the system folders, not under the home directory of the user (like configuration files, etc), that's why I have a problem placing my python script into the home folder of the user.

Nautilus Extensions Documentation is available at: [https://live.gnome.org/Nautilus/Development/Extensions](https://live.gnome.org/Nautilus/Development/Extensions)

---

### Post by hakermania on 2012-08-07
bump

---

### Post by hakermania on 2012-08-11
desparate BUMP :D Anyone?

---

### Post by hakermania on 2012-08-11
And... The answer isssssssssssssssss

**/usr/share/nautilus-python/extensions**

---

