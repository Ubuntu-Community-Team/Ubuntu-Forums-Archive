---
title: "Make Wine apps look better"
date: 2009-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Vadi on 2009-01-14
Found this neat tutorial today on how to make wine apps look much better. [SIZE="4"][The original tutorial is available here]("http://www.ubuntuproductivity.com/journal/software/01/2009/theme-wine-integrate-with-ubuntu-human/")[/SIZE] - I didn't write it, just reposted here with permission.

**Before**:
[CENTER][IMG]http://www.ubuntuproductivity.com/journal/wp-content/uploads/2009/01/screenshot_06.png[/IMG][/CENTER]

**After**:
[CENTER][IMG]http://www.ubuntuproductivity.com/journal/wp-content/uploads/2009/01/screenshot_05.png[/IMG][/CENTER]

**[SIZE="3"]Tip[/SIZE]**

Theme Wine apps to better integrate with Ubuntu’s Human theme
[B][SIZE="3"]
Resources[/SIZE][/B]

- [How to install a theme in Wine]("https://help.ubuntu.com/community/Wine")
-   Look to the section entitled “Using Theme/Skin”
- [Ubuntu Human theme on Deviant Art]("http://fioressj.deviantart.com/art/Human-for-Windows-37743373")

**[SIZE="3"]Notes[/SIZE]**

I had read quite a bit about [Wine’s theming capabilities being limited]("http://tombuntu.com/index.php/2008/01/04/stop-wine-from-beating-your-windows-apps-with-the-ugly-stick/"), slow, and rather useless, but thought I would give it a go anyways. I was pleasantly surprised to find that after following [these instructions]("https://help.ubuntu.com/community/Wine") Wine ran just as fast and looked **a lot** better.

Here is a summary of the steps I followed:

- Of course, make sure [Wine is installed]("apt:wine")
- [Download the Ubuntu Human theme from Wine from Deviant Art]("http://fioressj.deviantart.com/art/Human-for-Windows-37743373")
- Navigate to /home/<username>/.wine/drive_c/windows/Resources/Themes/
- You probably have to create Resources and Themes
- Install the *Human* theme folder (that you downloaded from Deviant Art) inside the */Resources/Themes/* folder
- The final path to the theme’s .msstyles file needs to be /home/<username>/.wine/drive_c/windows/Resources/Themes/Human/Human.msstyles
- Run Wine Config
- Choose the Human theme in the Desktop Integration tab
- Click Apply and Ok, then it will re-render all Wine apps in the new theme

**Enjoy!**

Source: [http://www.ubuntuproductivity.com/journal/software/01/2009/theme-wine-integrate-with-ubuntu-human/](http://www.ubuntuproductivity.com/journal/software/01/2009/theme-wine-integrate-with-ubuntu-human/)

---

### Post by KillerKiwi on 2009-01-15
The script from this post uses the colors from your current GTK theme :)

[http://ubuntuforums.org/showpost.php?p=5506889&postcount=29](http://ubuntuforums.org/showpost.php?p=5506889&postcount=29)

---

### Post by Vadi on 2009-01-15
Thanks for that!

---

### Post by WastePotato on 2009-01-16
Nice. :D

---

