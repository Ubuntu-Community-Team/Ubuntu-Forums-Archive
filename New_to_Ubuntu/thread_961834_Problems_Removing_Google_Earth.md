---
title: "Problems Removing Google Earth"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by luangwa on 2008-10-28
I read almost all of the steps on how to install Google Earth and everything was going fine and then.... I click on the start button when the last install window popped up. BIG MISTAKE. The Google Earth logo came up and then the screen displayed something so fast I couldn't read it... then it went blank... and finally back to the log on screen.. but no Google Earth. [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

After reading further:

When installation is complete, press Quit.
Do not press Start as this will run it as root which is never a good idea.

[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

So I tried to uninstall Google Earth as described on 

[https://help.ubuntu.com/community/GoogleEarth?highlight=(earth)|(google)#Troubleshooting](https://help.ubuntu.com/community/GoogleEarth?highlight=(earth)|(google)#Troubleshooting)

Uninstallation

Assuming you installed Google Earth according to the Installation section above, Google Earth can be uninstalled by pasting the following command in a terminal:

    *

      This command is all on one line. Copy it and paste it in your terminal. 

sudo rm -rf /opt/google-earth && sudo rm /usr/share/mime/application/vnd.google-earth.* /usr/share/mimelnk/application/vnd.google-earth.* /usr/share/applnk/Google-googleearth.desktop /usr/share/mime/packages/googleearth-mimetypes.xml /usr/share/gnome/apps/Google-googleearth.desktop /usr/share/applications/Google-googleearth.desktop /usr/local/bin/googleearth

You may also wish to remove your user preferences folder, although this is not necessary if you intend to reinstall later. This directory contains Google Earth settings and the cache:

rm -rf ~/.googleearth

I thought if I could remove it I could install it again. It didn't work. So I am at a lost at how to completely remove my incorrectly installed version of Google Earth and try again.

Thanks for your anticipated help.

---

### Post by ZankerH on 2008-10-28
You could try searching for any leftover directories named google earth and deleting them manually.

btw, did you get any errors after running that command?

---

### Post by Dougie187 on 2008-10-28
Try this.

```
sudo updatedb
locate google-earth
```

and then delete all the directories that come up.

Also, installing it should be a simple
```
sudo apt-get install google-earth
```

---

### Post by luangwa on 2008-10-29
Thanks for responding to my problem. I tried what you suggested and it listed many files. Being a newbie, I'm still a little fuzzy on how to delete all the files in a folder so I tried using the file browser. Here is the message I received after I tried to delete /trash the entire folder.

The file "google-earth" cannot be moved to the trash.

What next?

---

### Post by luangwa on 2008-10-29
Dougie187

I tried using terminal command to erase remove the entire google-earth folder and all its files using rm -R /opt/google-earth. It had me respond as to whether I wanted to delete a particular file in the folder and when press y then enter. I received a polite permission denied. I was logged in using sudo. What am I over looking? 

Thanks for your patients.

---

