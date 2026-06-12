---
title: "Changing system sounds"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by keiichidono on 2008-07-03
I am trying to customize my system to my liking and i'm almost done, i just need to change system sounds. What i want to know is how i can get control over /usr/share/sounds (or any directory) so that i can delete everything there and copy over my custom system sounds. Can anyone help me please?

---

### Post by lukjad on 2008-07-03
> **CalvinB said:**
> I am trying to customize my system to my liking and i'm almost done, i just need to change system sounds. What i want to know is how i can get control over /usr/share/sounds (or any directory) so that i can delete everything there and copy over my custom system sounds. Can anyone help me please?

System->Preferences->Sound and click on the Sounds tab. Then select the sound you want by clicking the drop down arrow at the appropriate system sound and clicking Select Sound File.

---

### Post by keiichidono on 2008-07-03
> **lukjad007 said:**
> System->Preferences->Sound and click on the Sounds tab. Then select the sound you want by clicking the drop down arrow at the appropriate system sound and clicking Select Sound File.
Thanks, but that doesn't allow me to take control over the /usr/share/sounds directory so i can replace the sounds with my custom ones, that's where i want them to stay. Do you know how to do this? Thanks for the help.

---

### Post by strongboww on 2008-07-03
> **CalvinB said:**
> Thanks, but that doesn't allow me to take control over the /usr/share/sounds directory so i can replace the sounds with my custom ones, that's where i want them to stay. Do you know how to do this? Thanks for the help.

normally should function via shell copy command and sudo

---

### Post by keiichidono on 2008-07-03
I'm not very experienced with the shell though, i am looking for a way to gain root access using the GUI/CLI so i can use the GUI to delete the files there and copy the files i want over.

---

### Post by Xzallion on 2008-07-03
You just need to run the gui app as root to copy the files to there?  Here ya go.

```
gksu nautilus
```

---

### Post by Xzallion on 2008-07-03
Whoops, sorry double post.

---

### Post by keiichidono on 2008-07-03
Thanks i ran it and did what i had to do and it worked. one thing i'm concerned about it that it gave me some errors here and there in the terminal but i'm guessing it's nothing to worry about.

---

### Post by lukjad on 2008-07-03
> **CalvinB said:**
> Thanks i ran it and did what i had to do and it worked. one thing i'm concerned about it that it gave me some errors here and there in the terminal but i'm guessing it's nothing to worry about.

That happens. If it says something like unable to get root access or something like that and Nautilus still opens you needn't worry usually.

---

