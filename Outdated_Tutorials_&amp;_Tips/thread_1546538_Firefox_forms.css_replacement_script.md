---
title: "Firefox forms.css replacement script"
date: 2010-08-05
forum: Outdated Tutorials &amp; Tips
---

### Post by movak on 2010-08-05
If you installed a dark theme for Firefox according to [this HowTo]("http://ubuntuforums.org/showpost.php?p=5479698&postcount=1"), you'll probably need to repeat Step 4 and 5 after each Firefox update which replaces the dark forms.css with the  default firefox forms.css. To  avoid the manual work of restoring the dark forms.css you can use the fcr.sh script.


** 1. Before the first run of the script**

You have to do these steps only once before running the script the first time.

1. Go to the **res** sub-directory which is in the Firefox directory (replace 3.x.x with the installed version)
```
cd /usr/lib/firefox-3.x.x/res
```2. Make a copy of the forms.css with the name forms.css.dark in the same directory:
```
 sudo cp forms.css forms.css.dark
```3. Go to the directory that contains the script and make it executable:
```
chmod 744 fcr.sh
```[B]

2. After a Firefox update[/B]

You can run the script in a terminal or from Gnome.

** Via command line:**

Just go to the directory that contains the script and execute it. For example:

```
cd ~/scripts
./fcr.sh
```**Via Gnome:**

Just double-click on the script file.

If this doesn't work, you can change the corresponding preference in Nautilus in:

Edit, Preferences, Behavior, Executable Text Files

Furthermore, the terminal shouldn't close automatically after the script was executed so that you can see if it was successful. This can be set in the Terminal in:

Edit, Profile Preferences, Title and Command, When command exits: Hold the terminal open


Btw, the script won't change anything if the forms.css has already been replaced.

---

### Post by UltraAnders on 2010-11-08
Followed these steps and still getting the annoying black boxes and font. Are the steps listed in your post all that needs to be done, or should I have first done the steps [here]("http://ubuntuforums.org/showpost.php?p=5479698&postcount=1")? Cheers.

---

### Post by movak on 2010-11-09
Yes, you've to do the steps in the HowTo first. The script just automates step 4 and 5 of the HowTo which have to be repeated after a FF update. I forgot to actually link this thread..  Thanks for the note!

---

