---
title: "Google Earth Doesn't Work - Can't Remove"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by luangwa on 2008-10-30
I first want to thank you for looking at my post. I tried installing Google Earth. I read almost all of the steps on how to install Google Earth and everything was going fine and then.... I click on the start button when the last install window popped up. BIG MISTAKE. The Google Earth logo came up and then the screen displayed something so fast I couldn't read it... then it went blank... and finally back to the log on screen.. but no Google Earth. 

After reading further:

When installation is complete, press Quit.
Do not press Start as this will run it as root which is never a good idea.

So I tried to uninstall Google Earth as described on 

[https://help.ubuntu.com/community/Go...roubleshooting](https://help.ubuntu.com/community/Go...roubleshooting)

Uninstallation

Assuming you installed Google Earth according to the Installation section above, Google Earth can be uninstalled by pasting the following command in a terminal:

This command is all on one line. Copy it and paste it in your terminal. 

sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth

You may also wish to remove your user preferences folder, although this is not necessary if you intend to reinstall later. This directory contains Google Earth settings and the cache:

rm -rf ~/.googleearth

This didn't work.
It was then suggested that I try this
sudo updatedb
locate google-earth
and then delete all the directories that come up.
Also, installing it should be a simple
Code:
sudo apt-get install google-earth

The screen showed the Google Earth, then went black, and back to the log on screen. 

I have even installed a driver for the ATI card which might have been causing the problem libGL.so.2 and renamed in libGL.so.1. I placed it the the Google Earth folder and still nothing.  I'm stumped and would appreciate your sharing your expertise in solving this problem.

Thanks again for reading my post.

---

### Post by mubtasim123 on 2011-01-29
:wink:
I am new to ubuntu but I can tell how I used to remove my google earth when it didn't work. Other than putting codes to terminal I went to ubuntu software center. From the left slide I clicked on google and on the right side you will see google-earth-stable go in it and remove. On my case after removing I still have the icon on the programm of google earth but it doesn't do anything and using terminal I made sure that there was no file or directory. I am just a noob new user to ubuntu, this might not work for you but give it a try..#-o

---

### Post by overdrank on 2011-01-29
Hi and thanks for helping but no need to revive a 2 year old thread. :) Thread closed

---

