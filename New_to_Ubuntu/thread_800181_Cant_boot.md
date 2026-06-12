---
title: "Cant boot"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by cronin4392 on 2008-05-19
Last night i put my computer on hibernate and this morning i went to turn it back on. i wasnt able to get it out of hibernate(i tried the power button, the mouse, and keyboard) so i just held the powerbutton for 5 seconds and then rebooted. when Ubuntu started back up it went through the loading screen and about 75% through it said it had to check my harddrives for errors or what ever which is normal. this is where it gets messed up. at this point my monitor would go to sleep, so i would have to turn it off and turn it back on and the DOS type screen was on my monitor. once it went through all the commands it had some error (i think it was a bash command it couldnt execute) and then nothing happened. all that i could do was type stuff in terminal like normal. what should i do? is there a command where i can shut down my computer like normal through terminal, i imagine there has to be, and is that what i should do or no?

---

### Post by Oak37 on 2008-05-19
```
sudo shutdown -r now
```

will restart your computer from the terminal. See if the same thing starts happening again.

---

### Post by cronin4392 on 2008-05-19
it says command 'sudo' is available in 'usr/bin/sudo'
the command could not be located because 'usr/bin' is not included in the PATH environment variable

---

### Post by wog on 2008-05-19
When it starts up again, try pressing the "shift" key every minute or so. The key press should interrupt the sleep process so you can get all the way through the system check, and yet not insert any characters to mess up said system check. 

I hope this helps.

---

