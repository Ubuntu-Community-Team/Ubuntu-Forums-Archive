---
title: "Black screen w/ cursor after boot"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by lite-blu-shadow on 2013-12-01
After doing some schoolwork I left my computer with ubuntu 13.10 running over night. Next morning; I come back to see it glitching a bit (Software center app dissapeared, terminal is black/white instead of the softer purple/white) so, like any normal person, I decide to restart it.
After restarting it, everything's working fine. I get to the login screen, log in, etc. But after the login, instead of my desktop w/ the folder/apps I just get my wallpaper with nothing on it. The menu isn't there, and neither are the files.
So I decide to browse for a solution on the mighty internet. After opening up tty1 and reinstalling nvidia, unity, bunch of other stuff I find that after I log in instead of my wallpaper it's now a black screen.
I persist and keep install/deleting/reinstalling anything that the forums tell me to and it does. Not. Work.
Eventually, (I know my way around Ubuntu) I just type in 'sudo apt-get install nvidia-current' and execute it 'till the end.
I restart, only to find that after the bootup, instead of the login screen I get that same black screen with a cursor. Even if I press Ctrl+Alt+F1, my monitor stops receiving input. So after about 2 hours, it finally broke me and so I turn to the forums.
Any hints/advice/solutions? System specs will be dispensed at request. Any help is greatly appreciated

---

### Post by 3246251196 on 2013-12-01
Give NOMODESET a go:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by lite-blu-shadow on 2013-12-01
Ok, so I tried doing what you asked with nomodeset and it worked, so thanks a lot!
But sadly, it's back to the problem where after I login, all I get is a black screen with my cursor but now the cursor is a black cross.
Any suggestions on what I should do?

---

