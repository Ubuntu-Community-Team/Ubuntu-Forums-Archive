---
title: "Some advice and how to create shortcut apps"
date: 2022-02-20
forum: New to Ubuntu
---

### Post by temuko on 2022-02-20
Hi ! 

Im noob and Im trying to create a shortcute to Matlab app. I have the executable in  **/usr/local/MATLAB/R2021b/bin **and i want to create the shortcut in the dock but i dont know how to do it. I read some thread but i haven't got it. 

Furthermore im novice in Ubuntu and i want to improve my level with some book because i need intermidiate level for practise machine learning. Can you recommend me some book?

Thanks a lot.

Pd. Sorry for my english

---

### Post by GhX6GZMB on 2022-02-20
Application Menu entries are on a per-user basis (every user has his/her own configuration).

It's done using .desktop files, you'll find those in $HOME/Desktop. Study the existing ones using a text editor, and select one as a template for your purpose.

---

### Post by him610 on 2022-02-20
Procedure to install matlab is here - [https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")

See the reference to Linux Command Line for book on Linux.
Good luck, and hope you enjoy successful endeavors.

---

### Post by vanadium on 2022-02-21
Creating your own shortcuts is in a default Ubuntu installation essentially a manual procedure. You create a .desktop launcher and place it in your ~/.local/share/applications directory. Not difficult once you know, but the format of the file needs to be right.

It is probably easier to install the utility "libremenu" in the software center. That gives you a graphical user interface to create a menu entry, i.e., such launcher.

---

### Post by yancek on 2022-02-21
One of the links below should work depending upon which file manager and release of Ubuntu you are using.

[https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-create-desktop-shortcut-launcher-on-ubuntu-20-04-focal-fossa-linux)

[https://fostips.com/app-icons-to-desktop-ubuntu-21-04/](https://fostips.com/app-icons-to-desktop-ubuntu-21-04/)

---

### Post by mIk3_08 on 2022-02-21
> **temuko said:**
> Hi !
Im noob and Im trying to create a shortcute to Matlab app. I have the executable in  **/usr/local/MATLAB/R2021b/bin **and i want to create the shortcut in the dock but i dont know how to do it. I read some thread but i haven't got it.
Furthermore im novice in Ubuntu and i want to improve my level with some book because i need intermidiate level for practise machine learning. Can you recommend me some book?
Thanks a lot.
Pd. Sorry for my english

You can easily create a shortcut for your matlab here, just follow the some instructions. [Click here]("https://help.ubuntu.com/community/MATLAB#Create_A_MATLAB_Launcher.2Fshortcut") for more detailed instructions. Good Luck and Cheers

---

### Post by wladimirr on 2022-02-21
nice

---

### Post by Dennis N on 2022-02-21
> **temuko said:**
> Hi ! 

Im noob and Im trying to create a shortcute to Matlab app...i want to create the shortcut in the dock.. 

When you start the program either from the Applications Menu or by using the search box in the Activities Overview, it's icon will appear in the Ubuntu Dock while it is running. To keep an icon there permanently, right click on the icon, and click on "Add to Favorites".

---

