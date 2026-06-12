---
title: "tuxboot"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by pjmlmas on 2013-11-24
I would like clonezilla on a usb drive.
I was instructed to download tuxboot.
I was also told there a deb file.
What are the actually correct steps to get clonezilla on a usb drive.
Hopefully, if possible, steps that do not include the following:
> Or if you can handle a GLIBC 2.4 dependency:

qt4-x11.7z [http://launchpad.net/tuxboot/trunk/trunk/+download/qt4-x11.7z](http://launchpad.net/tuxboot/trunk/trunk/+download/qt4-x11.7z)


Thanks

---

### Post by heir4c on 2013-11-25
Open a terminal and type:
```
sudo apt-add-repository ppa:thomas.tsai/ubuntu-tuxboot
```
click Enter.
Your password will be asked. You will see nothing when you type now your password, that is normal, you have to type it "blind".

After that type:
```
sudo apt-get update
```
Click Enter and wait a moment to let the computer do his job.
After you got back the "prompt" type:
```
sudo apt-get install tuxboot
```
Now you can find tuxboot via the Dash (UbuntuLogo in the top left).


Or (If the method above don't work):


Download from here:
[http://sourceforge.net/projects/tuxboot/files/0.6/Linux/](http://sourceforge.net/projects/tuxboot/files/0.6/Linux/)
Than go to the Download folder. And there you see this:
[IMG]http://i.imgur.com/YFs5ixA.png[/IMG]

Rightclick on it and check the Permissions Tab. Below you check the box next where you read something about 'make executable' (I have not a English version).
Close the window and Doubleclick on the icon. Tuxboot will start.

[IMG]http://i.imgur.com/cQNKF8R.png[/IMG]

At the bottom of the window you will see your usb drive if you plug it in. Click OK. It will download Clonezilla automatic and install it on the usb.


If you want, you can move the executable file to your Home folder. 
That can you do like this:
Rightclick on the executable and choose to move it to.... and choose from the window your home folder.

---

