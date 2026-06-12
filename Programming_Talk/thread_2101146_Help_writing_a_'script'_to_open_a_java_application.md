---
title: "Help writing a 'script' to open a java application in dash home"
date: 2013-01-03
forum: Programming Talk
---

### Post by Marcus Aurelius on 2013-01-03
Hello,  I apologize in advance if I am posting on the wrong forum, or if what I am trying to accomplish is impractical.
I have Ubuntu 12.04 LTS.  I found a nice little program which takes a .pdf file and opens it, and crops the .pdf to size.  This is called briss-0.9.  I can run the application by executing following command in terminal: java -jar briss-0.9.jar or java -jar briss-0.9.jar cropthis.pdf.  For the moment I have this file in my downloads folder. But every time I want to crop a .pdf, i have to cd to the DL folder and execute the command.
What I would like to do is to simplify this is to have it so I can click the "Dash Home" icon and type pdf or briss in the search and have the program appear in there.  Then I can one-click on it and have it auto-execute.  (Rather than me going into terminal every time).  
Can a script be written to automate this, or is there another approach I can use?
I've tried other cropping software such as gscan2pdf and pdfshuffler and a few others, but none of them works very well on my computer or crashed.  
If I could make loading briss from the dash it would be congenial.  
Thanks in advance for any assistance.

---

### Post by r-senior on 2013-01-04
You need to create a .desktop file in ~/.local/share/applications (or in /usr/share/applications if you want it to work for other users on your box). You will also need to write a small shell script wrapper that runs your Java program with appropriate options. To complete the Dash/Launcher experience, you'll also need an icon.

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)
[http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

If you already have a Java application installed, e.g. Netbeans or Eclipse, you could use their .desktop files as a starting point. You'll find those in /usr/share/applications.

---

