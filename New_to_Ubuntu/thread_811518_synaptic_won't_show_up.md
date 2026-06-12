---
title: "synaptic won't show up"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Falc7 on 2008-05-29
I noticed that although synpatic is listed in the main menu as being displayed, it isen't actually displayed in system -> administration, how can i show it?

Another thing is that i am trying to set up a different user account for my mum and brother on the home computer, I am trying to install the future looks theme. For which i have to install emerald, but i get this error message.
mum@mj-desktop:~$ sudo aptitude install emerald
[sudo] password for mum: 
mum is not in the sudoers file.  This incident will be reported.
EDit:fixed

---

### Post by drs305 on 2008-05-29
The easiest first step would be to try to reinstall synaptic:
```
sudo apt-get install --reinstall synaptic
```

If that doesn't work we can look deeper.

Second part:
Are you trying this while logged in as 'mum'? The first user (you) has the ability to use sudo because he/she has administrative powers. But not every user can use sudo unless they are made part of the admin group. Otherwise every user could use the 'sudo' command to do anything they wanted to any part of the computer. I think she (mum) may be able to install some things for herself but she can't use sudo. You can go back to your profile and install it for everyone using sudo.

In System, Admin, Users and Groups, you CAN give other users admin privileges (unlock and edit users) but it's generally not done.

---

### Post by Falc7 on 2008-05-29
Yep, synaptic is fine now, thanks!

---

### Post by Falc7 on 2008-05-29
I have a few small questions and i didn't really think it was worth opening a new topic for them

1.I don't seem to have my deleted items showing on the panel at the bottom, so i right clicked, add to panel, then found the deleted items and tried to add it. Nothing happens. How can i bring it back?

2.How can i make a shortcut to my home folder on the desktop?

3. My list of open windows (in this case 2 firefox windows, seem to be very squashed into a small area in the bottom panel, even though there is a lot of space to the left of them on the panel, how can i make them spread themselves out?
edit: re part 3. I have now somehow managed to delete the list of open windows, i have several FFs open, but they do not show up at the bottom

---

### Post by drs305 on 2008-05-29
> **Falc7 said:**
> 
2.How can i make a shortcut to my home folder on the desktop?

With your desktop showing, System, Places, click and hold 'Home Folder', drag it to the desktop and release. It will create an icon for your home folder there.

> **Falc7 said:**
> 
1.I don't seem to have my deleted items showing on the panel at the bottom, so i right clicked, add to panel, then found the deleted items and tried to add it. Nothing happens. How can i bring it back?



I don't know why it won't let you put the trash icon (if that's what you mean by 'deleted items) in the panel (Trash), but you can put a trash icon on the desktop with:
```

 gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible 'true'

```

As for #3, you should be able to restore the open windows feature of the panel by right clicking and selecting Add to Panel, Window List.

---

### Post by Falc7 on 2008-05-31
> **drs305 said:**
> With your desktop showing, System, Places, click and hold 'Home Folder', drag it to the desktop and release. It will create an icon for your home folder there.

I get this error message
Error stating file '/home/mum/.gvfs': Transport endpoint is not connected


Thanks number 2 and 3 are fine :)

---

### Post by drs305 on 2008-05-31
> **Falc7 said:**
> I get this error message
Error stating file '/home/mum/.gvfs': Transport endpoint is not connected
Thanks number 2 and 3 are fine :)

I'm easily confused by our numbering of the questions, so I'm not sure which problem is unsolved. If it is putting a home folder on your desktop, run this command:

```
 gconftool-2 --type bool --set /apps/nautilus/desktop/home_icon_visible 'true'
```

To remove/hide it from the Desktop, change the value to 'false'.

If that wasn't the problem, just come on back! If everything is solved, please mark this thread solved with the link under 'Thread Tools' at the top right of the first post.

---

