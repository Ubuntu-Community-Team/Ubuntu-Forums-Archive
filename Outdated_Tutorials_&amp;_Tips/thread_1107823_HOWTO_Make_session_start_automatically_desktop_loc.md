---
title: "HOWTO: Make session start automatically desktop locked from GDM"
date: 2009-03-27
forum: Outdated Tutorials &amp; Tips
---

### Post by jis on 2009-03-27
If you use GDM as login manager (or should I say display manager), administrator has an option to set automatic instant or timed login for a user by gdmsetup. Coupling that with instant screen locking can be a tempting option especially, if hibernation does not work in your system.

In order to make such automatic screen locking work in Xfce session, I added some code to xinitrc script that is run in startup of Xfce session. See [here]("http://wiki.xfce.org/tips#how_to_customize_starting_xfce")  for more about customizing xinitrc. I noticed that gnome-screensaver daemon has to be launched little bit differently to be instantly usable; later I ended up rewriting the section that starts a screen saver daemon, to make it easier for an administrator or a user to configure preferred screen saver. My script would replace the code that starts screen saver daemon within the if-block in the default xinitrc, such as lines 104-108 in this trunk [revision]("http://svn.xfce.org/index.cgi/xfce/xfce-utils/trunk/scripts/xinitrc.in.in?revision=29670&view=markup"). So here is the new code:
```

   #### Choose your preferred screensaver here; options are "" for none, "gnome-screensaver" and "xscreensaver" 
   PreferredScreensaver="gnome-screensaver"

   case "$PreferredScreensaver" in
    xscreensaver )
        if test -n "`which xscreensaver 2>/dev/null`"; then
           xscreensaver -no-splash &
        fi
    ;;
    gnome-screensaver )
        if test -n "`which gnome-screensaver 2>/dev/null`"; then
           gnome-screensaver
           # Trailing & is not used after the command; consequently 
           # the screensaver can be used immediately.
        fi
    ;;
   esac

   #### Set this "true", if you want to have screen locked after automatic login:
   LockInAutoLogin="true"
   
   if test "$LockInAutoLogin" = "true"; then
   	
   	# Test if GDM is running; if it is running, it was used for login?
   	if ps -A --format comm | grep "^gdm$"  > /dev/null 2>&1; then
   		
   		# GDM configuration file is used to check, whether this is an automatic (or timed) login.
   		# You can use gdmsetup (as root) to make such settings.
   		# Note: Some older versions of GDM use the "gdm.conf" file for configuration.
   		gdmconf="/etc/gdm/gdm.conf-custom" 
   	 	if test -e "$gdmconf"; then
   		  user="`whoami`"  
   		  tmpconf="`tempfile`"
   	
   		  # remove blanks and comments; convert to lower-case
   		  sed '/^[[:blank:]]*$/d; /^[[:blank:]]*#/d; s/[[:blank:]][[:blank:]]*#.*//; s/[[:blank:]]//g' \
   		   "$gdmconf" | tr '[:upper:]' '[:lower:]' > "$tmpconf"  
   	
   		  # If automatic login or timed login is enabled for the current user in
   		  # the GDM configuration, lock screen.  
   		  if test \
   		   -n "`grep "^automaticloginenable=true$" "$tmpconf"`" \
   		   -a -n "`grep "^automaticlogin="$user"$" "$tmpconf"`" \
   		   -o \
   		   -n "`grep "^timedloginenable=true$" "$tmpconf"`" \
   		   -a -n "`grep "^timedlogin="$user"$" "$tmpconf"`"
   	     then 
   	   	   xflock4		   	   
   		  fi
   		  rm "$tmpconf"
   		else 
   		  # Could not find GDM configuration file; lock anyway
   		  xflock4
   		fi
   	fi
   fi

```

You can set the preferences below lines marked by ####.

---

