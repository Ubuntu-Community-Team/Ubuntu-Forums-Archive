---
title: "Adding an html link to the side bar - and changing the icon to the link"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Nevin_Staub_III on 2014-02-22
Hey, does anyone know a way I can add an html link to the unity panel. The problem I'm having is I can't do it the normal way because Firefox is already on the side bar so how could I possibly link a website shortcut to it the way the lock to launcher works. I know I could just simply make it a desktop shortcut or even use a different web browser and set it as the home page, but for only superficial reasons I want to make it so when I click a icon on the unity bar my favorite sites come right up on Firefox. I also want to be able to change the icons on these links to what I see fit, the problem I'm having with that is when I attempt to copy the .png icons to the usr/share/icons folders I get a permission denied error, and when I attempt to do it via terminal after it copies I get "failed to open input stream for file". 

Let me rephrase it in a simple way. Lets say I want to put a direct link to "netflix" on the unity launcher where it is one click away, then change the icon to "moviefilm.png". How would I go about doing it?

---

### Post by Frogs Hair on 2014-02-22
You can create a dash/panel launcher to open the browser to a web site if alacarte is installed. In order to install without adding the gnome panel use the following command.```
sudo apt-get install --no-install-recommends alacarte
``` Next, open the main menu from dash. Select the category from the left where you want the launcher to appear and select new item . see screen shot . In the command dialog use the following for Firefox .

```
firefox%u https://www.netflix.com/?locale=en-US
```  The launcher can be named what ever you want and comment is optional . Using the icon picture in the launcher properties adding a custom icon is possible simply by navigating to a folder where an image is stored .  Close launcher properties to save and look  for the icon in dash. I created and tested a launcher while writing this .

---

### Post by IvoGuerreiro on 2014-02-22
Hi,
Really, i'm new in ubuntu so i spend many time searching solution to my problems, and the others users problems, when i find it i comment. It's my way to me to learn.
And i was searching and searching, and you just arrived and posted LOL, jesus you guys really are year of lights from me.

---

### Post by Nevin_Staub_III on 2014-02-22
Thanks, Frogs Hair. Problem solved, it did exactly what I wanted and it was easy as can be.

---

### Post by Frogs Hair on 2014-02-23
You're Welcome !

---

