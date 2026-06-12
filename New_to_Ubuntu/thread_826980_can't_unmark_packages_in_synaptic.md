---
title: "can't unmark packages in synaptic"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-12
is there a way to unmark broken packages in synaptic?  i have 2 that are now marked for removal and i want to be able to unmark them for the time being- every time i choose the option to unmark all packages synaptic just takes me back to the main screen but they are still marked for removal when i look at them again- even if i close synaptic (it asks me if i'm sure that i want to quit without taking action on the marked packages) and re-open synaptic they are still marked!  rebooting the computer doesn't do the trick either.

any help please?

thanks.

---

### Post by sdennie on 2008-06-12
Once you've unmarked them, did you hit the Apply button?

---

### Post by argail1980 on 2008-06-12
does ```
sudo apt-get purge <package name>
``` (without the < >, of course) work?

---

### Post by erginemr on 2008-06-12
Is there really no way to fix the broken packages?

---

### Post by Anicka on 2008-06-12
In synaptic, in one of the menu-tabs there is the option "fix broken packages". Have you tried that? Also run (in the terminal) the command : "dpkg -C" (n.b. capital C).

It should tell you if you have any broken packages and what to do about it. It will probably tell you to run: "sudo dpkg --configure -a" Do that!

In the terminal you should have a look at this: "dpkg --help" and "dpkg --force-help"

Good luck!

---

### Post by Matt26 on 2008-06-12
thanks for the suggestions- i have tried hitting the Apply button after unmarking all packages but it just attempts to go ahead and remove the packages again.

using the fix broken packages option under the Edit menu didn't seem to help either- when i click the option nothing happens on the screen but the status bar at the bottom of synaptic indicates that the packages have been fixed, but if i reload synaptic they are still there marked for removal.

i tried the command sudo dpkg -C and it told me that 3 packages (2 of which are the ones marked for removal in synaptic) are only half installed and advises that they can be removed and reinstalled, but if i try to remove them i am getting errors indicating that a directory/file cannot be removed (which doesn't actually exist which is probably why the error comes up).

---

### Post by Anicka on 2008-06-13
What does "sudo dpkg --configure -a" give? If it still gives you error messages, try this in the terminal: sudo dpkg --purge <packagename(s)>

If that doesn't kick out the packages (test with dpkg -C) then do: sudo dpkg --purge --force-all <packagename(s)>

After that you should be able to install them again using your favourite application.

---

### Post by Matt26 on 2008-06-16
well i finally fixed the problem with the packages- i discovered through various posts on this and other forums that the problem was with the packages themselves- they were in a state of being "half/partially installed"... i found this post (see link below) which shows you how to edit the file which apparently keeps track of the status of all the packages installed on ubuntu, so that the broken packages are no longer recognized by the system and can therefore be downloaded and installed again- the best part is, when i installed Firefox again, it kept all my settings (bookmarks, page history, add-ons, previously saved sessions) so it worked out well.

hope this can help others having this issue cause it sure drove me nuts for a solid week!

[https://answers.launchpad.net/ubuntu/+question/4838](https://answers.launchpad.net/ubuntu/+question/4838)
(check the grey section for details on solution)

---

### Post by cariboo on 2008-06-16
Matt26 you've got three threads on this same topic, the least you could do is mark them all solved.

Jim

---

### Post by DeadSuperHero on 2008-06-16
One way to fix it is to try opening up a terminal, and typing

```
sudo aptitude install gpaint
```

It doesn't have to be gpaint, just any simple app you can think of. Aptitude is great at fixing dependency errors. It will offer you a possible solution, and you can type Y or N. If it's N, it goes to another solution. Keep doing this until you find the one you want, and it should be fixed.

---

