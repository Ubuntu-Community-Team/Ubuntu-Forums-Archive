---
title: "Menu icons not working?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-05-19
Several (but not all) of my menu icons do not start the programs they are supposed to start. Is there a fix?:(

---

### Post by NewDisciple on 2008-05-19
Right click on the icon - then properties - look at command and make sure the file path is correct.

---

### Post by oldrocker99 on 2008-05-19
> **NewDisciple said:**
> Right click on the icon - then properties - look at command and make sure the file path is correct.

When I right click, I get Add this launcher to panel
                          Add this luncher to Desktop
                          Entire Menu -> Add this as drawer to panel
                                         Add this as menu to panel

No properties at all...:(

---

### Post by DieB on 2008-05-19
navigate to main menu via system-settings (might be slightly different) inside that you get the ability to realign or to change the commands of your apps.

---

### Post by N.N. on 2008-05-19
> **oldrocker99 said:**
> When I right click, I get Add this launcher to panel
                          Add this luncher to Desktop
                          Entire Menu -> Add this as drawer to panel
                                         Add this as menu to panel

No properties at all...:(

I think NewDisciple meant that you should right-click on the menu itself, i.e. the Ubuntu icon, and then select "Edit menus". Alternately, go to "System" > "Preferences" > "Main menu".

Once you've thus opened the menu editor, right-click on one of the defective launchers, click "Properties", and see if the command field looks odd. Try to compare it to the command field of one of the working launchers. Also, please post what it says in the command field of one of the defective launchers.

---

### Post by oldrocker99 on 2008-05-19
> **DieB said:**
> navigate to main menu via system-settings (might be slightly different) inside that you get the ability to realign or to change the commands of your apps.

Uh, where is system-settings?

Two weeks and I still feel n00bish...:confused:

---

### Post by N.N. on 2008-05-19
> **oldrocker99 said:**
> Uh, where is system-settings?

Two weeks and I still feel n00bish...:confused:

See attached image. The menu items are in Danish, but you'll get the gist of it. :)

---

### Post by NewDisciple on 2008-05-19
Thank you N.N., that's what I meant.  You have got it covered.

---

### Post by oldrocker99 on 2008-05-19
> **N.N. said:**
> I think NewDisciple meant that you should right-click on the menu itself, i.e. the Ubuntu icon, and then select "Edit menus". Alternately, go to "System" > "Preferences" > "Main menu".

Once you've thus opened the menu editor, right-click on one of the defective launchers, click "Properties", and see if the command field looks odd. Try to compare it to the command field of one of the working launchers. Also, please post what it says in the command field of one of the defective launchers.

OK, I figured out how to get to the menu editor (thanks!). The icons that work appear to have a %U after the command, or at least some of them. I tried putting a %U after the command for the Pan newsreader (which was the fist program that wouldn't start from the menus), but it still won't start.

Grrrr...:mad:

---

### Post by N.N. on 2008-05-19
> **oldrocker99 said:**
> OK, I figured out how to get to the menu editor (thanks!). The icons that work appear to have a %U after the command, or at least some of them. I tried putting a %U after the command for the Pan newsreader (which was the fist program that wouldn't start from the menus), but it still won't start.

Grrrr...:mad:

Okay. Please post what it says in the command field of the Pan launcher. If it simply says "pan", as it should, then the problem doesn't lie with the launcher. 

If that is the case, try opening a terminal by going to "Applications" > "Accessories" > "Terminal" and type the following command: ```
pan
``` This will attempt to launch pan and output error messages that will reveal what is preventing the program from being launched. Please post these error messages.

EDIT: If there are a lot of error messages, you can benefit by redirecting them to a text file. Run the following command in a terminal to do so: ```
pan &> pan_error.txt
``` You can then attach this file to your next post.

---

### Post by oldrocker99 on 2008-05-19
> **N.N. said:**
> Okay. Please post what it says in the command field of the Pan launcher. If it simply says "pan", as it should, then the problem doesn't lie with the launcher. 

If that is the case, try opening a terminal by going to "Applications" > "Accessories" > "Terminal" and type the following command: ```
pan
``` This will attempt to launch pan and output error messages that will reveal what is preventing the program from being launched. Please post these error messages.

EDIT: If there are a lot of error messages, you can benefit by redirecting them to a text file. Run the following command in a terminal to do so: ```
pan &> pan_error.txt
``` You can then attach this file to your next post.

OK, here's the error message:
pan: parts.cc:244: 
void pan::Parts::set_parts(const pan::PartBatch&): 
Assertion `pch == part_mid_buf + part_mid_buf_len' failed.
Aborted

This is after a reinstallation via Synaptic (I haven't tried a complete removal and reinstallation yet)

---

### Post by N.N. on 2008-05-19
The error is specific to Pan it seems. According to a forum thread from the archive ([http://ubuntuforums.org/archive/index.php/t-441073.html](http://ubuntuforums.org/archive/index.php/t-441073.html)) you should be able to fix it by deleting the tasks.nzb file, which is located in the .pan2 folder in your home directory:

Open the file manager and press CTRL+H or go to "View" > "Show hidden files" to reveal hidden folders (those that begin with a period character, such as .pan2). Find the folder called .pan2, open it, and delete the file in it called tasks.nzb. Then try to start Pan again to see if this has fixed the problem. If it hasn't, delete the entire .pan2 directory and start Pan again.

---

### Post by oldrocker99 on 2008-05-19
> **N.N. said:**
> The error is specific to Pan it seems. According to a forum thread from the archive ([http://ubuntuforums.org/archive/index.php/t-441073.html](http://ubuntuforums.org/archive/index.php/t-441073.html)) you should be able to fix it by deleting the tasks.nzb file, which is located in the .pan2 folder in your home directory:

Open the file manager and press CTRL+H or go to "View" > "Show hidden files" to reveal hidden folders (those that begin with a period character, such as .pan2). Find the folder called .pan2, open it, and delete the file in it called tasks.nzb. Then try to start Pan again to see if this has fixed the problem. If it hasn't, delete the entire .pan2 directory and start Pan again.

That did the trick! These forums are one of the many, many reasons to love Linux, and Ubuntu in particular!

Thanx * 10^6!:KS:biggrin:

---

