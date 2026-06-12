---
title: "Saving file to desktop - ?"
date: 2022-05-11
forum: New to Ubuntu
---

### Post by jonfisher on 2022-05-11
I'm using Ubuntu 22.04 lts.  In an attempt to save an image file to the desktop, since it's not available as a choice in files on the left, I choose to save image then I navigate to other locations->computer->home->my name->desktop and save the file.  Yet it doesn't show up on the desktop - ?

---

### Post by ben-mo1 on 2022-05-12
The following solution is for gnome users only, which is the default desktop environment in Ubuntu. If you don't know what a desktop environment is and/or have never heard of gnome, you are most likely using it.
Try opening your terminal and running [FONT=courier new]sudo apt install gnome-tweaks[/FONT] (this requires the administrator's password).
You should see a new app called "Tweaks". If you don't see it, run [FONT=courier new]gnome-tweaks & [/FONT] (don't forget the whitespace at the end).
Anyway, this new app should list an extension called "Dektop icons". Make sure it's enabled. If you don't see the extension, run
[FONT=courier new]sudo apt install gnome-shell-extension-desktop-icons[FONT=system] and restarting the tweaks app.
[I]Handy trick: you can paste command in the terminal by pressing ctrl+shift+v
[/I][/FONT][/FONT]

---

### Post by yancek on 2022-05-12
This was a deliberate decision by the developers of Gnome/Nautilus explained at the link below.

[https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28](https://www.omgubuntu.co.uk/2018/01/gnome-desktop-icons-removed-3-28)

Another method folr putting icons on the Desktop with Gnome/Nautilus at the link below..  It is specifically discussing 20.04 so I'm not sure it will work with 22.04.  I'd suggest trying the gnome-tweaks option suggested above first.

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by Claus7 on 2022-05-12
Hello,

> **jonfisher said:**
> I'm using Ubuntu 22.04 lts.  In an attempt to save an image file to the desktop, since it's not available as a choice in files on the left, I choose to save image then I navigate to other locations->computer->home->my name->desktop and save the file.  Yet it doesn't show up on the desktop - ?

by using wayland ubuntu, you won't be able to see the Desktop folder on the left hand side of Files (Nautilus). It is supposed to be an open issue for some time now. If you are using xorg ubuntu, then you will be able to see the Desktop folder by opening dfonf editor (you can install dconf via synaptic) and set
/org/gnome/desktop/background/show-desktop-icons to true
if not already enabled. By doing so, you will be able to see right away the Desktop folder when opening Files.

Still with wayland, I do not know if you manage to save your file under desktop. It seems that you tried to bypass that but it did not work. Try the options offered here and check if any of these solve your issue. If you still cannot save a file on Desktop you could try to use nemo to handle your desktop, yet I do not recommend it, since you will have to tamper more with your system:
[https://ubuntuforums.org/showthread.php?t=2468893&p=14066854](https://ubuntuforums.org/showthread.php?t=2468893&p=14066854)

Regards!

---

### Post by mIk3_08 on 2022-05-12
> **jonfisher said:**
> I'm using Ubuntu 22.04 lts.  In an attempt to save an image file to the desktop, since it's not available as a choice in files on the left, I choose to save image then I navigate to other locations->computer->home->my name->desktop and save the file.  Yet it doesn't show up on the desktop - ? Please run this command in your terminal. To access terminal just press both ctrl and alt + t or just find it in your installed application in your Ubuntu Desktop. Regards and Cheers.
```
echo "This is a test" >~/Desktop/yourdesktoptextfile.txt
```

---

### Post by jonfisher on 2022-05-12
hmm, 
Can't seem to find Desktop icons
Perhaps tell me which of these it's under - I've looked several times

---

### Post by deadflowr on 2022-05-12
Extensions are handled by the Extensions app not Tweaks.
Though I also recall some extension features might be accessible in the System Settings > Appearance setting.

I think Extensions app should be installed.

---

### Post by SeijiSensei on 2022-05-12
In Kubuntu, saving things to the desktop is built-in by default.

---

### Post by ajgreeny on 2022-05-12
> **SeijiSensei said:**
> In Kubuntu, saving things to the desktop is built-in by default.
Similarly in Xubuntu though it is not something I do very much.

As far as I'm concerned gnome seems to enjoy making the use of a computer GUI more and more difficult.
I presume users who have stuck with it since Ubuntu changed from gnome-2 to Unity, then to the current gnome default, have managed to instill the needed methods into their way of working; I tried but it was just too annoying and frustrating for me, hence my use of Xubuntu.

Thank goodness for the choices that the Ubuntu family of OSs gives us!

---

### Post by Dennis N on 2022-05-12
The extension to allow icons on the Desktop is called "Desktop Icons NG" and is installed by default in Ubuntu 22.04. It appears under the "System Extensions" in Extensions Manager. See attached image, yellow arrow. It should be ON in order for icons to appear on your Desktop. By default, icons of new items appear in the lower right corner of the screen. Maybe you aren't looking there. You can change this behavior in the Settings > Appearance dialog.

The best tool to handle extensions is now "Extensions Manager". It allows you to search for and install extensions - something that "Extensions" did not do. It's NOT installed by default, but is in the Ubuntu repository as gnome-shell-extension-manager and also as a Flatpak package.

---

### Post by grahammechanical on 2022-05-13
Are you looking in the right place? On Ubuntu 20.04 files saved in the Desktop folder appear at the top left of the desktop. In 22.04 files save to the Desktop folder appear in the bottom right of the desktop. The Home folder on the desktop is also put at the bottom right by default in 22.04.

In System Settings>Appearance>Position of New Icons we get four options of where we want desktop icons (including icons for files stored in the Desktop folder) to be put. I am on 22.04 right now and I have not found any problem saving a file to the desktop, But it does appear in a place we are not expecting it to appear. It is a bit of a shock not to see the file icon at the top right.

Regards

---

