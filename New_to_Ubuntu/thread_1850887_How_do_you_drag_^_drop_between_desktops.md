---
title: "How do you drag ^ drop between desktops?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by suomalainen on 2011-09-27
Ubunteros,

I have 10.04 installed and I use to be able to drag and drop open applications between desktops.

How do you activate this service?

Thank you!

---

### Post by Krytarik on 2011-09-27
If you are using the "Desktop Wall", enable the option "System -> Preferences -> CompizConfig Settings Manager -> Desktop Wall -> Edge Flipping -> Edge Flip Move". If you want the same behaviour for objects, enable the option "Edge Flip DnD" right below of it as well.

Therefore, you obviously need CCSM to be installed (package "compizconfig-settings-manager").

Greetings.

---

### Post by suomalainen on 2011-09-27
Thanks Krytarik!

I did what you said and all appropriate boxes are ticked but it still isn't working. Not even after reboot.

:(

---

### Post by Krytarik on 2011-09-27
> **suomalainen said:**
> I did what you said and all appropriate boxes are ticked but it still isn't working. Not even after reboot.
Are you sure that Compiz is even running?
"System -> Preferences -> Appearance -> Visual Effects" set to anything other than "None"?

Also, do you have even set up multiple workspaces under "CompizConfig Settings Manager -> General Options -> Desktop Size"?

---

### Post by suomalainen on 2011-09-27
@Krytarik I got everything set just like that and it still doesn't work. I really can't figure it out...

---

### Post by Krytarik on 2011-09-27
> **suomalainen said:**
> I got everything set just like that and it still doesn't work. I really can't figure it out...
Well, if that's really the case, I have no idea either, sorry! As you can see in my profile, I'm running Lucid 10.04, too; and it works here.

---

### Post by suomalainen on 2011-09-27
THANK YOU to everyone who helped lead me in the right direction toward a solution.

I can drag and drop applications between desktops now.

And believe it or not I followed this instruction:

"System -> Preferences -> Appearance -> Visual Effects" set to "None"?

Thanks again to you all!

Bye!

---

### Post by Kixtosh on 2011-09-27
> **suomalainen said:**
>  ...I can drag and drop applications between desktops now.

And believe it or not I followed this instruction:

"System -> Preferences -> Appearance -> Visual Effects" set to "None"? ...
Would you mind explaining how you got it to work, for my benefit (and possible the benefit of other users)?

Thanks!

---

### Post by suomalainen on 2011-09-27
I got it working like this

If you are using the "Desktop Wall", enable the option "System -> Preferences -> CompizConfig Settings Manager -> Desktop Wall -> Edge Flipping -> Edge Flip Move"

"System -> Preferences -> Appearance -> Visual Effects" set to "None"?

---

### Post by Kixtosh on 2011-09-27
Thank you for your response. I think I must be missing something (Ubuntu 10.04 Lucid Lynx), since even when I set *System > Preferences > Appearance > Visual Effects* to "E_x_tra", I still don't have a list item in the Preferences menu for "CompizConfig Settings Manager".

Right now, I just right click on the panel label for the window in question, and then select "Move to Another Workspace". I was just hoping for a more keyboard or mouse friendly (not to mention expedient) method.

---

### Post by Krytarik on 2011-09-27
> **Kixtosh said:**
> I still don't have a list item in the Preferences menu for "CompizConfig Settings Manager".
As mentioned in my initial post, you need to install CCSM first:
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Kixtosh on 2011-09-27
Thank you, that's my missing part! I'll try it out.

EDIT:

It didn't take long. Very easy to do, and now I can:

[LIST=1]
[*] Press the "Windows" <Super> key and <E> key at the same time, to show the desktop wall.
[*]Then drag and drop application windows from any available desktop to another, including the "extended" desktop area (laptop display, or LCD external monitor).
[*]Press the <Super> and <E> keys again to "release" the desktop wall and return to normal use.
[/LIST]
Very nice. Thank you gentlemen! The thread is doubly "solved" now!

... ;)

---

### Post by suomalainen on 2011-09-28
My visual effects is set to none.

---

