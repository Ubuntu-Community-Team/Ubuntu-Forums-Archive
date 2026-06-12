---
title: "[HowTo] Instal Flock 2.0.x on Ubuntu"
date: 2009-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by MadnessRed on 2009-05-15
I have found the tutlrials that exist already to be slightly confusing or not to work. So here is how I installed Flock 2.0.4.

I was following [this](http://ubuntuforums.org/showthread.php?t=268273) tutorial which doesn't actually work for hte version I was trying to install, I think it is mean for flock 1.x

Anyway here goes...
1) Download :
Dowbnload flock from teh link below.
[http://www.flock.com/versions]("http://www.flock.com/versions")
Make sure you get the Linux one which is the third column, direct link to English version is below.
[Download]("http://downloads.flock.com/index.php?utm_source=flockcom&utm_medium=versionspage&utm_campaign=flockcom002&utm_content=lin_language&os=linux&lang=en-GB&product=flock-2.0.3")

2) When the file is downloaded, right click on it an select "Extract to here". Double click on the folder and take note of where the files have been extraced to. From now on I will assume that you downloaded the files to your desktop so the folder called flock is on the desktop, if not then you will need to ammend the cd command in the next part or jsut copy the files there. Don't worry you can delete them after the install.

3) Open terminal and cd to the flock folder:
cd Desktop/flock
(change directory to : Desktop/flock)

4) Copy files to /opt
I am giving a command line for instructions 3 and 4 because it requires sudo. Alternative options would be to run sudo nautilus or login as root. Both are more complicated.
sudo cp -a flock /opt
(as admin : copy : and give attribute of -a : the folder "flock" : into the folder "/opt")

Note that the files no your Desktop are not needed any more so can be deleted.

5) Create a link to flock
sudo ln -s /opt/flock/flock-browser /usr/bin/flock-browser
(as admin : make link : to "/opt/flock/flock-browser" : at "/usr/bin/flock-browser")

Note you can now exit terminal, just type exit

6) Add link to main menu
Open Main Menu
System > Preferences > Main Menu
Select "Internet" on the left hand pane, then select the "New Item" button on the right.

7) Add the following info
Name: Flock
Command: flock-browser
Comment: Flock Web browser
and the for the icon, click on the square button on the top right, and then in the new window, in the text-box left of the browser button paste the following.
"/opt/flock/icons/mozicon128.png" Select the icon the press ok. Press Close on the "New Item" window and the Close on the "Main Menu" window.

8) Add icon to panel/deskop. (Optional)
Select Applications > Internet from the main menu and right click on "Flock"
Then select "Add this launcher to Desktop" or "Add this launcher to Panel"

You can now run it from Terminal/Alt+F2 by typing flock-browser, from the main menu Application > Internet > Flock, or via the panel or Desktop if you set it up that way.

This is my first tutorial so please go easy on me :)

---

