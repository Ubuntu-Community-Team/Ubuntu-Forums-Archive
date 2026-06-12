---
title: "installed program but no way to find it."
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Tex786 on 2008-05-08
I have the orca screen reader / Magniffier installed but it is not showing up in my applications menu.

I need this to use my computer but can't seen to find it.

I need help!

---

### Post by Bigtime_Scrub on 2008-05-08
Did you install it with the terminal or with Synaptic Package Manager?

Did you look in Application -> Accessories ?

---

### Post by funrider on 2008-05-08
can you run it in terminal by typing

$orca

---

### Post by ironclaw on 2008-05-08
I don't think it is shown in the applications menu by default. To show it you would have to go to System --> Main Menu and click on 'Universal Access' on the left hand pane. Click on the 'show' box in order to show it under Applications --> Universal Access.

---

### Post by asrai on 2008-05-08
Are you using Hardy?

If you go into system/preferences/main menu and click on 'universal access' on the left column, does it then show orca on the right column? If you put a tick in the box next to where it says orca in the right column it will then display in your applications menu.

---

### Post by Tex786 on 2008-05-08
> **Bigtime_Scrub said:**
> Did you install it with the terminal or with Synaptic Package Manager?

Did you look in Application -> Accessories ?

I installed it in the add/remove box. I chekced everywhere in my menus and it did not show up. i searched for the name of the program and it did not show up.

how do we install apps that come from websites. Ubuntu is different than what i am use to with windows. i don't know much. today will be my first full day of ubuntu. last night i installed it.

---

### Post by drs305 on 2008-05-08
I am not familiar with orca but you can find where it is located by typing this in a terminal window:
```
sudo find / | grep orca 
```

You will probably find a listing such as /usr/bin/orca

You can make a shortcut on the upper panel by right clicking on it, Add to Panel, Application Launcher, then find Orca in one of the listings. If it isn't there, then back out and choose Custom Application Launcher. In the Command entry, enter what you found during your search (e.g. /usr/bin/orca or whatever it was) or whatever you command you have found that will start it in a terminal window. You can add an icon by referencing the search and looking for a .png or other image file. You add the icon by clicking on the icon in the upper left corner of the Custom Launcher and pointing to the location of the new icon.

With normal installations, you can open synaptic, click on Search and then type in the name of the app. Once you find it, highlihgt it, select Properties and then the Installed Files tab to see where the installation files are located.

---

### Post by Tex786 on 2008-05-08
> **drs305 said:**
> I am not familiar with orca but you can find where it is located by typing this in a terminal window:
```
sudo find / | grep orca 
```

You will probably find a listing such as /usr/bin/orca

You can make a shortcut on the upper panel by right clicking on it, Add to Panel, Application Launcher, then find Orca in one of the listings. If it isn't there, then back out and choose Custom Application Launcher. In the Command entry, enter what you found during your search (e.g. /usr/bin/orca or whatever it was) or whatever you command you have found that will start it in a terminal window. You can add an icon by referencing the search and looking for a .png or other image file. You add the icon by clicking on the icon in the upper left corner of the Custom Launcher and pointing to the location of the new icon.

WIth normal installations, you can open synaptic, click on Search and then type in the name of the app. Once you find it, highlihgt it, select Properties and then the Installed Files tab to see where the installation files are located.

Where do i find this window to type what you gave me in?

---

### Post by unutbu on 2008-05-08
In the upper left corner of the screen is your 'gnome panel'. Click on Applications>Accessories>Terminal.

Once you get to a terminal, you can find all files that contain 'orca' in its name or path the way drs305 described, or by using the `locate` program, which is faster.

```
sudo /etc/cron.daily/slocate
locate orca
```

---

### Post by drs305 on 2008-05-08
> **Tex786 said:**
> Where do i find this window to type what you gave me in?

Alt F2, check run in terminal. Or you can Applciations, Accessories, Terminal. 

In fact, I'd use the second method, right click on the terminal icon and select 'add this launcher to panel' so it's always available.

---

### Post by psycosmyth on 2008-05-08
applications>accessories>terminal

it will as for your password.

then type command.


HaHa 3 at once! Get that kinda help with any other OS?

---

