---
title: "gedit -- SnapOpen Help"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-05
Good morning|afternoon|evening.
How to install snapopen on gedit. Help !!!
Could you teach me step by step ? I'm just newbie.

---

### Post by quirks on 2008-05-05
I assume you downloaded it from here: [http://www.upperbound.net/snapopen/](http://www.upperbound.net/snapopen/)

There is a link on the page that points to INSTALL instructions, which are:
> Gedit Snap Open Plugin
Copyright (C) 2008 Mads Buus Westmark <online@buus.net>

INSTALLATION INSTRUCTIONS
1) Extract contents of archive
2) Copy files from gedit-snapopen directory to
   ~/.gnome2/gedit/plugins
3) Fire up gedit, go to Edit->Preferences, select the
   Plugins tab, and make sure "Snap Open" is checked

Do you have trouble performing these steps? If yes, where is your problem?

---

### Post by otrojake on 2008-05-05
Since you're new at this I'll give you some more detailed instructions than those that are on the snapopen site.

1) Download [this]("http://www.upperbound.net/snapopen/snapopen-1.1.4.tar.gz") file to your home directory.

2) Make a directory if it's not already there for the plugins for gedit by typing in this code in the terminal.```
mkdir -p ~/.gnome2/gedit/plugins
```

3) Extract the files from the archive you downloaded in step one to the plugins directory you just created by typing this into a terminal. ```
tar -xzvf snapopen-1.1.4.tar.gz -C ~/.gnome2/gedit/plugins
```

4) Open gedit and go to Edit>Preferences and then click on the Plug-ins tab and check snapopen.

You should be good to go then.:)

---

### Post by Zeck on 2008-05-05
> **otrojake said:**
> Since you're new at this I'll give you some more detailed instructions than those that are on the snapopen site.

1) Download [this]("http://www.upperbound.net/snapopen/snapopen-1.1.4.tar.gz") file to your home directory.

2) Make a directory if it's not already there for the plugins for gedit by typing in this code in the terminal.```
mkdir -p ~/.gnome2/gedit/plugins
```

3) Extract the files from the archive you downloaded in step one to the plugins directory you just created by typing this into a terminal. ```
tar -xzvf snapopen-1.1.4.tar.gz -C ~/.gnome2/gedit/plugins
```

4) Open gedit and go to Edit>Preferences and then click on the Plug-ins tab and check snapopen.

You should be good to go then.:)

Hi,
I'm tried it. But it have a problem.
Here is the problem.

zeck@zeck-desktop:~$ mkdir -p ~/.gnome2/gedit/plugins
zeck@zeck-desktop:~$ tar -xzvf snapopen-1.1.4.tar.gz -C ~/.gnome2/gedit/plugins
tar: snapopen-1.1.4.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zeck@zeck-desktop:~$ 
zeck@zeck-desktop:~$

---

### Post by otrojake on 2008-05-05
When you downloaded the file I linked to in step 1, did you put it in your home directory?  I'm sure those commands are correct commands and I think the error you're getting is because it's not finding the snapopen-1.1.4.tar.gz file in your home directory.  An easy way to get that file to your home directory is by running this command```
wget http://www.upperbound.net/snapopen/snapopen-1.1.4.tar.gz
```

---

### Post by pengper on 2011-05-18
I've got the same error.

Not only that, but I don't get a reaction when I try to add the .gnome2 file in the Terminal, and it refuses in File Manager because it's already there- it must be hidden. How would I go about unhiding it? Mine is the only account on the machine with full permissions. I had a look in the 'Properties' menu, and gave myself R/W rights for all files, but other than that...

I tried redownloading it via the Terminal command you posted last, but then when I ran the command in step 3, I got "gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now"

---

