---
title: "Add fonts from XP font folder"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by bluebirday on 2008-10-08
Need to add fonts from XP font folder to Ubuntu font folder
I tried the following but it did not work out

1- I add the MS core fonts but it did not add all XP core fonts
2- I tried to copy and paste the required fonts from XP folder to Ubuntu folder but the operation denied
   because the Unbuntu folder could not be access. need permission
3- I knew that this operation was possible before but I do not know why it does not work now

Thanks for help

---

### Post by ddarsow on 2008-10-08
type in a terminal: ```
gksudo nautilus
``` 
This will give you a root file browser and allow you to do that operation.

Alternately:
```
sudo cp [src dir/*ttf] [destination dir]
```

---

### Post by bluebirday on 2008-10-08
Thank for your help but when I wrote the mentioned commands 
I got a reply that destination is not a directory

Ubuntu fornt folder /usr/local/share/fonts

thanks

---

### Post by ddarsow on 2008-10-08
> **bluebirday said:**
> Thank for your help but when I wrote the mentioned commands 
I got a reply that destination is not a directory

Ubuntu fornt folder /usr/local/share/fonts

thanks

it needs to be like this:

```
sudo cp [src directory/*ttf] /usr/local/share/fonts/
```

there needs to be a / after a dir name

---

### Post by Sef on 2008-10-08
Moved to A.B.T.

---

### Post by airtonix on 2008-10-09
No need for sudo here. just put any fonts you want to use under your account in ```
~/.fonts
```

---

### Post by bluebirday on 2008-10-09
sorry you mean that I just write down ~/.fonts

Please confirm

---

### Post by Valsum on 2008-10-09
Copy them at your /home/<username>/.fonts folder. You can use your file manager (Nautilus, I guess), typing CTRL + H to see hidden folders, and copying the fonts into the .fonts folder.

---

### Post by SuperSonic4 on 2008-10-09
In this case user is what you called your account.

You might need to create the fonts folder first at /home/user/.fonts

```
mkdir /home/user/.fonts
```

Then use nautilus to copy and paste them (you may need to be root to do this if so type) - ```
gksudo nautilus
``` and copy and paste in /home/user/.fonts

after that close nautilus and type in terminal: ```
fc-cache
```

Finally restart your apps and check (you may need to reboot or restart X if closing the program fails[

---

### Post by Kellemora on 2008-10-09
Hi BBJ

I don't want to confuse you with the different methods already stated.  BUT!

I just go into Nautilus (that means I'm root) then make my way to the folder
/usr/share/fonts/truetype
Within this folder, you will see other font folders.
I just create a new folder for the style font I want to add.  It doesn't seem to be picky about what you name the folder, or the font files inside for that matter, as it reads the built-in font headers.

So far, knock on simulated woodgrain, this has worked for every ttf type font I've done it with, even the proprietary ones that are not portable.

TTUL
Gary

---

