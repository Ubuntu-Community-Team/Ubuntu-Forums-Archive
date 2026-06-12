---
title: "How to create desktop shortcut in Ubuntu 13.10 ?"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by veeravit on 2013-10-18
I used to drag application from dash and put in the desktop to create desktop shortcut in ubuntu 13.04, but in 13.10 I can't do it. After I dragged it to the desktop, there is a message like this. 

[ATTACH=CONFIG]247046[/ATTACH]

Does anyone have a solution to solve this problem?

---

### Post by deadflowr on 2013-10-19
I think this is a bug, but not sure. Might be a feature.

Try this as a solution:
Go to the folder /usr/share/applications and find the program you want.
Then right click on it and copy.
Now go to your home folder and open up the folder Desktop.
Right click and then select paste.

See if that works.

---

### Post by veeravit on 2013-10-19
Thanks for your help, now I can access my programs. :)

---

### Post by stinkeye on 2013-10-19
> **deadflowr said:**
> I think this is a bug, but not sure. Might be a feature.

Try this as a solution:
Go to the folder /usr/share/applications and find the program you want.
Then right click on it and copy.
Now go to your home folder and open up the folder Desktop.
Right click and then select paste.

See if that works.
Your method works but something in the dash has changed.
I can no longer drag an app from the dash to gedit to view the .desktop file.
Probably something to do with the new Double-click to activate, single click to preview files.

---

### Post by deadflowr on 2013-10-19
> **stinkeye said:**
> Your method works but something in the dash has changed.
I can no longer drag an app from the dash to gedit to view the .desktop file.
Probably something to do with the new double-click to run setting in the dash.

Yeah, who knows if it's a feature or a bug.(Wait, the devs do!)
And who knows how long copying the .desktop file from the /usr/share/applications folder will work.
I figure it's a quick workaround for now.

Of course, this only works per user. As the Desktop folder is a user folder and not a system folder.

---

### Post by squakie on 2013-10-19
I posted this same problem about a week ago in the +1 forum before 13.10 became available.  I was pretty much told there that it isn't supposed to work and to just use the dash.  I told the user who replied with that response that if that is the case then having a desktop is useless.

I personally believe this is a bug.  Too many of us have always done things this way - it preserves the icon, etc..  Going through the "hoop" of creating a desktop launcher had always seemed like a waste to me if the application is already in the unity dash - just drag and drop to desktop.  I really hope that if "someone" decided it was a good idea to get rid of this functionality that they think again about it.  If it's some sort of security issue just ask for the password before allowing the drag.

I am also looking forward to a resolution to this problem and will be following this thread.

---

### Post by W7nDXAr on 2013-10-22
> **squakie said:**
> I posted this same problem about a week ago in the +1 forum before 13.10 became available.  I was pretty much told there that it isn't supposed to work and to just use the dash.  I told the user who replied with that response that if that is the case then having a desktop is useless.

I personally believe this is a bug.  Too many of us have always done things this way - it preserves the icon, etc..  Going through the "hoop" of creating a desktop launcher had always seemed like a waste to me if the application is already in the unity dash - just drag and drop to desktop.  I really hope that if "someone" decided it was a good idea to get rid of this functionality that they think again about it.  If it's some sort of security issue just ask for the password before allowing the drag.

I am also looking forward to a resolution to this problem and will be following this thread.
+1

---

### Post by mc4man on 2013-10-22
[https://bugs.launchpad.net/unity/+bug/1241972](https://bugs.launchpad.net/unity/+bug/1241972)

---

### Post by gacb on 2013-11-07
I use Cairo-Dock for my frequently used apps. The latest version has a search function.

---

### Post by deadflowr on 2013-11-07
> **gacb said:**
> I use Cairo-Dock for my frequently used apps. The latest version has a search function.

Can you drag the apps from the dock to the desktop?

Which is what the OP was looking for.

---

### Post by Rodrigo_Ribeiro on 2014-02-11
Havig the same problem.

It's a bug?

---

### Post by whitesmith on 2014-02-11
> **deadflowr said:**
> Can you drag the apps from the dock to the desktop?

Which is what the OP was looking for.On my (12.04 LTS 64-bit Gnome 3) system drag-and-drop doesn't work because of a permission denied error. But r-click followed by Copy to -> Desktop *does* work, so the problem isn't limited to a particular DE. Go figure.

---

### Post by deadflowr on 2014-02-11
> **Rodrigo_Ribeiro said:**
> Havig the same problem.

It's a bug?
It this question, or a statement?
> **whitesmith said:**
> On my (12.04 LTS 64-bit Gnome 3) system drag-and-drop doesn't work because of a permission denied error. But r-click followed by Copy to -> Desktop *does* work, so the problem isn't limited to a particular DE. Go figure.

I'm guessing you have the gnome3 ppa?

---

### Post by asus-user on 2014-02-11
> **veeravit said:**
> I used to drag application from dash and put in the desktop to create desktop shortcut in ubuntu 13.04, but in 13.10 I can't do it. After I dragged it to the desktop, there is a message like this. 

[ATTACH=CONFIG]247046[/ATTACH]

Does anyone have a solution to solve this problem?

Why don't you simply create a file with .desktop extension and customize it to run whatever you want?
usually it should contain something like:
```
[Desktop Entry]
Type=Application
Terminal=false
Name={app-name}
Exec= {path to the desired app}
Name[en_US]={app-name}
```

Of course you need to make it executable after that by running this command in terminal:

```
sudo chmod a+x ~/Desktop/{filename}.desktop
```

Try it and post if something went wrong.

---

### Post by whitesmith on 2014-02-11
> **deadflowr said:**
> It this question, or a statement?


I'm guessing you have the gnome3 ppa?Yes.

---

### Post by Aegedus on 2014-02-27
Hello,

I had about the same problem. I found as solution to change dconf setup like following :
1/ launch dconf-editor
2/ go to org-> gnome-> desktop -> background
3/ Check the option : show-desktop-icons to true.

I've got back icons, short-cuts, background pictures and right-click.

Regards,
Aegedus

Config : brand new Sony Vaio Pro 13" i7-4650U-64bits  8Gb RAM
USB live Ubuntu 13.10
Linux ubuntu 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by deadflowr on 2014-02-27
> **Aegedus said:**
> Hello,

I had about the same problem. I found as solution to change dconf setup like following :
1/ launch dconf-editor
2/ go to org-> gnome-> desktop -> background
3/ Check the option : show-desktop-icons to true.

I've got back icons, short-cuts, background pictures and right-click.


Can you drag launchers from the dash menu?
(Without getting a permission denied?)

---

### Post by pschalkx on 2014-03-27
Hi, I had the same problem, here's how I solved it:

- Using the "Files" icon in the left bar go to the folder where the executable file resides.
- Right-click on given executable and select "Create Link" 
- Copy/paste this link the desktop.

I hope it helps you guys.

Rgds,

Philip

---

### Post by pyrotheseus on 2014-03-28
You could right click it, and make a link to it, and drag that onto the desktop. Or is that only in 12.04?

---

### Post by 3rdalbum on 2014-03-28
Actually guys, you can't "Make Link" and then drag to the desktop. User can't write to /usr/bin.

However you can middle-click-drag the program to the desktop. When you release the mouse button you will be given a menu, and you choose Create Link. Easy!

---

### Post by tarakonas on 2014-06-03
this works nice from terminal

[COLOR=#000080]cp /usr/share/applications/your_app.desktop ~/Desktop
chmod 755 ~/Desktop/your_app.desktop[/COLOR]

---

### Post by monkeybrain20122 on 2014-06-03
Just put your launchers on the dock, this is what it is for. If you put something on the desktop you would have to minimize your open windows to get them out of the way in order to access the desktop, I can't see how that is more efficient that using the dock or just press super to reveal the dash. Unity is not supposed to work like xp. :)

---

### Post by Vladlenin5000 on 2014-06-03
> **monkeybrain20122 said:**
> Unity is not supposed to work like xp. :)

+1

---

