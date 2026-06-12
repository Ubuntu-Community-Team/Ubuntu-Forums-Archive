---
title: "Software Centre - Disc Utility launch"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by RayArdia on 2011-10-31
Trying to launch Disc Utility. From Help I read;-

Using a program once it’s installed
For most programs, once they are installed, you can launch them from the Applications menu. (Utilities for changing settings may appear inside System &#9656; Preferences or System &#9656; Administration instead).
To find out where to launch a new program, navigate to the screen for that program in Ubuntu Software Center, if it is not still being displayed. The menu location should be displayed on that screen, below the colored bar.

For 'from the Applications menu' I assumed I needed to go 'Dash? then the app. Not there. Disc Utility screen in Software Centre wasn't any help either.
Where in Ubuntu 11.10 do I find the System>Preferences or>Administration?
There is no reference to how to install on the  Disc Utility page - and there's no 'colored' or even coloured line.

I think I am beginning to regret upgrading to 11.10, perhaps it's just because I'm a 'wrinkly' that I'm having problems getting used to it - but perhaps I'm not alone................?

---

### Post by westie457 on 2011-10-31
> **RayArdia said:**
> Trying to launch Disc Utility. From Help I read;-

Using a program once it’s installed
For most programs, once they are installed, you can launch them from the Applications menu. (Utilities for changing settings may appear inside System &#9656; Preferences or System &#9656; Administration instead).
To find out where to launch a new program, navigate to the screen for that program in Ubuntu Software Center, if it is not still being displayed. The menu location should be displayed on that screen, below the colored bar.

For 'from the Applications menu' I assumed I needed to go 'Dash? then the app. Not there. Disc Utility screen in Software Centre wasn't any help either.
Where in Ubuntu 11.10 do I find the System>Preferences or>Administration?
There is no reference to how to install on the  Disc Utility page - and there's no 'colored' or even coloured line.

I think I am beginning to regret upgrading to 11.10, perhaps it's just because I'm a 'wrinkly' that I'm having problems getting used to it - but perhaps I'm not alone................?

All programs not in the Launcher Panel are started the same way.

Click on the button Top-Left, the Dash pops out, start typing the name of what you want to start - after a couple of key-presses its icon will be showing in the Dash if it has been installed.

When installing from SC you are given the chance to add the program to the Launcher if it has a gui. If no option then it is a terminal only app you are installing.

Preferences and Administration is handled with System Settings under the power button at the top right of the screen. The same one used to shutdown your computer.

By the way, Disc Utility is already installed.

Hope this helps

---

### Post by RayArdia on 2011-10-31
Disc Utility doesn't appear in Dash when typed. No option to add to Launcher so I guess it must be a terminal-only app?

Reason I wanted to open Disc Utility was that I hoped, by using it, to sort out which of my partitions contains the version of 11.10 that has my (now) successfully restored data. Then I want to expand that partition and scrub the others. BTW I have Gparted on a CD but it doesn't seem to tell me anything about the actual data, just the sizes of the partitions so I'm worried that I might delete the wrong ones!
Ray

---

### Post by westie457 on 2011-10-31
Open a terminal and type in ```
palimpsest
```

#This is the terminal command for 'Disk Utility', if it is not installed you will be informed about how to install.

Another thing you can try is opening the 'File Browser' by clicking on your Home Folder, usually the top icon in the Launcher. In the window that opens in the left pane will be a list containing various things including partitions whether they are mounted or not. Clicking on one will mount it for viewing. Your current OS will be listed as 'File System'.

---

### Post by RayArdia on 2011-10-31
Thank you. After lots of problems, starting from upgrading from 9.10 to 10.10 etc etc, I now have lots of 'bitty' partitions, including no less than 5 Swap spaces.
I have a copy (not a backup) of my Home folder on a removable HDD. Perhaps my best bet is to go back to 'square one', format the drive, reinstall 11.10 and then copy my Home folder from my removable drive.
As I said before I have GParted live, and of course 11.10, on CDs.
Can you foresee any problems?
Ray

---

### Post by Mark Phelps on 2011-10-31
That's because -- it's not "Disc" Utility; it's "Disk" Utility.  Spelling is important in Dash.

---

### Post by RayArdia on 2011-10-31
.Thank you Mark

---

