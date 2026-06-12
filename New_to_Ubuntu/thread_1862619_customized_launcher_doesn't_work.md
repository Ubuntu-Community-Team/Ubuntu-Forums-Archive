---
title: "customized launcher doesn't work"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by beew on 2011-10-16
Hi, I am testing my new Ubuntu 11.10 install.

I downloaded a program called weka which is basically a .jar file that doesn't need installation. To start it one needs only to type ```
java -jar pathtoweka.jar
```  I made a launcher using alacarte, the .desktop file is created in ~/.local/share/applications. 

The icon for the program appears in the dash, but clicking it has no effect. I have also dragged the .desktop file to the Unity bar, again clicking it has no effect. Clicking the .desktop file directly again has no effect. I have checked the permission to ensure that it can be executed as a program. 

It doesn't work in Unity and it doesn't work in Gnome shell.

I have done exactly the same thing in Natty and it worked without a problem. 

But here is something really strange. I  have installed a classic menu indicator in 11.10's Unity desktop with this ppa [https://launchpad.net/~diesch/+archive/testing]("https://launchpad.net/%7Ediesch/+archive/testing")
The launcher actually shows up in the menu drop down list and it works!

Here is the actually .desktop file```
[Desktop Entry]
Categories=;
Exec=java -jar ~/weka-3-6-5/weka.jar
Hidden=false
Icon=/home/mb/weka-3-6-5/weka.gif
Icon[en_CA]=/home/mb/weka-3-6-5/weka.gif
Name=weka
Name[en_CA]=weka
Terminal=false
Type=Application
Version=1.0
```Thanks for any help in advance!

---

### Post by hwttdz on 2011-10-17
I'd give it the full path to java as well, just to be sure.

---

### Post by mcduck on 2011-10-17
...and definitely add a full path to the jar file. While Bash easily recognizes and expands "~" as path to your home, it isn't an universally supported shortcut. You should always use full paths outside of the shell.

---

### Post by mc4man on 2011-10-17
Your Exec= should generally be full path
In the case of where directories in your home folder are included in the Exec= they can also just start at the dir. name.
This applies to both the main Exec= or any time you have quicklist entries
So either of these should work
Exec=java -jar /home/mb/weka-3-6-5/weka.jar 
Exec=java -jar weka-3-6-5/weka.jar

usually safer to just  full path all

---

### Post by beew on 2011-10-18
> **mc4man said:**
> Your Exec= should generally be full path
In the case of where directories in your home folder are included in the Exec= they can also just start at the dir. name.
This applies to both the main Exec= or any time you have quicklist entries
So either of these should work
Exec=java -jar /home/mb/weka-3-6-5/weka.jar 
Exec=java -jar weka-3-6-5/weka.jar

usually safer to just  full path all

Hi,

Removing ~/ and just ```
 java -jar weka-3-6-5/weka.jar
``` works. Turns out that was what I used in Natty as well.

Thanks again! You have been really helpful!


Thanks to others who have responded as well.

P.S. Turns out I can make the launcher appear under the correct type in the dash by editing the "Categories;" line in the .desktop file by changing it to "Categories=Science;" Did it before but forgot the capital "S".

---

