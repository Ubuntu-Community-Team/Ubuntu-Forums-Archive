---
title: "How-To Install Sunbird 0.8"
date: 2008-08-31
forum: Outdated Tutorials &amp; Tips
---

### Post by gauntface on 2008-08-31
[LIST=1]
[*]To start off we need to get the latest .tar.gz file from the official Sunbird site [here]("http://download.mozilla.org/?product=sunbird-0.8&os=linux&lang=en-US").
[*]Now we need extract the files into the /opt directory on your computer, so cut and paste the .tar.gz file into your home folder if it isn't there already and open a terminal to do the following.
```
sudo tar zxvf sunbird-0.8.en-US.linux-i686.tar.gz -C /opt/
```
[*]Sunbird requires some dependencies, so we'll need to install these before we continue.
```
sudo apt-get install libstdc++5
```
[*]The next thing to do is set the files permissions so we can launch Sunbird from /opt directory.
```
sudo chown -R root:root /opt/sunbird/
```
```
sudo chmod -R 755 /opt/sunbird/
```
[*]You should now be able to launch Sunbird with this command.
```
/opt/sunbird/sunbird
```
[*]If you get an error message like this one

[IMG]http://tutorials.gauntface.co.uk/images/ubuntu/sunbird/chromeerror.png[/IMG]

then type the following command and it should fix it.
```
sudo touch /opt/sunbird/extensions/talkback@mozilla.org/chrome.manifest
```

[*]I'm assuming many of you, like me, would prefer Sunbird to be installed in the 'Applications' menu, rather than have launch it through a terminal. This is easy to achieve.

[LIST=1]
[*]Right click on the 'Applications' menu (on the top left of the screen) and select 'Edit Menus'
[*]Select the category you would like to place the Sunbird launcher and click 'New Item' (I'm going to place the Sunbird launcher in my office category)

[IMG]http://tutorials.gauntface.co.uk/images/ubuntu/sunbird/menu1.png[/IMG]

[*]Now in the new window that pops-up, set each part to the following

      Type: Application
      Name: Sunbird
      Command: /opt/sunbird/sunbird
      Comment: Mozilla Sunbird Cross-Platform Calendar Application

      Now to change the icon right click and select 'Save Link As' here.(Icon kindly provided by Benjamin Vincent Gernier).

      Save/move this picture to a place you are happy to leave it because if you move/delete it at a later date your menu item won't have an icon.
      When you've saved/moved 'sunbird.png' somewhere, click on the "spring" icon and select 'Browse' in the window that opens, find your icon and click 'Open' and then 'OK'.

[IMG]http://tutorials.gauntface.co.uk/images/ubuntu/sunbird/menu2.png[/IMG]

      Finally close the menu editor and Sunbird should now be under your chosen category.

[IMG]http://tutorials.gauntface.co.uk/images/ubuntu/sunbird/menu3.png[/IMG]
[/LIST]

[/LIST]

---

### Post by akber on 2009-11-22
Brilliance! Much appreciated.

---

### Post by leonidas25 on 2010-07-16
Works great with the new beta version
I was trying to install Sunbird from "Ubuntu Software Center", then by terminal, then by synaptics
anyway, this solved my problem. Thanks so much!!!!

---

