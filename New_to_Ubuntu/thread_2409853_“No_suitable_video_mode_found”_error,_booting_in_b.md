---
title: "“No suitable video mode found” error, booting in blind mode"
date: 2019-01-07
forum: New to Ubuntu
---

### Post by kucapapelle on 2019-01-07
Since a few days I am getting the error written in the tittle when booting my PC, having the current Ubuntu 18.04.1 LTS bionic. 
  I have searched the web for a solution, tried to reinstall grub2 and  it did not work. I also tried out a solution, where the following lines:  
  ```
loadfont "unicode"
set gfxmode=auto
set gfxpayload=keep
insmod all_video
insmod gfxterm
terminal_output gfxterm

```  should be added to /boot/grub/grub.cfg
  however all of this commands are already (a little bit scattered around the file, and some of them in some if blocks. 
  Did someone have a similar problem and if yes, you maybe have some advices what else I could try out?

---

### Post by Impavidus on 2019-01-08
Changing stuff in /boot/grub/grub.cfg is a bit pointless as all changes are overwritten whenever the update-grub script runs, which is after every kernel update/removal.

I once had a very similar problem with an old computer after connecting a new monitor. The trick was to disable the graphical terminal by uncommenting one line in /etc/default/grub, so that it now reads```
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
```Whether that applies to your situation too, I don't know.

After changing /etc/default/grub, you can apply the changes with```
sudo update-grub
```which will update /boot/grub/grub.cfg

---

### Post by kucapapelle on 2019-01-09
I did not quite get which line of code did you comment out? I can try your trick, and let you know if it works.

---

### Post by oldrocker99 on 2019-01-09
I personally use this:
```
sudo nano /etc/default/grub
```

Then look for ```

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console
```
Then uncomment it.

---

### Post by Impavidus on 2019-01-09
I uncommented a line. So the line that said```
#GRUB_TERMINAL=console
```now says```
GRUB_TERMINAL=console
```

---

