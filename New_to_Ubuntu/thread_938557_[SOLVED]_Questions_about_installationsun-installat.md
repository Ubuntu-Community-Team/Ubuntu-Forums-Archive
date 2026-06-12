---
title: "[SOLVED] Questions about installations/un-installations"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Eto_Demerzel on 2008-10-05
I have a few questions regarding installation process of a program in Ubuntu.

1) When I install a program through Synaptic package manager, which all folders/files that are modified/created in the system?

2) When a program is installed in Windows, keys are added in the registry. Is there something like registry in Ubuntu?

3) Say I have installed a program called blahblah through Synaptic. I find all files and folders containing the word blahblah and delete all of them. Is this as good as uninstalling blahblah using Synaptic? If it is not so, what else does Synaptic do during an uninstallation?

4) Is there any way of uninstalling a program NOT installed through synaptic package manager?

Specifically, I installed RealPlayer from their site. It was a bin file. I want to remove it. Is there an easy way? If not, which all folders/files must I delete?

I'm sure I'm not the only person curious about how an installation process works. :)

Thanks.

---

### Post by jamesrl on 2008-10-05
1) Depends on the program.  If you go into synaptic, select any particular program (say gedit), and look at installed files you'll see a list like this:
```
/.
/usr
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/gedit
/usr/share/doc
/usr/share/doc/gedit
/usr/share/doc/gedit/copyright
/usr/share/menu
/usr/share/menu/gedit
/usr/share/applications
/usr/share/applications/gedit.desktop
/usr/share/gconf
/usr/share/gconf/schemas
/usr/share/gconf/schemas/gedit-file-browser.schemas
/usr/share/gconf/schemas/gedit.schemas
/usr/share/python-support
/usr/share/python-support/gedit.dirs
/usr/bin
/usr/bin/gedit
/usr/lib
/usr/lib/gedit
/usr/lib/gedit/gedit-2
/usr/lib/gedit/gedit-2/gedit-bugreport.sh
/usr/lib/gedit-2
/usr/lib/gedit-2/plugins
/usr/lib/gedit-2/plugins/changecase.gedit-plugin
/usr/lib/gedit-2/plugins/docinfo.gedit-plugin
/usr/lib/gedit-2/plugins/externaltools.gedit-plugin
/usr/lib/gedit-2/plugins/filebrowser.gedit-plugin
/usr/lib/gedit-2/plugins/indent.gedit-plugin
/usr/lib/gedit-2/plugins/modelines.gedit-plugin
/usr/lib/gedit-2/plugins/pythonconsole.gedit-plugin
/usr/lib/gedit-2/plugins/sample.gedit-plugin
/usr/lib/gedit-2/plugins/snippets.gedit-plugin
/usr/lib/gedit-2/plugins/sort.gedit-plugin
/usr/lib/gedit-2/plugins/spell.gedit-plugin
/usr/lib/gedit-2/plugins/taglist.gedit-plugin
/usr/lib/gedit-2/plugins/time.gedit-plugin
/usr/lib/gedit-2/plugins/libchangecase.so
/usr/lib/gedit-2/plugins/libdocinfo.so
/usr/lib/gedit-2/plugins/libfilebrowser.so
/usr/lib/gedit-2/plugins/libindent.so
/usr/lib/gedit-2/plugins/libmodelines.so
/usr/lib/gedit-2/plugins/libsample.so
/usr/lib/gedit-2/plugins/libsort.so
/usr/lib/gedit-2/plugins/libspell.so
/usr/lib/gedit-2/plugins/libtaglist.so
/usr/lib/gedit-2/plugins/libtime.so
/usr/lib/gedit-2/plugins/pythonconsole
/usr/lib/gedit-2/plugins/pythonconsole/__init__.py
/usr/lib/gedit-2/plugins/pythonconsole/console.py
/usr/lib/gedit-2/plugins/externaltools
/usr/lib/gedit-2/plugins/externaltools/__init__.py
/usr/lib/gedit-2/plugins/externaltools/capture.py
/usr/lib/gedit-2/plugins/externaltools/ElementTree.py
/usr/lib/gedit-2/plugins/externaltools/functions.py
/usr/lib/gedit-2/plugins/externaltools/library.py
/usr/lib/gedit-2/plugins/externaltools/manager.py
/usr/lib/gedit-2/plugins/externaltools/outputpanel.py
/usr/lib/gedit-2/plugins/externaltools/tools.glade
/usr/lib/gedit-2/plugins/snippets
/usr/lib/gedit-2/plugins/snippets/__init__.py
/usr/lib/gedit-2/plugins/snippets/Document.py
/usr/lib/gedit-2/plugins/snippets/ElementTree.py
/usr/lib/gedit-2/plugins/snippets/Exporter.py
/usr/lib/gedit-2/plugins/snippets/Helper.py
/usr/lib/gedit-2/plugins/snippets/Importer.py
/usr/lib/gedit-2/plugins/snippets/Library.py
/usr/lib/gedit-2/plugins/snippets/Manager.py
/usr/lib/gedit-2/plugins/snippets/Parser.py
/usr/lib/gedit-2/plugins/snippets/Placeholder.py
/usr/lib/gedit-2/plugins/snippets/Snippet.py
/usr/lib/gedit-2/plugins/snippets/SnippetComplete.py
/usr/lib/gedit-2/plugins/snippets/SubstitutionParser.py
/usr/lib/gedit-2/plugins/snippets/WindowHelper.py
/usr/lib/gedit-2/plugins/snippets/snippets.glade
/usr/share/doc/gedit/README
/usr/share/doc/gedit/BUGS
/usr/share/doc/gedit/AUTHORS
/usr/share/doc/gedit/NEWS.gz
/usr/share/doc/gedit/changelog.Debian.gz
```
which shows where it installs files to.  Mostly I'd say it installs programs within the /usr directory, libraries in the /lib directory, and for system wide configuration files in the /etc directory.

2)  For the most part no there is no linux registry, but two things sort of similar.  System wide configuration files are usually within /etc directory [local configurations files for each user are in the user's home directory (often hidden with a dot . as first letter in file name - use 'ls -a' or 'l.' to see)].  Gnome has something akin to a registry that you can search for keys, and that you can edit with gconf-editor (GUI) or gconftool-2 (by the command line).

3) No, you should leave it to synaptic.  Synaptic (actually dpkg will, which synaptic is just one front-end for (other frontends are apt-get, aptitude, adept, ..)) will register the program still installed.  This not a big problem, however if you try and install a new program that relies on your manually deleted program as a dependency, the new program won't work.  The package-manager is your friend, it finds all the files and checks all the dependencies and allow for easy installs/removals.

4)Actually you could try looking around the /opt/real/Realplayer/postinst/ directory for uninstall scripts and run all that you see, and then follow the following advice:

[I]4) You should manually remove the files.  checkinstall -D can create packages for things you have to compile yourself which allows for easy removal.  But for your specific problem, I believe you have to find and manually remove the files yourself.
So run
```
locate -i realplay

```
to find where realplayer installed files.  On my system all the files (except a few small icons that are more work than its worth to remove) are located within /opt/real
so a simple 
```
rm -r /opt/real
```
would remove it.[/I]

---

### Post by Eto_Demerzel on 2008-10-05
Thanks a lot for the reply. I appreciate it.

---

