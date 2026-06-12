---
title: "Network traffic monitor in Ubuntu Unity: Please help me test it."
date: 2012-03-09
forum: Programming Talk
---

### Post by manolo on 2012-03-09
I am still using Ubuntu 10.04 but I am getting ready for 12.04
I have written a simple Python script to show network traffic in an application indicator but I can not test it because my version of python-appindicator does not include 'set_label()' method.
Could you test my script in your computer?

Please find the script as an attached file.
To test it:
  Check that you are using Ubuntu Unity
  Check that the following packages are installed:
  - python-appindicator
  - python-gtk2
  - python-gobject
  - python-gtop
  Download the script mentioned above (NetTraffic.py)
  Make the file executable
  Run it:
  - If it is in Temp directory, (in a terminal) cd Temp; ./NetTraffic.py
  - You can stop it by typing CtrlC
  Please let me know what you see in the Unity panel

I have never programmed in Python before and it is the first time I use appindicator. Any expert is welcome to improve the code.
Thank you very much!

---

### Post by r-senior on 2012-03-09
Could you edit your post and wrap the code in code tags by selecting it and using the # button just above the edit post window?

I can't test it, but would be interested to read it.

---

### Post by manolo on 2012-03-09
> **r-senior said:**
> Could you edit your post and wrap the code in code tags by selecting it and using the # button just above the edit post window?

I can't test it, but would be interested to read it.

I noticed the loss of formatting and have attached the file instead of including it in the thread.

---

### Post by klyshas on 2012-04-15
I've tested your script with 12.04 and it works. Thanks, it is exactly what I was looking for. I couldn't find any decent indicator of network traffic for Unity panel.

---

### Post by hakermania on 2012-04-15
It works for me too. Nice one :)

---

### Post by r-senior on 2012-04-15
Good job! \\:D/

Have you considered making a project for it on Launchpad and packaging it into a PPA?

---

### Post by manolo on 2012-04-15
Thank you very much klyshas, hakermania & r-senior! :-)
Could you please post a screenshot?
I wonder if it would be possible to get rid of the icon.

I am currently very busy r-senior, and I can't start a Launchpad project. Could any of you take care of it?

---

### Post by r-senior on 2012-04-15
I might have a go at packaging it. No idea how to get it to load on startup but we'll see. Do you have a Launchpad ID? Do you mind what license it uses? GPL3 ok?

---

### Post by manolo on 2012-04-16
That would be wonderful r-senior, thank you!
Yes I have a Launchpad ID:
[https://launchpad.net/~glesialo]("https://launchpad.net/~glesialo")

It is very easy to load the script on start up:
You need to write a desktop file like this: {
[Desktop Entry]
GenericName=Network traffic indicator
Name=Network traffic indicator
Name[en]=Network traffic indicator
Comment=Shows download/upload traffic in panel
Comment[en]=Shows download/upload traffic in panel
Name[es]=Indicador de tráfico de red
Comment[es]=Muestra tráfico de subida y bajada en el panel
Encoding=UTF-8
Exec=NetTraffic.py
Categories=GNOME;Utility;
Type=Application
Terminal=false
Icon=network-transmit-receive
}

The line 'Exec=NetTraffic.py' assumes that the file is in a $PATH directory, if it is not you should include the full path.
You should drop the desktop file in directory '/etc/xdg/autostart' if you want the script to run for every user. To start it for just a particular user you want the desktop file in '$HOME/.config/autostart'.
I have never done any distribution packaging but I guess you should include dependencies. The script needs the following packages:
_ python-appindicator
_ python-gtk2
_ python-gobject
_ python-gtop

Best regards,
Manolo.

P.S. GPL3 license is all right :-)

---

### Post by r-senior on 2012-04-16
OK, I've created a Launchpad project and uploaded the code (with the licenses attached and organised into a packageable structure).

[https://launchpad.net/nettraffic](https://launchpad.net/nettraffic)

I've not added the packaging stuff but I'll try and do that toward the end of this week.

---

### Post by manolo on 2012-04-16
> **r-senior said:**
> ok, i've created a launchpad project and uploaded the code (with the licenses attached and organised into a packageable structure).

[https://launchpad.net/nettraffic](https://launchpad.net/nettraffic)

i've not added the packaging stuff but i'll try and do that toward the end of this week.

:p

---

### Post by giva182 on 2012-05-14
Great! Thanks!

---

### Post by manolo on 2012-05-15
> **giva182 said:**
> Great! Thanks!

You are welcome.
I have installed Ubuntu 12.04 (In an external disk) and I have, finally, had a chance to see it working: I was a bit disappointed because the font used in the panel has variable character width making the string of net traffic information's length change with values. It is a pity because I had written the program so that the number of characters remains always constant :-(

If I finally update my distro to 12.04, I won't need nettraffic because I'll use 'gnome classic no effects' as desktop.

Saludos

---

