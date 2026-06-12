---
title: "LightDM GTK+ greeter settings unable to select files in Desktop Folder"
date: 2016-08-06
forum: New to Ubuntu
---

### Post by chessmate99 on 2016-08-06
Hi all, I am trying to change the background of my login screen, but I cannot seem to select the desktop folder's file. When I clicked the Desktop option, it gives me no files, and I have to click multiple times to even select the desktop folder. Why?
Here is an image:

[http://i.imgur.com/v9FOFyB.png](http://i.imgur.com/v9FOFyB.png)

There's nothing to be selected. Why? Even for my File System folder it's the same. I do have jpeg files in my Desktop folder, though.

---

### Post by wildmanne39 on 2016-08-06
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by wildmanne39 on 2016-08-06
What version of ubuntu are you using? if ubuntu are you using unity?

---

### Post by grahammechanical on 2016-08-06
When we open the file manager with administrator/root privileges we get the result that you are getting when we access the desktop folder because we are not starting high enough up the tree. We are already in the user home folder and that is low down on the directory tree.

We need to start at the root of the file system and then select Home>Username>Home>Desktop to see any folders and files that are in the Desktop folder. With Ubuntu 16.04 the file manager will have a listing for Computer and that is where we start.

Regards

---

### Post by deadflowr on 2016-08-06
Lightdm greeter settings starts you in root's home directory.
You need to navigate to home and then your user's directory within the home directory.

To do so, simply click on the arrow pointing to the left next to root in the bar right above the window area.
After you click the arrow a new box with an odd icon will show, click on that.
Now after you click on that odd icon the main window area will populate with the directories, like bin and boot and usr.
Locate the home directory and click on it (might need to double click).
then when it opens you should see user user's name listed.
Click on the username and this should open the contents of your user's home folder.
Now you can go the sub-folder of where ever you placed the image you wanted to use.
And then select the image.

Also, a quick tip, the bar at top will always show you where in the file system you are, so you can also use that to help navigate if you get lost.
(It's generally referred to as breadcrumbs)

Hope it helps

---

### Post by mook765 on 2016-08-06
I just tried that out on my system and is indeed funny.
when i click on the button to choose a background in lightdm settings window it leads me to /usr/share/backgrounds/ubuntustudio.
i close this window and in the settings window and click the button again, this time it leads me to root ( as shown in chessmate's picture ).
In the third try it leads me back to the first location, close the window and click button again, and i am back to root,
the location alternate each time i click the button....
Ok, i can live with that...

---

