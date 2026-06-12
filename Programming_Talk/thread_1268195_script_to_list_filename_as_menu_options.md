---
title: "script to list filename as menu options"
date: 2009-09-16
forum: Programming Talk
---

### Post by terry_gardener on 2009-09-16
wonder if this is possible. 

i have install championship manager 2010 via wine but you have to load saved games with the cm2010.exe to load the files as if you dont it goes straight into create new game. 

i have written script to display menu i have manually entered the filenames, actually i have edited another script created for hellanzb install. 

is there a way to automate this... 

so what i want it to do is search the saved games folder and list the filenames as options and add new options if needed.

and then add the command at the bottom with the filename. 

i have attached the script with the filenames entered manually. 

thanks

---

### Post by terry_gardener on 2009-09-16
forgot to attach file 

here it is.

---

### Post by spupy on 2009-09-17
If it can help you, I wrote a small python utility that creates menus from the command line. As arguments you specify any number of tuples with text for the label and the command to be executed (and an optional gtk stock icon), and the menu is created from these arguments and displayed.

---

### Post by geirha on 2009-09-17
Easiest way I can think of would be something like this:
```

#!/bin/bash
cd "/home/terry/.wine/drive_c/Program Files/Eidos/Championship Manager 2010/CM2010_0/" || exit
select choice in "Save Games"/*.CM2010-SaveGame Exit; do
    [[ $choice = Exit ]] && exit
    [[ $choice = *.CM2010-SaveGame ]] || continue
    exec wine CM2010.exe "$choice"
done

```

Not as colorful as your current script, but shorter :)

Oh, btw. Don't add the .sh extension on a bash script; .sh is for sh-scripts. I recommend not using an extension at all.

---

### Post by terry_gardener on 2009-09-17
thank you for your help. 

the script didn't work at first put i placed a symb link in the CM2010_0 folder to the save games folder and now works.

---

### Post by hungry_pete on 2009-10-02
Apologies that  this is a bit of side issue to this thread, but I'm trying to install Championship Manager 2010 with WINE and I'm running into trouble!

I'm using ubuntu 9.04 and WINE version 1.1.23.

Did you do any tweaks to make sure it installed, or did it just run through the installation without problems for you? Are there any extra components of windows that you have installed through WINE that help this to work?

I'm simply putting in the disc, and launching the 'setup.exe' on the root directory of the CM2010 disc with WINE windows program loader. It then allows me to choose a language, but crashes whilst 'setup is preparing the InstallShield Wizard'.

I've come across suggestions to install .net frameworks 2.0 and 3.0 using winetricks on other forums, but the installation of .net 3.0 fails also.

I'd appreciate any advice you can give me as I'm still relatively a novice when it comes to linux. Thanks in advance!

---

### Post by terry_gardener on 2009-10-04
no it installed ok for however, i stopped the install when it gets to the install directx and .net as these dont install porperly anyway. 
also i copied the d3dx9_36.dll and place into wines system32 folder. 

also you should upgrade to the latest wine version i use wine 1.1.28

hope this helps

---

### Post by hungry_pete on 2009-10-07
Brilliant! The game installed, runs smoothly and a lot better than I anticipated.

Apparently I forgot to redo the WINE repository when I upgraded to jaunty so it wasn't updated to newer versions. I now have 1.1.30 installed and the installation ran very smoothly

Now to have a play with these scripts to sort out the loading a save game issue!

Thanks for your help!

---

