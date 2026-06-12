---
title: "Ubuntu &quot;Search for Files&quot; History"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Hastings101 on 2008-06-17
Is there a way to delete the list of recently used keywords in your searches that appear in  "Search for Files" under the places tab?  I've noticed my list has gotten fairly long, but I'm not sure how to delete it.  It's not a big deal or anything, it just sort of annoys me.

Ubunty Hardy 8.04

---

### Post by kansasnoob on 2008-06-17
I'm NOT absolutely sure of this but I do it when I'm bloated with "stuff":

```
sudo apt-get autoclean

```

But wait and double check this with someone less "noobish" before doing it.

---

### Post by Corrupt3d on 2008-06-17
Hey, this will work.

You have to edit [COLOR="Green"]~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml[/COLOR]

-[COLOR="Red"]Make a backup[/COLOR]
[quote=]
$ cp [COLOR="DarkOrange"]~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml [/COLOR] [COLOR="Blue"]~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.Bak1.xml[/COLOR][/quote]

Then
[quote=]$ gedit [COLOR="Green"]~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml[/COLOR][/quote]

You should see all the search entries listed between [COLOR="Red"]<li>[/COLOR] & [COLOR="Red"]</li>[/COLOR]
Edit the way you want it.
In my experience, deleting at least one entries, resets the search history back to its default. 

[COLOR="Red"]Relog[/COLOR] for changes to take effect.

---

### Post by iaculallad on 2008-06-17
A workaround on how to delete your "Search for Files" history: Open your terminal and issue the command below:

```
gksu gedit /home/ian/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml
```

A file with texts similar below will appear:

```
<?xml version="1.0"?>
<gconf>
        [COLOR="Blue"][B]<entry name="history-gsearchtool-file-entry" mtime="1212654242" type="list" ltype="string">
                <li type="string">
                        <stringvalue>*.txt</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>*.jpg</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>*.avi</stringvalue>
                </li>
        </entry>[/B][/COLOR]
</gconf>

```

Try to delete the blue-colored bold-letters part, start from **<entry name=** and ends in **</entry>**. Save the file and restart to see the result.

---

