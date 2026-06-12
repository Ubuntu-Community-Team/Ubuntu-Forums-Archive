---
title: "BASH script Security problem?? Help!"
date: 2008-09-04
forum: Programming Talk
---

### Post by hammer v2 on 2008-09-04
Hi guys,
I'm getting a wierd error when trying to run this executable bash script;

```
#!/bin/bash
gksu
sudo mkdir /tmp/setupsdeb
sudo cp -r *.* /tmp/setupsdeb
sudo cp -r ./install -d /tmp/setupsdeb/
sudo mv -f /etc/apt/sources.list /etc/apt/sources.list.bak
sudo mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak
sudo cp sources.list -t /etc/apt/
gksu gdebi-gtk AMSN-SUPERDEB-BETA.deb
yes | sudo apt-get install AMSN-SUPERDEB-BETA
sudo mv -f /etc/apt/sources.list.bak /etc/apt/sources.list
sudo mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d
zenity --info /
--text="Setup Completed. You can now run the program from the applications menu"
exit 1
fi
```

This is the error that comes up;
[IMG]http://superdeb.googlecode.com/files/Untitled.jpg[/IMG]

Any ideas as to why? How do I stop this from happening? - This is under Gutsy BTW..

Thanks!
H.

---

### Post by ghostdog74 on 2008-09-04
remove everything except these 2 lines
```

#!/bin/bash
gksu gdebi-gtk AMSN-SUPERDEB-BETA.deb
yes | sudo apt-get install AMSN-SUPERDEB-BETA

```
what did you see.?

---

### Post by rogeriopvl on 2008-09-04
I don't see any error :\

---

### Post by SeanHodges on 2008-09-04
That dialog will appear if you type "gksu" on its own. Which is the first command that your script is performing.

Remove gksu at the top, and replace your use of "sudo" with "gksu":

```
#!/bin/bash
gksu mkdir /tmp/setupsdeb
gksu cp -r *.* /tmp/setupsdeb
gksu cp -r ./install -d /tmp/setupsdeb/
gksu mv -f /etc/apt/sources.list /etc/apt/sources.list.bak
gksu mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak
gksu cp sources.list -t /etc/apt/
gksu gdebi-gtk AMSN-SUPERDEB-BETA.deb
yes | sudo apt-get install AMSN-SUPERDEB-BETA
gksu mv -f /etc/apt/sources.list.bak /etc/apt/sources.list
gksu mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d
zenity --info /
--text="Setup Completed. You can now run the program from the applications menu"
exit 1
```

---

### Post by Martin Witte on 2008-09-04
I would remove 'gksu' from the script, and - suppose the script is called 'my-install.sh' run it as sudo ./my-install.sh or gksu ./my-install.sh

---

### Post by Titan8990 on 2008-09-04
Scripts should not include sudo or gksudo. Instead you should run the script with sudo. Example assuming the script is named example.sh:

```
#!/bin/bash
mkdir /tmp/setupsdeb
cp -r *.* /tmp/setupsdeb
cp -r ./install -d /tmp/setupsdeb/
mv -f /etc/apt/sources.list /etc/apt/sources.list.bak
mv -f /etc/apt/sources.list.d /etc/apt/sources.list.d.bak
cp sources.list -t /etc/apt/
gdebi-gtk AMSN-SUPERDEB-BETA.deb
yes | sudo apt-get install AMSN-SUPERDEB-BETA
mv -f /etc/apt/sources.list.bak /etc/apt/sources.list
mv -f /etc/apt/sources.list.d.bak /etc/apt/sources.list.d
zenity --info /
--text="Setup Completed. You can now run the program from the applications menu"
exit 1
```

In the terminal you would run:

sudo ./example.sh

Again, you should not use sudo **inside** of the script.

---

