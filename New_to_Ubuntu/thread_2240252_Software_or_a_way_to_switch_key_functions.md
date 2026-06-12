---
title: "Software or a way to switch key functions?"
date: 2014-08-18
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-08-18
I have a broken "J" key on my PC. Is there someway, perhaps downloadable software, that allows using the Windows key (which I do not use) to function as a "J" key until I get a new keyboard? (By the I am still able to type "J" by hitting the button under the key.)

Thanks,

R.

---

### Post by Sanctimonious_Ape on 2014-08-19
Solutions I found mentioned installing "xkeycaps", but I tried this program and couldn't get it to use the right keymap. I selected the default 105-key US layout that my settings tell me I'm using and it remapped several of my keys - most notably my cursor keys (UP became a screenshot shortcut). I don't recommend it unless you're willing to keep working with it to find the right mapping for your hardware, but your mileage may vary.

Next solution I found was programmer oriented, but not that difficult to follow. First they had you run 'xev' at a terminal window. That program appears to describe in excruciating detail every input event (mouse movement, keypress, etc.) for programmers that need the low-level detail it provides. Start it, don't move your mouse, and press they key you want to use as your "j" key. Somewhere in the middle of each of the couple of paragraphs of text that appear in the terminal window is the word "keycode" followed by a number - jot down that number. In the example below I've highlighted it (I used the "menu" key to the right of my space bar):
```

KeyRelease event, serial 37, synthetic NO, window 0x3600001,
    root 0x26c, subw 0x0, time 48221965, (165,-11), root:(588,314),
    state 0x0, **keycode 135** (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

```

Close the small window that appeared when you started 'xev' (ignore the mass of text that appears in the terminal window as you move the mouse). Back in the terminal window enter the following, replacing the '135' I'm using with the code you just got for your preferred key:
```
xmodmap -e 'keycode 135=j'
```

Should take effect immediately, but will be lost upon logout/reboot.

I tried to make it stick by the usual Settings -> Session and Startup method, but it didn't work for me (I have a guess as to why, but don't know how to correct it).  I'll describe it, maybe you'll have better luck.  Only other option is to get the command into some startup script, but I don't know if you're comfortable with editing important text files.

Anyway if you want to try what is *supposed* to work, then here goes: go to Settings -> Session and Startup -> Application Autostart (tab), and then click "Add" at the bottom. Put whatever you like in the first two boxes of the dialog that appears (note the name you give it, you'll need to find that in the list to disable it later), but put the command above in the last one (see attached screenshot) and click "OK".  When you get your new keyboard, return to this Application Autostart list and uncheck the item with then name you assigned (you can leave it there for future use should you need it again).

[ATTACH=CONFIG]255625[/ATTACH]

Hopefully this works for you better than it did me.  Otherwise I'm out of ideas to make it stick unless you're willing to carefully edit a startup script.

---

### Post by Impavidus on 2014-08-19
+1 to using xmodmap. I use it to make my Windows key my compose key. I've put the xmodmap command in a script that also does some other things on login and call the script at login using the session and startup settings. It works.

---

### Post by Sanctimonious_Ape on 2014-08-19
Hmmm... a script works, eh?  Wonder if that means the parameters aren't being passed - putting it into a script would certainly bypass that issue.  Ahh, well - I need to go to bed, so I'll leave it as an exercise for the reader for now.

---

### Post by Impavidus on 2014-08-19
To be exact, I didn't use **xmodmap -e blah** but **xmodmap ~/.xmodmap**, with ~/.xmodmap a separate file with the definition(s).

---

### Post by mastablasta on 2014-08-19
in KDE there is a GUI for this key re-maping. is there nothing like that in Ubuntu? 

btw if button still works you can replace only the key...

---

### Post by AbleTassie on 2014-08-19
Thanks Ape and Impavidus, 

I am using Lubuntu, and I don't see an option of: "Settings -> Session and Startup -> Application Autostart", etc. Are these options available in Lubuntu? I don't know anything about scripts.

Mastablasta, Good thought, but there are two metal tabs at the top of the key dock that anchor the J key, one of these tabs is broken. So replacing just the key is not an option.

Thanks,

R.

---

### Post by Sanctimonious_Ape on 2014-08-19
Sorry, somewhat new to Linux myself and I just dumped Lubuntu after a recent software update killed my panel, and I didn't have enough time with it to remember if it had such a feature.  Xubuntu seems just about as light as Lubuntu, but has more features.  The trade-off is that it's not as nicely configured for Windoze escapees as Lubuntu is.  Will continue using XFCE/Xubuntu for now, but [LXQt]("http://lxqt.org/") -- the next generation of Lubuntu's environment -- is looking very tempting and I can't wait for it to be finished and ready for prime time.

I'll try to locate a better solution for you (so subscribe to this thread).  In the meantime, you can simply save the "xmodmap" command somewhere and paste it in every time you log in.  Alternatively, you can try installing a "virtual keyboard" (search using that phrase in Lubuntu Software Center), or Lubuntu may already have one installed (Xubuntu has "Onboard" installed).  It's a software keyboard much like the ones on common touch screen smartphones.

Hopefully, I (or someone else) will get back to you soon with a better solution -- or you'll get that replacement in soon).

---

### Post by Sanctimonious_Ape on 2014-08-19
Found a solution that seems to work.  The following instructions assume you got the keycode by running the xev program [as I described above](http://ubuntuforums.org/showthread.php?t=2240252&p=13102262#post13102262).

1. Open a file manager window (PCmanFM in Lubuntu) in your home directory (usually where it starts by default, for example mine would be something like "/home/ape").  

2. Press CTRL-H on your keyboard.  This toggles showing you a BUNCH of files and folders that are normally hidden from you because they're things you really shouldn't play with unless you know what you're doing.  They contain virtually everything to do with your specific logon/profile.  You may notice they ALL start with a period/dot for their name -- that's what indicates to Linux that they should normally be hidden.

3. Right-click on a blank area and choose "Create New..." and the submenu item "Empty File" -- you'll be prompted for a name, so name it ".Xmodmap" (no quotes and notice the starting period/dot as well as the uppercase first letter followed by all lowercase).

4. Right-click on the file you just created (.Xmodmap) and choose "Leafpad", "Mousepad", or whatever other text editor program it offers.

5. Enter or paste the following, changing the 135 to whatever code you got earlier: ```
keycode 135 = j
```

6. Go to the File menu in the text editor and tell it to close or quit, have it save the document when prompted.  In the file manager, press CTRL-H again to make it hide the normally hidden files again.  Log out and back in and your key should be mapped.

When you get your replacement keyboard, you'll probably want to disable this.  Just start up the file manager again, make it show the hidden files, delete .Xmodmap, hide the files again, and finally log out and back in again.

---

### Post by Impavidus on 2014-08-21
Great, so that's what I was doing wrong: I hadn't used a capital X. Now it works without calling xmodmap explicitly. You learn something new every not so long period of time.

To the OP: When you have your new keyboard you can delete you .Xmodmap, but once you know the trick you can also put something else useful in it. I have```
keycode 133 = Multi_key
```which turns my Windows key into a [compose key](http://en.wikipedia.org/wiki/Compose_key).

---

### Post by Sanctimonious_Ape on 2014-08-22
I prefer to leave the Super/Windows key alone as a number of keyboard shortcuts are already mapped to it (and I've mapped some of my own since I'm a longtime Windows user).  I mapped my near useless CapsLock key to compose, although I've considered swapping it and CTRL to make it more of a hackers keyboard (too many years of muscle memory and potential confusion on other keyboards holds me back, though).

---

### Post by AbleTassie on 2014-08-22
Thanks Ape and Impavidus, 

 I actually physically repaired the metal slot in the metal key dock for the J key and it works. I used a piece of bent paper clip and pryed up some of the sheet metal in the key dock. Then I slid my bent paper clip piece in place under the sheet metal and epoxied it in place. But the upper pegs in the white plastic hinged assembly that sits under the key do not slide freely in the repaired slot as they do in a normal slot. So the key has a somewhat different feel than a normal key, but it still seems to work well. This link ( [www.machinaelectronics.com/blog/hinge-type-k10/]("http://www.machinaelectronics.com/blog/hinge-type-k10/") ) has good information on keys generally and my key type K10 in particular.  I may still, however, very well use the software patch that Ape discovered and Impavidus elaborated on. Thanks again. I will mark this post as Solved.  

R.

---

