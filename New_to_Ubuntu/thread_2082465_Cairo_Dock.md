---
title: "Cairo Dock"
date: 2012-11-09
forum: New to Ubuntu
---

### Post by czgirb on 2012-11-09
Today I give it a try once again ... and my system FREEZE again. Why?

Based on what I see, Cairo always minimized the opened application as a **BRIGHT POINT** and placed below the icon. How can I set the minimization was placed on **DOCK** ... as **MacOS**.

---

### Post by daslinkard on 2012-11-09
How did you install Cairo Dock?  Did you run the update for the program? Also, can you give specs for the PC you installed it upon?

---

### Post by czgirb on 2012-11-10
> **daslinkard said:**
> How did you install Cairo Dock?
As I remembered the guidance is in [http://glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en](http://glx-dock.org/ww_page.php?p=ppa%20Weekly&lang=en) and it said:
> sudo add-apt-repository ppa:cairo-dock-team/weekly 
sudo apt-get update >/dev/null 
sudo apt-get install cairo-dock cairo-dock-plug-ins

> **daslinkard said:**
> Did you run  the update for the program?
Would you mind to show me how to run it?

> **daslinkard said:**
> 
Also, can you give specs for the PC you  installed it upon?
Lappie Compaq CQ40-328TU

I use 12.04 and run the dock in Ubuntu Classic Desktop Environment
Is it a problem?

Wait for your reply

---

### Post by daslinkard on 2012-11-10
I would recommend purging cairo dock and then reinstalling from the Ubuntu Software Center.  I have played around with cairo dock quite a bit, installing, removing, re-installing, removing, re-re-installing....It has worked pretty flawless downloading from the Software Center.

I would start by purging the program....
```

sudo apt-get purge cairo-dock
```

After it has been removed from the system then go to your Ubuntu Software Center and search for Cairo Dock.  Once you have found the program you will click install.  Once the program has been installed then you can run 
```

sudo apt-get update cairo-dock
```

---

### Post by czgirb on 2012-11-11
[SIZE=4]SORRY ... SORRY[/SIZE]
Just remembered ... I install it from here [http://glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://glx-dock.org/ww_page.php?p=From%20the%20repository&lang=en) it said:
> sudo -v 
 sudo add-apt-repository ppa:cairo-dock-team/ppa 
 sudo apt-get update 
sudo apt-get install cairo-dock cairo-dock-plug-ins
as I used Pangolin, I add the following command:
> deb [http://download.tuxfamily.org/glxdock/repository/ubuntu](http://download.tuxfamily.org/glxdock/repository/ubuntu) precise cairo-dock
and do an update with the following command:
> sudo apt-get update 
sudo apt-get install cairo-dock

---

### Post by newb85 on 2012-11-11
```
sudo -v 
sudo add-apt-repository ppa:cairo-dock-team/ppa 
sudo apt-get update 
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

This much looks fine.  Cairo-dock is already in the main repositories, so adding this PPA wasn't necessary, but it probably gave you a newer version of CD.  However, it is not a good idea to add that PPA and then proceed to add the source
```
deb http://download.tuxfamily.org/glxdock/repository/ubuntu precise cairo-dock
```
to your sources.list file.  CD's website (as you linked) recommends these as two alternative methods for installation.  You shouldn't do both.

---

### Post by czgirb on 2012-11-11
> **daslinkard said:**
> I would recommend purging cairo dock and then reinstalling from the Ubuntu Software Center.  I have played around with cairo dock quite a bit, installing, removing, re-installing, removing, re-re-installing....It has worked pretty flawless downloading from the Software Center.

I would start by purging the program....
```

sudo apt-get purge cairo-dock
```After it has been removed from the system then go to your Ubuntu Software Center and search for Cairo Dock.  Once you have found the program you will click install.  Once the program has been installed then you can run 
```

sudo apt-get update cairo-dock
```

installed it from USC and update it:
> czgirb@czgirb:~$ sudo apt-get update cairo-dock
E: The update command takes no arguments

Any opinion?

---

### Post by newb85 on 2012-11-11
Yeah, that command should be
```
sudo apt-get install cairo-dock
```

---

### Post by czgirb on 2012-11-12
> **newb85 said:**
> Yeah, that command should be
```
sudo apt-get install cairo-dock
```

The Cairo was installed through USC, right?
Why I should:
```
sudo apt-get install cairo-dock
```
again?

---

### Post by newb85 on 2012-11-12
That will ensure CD is at the latest version available from the sources you have enabled.

---

### Post by daslinkard on 2012-11-12
Did Newb85's suggestion work for you?

---

### Post by NewAmercnClasic on 2012-11-13
Depending on video card drivers/ hardware I have had luck resolving Cairo issues switching to non openGL mode.

---

### Post by czgirb on 2012-11-13
> **daslinkard said:**
> Did Newb85's suggestion work for you?

Yup! It installed ... worked ... and now, the problem left is:
When I minimized the opened window, it will be minimized to dock as a **bright-white spot** mark. How can I modified it to be a **small window** ... instead as a **bright-white spot**.
Cos when I minimized the firefox, both **main** and** download** window ... it will be minimized in a **two bright-white spot**. So, I do not know which one is.

---

### Post by fabounet on 2012-11-16
Do you have the same problem without OpenGL ?
Anyway, this is the option to show a thumbnail of the window when it's maximised.
It seems to not work in this case, so you can turn it off in the advanced config window (section 'Taskbar').
By the way, is you scroll on the firefox icon in the main dock, it will switch between the different windows of Firefox, which is quite convenient to quickly switch between windows of a same appli ;-)

---

