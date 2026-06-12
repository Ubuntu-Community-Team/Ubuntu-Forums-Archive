---
title: "DropBox - How can I create a launcher in 12.04LTS"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by suomalainen on 2012-04-30
Ubunteros,

In 12.04LTS, how can I create a DropBox launcher that I can add to the Lancher Bar on the left of the screen?

The old way was to simply right click on empty desktop and create a launcher. Now this feature appears not to be found.

Thank you!

---

### Post by josephmills on 2012-04-30
```
sudo apt-get install nautilus-dropbox

```

also see 

[http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available](http://askubuntu.com/questions/35488/what-custom-launchers-and-unity-quicklists-are-available)

---

### Post by suomalainen on 2012-04-30
Thanks!

Just to clarify, I don't want to do the DropBox install and the syncing all the time. I don't want these features.

I would like to create a "Speed Link" to Dropbox sign on page, then logon, and do my business then log out.

I hope this clarifies my objective.

Thanks

---

### Post by SysBoot on 2012-04-30
Dropbox, once launched for the first time should run automatically it the background. Are you trying to create a shortcut to your Dropbox folder or what?

---

### Post by josephmills on 2012-04-30
> **suomalainen said:**
> Thanks!

Just to clarify, I don't want to do the DropBox install and the syncing all the time. I don't want these features.

I would like to create a "Speed Link" to Dropbox sign on page, then logon, and do my business then log out.

I hope this clarifies my objective.

Thanks

Look at 2nd part of post the ask ubuntu part I edited it

---

### Post by suomalainen on 2012-04-30
That's exactly what I don't want. Just speend link to sign on page.

---

### Post by hakermania on 2012-04-30
Please read: [http://ubuntuforums.org/showthread.php?t=1962862](http://ubuntuforums.org/showthread.php?t=1962862)

---

### Post by josephmills on 2012-04-30
yo bro the link shows you how to make "speed link" or .desktop file to wherever you like on what ever you like.
Nice link hakermania

---

### Post by suomalainen on 2012-04-30
This is for applications. what if I want to launch a web page. How is this done?

---

### Post by josephmills on 2012-04-30
> **suomalainen said:**
> This is for applications. what if I want to launch a web page. How is this done?
```
[Desktop Entry]
Name=DropedPassword
Name[fn]=oletusalbumi
Comment[fn]=laittaa tiedostot paikkaan kaikkien nähtäväksi.
Comment=put your files in a place for every one too see. 
Type=Application
Exec=xdg-open https://www.dropbox.com/login
Icon=/usr/share/icons/gnome/48x48/status/software-update-urgent.png
Terminal=false
Encoding=UTF-8
Categories=Web;
```

---

### Post by suomalainen on 2012-04-30
@josephmills,

As a test, I opened gedit and cut & paste the code you gave into said doc. Then I saved it to desktop. I right clicked and enabled execution as program.

Nothing happens. How come?

---

### Post by suomalainen on 2012-05-03
Bump,

Anyone know how to make a quick launch to Dropbox or even TunedIn?

Thank you!

---

### Post by muteXe on 2012-05-03
Isn't it far less hassle to set your browser homepage to dropbox?

then click on your browser shortcut on your desktop and hey presto....

---

### Post by suomalainen on 2012-05-03
@muteXe,

> then click on your browser shortcut on your desktop and hey presto.... 

YOu lost me here....

---

### Post by suomalainen on 2012-05-29
Simple launcher like in 10.04LTS. That's all.

Any ideas????

---

### Post by mvineetmenon on 2012-05-29
What you can do is probably, create a shell script with this entry,

`~/dropbox-dist/dropboxd`

As long as the parent terminal runs, your dropbox deamon will run. To kill the deamon you can `Ctrl+C` the terminal, and the deamon will be killed...

---

### Post by dcsoldschool53 on 2012-05-29
If you are trying to create a simple web page launcher, type in a terminal```
gnome-desktop-item-edit --create-new ~/Desktop
```This will open up a launcher for anything that you want to add to your desktop. Type in a name for launcher, like dropbox. Under the command, type```
firefox and whatever the webpage.address for dropbox is
```See attachments. I hope this helps.

---

