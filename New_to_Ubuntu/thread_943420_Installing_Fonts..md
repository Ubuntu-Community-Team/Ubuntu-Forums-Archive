---
title: "Installing Fonts."
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Commander_Keen on 2008-10-10
HI.
  I thought I had posted this, but now I can not find it.
Anyway I was told that inorder to install fonts you have to create a new Folder called .fonts
  Now when that folder is created how does the OS, Kernal or applications pick up on that folder to use the fonts?

---

### Post by shifty_powers on 2008-10-10
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

has some useful info...

---

### Post by m_duck on 2008-10-10
Once you've put the fonts into the .fonts folder, open a terminal and run:```
fc-cache
```

---

### Post by b0b138 on 2008-10-10
create a font folder in your home directory
```
mkdir /home/user/.fonts
```

Now you can either put your fonts directly into that folder or create subfolders. ex.  /home/user/.fonts/msfonts

then run ```
fc-cache -fv
``` This will recache all the fonts so the new ones will be known.


Not to get offtopic, but, up at the top of the page next to "new posts" and "quick links" is "search" (not the box in the top right) with options to search for your posts/threads etc etc :)

---

### Post by Commander_Keen on 2008-10-10
I did search for my threads and posts, and could't find it.

But the main question was once you have created the new folder and placed the fonts in the folder, how does Open office know to use those fonts.
Now somebody suggested to use fc-cache -fv, now what does that command do?

---

### Post by Louis de Broglie on 2008-10-10
Is not it necessary to setup locals too? :)

---

### Post by Kellemora on 2008-10-10
Hi CK

I'm a noob, so the advice of others more experienced should be considered before anything I have to say, first.

I put ALL of my truetype fonts in the EXISTING font folder designed for same, and they all work without a problem, no matter WHAT I name them.
Probably due to the recognized names found within the font itself.

All I do is make a new folder inside of the truetypes folder.
It's located here 
/usr/share/fonts/truetype
I will make a NEW folder using Nautilus in Root and name it so I recognized the font name.  EG:  ttf-quickfonts-rumble
Then inside this folder I will copy and paste all the versions of that font.  EG. rumblebold.ttf, rumbleitalic.ttf, rumblenormal.ttf

By placing them here, instead of in a hidden folder in my /home directory, every user can use the fonts and programs have had no trouble finding them either.

I have 9 new fonts that I installed this way, 3 of them are proprietary fonts (meaning non-portable fonts in my case).  And all of them work perfectly with Open Office and other programs that use selectable fonts.

Easier to keep track of your fonts when they are all in one place too!

TTUL
Gary

---

