---
title: "Tweaking Gnome 3.4.1 (in Ubuntu 12.04.1 LTS)"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by benbrockn on 2012-11-27
So. I quickly got tired of Unity and at first wanted Gnome 2, but instead, I came across Gnome 3.4.1 and found some cool things like Gnome Tweak Tool and Gnome Shell Extensions.

I'm still trying to tweak Gnome and I was wondering if any of these are possible:


[LIST=1]
[*]The Battery Icon is way too small. I know with Gnome Tweak Tool I can make the text larger (text scaling factor) which makes the icon larger, but I do not want to do this. I like the text size as is, I just want the battery icon bigger. (it would also be great if there where a battery % next to the icon as well)
[*]Unlike Unity and Gnome 2, I noticed that Gnome 3 did not have minimize or maximize buttons. How do I get them back?
[*]I want to add shortcuts to the desktop (for instance Terminal) how do I do that?
[*]I know in MS Windows you can right-click on a file/folder and select properties to get a lot of useful info on that file/folder. Is there any way to find out file/folder properties? Also, what was very helpful with that is that it gave you the absolute pathname to said file/folder. This would be extremely helpful. (I don't know where the Terminal app resides in Ubuntu, but if I could find out that would help me create a shortcut to it on the desktop).
[*]I found out that by installing Gnome 3, it also installs 2 versions of Gnome Classic. I see these when I log out and can select which shell to log in to. I made myself admin, but I want a standard user on here that can ONLY access the Gnome 3 shell when they log in instead of having the option for Unity, Unity 2D, Gnome Classic 1, and Gnome Classic 2. Is there a way to do this?
[/LIST]

Thanks for your help. I am currently running all this on the Live CD and any time I shut it off I have to re-run everything, but it's nice to tweak before I install. Currently, I downloaded all the .deb packages through Ubuntu Software Center/Terminal which installs them to /var/cache/apt/archives and then I copied all of them to my laptop harddrive and when I have to restart Ubuntu I am just installing all of those packages again using ```
sudo dpkg -i *.deb
```

So yeah, it's a process but it works. Anyway, thanks in advance if any of these questions can be answered!

---

### Post by Cheesemill on 2012-11-27
> **benbrockn said:**
> Unlike Unity and Gnome 2, I noticed that Gnome 3 did not have minimize or maximize buttons. How do I get them back?
Use gnome-tweak-tool. Go to 'Shell > Arrangement of buttons on the titlebar' and select 'All'.
> I know in MS Windows you can right-click on a file/folder and select properties to get a lot of useful info on that file/folder. Is there any way to find out file/folder properties? Also, what was very helpful with that is that it gave you the absolute pathname to said file/folder. This would be extremely helpful. (I don't know where the Terminal app resides in Ubuntu, but if I could find out that would help me create a shortcut to it on the desktop).It's just the same as Windows, right-click on a file and select 'Properties'.
The full path is given on the first tab.

The default Ubuntu terminal application is called gnome-terminal. To find out where it lives you can use the which command:
```
rob@ubuntu:~$ which gnome-terminal
/usr/bin/gnome-terminal
```> I found out that by installing Gnome 3, it also installs 2 versions of Gnome Classic. I see these when I log out and can select which shell to log in to. I made myself admin, but I want a standard user on here that can ONLY access the Gnome 3 shell when they log in instead of having the option for Unity, Unity 2D, Gnome Classic 1, and Gnome Classic 2. Is there a way to do this?You can delete the unwanted session profiles. Hit ALT+F2 and enter 'gksudo nautilus' to open a file browser window with root privileges.
Then browse to /usr/share/xsessions and delete your unwanted session profiles.
This will remove the sessions for ***all*** users.

---

### Post by benbrockn on 2012-11-27
Thanks Cheesemill. Yeah I have no idea why I didn't see properties before, oh well.

I haven't tried the session profiles tip yet, but the other advice worked.

Also, I don't think my laptop fan is working. It's normally quiet but I could at least feel it blowing. My laptop is getting quite warm and I'm concerned. How can I check if it is working or be able to adjust fan speed?

**EDIT: Cheesemill's tip on the session profiles worked! An added bonus is that I'm using the Live USB version and when you hit "Try Ubuntu" it no longer logs you into "Ubuntu" automatically because I deleted the Ubuntu session (Unity). Instead, it pulls up the log in screen where I can log in (which is what I wanted anyway!)**

---

### Post by benbrockn on 2012-11-28
Anyone else have any ideas?

---

### Post by benbrockn on 2012-11-28
So I've moved on up to Ubuntu 12.04 LTS on a Live USB (instead of the CD) with a persistence  file of 2.5 GB (because I could) running GNOME 3.4.1 instead of Unity.

I love it!! I've customized it to my heart's content.

But  weird things randomly happen... (I haven't changed anything to cause  these occurrences and they go away after I reboot, but they sometimes  re-appear)


[LIST]
[*]One time my touchpad on my laptop suddenly stopped working (I had to use my wireless mouse instead)
[*]Another time my wireless card stopped working (it said there were no connections when there obviously was one)
[*]Applications tab (from gnome-tweak-tool) decided to freeze
[/LIST]


Are these normal for Ubuntu in general? Is this some side effect of using a Live USB (or CD)?

Just curious...

**EDIT: Also, any idea for the Battery Icon? Other than this list in this reply, my other questions were answered, thanks.**

---

