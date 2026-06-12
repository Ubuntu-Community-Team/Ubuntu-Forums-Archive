---
title: "Mouse / pointer / &quot;active area?&quot;  question"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by 440roadrunner on 2015-06-15
I   "ain't"  technical  in the  computereze world.   I had been running Mint Mate,  converted recently to the  Ubutu  Mate  distro,   Mate  1.8.2 

My question is  that   when trying to resize  a window,  it's difficult  to "capture"    the  side or corner of the window  with the mouse pointer.   As far as I can tell, this is not much  affected  by   pointer  size or style,  or by  the software  that is open.     I  don't remember this being  any issue  with the earlier  Mint  I ran.   Anyone have  idea?

---

### Post by kryten35 on 2015-06-15
Yes it is difficult to resize a window.Use CompizConfig which is in Ubuntu software centre .

Run compizconfig and go to Window management and click on resize window.

I have my mouse set to Alt + button 3   (right click) .Makes it a LOT easier.You only have to be near an edge or corner inside a window.

---

### Post by 440roadrunner on 2015-06-15
Thanks  for the comeback,  but that  looks  dangerous in my hands,  LOL.   May  now  I can google  Compiz   and  figure out what I'm doing.

---

### Post by mcduck on 2015-06-16
Alt-Right Button should already resize windows by default (or it might be Alt+Middle button.) At least it has always done that in Gnome, so I'd expect the default to have carried over to Mate as well.

Anyway, you are right, it doesn't depend on your cursor size (mouse cursor will always point to a single pixel). Instead the *window border theme* you are using does make a difference, some themes have wider borders, some have narrower ones. So if you don't want to use the Alt shortcut, then finding a wider-bordered theme would solve the problem.

---

### Post by 440roadrunner on 2015-06-16
Thank you,  I'll  try that.   In the meantime is there a way  to drag the developers through the mud  a bit on this?   Seems  like a basic  issue,  IE   the car you buy should come  with a gas pedal  large enough for your foot, LOL

---

### Post by mcduck on 2015-06-16
You could try, but it's unlikely you'd have any success. :D

It's not development issue, it's up to art&design team. And they have already provided people with a Compiz plugin (on Unity desktop) to make things easier, plus all the built-in mouse shortcuts etc. available on different desktop environments and window managers. Plus the ability to just switch to a different theme. 

Asking for Ubuntu to include alternative window theme with wider borders might get you somewhere. How well that works with Mate is a different question.

---

### Post by Dennis N on 2015-06-16
Use the resize option on the window menu and the cursor changes to the double arrow resize cursor positioned on the corner. It sticks there until done. You don't have to hold any buttons down while resizing. Click the mouse to return to normal cursor. On mine, it always uses the lower right corner for resize, however.

---

### Post by 440roadrunner on 2015-06-16
> **Dennis N said:**
> Use the resize option on the window menu and the cursor changes to the double arrow resize cursor positioned on the corner. It sticks there until done. You don't have to hold any buttons down while resizing. Click the mouse to return to normal cursor. On mine, it always uses the lower right corner for resize, however.

Actually   "for now"  that  is a fairly  easy  solution.   THANK YOU  very much!!!


On a  "side" note  (unrelated)  I just dragged home an  "all in one"   iMac  yesterday  to  "get my feet wet"  learning something about  "them,"  LOL

---

### Post by vasa1 on 2015-06-16
If you like a theme but it has thin borders, isn't it possible to edit something like ~/.themes/BlackMATE/metacity-1/metacity-theme-2.xml to make the borders thicker?

I see code like this:```
<?xml version="1.0"?>
<metacity_theme>
<info>
  <name>BlackMate</name>
  <author>Wolfgang Ulbrich (aka. NiceandGently aka raveit65)</author>
  <copyright>none</copyright>
  <date>April 2013</date>
  <description>A clean dark theme</description>
</info>

<!--================-->
<!--Frame Geometries-->
<!--================-->

<frame_geometry name="normal" rounded_top_left="true" rounded_bottom_left="true" rounded_top_right="true" rounded_bottom_right="true">
  [B]<distance name="left_width" value="2"/>
  <distance name="right_width" value="2"/>
  <distance name="bottom_height" value="6"/>[/B]
  <distance name="left_titlebar_edge" value="4"/>
  <distance name="right_titlebar_edge" value="4"/>
  <distance name="button_width" value="20"/>
  <distance name="button_height" value="23"/>
  <distance name="title_vertical_pad" value="3"/>
  <border name="title_border" left="1" right="0" top="4" bottom="4"/>
  <border name="button_border" left="1" right="0" top="4" bottom="0"/>
</frame_geometry>

```Edit: this is just speculation on my part. I haven't tried it myself.

---

