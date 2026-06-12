---
title: "cp chromium-browser into startup"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by unibroker on 2012-06-04
I would like to automatically start up my browser after logging on.  I cp the browser from the etc folder into etc/xdg/autostart and did an ls to make sure it was there.  It was.  Apparently it is not as simple as I thought because on restart the browser did not automatically load.  What am I missing besides further command of the command line!?

---

### Post by cortman on 2012-06-04
> **unibroker said:**
> I would like to automatically start up my browser after logging on.  I cp the browser from the etc folder into etc/xdg/autostart and did an ls to make sure it was there.  It was.  Apparently it is not as simple as I thought because on restart the browser did not automatically load.  What am I missing besides further command of the command line!?

It's much easier than that. Assuming you're using Unity (please say if not- it'll take different instructions for different DE's: Click the gear icon in the upper right hand corner of the top panel. Select Startup Applications. Click Add. In the resulting dialog box give command as the name of the browser. Click add and close.

---

### Post by unibroker on 2012-06-04
> **cortman said:**
> It's much easier than that. Assuming you're using Unity (please say if not- it'll take different instructions for different DE's: Click the gear icon in the upper right hand corner of the top panel. Select Startup Applications. Click Add. In the resulting dialog box give command as the name of the browser. Click add and close.
Sorry cortman.  I should have stated that I'm using this little exercise to further my using of the command line.

---

### Post by cortman on 2012-06-04
> **unibroker said:**
> Sorry cortman.  I should have stated that I'm using this little exercise to further my using of the command line.

Ah, I see. Have you tried adding it to crontab? Google for info on that. :)

---

### Post by spcwingo on 2012-06-04
Does this work:

```
sudo ln -s /usr/share/applications/chromium-browser.desktop /etc/xdg/autostart/chromium-browser.desktop
```

---

### Post by unibroker on 2012-06-04
> **spcwingo said:**
> Does this work:

```
sudo ln -s /usr/share/applications/chromium-browser.desktop /etc/xdg/autostart/chromium-browser.desktop
```
Thanks for the response.  It did not although I got no error upon entering the suggested line.

---

### Post by deadflowr on 2012-06-04
Assuming you built your .desktop file right. In a terminal

```
sudo gedit /etc/xdg/autostart/nameoffile.desktop
```

Find the line Nodisplay and make sure it is set to false. Then save.

---

### Post by unibroker on 2012-06-04
> **spcwingo said:**
> Does this work:

```
sudo ln -s /usr/share/applications/chromium-browser.desktop /etc/xdg/autostart/chromium-browser.desktop
```
I just checked the list under Start Up Applications and Chromium is listed!  I think the problem might be that it is no longer at .Desktop.  I moved it when I first started in Ubuntu to the side menu bar.  I'm going to edit out .Desktop and see if that works.

---

### Post by deadflowr on 2012-06-04
Programs listed in the Startup applications section are user-specific. The .desktop file is located in a hidden folder in the home directory.(ctrl+h).config/autostart.

---

### Post by unibroker on 2012-06-04
> **deadflowr said:**
> Programs listed in the Startup applications section are user-specific. The .desktop file is located in a hidden folder in the home directory.(ctrl+h).config/autostart.
I did ```
ls -a
``` in my home directory and .desktop is not listed.

---

### Post by deadflowr on 2012-06-04
> **unibroker said:**
> I did ```
ls -a
``` in my home directory and .desktop is not listed.

Unless you've cd into the directory ~/.config/autostart, the ls -a command will only show you folders and files directly in the home folder, not what's inside the folders.(ie, it shows you the video folder but not the video files inside the video folder.)

In an aside, I forgot to say in my earlier post, the command should have been

gksudo gedit not sudo gedit as you would be launching a gui application. If you were running a cli editor it would be sudo whatever your editor is, usually nano).

---

### Post by unibroker on 2012-06-04
> **deadflowr said:**
> Unless you've cd into the directory ~/.config/autostart, the ls -a command will only show you folders and files directly in the home folder, not what's inside the folders.(ie, it shows you the video folder but not the video files inside the video folder.)

In an aside, I forgot to say in my earlier post, the command should have been

gksudo gedit not sudo gedit as you would be launching a gui application. If you were running a cli editor it would be sudo whatever your editor is, usually nano).
The only thing that comes close to the boolean expression you previously said to look for is: ```
Exec=/usr/bin/chromium-browser %U
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=chromium-browser
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;x-scheme-handler/http;x-scheme-handler/https;
StartupWMClass=Chromium-browser
StartupNotify=true
X-Ayatana-Desktop-Shortcuts=NewWindow;Incognito;TempProfile

```

I did find the .desktop as you described.

---

### Post by deadflowr on 2012-06-04
To see if this would work, I added my firefox to the startup applications this is my .desktop file:

/home/me/.config/autostart/firefox.desktop
```

[Desktop Entry]
Type=Application
Exec=firefox
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=firefox
Name=firefox
Comment[en_US]=
Comment=
```

As you can see this is how it should look, this launches the firefox browser upon logging into my user.
To add for all users, I've found the easiest way is to execute the text editor in root and save(save as) the file in the /etc/xdg/autostart folder.

Through the command line use:

```
sudo mv ~/.config/autostart/filename.desktop /etc/xdg/autostart
```

This launches firefox, regardless of whose logged in.
I hope this helps.

---

### Post by unibroker on 2012-06-04
> **deadflowr said:**
> To see if this would work, I added my firefox to the startup applications this is my .desktop file:

/home/me/.config/autostart/firefox.desktop
```

[Desktop Entry]
Type=Application
Exec=firefox
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=firefox
Name=firefox
Comment[en_US]=
Comment=
```

As you can see this is how it should look, this launches the firefox browser upon logging into my user.
To add for all users, I've found the easiest way is to execute the text editor in root and save(save as) the file in the /etc/xdg/autostart folder.

Through the command line use:

```
sudo mv ~/.config/autostart/filename.desktop /etc/xdg/autostart
```

This launches firefox, regardless of whose logged in.
I hope this helps.
This is all I get in my editor:
```
[Desktop Entry]
Type=Application
Terminal=false
Exec=/usr/bin/chromium-browser --no-startup-window
Name=Chromium
```:confused:

---

### Post by deadflowr on 2012-06-04
I don't run chromium, but I do use google-chrome. I noticed that my startup applications list google-chrome with that exact .desktop file(changing chromium-browser with google-chrome).Adding a new chrome to the startup applications worked once, upon my intial relogin, but then disappeared from the startup applications. Seemed like the one in place simply overrides the new one. I tried to edit out the line --nostartup-window(or whatever it's called), did a relogin again it launched chrome, but the .desktop file reverted again.
So on a third try I simply copied my firefox.desktop file open gedit and pasted it in and replaced the Exec and name with the path to google-chrome. I saved, save as, named it chrome.desktop and saved it in the .config/autostart folder(right click when in the save folder screen to show hidden files option. Now chrome launches whenever I log in.
Hope this helps.

---

### Post by unibroker on 2012-06-04
> **deadflowr said:**
> I don't run chromium, but I do use google-chrome. I noticed that my startup applications list google-chrome with that exact .desktop file(changing chromium-browser with google-chrome).Adding a new chrome to the startup applications worked once, upon my intial relogin, but then disappeared from the startup applications. Seemed like the one in place simply overrides the new one. I tried to edit out the line --nostartup-window(or whatever it's called), did a relogin again it launched chrome, but the .desktop file reverted again.
So on a third try I simply copied my firefox.desktop file open gedit and pasted it in and replaced the Exec and name with the path to google-chrome. I saved, save as, named it chrome.desktop and saved it in the .config/autostart folder(right click when in the save folder screen to show hidden files option. Now chrome launches whenever I log in.
Hope this helps.
Success!  Kind of defeats the purpose because at this point I don't understand how your code with the filename change works but that is for tomorrow.  Also I'm going to learn to use cortman's suggestion of crontab.

Thanks for your help.

---

### Post by jtarin on 2012-06-04
I used to put my start up commands in /etc/rc.local or /etc/rcd./rc.local....depending on the distro. Don't have the file? You can make it then make it executable.

---

### Post by deadflowr on 2012-06-04
> **unibroker said:**
> Success!  Kind of defeats the purpose because at this point I don't understand how your code with the filename change works but that is for tomorrow.  Also I'm going to learn to use cortman's suggestion of crontab.

Thanks for your help.
I agree, and I have no idea how long it will work(depending on updates and such.) Learning crontab seems pretty interesting, along with:

> **jtarin said:**
> I used to put my start up commands in /etc/rc.local or /etc/rcd./rc.local....depending on the distro. Don't have the file? You can make it then make it executable.

And you see? This is why I love linux. There are many different ways to skin the cat.

---

### Post by unibroker on 2012-06-05
> **deadflowr said:**
> I agree, and I have no idea how long it will work(depending on updates and such.) Learning crontab seems pretty interesting, along with:



And you see? This is why I love linux. There are many different ways to skin the cat.
Alas, I spoke too soon.  I should have done a reboot after my initial success after logging out because I experienced the same thing you did.  This is definitely the type of exercise I was looking for to advance my CLI learning.

---

### Post by unibroker on 2012-06-05
```
/etc/xdg/autostart$ ls -l
```
There are 2 entries for chromium-browser when I enter the above code (there were 3 but I did an unlink for symbolic link recommended earlier).  I did a chmod 777 on one and the desired startup of chromium didn't happen when I re-booted.  The other chromium-browser entry doesn't have execution privileges so I want to remove that but I've read horror stories when improperly using the rm command.  BTW, the only difference in the two chromium entries besides chmod I performed is that there is a tilde at the end of the chromium I want to remove.  TIA

---

