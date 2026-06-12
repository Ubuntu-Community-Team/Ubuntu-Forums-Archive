---
title: "how do i a add a defaut application??"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by nutpants on 2012-05-13
i am tring to have a file type open with an application by default..
but the application is not in the applicaion list when i go mouse 2>
properties >  open with

how do i add an application??

( this is for real vnc to open .vnc files)
but i would like to to knpow to do it for any file extention.
and any file

---

### Post by Vaphell on 2012-05-13
is there a .desktop file in /usr/share/applications for the program in question? If so, what does its 'Exec=program' line look like?

reportedly programs refuse to appear in 'open with' dialog if there is no placeholder for the file name (%u). If it's missing in 'Exec=program' line then add it manually.
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables)

```
gksu gedit
``` to run text editor with admin rights to make changes outside the home dir.

---

### Post by nutpants on 2012-05-14
> **Vaphell said:**
> is there a .desktop file in /usr/share/applications for the program in question? If so, what does its 'Exec=program' line look like?

reportedly programs refuse to appear in 'open with' dialog if there is no placeholder for the file name (%u). If it's missing in 'Exec=program' line then add it manually.
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#exec-variables)

```
gksu gedit
``` to run text editor with admin rights to make changes outside the home dir.

no there is nothing in usr\share for the program.
it is just an executable in my home directory

i was expecting a simpler way to add a program to the "open with"

---

### Post by codemaniac on 2012-05-14
> **nutpants said:**
> i am tring to have a file type open with an application by default..
but the application is not in the applicaion list when i go mouse 2>
properties >  open with

how do i add an application??

( this is for real vnc to open .vnc files)
but i would like to to knpow to do it for any file extention.
and any file
There can be multiple text editors installed on your ubuntu system. If you want to pick a default application, update-alternatives is your friend. 
[http://www.debian-administration.org/articles/91](http://www.debian-administration.org/articles/91)

---

### Post by forrestcupp on 2012-05-14
You used to be able to set a custom "open with" command in Nautilus, but since they changed to Gnome3 in 11.10, it doesn't have that option anymore. You can do it from the command line, though. Open up a terminal and **cd** to a directory that has a .vnc file. Now, type the following command, substituting your file's name:
```
mimeopen -d *filename.vnc*
```In the choices that are listed, enter whatever number says "Other", and it will let you enter a custom command, which you would just enter the command for opening vnc.

Then you can go back to Nautilus, and you should find it in the list of "Open with" apps.

---

### Post by mc4man on 2012-05-14
> **forrestcupp said:**
> You used to be able to set a custom "open with" command in Nautilus, but since they changed to Gnome3 in 11.10, it doesn't have that option anymore. You can do it from the command line, though. Open up a terminal and **cd** to a directory that has a .vnc file. Now, type the following command, substituting your file's name:
```
mimeopen -d *filename.vnc*
```In the choices that are listed, enter whatever number says "Other", and it will let you enter a custom command, which you would just enter the command for opening vnc.

Then you can go back to Nautilus, and you should find it in the list of "Open with" apps.
That's an interesting alternate method - to note
It will create a <name>-usercreated-X.desktop in ~/.local/share/applications & create or add an entry to ~/.local/share/applications/defaults.list

(does have a small bug of no real consequence in the .desktop creation, misspells a line here - NoDsiplay=true

Edit - also doesn't auto  add a %<letter> to the Exec= line so won't show or be set as the actual default, letter should  be added after comand
I use, in most cases, %U of %f here.

For setting as default may be better to add/edit in ~/.local/share/applications/mimeapps.list instead

---

### Post by flemur13013 on 2012-05-14
Open nautilus or the equivalent*
Rt-click on a file of the type you want to change.
Select "Properties" -> Open With.

If the program you want isn't in the list, "use custom command" and just type in the program name - NO $1 or %1.

* ?!  I just noticed that this works with Thunar but the "custom" part is greyed out on nautilus. ??


Afterwards a double-click or Open on the file will start the program you entered.

---

### Post by forrestcupp on 2012-05-14
> **mc4man said:**
> That's an interesting alternate method - to note
It will create a <name>-usercreated-X.desktop in ~/.local/share/applications & create or add an entry to ~/.local/share/applications/defaults.list

(does have a small bug of no real consequence in the .desktop creation, misspells a line here - NoDsiplay=true

Edit - also doesn't auto  add a %<letter> to the Exec= line so won't show or be set as the actual default, letter should  be added after comand
I use, in most cases, %U of %f here.

For setting as default may be better to add/edit in ~/.local/share/applications/mimeapps.list insteadYeah, I forgot to mention that when you do the mimeopen command and enter your custom command, you should put "%f" after the command (without the quotes). If you do that, you shouldn't have to mess with editing anything. I've done it this way, and it worked without editing anything else.

> **flemur13013 said:**
> 
* ?!  I just noticed that this works with Thunar but the "custom" part is greyed out on nautilus. ??Yeah, like I said earlier, they didn't include that functionality in Nautilus when they switched over to Gnome3. Hopefully, it will get put back in the future.

---

