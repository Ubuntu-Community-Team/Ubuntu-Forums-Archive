---
title: "writing a bash install script"
date: 2009-02-23
forum: Programming Talk
---

### Post by miesnerd on 2009-02-23
Hey guys-
Im writing a script (to learn, and to automate the process for myself and my gaggle of ubuntu converts.
I have two issues, i guess.
1. I dont really know how to debug the script. It appears to work, but doesnt.
2. I dont know the best environment for trying out the script. All the programs I want it to install are already on my current setup.

i tried to attach the output, but it said it exceeded the limit.

I'm open to anything. Fire away.

---

### Post by miesnerd on 2009-02-23
in case anyone is weary of downloading the script, I have copied and pasted it in here, for you to view and scrutinize.

#!/bin/bash
if [ $USER != 'root' ]
then
    echo "REQUIRES ROOT"
    exit 0
fi
   OPTIONS="Install Quit"
           select opt in $OPTIONS; do
               if [ "$opt" = "Quit" ]; then
                echo done
                exit

               elif [ "$opt" = "Install" ]; then
                echo OMGEEZEY! Lets do this ****!

###nemo repo
sh -c 'echo deb [http://www.iola.dk/nemo/repo](http://www.iola.dk/nemo/repo) binary/ > /etc/apt/sources.list.d/nemo.list'

###banshee repo
sh -c 'echo deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main'

###begin repo for ubuntu tweak
sh -c 'echo deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) intrepid main'
sh -c 'deb-src [http://ppa.lauchpad.net/tualatrix/ubuntu](http://ppa.lauchpad.net/tualatrix/ubuntu) intrepid main'

###begin mass install section

sudo apt-get update && sudo apt-get install nemo amarok wesnoth-all streamtuner streamripper songbird ubuntu-restricted-extras k3b envyng-gtk win32-codecs libdvdcss2 wine vlc kompozer kopete sysinfo

 ###beign play on linux section
sudo wget [http://deb.mulx.net/playonlinux_hardy.list](http://deb.mulx.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://deb.mulx.net/pol.gpg](http://deb.mulx.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux


    clear
    echo The install was successful. If you want to exit, press 2. Or you can be a retard and mash the keyboard. Note that the restricted extras installs audio/video codecs as well as flash player and Java Runtime Environment 6. See the email to see the description of the files.

               fi
           done
### Other programs that I like : Ultamatix

---

### Post by Subreu9ja on 2010-05-24
Hi,
Am trying to write a script that would also perform installations, but mine would run from a CD. Do have any idea on how i can go about it.

Thanks

---

### Post by Barrucadu on 2010-05-24
Yes. However, you've posted in a thread over one year old&#8212;better to make a new one than resurrect the dead.

Having said that, it would operate very similarly to the OP's script, but would need to do some additional set up such as mounting (possibly even making and formatting) partitions, and then perform all operations relative to the desired partition.

---

