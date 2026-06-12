---
title: "How to set working directory for app locked to launcher?"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by f(fanta) on 2014-11-22
I have locked a certain application to the launcher, but by clicking  on it it will not start, as the application requires to be started from within its own directory. I.e., from shell I can start it with:

[B]cd /opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux
./vrep.sh[/B]

Note that I have locked the application  to the launcher, but cannot find any related .desktop file neither under /usr/share/applications nor under ~/.local/share/applications/

*How can I set the working directory for an application locked to the launcher? I am running ubuntu 14.10 with unity.*

Thank you for any help.

---

### Post by CantankRus on 2014-11-22
Make your own launcher.
In terminal...
```
gedit ~/.local/share/applications/V-REP.desktop
```
Copy and paste in...
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=sh -c "cd /opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux; ./vrep.sh" 
Name=V-REP
Icon=[COLOR="#FF0000"]/path/to/icon[/COLOR]
```

Add a [COLOR="#FF0000"]path to an icon[/COLOR].
I've attached one you could use.
Save file and then search in the dash for vrep or in the file browser navigate to ~/.local/share/applications
Drag and drop on the launcher.

---

### Post by nerdtron on 2014-11-22
You can create a link to your application on the /usr/local/bin directory. This will be recognized by the terminal and will run it by just calling "vrep"

```
ln -s /opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux/vrep.sh /usr/local/bin/vrep 
```
To verify
```
ll  -h /usr/local/bin/
```

Now just simply type vrep from the terminal or on a launcher and it should be recognised by the system.

---

### Post by f(fanta) on 2014-11-23
Thanks [**[COLOR=#000000]CantankRus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1938181")! It worked to some extent. It doesn't recognize the icon (it shows a '?' instead), but that's a minor issue, I will look into it more. More annoying, when I start the application clicking on the launcher icon (top red arrow on attached image), another icon for the same application comes up on the launcher (bottom red arrow). Any idea how to get rid of the extra icon that appears when the application starts? 
I tried locking the extra icon to the launcher, but that one then fails starting then application, it is not useful.
[ATTACH=CONFIG]258136[/ATTACH]

---

### Post by mcduck on 2014-11-23
The extra icon is for the shell that your command uses to cd into right directory and start the application (the shell will continue running until the program you started closes).

Anyway, you could also just try setting the path directly in the desktop file itself, and avoid opening the extra shell:

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Path=/opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux
Exec=vrep.sh 
Name=V-REP
Icon=/path/to/icon
```

---

### Post by mc4man on 2014-11-23
What may give you one icon is to start the app from a script that cd's to the dir & runs ./vrep.sh
Then in your .desktop the Exec= line is Exec=scriptname (if script is in $PATH) or Exec=/path/to/scriptname if not.

You don't really need to use this in your .desktop - #!/usr/bin/env xdg-open, serves no advantage
(edit- seems ok - screen

---

### Post by f(fanta) on 2014-11-24
Thank you all. Here what worked, should it help anyone else.

Create a new file vrep.desktop inside ~/.local/share/applications and fill it with:

[Desktop Entry]
Version=1.0
Name=V-REP
Comment=This is my comment
Exec=/opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux/vrep
Path=/opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux
Icon=/opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux/helpFiles/en/images/features/vrepProEdu.png
Terminal=false
Type=Application
Categories=Utility;Application;

Edit the ~/.profile to add at the end an environment variable that the application needs to start (I believe that environment variables set in ~/.bashrc do not affect Unity launcher; to affect the launcher, environment variables must be in ~/.profile)
export LD_LIBRARY_PATH="/opt/V-REP_PRO_EDU_V3_1_3_rev2b_64_Linux"

From the Files explorer, navigate to ~/.local/share/applications and right-click on the file > Properties and then the tab Permissions, and tick "Execute: Allow executing file as program"
From the Files explorer, still in ~/.local/share/applications, start the V-REP application by clicking on the icon

Once the application has started, right click on its icon in the launcher and lock it to the launcher.

I have found a specification of the .desktop files format, here it is [http://standards.freedesktop.org/desktop-entry-spec/latest/](http://standards.freedesktop.org/desktop-entry-spec/latest/)

---

