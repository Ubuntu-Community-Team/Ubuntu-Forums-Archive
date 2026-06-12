---
title: "executable"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-09-02
How can i make any python programme (.py) executable so that i just click on it and it runs.
I tried making it executable from the permission window and also by chmode, i added the shebang but still i have to execute it through the terminal or through idle.
What should i do ?

---

### Post by nerdtron on 2013-09-02
You want to double click it on the file manager so that it runs?
I think there is a setting in Nautilus about it's behavior when opening executable files.
I can't confirm exactly where (I'm in xubuntu right now) but you might want to check the preferences of Nautilus.

---

### Post by 3dmatrix on 2013-09-02
I just wish to click on its icon (where ever it is) and run it. As we do with any other application. I do not want to change rules for all .py files.

---

### Post by 3dmatrix on 2013-09-02
If i execute it through a terminal, i have to keep the terminal open, else on closing it the programme also closes.

---

### Post by scbingham on 2013-09-02
To run from terminal & then close terminal leaving the command running, just type: command.py &

I have icons on my desktop for programs, settings for the icons are: under Basic, 'command' is the full path name & under Permissions the 'Allow executing file as program' is ticked.

Execute permissions for the programs are also set.

Hope this helps.

Edit: You didn't mention which desktop you're using, I use Unity.

---

### Post by 3dmatrix on 2013-09-02
I use Gnome 3. I wish to execute those programmes just as exe files are executed in windows.
Can we do that ? Without opening the terminal, typing etc.

---

### Post by Crusty Old Fart on 2013-09-03
Create a "launcher" for it.

---

### Post by vasa1 on 2013-09-03
> **Crusty Old Fart said:**
> Create a "launcher" for it.
Maybe these links will help:
[http://askubuntu.com/a/282187/25656](http://askubuntu.com/a/282187/25656)
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

---

### Post by Crusty Old Fart on 2013-09-03
> **vasa1 said:**
> Maybe these links will help:
[http://askubuntu.com/a/282187/25656](http://askubuntu.com/a/282187/25656)
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
Thanks for the cover, Vasa.
Still running Lucid here. Launchers are so much easier than they are in Unity.
The more I see of Unity, the more I want to stay as far away from it as I can.
Fortunately, we still have Xubuntu.

Best wishes,

Crusty

---

### Post by vasa1 on 2013-09-03
> **Crusty Old Fart said:**
> ...
Fortunately, we still have Xubuntu.
...
I'm using a "hybrid" of Lubuntu 13.04 and Thunar/Xfce. It doesn't make my "non-GPU" laptop all sweaty ;)

---

### Post by 3dmatrix on 2013-09-04
Yes after making the launcher it is working.
Thanks  :)
I did not know how to make it, thanks for the info.

---

