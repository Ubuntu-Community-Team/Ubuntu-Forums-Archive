---
title: "Problems with unity dashboard and permissions"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by rolfUser on 2015-07-07
Hi. I've been having problems with with the Unity Dashboard.
I wanted to access the application "Ubuntu Software Center" and it will not come up. I tried adjusting the filters but only pictures and file folders appear in the results.  I even tried seeing if firefox of google chrome would pop up, but it wouldn't and neither would any other application.

Something may have gone wrong when I tried adjusting the permissions section in the /opt/ directory. I did this because I was trying to re-install firefox developer edition from the /opt/ directory and the system would not allow it. I made a few minor changes and installation worked this time.

Now I tried moving XnRetro to the /opt/ directory but the computer and archive manager will not extract the package.  I'm guessing that these two issues are related since there were not other changes made to the system.

---

### Post by nerdtron on 2015-07-07
Yup, permission issues. If you need to extract something from the /opt directory, you most likely need to be root. So either, extract it using the command line and use sudo, or run the File Manager using root.
Try running:
gksudo nautilus
or
gksu nautilus

---

### Post by rolfUser on 2015-07-07
Before I try anything...
What do you mean I need to be "root"?

---

### Post by nerdtron on 2015-07-07
From the screenshot you have provided you'll see that the owner of the files is "root". How did those files/folders end up in /opt? Did you use any command with "sudo" to put them there?

---

### Post by yancek on 2015-07-07
> What do you mean I need to be "root"? 		

That was explained in the post, open a terminal type:   gksudo nautilus or gksu nautilus.  You will be prompted for your primary user password, enter it and you should be in the file manager with root permissions.

---

### Post by ninetailz2 on 2015-07-08
Root is the superadmin who has all the permission, so since the files in /opt/ are owned by root and only root can change it you have to use the commands as nerdtorn said to be able change/edit files there

First Run this in the terminal:
> sudo apt-get install gksu
Then Run this:
> gksu nautilus /opt/

it will open up /opt/ and you can edit files after those commands :3

---

### Post by rolfUser on 2015-07-08
> **nerdtron said:**
> From the screenshot you have provided you'll see that the owner of the files is "root". How did those files/folders end up in /opt? Did you use any command with "sudo" to put them there?

What I did is I used
```
gksudo nautilus
```
To open up a window that allows me to drag files to restricted/protected directories.
I downloaded XnRetro-linux.tgz from [http://www.omgubuntu.co.uk/2015/05/instagram-photo-filters-ubuntu-desktop-app](http://www.omgubuntu.co.uk/2015/05/instagram-photo-filters-ubuntu-desktop-app)
and dragged the file over to the /opt/ directory.

There was a problem though. This is important and I thank everyone so far for their patience.
Installation actually did work out fine the first time.     The problem is that I decided to remove **XnRetro** from the /opt/ directory from the Terminal.   I did this because the icon it was supposed to have did not appear. Instead I got a question mark for a luancher, although the application seemed to work just fine.    I thought that by removing it, and bringing in another copy, I could re-install it, and put in the respective icon for the launcher this time.  Ubuntu put a restriction for permissions.

I remember entering this command to bring up the list of launchers:
```
[COLOR=#111111][FONT=Consolas]ls /usr/share/applications/*.desktop[/FONT][/COLOR]
```
and could not find **XnRetro** on the list -- the one that opens the app --  Although I did remember seeing it appear two or three times in  a  different color from the rest of the files. I thought those were launchers that did not open any applications.

I guessing there is something I need to do involving Properties in order for my computer to trust that I am just trying to get it installed and nothing more.

Applications appear now under the Unity dashboard. I guess a software update somehow fixed the problem where they wouldn't appear. I'm grateful for it.

---

### Post by rolfUser on 2015-07-14
> **ninetailz2 said:**
> Root is the superadmin who has all the permission, so since the files in /opt/ are owned by root and only root can change it you have to use the commands as nerdtorn said to be able change/edit files there

First Run this in the terminal:

Then Run this:


it will open up /opt/ and you can edit files after those commands :3


It worked out. I was able to extract the file from the package inside the /opt/ directory.
Then I just created a launcher:

```
sudo gnome-desktop-item-edit /usr/share/applications/ --create-new
```

and XnRetro launched when I selected it from the Unity dashboard.  I appreciate everything, but we're  still not done.  When I searched for it on unity dashboard, XnRetro appeared twice -- two side-by-side.    It appeared with the launch icon that I selected when I created the launcher, and the second one has this other icon that appears in the prompt when I typed in the above code to create my launcher.

I entered this into the terminal.
```
[COLOR=#111111][FONT=Consolas]ls /usr/share/applications/*.desktop[/FONT][/COLOR]
```
I searched to the bottom of the outputted list. I am not entirely sure what I should do.
There are two launch icons. I only need one. I know I can delete the one in green, but which one will it delete?
The directory I chose for the launch icon is : usr/share/pixmaps

---

### Post by rolfUser on 2015-07-14
also i forgot to mention that both of these icons will launch the app.
But the app will appear twice -- once in each icon.

---

