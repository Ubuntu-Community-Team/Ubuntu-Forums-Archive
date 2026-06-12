---
title: "/etc/skel directory bug fix in Ubuntu 11.10"
date: 2012-01-15
forum: Programming Talk
---

### Post by AZorin on 2012-01-15
Hello everyone!
I have a bug which unfortunately, I could not find a cause for. 
In order to change the default user settings when creating a new account (UI settings mainly for things like the panel and wallpaper) I would usually override the default settings by pasting the preferred programs' configuration files into the /etc/skel directory. This directory contains files that are copied over to a newly created home account directory. The problem is that these settings don't work anymore in Ubuntu 11.10, even though all of them are successfully copied over to the new home directory. For example: I copied over a Nautilus desktop-metadata file to list the Computer, Home folder and Trash icons on the desktop but the icons don't show up. This happens for all the program settings that are copied over from the /etc/skel directory. I beleive that Gtk3 programs now use Gsettings instead of GConf (please correct me if I'm wrong) but most of the program settings that I want to copy over only store their settings in GConf (and the program settings do change when I edit the configuration files in the GConf folder on a working account). Unfortunately we don't know why this is happening so this is all the information about this bug that we can offer to you now.
We would recommend using a Guest account to see if your potential solution to this problem works.

We would be very grateful if anyone could help us to resolve this issue as soon as possible.

---

