---
title: "HOWTO: Have a menu which shows all installed applications on your system"
date: 2005-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by jobezone on 2005-05-06
**Howto have a menu which shows all installed applications on your system**

**Explanation**

As any new user to ubuntu will notice, not every package they install on their system through the Package Manager will show up in the Applications menu.
Gnome and KDE use a recent standard, developed inside the freedesktop.org's project, for a common menu format, which means that application developers only have to add a few lines of text to their application, and it will be automatically shown in both desktops. XFCE also uses this standard.
The bad news is, that this standard is so recent, most of the applications available in the Ubuntu repositories still aren't packaged with this information.
The good news is that Debian has had their own menu system up and running for years, with every package in their repositories adding themselves to the Debian menu.
The excelent news is that you can install this Debian menu in Ubuntu and make use of it!
[B]
Installation[/B]
[list=1]
[*]Launch the Package Manager (Synaptic)
[*]Go to Settings->Repositories
[*]Activate the Universe repository
[*]Search for and install the packages named "menu" and "menu-xdg"
[*]Run in the Console:
[/list] 
```
sudo update-menus
```
Look in your Applications menu, and you will have a new menu called Debian with all the applications you installed using synaptic, apt-get or individual .deb packages. Aditional applications you install using these methods will be placed there, as the update-menu is automatically run when a package is found to be using the debian menu.

You can also place the Debian menu on the panel (thanks to **atilasendil** for the hint):
Right click on the panel, and choose "Launcher from menu", click next and add Debian. 

**For Kubuntu**, the instructions are the same, and the Debian menu will be placed in the "K" menu.
**Other desktop environments** should (or could?) use Debian menu, but if they don't, there's still use of it. 
[list=1]
[*]Install pdmenu either from Synaptic, or running in a terminal:
```
sudo apt-get install pdmenu
``` 
[*] From a console, run
[/list]
```
pdmenu
```
which will give the Debian menu in ncurses.
[B]
More information[/B]

After you've installed "menu", you'll have full documentation of it in your system in this directory:
/usr/share/doc/menu/
The manual is in:
/usr/share/doc/menu/html/

**Troubleshooting**
For some people, the Debian menu may not appear immediately in Gnome, nor in the pdmenu application. This happened to me also, when I reinstalled ubuntu hoary. But it can be solved:
[list=1]
[*]Log out of Gnome
[*]Do Ctrl+alt+F1 and login with your username
[*]Do:
```
sudo update-menus
```
[*]Run ```
pdmenu
```, if you've installed it(see above), and make sure the debian menu is working
[*]Get back to Gnome
[*]Get and install "smeg", the menu editor, from [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)
[*]Open **smeg**, and make the Debian menu visible
[/list]
 

**Kubuntu specific troubleshooting**, added by Firetech:

If you, like me, accidentally have deleted the debian menu earlier (because it was empty, and thus not showing anyway in the K-menu) follow these steps to get it back (AFTER following jobezone's guide!):

[list=1]
[*]Open a Konsole window (or any other terminal you prefer).
[*]Type ```
nano ~/.config/menus/applications-kmenuedit.menu
``` and press Enter.
[*]Press Ctrl+W and type "Debian" (without quotes) and then press Enter.
[*]If you get to the following text, delete it:
```
<Menu> <Name>Debian</Name> <Deleted/> </Menu>
```
If you don't get to exactly that text, try again by pressing Ctrl+W and then Enter. (You don't need to type "Debian" again.)
[*]After deleting the above text (you can delete entire lines with Ctrl+K) press Ctrl+O and then Enter to save the file. (If you've made something wrong, E.G. deleting too much or something like that, press Ctrl+X and start over from step 2)
[*]Press Ctrl+X to exit nano.
[*]Type ```
kmenuedit
```in the console and press Enter.
[*]Just press the save button in the menu editor (I know the debian menu isn't showing.), and then exit that program.
[*]Open your K-menu, and there should be a Debian menu at the top.
[/list]
This IS working, I've tried it twice. (I actually deleted it once more to get more precise in this guide...)

(If it doesn't show even if you haven't deleted the menu, you can try it. You'll probably get stuck on step 4 in that case...)

---

### Post by Karlos on 2005-05-06
I've got a wierd thing happening with my menus 

when I run update menus

I installed kubuntu into an ubuntu installation but decided it was a bit buggy so I removed it via removing the kde-core, which seemed to remove all of the kde stuff

but

update menus hasn't removed any of the kde stuff from the debian menu

does anyone know why ???

---

### Post by thechitowncubs on 2005-05-06
I don't like this, how can I remove it from my gnome-menu?

---

### Post by jobezone on 2005-05-06
[QUOTE=thechitowncubs]I don't like this, how can I remove it from my gnome-menu?[/QUOTE]
 sudo apt-get remove menu ?

---

### Post by thecrimsonking on 2005-05-06
Thanks jobzone.  Takes away the annoyance of having to remember all those console commands for all the apps not in the menu.

---

### Post by metaldclxvi on 2005-05-06
this one didn't work for me i have no new menu....

---

### Post by SteveyDevey on 2005-05-06
[QUOTE=metaldclxvi]this one didn't work for me i have no new menu....[/QUOTE]
It didn't do much for me, either. I'm running kubuntu, you said it would work, so I gave it a try.

It seems to have installed, but not given me a menu. I got no errors from any of the steps (except that I couldn't get Synaptic to run, since afaik, kubuntu uses Kynaptic instead (and I beleive you have to edit your repository listings by hand, which I've done already). I had already added the Universe listing I believe. I did "apt-get install menu" and it did. I told it to "update-menus" and it did. It created the directories "/usr/share/doc/menu/" and "/usr/share/doc/menu/html/", and I skimmed through the manual. I've got no "application menu" though, and I'm guessing it's either because I was having trouble with KDE pooping on itself (update problems because of kdelibs), or because there just isn't an "application menu" in KDE ;)

Did I miss something, or is there another step that's been forgotten? Thanks. :)

---

### Post by mrbass on 2005-05-06
Hopefully we'll have namely or quicksilver (both on mac) for gnome soon.
[http://developer.imendio.com/wiki/GNOME_Launch_Box](http://developer.imendio.com/wiki/GNOME_Launch_Box)
We can only  hope and dream.  Basically you just type first few letters then it shows matches and you press arrows keys and ENTER to launch app.  I use namely even with Tiger as it shaves about 2 seconds off from using spotlight.

---

### Post by jobezone on 2005-05-06
[QUOTE=SteveyDevey]It didn't do much for me, either. I'm running kubuntu, you said it would work, so I gave it a try.

It seems to have installed, but not given me a menu. I got no errors from any of the steps (except that I couldn't get Synaptic to run, since afaik, kubuntu uses Kynaptic instead (and I beleive you have to edit your repository listings by hand, which I've done already). I had already added the Universe listing I believe. I did "apt-get install menu" and it did. I told it to "update-menus" and it did. It created the directories "/usr/share/doc/menu/" and "/usr/share/doc/menu/html/", and I skimmed through the manual. I've got no "application menu" though, and I'm guessing it's either because I was having trouble with KDE pooping on itself (update problems because of kdelibs), or because there just isn't an "application menu" in KDE ;)

Did I miss something, or is there another step that's been forgotten? Thanks. :)[/QUOTE]
 My brother uses KDE, in this computer, and and he also got a Debian menu in it. Make sure you have the latest kde, try loging out and into KDE. Also, try creating a new user, and starting KDE with it, and see if it appears. If it does with that new user, the problem must be your own KDE configurations. If it doesn't appear as well... I don't know, make sure you ran update-menus using sudo! Also, check out the /usr/lib/menu , this is where all the menu entries are placed system-wide.


sorry, made the correction: /usr/lib/menu

---

### Post by jobezone on 2005-05-06
[QUOTE=Karlos]I've got a wierd thing happening with my menus 

when I run update menus

I installed kubuntu into an ubuntu installation but decided it was a bit buggy so I removed it via removing the kde-core, which seemed to remove all of the kde stuff

but

update menus hasn't removed any of the kde stuff from the debian menu

does anyone know why ???[/QUOTE]
 Were talking about the "Debian" menu,

Make positively sure that those KDE apps are uninstalled (try synaptic). I think that they should have been removed from the Debian menu. If you want to be quick and drastic, go to /usr/lib/menu and see if those unwanted apps are there, and delete them.

Debian should automatically remove menu entries from packages you uninstalled, but nevertheless you could try removing them with the "purge" option, which removes all the package's configurations.

---

### Post by jobezone on 2005-05-06
[QUOTE=SteveyDevey]It didn't do much for me, either. I'm running kubuntu, you said it would work, so I gave it a try.

It seems to have installed, but not given me a menu. I got no errors from any of the steps (except that I couldn't get Synaptic to run, since afaik, kubuntu uses Kynaptic instead (and I beleive you have to edit your repository listings by hand, which I've done already). I had already added the Universe listing I believe. I did "apt-get install menu" and it did. I told it to "update-menus" and it did. It created the directories "/usr/share/doc/menu/" and "/usr/share/doc/menu/html/", and I skimmed through the manual. I've got no "application menu" though, and I'm guessing it's either because I was having trouble with KDE pooping on itself (update problems because of kdelibs), or because there just isn't an "application menu" in KDE ;)

Did I miss something, or is there another step that's been forgotten? Thanks. :)[/QUOTE]
 Atention:
In KDE it will appear in the "K" menu.

---

### Post by T31 on 2005-05-06
anyone knows where I can find it in the xfce menus?

thx in advance :)

---

### Post by jobezone on 2005-05-06
[QUOTE=T31]anyone knows where I can find it in the xfce menus?

thx in advance :)[/QUOTE]
 Sorry, I made a mistake :(
I thought that the xfce4-panel-menu-plugin did this, but it doesn't :/
But you can install pdmenu which will open a ncurses Debian menu.

---

### Post by Karlos on 2005-05-07
>   	Quote:
 	 	 		 			 				Originally Posted by **Karlos**
 				[i]I've got a wierd thing happening with my menus 

when I run update menus

I installed kubuntu into an ubuntu installation but decided it was a bit buggy so I removed it via removing the kde-core, which seemed to remove all of the kde stuff

but

update menus hasn't removed any of the kde stuff from the debian menu

does anyone know why ???[/i]
 			 		 	 	 

 Were talking about the "Debian" menu,

Make positively sure that those KDE apps are uninstalled (try synaptic). I think that they should have been removed from the Debian menu. If you want to be quick and drastic, go to /usr/lib/menu and see if those unwanted apps are there, and delete them.

Debian should automatically remove menu entries from packages you uninstalled, but nevertheless you could try removing them with the "purge" option, which removes all the package's configurations.
  		 	 		 		 		 		 			  				__________________
				"Philosophical positions without examples
or other specifics, specific suggestions or implementation techniques
without introductory or background explication, and explicit questions
without any attempted answers are all acceptable."-[RFC3,1969]("http://www.rfc-archive.org/getrfc.php?rfc=3") 			
  

thanks....

my menus now look right again

---

### Post by jobezone on 2005-05-07
you're welcome! I loved the Debian Menu when I ran Debian (the distribution I continually use ever since I learned about apt-get 4/5 years ago(well and until I learned about ubuntu)), and only recently did I figure this should exist in the ubuntu repositories as well.

---

### Post by Firetech on 2005-05-07
Just a quick(?) note for all kubuntu users.

If you, like me, accidentally have deleted the debian manu earlier (because it was empty, and thus not showing anyway in the K-menu) follow these steps to get it back (AFTER following jobezone's guide!):
1. Open a Konsole window (or any other terminal you prefer).
2. Type "nano ~/.config/menus/applications-kmenuedit.menu" (without the quotes) and press Enter.
3. Press Ctrl+W and type "Debian" (again, without quotes) and then press Enter.
4. If you get to the following text, delete it:
```
 <Menu>
  <Name>Debian</Name>
  <Deleted/>
 </Menu>
```If you don't get to exactly that text, try again by pressing Ctrl+W and then Enter. (You don't need to type "Debian" again.)
5. After deleting the above text (you can delete entire lines with Ctrl+K) press Ctrl+O and then Enter to save the file. (If you've made something wrong, E.G. deleting too much or something like that, press Ctrl+X and start over from step 2)
6. Press Ctrl+X to exit nano.
7. Type "kmenuedit" (you know the drill, without quotes) in the console and press Enter.
8. Just press the save button in the menu editor (I know the debian menu isn't showing.), and then exit that program.
9. Open your K-menu, and there should be a Debian menu at the top.

This IS working, I've tried it twice. (I actually deleted it once more to get more precise in this guide...)

(If it doesn't show even if you haven't deleted the menu, you can try it. You'll probably get stuck on step 4 in that case...)

---

### Post by Marquis_de_Carabas on 2005-05-20
Thanks jobezone. Browsing through /usr/bin and /usr/games in a terminal to find how to start the program I'd just installed was getting to be a pain!

---

### Post by Poul on 2005-05-21
It didn't worked for me . I already have a package " menu" llisted in synaptic. I tried sudo update-menus but it hasn't changed anything. Any ideas??

---

### Post by Nu-Buntu on 2005-05-21
Worked great. Thanks!

---

### Post by basse1989 on 2005-05-21
Thanks for this howto. :)
Reading it I was able to get rid of the bloated debian menu, which I don't like.
Thanks. :)

---

### Post by David Kaisemann on 2005-05-21
Wow! 
Thank for help all newbe users!

---

### Post by jobezone on 2005-05-22
[QUOTE=Poul]It didn't worked for me . I already have a package " menu" llisted in synaptic. I tried sudo update-menus but it hasn't changed anything. Any ideas??[/QUOTE]
 Have you tried loging out and back in? In my system it worked automatically, but just try it.

---

### Post by maspro on 2005-05-22
It didn't work for me either, I'm running Gnome.

---

### Post by hanzj on 2005-05-22
How can I edit the Debian Menu (commands)? Coz I downloaded some games, and they can be run only in Terminal mode.

---

### Post by ykpaiha on 2005-05-22
just a dream
How comes a modern ESystem without this simple possibility:

Knowing what you have in installed your system and chowing them in a proper display !!

Someting like synaptic could manage a link to a virtual menu and from there display it or not, uninstall it or not?

OK it was a dream..

I''ll come back soon.

---

### Post by Ptero-4 on 2005-05-22
[QUOTE=hanzj]How can I edit the Debian Menu (commands)? Coz I downloaded some games, and they can be run only in Terminal mode.[/QUOTE]
 run update-menus and then logout, login again. That should make them appear in the "Debian" menu.

---

### Post by wondering_jew on 2005-05-23
or just  "killall gnome-panel" which will just restart the panel. When the panel restarts so will the menu, shouldn't need to log out.

---

### Post by hanzj on 2005-05-23
To my question:&#12288;”How can I edit the Debian Menu (commands)? Coz I downloaded some games, and they can be run only in Terminal mode.”


I got 2 responses:

Post #26 
run "update-menus" and then logout, login again. That should make them appear in the "Debian" menu."

and Post 27
"killall gnome-panel"


I'm afraid you two misunderstood my intended meaning. What I mean is: not how to make applications appear in the Debian menu. (They already do). The thing I want to do is to edit the already-present icons in the Debian menu, so that when I click them, the program will run in a Terminal rather than in X.


Thank you for your help!

---

### Post by veritas366 on 2005-05-23
i killed the panel after following these steps and still no menu.  

slightly off-topic...why isn't it standard to feature the command name of various programs in the docs.  I don't mean in any technical way, but I always find it strange that I, as the user, have to prowl around to find the command to execute a program I just installed.  

I'd still like the menu to work though.

---

### Post by Marquis_de_Carabas on 2005-05-23
[QUOTE=hanzj]The thing I want to do is to edit the already-present icons in the Debian menu, so that when I click them, the program will run in a Terminal rather than in X.[/QUOTE]

As far as I'm aware the only way to do this (before the next version of Gnome is released, anyway) is by using a third party menu editing program. Have a look at [this forum](http://ubuntuforums.org/forumdisplay.php?f=67), which relates to [Smeg](http://www.realistanew.com/projects/smeg/) (Simple Menu Editor for Gnome). I haven't used it, but it looks fairly nifty.

---

### Post by Curing@ on 2005-05-25
Great hint!!! Thanks!!

---

### Post by theerga on 2005-05-26
This did not work for me.  I have rebooted and everything and i am runing gnome without kde installed. is there any reason why it would not work?

---

### Post by maspro on 2005-05-26
[QUOTE=theerga]This did not work for me.  I have rebooted and everything and i am runing gnome without kde installed. is there any reason why it would not work?[/QUOTE]
I'd also like to know this...?!  :-?

---

### Post by jobezone on 2005-05-26
[QUOTE=theerga]This did not work for me.  I have rebooted and everything and i am runing gnome without kde installed. is there any reason why it would not work?[/QUOTE]
 I had to reinstall ubuntu hoary yesterday, and the debian menu also did not automatically appear. I'm now going to edit the howto to include this, but basically what I did was:
1-Log out of Gnome
2-Do Ctrl+alt+F1 and login with your username
3-Do "sudo update-menus"
4-Run "pdmenu" to make sure the debian menu is working
5-Get back to Gnome
6-Get and install "smeg" from [http://ubuntuforums.org/showthread.php?t=36608](http://ubuntuforums.org/showthread.php?t=36608)
6-Open smeg, and make the Debian menu visible

---

### Post by theerga on 2005-05-26
i guess if pdmenu dose not work that means that the debian menu is not working. hmmm i followed all the instructions so i do not know what is going on but pdmenu is not working for me.

---

### Post by jobezone on 2005-05-26
[QUOTE=theerga]i guess if pdmenu dose not work that means that the debian menu is not working. hmmm i followed all the instructions so i do not know what is going on but pdmenu is not working for me.[/QUOTE]
 do you have pdmenu installed? it's a different package.

---

### Post by Dave88 on 2005-05-26
thanks, thats a neat little mod!

---

### Post by theerga on 2005-05-26
thank got it working it dose not have all the stuff i have already insatalled though do i have to go back and do that?

---

### Post by YopY on 2005-05-30
Thanks a lot for this, it's really helpful (imo). I had a lot of games installed and it was kinda annoying to go to /usr/games all the time just to start them, not to mention the cryptic filenames etc O_o. But thanks a lot, really helpful.

---

### Post by Marquis_de_Carabas on 2005-05-30
[QUOTE=YopY]Thanks a lot for this, it's really helpful (imo). I had a lot of games installed and it was kinda annoying to go to /usr/games all the time just to start them, not to mention the cryptic filenames etc O_o. But thanks a lot, really helpful.[/QUOTE]

Drawers are a really useful way to get at often used programs too. I have Doom 3, Postal 2 and Crack Attack! in their own little drawer. Much quicker than navigating through any menus.

---

### Post by jobezone on 2005-05-30
[QUOTE=theerga]thank got it working it dose not have all the stuff i have already insatalled though do i have to go back and do that?[/QUOTE]
 sorry, I don't understand exactly what your having trouble with... :/

---

### Post by Kyral on 2005-05-30
I seem to have "accidently" installed the menu. I installed k3b (I run GNOME) and next time I restarted GNOME, the Debian menu was there. Nice feature, but now I'm thinking it has to do with the KDELibs

---

### Post by theerga on 2005-06-03
[QUOTE=jobezone]sorry, I don't understand exactly what your having trouble with... :/[/QUOTE]
what i am saying when i install packages with synoptic package manager the things i install are no autmaticaly put into the redian menu.

---

### Post by allforcarrie on 2005-06-03
NICE! I have been looking for something like this.

---

### Post by allforcarrie on 2005-06-03
so what exactly would you say the point of this is????

---

### Post by statsministern on 2005-06-03
Ok I followed all the steps on how to get the Debian menu but i cant get Smeg to make the Debian menu visible. It works in pdmenu... I have smeg 0.7.4

---

### Post by allforcarrie on 2005-06-04
I tryed this, I am guessing it doesnt work with KDE.

---

### Post by Merc248 on 2005-06-04
It worked for me after installing menu-xdg (running GNOME).

I had to search for the Ubuntu .deb file manually through Google, though; it couldn't get the file from the Ubuntu repository for some reason.

---

### Post by statsministern on 2005-06-05
Great Merc248! Just apt-get it and it worked!

---

### Post by minimidgy on 2005-06-07
I did everything the OP said, and smeg doesn't recognize a debian menu.  It appears in smeg, but smeg says it doesn't contain anything.

---

### Post by jobezone on 2005-06-07
[QUOTE=minimidgy]I did everything the OP said, and smeg doesn't recognize a debian menu.  It appears in smeg, but smeg says it doesn't contain anything.[/QUOTE]
 Did you try and run 
# sudo update-menus
?
If you have, install the package pdemnu and run it, to see if you have menu working. Also, like another person said, install menu-xdg .

In my system, the Debian entries appear in smeg but I can't do much with them. When I want to add a debian entry into the main Gnome menu, I create a new menu entry in smeg, following that applications file in /usr/lib/menu/ . For example, when I wanted to add EasyTag, I opened /usr/lib/menu/easytag which contains the following:
> 
?package(easytag):needs="X11" \
        section="Apps/Sound" \
        title="easytag" \
        command="/usr/bin/easytag" \
        icon="/usr/share/pixmaps/easytag.xpm"

I then use this information to create the new entry using smeg.

---

### Post by jobezone on 2005-06-07
[QUOTE=allforcarrie]I tryed this, I am guessing it doesnt work with KDE.[/QUOTE]

It does, in my brother's KDE it did. Also, have you checked the Troubleshooting section of the Howto? It contains information for people which can't see the menu in KDE.

---

### Post by angrykeyboarder on 2005-06-07
[QUOTE=jobezone]**Howto have a menu which shows all installed applications on your system**

**Explanation**

As any new user to ubuntu will notice, not every package they install on their system through the Package Manager will show up in the Applications menu.
Gnome and KDE use a recent standard, developed inside the freedesktop.org's project, for a common menu format, which means that application developers only have to add a few lines of text to their application, and it will be automatically shown in both desktops. XFCE also uses this standard.
The bad news is, that this standard is so recent, most of the applications available in the Ubuntu repositories still aren't packaged with this information.
The good news is that Debian has had their own menu system up and running for years, with every package in their repositories adding themselves to the Debian menu.
The excelent news is that you can install this Debian menu in Ubuntu and make use of it!
[b]
Installation[/b]

[list=1]
[*]Launch the Package Manager (Synaptic)
[*]Go to Settings->Repositories
[*]Activate the Universe repository
[*]Search for and install the package named "menu"
[*]Run in the Console:
[/list]```
sudo update-menus
```
Look in your Applications menu, and you will have a new menu called Debian with all the applications you installed using synaptic, apt-get or individual .deb packages. Aditional applications you install using these methods will be placed there, as the update-menu is automatically run when a package is found to be using the debian menu.
**For Kubuntu**, the instructions are the same, and the Debian menu will be placed in the "K" menu.
**Other desktop environments** should (or could?) use Debian menu, but if they don't (XFCE aparently doesn't), there's still use in it. 
[list=1]
[*]Install pdmenu either from Synaptic, or running in a terminal:
 
```
sudo apt-get install pdmenu
```
[*] From a console, run
[/list]```
pdmenu
```
which will give the Debian menu in ncurses.
[b]
More information[/b]

After you've installed "menu", you'll have full documentation of it in your system in this directory:
/usr/share/doc/menu/
The manual is in:
/usr/share/doc/menu/html/

**Troubleshooting**
For some people, the Debian menu may not appear in Gnome, nor in the pdmenu application. This happened to me also, when I reinstalled ubuntu hoary. But it can be solved:
[list=1]
[*]Log out of Gnome
[*]Do Ctrl+alt+F1 and login with your username
[*]Do:
 
```
sudo update-menus
```
[*]Run ```
pdmenu
```, if you've installed it(see above), and make sure the debian menu is working
[*]Get back to Gnome
[*]Get and install "smeg", the menu editor, from [http://www.realistanew.com/projects/smeg/]("http://www.realistanew.com/projects/smeg/")
[*]Open **smeg**, and make the Debian menu visible
[/list]
**Kubuntu specific troubleshooting**, added by Firetech:

If you, like me, accidentally have deleted the debian menu earlier (because it was empty, and thus not showing anyway in the K-menu) follow these steps to get it back (AFTER following jobezone's guide!):

[list=1]
[*]Open a Konsole window (or any other terminal you prefer).
[*]Type ```
nano ~/.config/menus/applications-kmenuedit.menu
``` and press Enter.
[*]Press Ctrl+W and type "Debian" (without quotes) and then press Enter.
[*]If you get to the following text, delete it:
 
```
<Menu> <Name>Debian</Name> <Deleted/> </Menu>
```
 
If you don't get to exactly that text, try again by pressing Ctrl+W and then Enter. (You don't need to type "Debian" again.)
[*]After deleting the above text (you can delete entire lines with Ctrl+K) press Ctrl+O and then Enter to save the file. (If you've made something wrong, E.G. deleting too much or something like that, press Ctrl+X and start over from step 2)
[*]Press Ctrl+X to exit nano.
[*]Type ```
kmenuedit
```in the console and press Enter.
[*]Just press the save button in the menu editor (I know the debian menu isn't showing.), and then exit that program.
[*]Open your K-menu, and there should be a Debian menu at the top.
[/list]This IS working, I've tried it twice. (I actually deleted it once more to get more precise in this guide...)

(If it doesn't show even if you haven't deleted the menu, you can try it. You'll probably get stuck on step 4 in that case...)[/QUOTE]

 
It's not working on the Hoary Live CD.  I tried your troubleshooting tips as well. No dice.

---

### Post by jobezone on 2005-06-08
[QUOTE=angrykeyboarder]It's not working on the Hoary Live CD.  I tried your troubleshooting tips as well. No dice.[/QUOTE]
 I haven't tested this with a Live CD. Indeed, I didn't know that you could install packages in a LiveCD :)
Unless you give more complete explanations on what is not working, i can't help you much. If it doesn't work at all, this is, if you installed menu, menu-xdg, pdmenu, ran update-menus, pdmenu, and looked into /usr/lib/menu/ only to find it empy, then it may just be that it can't work on a Live CD?

---

### Post by sjlsam on 2005-06-09
im trying to do this tutorial on gnome, i have everything installed including SMEG
but Debian is greyed out in smeg.. any ideas?

i click on the check to add it to the menu, but it doesn't let me check it.. it stays grey
ive done everything in the tutorial above, i need this menu!!

---

### Post by sjlsam on 2005-06-09
bump

---

### Post by sjlsam on 2005-06-10
[QUOTE=Merc248]It worked for me after installing menu-xdg (running GNOME).

I had to search for the Ubuntu .deb file manually through Google, though; it couldn't get the file from the Ubuntu repository for some reason.[/QUOTE]


holy crap!! that is the answer for all those who couldn't get it to show up on Gnome

---

### Post by arnieboy on 2005-06-16
for all those out there who cant get the debian menu even after installing menu-xdg, install the following package from synpatic and it will work:
libgnome-menu-dev

It will work after that.

---

### Post by czambran on 2005-07-13
I have installed everythin but it still wont work. THe debian menu appears grayed out on SMEG, but when I run pdmenu the debian menu does appear. any suggestions?

---

### Post by JPatrick on 2005-07-16
I moved some games from

Debian -> games to games and they've disappeared  :shock:

---

### Post by geearf on 2005-07-16
Thanks for this howto, can be very usefull to drop some programs that were installed before, and not showing in the menus.

---

### Post by arnieboy on 2005-07-16
[QUOTE=JPatrick]I moved some games from

Debian -> games to games and they've disappeared  :shock:[/QUOTE]
revert to "game" and it wil come back.. some groups arent supported.

---

### Post by atilasendil on 2005-07-17
Thanks a lot;
worked for me and on my fifth day on ubuntu and linux I am so happy to have a this :-)
But as you know people demand more all the time (after being grateful for what they get)
so what I would love to have is have the debian menu on the panel ..........
<Stop the press>
I have found the solution (am I learning Gnome ???)

So for the people who are dumb as me to start writing here and then find for themselves; or those who would like an option :
to add Debian Menu to the Panel I just chose "Launchers from menus" then clicked next and added Debian :-)

Well;
thanks again for the help

---

### Post by czambran on 2005-07-18
I have installed everythin but it still wont work. THe debian menu appears grayed out on SMEG, but when I run pdmenu the debian menu does appear. any suggestions?

---

### Post by jobezone on 2005-07-20
[QUOTE=czambran]I have installed everythin but it still wont work. THe debian menu appears grayed out on SMEG, but when I run pdmenu the debian menu does appear. any suggestions?[/QUOTE]
 This is not a problem with the menu package, but SMEG. Try upgrading to a newer version of SMEG, or bring this up with the SMEG developers.


[EDIT]Ups, sorry... At first read it seemed that you had the debian menu, and that you couldn't edit it using SMEG. 

So you mean that you don't have the Debian menu in Applications, and you can't activate it on SMEG? 

Maybe you are not using the most recent version of SMEG, or maybe this is a problem with the version of SMEG you are using?

---

### Post by czambran on 2005-07-20
> So you mean that you don't have the Debian menu in Applications, and you can't activate it on SMEG?  

That is what I meant, but I restarted my machine the other day because I had to use windows to play AOE and when I came back to Ubuntu, I was able to enable it. It is so weird. Thanks for the awesome How-To.

---

### Post by ep_ on 2005-07-21
Note: kubuntu-desktop is installed and current (see below).
Note: I ran update-menus a second time with debug output (see below).

No Debian menu on KDE, this procedure did not update the Kmenu on my system.  Seems to  work great in Gnome. Maybe its been working all along in Gnome, not sure, never use it,

I'd like to get this working, any suggestions?

mdr@ep-home:~$ sudo update-menus -d -v
Password:
update-menus[9959]: Dpkg is not locking dpkg status area, good.
update-menus[9959]: Reading installed packages list...
update-menus[9959]: Reading menu-entry files in /etc/menu/.
update-menus[9959]: 0 menu entries found (0 total).
update-menus[9959]: Reading menu-entry files in /usr/lib/menu/.
update-menus[9959]: 612 menu entries found (612 total).
update-menus[9959]: Reading menu-entry files in /usr/share/menu/.
update-menus[9959]: 0 menu entries found (612 total).
update-menus[9959]: Reading menu-entry files in /usr/share/menu/default/.
update-menus[9959]: 0 menu entries found (612 total).
update-menus[9959]: Running menu-methods in /etc/menu-methods/.
update-menus[9959]: Running method: /etc/menu-methods/gnome-panel-data
update-menus[9959]: Running method: /etc/menu-methods/xdg-desktop-entry-spec-dirs
update-menus[9959]: Running method: /etc/menu-methods/menu-xdg
update-menus[9959]: Running method: /etc/menu-methods/xdg-desktop-entry-spec-apps

mdr@ep-home:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
kubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mdr@ep-home:~$

---

### Post by jobezone on 2005-07-21
Have you tried doing what is in the Kubuntu troubleshooting section of the howto?

---

### Post by jobezone on 2005-07-21
[QUOTE=czambran]That is what I meant, but I restarted my machine the other day because I had to use windows to play AOE and when I came back to Ubuntu, I was able to enable it. It is so weird. Thanks for the awesome How-To.[/QUOTE]


Thanks:)
I'm having more trouble being able to support this thread, since my main computer is now Debian, and so I can't test things and know for sure they will work in Ubuntu. Thanks to all who have helped in this thread.

---

### Post by ep_ on 2005-07-21
[QUOTE=jobezone]Have you tried doing what is in the Kubuntu troubleshooting section of the howto?[/QUOTE]

Yes, I've tried doing whats in the Kubuntu troubleshooting (added by Firetech) in the section above.  However, my applications-kmenuedit.menu file does not contain the following text:

```
<Menu> <Name>Debian</Name> <Deleted/> </Menu>
```


So, I can't delete what is not there.  BTW, I don't know XML  but isn't it odd to be deleting the close tag ```
<Deleted/>
```  and leaving the associated open tag dangling somewhere?

Anyway I  could paste my  ~/.config/menus/applications-kmenuedit.menu  here or to a pastbin if someone thinks it might help.  One thing I might mention is I have done some editing of the Kmenu file (i.e added some menu items) before trying all this.

---

### Post by rjwood on 2005-07-28
Thank You for this info. I was wondering where things were. Now I have another delema, ' What the heck is all this stuff'? lol! What for instance is 'beforelight'? Maybe i am in the incorrect forum for this but, I tried searching and get no matches. There are other apps there that I would like to know about.  YIKES!!!!   But I'm having fun learning...

---

### Post by craigevil on 2005-07-29
Thank you. This helped alot. Much easier to find things now. Even works under XFCE.

---

### Post by Penguinette on 2005-08-07
Just curious, am I the only person that can't install SMEG?  It keeps saying I need the latest version of Python, which isn't available in any of the Ubuntu or Universe repositories.

Anyway, I got the Debian menu working finally after following some of the steps on this thread.

---

### Post by unclben on 2005-08-14
Just thought I'd add to the knowledge base here with my own experience...note that I logged out of and back into Gnome after each installation.

Installed and updated 'menu': no Debian menu.
Installed 'pdmenu': this showed the Debian menu just fine in ncurses, but still nothing in Gnome.
Installed 'smeg': smeg showed the Debian menu, but it was grayed out so I couldn't activate it.
Installed 'menu-xdg': success!

---

### Post by jobezone on 2005-08-15
[QUOTE=unclben]Just thought I'd add to the knowledge base here with my own experience...note that I logged out of and back into Gnome after each installation.

Installed and updated 'menu': no Debian menu.
Installed 'pdmenu': this showed the Debian menu just fine in ncurses, but still nothing in Gnome.
Installed 'smeg': smeg showed the Debian menu, but it was grayed out so I couldn't activate it.
Installed 'menu-xdg': success![/QUOTE]
 Ok, I see that everybody needs to have menu-xdg installed, so I just moved it up to the begining of the installation instructions. Thanks for telling your experience.

---

### Post by Eleaf on 2005-08-21
[QUOTE=jobezone]**Howto have a menu which shows all installed applications on your system**

**Explanation**

As any new user to ubuntu will notice, not every package they install on their system through the Package Manager will show up in the Applications menu.
Gnome and KDE use a recent standard, developed inside the freedesktop.org's project, for a common menu format, which means that application developers only have to add a few lines of text to their application, and it will be automatically shown in both desktops. XFCE also uses this standard.
The bad news is, that this standard is so recent, most of the applications available in the Ubuntu repositories still aren't packaged with this information.
The good news is that Debian has had their own menu system up and running for years, with every package in their repositories adding themselves to the Debian menu.
The excelent news is that you can install this Debian menu in Ubuntu and make use of it!
[B]
Installation[/B]
[list=1]
[*]Launch the Package Manager (Synaptic)
[*]Go to Settings->Repositories
[*]Activate the Universe repository
[*]Search for and install the packages named "menu" and "menu-xdg"
[*]Run in the Console:
[/list] 
```
sudo update-menus
```
Look in your Applications menu, and you will have a new menu called Debian with all the applications you installed using synaptic, apt-get or individual .deb packages. Aditional applications you install using these methods will be placed there, as the update-menu is automatically run when a package is found to be using the debian menu.

You can also place the Debian menu on the panel (thanks to **atilasendil** for the hint):
Right click on the panel, and choose "Launcher from menu", click next and add Debian. 

**For Kubuntu**, the instructions are the same, and the Debian menu will be placed in the "K" menu.
**Other desktop environments** should (or could?) use Debian menu, but if they don't, there's still use of it. 
[list=1]
[*]Install pdmenu either from Synaptic, or running in a terminal:
```
sudo apt-get install pdmenu
``` 
[*] From a console, run
[/list]
```
pdmenu
```
which will give the Debian menu in ncurses.
[B]
More information[/B]

After you've installed "menu", you'll have full documentation of it in your system in this directory:
/usr/share/doc/menu/
The manual is in:
/usr/share/doc/menu/html/

**Troubleshooting**
For some people, the Debian menu may not appear immediately in Gnome, nor in the pdmenu application. This happened to me also, when I reinstalled ubuntu hoary. But it can be solved:
[list=1]
[*]Log out of Gnome
[*]Do Ctrl+alt+F1 and login with your username
[*]Do:
```
sudo update-menus
```
[*]Run ```
pdmenu
```, if you've installed it(see above), and make sure the debian menu is working
[*]Get back to Gnome
[*]Get and install "smeg", the menu editor, from [http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)
[*]Open **smeg**, and make the Debian menu visible
[/list]
 

**Kubuntu specific troubleshooting**, added by Firetech:

If you, like me, accidentally have deleted the debian menu earlier (because it was empty, and thus not showing anyway in the K-menu) follow these steps to get it back (AFTER following jobezone's guide!):

[list=1]
[*]Open a Konsole window (or any other terminal you prefer).
[*]Type ```
nano ~/.config/menus/applications-kmenuedit.menu
``` and press Enter.
[*]Press Ctrl+W and type "Debian" (without quotes) and then press Enter.
[*]If you get to the following text, delete it:
```
<Menu> <Name>Debian</Name> <Deleted/> </Menu>
```
If you don't get to exactly that text, try again by pressing Ctrl+W and then Enter. (You don't need to type "Debian" again.)
[*]After deleting the above text (you can delete entire lines with Ctrl+K) press Ctrl+O and then Enter to save the file. (If you've made something wrong, E.G. deleting too much or something like that, press Ctrl+X and start over from step 2)
[*]Press Ctrl+X to exit nano.
[*]Type ```
kmenuedit
```in the console and press Enter.
[*]Just press the save button in the menu editor (I know the debian menu isn't showing.), and then exit that program.
[*]Open your K-menu, and there should be a Debian menu at the top.
[/list]
This IS working, I've tried it twice. (I actually deleted it once more to get more precise in this guide...)

(If it doesn't show even if you haven't deleted the menu, you can try it. You'll probably get stuck on step 4 in that case...)[/QUOTE]
 Thank you!!  This works great!  This will help me a lot..  Thanks! =-)

---

### Post by jobezone on 2005-08-21
[QUOTE=Eleaf]Thank you!!  This works great!  This will help me a lot..  Thanks! =-)[/QUOTE]
 You're welcome. I think as time goes by this will not be necessary. More and more programs are released with a .desktop file, which is a menu entry, which when placed in the right place in the system, as packages when installing do, makes those applications have an entry in the menu of KDE, Gnome, XFCE I think, and many more as time goes by.

So for those applications which don't have one, we should probably ask their developers to use it, by filling a bug.

---

