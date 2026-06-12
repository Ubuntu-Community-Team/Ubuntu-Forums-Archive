---
title: "how to create a shortcut"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by mike acker on 2012-11-29
how can I create a shortcut that will take me quickly to my DEBUG directory
```
~/Desktop/c_programs/Factoring_Project_Dir/Factoring_Project_wksp/Factoring_Project/Debug$
```from my desktop ?

the odds of me typing all that in without cussing ain't too good

---

### Post by Abhinav Kumar on 2012-11-29
> **mike acker said:**
> how can I create a shortcut that will take me quickly to my DEBUG directory
```
~/Desktop/c_programs/Factoring_Project_Dir/Factoring_Project_wksp/Factoring_Project/Debug$
```from my desktop ?

the odds of me typing all that in without cussing ain't too good
Hi mike,
Just navigate to ~/Desktop/c_programs/Factoring_Project_Dir/Factoring_Project_wksp/Factoring_Project/

You will see the folder named Debug. Select and right Click. Select Make Link from right Click Menu. You will see a link icon. Cut this link and paste on your desktop. Now, if you click this link, it will always open Debug folder.

Regards,
Abhinav

---

### Post by Pletched on 2012-11-29
Click anywhere on the desktop or folder;  right click in an empty area and select "create launcher..." change the type to location, input the rest and you're done.

This will create a link I think.

---

### Post by mike acker on 2012-11-29
> **Abhinav Kumar said:**
> Hi mike,
Just navigate to ~/Desktop/c_programs/Factoring_Project_Dir/Factoring_Project_wksp/Factoring_Project/

You will see the folder named Debug. Select and right Click. Select Make Link from right Click Menu. You will see a link icon. Cut this link and paste on your desktop. Now, if you click this link, it will always open Debug folder.

Regards,
Abhinav

cool, but: it created "Link to Debug" and it won't let me rename it.  I need it to read Link_to_Factoring

---

### Post by gnusci on 2012-11-29
Run the following command:

$ ln -s ~/Desktop/c_programs/Factoring_Project_Dir/Factoring_Project_wksp/Factoring_Project/Debug ~/Desktop/Link_to_Factoring

---

### Post by Abhinav Kumar on 2012-11-30
> **mike acker said:**
> cool, but: it created "Link to Debug" and it won't let me rename it.  I need it to read Link_to_Factoring
Hi,
Press F2 and rename it.

Regards,
Abhinav

---

