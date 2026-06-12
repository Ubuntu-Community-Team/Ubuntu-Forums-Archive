---
title: "where are the ubuntu wallpaper/backgrounds located?"
date: 2018-06-12
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-12
i looked all over and do not see where they could be - wanted to add a few more of my own stuff.  thanks.

---

### Post by Bashing-om on 2018-06-12
bodhin2; Hello -

Try looking in the /usr/share/wallpapers directory.
```

sysop@x1810:~$ ls -al /usr/share/wallpapers
total 16
drwxr-xr-x   2 root root  4096 May 19 20:55 .
drwxr-xr-x 252 root root 12288 May 27 18:02 ..
lrwxrwxrwx   1 root root    27 May 20 12:57 greybird.svg -> ../backgrounds/greybird.svg
lrwxrwxrwx   1 root root    27 May 20 12:57 greybird-wall-1920x1200.png -> ../backgrounds/greybird.svg
lrwxrwxrwx   1 root root    27 May 20 12:57 greybird-wall.svg -> ../backgrounds/greybird.svg
sysop@x1810:~$

```

maybe similar in your install ..

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by bodhin2 on 2018-06-12
sorry i am not sure what you mean.  usr = home but i see no share /wallpapers......  i also looked under hidden files and again do not see anything there.  i was told to create a .theme and .icon folder for such items but no wallpaper.  thanks - i appreciate the response.  some reason i thought it would be easier to find.

got  this in terminal

~$ ls -al /usr/share/wallpapers
ls: cannot access '/usr/share/wallpapers': No such file or directory

i believe i deleted this folder because in another distro it was empty and no use so i figured that was the same.  i also still have access to the wallpapers included though?  i am using a plain gray background now.

---

### Post by Bashing-om on 2018-06-12
bodhin2; Well !

what release and flavor are you running ?

lubuntu:
/usr/share/lubuntu/wallpapers/

as another instance .

[INDENT][INDENT]2 steps back
but one forward
[/INDENT][/INDENT]

---

### Post by bodhin2 on 2018-06-12
18.04 gnome. the standard version i believe

---

### Post by &amp;KyT$0P# on 2018-06-12
/usr/share/backgrounds

---

### Post by bodhin2 on 2018-06-12
ok in terminal they show up but where via gui/window  do i find in?  that is where i am lost.  thank s.

---

### Post by Frogs Hair on 2018-06-12
Right click the desktop and select change background or from settings background.
 
Edit: > [COLOR=#000000] wanted to add a few more of my own stuff[/COLOR]

You have open nautilus as administrator and navigate to usr/share/backgrounds though you can't just add pictures to that folder and see them in the wallpaper selector.

[https://ubuntuforums.org/showthread.php?t=2033019](https://ubuntuforums.org/showthread.php?t=2033019)

[https://askubuntu.com/questions/507069/ubuntu-background-changer-not-showing-new-images-in-usr-share-backgrounds](https://askubuntu.com/questions/507069/ubuntu-background-changer-not-showing-new-images-in-usr-share-backgrounds)

---

### Post by bodhin2 on 2018-06-12
FH i got that but not sure where or how to add my own stuff to the respective folder.  i cannot believe little things like this lost me in ubuntu.

:-)

---

### Post by Frogs Hair on 2018-06-12
See my edit. :redface:

---

### Post by bodhin2 on 2018-06-12
Ok thanks for the link.  i did try: what was mentioned:


[COLOR=#000000] give ALT+F2 type in, gksudo nautilus and hit enter. Then, manually copy your pictures to /usr/share/backgrounds using the file browser window that opened. Be careful though because you have super user privileges with this window and it lets you edit any part of your system!

when i did the lt f2 and typoed and even pasted the gksudo no command was found came back.

so - i will have to read everything more closely and see what i can figure out.  never knew how to get into nautilus.  so it helps me .   

may wait until i am fresher tomorrow to try or just give up and keep things as they are.  thanks so much!
[/COLOR]

the old gnome wallpaper changer and addinga nd deleting was so m uch easier but tedious to do one at a time.....

---

### Post by oldrocker99 on 2018-06-12
They're located in ```
/usr/share/backgrounds/
```
Copy a properly-sized and formatted image to there, thus: ```
sudo cp [name-of-picture] /usr/share/backgrounds/
```

Then open the Change Background app, and you can pick that image.

For a lot of extra backgrounds, just do this:```
sudo apt install gnome-backgrounds mate-backgrounds
```

That was a good question, BTW. If you have the problem solved, you might want to edit the message header to say [SOLVED] before the header, so that other new users can benefit.

---

### Post by Frogs Hair on 2018-06-12
Gksudo is depreciated .  ```
[COLOR=#333333][FONT=Menlo]sudo apt install nautilus-admin[/FONT][/COLOR]
``` Then you will have a right-click option in nautilus though you will get two password prompts the first use. Editing the .xlm  to ad your images is no fun . I just use my own folder in pictures which requires opening nautilus to change wallpaper.

---

### Post by bodhin2 on 2018-06-12
thanks everyone.   i will check out tomorrow and see what i can get working (or not)!!!!!

:-))))   i live on 2 hrs a night of sleep the last 6 months or so .... just exhausted.

thanks again  please check back tomorrow in case i need a bit more help.  i appreciate the info and helps me to learn some more.  i am so not a command line guy.

see no sleep yet-----  

so this command: [COLOR=#333333][FONT=Menlo]sudo apt install nautilus-admin[/FONT][/COLOR]
 it opens as such nautilus or launches it and not really installs it yes?

---

### Post by deadflowr on 2018-06-12
> so this command: sudo apt install nautilus-admin
it opens as such nautilus or launches it and not really installs it yes?
It install the administrator package which will add an option to open as the administrator when right clicking inside the Files program.

So after you install nautilus-admin, open Files and go to Other Locations >> usr >> share.
Then locate the backgrounds folder, and highlight it (or if single click is set set the mouse pointer over that folder) and then right click and an option to open as admin will show.
select the open as admin and it'll ask for a password. It'll then open a new window as root for the selected folder.
You can then edit and add whatever you want to that folder.
(Well you can edit or add or delete anything anywhere really, as the new root opened folder is still accessible to the rest of the file system. If that makes sense. So be careful)


Note that it's not enough to simply add the pictures to the /usr/share/backgrounds folder.
You need to also edit the xml file located at
```
/usr/share/gnome-background-properties/bionic-wallpapers.xml
```
and add them as entries to that as well.
Otherwise all they are is located in the directory.
They don't show within the wallpaper selections until added to that xml file.

(You can edit the xml file with gedit.
**MAKE a BACKUP COPY OF THE FILE BEFORE YOU EDIT IT.**
(I would recommend just right click copy the file and paste the copy somewhere in you own user home folder. Out of the way.

What you can do is copy one of the entries from the
<wallpaper>
to the ending </wallpaper>
then clear out the old name and path and put your new pictures name and location path in it.
Like this
(This is the last wallpaper listed in the xml file for the bionic backgrounds)
```
 <wallpaper>
     <name>**Wall with door on Gozo**</name>
     <filename>**/usr/share/backgrounds/Wall_with_door_on_Gozo_by_Matthias_Niess.jpg**</filename>
     <options>zoom</options>
     <pcolor>#000000</pcolor>
     <scolor>#000000</scolor>
     <shade_type>solid</shade_type>
</wallpaper>
``` 
Just copy it and add it the file
and then change what's bolded to fit your pictures information. and save.
If that makes sense.

It seems rather convoluted because it is, most users would opt to use their own pictures in their own home pictures folder.
Since that takes a lot less time and basic syntax knowledge of xml.

(It's really easy to mess it up by accidentally removing some key character like an > or by adding extra useless characters.
When that happens the wallpaper selections might either show nothing, or only up until the error in the file.
at which point you'll need to eagle eye review your dastardly workings to find the error you made.)

So I say +1 to doing none of this and use you Pictures folder to save yourself the heartaches.

It is fun though.

Hope it helps

---

### Post by again? on 2018-06-13
> **bodhin2 said:**
> i looked all over and do not see where they could be - wanted to add a few more of my own stuff.  thanks.
If you don't need the pictures to be available system wide (ie just for your use), place your custom images in ~/Pictures and
they will show up in Settings>Background when choosing the Pictures tab.

---

### Post by Impavidus on 2018-06-13
I don't know about regular Ubuntu, but on Xubuntu I can simply select any image file as background image. Mine are in ~/Pictures/background/. You can set them using the GUI settings tool or the command line, which is great if you want to automate it.

---

### Post by bodhin2 on 2018-06-13
deadflowr and guber2---- thanks for the 1. detailed answer and  2. the simple alternate answer.  stupid me not knowing enough about the new ubuntu - since i am new - never made the connection to the pictures folder!!!!  thank you to all of you.  i will reread multiple times the info to try to learn more about linux and ubuntu!!!!!

---

### Post by bodhin2 on 2018-06-13
follow up question/thoughts:

installing nautilus admin - what use is it other than what you have told me in this thread re; background etc....  is there other useful tasks to have it available on the system?  thanks again.

---

### Post by Frogs Hair on 2018-06-13
> **bodhin2 said:**
> follow up question/thoughts:

installing nautilus admin - what use is it other than what you have told me in this thread re; background etc....  is there other useful tasks to have it available on the system?  thanks again.

Installing themes and icons for all users in usr/share/themes and usr/share/icons . I don't play around in the file system without specific and current instructions and don't I recall having a reason to except for during the development cycle.

---

### Post by bodhin2 on 2018-06-13
Thanks - i had to ask!

---

