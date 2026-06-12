---
title: "Upgrade from 12.04LTS to 14.04LTS hanging before login"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by rctben on 2014-08-25
Hi Guys 
Been searching a lot and not finding answer . Seems it is common problem after login but not before . 
My problem similar to what I saw in this thread : [http://ubuntuforums.org/showthread.php?t=2228756](http://ubuntuforums.org/showthread.php?t=2228756)  
I updated from 12.04 ( been using it for a few years ) via update manager to 14.04 . It loaded and restarted  . It installed and I got 14.04 running . Very pleased with the setup and all my files / apps were there , all working fine .
I then restarted after it slowed down  when I set appearance in settings . This was not a hard restart but closed it via the restart option . 
The Ubuntu logo will show for a second and then I get a black screen with cursor top left corner ( not blinking ) . I do not get to the login page . 
Eventually I downloaded 14.04 on another computer and loaded it side by side to the older installation that can now not be opened  . Now that loads fine and I can get access to my documents via the second installation.

I tried Boot-repair ( using the LiveCD ) but no change . 
I tried Grub update ( found that somewhere ) but no success . 

I am not in the mood to load all my apps again on the second installation and would prefer to get into my original installation where all my apps and folders are . Is there an solution ?

---

### Post by rctben on 2014-08-25
More info 
Mecer laptop 500GB harddrive , 4GB ram , i5 . Only Ubuntu installed on the laptop ( no need for other OS )

Also tried the ro to rw fix in GRUB mentioned  [http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)
That also had no effect and it still hangs after Ubuntu logo .

When I Type Ctlr+Alt+F? it does nothing - I cannot get to terminal at all when it hangs

---

### Post by mozalmy on 2014-08-25
When you see the Ubuntu logo at startup, press Ctrl+Alt+F1. At the shell level type your login ID and password.

Then type following command and press enter:

```
sudo update-initramfs -u
```

There should be some activity on your screen.

When finished, type following command and press enter:

```
sudo update-grub && sudo shutdown -r now
```

See if that solves your problem.

---

### Post by rctben on 2014-08-25
Hi , thanks for the reply mozalmy

Unfortunatelty that did not help. 
When I pressed the  Ctrl+Alt+F1 is got the shell level but there appeared a few pages of script that read:
> [    28.958222] hub 1-1:1.0: connect-debounce failed, port 2 disabled 
This kept repeating numerous time with the numerical value increasing . It started by itself where you normally enter login name .

When it eventually stopped I could enter what you suggested . Unfortunately it did not make any difference and the startup procedure froze at the same place ( one difference : the screen is just black and no cursor in top part of screen any more ) :(

---

### Post by mozalmy on 2014-08-25
It seems like you're facing a hardware issue. Problem with your USB controller, I guess.

---

