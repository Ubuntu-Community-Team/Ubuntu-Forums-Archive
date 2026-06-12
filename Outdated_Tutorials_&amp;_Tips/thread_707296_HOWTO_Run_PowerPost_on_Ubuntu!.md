---
title: "HOWTO: Run PowerPost on Ubuntu!"
date: 2008-02-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Martje_001 on 2008-02-25
**Step 1:**
*Install wine*
Install wine via "system --> Administration --> Synaptic Package Manager" or follow the instrucions on [WineHQ]("http://www.winehq.org/site/download-deb").

**Step 2:**
*Solve the dll-hell ;)*
Do this in a terminal:
```
cd ~/.wine/drive_c/windows/system
wget http://dll.softandco.com/dll/dlls/Mfc42.zip -O mfc42.zip
unzip mfc42.zip
cp Mfc42.dll mfc42.dll
rm mfc42.zip
cd ~
```

**Step 3:**
*Get powerpost*
Do this in a terminal:
```
wget http://powerpost.free.fr/files/'YencPowerPostA&A11b.zip'
unzip 'YencPowerPostA&A11b.zip'
rm 'YencPowerPostA&A11b.zip'
mv 'YencPowerPostA&A11b' .PowerPost
```

**Step 4:**
*Make a system-wide link*
```
cd /usr/bin
sudo nano powerpost
```
Paste these two lines:
```
#!/bin/bash
wine ~/.PowerPost/'YencPowerPostA&A11b.exe'
```
Press **CTRL+O** to save and **CTRL+X** to exit.
Now do:
```
sudo chmod +x powerpost
```

**Step 5:**
*Run PowerPost!*
Press **ALT+F2** --> **powerpost**

---

### Post by dalezjc on 2008-05-26
When I try to unzip, I get the following:

Archive:  mfc42.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of mfc42.zip or
        mfc42.zip.zip, and cannot find mfc42.zip.ZIP, period.

---

### Post by Martje_001 on 2008-05-27
* updated link *

[http://dll.softandco.com/dll/dlls/Mfc42.zip](http://dll.softandco.com/dll/dlls/Mfc42.zip)

please try again with the new link

---

### Post by dalezjc on 2008-05-27
Works perfect!  Great instructions.
thanks,
Dale

---

