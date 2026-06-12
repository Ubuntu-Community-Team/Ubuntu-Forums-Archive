---
title: "problem run script inside a gnome-terminal"
date: 2012-06-22
forum: Programming Talk
---

### Post by jao_madn on 2012-06-22
hi,

I would like to ask about using gnome-terminal command, I had a script that will run my VBOX VM in headless and i want to display the output(STDOUT) on the gnome-terminal window. The purpose that i want to display the STDOUT of the script cause i will used it or create a desktop shortcut for one click start all and want a visual display of the script running all the VM's for confirmation. The script works fine when i used in terminal. It failed to run the Script if i will used the "gnome-terminal -e" command. "Its like it runs all the command inside the script and STDOUT it on gnome-terminal window that pop-up and as soon as the script exit all the command inside the script will abort or simple the VM state will abort or stop running"already try all the option on gnome-terminal but unsuccesfull. Here are some i tried:
 > gnome-termial -e "bash /home/<location_script>/startvm.bsh" 
gnome-termial -e "/home/<location_script>/startvm.bsh

i also used --working-directory, profile i guess all argument in gnome-terminal.

My goal would be run all the command inside the script and if the script exit and also the gnome-terminal exit all the command inside the script won't be affected.

Hope someone knows something..

Thanks in advance..

---

### Post by hakermania on 2012-06-23
That's weird. I do exactly the same thing as you, and it works just fine! (I do the 2nd thing, without referring to 'bash' at all)
Are you sure your script has executable rights?
What errors do you get?

---

### Post by jao_madn on 2012-06-23
> **hakermania said:**
> That's weird. I do exactly the same thing as you, and it works just fine! (I do the 2nd thing, without referring to 'bash' at all)
Are you sure your script has executable rights?
What errors do you get?

When above command run on a terminal it fails and exit. without throwing no errors. Yup put full executable rights to the script its 755

---

