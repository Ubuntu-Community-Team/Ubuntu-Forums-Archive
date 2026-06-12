---
title: "question about developing a program"
date: 2011-02-02
forum: Programming Talk
---

### Post by ekoMs on 2011-02-02
If I would want to make a program that would that would allow me to switch into TwinView for my dual-display NVidia Monitors when I press a button. How would I go about writing this program?

Should I write it in C? I am most familiar with C.

Its just so annoying everytime I want to go into dual display to go through the System->Administration->etc....

any help/suggestions/ideas would be greatly appreciated.

Thanks

---

### Post by Ferrat on 2011-02-02
if the nvidia program takes arguments for actions like that you should look in to bash, if it doesn't then it will be next to impossible I think as the driver is closed source (it is right? not 100% sure)

---

### Post by Yougo on 2011-02-02
writing a program that talks to Nvidia-settings is quite a challenge methinks. and that's assuming Nvidia-settings is listening in the first place :-\ writing something to succesfully take over from nvidis-settings sounds really ambitious (ofcourse should you succeed you're a hero! :) )

i imagine a script to change some config files (swap them out, or point to another one) and then reload the screens, but i wouldn't know where to start. (also that sounds like restarting your GFX card, tearing down your X session :-S )

here's a manpage for nvidia-settings:
[http://linux.die.net/man/1/nvidia-settings](http://linux.die.net/man/1/nvidia-settings)

maybe there's some arguments you could use to do things without bringing up the GUI?

---

### Post by ekoMs on 2011-02-02
Nice suggestions... I looked into the manual and this sounded promising:

"**nvidia-settings** has a rich commandline interface: all attributes that can be manipulated with the GUI can also be queried and set from the command line."

So I'll look into that. Maybe I can just make a script that will execute a few commands on the command line?

---

### Post by Rany Albeg on 2011-02-03
> "**nvidia-settings** has a rich commandline interface: all attributes that can be manipulated with the GUI can also be queried and set from the command line."

If it is CLI manipulated the best way is to write a Bash script for this task.
Good luck, and come back if you need help with that.

---

