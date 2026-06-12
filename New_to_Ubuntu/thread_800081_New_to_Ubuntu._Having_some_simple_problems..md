---
title: "New to Ubuntu. Having some simple problems."
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Bryantos on 2008-05-19
I'm having a few simple problems when it comes to file management. I have one more problem with keyboard shortcuts and Compiz Fusion.
[B]
[COLOR="DarkRed"]1.)[/COLOR][/B] The first problem I'm having is logging into the root user. I understand that using sudo through terminal will give me the same privileges as if was logged in as the root user, but with my minimal knowledge of terminal commands its harder for me to do it through terminal. I set a password for the root user, but when I try to log in through the log in screen, its tells me that administrator can not log in through that screen. **How can log into root if I already set a password for it?**

**[COLOR="DarkRed"]2.)[/COLOR]** Next, my cp command to copy files/directories is not working. I'm having to use this command because there is a folder that is owned by the root user that I can not modify. I installed mame to play some arcade games on my laptop, but I can not edit the roms folder because it is owned by root. I tried to change the folder that mame looks to for roms in the .ini file, but when I tried to save it, it says I do not own the file and can not modify it. However, when I try to copy the file that contains the roms over to the folder using this command: ```
cp -r /home/desktop/B's folder/Roms/1944 /usr/local/share/games/sdlmame/roms
```

The terminal just sits there and does nothing. It shows ">" and I can type whatever I want, but the commands are not executed and no action is taken by anything I do. When I just type cp into terminal, its says "cp: missing file operand. Try cp --help for more information". cp --help works, but it doesn't explain why the command is not doing anything.

**[COLOR="DarkRed"]3.)[/COLOR]** My last problem is with Compiz and keyboard shortcuts. I was able to set a shortcut for my Terminal via System->Preferences->Keyboard Shortcuts, but now my shortcut for my terminal doesn't work ever since I installed Compiz. I've changed the shortcut to several different key combinations with ALT + [key], and none of them worked. I then tried to change it to the tilde (~) key by itself and that doesn't work. I then tried CNTL + [key] and those don't work either. All of my other hotkeys seem to work perfectly fine. Any idea why?

Thanks for any help. <3

---

### Post by bluefrog on 2008-05-19
1) if logging as root is a problem for you then you have no business being logged graphically as root.

2) use sudo and put B's in double quote

3) ctrl T in keyboard-shortcuts works perfectly to open a terminal if compiz is installed and running

---

### Post by stchman on 2008-05-19
> **Bryantos said:**
> I'm having a few simple problems when it comes to file management. I have one more problem with keyboard shortcuts and Compiz Fusion.
[B]
[COLOR="DarkRed"]1.)[/COLOR][/B] The first problem I'm having is logging into the root user. I understand that using sudo through terminal will give me the same privileges as if was logged in as the root user, but with my minimal knowledge of terminal commands its harder for me to do it through terminal. I set a password for the root user, but when I try to log in through the log in screen, its tells me that administrator can not log in through that screen. **How can log into root if I already set a password for it?**

**[COLOR="DarkRed"]2.)[/COLOR]** Next, my cp command to copy files/directories is not working. I'm having to use this command because there is a folder that is owned by the root user that I can not modify. I installed mame to play some arcade games on my laptop, but I can not edit the roms folder because it is owned by root. I tried to change the folder that mame looks to for roms in the .ini file, but when I tried to save it, it says I do not own the file and can not modify it. However, when I try to copy the file that contains the roms over to the folder using this command: ```
cp -r /home/desktop/B's folder/Roms/1944 /usr/local/share/games/sdlmame/roms
```

The terminal just sits there and does nothing. It shows ">" and I can type whatever I want, but the commands are not executed and no action is taken by anything I do. When I just type cp into terminal, its says "cp: missing file operand. Try cp --help for more information". cp --help works, but it doesn't explain why the command is not doing anything.

**[COLOR="DarkRed"]3.)[/COLOR]** My last problem is with Compiz and keyboard shortcuts. I was able to set a shortcut for my Terminal via System->Preferences->Keyboard Shortcuts, but now my shortcut for my terminal doesn't work ever since I installed Compiz. I've changed the shortcut to several different key combinations with ALT + [key], and none of them worked. I then tried to change it to the tilde (~) key by itself and that doesn't work. I then tried CNTL + [key] and those don't work either. All of my other hotkeys seem to work perfectly fine. Any idea why?

Thanks for any help. <3

I don't believe you can log in as root in Ubuntu.  There is absolutely no reason to ever do so.

Problem with your copy statement is that you have spaces in the folder names.  I recommend using underscores _ instead of spaces.

I have never tried to make a keyboard shortcut for an app, I just put them on the desktopor the panel.

---

### Post by billgoldberg on 2008-05-19
> **Bryantos said:**
> I'm having a few simple problems when it comes to file management. I have one more problem with keyboard shortcuts and Compiz Fusion.
[B]
[COLOR="DarkRed"]1.)[/COLOR][/B] The first problem I'm having is logging into the root user. I understand that using sudo through terminal will give me the same privileges as if was logged in as the root user, but with my minimal knowledge of terminal commands its harder for me to do it through terminal. I set a password for the root user, but when I try to log in through the log in screen, its tells me that administrator can not log in through that screen. **How can log into root if I already set a password for it?**

**[COLOR="DarkRed"]2.)[/COLOR]** Next, my cp command to copy files/directories is not working. I'm having to use this command because there is a folder that is owned by the root user that I can not modify. I installed mame to play some arcade games on my laptop, but I can not edit the roms folder because it is owned by root. I tried to change the folder that mame looks to for roms in the .ini file, but when I tried to save it, it says I do not own the file and can not modify it. However, when I try to copy the file that contains the roms over to the folder using this command: ```
cp -r /home/desktop/B's folder/Roms/1944 /usr/local/share/games/sdlmame/roms
```

The terminal just sits there and does nothing. It shows ">" and I can type whatever I want, but the commands are not executed and no action is taken by anything I do. When I just type cp into terminal, its says "cp: missing file operand. Try cp --help for more information". cp --help works, but it doesn't explain why the command is not doing anything.

**[COLOR="DarkRed"]3.)[/COLOR]** My last problem is with Compiz and keyboard shortcuts. I was able to set a shortcut for my Terminal via System->Preferences->Keyboard Shortcuts, but now my shortcut for my terminal doesn't work ever since I installed Compiz. I've changed the shortcut to several different key combinations with ALT + [key], and none of them worked. I then tried to change it to the tilde (~) key by itself and that doesn't work. I then tried CNTL + [key] and those don't work either. All of my other hotkeys seem to work perfectly fine. Any idea why?

Thanks for any help. <3

1 & 2) in a terminal 

```
gksudo nautilus
```

3) try setting it to "f12"

---

### Post by Bryantos on 2008-05-19
I was able to copy the files over using ```
sudo cp -r /home/brynt/Desktop/"B's Folder"/Roms/1944 /usr/local/share/games/sdlmame/roms
```

Thank you for helping me with that.

So, what are the alternatives, besides using sudo through terminal, to edit files owned by root? For example, how would I edit the mame.ini file if I don't own it? It tells me I don't have permission to access it, so is that the same as not owning the file? Sorry for all the basic questions. :-?

The thing I don't understand about the hotkeys is that a friend of mine has Compiz and is able to use his hotkeys perfectly fine. However, he is running Ubuntu 7.10.

Thanks for the help, and I'll try to set the hotkey to F12.

[COLOR="DarkRed"]**Edit**[/COLOR]: Ahhh, so using: ```
gksudo nautilus
``` is similar to being logged in as the root user?

YAY.

I love all of you <3, but my hotkey for terminal still doesn't work.

---

### Post by y-lee on 2008-05-19
> **stchman said:**
> I don't believe you can log in as root in Ubuntu.  There is absolutely no reason to ever do so.



You *can* log in as root in ubuntu but you have to know how. **It is not advised at all.** If you don't know how then you certainly don't need to.

Use sudo instead :)

---

