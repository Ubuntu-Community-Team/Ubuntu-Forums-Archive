---
title: "[SOLVED] Gtk skin"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Toliot on 2008-07-11
hey,
im trying to load/use a gtk skin are there any programs that will let me do this? on ubuntu?:confused:

---

### Post by dracayr on 2008-07-11
of course, just rightclick your desktop (background) and choose "change background" then click theme. to install a theme, click install, and navigate to the theme file or archive, or simply drag the file into the window

dracayr

---

### Post by Toliot on 2008-07-11
haha thx im gunna do that right now :KS

:( im trying to load this gtk theme [http://www.gnome-look.org/content/show.php/Matrix+Complete?content=79849](http://www.gnome-look.org/content/show.php/Matrix+Complete?content=79849)
i cant get the appearence preferences to open it theres more then 1 folder and the instructions that are on the site arnt working
any ideas ?

---

### Post by Toliot on 2008-07-11
hey,
can someone explain to me how to setup a gtk skin like everything becuz ive been trying to set it up for like an hour its jus when i install it says that theme has been installed but i cant like click on it(it doesnt show up)
and can u plz tell me some other skin changing programs i already no emerald
but i want to change the icons and well everything :P
thx in advance :)

---

### Post by nowshining on 2008-07-11
anything with a ~ means the home folder of that user.

in nautilus in ur home folder press ctrl+h

find the folder .themes

```
Place gtk theme folder in ~/.themes
Place icon theme folder in ~/.icons
Place font in /usr/share/fonts
Place style folder in ~/.fluxbox/styles 
```

u may need to open up the terminal and sudo cp Desktop/font /usr/share/fonts

or

create a .fonts folder in ur home folder and place the font in there, :)

for fluxbox, hmmm u can manually create the .fluxbox and .flusbox/stylses folder if need be.

edit: try this [http://gnome-look.org/content/show.php/Matrix+full+pack?content=82388&PHPSESSID=9a00a34e41df659b525d1942e46ac857](http://gnome-look.org/content/show.php/Matrix+full+pack?content=82388&PHPSESSID=9a00a34e41df659b525d1942e46ac857)

---

### Post by mcduck on 2008-07-11
You don't need any extra programs for themes. Everyhtning you need for differnt application(GTK2), icon and window frame (Metacity) themes is already there..

When you are in the Appearances-window click the Customize-button and you'll get a dialog where you can select different parts of the theme.

Only complte themes (combination of application, icon and window theme) will show in the Appearance-window. Since the theme you downloaded most likely only has one of these you have to use the customize-dialog to create combination you like. You can then save this combination and it will show in the main Appearance-window.

---

### Post by Toliot on 2008-07-11
thx for the help im gunna try that right now :) 
so how many parts do i need for a full theme?
e.g wallpaper? icons?

---

### Post by Toliot on 2008-07-11
kk im gunna try that right now ill tell u if it works :D

sry dude, but is there a way to put the gtk theme files in the proper folder/place:P threw terminal
if so can u post the code plz 
thx in advance :)

---

### Post by Bachstelze on 2008-07-12
Threads merged. Pease do not create more than one thread regarding the same issue.

---

### Post by tjwoosta on 2008-07-12
just so theres no confusion

in that picture of the matrix theme they are using fluxbox (not gnome)

so the only way to make your desktop look exactly like that would be to install fluxbox

---

### Post by Toliot on 2008-07-12
> **tjwoosta said:**
> just so theres no confusion

in that picture of the matrix theme they are using fluxbox (not gnome)

so the only way to make your desktop look exactly like that would be to install fluxbox

ok, sry :(

---

### Post by Toliot on 2008-07-12
> **nowshining said:**
> anything with a ~ means the home folder of that user.

in nautilus in ur home folder press ctrl+h

find the folder .themes

```
Place gtk theme folder in ~/.themes
Place icon theme folder in ~/.icons
Place font in /usr/share/fonts
Place style folder in ~/.fluxbox/styles 
```

u may need to open up the terminal and sudo cp Desktop/font /usr/share/fonts

or

create a .fonts folder in ur home folder and place the font in there, :)

for fluxbox, hmmm u can manually create the .fluxbox and .flusbox/stylses folder if need be.

edit: try this [http://gnome-look.org/content/show.php/Matrix+full+pack?content=82388&PHPSESSID=9a00a34e41df659b525d1942e46ac857](http://gnome-look.org/content/show.php/Matrix+full+pack?content=82388&PHPSESSID=9a00a34e41df659b525d1942e46ac857)

thx alot i finally got it to work

---

