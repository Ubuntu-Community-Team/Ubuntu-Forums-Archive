---
title: "How to make Ubuntu Tablet-Friendly (3: Configuration Panel)"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ErkDemon on 2011-08-24
One of the current weaknesses with Ubuntu regarding tablets is its lack of a tablet configuration control panel page. 

There's four main reasons for having one of these:

[LIST=1]
[*]So that users can configure their tablet hardware, and any related space-optimisation features like font sizes, from a single friendly location,
[*]So that even if the users never touch the control panel, they have the reassurance of knowing that it's there, and that the OS devleopers have invested some effort in looking after the needs of the tablet community,
[*] The act of writing and bug-testing the panel GUI forces developers to confront any outstanding problems with tablet functions that might previously have been swept under the carpet, and,
[*] If you want hardware manufacturers to start preinstalling Ubuntu on tablets, it's useful to be able to show them evidence that the OS "has its act together" when it comes to tablet hardware. Windows has probably had a tablet control panel for the last ten years or so.
[/LIST]
    
Canonical are trying to promote Ubuntu to tablet builders, but if they'd tried writing a control panel for tablet devices, they'd have quickly realised that the default distributions of 10.x and 11.04 simply don't work properly even on old IBM/Intel/Wacom hardware. It's not to difficult to fix ... once you realise that you have to write your own scripts, that most of the information on the web is outdated and refers to systems that aren't on the current release of Ubuntu, and that you'll essentally have to modify the online script exmaples to get them to work, if you want stuff like portrait mode to work properly on recent Ubby relweases.

If I was a hardware manufacturer, and someone assured me that Ubuntu was a good option for tablets, and I downloaded 11.04, tried it on the most standard hardware I could think of, and realised that to get it to work required a page of scripting and custom commandline stuff, and that none of the online documentation seemed ot work with OS versions released in the last 18 mionths, then I'd run like heck into the arms of Win8 or Android and want to have nothing to do with Ubuntu ... not because the problems aren't fixable, but because the developers wouldn't seem to have bothered maintaining basic tablet functions in a workable state for the last year and a half, and that's worrying if you'll be trying to sell a tablet product based on that OS. While the rest of the world has been going tablet-crazy, Ubuntu doesn't even have a subject category for them on its forum.

I we'd like Ubuntu to be a player on mobile devices, and not simply hand the "pro tablet" market to Win8 by default because we don't have a working competing product, then there probably needs to be some sort of initiative to focus people's minds, afresh. Building a tablet control panel might be the way to do it. And as a bonus, Ubuntu would get a shiny new GUI feature.

---

### Post by jbicha on 2011-08-24
What should be in this Tablet Settings app? The only thing you specifically mentioned was "font size" which is already partially configurable in System Settings>Universal Access.

---

### Post by ErkDemon on 2011-08-27
> **jbicha said:**
> What should be in this Tablet Settings app? The only thing you specifically mentioned was "font size" which is already partially configurable in System Settings>Universal Access.

I was thinking of the sorts of setup pages that we currently have for keyboard and mouse functions, you know, where you set double-click rates and the like. For instance, my ThinkPad supposedly has an accelerometer onboard, but I have no idea whether it works, what its features are, whether the driver reads it properly or whether the OS is in proper communication with the driver. For a full tablet, it might be nice to link accelerometer events to custom actions, like having the tablet go into sleep mode when you put it face-down. At the moment if you want to do that you probably have to write your own scripts (and good luck with debugging).
So ...

(1) Accelerometer 
* Feature listing and diagnostics
* Event assignment (like whether you want the screen to automatically change orientation dependign on how it's held).
* Driver details (probably hidden behind an "Advanced ..." button, also for all subsequent sections)

(2) Front panel and edge hardware buttons
* Listing and diagnostics
* Event assignment (what happens when you press them, handy if you want "check email", or "view schedule" buttons).

(3) Stylus, stylus buttons and stylus functions
* Listing, diagnostics and event assignment ... all probably already handled by the software that came with the driver.

(4) Other Sensors (stylus bay sensor, ambient light sensor, docking port sensor, headphones plug sensor, etc.)
* Listing and diagnostics
* Event assignment (you might want to launch a graphics app when you take out the stylus, or mute audio when you clap your hand over the front of the device, shading the light-sensor)

(5) GPS/ Compass/ other location devices
* Listing and diagnostics
* Event assignment (maybe enable or disable certain things when you're at the office, or at home).

(6) Screen Rotation
* Event assignment (launching further events when the screen orientation rotates)
* Graphics (optionally briefly blank the display or show a graphic or animation when rotating, to hide the messy screen redraws) 
* Optional link between screen orientation 1-4 and workspaces
* Optional application launcher/refresh when moving to specific orientations
* Overrides for which pointing devices and cursor buttons should rotate with the screen, and which shouldn't.    

(7) Default helper apps
* Listing launcher and settings for onscreen keyboard, journalling software, gesture control, etc.
 
(8) Gesture control
* Listing (and perhaps editing) the main default navigation gestures.

(9) Screen optimisations
* Use or don't use Unity
* Use or don't use new "needle" scrollbars
* use or don't use other screen-space optimisations   

There's going to be other functions that I can't think of right now, and some mobile devices are going to have other exotic sensors and outputs (vibration alarm? haptic feedback? camera light?), but the list's probably already a bit long. Some of this stuff might actually be useful, for instance, you might want the camera light to start blinking on your docked tablet as a silent alarm when you have an incoming work email.

But we'd need some way to connect all these inputs and outputs together at the system level and test that it all works, without asking the user to write a plethora of scripts or use a slew of different applications, none of whom know that the others exist. 

It might also be useful to load and save complete sets of settings as a file or folder, so that once someone's got a nice set of settings for a specific device, they can share them, or so they can experiment without losing the "factory" setup. If it's a folder, then it might also be nice to include a line drawing of the particular tablet model that the setup was for. With configurable setups that let you add user-names to items, you could download a setup designed for your specific tablet, and have all the custom hardware buttons and features pre-named for you.   

Eric

---

### Post by Favux on 2011-08-27
Part of what you are asking for has been implemented albeit in a scattered form.

For example there was some recent work adding some Wacom keys to the gnome-settings-daemon so they would be available to the gnome-control-center:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools)  And of course the Synaptic touchpad gui could be looked at.

---

