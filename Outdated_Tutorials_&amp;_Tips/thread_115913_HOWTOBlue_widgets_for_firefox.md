---
title: "HOWTO:Blue widgets for firefox"
date: 2006-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by art on 2006-01-11
EDIT:: Added the way to roll back to original

Hi forum
I just made little changes to the wonderfull winterfox widgets theme, and added to it the firefoxy buttons. This is for FF1.5 installed in /opt directory. 

[http://gnome-look.org/content/show.php?content=21812](http://gnome-look.org/content/show.php?content=21812)
[http://emps.l-c-n.com/downloads](http://emps.l-c-n.com/downloads)

The firefoxy doesn't work really well on my ubuntu, the location bar gets broken. So here it is. 

Download the winterfox, and  Prettywidgets-Linux.tgz
tar jxf winterfox-0.7.tar.bz2
tar zxf Prettywidgets-Linux.tgz

Installing winterfox: 
Make a backup 
sudo cp -r /opt/firefox/res /opt/firefox/res_bckp

After extracting winterfox you'll get a folder called res. 

cd ~/Desktop/res/
sudo cp -r * /opt/firefox/res
sudo cat /opt/firefox/res/winter.css >> /opt/firefox/res/forms.css 

Installing firefoxy buttons:
cd ~/Desktop/widgets-linux-P/for_1.5
sudo cp aguaButton_focus.png /opt/firefox/res/winter/button-bg-active.png
sudo cp aguaButton.png /opt/firefox/res/winter/button-bg.png
sudo cp radio.png /opt/firefox/res/winter/radio.png
sudo cp radio_checked.png /opt/firefox/res/winter/radio_checked.png
sudo cp droparrow.png /opt/firefox/res/winter/droparrow.png
sudo gedit /opt/firefox/res/forms.css 

and change 

/* --------------------------------------------
DROPDOWNS
-----------------------------------------------*/

select, 
select:not([size]),
select[size="0"],
select[size="1"] { 
	font-weight: normal !important; 
	color: black;
	background: **#efebe7 **url(winter/button-bg.png) repeat-x bottom right !important;

to 

/* --------------------------------------------
DROPDOWNS
-----------------------------------------------*/

select, 
select:not([size]),
select[size="0"],
select[size="1"] { 
	font-weight: normal !important; 
	color: black;
	background: **#f1f4f8** url(winter/button-bg.png) repeat-x bottom right !important;

I like it, hope you'll too... Here is a little screenie

If you didn't like it, here is how to roll back
sudo rm -rf /opt/firefox/res/* 
cd /opt/firefox/res/
sudo cp -r /opt/firefox/res_bckp/* .

---

### Post by adam.tropics on 2006-01-13
Nice. Cheers.

One problem (Ihad it before, but thought you might know) is that when i click find in page in firefox, the text area is to small to see the text! All I see is the top third of the letters, any ideas?

---

### Post by art on 2006-01-13
Well, I know what you are referring to, but as you see on thepicture below, I don't have it. I had it with the other widget theme, the Clearlooks one. So maybe if you have it installed, uninstall and try this one again.

---

