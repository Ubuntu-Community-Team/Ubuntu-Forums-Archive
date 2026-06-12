---
title: "Replace Office Profile - Where can I see the folder?"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by 171742 on 2014-04-02
Hi,

I try to find this to replace my OO profile to Libre Office:

[https://wiki.documentfoundation.org/Documentation/UserProfile#The_LibreOffice_User-Profile](https://wiki.documentfoundation.org/Documentation/UserProfile#The_LibreOffice_User-Profile)

is this possible graphically? And if not, how to do it in the terminal?


Thanks!

---

### Post by amanchesterman on 2014-04-02
Yes it should be possible to do it graphically. I have Xubuntu so I use Thunar to manage files and folders: if you are using Ubuntu you probably have Nautilus.
To find your Libre Office profile you need to see the /home/user/.config folder. (Mine is /home/john/.config, yours will be different depending on your user name.) Observe that the '.config' folder begins with a dot, so it is usually hidden when you open a graphical file manager. You have to tell Nautilus to 'show hidden files' in order to see it. (In Thunar, the command is under the 'view' menu.) Once you can see the hidden folders, you should find the 'libreoffice' folder inside the '.config' folder, and that's where your user profile is.

---

### Post by mastablasta on 2014-04-02
ctrl+h is shortcut to show hidden files in nautilus i believe. in Dolphin is alt+.

---

