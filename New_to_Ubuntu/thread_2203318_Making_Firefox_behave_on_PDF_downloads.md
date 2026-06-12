---
title: "Making Firefox behave on PDF downloads"
date: 2014-02-02
forum: New to Ubuntu
---

### Post by cigtoxdoc on 2014-02-02
I download numerous PDF files every day from the websites of scientific journals.  If I tell Firefox to save the files, it wants to save them in tmp.  If I tell them to use Adobe reader, it wants to use the Linux version of Adobe 9.  I really need it to use the Adobe Reader XI. There are also other types of files that I need to either save to USERNAME/Downloads or open with programs I have installed under wine.  The same goes for associating files with wine programs in Nautilus.  How does one make Firefox and Nautilus behave so that they are effective in a business environment?  Firefox is v26.0

John

---

### Post by varunendra on 2014-02-02
> **cigtoxdoc said:**
> If I tell Firefox to save the files, it wants to save them in tmp
In Firefox,
**Edit > Preferences > General tab > select "Always ask me where to save files"** (or select a desired location in the "Save files to.." option above).

Besides that, goto **"Applications" tab in the same Preferences box > browse to "PDF documents" > click the action and change it to "Always ask"**.

This is how I have it here and it works perfectly.

> **cigtoxdoc said:**
> There are also other types of files that I need to either save to USERNAME/Downloads or open with programs I have installed under wine.
In the same box where you set "Always ask", select** "Use other..." > browse to .wine/drive_c/Program Files (or Program Files (x86), as applicable) > the desired program folder > select the program executable file** (e.g. "WINWORD.exe").
Note that you may have to enable "Show Hidden files" (shortcut - Ctrl-H) beforehand to be able to see the hidden folder .wine.

I'm not sure if the above will always work since the programs installed in wine are not Linux executables, they can't always be directly associated with file types in Linux. You may have to create some sort of 'launcher' to launch them properly using wine.

> **cigtoxdoc said:**
> The same goes for associating files with wine programs in Nautilus.

Assuming you are using default Ubuntu (with Unity), you must create ".desktop" files (e.g. - AdobeReader.desktop) if wine didn't already create them. If it did create them, simply change the default "mime" associations in the** .local/share/applications/mimeapps.list** file in your home.

For example, if wine already created a .desktop launcher file, say, adobereader.desktop on the desktop and it works, copy it to your ** .local/share/applications/** directory (or /usr/share/applications, if you need to do it for all users on the same computer), and add its name to your **.local/share/applications/mimeapps.list** file, so that the line -
```
application/pdf=evince.desktop
```
under **[Default Applications]** section becomes -
```
application/pdf=adobereader.desktop
```

Note that the existing .desktop files may not appear by their actual filenames, but by the "Name=" value in their contents. One of a few ways to see their actual filenames is to simply copy the files (if you know those are launchers) and paste them in a text editor or terminal.

Once the mimeapps.list file has been properly modified and saved, the next time you double-click a file, it will open with the new program that you associated with in the mimeapps.list file.

If wine hasn't already created a .desktop launcher, here is the contents of a sample file (emu8086.desktop) for reference to create your own -
```
[Desktop Entry]
Name=emu8086
Exec=env WINEPREFIX="/home/varun/.wine" wine C:\\\\emu8086\\\\emu8086.exe 
Type=Application
StartupNotify=true
Path=/home/varun/.wine/dosdevices/c:/emu8086
Icon=E538_icon.0
```

**PS:**
It is a good idea to back up the original mimiapps.list file before making changes to it. Just in case something is messed up and you need to start over. :)

---

