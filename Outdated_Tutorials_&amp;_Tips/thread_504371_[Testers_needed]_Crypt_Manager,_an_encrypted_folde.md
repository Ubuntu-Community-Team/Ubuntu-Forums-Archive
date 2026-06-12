---
title: "[Testers needed] Crypt Manager, an encrypted folder manager for Linux"
date: 2007-07-19
forum: Outdated Tutorials &amp; Tips
---

### Post by keyes on 2007-07-19
Hello, my Google Summer of Code for Ubuntu is ready to his test phase.

This an encrypted folder manager. He allow to easily encrypt, decrypt, open and close folders. It works in command line, have a GTK interface and provide a Nautilus extension.

[B]Be careful ! Don't use this tool on important data and backup evrything before !!!
This is just an SVN version, still in dev with a lot of bugs.[/B]

To try it :
$ sudo addgroup <your-login> fuse
$ sudo apt-get install encfs python2.4-dev python-nautilus subversion
$ svn checkout [http://crypt-manager.googlecode.com/svn/trunk/](http://crypt-manager.googlecode.com/svn/trunk/) crypt-manager
$ sudo crypt-manager/install.sh

And type :
$ gcrypt-amanger
Or go to System -> Administration -> Encrypted folders

You can also use it by right clicking on a folder in Nautilus.

For command line, try :
$ crypt-manager --help

When you got a bug, please join the traceback (which is displayed in the terminal window) and an archive (tar.bz2, Zip, ...) of the folder you was trying to encrypt.


It uses EncFS as backend (there is also an old version using cryptsetup and LUKS but must be run as root and add a size limitation to folders).


**What's the difference between Crypt Manager end CryptKeeper or the Gentoo wiki Zenity script ?**

In a graphical way, Crypt Manager want to allow non-computer sciencer users (like my grand mother) to protect his sensitives data.
The goal is to have someting easy, natural and performant as possible.
It must be really simple to understand and to use, integrated with (in a first time) GNOME.
The final behavior must be something like "right click on a folder, choose encrypt" or "go to your encrypted folder, a pop-up ask your password".

There is already some usefull functions like encrypt existing folders, change the folder password or auto-close the encrypted folder after X minutes of IDLE.

But Crypt Manager it's more than just a GUI.
It's also a powerfull command tool for scripting (the GUI also have a CLI) and server use.

Crypt Manager also provide a Python module to manage encrypted folders, manage and perform operations on the list.
It's easy to integrate with other applications or (for example) write a QT or what else GUI.

The goal is to be as generic as possible and to provide a standard interface to manage crypted folders on Linux.

Please send me feedback about this project and... report the lot of bugs it must have on our issues tracker :)


The issues tracker : [http://code.google.com/p/crypt-manager/issues/list](http://code.google.com/p/crypt-manager/issues/list)
More infos and docs : [http://code.google.com/p/crypt-manager/](http://code.google.com/p/crypt-manager/)

---

### Post by frodon on 2007-07-19
Hi keyes, nice to see you here again with another great project :)

---

### Post by franestepona on 2007-07-19
Hi keyes
I try it, and it got stuck after a while (the processor wasnt working but the program seemed working) and the folder i was trying to encrypt it's empty now. If i open the program and choose decrypt nothing happend. What can I do to recover my data?

Help please!

---

### Post by keyes on 2007-07-19
Take a look into /tmp/cryptmanager/aDigestWithManyLetters.

Of course don't run this SVN version on important data !! I'll add a warning...

Can you send me the trackback displayed in the terminal window and an archive of the folder you try to encrypt ?

---

### Post by keyes on 2007-07-24
Now available as Debian / Ubuntu packages :
[http://code.google.com/p/crypt-manager/downloads/detail?name=crypt-manager_0.0.1-1ubuntu0_all.deb](http://code.google.com/p/crypt-manager/downloads/detail?name=crypt-manager_0.0.1-1ubuntu0_all.deb)
[http://code.google.com/p/crypt-manager/downloads/detail?name=gcrypt-manager_0.0.1-1ubuntu0_all.deb](http://code.google.com/p/crypt-manager/downloads/detail?name=gcrypt-manager_0.0.1-1ubuntu0_all.deb)
[http://code.google.com/p/crypt-manager/downloads/detail?name=nautilus-crypt_0.0.1-1ubuntu0_all.deb](http://code.google.com/p/crypt-manager/downloads/detail?name=nautilus-crypt_0.0.1-1ubuntu0_all.deb)

---

### Post by yopnono on 2007-07-25
> **franestepona said:**
> Hi keyes
I try it, and it got stuck after a while (the processor wasnt working but the program seemed working) and the folder i was trying to encrypt it's empty now. If i open the program and choose decrypt nothing happend. What can I do to recover my data?

Help please!

Well I just tried it and I had the same issue, and this was because I was not in the fuse group. Also there seems to be no nautilus entry of any kind.
I installed using the deb you are providing.

EDIT: Missing Icon
It's missing the icon for decrypt dialog see img.

EDIT: Error...
If open the main GTK dialog and select properties, and then close the properties window on the close button at the top corner the main dialog stays open, grayed out. 
And I need to kill from the terminal or system manager. 

If I don't and open the GTK again, it sometimes corrupt the FUSE mounted folder, It's not showing up in the main dialog, also there is still running multiply cryptfolder-gtk as processes.

---

### Post by yopnono on 2007-07-25
Other thing that would be great is to be able to save the settings like "always auto close on "XX" min" Instead of like now, that you need to set the timer everytime.

Great work by the way :)

---

### Post by rob_quill on 2007-08-07
Hi,

I really like the idea of your program but I am having trouble getting it to work. I have encrypted a folder: /home/rob/encrypted. However I can still open it in nautilus. Am I doing something wrong?

Keep up the good work :) Excellent idea IMHO.

Rob

---

### Post by keyes on 2007-08-09
Fixed gray bug yopnono, for always auto-close I'll look what I can do.
The icon bug seems to be a glade bug :S

rob_quill: can you paste me what appear in a terminal when you type:
```
nautilus -q && nautilus --restart
```

Thanks :)

The thread continue here: [http://ubuntuforums.org/showthread.php?t=521764](http://ubuntuforums.org/showthread.php?t=521764)

---

### Post by twizler on 2008-08-28
PROBLEM _ I installed the Program - The Folder I attempted to encrypt was 200 megabyte folder with pictures taken via my iphone. Dont get excited on pictures it was borning stuff thats why i used it AS A TEST. Anyhow, in my initial test the crypt program locked up, and after 20 min i had to kill the process. So the folder thinks its encrypted and when i click on the folder it tells me i dont have permission to view it and folder is empty, but when i go into the dialog window of Crypt manager it doesnt show the folder in the list as encrypted. If i try to do anything to the folder such as delete it as root it gives me an error and i cant delete it and i cant unencrypt it because it doenst know via Crypt Manager gui its encrypted. Now if i try to re-encrypt the folder it tells me via a nice pop up window that the folder is already encrypted ... 

QUITE annoying.  ( Dont think this is a very stable program at all yet) 

Any advice on how to delete the encrypted but not so encrypted folder -- ANNOYING AS HECK.

---

### Post by twizler on 2008-08-28
once you encrypt you cant delete the files -- BIG problem here -

---

### Post by twizler on 2008-08-28
CANT DELETE folders even if they are unencrypted. __
I ended up having to boot to a ubuntu CD -- then click option to not effect this computer -- go to terminal off of the CD -- mount the hard drive -- then as root went to -- media/disk/home/Desktop and removed the un-deletable files. PAIN -- in the rump if you ask me

---

