---
title: "trouble installing calibre"
date: 2019-06-18
forum: New to Ubuntu
---

### Post by billmaxey on 2019-06-18
I'm new to ubuntu, and am having trouble loading/installing calibre.
I am a total novice and would appreciate any help.
Thanks,
Bill Maxey

---

### Post by TheFu on 2019-06-18
If your system is fully patched, then 
```
sudo apt install calibre
```
will install the calibre server.

I don't know which port it listens on by default. Mine is set to 8181/tcp.
On my 16.04 server, the main startup happens in this file: /etc/init.d/calibre-server  where a few important settings are made at the top.  To get it actually working, start and kill symlinks were made to the normal rcN.d/ directories. This was done by the installer.  I only changed the userid it runs as, the port, and the location for the library.

If you are new to Linux/Unix and not just Ubuntu, this might not be enough information.  If you are a Unix guy, that should be more details that necessary. Nothing funny happening with Calibre that I can see.

If you've done something else attempting to get it install, probably best to undo all of that.

---

### Post by oldos2er on 2019-06-18
The command given [here]("https://calibre-ebook.com/download_linux") has always worked for me. Calibre is updated fairly frequently so I prefer to install it this way instead of from the repositories.

```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```

---

### Post by #&amp;thj^% on 2019-06-18
> **oldos2er said:**
> The command given [here]("https://calibre-ebook.com/download_linux") has always worked for me. Calibre is updated fairly frequently so I prefer to install it this way instead of from the repositories.

```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```

Nice and tidy thanks! And not only for Ubuntu. :D
```
 sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
Password: 
2019-06-18 15:02:47 URL:https://download.calibre-ebook.com/linux-installer.sh [31301/31301] -> "-" [1]
Using python executable: /usr/bin/python3
Installing to /opt/calibre
Downloading tarball signature securely...
Will download and install calibre-3.44.0-x86_64.txz 
                     Downloading calibre-3.44.0-x86_64.txz                      
100% [======================================================================]
                                                                                Downloaded 62464020 bytes 
Checking downloaded file integrity... 
Extracting files to /opt/calibre ...
Extracting application files... 
Creating symlinks...
	Symlinking /opt/calibre/fetch-ebook-metadata to /usr/bin/fetch-ebook-metadata
	Symlinking /opt/calibre/lrs2lrf to /usr/bin/lrs2lrf
	Symlinking /opt/calibre/markdown-calibre to /usr/bin/markdown-calibre
	Symlinking /opt/calibre/lrfviewer to /usr/bin/lrfviewer
	Symlinking /opt/calibre/calibredb to /usr/bin/calibredb
	Symlinking /opt/calibre/ebook-viewer to /usr/bin/ebook-viewer
	Symlinking /opt/calibre/ebook-convert to /usr/bin/ebook-convert
	Symlinking /opt/calibre/calibre to /usr/bin/calibre
	Symlinking /opt/calibre/ebook-device to /usr/bin/ebook-device
	Symlinking /opt/calibre/ebook-polish to /usr/bin/ebook-polish
	Symlinking /opt/calibre/web2disk to /usr/bin/web2disk
	Symlinking /opt/calibre/ebook-edit to /usr/bin/ebook-edit
	Symlinking /opt/calibre/calibre-server to /usr/bin/calibre-server
	Symlinking /opt/calibre/lrf2lrs to /usr/bin/lrf2lrs
	Symlinking /opt/calibre/calibre-debug to /usr/bin/calibre-debug
	Symlinking /opt/calibre/ebook-meta to /usr/bin/ebook-meta
	Symlinking /opt/calibre/calibre-customize to /usr/bin/calibre-customize
	Symlinking /opt/calibre/calibre-smtp to /usr/bin/calibre-smtp
	Symlinking /opt/calibre/calibre-parallel to /usr/bin/calibre-parallel
Setting up command-line completion...
Installing zsh completion to: /usr/share/zsh/site-functions/_calibre
Package bash-completion was not found in the pkg-config search path.
Perhaps you should add the directory containing `bash-completion.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bash-completion' found
Failed to find directory to install bash completions, using default.
Installing bash completion to: /usr/share/bash-completion/completions/calibre
Setting up desktop integration...
Creating un-installer: /usr/bin/calibre-uninstall
Run "calibre" to start calibre 

```
On:
```
lsb_release -a
LSB Version:	n/a
Distributor ID:	Gentoo
Description:	Gentoo Linux amd64 

```

---

### Post by billmaxey on 2019-06-18
Thanks.  That got it installed.  Now I have to figure out how to use it.
But first I need to mark this thread as solved.

---

### Post by TheFu on 2019-06-18
I'm curious. How do you maintain and update if not using the package manager?  Do you manually uninstall and reinstall monthly?

For me, using the Canonical repos is THE main reason to choose Ubuntu.  Stuff that needs to be manually maintained is something a avoid unless absolutely necessary and then only if it is special enough to be put onto a dedicated system.

---

### Post by #&amp;thj^% on 2019-06-18
All my systems are dedicated for one reason or another, I'm not sure if oldos2er uses the same method, but i like clean and tidy, and use:
```
cd /usr/bin/ && sudo calibre-uninstall
```
Un-install goes:
```
Removing mime resource: calibre-mimetypes.xml
Removing /usr/bin/markdown-calibre
Removing /usr/bin/calibre-customize
Removing /usr/bin/calibre-server
Removing /usr/bin/lrfviewer
Removing /usr/bin/fetch-ebook-metadata
Removing /usr/bin/ebook-viewer
Removing /usr/bin/ebook-polish
Removing /usr/bin/ebook-device
Removing /usr/bin/calibre-smtp
Removing /usr/bin/calibre
Removing /usr/bin/calibre-parallel
Removing /usr/bin/ebook-convert
Removing /usr/bin/lrf2lrs
Removing /usr/bin/calibre-debug
Removing /usr/bin/calibredb
Removing /usr/bin/lrs2lrf
Removing /usr/bin/web2disk
Removing /usr/bin/ebook-meta
Removing /usr/bin/ebook-edit
Removing /usr/share/zsh/site-functions/_calibre
Removing /usr/share/bash-completion/completions/calibre
Removing /usr/share/metainfo/calibre-gui.appdata.xml
Removing /usr/share/metainfo/calibre-ebook-viewer.appdata.xml
Removing /usr/share/metainfo/calibre-ebook-edit.appdata.xml
Removing /usr/bin/calibre-uninstall
Removing /opt/calibre
Removing /tmp/mime-hack.o1d7pg3d
Removing icon: calibre-gui from context: apps at size: 16
Removing icon: calibre-gui from context: apps at size: 32
Removing icon: calibre-gui from context: apps at size: 48
Removing icon: calibre-gui from context: apps at size: 64
Removing icon: calibre-gui from context: apps at size: 128
Removing icon: calibre-gui from context: apps at size: 256
Removing icon: calibre-viewer from context: apps at size: 16
Removing icon: calibre-viewer from context: apps at size: 32
Removing icon: calibre-viewer from context: apps at size: 48
Removing icon: calibre-viewer from context: apps at size: 64
Removing icon: calibre-viewer from context: apps at size: 128
Removing icon: calibre-viewer from context: apps at size: 256
Removing icon: calibre-ebook-edit from context: apps at size: 16
Removing icon: calibre-ebook-edit from context: apps at size: 32
Removing icon: calibre-ebook-edit from context: apps at size: 48
Removing icon: calibre-ebook-edit from context: apps at size: 64
Removing icon: calibre-ebook-edit from context: apps at size: 128
Removing icon: calibre-ebook-edit from context: apps at size: 256
Removing desktop file: calibre-gui.desktop
Removing desktop file: calibre-lrfviewer.desktop
Removing desktop file: calibre-ebook-viewer.desktop
Removing desktop file: calibre-ebook-edit.desktop

Remove the e-book format icons? [y/n]:
Removing icon: application-lrf from context: mimetypes at size: 16
Removing icon: application-lrf from context: mimetypes at size: 32
Removing icon: application-lrf from context: mimetypes at size: 48
Removing icon: application-lrf from context: mimetypes at size: 64
Removing icon: application-lrf from context: mimetypes at size: 128
Removing icon: application-lrf from context: mimetypes at size: 256
Removing icon: text-lrs from context: mimetypes at size: 16
Removing icon: text-lrs from context: mimetypes at size: 32
Removing icon: text-lrs from context: mimetypes at size: 48
Removing icon: text-lrs from context: mimetypes at size: 64
Removing icon: text-lrs from context: mimetypes at size: 128
Removing icon: text-lrs from context: mimetypes at size: 256
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 16
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 32
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 48
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 64
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 128
Removing icon: application-x-mobipocket-ebook from context: mimetypes at size: 256
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 16
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 32
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 48
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 64
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 128
Removing icon: application-x-topaz-ebook from context: mimetypes at size: 256
Removing icon: application-x-kindle-application from context: mimetypes at size: 16
Removing icon: application-x-kindle-application from context: mimetypes at size: 32
Removing icon: application-x-kindle-application from context: mimetypes at size: 48
Removing icon: application-x-kindle-application from context: mimetypes at size: 64
Removing icon: application-x-kindle-application from context: mimetypes at size: 128
Removing icon: application-x-kindle-application from context: mimetypes at size: 256
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 16
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 32
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 48
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 64
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 128
Removing icon: application-x-mobi8-ebook from context: mimetypes at size: 256

```

Works well for all my Distros.

---

### Post by oldos2er on 2019-06-19
> **billmaxey said:**
> Thanks.  That got it installed.  Now I have to figure out how to use it.
But first I need to mark this thread as solved.

Under Thread Tools at the top of the page there is a drop-down menu; thank you for marking this 'Solved.'

---

