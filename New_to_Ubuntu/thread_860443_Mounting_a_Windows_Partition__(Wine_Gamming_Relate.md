---
title: "Mounting a Windows Partition?  (Wine Gamming Related)"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by IamJohnHayes on 2008-07-15
Basically, I started playing this free MMO racing game called Project Torque.  Tried it on the windows bax in the house and it was cool until there was some bs vista graphics driver nonsense.  So I installed in on my linux box running with wine and it took a few little tweaks to get it to have the right resolution.  But now when i start the game it loads correct i connect good but all the text shows up as a squares or solid rectangular blocks.  I thought it may be font related so i posted on their forums if anyone ran linux and or knew what font the game used and i got a few anti linux we dont support linux responses and then this 

"What does your wine config look like? I haven't been able to get PT running under wine? I haven't tried the latest version of PT yet.

Try doing this:
mount windows partition on say /media/wincrap
make a symbolic link from your dotwine directory's windows folder to the /media/wincrap's windows font folder using:
ln -s $HOME/.wine/drive_c/windows/font /media/wincrap/windows/font
I think that's the right paths..

see if that helps you out." 

apparently i have one of the most functional running games on linux (dont know how, gameplay is ok a little laggy but not too bad) but im not entirely sure what this person is asking me to do or how to do,  I am still very much a noob.

---

### Post by Chris S. on 2008-07-15
Perhaps he means there are fonts installed on your Windows box that are used by the game, but these fonts do not exist in the Wine install.  What he wants you to do, essentially, is redirect your fonts folder on the Linux machine to point to the fonts folder on the Windows machine.  It doesn't matter if that's even possible, because it's entirely unnecessary.

Just go to C:\WINDOWS\Fonts on the Windows box and copy all the files there to a flash drive or something.  Then take all those font files to your Linux machine and copy them to the /home/<your user name>/.wine/drive_c/windows/font folder.  The directory names may not be exactly the same, but they'll be similar.

Hopefully that's all you'll need, and that's all he's saying.

---

### Post by LowSky on 2008-07-15
I know with Steam you need to install the tahoma font to you wine's fake windows\fonts directory. tahoma is a very popular windows font it may be that one.

---

### Post by IamJohnHayes on 2008-07-15
ok I copied my entire windows box font collection into my .wine/fonts and still same problem.  also tried changing the in game resolution and the wine resolution in wine config and still no solution.  tried to screenshot the game but i just got a light blue screen so i used the digi to take some pics.  the text is exactly as the pics show.

---

### Post by Chris S. on 2008-07-16
Maybe it's not a Windows font issue after all.  You did put the fonts in .wine/drive_c/windows/fonts/, right?

So try this, now.  Run the game from the terminal with ".wine <path-to-game>.exe".  Go through the screens and menus until you get to something where the fonts aren't showing up.  Then exit the game and post the output from the terminal.  Hopefully the wine messages are easy enough to decipher and can point ot a problem.

---

### Post by IamJohnHayes on 2008-07-17
right after i took these pics the text actually would disappear and then reappear but i will attemp to run for the terminal when i have time tomorrow

---

