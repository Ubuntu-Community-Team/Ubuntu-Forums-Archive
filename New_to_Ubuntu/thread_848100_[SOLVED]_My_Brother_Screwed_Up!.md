---
title: "[SOLVED] My Brother Screwed Up!"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by marenkar on 2008-07-03
Hello, my brother screwed up the root user by changing the theme and doing stuff ( I'm not sure if he told me everything) and now the font is really huge, as in when u right click something, the words barely fit into the screen. And the Worspaces are on the top, covering 1/4 of the screen, while the trash bin is at the bottom doing the same. The icons looks normal though, but when i click it, i cant see any content, just the go and url space.

Thanks to a computer technician who knows ubuntu, he taught me how to make a new account through terminal, so i didnt really need to use the screwed up root user, thats why I'm able to post this.

But I need the root user because there are some files there that I want. Is there a way I can reset the desktop settings through terminal or copy the files to this account?

P.S I'm using 6.06 LTS . Thanks

---

### Post by abn91c on 2008-07-03
try log in using a recover kernel- hit ESC when rebooting at the GRUB prompt, then choose one from the list

---

### Post by hyper_ch on 2008-07-03
why does your brother has access to the root user?

---

### Post by mcduck on 2008-07-03
Sounds like the biggest changes on the amdin account's settings are bigger font size, and possibly smaller resolution (unless he changed the dpi-settings in the font options).

Anyway, the simplest way to reset the account to default settings is to delete every hidden file from that account's home directory. All personal settings are stored in these hidden files, so if you remove them the next time you log in the account will be just like after installing Ubuntu. (New setting diles will be automaticly generated when required).

You can keep all the personal files, and even the setting files for specific programs, like Firefox, if you want.

..and yeah, you'd probably better make your brother own account, perhaps with no admin rights? :D

---

### Post by nothingspecial on 2008-07-03
> **mcduck said:**
> 
Anyway, the simplest way to reset the account to default settings is to delete every hidden file from that account's home directory. All personal settings are stored in these hidden files, so if you remove them the next time you log in the account will be just like after installing Ubuntu. (New setting diles will be automaticly generated when required).
 :D

Is this right? So next time I screw up my system, as I often do (serial tweaker), all I have to do is delete the hidden files in my home directory?

---

### Post by Dr Small on 2008-07-03
> **nothingspecial said:**
> Is this right? So next time I screw up my system, as I often do (serial tweaker), all I have to do is delete the hidden files in my home directory?
That really depends on if you messed up settings for a certain app, theme settings, or if you made a system wide change.

---

### Post by mcduck on 2008-07-03
> **nothingspecial said:**
> Is this right? So next time I screw up my system, as I often do (serial tweaker), all I have to do is delete the hidden files in my home directory?

As long as you didn't mess the system, but only your own user account, cleaning the home directory is all you need to do. :)

---

### Post by marenkar on 2008-07-03
Thanks, I'll try 'em later, but now my sound doesnt work on this new account, why?

---

### Post by unutbu on 2008-07-03
Deleting all the dot config directories will also delete your browser's bookmarks, and all GNOME configuration settings. It can be a little bit tramatic in its own right.

If you want to move more cautiously, just rename the directories. Change .config to .config-orig for example.

If you use firefox and FF is not the source of the problem, (and it sounds like it isn't), just don't touch the .mozilla directory.

marenkar, regarding sound: Go to System>Users and Groups. Click on the new user name. Click the Properties Button, and then the User Privileges tab. Enable everything that you want, but especially "Use audio devices".

---

### Post by Dr Small on 2008-07-03
> **marenkar said:**
> Thanks, I'll try 'em later, but now my sound doesnt work on this new account, why?
Is your new account in the audio group?

---

### Post by nothingspecial on 2008-07-03
> **unutbu said:**
> Deleting all the dot config directories will also delete your browser's bookmarks, and all GNOME configuration settings. It can be a little bit tramatic in its own right".

`spose you`re right, but it`s got to be worth a go before I do another reinstall and have to start from the beginning again.

---

### Post by marenkar on 2008-07-04
> **unutbu said:**
> Deleting all the dot config directories will also delete your browser's bookmarks, and all GNOME configuration settings. It can be a little bit tramatic in its own right.

If you want to move more cautiously, just rename the directories. Change .config to .config-orig for example.

If you use firefox and FF is not the source of the problem, (and it sounds like it isn't), just don't touch the .mozilla directory.

marenkar, regarding sound: Go to System>Users and Groups. Click on the new user name. Click the Properties Button, and then the User Privileges tab. Enable everything that you want, but especially "Use audio devices".

I wont be able to do that since I can't see the menu from the root user.

I also cant see the menu bar btw, so I cant delete the hidden files of the home folder.

I just need to reset the desktop settings somehow through terminal, not through any other way since I wouldnt be able to use the desktop, or any thing in there for that matter.

---

### Post by marenkar on 2008-07-04
> **mcduck said:**
> Sounds like the biggest changes on the amdin account's settings are bigger font size, and possibly smaller resolution (unless he changed the dpi-settings in the font options).

Anyway, the simplest way to reset the account to default settings is to delete every hidden file from that account's home directory. All personal settings are stored in these hidden files, so if you remove them the next time you log in the account will be just like after installing Ubuntu. (New setting diles will be automaticly generated when required).

You can keep all the personal files, and even the setting files for specific programs, like Firefox, if you want.

..and yeah, you'd probably better make your brother own account, perhaps with no admin rights? :D


Is there a way I can delete the hidden files through terminal?

Sorry for the repost. I didnt see the old one there.

---

### Post by unutbu on 2008-07-04
Try this:
```

Log out                              # So GNOME isn't messing with your dot configuration directories
Press Ctrl-Alt-F2                    # Get to a text terminal
Log in
mv ~/.config ~/.config-orig          
mv ~/.gconf ~/.gconf-orig            
mv ~/.gnome ~/.gnome-orig            
mv ~/.gnome2 ~/.gnome2-orig          
exit
Press Ctrl-Alt-F7                    # Get back to gdm
Login as the old user 
```
You should now have an account with no GNOME configurations. GNOME will automatically create new configuration directories as needed. You'll have to reset any GNOME configurations that you want.

If it doesn't work, to regain your old settings:
```

Log out                              
Press Ctrl-Alt-F2                    
Log in
mv ~/.config-orig ~/.config          
mv ~/.gconf-orig ~/.gconf            
mv ~/.gnome-orig ~/.gnome            
mv ~/.gnome2-orig ~/.gnome2          
exit
Press Ctrl-Alt-F7                    
Login as the old user 

```

---

### Post by marenkar on 2008-07-10
Thanks! It worked!

P.S I found an easier way

rm-rf .gnome .gnome2 if ever anyone else gets the prob

---

### Post by admelfo on 2008-10-31
THANK you! Been pissing around with this issue for a week!

....now, if I can only figure out how to prvent myself from causing it again....

---

