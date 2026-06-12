---
title: "how to change window border width??"
date: 2007-05-10
forum: New to Ubuntu
---

### Post by fuzz500 on 2007-05-10
Hello All,
I've got a nice dual monitor setup running feisty at 3200 px wide, and I find the borders on metacity windows are very very tiny and hard to grab if I want to do a window resize... I've been searching everywhere to find out how to increase the window border width. This must be a very well kept secret!!

Any suggestions? How do you specify your window border width??

regards, 
Fuzz

---

### Post by cmcginty on 2009-11-05
[https://bugs.launchpad.net/metacity/+bug/160311/comments/11](https://bugs.launchpad.net/metacity/+bug/160311/comments/11)

> 

It is relatively painless to change the dimensions of the surrounding border for themes. That said, you may end up with a gaudy looking heavy window, but I assume that you don't care about that.

To change border widths, simply open up the theme's Metacity XML file. For example, Human's theme is located in /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

The stanza in question should be apparent:
  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

Try mucking with the values until you get something you are happy with. Unfortuanately, resolution dependency still plagues much of Gnome.

---

### Post by Sef on 2009-11-06
Moved to ABT.

---

### Post by StefQube on 2010-08-19
A much easier way:  ( for Absolute Beginner Talk ! )

In Gnome:
    System / Preferences / Appearance / Theme / Customize / Window Border

[SIZE=1]That was originally posted by ozar here:
[COLOR=Blue]    [http://www.linuxforums.org/forum/ubuntu-help/151537-how-change-very-wide-window-borders.html](http://www.linuxforums.org/forum/ubuntu-help/151537-how-change-very-wide-window-borders.html)
[/COLOR][/SIZE]
I got up to 6 pixel border width from :
    System / Preferences / Appearance / Theme / Customize / Window Border <==> Atlanta

Before "Atlanta" I had "Radiance" which was only 1 pixel wide. This is a six fold improvement for my big screen.
And then, I piked the controls, then the colors ... looks so much better!
    System / Preferences / Appearance / Theme / Customize / controls <==> "Dust Sand"
    System / Preferences / Appearance / Theme / Customize / colors (...click on one)

Well, if you need, say, 12 pixels width, you may still be stuck with a file to edit as per the link above from : cmcginty, or maybe you can download a package or a theme...?
__________________
hope this helps, :D

---

### Post by choikwa on 2010-10-18
You can just go to system>Preference>appearance>windowborder>get themes online and download one that suits ur taste.

---

### Post by cmcginty on 2010-10-19
Changing the theme is a little drastic, I don't like the other window border themes.
[I]
Q: How do I make my car drive better?
A: Sell it and buy a BWM.[/I]

---

### Post by eddybeerke on 2012-09-25
> **cmcginty said:**
> [https://bugs.launchpad.net/metacity/+bug/160311/comments/11](https://bugs.launchpad.net/metacity/+bug/160311/comments/11)
Its value was "1" (I think they are pixels) I set it to "3":
<distance name="left_width" value="3"/>
<distance name="right_width" value="3"/>
<distance name="bottom_height" value="3"/>

---

### Post by nothingspecial on 2012-09-25
Old thread.

Closed.

---

