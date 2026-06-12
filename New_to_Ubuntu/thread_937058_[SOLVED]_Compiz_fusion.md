---
title: "[SOLVED] Compiz fusion"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by LeeHamo on 2008-10-03
Hi,

I want to install compiz fusion from add/remove so I managed to find compiz fusion tray in there but when I attempt to it gives me a load of warnings and stuff about potentially harmful software (cant remember exact warnings) but I want to use it cause i have been to this recommended website [http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/](http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/)
and i want to try it, i have added the link from there to the repositories for updating compiz but I dont know whether I should download it cause of the warnings.

Is it ok to download?

Im worried.

---

### Post by oldos2er on 2008-10-03
Which version of Ubuntu are you using?

---

### Post by nothingspecial on 2008-10-03
```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

If it was that you added to your sources list then no worries. The warnings are just because it`s not an official Ubuntu repository.

---

### Post by LeeHamo on 2008-10-03
I am using 8.04, the warnings didnt come from synaptic they came from add/remove when I selected to install compiz fuzion ill try and post a screenshot.  Aparently after I install compiz it will pop up an updte is available because of that string i put into synaptic.

---

### Post by mick222 on 2008-10-03
I'd use the version in hardy to start with ,you'll get the desktop cube expo and lots of stuff to play with before trying to upgrade. synaptic has simple compizconfig settings manager giving easy access to effects.Emerald is also good for decorating windows .

---

### Post by LeeHamo on 2008-10-03
> **mick222 said:**
> I'd use the version in hardy to start with ,you'll get the desktop cube expo and lots of stuff to play with before trying to upgrade. synaptic has simple compizconfig settings manager giving easy access to effects.Emerald is also good for decorating windows .

Where do I find the version in hardy? (hardy is hardy heron ie 8.04) am I right?

How do I try to upgrade?

Whats the compizconfig thing?

Sorry for my lack of knowledge.

---

### Post by nothingspecial on 2008-10-03
> **mick222 said:**
> I'd use the version in hardy to start with ,you'll get the desktop cube expo and lots of stuff to play with before trying to upgrade. synaptic has simple compizconfig settings manager giving easy access to effects.Emerald is also good for decorating windows .

Good advice. But like I said, there are some apps you might want to try later on that aren`t in official Ubuntu repositories. As long as it`s from a trusted source you will be fine.
 For example I run some streaming software that is specific to my streaming hardware. The software is not in the official Ubuntu repositories. The people who maintain that software have made a Repository for Ubuntu users but it warns me every time I get an update.
 If you are worried then remove that software source. 
All I`m saying is as long as you check (here would be a good place) you will be fine.

---

### Post by nothingspecial on 2008-10-03
> **LeeHamo said:**
> Where do I find the version in hardy? (hardy is hardy heron ie 8.04) am I right?

How do I try to upgrade?

Whats the compizconfig thing?

Sorry for my lack of knowledge.
 You`ve already got it. 
In your menus go to system > preferences > appearance.
Where it says visual effects check custom. Compiz fusion is now on.

---

### Post by howefield on 2008-10-03
Compiz is installed by default during the hardy install, to play with the various options, you can install compizconfig-settings-manager.

Install via Synaptic Package Manager, or type the following into a terminal

```
sudo apt-get install compizconfig-settings-manager
```

That will give you Advanced Desktop Effects Settings options in your System > Preferences menu.

---

### Post by LeeHamo on 2008-10-03
Ok ill forget about installing it and delete that string out of repositories, but where do i find the version in hardy as mentioned above.

We posted at same time thanks for the info d/l compiz config now.

---

### Post by nothingspecial on 2008-10-03
Sorry open system > preferences > synaptic package manager and searc for compiz look for compiz-config-settings manager and check it for installation.

---

### Post by oldos2er on 2008-10-03
Install the package compizconfig-settings-manager. Another useful one is fusion-icon, which simply places an icon in your panel for compiz settings.

---

### Post by bhadotia on 2008-10-03
[Here]("http://linuxowns.wordpress.com/2008/06/16/guide-to-customizing-ubuntus-look-and-feel/")is a good guide. Also contains info on compiz.

---

### Post by LeeHamo on 2008-10-03
Hi,

Thanks for all the info, ive sorted it all now.  Got the desktop cube working and im happy.

Lee.

---

### Post by bhadotia on 2008-10-03
> **LeeHamo said:**
> Hi,

Thanks for all the info, ive sorted it all now.  Got the desktop cube working and im happy.

Lee.

Great!
Please mark your thread as solved. The option is under 'Thread Tools' on the top right corner.:popcorn:

---

