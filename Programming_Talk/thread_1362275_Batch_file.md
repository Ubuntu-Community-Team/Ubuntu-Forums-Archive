---
title: "Batch file"
date: 2009-12-22
forum: Programming Talk
---

### Post by Marvin666 on 2009-12-22
Does anybody think the following batch file will work? It is going to be ran by win 98.
```

@echo off
:REM1 Coded by Marvin666.
:REM2  This batch file will save your Nethack game, and update your saved game.
set /p %1=Press y to save/update Nethack files. Press any other key to cancel.
if [exist] C:\Nethack\home-Marvin.NetHack-saved-game goto :c [else goto r:]
:c if [not] exist C:\home-Marvin.NetHack-saved-game goto :w
:r if [not] %1=y goto :o [else goto :y]
:y if [not] exist C:\Nethack\home-Marvin.NetHack-saved-game goto :s [else goto :u]
:s (copy C:\Nethack\home-Marvin.NetHack-saved-game
   paste C:\
   echo "You have saved your Nethack file."
   goto :e)
:u (copy C:\home-Marvin.NetHack-saved-game
   paste C:\Nethack
   echo "You have updated your Nethack file."
   goto e:)
:o (echo "You updated your Nethack file."
   goto :e)
:w echo "Error: No Nethack files found."
:e (pause
   exit)

```It's been quite a while since I've made anything this complex.

---

### Post by Marvin666 on 2009-12-23
I backed up a few things and finally tested it. No matter how much I mess with the file, command.com gives the exact same result:
```

Syntax error
Bad command or file name
"You have saved your Nethack file."
Label not found

```
Anybody know what's going on here?
It should look like:
```

Press y to save/update Nethack files. Press any other key to cancel.
Error: No Nethack files found.
Press any key to continue.

```

---

### Post by Marvin666 on 2009-12-23
Okay, I've redone and expanded the code, and no longer get any errors, but it still won't function correctly.
```

@echo off
:REM1 Coded by Marvin666.
:REM2 This batch file will save/restore you Nethack game, and launch Nethack for you.
if not exist home-Marvin.NetHack-saved game C:\Nethack\ goto :c [else goto :r]
:c if not exist home-Marvin.NetHack-saved-game C:\  goto :w
:r (choice /c:yn "Press y to save/restore Nethack files. Press n to cancel." |
   if not ERRORLEVEL=1 goto :o [else goto :y] )
:y if not exist home-Marvin.NetHack-saved game C:\Nethack\ goto :s [else goto :u]
:s (copy C:\Nethack\home-Marvin.NetHack-saved game C:\home-Marvin.NetHack-saved-game
   echo "You have saved your Nethack file."
   goto :l )
:u (copy C:\home-Marvin.NetHack-saved-game C:\Nethack\home-Marvin.NetHack-saved-game
   echo "You have updated your Nethack file."
   goto :l )
:o (echo "You have canceled Nethack file save/update."
   goto :l )
:l (choice /c:yn "Press y to launch Nethack. Press n to cancel." |
   if not ERRORLEVEL=1 goto :e [else goto :n] )
:n if not exist NetHackW.exe C:\Nethack\ goto :t [else goto :g]
:g (choice /c:gt "Press g to launch Nethack in tiles mode. Press t to launch Nethack in terminal mode." |
   if not ERRORLEVEL=1 goto t [else goto :n] )
:w (start C:\Nethack\NetHackW.exe
   echo "Nethack in tiles mode has been launched."
   goto :p )
:t if not exist NetHack.exe C:\Nethack\ goto :a [else goto :x]
:x (start C:\Nethack\NetHack.exe
   echo "Nethack in terminal mode has been launched."
   goto :p )
:e (echo "You have chosen not to launch Nethack."
   goto :p )
:a (echo "Error: No Nethack executables found."
   goto :p )
:p (pause
   exit )

```

---

### Post by Marvin666 on 2009-12-25
bump

---

### Post by Arndt on 2009-12-25
> **Marvin666 said:**
> bump

But Win98 is not Ubuntu.

---

### Post by Marvin666 on 2009-12-25
It's on the second machine in my signature, so ubuntu cannot be installed. Ubuntu also can't run batch files.

---

### Post by lisati on 2009-12-25
> **Marvin666 said:**
> It's on the second machine in my signature, so **ubuntu cannot be installed**. Ubuntu also can't run batch files.

I have a copy of Ubuntu 6.06 server edition on my old machine that came with Win98. It still needs a bit of tinkering but can be used.

Try taking the colons ":" off the REM statements........

---

