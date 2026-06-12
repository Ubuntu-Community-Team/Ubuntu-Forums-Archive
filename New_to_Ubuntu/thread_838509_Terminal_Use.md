---
title: "Terminal Use"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Pudworthy on 2008-06-23
Forgive me, this one really is newbie-ish

I'm trying to navigate around using the terminal, but having a slight problem navigating around my home directory. I can get to my directory, but after that I can't go any further...

lloyd@Lloyd:~$ dir
01\ Time\ To\ Pretend.mp3      DSC04386.JPG	       Other	      Templates
04\ Love\ Always\ Remains.mp3  Examples		       Pictures       Videos
bond.bmp		       Little\ bit\ giddy.jpg  Public
Desktop			       message.ubugrey	       qu2E5.tmp.jpg
Documents		       Music		       sakE6.tmp.jpg
lloyd@Lloyd:~$ cd music
bash: cd: music: No such file or directory
lloyd@Lloyd:~$ 

Terminal can see my directories, but I can't get into them. What stupid thing am I missing?

P

---

### Post by jualin on 2008-06-23
In Linux > cd Music and > cd music are not the same thing. Capitalization is important. So that's what you are missing. Don't worry about it, we have been there before.

---

### Post by sdennie on 2008-06-23
Unix is case sensitive.  "music" is not the same as "Music".  I think you need to:

```

cd Music

```

---

### Post by Zulu-Zeffir on 2008-06-23
Linux is case sensitive.  Meaning Music and music are different.
Try cd Music
and use ls instead of DIR

---

### Post by TeoBigusGeekus on 2008-06-23
Here is a good site to get you started with the terminal
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by Pudworthy on 2008-06-23
*Shame on me*
Thanks though.
:p hey, we all start somewhere.

P

---

### Post by sdennie on 2008-06-23
You can actually get a certain level of case insensitivity by making tab completion case insensitive.  Create a file called ~/.inputrc and add the following to it:

```

set completion-ignore-case on

```

Close your terminal window and open a new one.  Now you can type:

```

cd m

```

And hit tab and it will complete to "cd Music".

---

### Post by jualin on 2008-06-23
Nice one dude! Did not know about that, thanks

---

### Post by RiceMonster on 2008-06-23
just some quick advice on using ls:

use ls -a to see hidden files
use ls -ln to see file permissions
and if the list is too long to be displayed on the screen us ls | less (works with -ln, -a, etc). Scroll up and down with the arrows and hit q to exit.

---

### Post by Fingers &amp; Thumbs on 2008-06-23
> You can actually get a certain level of case insensitivity by making tab completion case insensitive. Create a file called ~/.inputrc and add the following to it:

That's gotta be one of the best bits of advice I've heard, I'm forever swearing at myself for inputting the wrong case, #1 Productivity booster, nice one.

---

