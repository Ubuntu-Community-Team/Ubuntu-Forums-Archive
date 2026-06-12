---
title: "resizing windows"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by il_maniscalco on 2012-01-18
one of the nastiest things compared to windows is that I really don't like nor the resizing borders for the windows (too narrow I barely manage to resize) and also the scrollbars, which I'd like to be windows-like (larger I don't care they take a bit of space).

how to configure?

---

### Post by cortman on 2012-01-18
> **il_maniscalco said:**
> one of the nastiest things compared to windows is that I really don't like nor the resizing borders for the windows (too narrow I barely manage to resize) and also the scrollbars, which I'd like to be windows-like (larger I don't care they take a bit of space).

how to configure?

It depends what DE you're using. If you're using Gnome shell, it's not difficult- see this quote, and the link at the bottom.

> As stated previously, the default GNOME Shell theme is Adwaita. You can modify this theme by editing /usr/share/themes/Adwaita/metacity-1/metacity-theme-3.xml. 

If you are already using the GNOME Shell, you probably have noticed that it is difficult to grab the frame of a window to stretch it. This is because the frame is only 1 pixel wide at the sides and 2 pixels in height on the bottom. To make windows easier to grab, I suggest you change each of these values to 3, 3 and 5 respectively. If you want a less intrusive titlebar, I suggest you change the value of title_vertical_pad to 8.


<distance name="left_width" value="3" />
<distance name="right_width" value="3" />
<distance name="bottom_height" value="5" />
<distance name="title_vertical_pad" value="8"/>


Read more: [http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html#ixzz1jp2SGblU](http://blog.fpmurphy.com/2011/03/customizing-the-gnome-3-shell.html#ixzz1jp2SGblU)

(from FP Murphy's blog)

---

### Post by il_maniscalco on 2012-01-18
fantastic that was just what I needed :)
thanks.

---

### Post by cortman on 2012-01-18
> **il_maniscalco said:**
> fantastic that was just what I needed :)
thanks.

Great. And as far as scrollbars, I think you can find instructions [here.]("http://askubuntu.com/questions/34214/how-do-i-disable-overlay-scrollbars")

---

### Post by il_maniscalco on 2012-01-18
I have some doubt about these scrollbars because I like the concept behind, but, there's Eclipse that's one of my main application, which doesn't implement them well (I mean, that don't work in any way). has anyone noticed this and perhaps solved it?

---

### Post by JimSP on 2012-01-18
i'd like to try this too. I have installed 11.04 off an ISO from the official site. Other than all the ususal downloads, i don;t think i changed anything. How do i tell if i am using Gnome?

---

### Post by audiomick on 2012-01-18
@ Cortman: thanks for that. That is something that has been irritating me for a while, too. I'll have a look at that when it is not so late at night. ;)

---

### Post by cortman on 2012-01-19
> **JimSP said:**
> i'd like to try this too. I have installed 11.04 off an ISO from the official site. Other than all the ususal downloads, i don;t think i changed anything. How do i tell if i am using Gnome?

Open a terminal and type

```
echo $DESKTOP_SESSION
```

---

### Post by JimSP on 2012-01-19
> **cortman said:**
> Open a terminal and type

```
echo $DESKTOP_SESSION
```

it comes back with

ubuntu

so where does that leave me? i have read last issue of ubuntu user and it's a lot to keep straight, all the various desktops etc 

still would like to know if i can implemnet the above commands to resize the edge of the windows and get scroll bar to work like i am used to.  will the commends work with the desktop i have. thanks for any help

---

### Post by cortman on 2012-01-19
> **JimSP said:**
> it comes back with

ubuntu

so where does that leave me? i have read last issue of ubuntu user and it's a lot to keep straight, all the various desktops etc 

still would like to know if i can implemnet the above commands to resize the edge of the windows and get scroll bar to work like i am used to.  will the commends work with the desktop i have. thanks for any help

A return of "ubuntu" means you're running Unity 3D, Ubuntu's own DE.
I don't think there's a way to resize the grab handles in Unity. See [this link]("http://askubuntu.com/questions/69379/how-do-i-make-the-window-resize-border-bigger") for more info on that. I think you should be able to change the scrollbars using the info in the link I provided in post #4. Good luck with Ubuntu, and feel free to post any questions you might have!

---

