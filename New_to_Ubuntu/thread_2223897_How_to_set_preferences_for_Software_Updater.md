---
title: "How to set preferences for Software Updater??"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by bobblex on 2014-05-13
I'm currently running Lubuntu 14.04, but also noticed this with Lubuntu 13.10, and I'm running the latest version of update-manager (1:0.196.12) .  

When I launch the Software Updater (or update-manager from the terminal), it immediately runs the program without asking for a password or withouth presenting any way to set the preferences or configuration options for the program.

How does one set preferences or options for the Software Updater/update-manager?  In earlier versions I used to get a gui that when launched asked for a password, then presented a nice application where one could configure the update-manager/Software Updater as well as search for and retrieve the updates, but that doesn't come up anymore.

Thanks

---

### Post by bapoumba on 2014-05-13
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)
Any user with admin privileges will have Software Updater run without asking for a password.

For prefs, do not you have a "Settings" tab leading you to the screenshot ?

---

### Post by pfeiffep on 2014-05-13
Due to the lack of consistency of software updater (or possibly my understanding) I've adopted using aptitude and don't concern my self with the gui
```
sudo aptitude update
sudo aptitude aptitude safe-upgrade
sudo aptitude autoclean

```

---

### Post by bapoumba on 2014-05-13
What do you call a lack of consistency ?

---

### Post by pfeiffep on 2014-05-13
@bapoumba
delta in results after software updater is run then immediately use aptitude. I possibly don't understand the delta results I see, so I choose and rely on aptitude

---

### Post by bapoumba on 2014-05-13
> **pfeiffep said:**
> @bapoumba
delta in results after software updater is run then immediately use aptitude. I possibly don't understand the delta results I see, so I choose and rely on aptitude

That is the phased updates : [http://www.murraytwins.com/blog/?p=127](http://www.murraytwins.com/blog/?p=127)

apt-get or aptitude do not check if bugs are filed against packages in the upgrade process.

---

### Post by pfeiffep on 2014-05-13
@[COLOR=#000000]bapoumba
I'm not clear why I should concern my self if there's a bug or not - if there's an update I should probably apply it
... perhaps you can elaborate?[/COLOR]

---

### Post by bapoumba on 2014-05-13
> **pfeiffep said:**
> @[COLOR=#000000]bapoumba
I'm not clear why I should concern my self if there's a bug or not - if there's an update I should probably apply it
... perhaps you can elaborate?[/COLOR]
Some updated packages may cause problems or bugs. The feature has been enabled to ensure new upgraded packages will not widely spread in that case. They are delivered to 10% of users and that number gradually increases to 100% if no bugs are reported over the next 2-3 days. If bugs are reported, the upgrade is not offered to additional users.

It is a matter of user preferences. Get any update as soon as it hits the repos (apt-get, synaptic, aptitude) or experience the phased updates with Software Updater.

---

### Post by bobblex on 2014-05-13
> **bapoumba said:**
> [https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)
Any user with admin privileges will have Software Updater run without asking for a password.

For prefs, do not you have a "Settings" tab leading you to the screenshot ?


No, I do not get any "Settings" tab when the Software Update (update-manager) runs.  It just comes up and starts checking for updates.  If there are updates, it waits for me to click on the install button.  If there are no updates, I get a dialog that says the computer is up to date.  No tabs or menu on any of the dialogs or boxes that open for the application.

Edited to add:

I just tried uninstalling the Software Updater application and then reinstalling it.  Things have changed after the reinstall.  
The program still comes up and starts checking for new updates, but if I click on the STOP button, I then get a Settings button that takes me to a window that lets me change/update/edit the sources (PPAs) and other settings.  Additionally, when the This Computer is Up to Date window comes up it also has a Settings button that takes me to the settings window.

---

### Post by bapoumba on 2014-05-14
OK, thanks for the update, and for marking your thread as solved :)

---

