---
title: "HOWTO: Set Sessions Startup Order"
date: 2009-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by drs305 on 2009-04-08
[COLOR="MAROON"]**[SIZE="4"][CENTER]*HOWTO: SET [I]SESSIONS* STARTUP ORDER[/I][/CENTER][/SIZE]**[/COLOR]

**[COLOR="DarkGreen"][SIZE="3"]In a Rush? Go Directly to #6 for the codes to enter in the *Sessions* command line.[/SIZE][/COLOR]**

**[COLOR="Navy"][SIZE="3"]1. Purpose and Background:[/SIZE][/COLOR] **
*Sessions* allows Ubuntu users to specifiy applications they wish to run on logon. This guide presents information on how to incorporate delay codes into the *Sessions* commands to start the applications in a relatively pre-determined order. ***Sessions* has been renamed *Startup Applications* in Jaunty Jackalope 9.04.** 

Often Ubuntu users want to delay the opening of a process listed in *Sessions*.  Attempting to make a direct entry into the *Sessions* command line of "sleep 20 && /path/<appname>" does not work. A common workaround was to create a BASH script which includes the *sleep* command and reference that script in the *Sessions* entry. 

With the proper formatting a user can include a delay period within the *Sessions*-generated command itself. This offers a more direct method, via a gui application, and avoids having to create  a BASH script. Reasons for wanting to input delays before an application run command include:
[List]

[*]Allowing another application to start first (or second, third, etc).
[*]Wanting to place the icons in a particular order on the panel's Window List.
[/LIST]

**[COLOR="Navy"][SIZE="3"]3. The Mechanics.[/SIZE][/COLOR]**
The tasks accomplished by *Sessions* should not be confused with runlevel actions performed by the system on entries in the /etc/init.d folder during boot. *Sessions* applications begin after the user logs on - thus they are specific to each user and do not require 'root' privileges to accomplish "non-root" tasks. 

When an addition is made to the *Sessions* menu, a configuration file is made in $HOME/.config/autostart folder **[COLOR="Navy"]*[/COLOR]**. The .config folder is "hidden". If you do not see it in a file browser, CTRL-H to view hidden files or use the application's *Preferences* menu to enable viewing them. The file is created with the extension *.desktop* and the contents are determined by what the user enters when creating a new startup item.
**[COLOR="DarkRed"]* Note: [/COLOR]**"$HOME" denotes the user's HOME folder, and can also be designated as ~/ or as /home/*username*/. So the path to the file could also be written as /home/*username*/.config/autostart.  


**[COLOR="Navy"][SIZE="3"]4. Determining the Run Command[/SIZE][/COLOR]**
Before proceeding you first must know what command starts the application. Some, such as "*gedit*", may seem obvious. Others may seem obvious but require certain switches to perform properly in *Sessions* (See *nautilus* in Section 7). Others are just not obvious, such as the *calc* function of OpenOffice (oocalc).
[LIST]
[*]**[COLOR="DarkRed"]Check the properties of the application's shortcut icon.[/COLOR]** 
[LIST]
[*]If you already have a shortcut a panel or the Desktop, right click the shortcut icon, select *Properties*, and view the *Command:* entry. 
[*]If the application appears within the Main Menu, open the menu for editing: Right click the Main Menu icon, *Edit Menus*. Select the appropriate category in the left panel, then highlight the application appearing in the right panel. Select *Properties* to display the run command.
[/LIST]
[*]**[COLOR="DarkRed"]If you think you know the correct name, type "which <*appname*>" in a terminal.[/COLOR]** 
This will return the start command and its path. 
Example: *which gimp* returns */usr/bin/gimp*
[*]**[COLOR="DarkRed"]Look in Synaptic.[/COLOR]** Find the application, highlight it, and select Properties in the top menu. Click on the "*installed files"* tab and look for a run command. Again, the path /usr/bin is a good place to start. 
Example: OpenOffice calc. /usr/bin/oocalc  
[*]**[COLOR="DarkRed"]Search the forums or internet in general.[/COLOR]** Including the common name and "command" or "run command" will generally provide useful search results.
[*]**[COLOR="DarkRed"]Note:[/COLOR]** Some application files end with the version number as part of the filename. If so, try running the command without the ending version number. If it opens the correct version, omit it. If it opens the wrong version or doesn't run, include these in the run command. Omitting the version number may allow the script to run without modification when the application version number changes with an upgrade.  
Example: *gimp-2.6* and *gimp* both work. Use *gimp* for future version compatibility if possible.


**[COLOR="Red"]Once you have the command, test it in a terminal window and make sure the application launches properly.[/COLOR]** Trying to add a delay code to a command that doesn't work on the command line will make troubleshooting more difficult.
[/LIST]


**[COLOR="Navy"][SIZE="3"]5. Creating a *Sessions* Listing[/SIZE][/COLOR]**
[LIST]
[*]**[COLOR="DarkRed"]Open the *Sessions* dialog box:[/COLOR]**
[LIST]
[*]From the Main Menu: System > Preferences > *Sessions* (renamed *Startup Applications* in Jaunty). Select "*Add +*"
[*]From the command line:
```
gnome-session-properties
```
[/LIST]
[*]**[COLOR="DarkRed"]Enter a name for the entry.[/COLOR]** This is the name which will appear in the *Sessions* menu. See Note 1.
[*]**[COLOR="DarkRed"]Enter the command.[/COLOR]** You can use the "Browse ..." button to the right of the command box to search for and select for the application's run command. Often this command is found in the /usr/bin folder. It is preferable to include the complete path to the command to prevent PATH errors.
[*]**[COLOR="DarkRed"]Enter a comment if desired.[/COLOR]**
[*]**[COLOR="DarkRed"]Select [COLOR="Navy"]"Add+"[/COLOR] to create the file.[/COLOR]**
[*]**[COLOR="DarkRed"]Note 1:[/COLOR]** The name entered in *Sessions* may not generate the same name in the .desktop file. The $HOME/.config/autostart/*.desktop file might start with *gnome*, *bash*, etc and may not even contain the name you entered in the *Sessions [COLOR="Navy"]name[/COLOR]* window. You don't really need to know the name to use it. If you want to view the file and don't see it listed in $HOME/.config/autostart look for the newest file. You can also probably locate a .desktop file by searching the *autostart* folder for files created within the last 5 mintues using this command:  "*find $HOME/.config/autostart -type f -cmin -5*"  
The files are simple text files that can be opened with a text editor.
[/LIST]


**[COLOR="Navy"][SIZE="3"]6. Adding a Startup Delay[/SIZE][/COLOR]**
To correctly process a delay code including the *sleep* command, the entry should be made in the following format. Replace **[COLOR="Navy"][COLOR="DarkRed"]X[/COLOR][/COLOR]** with the number of seconds you want to delay the start.
```

bash -c "sleep **[COLOR="DarkRed"]X[/COLOR]**; /path/application"

```
Example: bash -c "sleep 20; gimp"

**[COLOR="DarkRed"]Note [/COLOR]** The delay time may need to be adjusted to ensure an application is started before or after another one. Timing begins after the user logs in, but different applications have different initialization times. A complex program may start first but open long after a simpler program with a longer *sleep* delay. It may be necessary to adjust the time values to obtain the desired results. 
[/LIST]
To test the new *Sessions* entries, you must log out and log back in. Rebooting is not necessary.

**[COLOR="Navy"][SIZE="3"]7. Switches and Special Commands[/SIZE][/COLOR]**
Some commands will open an application normally in a terminal but will not open the same program via the *Sessions* script. This generally involves applications which require special *switches* or *additions* when opened in this manner. If you have difficulty in getting a particular application to start, check the "man" page and look at the available options.

I will expand this section as relatively common applications needing these switches are brought to my attention.

**[COLOR="DarkRed"]NAUTILUS:[/COLOR]**
*nautilus* is not just a file browser, it is a file *manager*. The command *nautilus* controls several important gnome processes. To use the command as a file browser include a PATH following the command. This ensures the nautilus file browser is started. Failure to include a path may result in the command running but not opening a browser window. 

```
bash -c "sleep 10; nautilus $HOME"
*or:*
bash -c "sleep 10; nautilus */media/mydata*"
```


**[COLOR="Navy"][SIZE="3"]8. A Sample *SESSIONS* .desktop File:[/SIZE]**[/COLOR]
This is a file created by *Sessions* to start *gimp* with a delay of 20 seconds. The *gimp* run command is "/usr/bin/gimp". The file, once created, was located at /home/*username*/.config/autostart/gimp.desktop
> 

[Desktop Entry]
Type=Application
Name=gimp
Exec=bash -c "sleep 40; /usr/bin/gimp"
Icon=system-run
Comment=This is a comment I entered.

**[COLOR="DarkRed"]Note:[/COLOR]** Each .desktop file contains a blank first line. The files are not marked as executable and are owned by the $HOME owner.

**[COLOR="Navy"][SIZE="3"]9. Acknowledgments[/SIZE][/COLOR]**
The guide was prepared following discussions which began on this thread: [*_Set session startup order ?_*]("http://ubuntuforums.org/showthread.php?t=1107749") by *RavanH*.
The thread evolved and was expanded by *plamen_todoroff*. Several different methods were discussed and this HOWTO is the result of those discussions. Thanks to all who participated and contributed in that thread.

---

### Post by snkiz on 2009-04-17
When you were looking through the .desktop files did you notice the x-gnome options? I find these to be more effective in setting the order.

```

Type=Application
Name=GNOME Settings Daemon
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
OnlyShowIn=GNOME;
X-GNOME-Autostart-Phase=Initialization
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-settings-daemon

```

so far the phases I've been able to figure out are; Initialization, Desktop, Panel, and Applications. kde has similar options worded differently. I would suggest using sleep in the exc only be used in the application phase and only sparingly because each second you add with sleep, adds to your over all startup time.

---

### Post by zero7404 on 2009-04-26
i was able to locate the individual files in the autostart folder, and want to make firestarter delay by about 30 sec, because i always get an error message since firestarter starts before my internet connection is established....

so where does this bash command belong, in the file ? when i open the file, the first entry is red, the rest of the items are green, should i add the bash command at the top or at the end ?

while on this topic...i'd like to make firestarter start minimized to the panel, is that possible ?

---

### Post by drs305 on 2009-04-27
> **zero7404 said:**
> i was able to locate the individual files in the autostart folder, and want to make firestarter delay by about 30 sec, because i always get an error message since firestarter starts before my internet connection is established....

so where does this bash command belong, in the file ? 

I installed firestarter, added it to Sessions/Startup Applications,  and checked the autostart file. Open the firestarter.desktop file with:
```
gedit $HOME/.config/autostart/firestarter.desktop
```
Note: the file may just be called "firestarter", in which case substitute this for "firestarter.desktop"

Then edit the line as indicated. You may have to experiment to see what type of delay you need.
*(Added later: See post #6 for modified command to account for root privileges.)*
```

[Desktop Entry]
Type=Application
Name=fs
**Exec=bash -c "sleep 30; /usr/sbin/firestarter"**
Icon=system-run
Comment=

```

---

### Post by zero7404 on 2009-04-27
thanks,

i changed the entry in the file, but on restart, i get an error saying i don't have privileges to start firestarter....

there used to be the entry gksu /usr/sbin/firestarter....
the new bash entry doesn't contain gksu or other superuser command...

---

### Post by drs305 on 2009-04-27
Since firestarter apparently needs admin privileges to run, you can insert "gksu" in the startup command. When I tried this, a password message appeared after the delay and asked me to insert it. Firestarter then ran normally.

Change the line in $HOME/.config/autostart/firestarter.desktop to:
> 
Exec=bash -c "sleep 30; gksu /usr/sbin/firestarter"


---

### Post by zero7404 on 2009-04-27
works great now, thanks !

---

### Post by DJ_Peng on 2009-12-24
> **drs305 said:**
> **[COLOR="Navy"][SIZE="3"]6. Adding a Startup Delay[/SIZE][/COLOR]**
To correctly process a delay code including the *sleep* command, the entry should be made in the following format. Replace **[COLOR="Navy"][COLOR="DarkRed"]X[/COLOR][/COLOR]** with the number of seconds you want to delay the start.
```

bash -c "sleep **[COLOR="DarkRed"]X[/COLOR]**; /path/application"

```
Example: bash -c "sleep 20; gimp"

**[COLOR="DarkRed"]Note [/COLOR]** The delay time may need to be adjusted to ensure an application is started before or after another one. Timing begins after the user logs in, but different applications have different initialization times. A complex program may start first but open long after a simpler program with a longer *sleep* delay. It may be necessary to adjust the time values to obtain the desired results. 
[/LIST]
To test the new *Sessions* entries, you must log out and log back in. Rebooting is not necessary.
Thank you for these instructions. I've been wanting to find a well-explained method for creating a pause before launching Google Gadgets Sidebar so it opens after Compiz and AWN. For the first time since I started using the Sidebar I don't have those ugly borders around my gGadgets. I definitely owe you a few beers for even these few paragraphs.

You rock! :guitar:

---

