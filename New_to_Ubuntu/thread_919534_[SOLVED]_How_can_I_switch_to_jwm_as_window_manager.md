---
title: "[SOLVED] How can I switch to jwm as window manager+desktop environment?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by KIAaze on 2008-09-14
Hi,

I tested puppy linux recently and was amazed by how light it was, while remaining very user-friendly.
However, I don't want to switch distros completely.
So I'm trying to run jwm with Ubuntu.

I installed openbox and jwm and can now select openbox as session at login time and then launch jwm (and ratpoison which I'm using right now. Horrible. ^^) by doing right-click->Desktop->Window managers->jwm.

But how can I add "jwm" to the session options at login?

I already tried "sudo dpkg-reconfigure gdm", but I still only get the choice between gdm and kdm.

edit: I think I found something:
[http://ubuntuforums.org/showthread.php?t=2920](http://ubuntuforums.org/showthread.php?t=2920)
[http://www.jpberlin.de/st.pofahl/html/science-and-software/Gnu-Linux/Window-manager.html](http://www.jpberlin.de/st.pofahl/html/science-and-software/Gnu-Linux/Window-manager.html)

---

### Post by urukrama on 2008-09-14
You'll have to create a new session. As root, create a new text file in /usr/share/xsessions:

```
sudo *text_editor_of your_choice* /usr/share/xsessions/jwm.desktop
```

Add the following to it:

```
[Desktop Entry]
Encoding=UTF-8
Name=Jwm
Comment=Log in using Jwm
**Exec=/usr/bin/jwm**
Icon=
Type=XSession
```

Make sure the Exec line points to the correct location. Jwm is most likely either installed in /usr/bin/ or in /usr/local/bin. To find out type "whereis jwm" in a terminal and adjust the above line appropriately.

Save the file, and make it executable: 

```
sudo chmod +x /usr/share/xsessions/jwm.desktop
```

Logout and log back in, and when GDM appears you should see the JWM session. If it doesn't try and restart X (press Ctrl+Alt+Backspace).

---

### Post by KIAaze on 2008-09-14
Thanks, it's working.
The "chmod +x" isn't even necessary.
All I had to do was add the .desktop entry in /usr/share/xsessions.

Actually, I went a little crazy today and installed a whole bunch of window managers:
```
[16][/usr/share/xsessions]$  ls
aewm++.desktop         Fvwm.desktop           openbox-kde.desktop
blackbox.desktop       gnome.desktop          pekwm.desktop
e-gnome.desktop        IceWM.desktop          ratpoison.desktop
e-kde.desktop          jwm.desktop            ssh.desktop
enlightenment.desktop  kde.desktop            twm.desktop
fluxbox.desktop        openbox.desktop        xfce4.desktop
fvwm-crystal.desktop   openbox-gnome.desktop

```
:D

I'm not sure which one I'll keep by default yet.
JWM and the *box ones are really light on the RAM, but I miss the easy shortcut creation from Gnome.
Any suggestions?

How can I get JWM easily configured like in puppy linux with desktop icons?

Note:
When not using Gnome or KDE, my wifi doesn't work. I solved this by simply running "nm-applet" from command-line. ;)

---

### Post by kk0sse54 on 2008-09-14
For having a desktop like the traditional sense where you can place things such as shortcuts on it  you can try installing idesk

---

### Post by KIAaze on 2008-09-16
Thanks for the tip about idesk. However, it doesn't seem to be straightforward to use since it requires writing .lnk files to get more icons. I was looking more for something where I can just click around to get a new launcher.
But it might still come in handy some day. :roll:

I still haven't chosen a new default WM, but I'm marking the thread as solved since I'm now able to add any kind of WM session I want. :)

In the meanwhile, I started hunting down RAM eaters a bit more with a self-made script (top and system monitor are a bit too dynamic for me).
Just in case somebody else might find this useful:
```
#!/bin/bash
echo "size in kB,%mem,pid,user"
if [ $# -eq 0 ]
then
        ps -eo rss,%mem,pid,user -o comm= | sort -k1 -n -r
else
        for prog in $@;
        do
                ps -eo rss,%mem,pid,user -o comm= | grep $prog
        done
fi

```
usage:
RAMuse.sh : list all processes by RAM use
RAMuse.sh prog1 prog2 ... : list RAM use of prog1,prog2...

Perhaps I'll be able to use gnome again if I can eliminate nautilus from it... ^^

---

