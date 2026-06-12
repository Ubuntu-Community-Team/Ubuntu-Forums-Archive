---
title: "python help with a gdesklet"
date: 2006-09-09
forum: Programming Talk
---

### Post by searayman on 2006-09-09
i am using the gdesklet gnome bar but don't like the notification area in it and want to take it out, so i am betting somehow you can change some line in the source code of it so it wont be there.here is what i want, i want to change this:

[IMG]http://3piclynk.com/out.php/i3768_1b6046ab538974f1dd1475115a4999b32.jpgworking.jpg[/IMG] 

to this:

[IMG]http://2piclynk.com/out.php/i3769_other.jpg[/IMG]

I have looked at the code and there is something in there about the notification area, and i was wondering if someone could edit the code for me to take out the notifications area, the point of doing that is to remove the white box on the gdesklet to make it look cleaner. Please help me i would really apreciate the help.

this is the source code for the gdesklet:

```
<?xml version="1.0" encoding="UTF-8"?>

<display id="gnomebar" window-flags="sticky, below" width="693" height="60">
	<meta author="Mark Dillavou and Sparrowhawk" name="Gnome Bar" version="2.0.2" preview="preview.png"
	        description="A Replacement for the Gnome Panels"
        	category="Toolbar/Misc"/>

	<control id="mytime" interface="ITime:7qktelp6tw29ve5p8q3lxn6bs-2"/>
	
	<!-- Left image with menu -->
	<image id="menuBg" uri="gfx/menubg.png"
		x="0" y="0"/>
	<!-- Foot Icon -->
	<image id="logo" uri="gfx/menu.png"
		x="2" y="2"/>
	<embed oafiid="OAFIID:GNOME_PagerApplet!prefs_key=/schemas/apps/workspace_switcher_applet/prefs;size=50;orient=PANEL_ORIENTATION_BOTTOM"
		x="56" y="3"
		width="72" height="48"/> 

 	<label id="timelabel" font="Sans 10" color="black" x = "135" y="3"/>
 	<label id="datelabel" font="Sans 10" color="black" x = "135" y="23"/>

	<!--embed oafiid="OAFIID:GNOME_ClockApplet"
		x="130" y="2"
		width="50" height="48"/-->	

	<!-- Taskbar -->
	<image id="taskBarBg" uri="gfx/middle.png"
		x="195" y="0"/>
	<embed oafiid="OAFIID:GNOME_TasklistApplet"
		height="24" width="450"
		x="200" y="2"/>
	<image id="taskbarEndBg" uri="gfx/middle-end.png"
		x="657" y="0"/>

	<!-- Icons -->
	<image id="iconbarBg" uri="gfx/iconbar-middle.png"
		x="195" y="28"/>
	<image id="icon1"	x="198" y="30"
		uri="gfx/nautilus.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon2"	x="228" y="30"
		uri="gfx/firefox.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon3"	x="258" y="30"
		uri="gfx/thunderbird.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon4"	x="288" y="30"
		uri="gfx/gaim.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>
	<image id="icon5"	x="318" y="30"
		uri="gfx/oowriter.png"
		on-enter="self.scale = 1.2"
		on-leave="self.scale = 1"/>

    <script><![CDATA[

    date_format = "%d. %m"
    
    def get_time(mytime):
    
        h, m, s = mytime
        Dsp.timelabel.value = "%02d:%02d.%02d" % (h, m, s)

    def get_cal(mydate):

        y, m, d = mydate
        out = date_format.replace("%m", `m`) \
                         .replace("%d", `d`)
        Dsp.datelabel.value = out

    mytime.bind("time", get_time)
    mytime.bind("date", get_cal)

    Dsp.icon1.on_click = "launch('nautilus')"
    Dsp.icon2.on_click = "launch('firefox')"  
    Dsp.icon3.on_click = "launch('thunderbird')"
    Dsp.icon4.on_click = "launch('gaim')"
    Dsp.icon5.on_click = "launch('oowriter')"

  ]]></script>

	<image id="iconbarEndBg" uri="gfx/middle-end.png"
		x="345" y="28"/>

	<!-- Notification Area -->
	<image id="systrayBg" uri="gfx/iconbar-middle.png"
		x="375" y="28"/>
	<embed oafiid="OAFIID:GNOME_NotificationAreaApplet"
		x="379" y="29"
		height="24" width="110"/>
	<image id="systrayEndBg" uri="gfx/middle-end.png"
		x="525" y="28"/>
  <prefs>

  <page label="Date, Time, Logo">

    <uri label="Logo Image:" bind="Dsp.logo.uri" help="Images 
should be no larger than 50 x 50 pixels."/>

    <boolean label="Show Time" bind="Dsp.timelabel.visible"/>
    <boolean label="Show Date" bind="Dsp.datelabel.visible"/>

    <color label="Time Color:" bind="Dsp.timelabel.color"/>
    <color label="Date Color:" bind="Dsp.datelabel.color"/>

    <font label="Time Font:" bind="Dsp.timelabel.font"/>
    <font label="Date Font:" bind="Dsp.datelabel.font"/>

  </page>

  <page label="Applications">

    <string label="Application 1:" bind="Dsp.icon1.on_click"/>
    <string label="Application 2:" bind="Dsp.icon2.on_click"/>
    <string label="Application 3:" bind="Dsp.icon3.on_click"/>
    <string label="Application 4:" bind="Dsp.icon4.on_click"/>
    <string label="Application 5:" bind="Dsp.icon5.on_click"/>
  
```

---

### Post by scxtt on 2006-09-09
i don't see any reason why you couldn't change it to:
```
	<!-- Notification Area
	<image id="systrayBg" uri="gfx/iconbar-middle.png"
		x="375" y="28"/>
	<embed oafiid="OAFIID:GNOME_NotificationAreaApplet"
		x="379" y="29"
		height="24" width="110"/>
	<image id="systrayEndBg" uri="gfx/middle-end.png"
		x="525" y="28"/> -->
```in order to comment it out - or honestly just back it up and delete those lines ...

---

### Post by searayman on 2006-09-09
scxtt you fix worked perfectly i copied your code adjustment and deleted that section in mine and put this in and bam!! it worked yippy!! thanks a bunch!

---

