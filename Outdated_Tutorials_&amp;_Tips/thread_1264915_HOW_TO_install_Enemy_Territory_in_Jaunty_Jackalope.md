---
title: "HOW TO: install Enemy Territory in Jaunty Jackalope 9.04"
date: 2009-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kenji_03 on 2009-09-12
Ok, first of all this is a copy from [another website]("http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904"), but it worked for me much better than the 2004 instructions so I wanted to upload this to the forums.

Installation works in this order:
1. Install Wolf: ET via Terminal
2. Update Wolf: ET via Terminal to 2.60b
3. Update Punkbuster via Terminal

Extras:
(A) Custom Resolution
(B) Sound Tweaks

> 
**[http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)**> Most of these steps will require use of the terminal. The terminal in Gnome is found at Applications > Accessories > Terminal. Enter the following commands in the terminal:
```


[LIST=1]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] libgtk1.2[/FONT]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]Desktop[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**wget**[/COLOR] [COLOR=#c20cb9]**ftp**[/COLOR]:[COLOR=#000000]**//**[/COLOR]ftp.idsoftware.com[COLOR=#000000]**/**[/COLOR]idstuff[COLOR=#000000]**/**[/COLOR]et[COLOR=#000000]**/**[/COLOR]linux[COLOR=#000000]**/**[/COLOR]et-linux-2.60.x86.run[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**chmod**[/COLOR] +x et-linux-2.60.x86.run[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**sh**[/COLOR] .[COLOR=#000000]**/**[/COLOR]et-linux-2.60.x86.run[/FONT]
[/LIST]

```It will then ask you to enter your password. After you input your password, the installation will begin. You can feel comfortable leaving all of the default settings (i.e. installation path, symbolic links, Punkbuster) during install and just select next every time.
 
***Important:** after the installation is complete it will prompt you to either start the game or exit the installer. Select the option to exit the installer. If you start the game you will have some permissions problems that will need to be fixed later.*

 **Installing the 2.60b Patch**
 Once again, in the terminal run the following commands:
```
 
[LIST=1]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]Desktop[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**wget**[/COLOR] [COLOR=#c20cb9]**ftp**[/COLOR]:[COLOR=#000000]**//**[/COLOR]ftp.idsoftware.com[COLOR=#000000]**/**[/COLOR]idstuff[COLOR=#000000]**/**[/COLOR]et[COLOR=#000000]**/**[/COLOR]ET-2.60b.zip[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**unzip**[/COLOR] ET-2.60b.zip[/FONT]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]local[COLOR=#000000]**/**[/COLOR]games[COLOR=#000000]**/**[/COLOR]enemy-territory[COLOR=#000000]**/**[/COLOR][/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**cp**[/COLOR] ~[COLOR=#000000]**/**[/COLOR]Desktop[COLOR=#000000]**/**[/COLOR]Enemy\ Territory\ 2.60b[COLOR=#000000]**/**[/COLOR]linux[COLOR=#000000]**/***[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]local[COLOR=#000000]**/**[/COLOR]games[COLOR=#000000]**/**[/COLOR]enemy-territory[COLOR=#000000]**/**[/COLOR][/FONT]
[/LIST]

```**Updating Punkbuster**
 Finally, we can update Punkbuster. This is a multi-step process, but I assure you if you follow these instructions, it will work just fine. In the terminal:
```

 
[LIST=1]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]local[COLOR=#000000]**/**[/COLOR]games[COLOR=#000000]**/**[/COLOR]enemy-territory[COLOR=#000000]**/**[/COLOR]pb[COLOR=#000000]**/**[/COLOR]htm[COLOR=#000000]**/**[/COLOR][/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**wget**[/COLOR] http:[COLOR=#000000]**//**[/COLOR]www.evenbalance.com[COLOR=#000000]**/**[/COLOR]downloads[COLOR=#000000]**/**[/COLOR]cod2[COLOR=#000000]**/**[/COLOR]pbsecsv.htm[/FONT]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] ..[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**chmod**[/COLOR] +x pbweb.x86[/FONT]
[*][FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] .[COLOR=#000000]**/**[/COLOR]pbweb.x86[/FONT]
[/LIST]

```The updates should run just fine. After the updates run, start the
game either from Applications or just type et in the terminal. After
the game starts, go ahead and exit it. We are only starting the game
for a second because we need to create the preferences folder in our
user's home folder.

After the game closes, go back to the terminal and enter the following:
```
 
[LIST=1]
[*][FONT=monospace][COLOR=#c20cb9]**cp**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]local[COLOR=#000000]**/**[/COLOR]games[COLOR=#000000]**/**[/COLOR]enemy-territory[COLOR=#000000]**/**[/COLOR]pb[COLOR=#000000]**/**[/COLOR]pbweb.x86 ~[COLOR=#000000]**/**[/COLOR].etwolf[COLOR=#000000]**/**[/COLOR]pb[/FONT]
[*][FONT=monospace][COLOR=#7a0874]**cd**[/COLOR] ~[COLOR=#000000]**/**[/COLOR].etwolf[COLOR=#000000]**/**[/COLOR]pb[/FONT]
[*][FONT=monospace].[COLOR=#000000]**/**[/COLOR]pbweb.x86[/FONT]
[/LIST]

```Congratulations, you now have a fully updated and patched Enemy Territory installation. Feel free to delete any of the downloaded files off of the Desktop. If you test these instructions out and a) find a problem with something or b) find a better way to do something, [please let me know in the comments]("http://adammichaelroach.com/blog/050409/wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904") and I'll update it in my instructions.


 **Additional Tweaks**

 **Custom Resolution:** Once inside the game you set a custom resolution. For instance, my laptop runs at 1440x900. To set this resolution manually you need to bring up the drop-down game console by pressing the ~ (tilde key). You can then enter your new resolution values by entering the following (please be sure to change the values to match the settings for your display/video settings):
```

 
[LIST=1]
[*][FONT=monospace][COLOR=#000000]**set**[/COLOR] r_customHeight [COLOR=#ff0000]"900"[/COLOR][/FONT]
[*][FONT=monospace][COLOR=#000000]**set**[/COLOR] r_customWidth [COLOR=#ff0000]"1440"[/COLOR][/FONT]
[*][FONT=monospace][COLOR=#000000]**set**[/COLOR] r_mode [COLOR=#ff0000]"-1"[/COLOR][/FONT]
[/LIST]

```When you restart the game, the new resolution should be in effect.


 **Sound Issues:** Anyone who plays Enemy Territory on Linux knows the challenge of sound problems. In Jaunty the fix for me was to change the in-game sound settings to the highest setting; 44khz, Ultra-High.

---

