---
title: "How can I install mouse curser's in Ubuntu 11.10?"
date: 2012-02-11
forum: New to Ubuntu
---

### Post by cQuinc on 2012-02-11
I am trying out Ubuntu 11.10  One of the first things I want to do is install a distinctive mouse curser to get the young kids interested in using the computer.

I don't have trouble finding or downloading the mouse curser's but I can not figure out how to install them.  

One instruction says to:

Go to **System > Preferences > Appearance**

Well,
I can not find that!  My menu's seem to be different.

Quin

---

### Post by wolfen69 on 2012-02-11
[http://askubuntu.com/questions/78888/how-to-change-the-mouse-pointer-theme](http://askubuntu.com/questions/78888/how-to-change-the-mouse-pointer-theme)

---

### Post by cQuinc on 2012-02-12
ok but how do I find [B]System > Preferences > Appearance ?
[/B]

---

### Post by wolfen69 on 2012-02-12
> **cQuinc said:**
> ok but how do I find [B]System > Preferences > Appearance ?
[/B]

There is no system>preferences>appearance in 11.10

You need to put your theme/icon files in /usr/share/icons/ or ~/.icons. Please carefully re-read the link I gave you.

---

### Post by cQuinc on 2012-02-13
I have spent a few hours on that website trying everything.  I now have a mouse theme in my download folder.  I also have the gnome-tweak-tool and I was able to change the mouse curser with the 4 options that it offers in the standard setup.  I can see how to extract the files into the /usr/share/icons/ folder but I can not get the permissions to cooperate.

I opened up a terminal window and ran gksu nautilus but when I go back to the graphical user interface and unzip the file into the icons folder it denies my permission.

HElP!!!!!!

---

### Post by 3rdalbum on 2012-02-13
> **cQuinc said:**
> I have spent a few hours on that website trying everything.  I now have a mouse theme in my download folder.  I also have the gnome-tweak-tool and I was able to change the mouse curser with the 4 options that it offers in the standard setup.  I can see how to extract the files into the /usr/share/icons/ folder but I can not get the permissions to cooperate.

I opened up a terminal window and ran gksu nautilus but when I go back to the graphical user interface and unzip the file into the icons folder it denies my permission.

HElP!!!!!!

Unzip the file first. Then drag it into the icons folder. Make sure that you are dropping INTO the root file browser.

---

### Post by stinkeye on 2012-02-13
Extract your downloaded cursor theme and place the extracted folder
in the **.icons** folder in your home directory.
Create the  **.icons** folder if there is none.
The  preceding "dot" makes the folder hidden. ctrl+h to see hidden files.

Then in the terminal run these two commands using [COLOR="darkorchid"]your cursor theme name[/COLOR], which will be the same as the extracted folder name.

```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="DarkOrchid"]ThemeName[/COLOR]"

sudo sh -c "echo '[Icon Theme]\nInherits=[COLOR="darkorchid"]ThemeName[/COLOR]' > /usr/share/icons/DMZ-White/cursor.theme"
```


You can change back to default with 
```
gsettings set org.gnome.desktop.interface cursor-theme "DMZ-White"

sudo sh -c "echo '[Icon Theme]\nInherits=DMZ-White' > /usr/share/icons/DMZ-White/cursor.theme"
```
You need to log out/in to complete.

---

### Post by cQuinc on 2012-02-13
> Unzip the file first. Then drag it into the icons folder. Make sure that you are dropping INTO the root file browser.

I believe that is exactly what I am doing but I get Permission Denied type of response.  I will try it some more today.

---

### Post by cQuinc on 2012-02-13
Stinkeye,
> Extract your downloaded cursor theme and place the extracted folder  That is the part I can not do.

> Then in the terminal run these two commands using your cursor theme name, which will be the same as the extracted folder name.

Ok I can try this instruction but it comes AFTER the unzip part and I can not unzip into the icons folder.

---

### Post by stinkeye on 2012-02-13
So you can't right click on the archive > Extract here ?
You may need to install 7zip.
Search and download in the software centre.

or

just install the extra archive formats in the terminal
```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

---

### Post by cQuinc on 2012-02-13
I have attached a screen shot of the permission notification.  This was after I had unzipped the Protozoa.tar.gz file to the desktop and then tried to drag it into the icons folder.

---

### Post by stinkeye on 2012-02-13
> **cQuinc said:**
> I have attached a screen shot of the permission notification.  This was after I had unzipped the Protozoa.tar.gz file to the desktop and then tried to drag it into the icons folder.

Open a terminal and run
```
gksudo nautilus /usr/share/icons
```
and drag and drop the folder in the window.

*** Most of the folders out side of your home directory require root permissions to write to.
Adding cursor themes or icon themes to **/usr/share/icons** will make them available to all users.

You can also just add them to **~/.icons**.
The tilde "~" symbol is short for **/home/your_username** ...eg **[COLOR="Blue"]~[/COLOR]/.icons** is the same as **[COLOR="blue"]/home/cQuinc[/COLOR]/.icons** 
If it's just a single user pc it's easier to just add to **~/.icons** because you have permissions to write to folders in your home directory and dont need to open nautilus as root.

---

### Post by cQuinc on 2012-02-13
THANKS!  I GOT IT TO WORK !!!

This was a great little project to help me get to know Ubuntu and it also will be a hit with the kids that I work with on the computer.

I got a lot more to learn but I will take it a step at a time.  I'm pretty happy about it.

---

### Post by stinkeye on 2012-02-13
> **cQuinc said:**
> THANKS!  I GOT IT TO WORK !!!

This was a great little project to help me get to know Ubuntu and it also will be a hit with the kids that I work with on the computer.

I got a lot more to learn but I will take it a step at a time.  I'm pretty happy about it.
Good.
Glad I could help.
:)

**P.S** To understand the tilde shortcut and file system a bit better
open a terminal and enter
```
nautilus ~/.config
```
then with the file browser window in focus hit ctrl+l to show the full path.
Now click on File System in the left pane to show your root directory "/"  which contains all directories and files.
In the right window, click on home then "your_user_name" and your back in your home folder.

---

