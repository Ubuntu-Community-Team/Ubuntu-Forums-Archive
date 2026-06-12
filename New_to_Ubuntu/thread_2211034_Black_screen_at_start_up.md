---
title: "Black screen at start up"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by sdvf on 2014-03-13
Hi guys. I'm full of this...just problems and more problems with linux dists. I spend more time solve problems than work with SO.

This time i'm on Lubuntu and i'm using transmission. I've got a massage that tranfer stop because i've got no space on HD. OK, i delete some files and i'm ready to go. Restart the trasnfer and got the same message. Try to open chrome to find an answer to how i got the trash bin on Lubuntu but it wont open. Try again and again and nothing happens.

I've got a windows thinking: "ok, if i reboot the SO this may work again". When it boots i've got a black screen. It wont open the desktop environment. Poer off and power on and still the same black screen.

What now?

---

### Post by r.stiltskin on 2014-03-14
Deleting files doesn't actually free up any disk space if the files are still in your Trash.

See if you can log into a console -- after it boots up press Ctrl-F2 and you should get a shell prompt.  Log in with your username and password, then

```

cd .local/share/Trash/files
ls

```
At this point you should see a listing of everything in Trash.  If so:

BE CAREFUL -- mess up here and you can lose all your files or even trash your system.  If and only if you are in the .local/share/Trash/files directory, you can do
```
rm -rf *
``` and it will delete everything in that directory, including any subdirectories.

Then you should also delete everything in the .local/share/Trash/info directory, so
```

cd ../info
rm *
```

Now reboot (just type reboot <enter> at the command line) and see if you can log in normally.

---

### Post by sdvf on 2014-03-14
Ctrl f2 don't work. How can i log into console if it wont boot up? Can i get it through BIOS?

---

### Post by Dennis N on 2014-03-14
Ctrl+Alt+F2 is what you want to switch to a terminal, not Ctrl+F2

---

### Post by sdvf on 2014-03-14
It Works guys. Tks

One more thing, how can i creat a trash bin to keep it empty?

---

### Post by r.stiltskin on 2014-03-14
No way that I know of.  But you can delete files without putting them in the trash.  Instead of using the delete key, right-click on the file and then select "delete" on the context menu that pops up.

---

### Post by r.stiltskin on 2014-03-14
Or you can set up a cron job to automatically empty the trash at specified intervals.  Write a simple bash script to delete the contents of the Trash files using the same commands as above.  And then make a crontab file to run that script every day, or every hour, or every 5 minutes -- whatever you like.  Google cron or crontab to learn how.

---

