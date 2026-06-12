---
title: "12:04 Ubuntu, Software Center Opens then Closes"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by RonanDex on 2012-05-13
when i try to open Software Center it now opens and then closes b4 i get a chance to use it.

this started happening at last update..

Please Advise

---

### Post by Lisiano on 2012-05-13
Please open a terminal (Ctrl+Alt+T) and type this ```
software-center --debug
``` then once it closes, copy and paste the output you got here using code tags (The hash (#) button)

---

### Post by RonanDex on 2012-05-13
gnu-r
2012-05-14 10:33:23,880 - softwarecenter.db.categories - DEBUG - adding section: restricted/gnu-r
2012-05-14 10:33:23,881 - softwarecenter.db.categories - DEBUG - adding section: universe/gnu-r
2012-05-14 10:33:23,882 - softwarecenter.db.categories - DEBUG - adding section: multiverse/gnu-r
2012-05-14 10:33:23,886 - softwarecenter.db.categories - DEBUG - adding tag: ttf*
2012-05-14 10:33:23,888 - softwarecenter.db.categories - DEBUG - adding tag: otf*
2012-05-14 10:33:23,889 - softwarecenter.db.categories - DEBUG - adding section: fonts
2012-05-14 10:33:23,890 - softwarecenter.db.categories - DEBUG - adding section: restricted/fonts
2012-05-14 10:33:23,893 - softwarecenter.db.categories - DEBUG - adding section: universe/fonts
2012-05-14 10:33:23,894 - softwarecenter.db.categories - DEBUG - adding section: multiverse/fonts
2012-05-14 10:33:23,895 - softwarecenter.db.categories - DEBUG - adding tag: ttfm
2012-05-14 10:33:23,897 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/Game.directory'
2012-05-14 10:33:23,901 - softwarecenter.db.categories - DEBUG - adding: Game
2012-05-14 10:33:23,910 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/SimulationGames.directory'
2012-05-14 10:33:23,927 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/SportsGames.directory'
2012-05-14 10:33:23,932 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/Graphics.directory'
2012-05-14 10:33:23,936 - softwarecenter.db.categories - DEBUG - adding: Graphics
2012-05-14 10:33:23,939 - softwarecenter.db.categories - DEBUG - adding: 3DGraphics
2012-05-14 10:33:23,941 - softwarecenter.db.categories - DEBUG - adding: VectorGraphics
2012-05-14 10:33:23,942 - softwarecenter.db.categories - DEBUG - adding: Viewer
2012-05-14 10:33:23,944 - softwarecenter.db.categories - DEBUG - adding: RasterGraphics
2012-05-14 10:33:23,945 - softwarecenter.db.categories - DEBUG - adding: Viewer
2012-05-14 10:33:23,949 - softwarecenter.db.categories - DEBUG - adding: Scanning
2012-05-14 10:33:23,952 - softwarecenter.db.categories - DEBUG - adding: Photography
2012-05-14 10:33:23,954 - softwarecenter.db.categories - DEBUG - adding: Publishing
2012-05-14 10:33:23,957 - softwarecenter.db.categories - DEBUG - adding: Scanning
2012-05-14 10:33:23,957 - softwarecenter.db.categories - DEBUG - adding: OCR
2012-05-14 10:33:23,960 - softwarecenter.db.categories - DEBUG - adding: Viewer
2012-05-14 10:33:23,963 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/Network.directory'
2012-05-14 10:33:23,967 - softwarecenter.db.categories - DEBUG - adding: Network
2012-05-14 10:33:23,969 - softwarecenter.db.categories - DEBUG - adding: InstantMessaging
2012-05-14 10:33:23,971 - softwarecenter.db.categories - DEBUG - adding: FileTransfer
2012-05-14 10:33:23,974 - softwarecenter.db.categories - DEBUG - adding: Email
2012-05-14 10:33:23,976 - softwarecenter.db.categories - DEBUG - adding: WebBrowser
2012-05-14 10:33:23,984 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/AudioVideo.directory'
2012-05-14 10:33:23,988 - softwarecenter.db.categories - DEBUG - adding: AudioVideo
2012-05-14 10:33:23,991 - softwarecenter.db.categories - DEBUG - reading '/usr/share/desktop-directories/Office.directory'
2012-05-14 10:33:23,994 - softwarecenter.db.categories - DEBUG - adding: Office
2012-05-14 10:33:24,000 - softwarecenter.db.categories - DEBUG - adding: X-Publication
2012-05-14 10:33:24,006 - softwarecenter.db.categories - DEBUG - adding type: Application
2012-05-14 10:33:24,013 - softwarecenter.db.categories - DEBUG - adding type: Application
2012-05-14 10:33:24,018 - softwarecenter.db.categories - DEBUG - adding tag: armagetronad
2012-05-14 10:33:24,020 - softwarecenter.db.categories - DEBUG - adding tag: calibre
2012-05-14 10:33:24,021 - softwarecenter.db.categories - DEBUG - adding tag: cheese
2012-05-14 10:33:24,022 - softwarecenter.db.categories - DEBUG - adding tag: homebank
2012-05-14 10:33:24,023 - softwarecenter.db.categories - DEBUG - adding tag: stellarium
2012-05-14 10:33:24,027 - softwarecenter.db.categories - DEBUG - adding tag: gimp
2012-05-14 10:33:24,029 - softwarecenter.db.categories - DEBUG - adding tag: inkscape
2012-05-14 10:33:24,030 - softwarecenter.db.categories - DEBUG - adding tag: blender
2012-05-14 10:33:24,031 - softwarecenter.db.categories - DEBUG - adding tag: audacity
2012-05-14 10:33:24,033 - softwarecenter.db.categories - DEBUG - adding tag: gufw
2012-05-14 10:33:24,034 - softwarecenter.db.categories - DEBUG - adding tag: frozen-bubble
2012-05-14 10:33:24,035 - softwarecenter.db.categories - DEBUG - adding tag: fretsonfire
2012-05-14 10:33:24,036 - softwarecenter.db.categories - DEBUG - adding tag: moovida
2012-05-14 10:33:24,037 - softwarecenter.db.categories - DEBUG - adding tag: liferea
2012-05-14 10:33:24,041 - softwarecenter.db.categories - DEBUG - adding tag: arista
2012-05-14 10:33:24,042 - softwarecenter.db.categories - DEBUG - adding tag: gtg
2012-05-14 10:33:24,043 - softwarecenter.db.categories - DEBUG - adding tag: freeciv-client-gtk
2012-05-14 10:33:24,045 - softwarecenter.db.categories - DEBUG - adding tag: supertuxkart
2012-05-14 10:33:24,046 - softwarecenter.db.categories - DEBUG - adding tag: tumiki-fighters
2012-05-14 10:33:24,047 - softwarecenter.db.categories - DEBUG - adding tag: tuxpaint
2012-05-14 10:33:24,048 - softwarecenter.db.categories - DEBUG - adding tag: webservice-office-zoho
2012-05-14 10:33:24,055 - softwarecenter.db.categories - DEBUG - Accessories applications-utilities Xapian::Query(((<alldocuments> AND ACutility) AND_NOT ACaccessibility))
2012-05-14 10:33:24,056 - softwarecenter.db.categories - DEBUG - Universal Access preferences-desktop-accessibility Xapian::Query(((<alldocuments> AND ACaccessibility) AND_NOT ACsettings))

---

### Post by RonanDex on 2012-05-13
there is alot more but it wont let me post it all

---

### Post by RonanDex on 2012-05-13
2012-05-14 10:33:24,056 - softwarecenter.db.categories - DEBUG - Universal Access preferences-desktop-accessibility Xapian::Query(((<alldocuments> AND ACaccessibility) AND_NOT ACsettings))
2012-05-14 10:33:24,057 - softwarecenter.db.categories - DEBUG - Developer Tools applications-development Xapian::Query((ACdevelopment OR XSdevel OR AEdevel OR XSrestricted/devel OR AErestricted/devel OR XSuniverse/devel OR AEuniverse/devel OR XSmultiverse/devel OR AEmultiverse/devel OR ACdebugger OR ACguidesigner OR XShaskell OR AEhaskell OR XSrestricted/haskell OR AErestricted/haskell OR XSuniverse/haskell OR AEuniverse/haskell OR XSmultiverse/haskell OR AEmultiverse/haskell OR ACide OR XSjava OR AEjava OR XSrestricted/java OR AErestricted/java OR XSuniverse/java OR AEuniverse/java OR XSmultiverse/java OR AEmultiverse/java OR XSlibdevel OR AElibdevel OR XSrestricted/libdevel OR AErestricted/libdevel OR XSuniverse/libdevel OR AEuniverse/libdevel OR XSmultiverse/libdevel OR AEmultiverse/libdevel OR XSlisp OR AElisp OR XSrestricted/lisp OR AErestricted/lisp OR XSuniverse/lisp OR AEuniverse/lisp OR XSmultiverse/lisp OR AEmultiverse/lisp OR (<alldocuments> AND ACtranslation) OR XScli-mono OR AEcli-mono OR XSrestricted/cli-mono OR AErestricted/cli-mono OR XSuniverse/cli-mono OR AEuniverse/cli-mono OR XSmultiverse/cli-mono OR AEmultiverse/cli-mono OR XSocaml OR AEocaml OR XSrestricted/ocaml OR AErestricted/ocaml OR XSuniverse/ocaml OR AEuniverse/ocaml OR XSmultiverse/ocaml OR AEmultiverse/ocaml OR XSperl OR AEperl OR XSrestricted/perl OR AErestricted/perl OR XSuniverse/perl OR AEuniverse/perl OR XSmultiverse/perl OR AEmultiverse/perl OR ACprofiling OR XSpython OR AEpython OR XSrestricted/python OR AErestricted/python OR XSuniverse/python OR AEuniverse/python OR XSmultiverse/python OR AEmultiverse/python OR XSruby OR AEruby OR XSrestricted/ruby OR AErestricted/ruby OR XSuniverse/ruby OR AEuniverse/ruby OR XSmultiverse/ruby OR AEmultiverse/ruby OR XSvcs OR AEvcs OR XSrestricted/vcs OR AErestricted/vcs OR XSuniverse/vcs OR AEuniverse/vcs OR XSmultiverse/vcs OR AEmultiverse/vcs OR ACrevisioncontrol OR (<alldocuments> AND ACwebdevelopment)))

---

### Post by RonanDex on 2012-05-13
there is a attached SS

---

### Post by Lisiano on 2012-05-13
Type in this command instead
```
software-center --debug &> ~/USC.Result.txt
```After it closes, in your home folder, you will find a file called USC.Result.txt, attach it here or copy paste it's content here [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and give us the link.

---

### Post by RonanDex on 2012-05-13
[http://paste.ubuntu.com/986477/](http://paste.ubuntu.com/986477/)

200k file lol 

so i had to use paste.

---

### Post by Lisiano on 2012-05-14
Okay so it seems USC is failing to read it's cache properly (EDIT: Pardon, the APT cache, noticed it only now), one way to fix this is to reset the cache, I don't remember what is needed to be done to check it, I'll find out later, in a few hours, once I get access to my PC.

---

### Post by Lisiano on 2012-05-14
Okay. Try to issue this command.
```
sudo apt-get update
``` If there are any errors, copy paste them here. If there are no errors, continue by issuing ```
sudo apt-get upgrade
```

---

### Post by RonanDex on 2012-05-14
Thanks so much that has solved the issue..

Thanks again.

---

### Post by codingman on 2012-05-14
don't forget to set this as solved!

---

### Post by Lisiano on 2012-05-23
Don't put an & at the end of the command. Run the command in foreground.

---

### Post by crazyredsextuplet on 2012-07-29
i type sudo apt-get update   and   end with this sentences...

Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [65.4 kB]
Fetched 14.0 MB in 3min 10s (73.5 kB/s)                                        
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

what should i do next?

---

### Post by richie16171 on 2012-11-09
I al so has the same probem in ubuntu 12.10 . I was trying to install skype and refered commands typed  in the terminal and hence software center cannot be opened.(open and closes). when i typed sudo apt-get update in terminal then this error messege came E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
 
Please help

---

