---
title: "GDM PreSession Edit---Extend the splash screen?  get rid of that #dab082 tan color"
date: 2008-03-30
forum: Programming Talk
---

### Post by SaikoRonin on 2008-03-30
I recently installed a gdm theme and a splash and got that working nicely.  However I noticed the Tan color popping up before and after the splash.

I looked at other posts and found a way to minimize this annoyance, 

Going into /etc/gdm/PreSession/Default 

Then changing the hex value for the backcolor from #dab082 to #000000(black)
```

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"
 	fi
```

Now Im kind of new to ubuntu and I cannot program at all, and this is where I need help.

I would like to change the backcolor to an image file, and basically extend the splash screen so that you would never see the plain "color" screen at all. Which would make a much smoother looking boot up.

It should be a simple code to do that,  However if we wanted to get technical with it we could figure out a way to actually pull the file location of the users splash screen image and put it right into the code so that less tech savvy people wouldn't have to go into the file to edit it.  And this could be an update, or it would save us from having to edit the file every time we change splash screens.

Im sure a lot of people would find this bit of code useful, and if I knew any coding I'd write it myself.


---l- Ronin

---

### Post by mssever on 2008-03-30
I'm not too familiar with xsetroot, but it appears that line 64 is the place where you'd set the image. The problem, though, is that this is the PreSession script, which is run **before** the session is started. So setting a graphical background here wouldn't be straightforward, because you're running as root, not the user, and there's only one script for all users. See [http://www.jirka.org/gdm-documentation/x241.html](http://www.jirka.org/gdm-documentation/x241.html) for more info.

---

### Post by SaikoRonin on 2008-03-30
hmm now I am confused.  That file says
 > 
PreSessionScriptDir

    PreSessionScriptDir=<etc>/gdm/PreSession

    Directory containing the scripts run before the user logs in. See the ``The Script Directories'' section for more info. 


Now this all takes place after the user login.  I don't understand why changing the x background color at that time will affect it after the login.  Unless the splash gets killed before loading desktop background, and the background color is underneath the whole time...

Now if thats the case then it might be better to load the desktop background first and get rid of the splash altogether and avoid the whole, color-Splash-color-Desktop process... Maybe I'm over thinking this now.

---

### Post by mssever on 2008-03-31
On re-reading your post, it appears that you want to extend the splash screen so that it begins immediately after login. Is that correct? If so, the problem is nontrivial, because the splash screen is the responsibility of stuff started in the Xsession script, which is run *after* PreSession. I believe the splash screen is started by gnome-session or something it launches.

[quote=SaikoRonin] 		hmm now I am confused.  That file says
  	Quote:
 	 	 		 			 				PreSessionScriptDir

    PreSessionScriptDir=<etc>/gdm/PreSession

    Directory containing the scripts run before the user logs in. See the ``The Script Directories'' section for more info.  			 		 	 	 
Now this all takes place after the user login. I don't understand why changing the x background color at that time will affect it after the login. Unless the splash gets killed before loading desktop background, and the background color is underneath the whole time...

Now if thats the case then it might be better to load the desktop background first and get rid of the splash altogether and avoid the whole, color-Splash-color-Desktop process... Maybe I'm over thinking this now.[/quote]I don't understand what you're saying here...

---

### Post by SaikoRonin on 2008-03-31
Yeah I don't know the first thing about programming.  I'm trying to learn but some stuff confuses me.  Just ignore that post.

And I think you may be right, and what i was talking about doing was getting the PreSession to load the splash instead of a color so that it jumps the splash in earlier in the process, would I just be able to change the tag from say "backColor" to the command for a background like 


```
	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKGROUND="/media/sda2/SplashitySplash.PNG"
 	fi
```

or something along those lines?  Im just talking about making it execute the command in the Presession instead of later, 

Or maybe just loading the background at that point and just doing away with the splash

---

### Post by mssever on 2008-03-31
> **SaikoRonin said:**
> Yeah I don't know the first thing about programming.  I'm trying to learn but some stuff confuses me.  Just ignore that post.

And I think you may be right, and what i was talking about doing was getting the PreSession to load the splash instead of a color so that it jumps the splash in earlier in the process, would I just be able to change the tag from say "backColor" to the command for a background like 


```
    # Default value
     if [ "x$BACKCOLOR" = "x" ]; then
         BACKGROUND="/media/sda2/SplashitySplash.PNG"
     fi
```or something along those lines?  Im just talking about making it execute the command in the Presession instead of later, 

Or maybe just loading the background at that point and just doing away with the splash

You might be able to set the background--though it probably won't work if you do it that way. I think you'll have to modify the xsetroot command on lne 64. Of course, a simple modification might work well for a single user machine (and so it might be good enough for you), but it isn't a general solution; that would be more complex.

I suspect that the right thing to do would be to simply make PreSession run faster, then set the background and/or splash as soon as possible in Xsession or perhaps more properly, in ~/.xsession.

---

