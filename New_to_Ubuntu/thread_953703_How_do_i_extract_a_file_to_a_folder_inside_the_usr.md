---
title: "How do i extract a file to a folder inside the usr folder? It says permission denied"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by g2bandrew on 2008-10-20
I don't want to do this using the terminal because it's just not a practical way or at all enjoyable way for somebody like me to do this. Is there a way i can just copy and paste a file or extract a file to certain locations without being told i don't have permission?

Is there a way i could get into an admin sort of mode so i could do it without being told permission denied?

---

### Post by Het Irv on 2008-10-20
use ```
gksu nautilus
```

after you type in your password it will open an instance of Nautilus in root mode.  Just be careful, I won't ask you "if you are sure you want to delete these system files."

---

### Post by snowpine on 2008-10-20
Yes, you need to preface the terminal command with 'sudo' (without the quotes) to temporarily assume root (aka administrator) privilages. 

There is a reason why copying files to your /usr folder requires a password; if you don't know what you're doing, you can break your system! Perhaps you should re-phrase your question and let us know what you're trying to do. Maybe we can suggest a less dangerous method to accomplish the same thing.

ps If you want complete and total control over your filesystem, use the command 'gksu nautilus' (without the quotes) to open a file manager with root privilages. Be careful!

---

### Post by issih on 2008-10-20
I understand you are terminal phobic, something you would be well advised to try and get over, its often easier to use the terminal for these things, because it is the traditional admin mode of unix based OS'es.

Anyway, there is of course a way to do it via the gui, but first of all be aware that the reason you can't just drag and drop files there normally is that location is owned by root, which you should really read as "this part of the system is important, and if you mess with it you could break things". So having siad that, if you really know what you are doing, and still want to copy stuff into root locations (it is sometimes necessary whilst configuring things)

simply hit alt+f2 and type:
```
gksudo nautilus
```

into the run box and hit enter.

then enter your login password in the dialog box that pops up.

what you have just done is open the file browser (nautilus) with root permissions (gksudo) you now have the ability to copy things wherever you want...just be careful you don't damage anything.

Hope that helps

---

### Post by fooman on 2008-10-20
there is an extension to nautilus that will add that functionality to the right click context menu.  it will allow you to right-click on a directory/file in nautilus and choose to "open as administrator".  you will then get prompted for your password and the directory will open for you make whatever changes you need.  if you right click on a *file* and choose "open as administrator"...it will open the file in a text editor for you to edit.  it is called "nautilus-gksu" and is in the repos:

```
sudo apt-get install nautilus-gksu
```

you will need to logout and back in again for the change to take effect.

i find that addition to be extremely useful,  but as was mentioned already....use caution with your root privileges.  it can be very easy to break something.

---

