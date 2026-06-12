---
title: "Remove duplicate icons from Activities overview"
date: 2021-02-13
forum: New to Ubuntu
---

### Post by dat789 on 2021-02-13
Hello! I am using Ubuntu 18.04 and had an application installed a while ago, which can be accessed quickly from the Activities overview. That application stopped its support and had to install its desktop version instead. I'm having trouble removing its redundant former unsupported version. Can anyone help, please? 

Screenshot available
[ATTACH=CONFIG]287955[/ATTACH]

---

### Post by dat789 on 2021-02-13
I searched $HOME/.local/share/applications/ but could not find that Authy (obsolete) icon. Instead, they are:

[ATTACH=CONFIG]287956[/ATTACH]

---

### Post by dat789 on 2021-02-13
Rrright! I resolved this!

Apparently, each *.desktop file in  $HOME/.local/share/applications has details of the application or  execution path. I viewed each of them and found the one I wanted to  remove.


```

$ cd ~/.local/share/applications
$ cat chrome-abcxyz.desktop
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=Postman
Exec=/opt/google/chrome/google-chrome --profile-directory=Default --app-id=abcxyz
Icon=chrome-abcxyz-Default
StartupWMClass=crx_abcxyz

$ cat chrome-xyzabc.desktop
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=Authy
Exec=/opt/google/chrome/google-chrome --profile-directory=Default --app-id=xyzabc
Icon=chrome-xyzabc-Default
StartupWMClass=crx_xyzabc

$ rm chrome-xyzabc

```

Good now!

---

