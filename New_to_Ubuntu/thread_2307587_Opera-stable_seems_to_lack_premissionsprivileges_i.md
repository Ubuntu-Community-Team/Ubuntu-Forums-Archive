---
title: "Opera-stable seems to lack premissions/privileges in 14.04"
date: 2015-12-26
forum: New to Ubuntu
---

### Post by kiklo on 2015-12-26
So I installed the official version of Opera named "opera-stable" in the Ubuntu Software Center.


[LIST]
[*]When I run it from launcher, it launches twice and displays a message (Translated to English by myself, may not be perfect):
[/LIST]
> Cannot read user configuration files. Some features may not be
available and any changes performed this session will not be saved.
 
Here's an image:
[ATTACH=CONFIG]266388[/ATTACH]



[LIST]
[*]When I run it from terminal, it throws these errors:
[/LIST]
```
[1226/165646:ERROR:desktop_window_tree_host_x11.cc(889)] Not implemented reached in virtual void views::DesktopWindowTreeHostX11::InitModalType(ui::ModalType)
[1226/165646:ERROR:download_history_importer.cc(50)] Failed to read a tag or its data.
[1226/165646:ERROR:migration_assistant.cc(87)] Could not open file: wand.dat
[1226/165646:ERROR:extensions_importer.cc(58)] Reading widgets.dat failed
```


[LIST]
[*]**Running it with the "sudo" command works perfectly well**, and saves all user settings. Though from what I read so far, having to run a browser with sudo is not a good thing.
[/LIST]

Now, I'm a newbie, but I followed [this]("http://askubuntu.com/questions/366919/ubuntu-opera-works-only-with-root-rigths") ask ubuntu post which recommends:
```
sudo chown -R group_name.user_name ~/.opera
```
and indeed I seem to be the owner of all the folders and subfolders that opera uses (I can't remember the command I used to check that) but it still doesn't work.

I also tried loads of other things like updating, upgrading, apt-mark hold command, reinstalling opera (both using the software center and manually unpacking .deb file) and maybe something more. As I said, I'm a newbie, I only use Ubuntu for 2 days, I just want to get Opera up and running properly, but I spent those 2 days looking for an answer.
Any idea?

---

### Post by deadflowr on 2015-12-26
Try removing the configuration folder.
(The ~/.opera folder)
You can either remove with a terminal command, or open the FIles program and locate the folder and right click move to Trash.

If the Folder does not show, which might happen since it is what is known as a hiodden folder, simply press ctrl + h, to view hidden files and folders.

---

### Post by kiklo on 2015-12-26
Thanks, but that only made matters worse - more errors when launching from terminal.

---

### Post by claracc on 2015-12-27
I am running 14.04 and I have not Opera browser in software center neither in synaptic package manager, what version have you installed and in what way?

Perhaps you want to try the last opera browswer version, for it you have to install the third party ppa for opera browser. Please see [http://www.ubuntuupdates.org/ppa/opera](http://www.ubuntuupdates.org/ppa/opera)

---

### Post by kiklo on 2015-12-28
I reinstalled Ubuntu and installed Opera from opera.com and it works OK. I must've done something terribly wrong to cause that. It works now, so, yeah.

---

### Post by Frogs Hair on 2015-12-29
Opening a web browser with sudo  creates a profile only accessible with elevated permissions and is not easy to reverse because the application looks for a path to a folder it can't access.

---

