---
title: "LibreOffice Links Break when dragged to desktop"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-01
I have a gnome desktop and menus and dont run unity.

Can someone explain to me why when I drag LibreOffice Icons to the desktop, and then right mouse click on them and click properties, it tells me that they are broken links.

I can open them in the 'Office' menu no problem, and have no problem with any other of my programs in any other groups, and can drag them to the desktop without issue, so why is LibreOffice misbehaving?

---

### Post by Senior_Buckethead on 2012-06-04
Bump

---

### Post by Senior_Buckethead on 2012-06-04
Bump

---

### Post by the.phantom on 2012-06-04
no answers here, sorry
but it does the same thing to me !
12.04 gnome

---

### Post by Senior_Buckethead on 2012-06-04
duoh!

---

### Post by Senior_Buckethead on 2012-06-06
Bump

---

### Post by Ubun2to on 2012-06-06
Sometimes this happens to me. I have to right click, go to properties, click the Permissions tab, and select "Allow executing file as a program" to get it to work. The Drawing, Database, and Formula apps never work as desktop icons or pinned Unity launcher shortcuts. I have no idea why.

---

### Post by Senior_Buckethead on 2012-06-06
This thread reminds me of a cartoon I once read of a man who was shouting at his computer 'Why!' when he was looking at a forum for an answer to a problem, and the only post was of another person, who had asked the same question, ten years earlier, with no answers.

---

### Post by Senior_Buckethead on 2012-06-07
Can I create new shortcuts in the ~/Desktop directory? if so, where would I look to aim the symbolic links?

---

### Post by Azdour on 2012-06-08
Hi,

It looks like when you drag the libreoffice application to the desktop it creates a symbolic link to a directory that does not exist. In your Desktop directory you will see the link goes to:

```

../../lib/libreoffice/share/xdg/

```

And using 'cd' you cannot get to this directory. Gnome Classic under 12.04 must have a bug when drag and dropping applications from the menus to the desktop.

Furthermore if you create the correct symbolic link yourself to /usr/lib/libreoffice/share/xdg/writer.desktop you cannot launch it because you get the message:

```

Untrusted application launcher

```

On Ubuntu 10.04 it creates the correct link when you have dragged it to your desktop, but you get the same "untrusted" error dialog and it will not launch.

So I am guessing that the only option left as you have said is to create your own desktop file. There may be an easier way to do this, but I ended up having to do it this way via terminal for librewriter:

```

cd /usr/lib/libreoffice/share/xdg/
sudo cp writer.desktop ~/Desktop
cd ~/Desktop
sudo chown fred:fred writer.desktop
chmod 755 writer.desktop

```

Now I have a launcher on my desktop that correctly launches librewriter.

---

### Post by Senior_Buckethead on 2012-06-08
Thanks for the insight. You know its the wierdest thing since everything else drags to the desktop (I wish I could send you a screenshot, but I wouldnt have a clue how to), except Libre Office. Your right about the directory. From properties of a dragged icon it is:
```

../../lib/libreoffice/share/xdg/draw.desktop
[CODE/]
Your right about the fix, it does work. Thank you.

You know, its getting late here, and you have sudo chown fred:fred I almost typed in 
[CODE]
sudo chown fried:chicken

```
perhaps me thinks its time for bed.

---

### Post by Azdour on 2012-06-08
Hi,

It's either time for bed or food :) Glad that its working. Could you mark this thread as solved, thanks.

---

### Post by BrianH_1 on 2012-07-26
> **Azdour said:**
> Hi,

It looks like when you drag the libreoffice application to the desktop it creates a symbolic link to a directory that does not exist. In your Desktop directory you will see the link goes to:

```

../../lib/libreoffice/share/xdg/

```

And using 'cd' you cannot get to this directory. Gnome Classic under 12.04 must have a bug when drag and dropping applications from the menus to the desktop.

Furthermore if you create the correct symbolic link yourself to /usr/lib/libreoffice/share/xdg/writer.desktop you cannot launch it because you get the message:

```

Untrusted application launcher

```

On Ubuntu 10.04 it creates the correct link when you have dragged it to your desktop, but you get the same "untrusted" error dialog and it will not launch.

So I am guessing that the only option left as you have said is to create your own desktop file. There may be an easier way to do this, but I ended up having to do it this way via terminal for librewriter:

```

cd /usr/lib/libreoffice/share/xdg/
sudo cp writer.desktop ~/Desktop
cd ~/Desktop
sudo chown fred:fred writer.desktop
chmod 755 writer.desktop

```

Now I have a launcher on my desktop that correctly launches librewriter.

This worked perfectly for Libreoffice - Thanks
I have the same problem with screenshot
What is the appropriate code / modification of the above code for screenshot?
Thanks

---

