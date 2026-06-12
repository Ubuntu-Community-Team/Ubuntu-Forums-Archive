---
title: "I do not understand how to install WineHQ"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by aaron9 on 2013-09-13
Hi all...I have just installed Ubuntu with a dual boot on my Toshibe Laptop... I tried to install Pokerstars but it will not install. Will WineHQ help ? I tried to install Wine but the Ubuntu Software Center does not look like the instructions " **Ubuntu Software  Center** and selecting **Edit->Software Sources****. Choose the [B]Other  Software** tab and click **Add** "   .

there is no Edit or Software Sources in the Ubuntu Software Center.

I[/B] tried the Wine forum, but the language is Greek to me. :confused:

---

### Post by ibjsb4 on 2013-09-13
Try installing it in terminal.

```
sudo apt-get install wine
```

You may also be interested in "Play On Linux"

[https://help.ubuntu.com/community/PlayOnLinux](https://help.ubuntu.com/community/PlayOnLinux)

```
sudo apt-get install playonlinux
```

---

### Post by grahammechanical on 2013-09-14
We do not install wine HQ. We can install Wine easily through the Ubuntu Software Centre buy seaching for wine and installing either Microsoft Windows Compatibility Layer (meta-package) wine or Wine Windows Program Loader Microsoft Windows Compatibility Layer (Binary emulator and Library). I usually choose the first one. This will install the most stable version of wine availbale for Ubuntu users.

THe WineHQ web site has later versions of wine, even a beta version but we install them through a PPA. The instructions are on the WineHQ web site. I suggest that you install wine through the Ubuntu Software Centre that will get you wine 1.4 which is the same as on the wine web site.

If you want to install the wine 1.5 beta version then you need to install the PPA (personal Package Archive) follow the instructions

Load the Ubuntu Software Centre. Move the mouse to the left side of the top panel. And some menu headers will appear. click on Edit and a drop down menu will appear and at the bottom you will see Software Sources. Click on it. Now it all depends on which version of Ubuntu you are using. You do not tell us. So, I will tell you what I see in 13.04/13.10. A dialog will appear called Software and Updates. Click on the Other Software tab. Then click Add. You will then see the dialog box shown in the wine web site page. It is called Enter the complete APT line of the Repository that you want to add as source. In the panel labelled APT type ppa:ubuntu-wine/ppa as shown on the web site. Click Add Source. Now you need to run Update Manager.

We can also get access to Software and Updates through System Settings. We can also install PPAs and packages through the terminal with certain commands.

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

followed by
```
sudo apt-get update
```
```
sudo apt-get install wine1.5
```

This is why I say it is easier to install through the Ubuntu Software Centre by searching for wine. The whole point of Ubuntu is to make things easier.

Regards.

---

