---
title: "new to this. XFCE resolution problem."
date: 2012-06-26
forum: New to Ubuntu
---

### Post by blairwrobinson on 2012-06-26
i am new to this. my friend hooked me up. love it. i use studio version right now but my problem is my stupidity. i accidentally clicked a lower screen resolution and now it is so zoomed in i cannot get to menus to change anything. was wondering if there were any ways for me to either go back to a previous setting or keystroke menu actions

---

### Post by audiomick on 2012-06-26
It is hard to say what you did exactly, but maybe you activated the zoom function. The keyboard shorcuts are
ctrl + + to zoom in
ctrl + - to zoom out
ctrl + 0 to return to the normal view.

If you have actually changed the resolution of the screen, it is a different matter altogether. See if the above helps you first. If not, then a different approach is in order.

By the way, people would find you posts easier to read if you would make the effort to use capital letters at the start of your sentences.

edit: wait a minute, I just noticed the "xfce" tag on this thread. Maybe the above is a load of rubbish. It applies to Gnome / Unity. I don't know for sure that it works in XFCE. Sorry.

---

### Post by mike555 on 2012-06-26
can't you hold in the Alt key and move the window?

---

### Post by blairwrobinson on 2012-06-27
Thank You....The + - works in window screen but not where this gets stuck. I am stuck the xfce wallpaper....If i could just figure out how to go back to my first version it should solve everything. I just got the update so I won't lose much

---

### Post by black veils on 2012-06-27
1.  right-click the desktop

2.  **create launcher**

3.  **name**: settings, **command**: xfce4-settings-manager

4.  press the **create** button

on your desktop will be a launcher for your **settings manager**, maybe you can change the resolution again.

---

### Post by blairwrobinson on 2012-06-27
Nothing happens with a right click. I cant even find my cusor. A go back should help immensly

---

### Post by black veils on 2012-06-27
edit your thread/first post, to something like "resolution is too small" to at least give an idea for people to help.


also, you say the problem only happened because you changed the resolution, but then you later refer to what seems like an upgrade?

what were you doing right before the screen went zoomed-in?

---

### Post by blairwrobinson on 2012-06-27
I the update a couple days ago. My son didn't believe me about the size difference with resolution. So I clicked one. It got so huge I could get to anything. Stupid I know. I just need help to go back. I think that might be the easiest way

---

### Post by cortman on 2012-06-27
Are you using standard Ubuntu/Unity? First post says you're using Ubuntu Studio, then you mention XFCE somewhere down the line. Which one are you using? This will determine what instructions we give you.

---

### Post by blairwrobinson on 2012-06-27
It has an xfce logo on the wallpaper but my buddy installed ubuntustudio.When I log in it gives my a choice of xfce session or ubuntu studio. From disc my buddy installed Ubuntustudio. If I could just get back to my last version the changes should be gone. I don't think I can do that from my guest account I am using right now. When I was re-booting once I came to a screen that asked which version I wanted and each had a choice (with command promts) or something like that. I fooloshly chose my latest version (with command prompts) instead of the earlier version. As since I haven't been able to find that boot screen. It originally came up before the login screen

---

### Post by black veils on 2012-06-27
i am thinking he needs to go into tty1, and do commands with xrandr.

You can direct xrandr to set a different resolution like this: 

  xrandr --output LVDS --mode 1024x768
  xrandr --output VGA1 --mode 1024x768

---

### Post by cortman on 2012-06-27
> **black veils said:**
> i am thinking he needs to go into tty1, and do commands with xrandr.

You can direct xrandr to set a different resolution like this: 

  xrandr --output LVDS --mode 1024x768
  xrandr --output VGA1 --mode 1024x768

Xrandr is what we want; but it doesn't work from a tty. OP needs to open a terminal in X somehow.

@ OP; right click on the desktop and see if you can get a terminal open. Then run the xrandr commands given above, replacing 1024x768 with your desired resolution.

---

### Post by black veils on 2012-06-27
what about in recovery mode? or some sort of dpkg-reconfigure ?

---

### Post by cortman on 2012-06-27
> **black veils said:**
> what about in recovery mode? or some sort of dpkg-reconfigure ?

Xrandr sets the resolution for X server, so recovery mode is out. I cannot conceive how dpkg has anything to do with this problem.

---

### Post by philinux on 2012-06-27
I think it ctrl alt + or - for screen res in xfce.

---

### Post by blairwrobinson on 2012-06-27
The thing is, I cant get to my desktop. I am using guest account right now. When I log in on my account it doesn't even go to my desktop wallpaper. It stays on the silver login screen and zoomed in. The zooms work on normal windows but not on this screen. Can I do anything from my guest account?

---

### Post by blairwrobinson on 2012-06-27
If I could only get to that Pre-login screen during boot, that gave me the choice of current version or previous version I may be able to get out of this

---

### Post by Elfy on 2012-06-27
> **blairwrobinson said:**
> i am new to this. my friend hooked me up. love it. i use studio version right now but my problem is my stupidity. i accidentally clicked a lower screen resolution and now it is so zoomed in i cannot get to menus to change anything. was wondering if there were any ways for me to either go back to a previous setting or keystroke menu actions

> **blairwrobinson said:**
> Nothing happens with a right click. I cant even find my cusor. A go back should help immensly

> **blairwrobinson said:**
> The thing is, I cant get to my desktop. I am using guest account right now. When I log in on my account it doesn't even go to my desktop wallpaper. It stays on the silver login screen and zoomed in. The zooms work on normal windows but not on this screen. Can I do anything from my guest account?
So what did you do in between being able to get to the screen and 5 minutes ago?

If it does in fact login - but you just can't see things you could try 

Alt+F2 then enter 

```
xfce4-settings-manager
```

Then Display and reset

Remember that a right click anywhere on the app and then Alt will allow you to move the whole thing up and down to get at various options.

If you really can't do that - maybe boot the livecd/usb click on the drive that the install is on 

Navigate to 

.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

See what that says.

The other thing you could do would be remove the .config/xfce4 folder to remove your customisations.

---

### Post by black veils on 2012-06-27
i dont see how that would make a difference, the problem happened because you changed the resolution. but to get to the grub screen (list of operating systems, kernals and recovery mode), hold the **Shift** key

---

### Post by blairwrobinson on 2012-06-27
hold the shift key while i reboot? Can I do any of this from guest account.....you are speaking to a total retard by the way, lol Will the xandr commands in terminal work in guest accound for all accounts?

---

### Post by black veils on 2012-06-27
when the computer is starting, yes hold the shift key, but it will only get you the grub screen, it wont sort your resolution problem.

follow what Elfy said

---

### Post by blairwrobinson on 2012-06-27
I can get to log in but alt+F2  Enter does nothing. i can get to grub screen. I can choose other versions but it does the same thing to me. It sucks that something so stupid like res settings can cause so many probs. I log into my main account and it doesn't even go to my desktop background. It stays on the silver screen and i cant do jack! I dont have the disc with me it's with my buddy and if i go that route I'll have to wait for him which could be days. I'd love to just reinstall but i have work in there from my old windows that i cannot retrieve and I HAVE to. I tried one command in grub but it was error.....I am lost and panicing

---

### Post by Elfy on 2012-06-27
Reboot, at grub choose the second option.

When you get to the menu - do the clean space option, just in case it is that.

When it asks - press enter, you will be then be back at the menu. Now choose root terminal.

BE careful from now as you could do damage.

You can remove the xfce4 configs from here.

Run this command 

```
ls /home
```

That will show you the name of your user(s)

run 

```
rm -r /home/yourusername/.config/xfce4
```

once that has done

exit

You will be back at the recovery menu - choose resume

---

### Post by blairwrobinson on 2012-06-27
I did all that.....The 1s /home said no command. i tried   1s /home, 1s/home, is/home....nothing. Not sure if you were entering spaces in some of that code. Good god is there anyway this can just go back to a couple days ago before all this happened? But i have to do it from guest or grub. Windows does suck compared to the potential this has when i get past the learning curve but at least if i did something like i did it would have given 10secs to confirm before it returned to original settings. I just need to go back 48hrs to settings. Can't that be done??? And if i have to reinstall, is there a way to recover my files from guest or grub and back them up before reinstall???....I just want to be able to recover system to earlier date!!!

---

### Post by Elfy on 2012-06-27
It's a lower case L not a 1.

You can recover your files - but you need a live medium.

Rather than wait for the live do you have a usb or something you can burn an iso to?

---

### Post by blairwrobinson on 2012-06-27
No, no burner. I did the lower case ls(space)/home.....brought me to what you said. Went to root, entered ....rm(space)-r(space)/home/myusername/(space).config/xfce4. It said rm cannot remove, no file.......tried other variations on spaces, then "no command" error. I am a retard i guess. Not very good at this

---

### Post by Elfy on 2012-06-27
None of this please "I am a retard i guess" ... no-one is born knowing everything :)

If in doubt you can use tab to autocomplete paths 

The only spaces should be between 

rm    -r    /home

and one is enough :)

so - and you need to put your folder name where it says username, which you should get from the  ls /home command.

rm (space) -r (space) /home/yourusername/.config/xfce4

if you do .con try tab and see what it does :)

---

### Post by blairwrobinson on 2012-06-27
tried with all you said and it says "rm cannot remove, no such file or directory"......I even went back and did the ls /home and this time it didn't list my user name. GRRRRRRRRRR. I'm wondering tho, if this does succeed and it is removed, is it gonna remove my user account along with all my files i have?

---

### Post by black veils on 2012-06-27
all it will do is remove some settings, not your user account or personal files.

---

### Post by blairwrobinson on 2012-06-27
Yea but it was still saying "cannot remove, no such file or directory". I will try again from step 1. But like i said, with   ls /home   it is now not even listing my user name. I will try again. If it doesn't work, is there anyway to reset the whole OS to default settings?

---

### Post by Elfy on 2012-06-27
> **black veils said:**
> all it will do is remove some settings, not your user account or personal files.
Yep.

@blairwrobinson - if one of your various tries to get it to remove happened to be 

rm -r /home/yourusername/ (space).config/xfce4

you will I am pretty sure have removed your home.

If ls /home is showing nothing then that is what you have done

---

### Post by blairwrobinson on 2012-06-27
that is what I have done. I log into my user name now and it just loops back to login screen. I guess I've lost all my files now as well, haven't I???

---

### Post by Elfy on 2012-06-27
It would appear that is what you've done.

I assume you've not got backups either.

---

### Post by blairwrobinson on 2012-06-27
I dont think my buddy back up anything on ghost. i dont understand why they would be completely gone from my machine. If the FBI wanted them they are tucked away for them to access, lol. Windows sucks yes, but why, if in windows, you remove a file and find you need to do a systems restore, the file is there again and you have to remove it again. Are you sure those files are nowhere in my machine??

---

### Post by Elfy on 2012-06-27
You can try testdisk - I've never used it though - [https://help.ubuntu.com/community/DataRecovery/](https://help.ubuntu.com/community/DataRecovery/)

You might be better of starting a new thread and reference this one in it.

Good luck with that.

Please remember that tab complete works, if in doubt check again - also linux is case sensitive - text and Text are 2 different things.

---

### Post by blairwrobinson on 2012-06-27
Well, thanks for all your help....I will move on with my totally screwed up life now....Peace

---

