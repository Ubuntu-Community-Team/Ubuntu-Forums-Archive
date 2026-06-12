---
title: "python dbus and gconf"
date: 2008-12-08
forum: Programming Talk
---

### Post by iggykoopa on 2008-12-08
I'm writing a power management gui in python, two of the settings I need to change for the nvidia stuff are in gconf. Since gconf changed its backend to dbus and the script is run as root you have to pass the dbus session environment variable for it to change. When I first wrote this (the code is below) it worked but in the last couple days it isn't anymore, can anyone tell me why?
```

sync_to_vblank, slide_duration = Config.get("nvidia", configSetting).split(",")
dbus = commands.getoutput('grep -v "^#" /home/%s/.dbus/session-bus/`cat /var/lib/dbus/machine-id`-0' % (Config.get("config","username"),)).split("\n")
os.system("sudo -u %s env %s gconftool-2 --type boolean --set /apps/compiz/general/screen0/options/sync_to_vblank %s" % (Config.get("config", "username"), dbus[0], sync_to_vblank))
os.system("sudo -u %s env %s gconftool-2 --type float --set /apps/compiz/plugins/wall/allscreens/options/slide_duration %s" % (Config.get("config", "username"), dbus[0], slide_duration))

```
I've also tried manually using the same commands so I don't think it's the python code that is wrong. The error I'm getting is:
```

Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

```
Did something change recently with gconf? I've also tried manually setting the values with gconftool-2 --direct --config-source and it changes the xml file but doesn't show correctly in gconf-editor.

---

