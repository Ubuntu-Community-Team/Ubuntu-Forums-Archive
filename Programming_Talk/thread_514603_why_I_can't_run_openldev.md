---
title: "why: I can't run openldev"
date: 2007-07-31
forum: Programming Talk
---

### Post by HansGong on 2007-07-31
when the openldev startup pic appeared ,it crashed.

I don't know how to solve it.

I just type the "apt-get install " command to install it.

---

### Post by moma on 2007-08-01
I think there is a tiny bug or omission in the openldev-settings/openldev-project.cc **file**.
See this thread:
[http://ubuntuforums.org/showthread.php?p=2900005#post2900005](http://ubuntuforums.org/showthread.php?p=2900005#post2900005)

The error is described in this [http://i1.no/04k5/](http://i1.no/04k5/) bug-report.

Do this:
[COLOR="Purple"]-2) [/COLOR]Uninstall Ubuntu's version of OpenLDev
$ [COLOR="Green"]sudo aptitude remove openldev[/COLOR]

[COLOR="DarkOrchid"]-1)[/COLOR] Install some necessities (it may require other packages too)
$ [COLOR="Green"]sudo apt-get install libgtksourceview-dev libvte-dev libgnomeprintui2.2-dev libgtk2.0-dev[/COLOR]

[COLOR="DarkOrchid"]0)[/COLOR] Download the OpenLDEv source ( openldev-1.0.tar.gz ) from 
[http://www.openldev.org/download.php](http://www.openldev.org/download.php)

[COLOR="DarkOrchid"]1)[/COLOR] Open the openldev-project.cc file (in the openldev-settings directory)
$ [COLOR="Green"]gedit openldev/openldev-settings/openldev-project.cc[/COLOR]

[COLOR="DarkOrchid"]2)[/COLOR] and fix the openldev_project_settings_new(...) function by adding the following 2 lines to the code. 

// Nullify the structure
memset(settings, '\0', sizeof(ProjectSettings));

The function should look like this after changes.

```
// Open the project located at the specified file name
ProjectSettings *openldev_project_settings_new (gchar *filename)
{
ProjectSettings* settings = g_slice_new (ProjectSettings);

// Nullify the structure
memset(settings, '\0', sizeof(ProjectSettings));

settings->open = FALSE;

if (filename == NULL)
   settings->name = NULL;
else
   openldev_project_settings_load_project_file (settings, filename);

return settings;
}
```

Save the file.

[COLOR="DarkOrchid"]3)[/COLOR] Configure, compile and install it.
$ [COLOR="Green"]cd openldev[/COLOR]
$[COLOR="Green"] ./configure [/COLOR]
$ [COLOR="Green"]make [/COLOR]
$ [COLOR="Green"]sudo make install [/COLOR]
[COLOR="DarkOrchid"]
4) [/COLOR]Start it.
$ [COLOR="SeaGreen"]openldev[/COLOR]

[COLOR="DarkOrchid"]5) [/COLOR]Inform the developers of OpenLDdev about this bug. 
Are they still active?

[COLOR="DarkOrchid"]6) [/COLOR]Make the Gutsy's developers known of this issue so the bug is fixed there too.
OpelLDev is included in the Gutsy??

---

### Post by panti85 on 2007-11-22
me pueden dar una mano con esto. no puedo entrar al openldev.
lo corro desde terminal y me aparece

panti@panti-pc:~$ openldev
Fallo de segmentación (core dumped)
panti@panti-pc:~$ 

alguien sabe porque?

---

