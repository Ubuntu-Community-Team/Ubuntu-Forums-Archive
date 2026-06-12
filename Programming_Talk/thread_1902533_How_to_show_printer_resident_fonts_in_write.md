---
title: "How to show printer resident fonts in write?"
date: 2011-12-31
forum: Programming Talk
---

### Post by Gurmeet Singh on 2011-12-31
[SIZE=2]Hi,

I am working on to develop a driver for 24 pin dot matrix printer using CUPS on Ubuntu. Printer has some resident fonts which i have mentioned in ppd file but now i want when driver installed on [/SIZE][SIZE=2]system then font should display in writer's font combo box like in libreoffice writer.
[/SIZE][SIZE=2]
Welcome if anybody share the procedure or some relevant links.

Thanks in advance.
[/SIZE]

---

### Post by Gurmeet Singh on 2012-01-02
Hi Experts,

Please help me to solve this one.
Thanks.

---

### Post by Zugzwang on 2012-01-02
Is it a PostScript printer?

If not, you should first search the CUPS documentation whether CUPS is actually able to use printer fonts on non-PostScript printer. This is highly non-trivial and might be unsupported.

If it is a PostScript printer, here is some link that I've found that tells you a bit about font-matching: [http://leuksman.com/linux/TrueType-HOWTO-6.html]("http://leuksman.com/linux/TrueType-HOWTO-6.html") You will need a usable copy of the printer's font as a font file in some format.

---

### Post by Gurmeet Singh on 2012-01-03
Thanks for your kind response.

> 
Is it a PostScript printer?

Yes, It is a PostScript Printer.

> 
You will need a usable copy of the printer's font as a font file in some format.


I have done this in windows for same printer. I have used .ufm font files in case of windows. This is automatic in windows DDK. I have just given the reference in .GPD file for font files. when printers installed/Uninstalled, these .ufm files automatically installed/uninstalled in system but i don't know how same is possible in ubuntu (in PPD files).

Please let me know, Where i can give reference of font files in ppd file or i have to develope a C/C++ program to acheive this?

Thanks.

---

### Post by Gurmeet Singh on 2012-01-03
Hi Experts,
Please look at below links for MS Windows. I want to implement same in ubuntu.
[http://www.techknowledgecorp.com/help/wherefontfrom.html](http://www.techknowledgecorp.com/help/wherefontfrom.html) <Read Paragraph under printer Driver>.

Thanks.

---

### Post by Zugzwang on 2012-01-03
If you already have font files for the printer fonts, it looks like as if  the link I've postet above should provide you help.

---

### Post by Gurmeet Singh on 2012-01-04
Hi Zugzwang,


Can i use .afm font files to solve my purpose?

if Yes then i have .afm files and i have mentioned these font file names in ppd files as in below format for example *font Draft 5 cpi:  Standard "(0001.006S)" Standard ROM
but these fonts are not shown in office writer. Where i have to copy .afm files so that these fonts are available in writer?
Sorry if i am asking foolish question. I am new to linux so confused.

Thanks in advance

---

### Post by Zugzwang on 2012-01-04
> **Gurmeet Singh said:**
> Can i use .afm font files to solve my purpose?


Did you actually read the page behind the link that I've posted above?

---

### Post by Gurmeet Singh on 2012-01-05
Hi Zugzwang,

I think i have not explained problem scenario in detail. Sorry for that.
Let me explain the problem scenario in detail
I am developing Dot Matrix Printer driver using CUPS. I have ppd file supplied by the vendor. I am able to print using ppd file through CUPS. Printer has some resident fonts. Now the requirement is that when Driver installed on system (Ubuntu) and same printer set as default printer then the fonts should display in the office writer's font combo box. If My printer is not default printer then font should not display in office writer's font combo box.

I have done same in case of windows. In windows i have developed driver for same printer with the help of WDK. I have given the reference of .ufm files in GPD file and compiled the same. It is working as expected. I want same in case of Ubuntu.

Thanks.

---

### Post by Zugzwang on 2012-01-05
I can't give you much help on details on how to achieve your task. But here is something that I can tell:

> **Gurmeet Singh said:**
> Now the requirement is that when Driver installed on system (Ubuntu) and same printer set as default printer then the fonts should display in the office writer's font combo box. If My printer is not default printer then font should not display in office writer's font combo box.


You might be better off *not* to rely on something like a default printer. First of all, the KDE default printer might be different to the GNOME default printer (as far as I know), so the default printer might be not well defined. Then, something like a printer driver might only be loaded when actually needed, and due to the fact that the font system in Linux is absolutely non-connected to printer drivers, having a font show up only when a driver is selected will be quite difficult and error-prone undertaking.

---

### Post by Gurmeet Singh on 2012-01-05
Thanks for your Response.

> 
You might be better off *not* to rely on something like a default  printer. First of all, the KDE default printer might be different to the  GNOME default printer (as far as I know), so the default printer might  be not well defined. Then, something like a printer driver might only be  loaded when actually needed, and due to the fact that the font system  in Linux is absolutely non-connected to printer drivers, having a font  show up only when a driver is selected will be quite difficult and  error-prone undertaking.


Please look at [http://www.techknowledgecorp.com/help/embedfontwin.html](http://www.techknowledgecorp.com/help/embedfontwin.html) link.
I have googled but nothing found helpful which describes same as in link above for Linux (Ubuntu)


Thanks in advance.

---

### Post by Zugzwang on 2012-01-05
> **Gurmeet Singh said:**
> 
I have googled but nothing found helpful which describes same as in link above for Linux (Ubuntu)


That's because Font handling works in a different way in Linux. For example, read the chapter "Background" in [http://en.gentoo-wiki.com/wiki/X.Org/Fonts](http://en.gentoo-wiki.com/wiki/X.Org/Fonts).

There is no reason that the sentence from your first line ("There are basically four ways that fonts appear in your applications: the operating system's Fonts folder, a type manager, local application folders, or the printer driver.") is true in Linux, too. In particular, given the complexity of the printing subsystem, I find it unlikely that a printer driver itself can install a font (unless you install it along with the font). Of course, I may be wrong, but there is no reason to believe so yet. If you want to install a font along with the printer for usage in LibreOffice, then the link I've provided you gives you some help. Note that the StarOffice suite which is mentioned there is a predecessor of LibreOffice and thus, what is written there, is likely to apply in LibreOffice, too.

---

### Post by Gurmeet Singh on 2012-01-06
Hi Zugzwang,

Thanks for your valuable help.

**I have a shell script which installs ttf in /usr/share/fonts . Can i use this script to solve my purpose?**

I have used same script to install the fonts in /usr/share/cups/fonts but it is not working.
How i can install fonts at same location.

Bellow is the link for script which i am using.
[http://ubuntuforums.org/showthread.php?t=275202&page=17](http://ubuntuforums.org/showthread.php?t=275202&page=17)

Thanks.

---

### Post by Zugzwang on 2012-01-06
> **Gurmeet Singh said:**
> http://ubuntuforums.org/showthread.php?t=275202&page=17


Can you post a link to the *post* and not the *page*? - I don't see any script on that page, probably because my forum settings are different to yours. Anyway, telling precisely which script you mean would make things easier.

Also, "doesn't work" isn't very specific. Please elaborate on that.

---

### Post by Gurmeet Singh on 2012-01-07
Hi Zugzwang,

The link for the post is [ubuntuforums.org/showthread.php?t=275202]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=275202")
and shell script which i am using is 

```

#!/bin/bash
#
# This script helps to install fonts
#
# Set your default font storage directory here
##DEFAULT_DIR="$HOME/fonts"
DEFAULT_DIR=`pwd`
# Set the default font installation directory here
DEFAULT_DEST="/usr/share/fonts/truetype/freefont"


# Don't edit anything below unless you know what you're doing.

echo "In which directory are the fonts?"
echo -n "[$DEFAULT_DIR] "\
read DIR

echo
echo "What is the extention (without the dot) of the fonts?"
echo -n "[ttf] "\
read EXT

echo
echo "Where should the fonts be installed?"
echo "DO NOT CHANGE THIS UNLESS YOU KNOW WHAT YOU'RE DOING!"
echo -n "[$DEFAULT_DEST] "\
read DEST

if [ -z "$DIR" ]; then
    DIR="$DEFAULT_DIR"
fi

if [ -z "$EXT" ]; then
    EXT="ttf"
fi

if [ -z "$DEST" ]; then
    DEST="$DEFAULT_DEST"
fi

sudo -v
if [ $? != 0 ]; then
    echo "Unable to obtain the necessary privileges. Exiting..."
    echo -n "Press <Enter> to continue. "
    read WER
    exit $?
fi

echo
echo

if [ ! -d "$DIR" ]; then
    echo "Directory $DIR does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read SDF
    exit 2
fi

if [ ! -d "$DEST" ]; then
    echo "Directory $DEST does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read DFG
    exit 1
fi

echo "Copying fonts..."
cd "$DIR"

for i in *."$EXT"; do
    sudo cp -iv "$i" "$DEST"
done

echo
echo
echo "Updating the font cache..."
sudo fc-cache -fv

if [ $? != 0 ]; then
    echo "Error updating the font cache. Your fonts haven't been completely installed. Try running sudo fc-cache -fv manually. Exiting..."
    echo -n "Press <Enter> to continue."
    read FSF
    exit $?
fi

echo
echo
echo "Finished."
echo
echo "You will probably need to restart running programs to use the new fonts."
echo -n "Press <Enter> to exit. "
read WERT
exit 0

```
> 
I have used same script to install the fonts in /usr/share/cups/fonts but it is not working.
When i install the fonts in /usr/share/cups/fonts, then the installed fonts are not showing in office writer.
Where i have to change the script so that the fonts installed on above mentioned directory will show up in office writer.

Thanks.

---

### Post by Zugzwang on 2012-01-09
> **Gurmeet Singh said:**
> 
The link for the post is [ubuntuforums.org/showthread.php?t=275202]("http://ubuntuforums.org/ubuntuforums.org/showthread.php?t=275202")
and shell script which i am using is 


Don't use this script! You should never install something into "/usr/share" while bypassing the package manager, as this can cause serious problems on the user's PC. A cleaner alternative is to create an Ubuntu package that contains the font, and to add post-installation and post-remove scripts for updating the font cache.

---

### Post by Gurmeet Singh on 2012-01-10
> 
Don't use this script! You should never install something into  "/usr/share" while bypassing the package manager, as this can cause  serious problems on the user's PC. A cleaner alternative is to create an  Ubuntu package that contains the font, and to add post-installation and  post-remove scripts for updating the font cache.


That means i have to install all required fonts when i will install the driver and these all fonts will be available to whole system that is if default printer is from other vendor then my fonts still displays in office writer's combo box and anyone can use it? The fonts will be removed when driver uninstalled?

Thanks.

---

### Post by mssever on 2012-01-10
> **Gurmeet Singh said:**
> That means i have to install all required fonts when i will install the driver and these all fonts will be available to whole system that is if default printer is from other vendor then my fonts still displays in office writer's combo box and anyone can use it? The fonts will be removed when driver uninstalled?

Thanks.
If you install the fonts as part of the driver installation process, then the fonts will be available to any app that is capable of using them, for them to use as they choose to use them. If your installer is a .deb file, then the fonts will be removed when the driver is removed.

---

### Post by Gurmeet Singh on 2012-01-10
> 
If you install the fonts as part of the driver installation process,  then the fonts will be available to any app that is capable of using  them, for them to use as they choose to use them. If your installer is a  .deb file, then the fonts will be removed when the driver is removed.


Thanks for your reply,

I am developing driver for 24 pin DMP using CUPS.
Can i use .deb package to install cups driver? 
if yes then please provide the links to start with and which type of font files (ttf, afm etc) i have to install with .deb?

Thanks.

---

### Post by Zugzwang on 2012-01-10
> **Gurmeet Singh said:**
> 
Can i use .deb package to install cups driver? 


Yes, of course. All program/driver installations are done this way in a Debian Linux or Ubuntu system.


> **Gurmeet Singh said:**
> 
if yes then please provide the links to start with


The stickies of this forum contains links to .deb making HOWTOs. So you should head there for information.

> **Gurmeet Singh said:**
> 
and which type of font files (ttf, afm etc) i have to install with .deb?

I don't know and suggest reading into the documentation of the integral parts of the font management system in a modern Linux distribution in order to do so. You can also look into other packages that contain fonts and check out how they do it.

Here's an additional note: if you ask some question the next time, make sure that it is obvious that you did some research using google or any other search engine beforehand. You can do so by asking more precise questions. The reason is that otherwise, people are likely not to answer you here and they would feel that they are doing your work then.

---

### Post by Gurmeet Singh on 2012-01-11
Thank you very much for your kind response throughout the discussion.
I will contact with you again if needed.

> 
Here's an additional note: if you ask some question the next time, make  sure that it is obvious that you did some research using google or any  other search engine beforehand. You can do so by asking more precise  questions. The reason is that otherwise, people are likely not to answer  you here and they would feel that they are doing your work then.


Thanks Zugzwang.
I will take care next time.

---

### Post by Gurmeet Singh on 2012-01-12
Hi Experts,

> 
If you install the fonts as part of the driver installation process,  then the fonts will be available to any app that is capable of using  them, for them to use as they choose to use them. If your installer is a  .deb file, then the fonts will be removed when the driver is removed.


Can i use rpm package also?

Thanks.

---

