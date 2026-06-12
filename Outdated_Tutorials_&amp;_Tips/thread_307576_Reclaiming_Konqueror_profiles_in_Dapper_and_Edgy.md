---
title: "Reclaiming Konqueror profiles in Dapper and Edgy"
date: 2006-11-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Jucato on 2006-11-26
[Based on [http://www.kubuntu.org/faq.php#konqueror]](http://www.kubuntu.org/faq.php#konqueror])

Kubuntu has modified Konqueror to include features and settings that are commonly used, making the interface much simpler and easier to use. Some users, however, prefer to have all the bells and whistles. This guide shows how you can revert to the original Konqueror configuration and get back the original profiles on Dapper and Edgy.

1. Remove the Kubuntu default settings for Konqueror:

```
sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
```

or launch Konqueror as root with

```
kdesu konqueror
```

Note: If you wish to keep the Kubuntu default settings for future use or reference, move or rename the folder rather than deleting it.

2. Restore the original Konqueror configuration file:

```
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc
```

Note: The configuration used by Konqueror is konqueror.rc, while the original is konqueror-orig.rc. If you wish to keep the Kubuntu default configuration for future use or reference, rename konqueror.rc before entering the command above. (The ~/.kde/share/apps/konqueror/konqueror.rc overrides this file)

3. Restore the other profiles. This extra step is necessary in Dapper and Edgy, since these other profiles are not installed in these releases.

Go to [http://jucato.org/kde/konq-profiles/](http://jucato.org/kde/konq-profiles/) and download the four profiles there. Put these profiles in either:

~/.kde/share/apps/konqueror/profiles - if you want the profiles to be visible to your user only

/usr/share/apps/konqueror/profiles - if you want the profiles to be visible to the whole system (all users and root)

4. Restart/Close Konqueror. If the changes in the menu do not appear immediately, try logging out of KDE and loggin in again. Note that the konqueror.rc in ~/.kde/share/apps/konqueror/ overrides the one in /usr/share/apps/konqueror. You might need to delete the on in your home directory for the change to take effect.

---

### Post by Rashid584 on 2006-12-26
i learnt all that the hard way :p

hope someone else finds your post useful :up:

-Rashid

---

### Post by kleeton on 2007-05-01
Hi

Well well. I make for Feisty:

```
sudo mv /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror.bak
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc
```

The Kubuntu's setting's seems to be always here.

I have miss something ? :confused:

#edit
Sure, i miss the ~/.kde/share/apps/konqueror/konqueror.rc :guitar:

---

### Post by strabes on 2007-07-31
I thought I would clear this up since I had to mess with the file in my home directory to get it to work.

1. Remove the Kubuntu default settings for Konqueror:

```
sudo rm -r /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror
```

Note: If you wish to keep the Kubuntu default settings for future use or reference, move or rename the folder rather than deleting it.

2. ```
sudo mv /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror /usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror.bak
```

3. Restore the original Konqueror configuration file:

```
sudo cp /usr/share/apps/konqueror/konqueror-orig.rc /usr/share/apps/konqueror/konqueror.rc
```

Note: The configuration used by Konqueror is konqueror.rc, while the original is konqueror-orig.rc. If you wish to keep the Kubuntu default configuration for future use or reference, rename konqueror.rc before entering the command above. (The ~/.kde/share/apps/konqueror/konqueror.rc overrides this file)


4. Restart/Close Konqueror. If the changes in the menu do not appear immediately, try logging out of KDE and logging in again. **Note that the konqueror.rc in ~/.kde/share/apps/konqueror/ overrides the one in /usr/share/apps/konqueror. You might need to delete the one in your home directory for the change to take effect.**

---

### Post by johnmuir on 2008-03-18
This seems to be way out of date. I also want the full menus, but
 
[COLOR="Blue"]/usr/share/apps/konqueror/konqueror-orig.rc[/COLOR]

does not exist. In

[COLOR="Blue"]/usr/share/apps/konqueror/[/COLOR]

there are two files which look promising:

[COLOR="Blue"]konq-simplebrowser.rc[/COLOR] and [COLOR="Blue"]konqueror.rc[/COLOR]

konqueror.rc has the menu entries for saving the views per folder (see below), but they do not actually appear in the Konqueror Settings menu. Is that 'noMerge' option the problem? Or something else?

In [COLOR="Blue"]~/.kde/share/apps/konqueror/[/COLOR] there are no files starting with konqueror at all.

In [COLOR="Blue"]~/.kde/share/config[/COLOR] there is a file [COLOR="Blue"]konquerorrc[/COLOR], but it's some kind of property file and not XML.


I'm stuck - what's up?

KDE Version: 3.5.8
Kbuntu: 7.10 (up to date)

```
<Menu name="settings" noMerge="1"><text>&amp;Settings</text>
  <Action name="options_show_menubar"/>
  <Merge name="StandardToolBarMenuHandler" />
  <Separator/>
  <Action name="fullscreen"/>
  <Separator/>
  <Action name="saveViewPropertiesLocally"/>
```

---

