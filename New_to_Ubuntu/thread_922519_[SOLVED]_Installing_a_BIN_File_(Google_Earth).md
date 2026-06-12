---
title: "[SOLVED] Installing a BIN File (Google Earth)"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Witling on 2008-09-17
I want to install Google Earth. I use Firefox as a browser. If I go to Google it downloads a file called GoogleEarthLinux.bin. How do I get from here to having Google Earth installed? If I try Synaptic it says, "Kiss my grits, Shorty!. I'm not touching your lousy BIN file." If I try using the Tools > Download function in Firefox it says, "Happy to oblige. Just tell me which program you want to use." Well, that's the question, isn't it. :confused: I actually did try searching both Ubuntu Help and these forums but I didn't find an answer that was understandable to me. I think that's probably operator error and not know the correct question to ask.

---

### Post by oldos2er on 2008-09-17
Open a terminal, type and enter these commands one at a time:

cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin

---

### Post by aloshbennett on 2008-09-17
To install a binary file or any file for that matter, first thing, it should be an executable. You can make it executable like this:

```
cd directory/containing/file
chmod +x GoogleEarthLinux.bin

```

Once you have given yourself execute previlage (+x), you can run it by:
```

./GoogleEarthLinux.bin

```

Some installations require root previleges. To install with root previlege, try "sudo ./GoogleEarthLinux.bin"

Ubuntu doesnt like .bin files cos there is no way to know what you are executing really.

---

### Post by drs305 on 2008-09-17
If you are running Hardy, here is the easiest way I know to install GoogleEarth:

If you haven't enabled it, add the Medibuntu repository from [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu"):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Install Google Earth (this is a metapackage, no version number required. current version 4.3.7+):
```

sudo apt-get update && sudo apt-get install googleearth
```

---

### Post by Witling on 2008-09-17
Thank you all very much but, more important than solving this particular problem, were the general explanations about installing BIN and other files. As they say in fake Japanese, "Thanks ohatchi, mucho!:D

---

### Post by Bölvaður on 2008-09-17
The guy above me here has it correct, and good/short explanations of what you are doing.

But here is the GUI version of it.

Right click on the file and click Properties.
Find Permissions tap and look for "Execute" on lower half of the dialog and mark it so it will execute (think it is a cross).

Now you can double click to run it.
When you have clicked it, it will prompt you with questions about what to do with it. I think you should either pick "Run" or "Run in terminal".


But because terminal commands are shorter than writing all this, and is foolproof.. you should go with the terminal.

---

