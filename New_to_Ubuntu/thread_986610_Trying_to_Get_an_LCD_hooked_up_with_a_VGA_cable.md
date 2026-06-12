---
title: "Trying to Get an LCD hooked up with a VGA cable"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Thirdman03 on 2008-11-18
So I already have an LCD monitor, Ubuntu, and a VGA cable. I want to be able to display pictures on my hard drive onto the TV screen. Windows does this perfectly on my computer with the press of Fn + F8, so I'm wondering if there's something very specific about Linux that someone could help me with. I can give more specifics about the computer, but since I get it to work with Windows and not Linux, I think there's probably something fundamental going on that's preventing it from working.
The only clue I may be able to give is that when I switch to Presentation Mode on Windows, it automatically resizes my resolution to something different than 1200x800 (but it is hard for me to figure out what since windows told me through the settings it was still 1200x800). Therefore, I tried messing with the resolution manually in Linux before pressing Fn + F8, but no matter what I try it won't work.
Can someone please help?

---

### Post by PierreDeKat on 2008-11-18
Not sure if I'm getting this right, but assuming you have Eye of GNOME installed and setup as your default picture viewer, you can browse Nautilus to a folder full of pictures.

Double click on an image to launch Eye of GNOME and view the picture you clicked. Then go to "View" and tick "Slideshow". And this should give you a slideshow of the pictures in that folder.

You can go to "Edit"->"Preferences" and set the how long you want to display each image and set the slideshow to "Expand images to fit screen".

Is this what you're trying to do?

---

### Post by Thirdman03 on 2008-11-24
Actually, I'm still trying to get the screen to output on a TV. Using VGA cables, I want the image normally on my laptop screen to be sent to the television set.

I'm not asking for any help on making slideshows.

Thanks for the response.

---

### Post by twisted_steel on 2008-11-24
I just did a presentation the other day on a laptop with VGA output.  Rather than use the System -> Preferences -> Screen program, which seemed a little clunky, I read up on xrandr.  It its command-line based, but actually works.

To find out if the LCD is recognized, plug it in and enter
```
xrandr -q
```With any luck, you will be able to see your TV listed.  I could on my laptop that has an ATI video card, though I was using the open source driver.  I believe the output of that command on my laptop showed LVDS for the local screen and VGA-0 for the other monitor.

[This page]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Using__.24_xrandr") is Thinkpad-specific, but it should help you if you can see anything from xrandr in the first place.  I believe the command I finally used to force both my laptop and the projector to use 1400x1050 was
```
xrandr --output LVDS --mode 1400x1050 --output VGA-0 --mode 1400x1050
```There is an auto option that I never tried.  Down the page, you can find a script to make the shortcut keys work properly, but I haven't tried that personally.

---

### Post by Thirdman03 on 2008-11-29
I'm not sure that the xrandr is working to detect the LCD monitor. Here is what I get from running: xrandr -q.

Screen 0: minimum 320 x 240, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       50.0* 
   1024x768       51.0  
   800x600        52.0  
   800x512        53.0  
   720x450        54.0  
   700x525        55.0  
   640x512        56.0  
   640x480        57.0     58.0  
   640x400        59.0  
   640x384        60.0  
   512x384        61.0  
   400x300        62.0  
   320x240        63.0  

Also, I have NVIDIA, not ATI, so I'm not sure if being a proprietary driver it does not want to work. Thanks for above and let me know if I can try something else. I'll keep reading through the Xorg site you linked to.

---

### Post by twisted_steel on 2008-12-04
I just read today that xrandr support is coming to the proprietary NVIDIA driver.  I guess this means that it is currently unsupported.  The page also states that managing displays was previously done with either the 'nvidia-settings' command line program or via the NVIDIA GUI.  Maybe there are options in there for remote displays?  I know I have an NVIDIA card on my desktop and used the GUI to set up dual monitors.

Here is the link to the news: [http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw](http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw)

---

### Post by SamNSane on 2008-12-05
> **twisted_steel said:**
> I just read today that xrandr support is coming to the proprietary NVIDIA driver.  I guess this means that it is currently unsupported.  The page also states that managing displays was previously done with either the 'nvidia-settings' command line program or via the NVIDIA GUI.  Maybe there are options in there for remote displays?  I know I have an NVIDIA card on my desktop and used the GUI to set up dual monitors.

Here is the link to the news: [http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw](http://www.phoronix.com/scan.php?page=news_item&px=NjkwMw)

I'm afraid I have nothing useful to add regarding the problem listed in the OP.

But, in reference to the news about the proprietary nVidia drivers finally having xrandr support --- well, about cotton-pickin' time, nVidia!

Thanks for posting that link!

---

### Post by Thirdman03 on 2008-12-17
Thanks. Not solved yet, but thank you sincerely.

---

### Post by Paqman on 2008-12-17
If you're using the Nvidia driver you should be able to go to System > Admin > Nvidia X-Server Settings and set up your TV there. Just hit "detect displays" when you've got it plugged in and set it up as an additional screen.

---

### Post by starcannon on 2008-12-17
a work around I use on some of my laptops to use external displays (T.V.'s, projectors, or what-ever) is to:

[LIST=1]
[*]press an arrow key at the grub screen
[*]press my FN+external_key button combo till I get what I want
[*]Let it boot up
[*]Set my external screen resolution as per normal once I'm at a desktop.
[/LIST]

---

