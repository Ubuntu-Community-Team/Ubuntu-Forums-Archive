---
title: "HOWTO: Tahoma Font in Breezy"
date: 2005-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Casey on 2005-10-26
**As far as I can tell, microsoft distributes this under a different license than the other true type core fonts.  I think that you have to have a valid windows license to use this.**

I did this for a friend who wanted to use Tahoma in Breezy.
The msttcorefonts package was already installed in this case.  It is a prereq for this to work that you install the msttcorefonts package (to create the directory that we will use).  You could modify this to use a different fonts directory, but this howto would not cover it).

Disclaimer: I don't have a Windows license so as far as I can tell I am not allowed to do this by the license.  Therefore I really can't help if it doesn't work, though I don't see any reason it wouldn't work (it worked on my friend's copy of breezy).

The first step is to install cabextract if you do not already have it installed.  You can do this through synaptic.  If you have already installed the msttcorefonts package (which creates a directory that we use later and thus is necessary), then you do not need to perform this step, as cabextract was installed at that time.

Next download the tahoma font package from microsoft.  It is available here: 
[http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB]("http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB")

I obtained this link from the .spec file at [http://corefonts.sourceforge.net/]("http://corefonts.sourceforge.net/")

Next, using the terminal navigate to the directory to which you downloaded the file.  For my friend, this was the desktop.
```
cd Desktop
```
At this point a new folder was created:
```
mkdir tahomafont
```
Now the downloaded font was moved to the tahomafont folder:
```
mv IELPKTH.CAB tahomafont
```
Now the directory was changed to the tahomafont folder:
```
cd tahomafont
```
Now the cabextract utility was used on the .CAB file:
```
cabextract IELPKTH.CAB
```
Now the resulting .ttf files were copied to the msttcorefonts folder in the system's fonts directory (note this step will require sudo):
```
sudo cp *.ttf /usr/share/fonts/truetype/msttcorefonts/
```

Now the fonts should be installed.  Open up the Gnome font selector (System->Preferences->Font) and insure that the Tahoma font is available in both regular and bold forms.

Edit: At this point feel free to delete the tahomafont directory that you created, as well as all of its contents.

Hopefully this will be of assistance to some people.

---

### Post by Xian on 2005-10-26
You could also verify that font path is in your /etc/X11/xorg.file.
Just look in the Section "Files" and review the FontPaths listed.

Also rebuild your font cache.

$ sudo fc-cache -f -v

---

### Post by poofyhairguy on 2005-11-09
This almost got lost in the desktop forum. Glad I wanted Tahoma and found it.

---

### Post by majed on 2005-11-09
What i did was copy the tahoma.ttf file from my windows installation to my ubuntu fonts directory and then rebuilt the font cache and all was fine :)

---

### Post by cowlip on 2005-12-11
THis worked great, THANK U!

---

### Post by shigs on 2006-03-26
Good stuff, this should probably be tacked onto some of the counter strike and wine FAQ's.

---

### Post by stoffe on 2006-04-10
Just wanted to say thanks a lot! =)

---

### Post by detyabozhye on 2006-04-12
Thanks, helped me with installing fonts in general. ^_^

---

### Post by repeat on 2006-04-12
[QUOTE=majed]What i did was copy the tahoma.ttf file from my windows installation to my ubuntu fonts directory and then rebuilt the font cache and all was fine :)[/QUOTE]
Where can I find the fonts directory?

I can't use the 'go to font folder' option in preferences -> fonts because I need root access for copying. So I have to use the command line for this...

---

### Post by majed on 2006-04-16
[QUOTE=repeat]Where can I find the fonts directory?

I can't use the 'go to font folder' option in preferences -> fonts because I need root access for copying. So I have to use the command line for this...[/QUOTE]

It is a hidden directory under your home directory; its name is (.fonts). Using the terminal, you can go to it with this command:

```
cd ~/.fonts
```

Good luck!

---

### Post by Sarisar on 2006-04-25
OK thanks all.  I did it a mix of all the way.  Got my father to copy over all his FONT directory onto a USB stick (I was too lazy to reboot into windows on my laptop).  Copied the TTFs into ~/.fonts and ran the fc-cache and... then it crashed when trying to select the font.

So don't try ALL the TTF fonts.  But just tahoma works fine :)

Thanks again everyone - I may yet beat Ubuntu with your help :)

---

### Post by justaguynpc on 2006-04-25
Thanks, I was really at a loss with my install of Dapper without Tahoma!

Everything is as it should be ....................... :)

---

### Post by maulattu on 2006-05-08
[QUOTE=majed]What i did was copy the tahoma.ttf file from my windows installation to my ubuntu fonts directory and then rebuilt the font cache and all was fine :)[/QUOTE]

nice! this simple method worked very good for me :) (followed by "*sudo fc-cache -f -v*")
thanks :-\"

---

### Post by YaNoS on 2006-05-08
Thanks for the 'HOWTO'!

---

### Post by kostkon on 2007-06-09
Thank you very much for this HOWTO!!

---

### Post by ~~Tito~~ on 2007-07-07
i have a problem when you get to the last part it says there is no file or folder.

---

### Post by Pronco on 2007-07-14
it doesn't work in Ubuntu Feisty Fawn 

It looks like a squares

it should be something wrong in particular as I should change something I guess 

Here's a snapshot attached to this POST . Take a peek into it 

Cheers, 
Pronco

---

### Post by Pronco on 2007-07-14
Any updates 

Thank You!

---

### Post by toutatis on 2007-07-20
Thanks for the explanation, Tahoma is my favourite font. It was what I missed most from Windows.

Roel

---

### Post by Pronco on 2007-08-08
Did someone take a look into my snapshot ?

I would ask you to attend to my issue as possible as you can.

Thank you.

---

### Post by jfarschman on 2007-10-30
> **~~Tito~~ said:**
> i have a problem when you get to the last part it says there is no file or folder.

Tito, You need to install the MS Core Fonts

apt-get install msttcorefonts

Then follow the instructions to add the missing Tahoma font.

---

### Post by Pronco on 2007-11-11
Eventually Tahoma is currently working in my Ubuntu 

It has been fixed by a tweaked fontconfig XML files and currently looks like on Windows

Thank You
Pronco

---

### Post by Impaque on 2007-12-17
Works like a charm in Ubuntu 7.10. Moreover, this Tahoma font actually *works*, unlike the Tahoma I copied from my Windows XP (I haven't actually done a diff on them to see if they differ, but the method from this thread simply worked instantly, while WinXP Tahoma gave squares instead of letters, like someone posted on this topic).

Thanks!

---

### Post by escobar_ on 2008-03-03
> **Impaque said:**
> Works like a charm in Ubuntu 7.10. Moreover, this Tahoma font actually *works*, unlike the Tahoma I copied from my Windows XP (I haven't actually done a diff on them to see if they differ, but the method from this thread simply worked instantly, while WinXP Tahoma gave squares instead of letters, like someone posted on this topic).

Thanks!

Thank you guys so much for this guide. I copied Tahoma from my XP installation but only squares showed up. With this guide I got everything working nicely.

Cheers!

---

### Post by MasterProg on 2008-07-06
Here's a shell script I made to do this automatically. It installs msttcorefonts package and downloads and installs Tahoma font. After that font cache is rebuilt.

```

#!/bin/bash
# Install Microsoft Fonts (Including Tahoma)

if [ "$(id -u)" == "0" ]
then
  if apt-get install msttcorefonts; then
    mkdir temp-tahomafont
    cd temp-tahomafont
    if wget http://download.microsoft.com/download/ie6sp1/finrel/6_sp1/W98NT42KMeXP/EN-US/IELPKTH.CAB; then
      cabextract IELPKTH.CAB
      if cp *.ttf /usr/share/fonts/truetype/msttcorefonts/; then
        if fc-cache -fv; then
          cd ..
          rm -r temp-tahomafont
          echo "Microsoft fonts are now installed"
        else
          echo "Could not rebuild font cache"
          exit -1
        fi
      else
        echo "Could not copy the font to /usr/share/fonts/truetype/msttcorefonts/"
        exit -1
      fi
    else
      echo "Could not download Tahoma font"
      exit -1
    fi
  else
    echo "Could not install msttcorefonts package" 
    exit -1
  fi
else
  echo "Run 'sudo ./addfonts.sh'"
  exit 0
fi

```

Save it as 'addfonts.sh', allow it to execute: ```
chmod +x addfonts.sh
``` and then run it as root: ```
sudo ./addfonts.sh
```

---

### Post by Lunx on 2009-02-05
I've been looking for an easy way to get hold of Tahoma, followed the steps in the OP and it worked perfectly in Intrepid :)

Found this site that has some really interesting information on [fonts in Linux]("http://avi.alkalay.net/linux/docs/font-howto/Font.html")

---

### Post by eju on 2009-04-28
Thank you Casey, that worked fine.
Really useful article

---

### Post by cyrylski on 2010-05-04
works cool under Lucid Lynx, 10.04. 

Thanks a lot for the script!

---

