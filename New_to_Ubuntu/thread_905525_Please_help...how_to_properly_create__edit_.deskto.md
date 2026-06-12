---
title: "Please help...how to properly create / edit .desktop files in /usr/share/application"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by jocko_johnson on 2008-08-30
Hello,
so I recently was learning about creating menu items for applications by creating a /usr/share/applications/'appName'.desktop file.

First attempt works fine and I can launch from the menu and the icon I added to the panel. second attempt, when I click on the menu item, I get a new window open in my panel that says "Starting IntelliJ", but then it disappears and no further response.

Here is my successful .desktop file for Eclipse:
[Desktop Entry]
Encoding=UTF-8
Name=Eclipse
Comment=Eclipse IDE
Exec=eclipse
Icon=/usr/local/eclipse/icon.png
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true

Here is the unsuccessful .desktop file for IntelliJ
[Desktop Entry]
Encoding=UTF-8
Name=IntelliJ
Comment=IntelliJ IDE
Exec=idea
Icon=/usr/local/idea-7941/bin/idea32.png
Terminal=false
Type=Application
Categories=GNOME;Application;Development;
StartupNotify=true

I think my problem lies that in the value for "Exec=eclipse" and "Exec=idea". Where "eclipse" and "idea" are both sym links in my /bin directory. the sym link for eclipse points to /path-to-eclipse/eclipse ( which is of type 'application/x-executable' ). the sym link for idea points to /path-to-idea/bin/idea.sh ( which is of type 'application/x-shellscript' ). However, I have no idea what the different available options for "Type" are ( i.e., Application is the one for Eclipse...are there other options? ).

Is what I am attempting possible? Not sure if you can do this with .sh files vs. executable files?

I am able to launch IDEA from the command line by calling "idea" from any directory, so I know the app and sym link is working OK - I just like having "quick launch" icons on my panel vs. having to go to the terminal to open.

any help is greatly appreciated. tried all night trying to find info on the different options available for .desktop files. wondering if I need to alter the "Type" value for IDEA because it is not "x-executable"?

new ubuntu user and trying my best to learn all this stuff.

Thank you

---

### Post by cariboo on 2008-08-30
Instead of trying to create menu entries by hand, why not just use the menu editor that is available by either right clicking Applications and select Edit Menus, or System-->Preferences-->Main Menu.

Jim

---

### Post by kpkeerthi on 2008-08-30
Press ALT + F2, type **idea** and press <enter>. Does it work?

---

### Post by gmxgeek on 2008-08-30
+1

---

### Post by jocko_johnson on 2008-08-30
> **cariboo907 said:**
> Instead of trying to create menu entries by hand, why not just use the menu editor that is available by either right clicking Applications and select Edit Menus, or System-->Preferences-->Main Menu.

Jim

Thanks for the suggestion, however that doesn't work either.  I right clicked on Applications and added an item that pointed to the sym lik for IDEA....when I try to open the program, nothing happens

Is it possible to create launchers for shell scripts?

---

### Post by jocko_johnson on 2008-08-30
> **kpkeerthi said:**
> Press ALT + F2, type **idea** and press <enter>. Does it work?

no.  I tried it both selecting and unselecting "run in terminal"

---

### Post by jocko_johnson on 2008-08-30
> **gmxgeek said:**
> +1

I'm confused by this one ....  what does "+1" mean?

---

### Post by kpkeerthi on 2008-08-30
> **jocko_johnson said:**
> no.  I tried it both selecting and unselecting "run in terminal"

What about /path-to-idea/bin/idea.sh in ALT+F2?

---

### Post by jocko_johnson on 2008-08-30
> **kpkeerthi said:**
> What about /path-to-idea/bin/idea.sh in ALT+F2?

no luck.  it's not so bad, I learned that I can run "idea &" so the app doesnt' hold up my terminal window.

thanks for trying

---

