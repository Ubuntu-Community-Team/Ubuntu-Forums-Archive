---
title: "install open office"
date: 2019-04-07
forum: New to Ubuntu
---

### Post by kanejohn82 on 2019-04-07
i have installed java with the following commands
sudo add-apt-repository ppa:linuxuprising/java
sudo apt update
sudo apt install oracle-java11-installer
sudo apt install oracle-java11-set-default

hen installed open office but it wont open it just goes to load and then dissapears can anyone help please :)

---

### Post by huff2 on 2019-04-08
Most likely you have not integrated the application with Gnome, which is necessary if you wan to open it from the desktop or the activities menu. Any reason why you want OpenOffice? I find LibreOffice (the default) to work great!

Here are detailed instructions for integrating an app with Gnome: [URL="https://developer.gnome.org/integration-guide/stable/desktop-files.html.en"]https://developer.gnome.org/integration-guide/stable/desktop-files.html.en


[/URL]

---

### Post by monkeybrain20122 on 2019-04-08
Try to start, say LO writer in  terminal and see what error messages you got. The command is simply
```
lowriter
```

BTW, you don't need oracle's java for LO (and 99.9% of the software), openjdk in repo is just as good and installing it removes an extra layer of unnecssary complexity since third party oracle java repos are not always well maintained and may give you update troubles.

Edited: did you mean openoffice or libreoffice?? I won't be surprised if OO doesn't work. I would just use LO.

---

### Post by oldrocker99 on 2019-04-08
OpenOffice has been pretty much abandoned by the original developers, who virtually all have moved to LibreOffice. Open Office is not in the repositories, but LibreOffice is, and is well advanced over OpenOffice. There really is no concrete reason to use OpenOffice.

---

### Post by Impavidus on 2019-04-09
Libreoffice should be installed by default. Openoffice conflicts with Libreoffice (or at least did so not so long ago), which could have led to an installation failure. That would also explain why Openoffice doesn't run and could mean you've got a package conflict to fix. We need more information on your situation.

BTW, (L/O)-Office only needs Java for some optional functions. You don't really need it, but some want it anyway.

---

