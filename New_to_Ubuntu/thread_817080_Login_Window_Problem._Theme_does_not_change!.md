---
title: "Login Window Problem. Theme does not change!"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by mochiko on 2008-06-03
hello, i'm super-new to ubuntu, and i have the hardy heron edition thingy.

i used to use gutsy gibbon, and i know how to get gdm themes from the internet and install them in the login window.

i'm quite frustrated with this problem that i'm facing - although i click the +Add Item button and the login theme is shown in the list AND i select the theme that i want, it doesn't actually change.

It kept showing this theme (like the ubuntu beige theme). i forgot the name because i removed the item, making it permanently lost. i thought this would solve the problem. but then when i logged out and came back, a window came up and said, "the ubuntu (whatever the name is) theme cannot be found" and it showed a completely different theme than i had selected still!

i really don't know what to do. i don't believe it's for a specific theme, but it doesn't switch to any theme. if anyone has any idea on how to deal with this, i would greatly appreciate the help.

---

### Post by Inxsible on 2008-06-03
1) Are you sure its a GDM theme that you are trying to install and not a GTK theme?

2) You could also install it by dragging and droping the tar.bz2 directly in the Login Window

3) Finally, Make sure that you have the theme "selected" in the checkbox next to the name of the theme. Or if you are using a Random theme out of selected option(above the theme window) - then too, you need to have that theme and a few others check marked.

---

### Post by mochiko on 2008-06-05
> **Inxsible said:**
> 1) Are you sure its a GDM theme that you are trying to install and not a GTK theme?

2) You could also install it by dragging and droping the tar.bz2 directly in the Login Window

3) Finally, Make sure that you have the theme "selected" in the checkbox next to the name of the theme. Or if you are using a Random theme out of selected option(above the theme window) - then too, you need to have that theme and a few others check marked.

thanks for the reply, i really appreciate it!

1. i went to gnome look and yes it is a GDM theme. here's the filename
Hardy-Simple Wine GDM.tar.gz
i also tried another file - 50255-wizard.tar.bz2
i dragged them in, and they show up in the theme window. i select it, it shows that i've selected it. 

see, everything works fine. it asks me whether i want to install it, and i say yes. it shows that it's been installed, it let's me select themes. but the problem is that when i actually log in, the selected theme does not come. 

what am i doing wrong? perhaps hte Style i chose is wrong? 
I tried "THemed with a face browser" and "Themed" and still no change.

And even now, everytime i log in, the first window is one that says, "Sorry, your human theme cannot be found" as an error message.

something is wrong and i don't know how to fix it! please help me if anyone can..

---

### Post by mochiko on 2008-06-06
it's okay, i got it to work somehow!

i had to change stuff in gdm.conf and it works.
thanks anyways!

---

