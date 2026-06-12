---
title: "[SOLVED] Change default buttons"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-30
I want to change the top left (ubuntu logo) and bottom left buttons (show desktop) for ubuntu. I downloaded [this](http://www.gnome-look.org/CONTENT/content-pre1/45987-1.jpg) skin, and in the top left corner it says "distributer logo". The theme came with that button, but I'm not sure how to change it. any help?

---

### Post by sayakb on 2008-06-30
Can you make it a bit more clear? Have you also downloaded this icon set shown in the image and are you **using** the downloaded icon set?

---

### Post by Bodsda on 2008-06-30
If you downloaded an icon set, the images are stored in ~/.icons.

Go to the scalable folder

~/.icons/<???>/scalable/places

<???> should be the name of your icons set, just browse with nautilus

once your there, or found the icon in a different folder, replace the icon called 

'start-here.png'

with an icon you want, then in a terminal type

```
killall gnome-panel
``` 

Your icon should now be there.

Hope this helps.

---

### Post by adobrakic on 2008-06-30
Yes, i have downloaded it. The thing is that I'm not sure how to implement it. I still have the default ubuntu icon. The button shown in the picture came as a .png, and if you'd like me upload it, i can. 

I also have another question. A folder titled "CgwdThemes" came with the download and the following files are inside of it:

```

truth_border.cgwdtheme
truth_noborder.cgwdtheme
truthround_noborder.cgwdtheme

```

I tried applying these in Appearance, just to see what it is, but I had no luck.

--edit--

> 
~/.icons/<???>/scalable/places


I tried finding this on my computer (well I tried finding the /.icons/ folder), but I'm not sure where it is. 
Sorry, i'm still new to linux. :x

---

### Post by sayakb on 2008-06-30
Open your Home folder and press Ctrl+H to reveal the hidden .icons folder

Icons to modify:
~/.icons/<name>/22x22/places/start-here.png
~/.icons/<name>/22x22/places/desktop.png

Do modify the icons of other sizes.

---

