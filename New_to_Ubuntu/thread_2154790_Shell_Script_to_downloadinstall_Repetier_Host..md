---
title: "Shell Script to download/install Repetier Host."
date: 2013-06-15
forum: New to Ubuntu
---

### Post by joeltrane on 2013-06-15
Hello,

My name is joeltrane and I am a new member of this community. Just recently I have been using Ubuntu (as a daily driver).

I am trying to install a Host program for 3D printing called Repetier Host: [Repetier-Host Linux 0.85c]("http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==") It is somewhat difficult to set up and I was hoping to create a shell script that could automate as much of this process as possible.

The requirements to accomplish this (listed below) I fave found here: [http://www.repetier.com/documentation/repetier-host/rh-installation-and-configuration/](http://www.repetier.com/documentation/repetier-host/rh-installation-and-configuration/)
**Linux installation**

 The linux version comes as gzipped tar file. Move it to where you  want your files and unpack its contents and run the post installation  script:
 
tar -xzf repetierHostLinux_0_70b.tgz cd RepetierHost sh configureFirst.sh After that you have a link in /usr/bin to the installation, so you  can start it with repetierHost. Make sure you have all required Mono  libraries installed. If you are in doubt, install Mono develop, which  has all needed libraries as dependency.
 One problem that most linux distributions have is, that the normal  users are not allowed to connect to a serial console. You need to put  your user into the right group. On Debian you can call:
 
usermod -a -G dialout yourUserName to add your user to the group dialout.

[B]
The Shell Script that I have already, is shown below:[/B]

```
#! /bin/bash

sudo apt-get update
sudo apt-get install wget
wget --version

sudo apt-get install mono-complete # add any flags you might need

wget http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw== ## URL of the file you wish to download
tar -xzf repetierHostLinux_0_70b.tgz
cd RepetierHost
sh configureFirst.sh

usermod -a -G dialout $(whoami)
```

I have also attached this as a gedit file.

I am running a version of Ubuntu Studio: Version 4.8 by Xubuntu. My  target audience however, are those running the latest Distro of Ubuntu  12.04 LTS. Would there be any conflicts with the two distros being able to use this script?

I have tried to run this script and it seems I cannot move forward.  It looks as thought the script hangs on something and never actualy  installs anything. Is there anyone out there that can assist me? I am  grateful for any help.

Please let me know if I can be more clear or provide you with additional information that I had not considered. I will be happy to do as much as I am able to help as well.

Best regards,
Joeltrane

P.S. If it matters or if anyone was curious, I am trying to use this with a Solidoodle 3D printer. I am unsure if this is irrelevant or not.

---

### Post by joeltrane on 2013-06-15
Hello,

I realized that this information might be useful as well: [Solidoodle On Linux]("http://wiki.solidoodle.com/linux")

---

### Post by steeldriver on 2013-06-15
Hello and welcome to the forum

The url that you specified in your wget command appears to download repetierHostLinux_**0_85c**.tgz so your 'tar -xvf repetierHostLinux_0_70b.tgz' command will fail - if you are distributing this script you will need to handle whatever version number is returned by the link rather than hardcoding it

Also the usermod command will likely need to be run with 'sudo' as well - in fact it would be better (imho) to remove the 'sudo' everywhere inside the script and instead run the whole script as 'sudo'

Hope this helps

---

### Post by joeltrane on 2013-06-16
steeldriver,

I have made the changes to correct the file version as you had mentioned. I am not sure how to run the entire script as super user. Do I just put something like this at the beginning:

```


#! /bin/bash 
sudo su

Everything else?

```

As far as this is concerned:

> you will need to handle whatever version number is returned by the link rather than hardcoding it

I am not sure where to begin with this. I apologize for my ignorance everyone. I am just not sure how to specify the version number rather then hardcoding it.

Where should I be looking in order to find this? I can only see the same link to download it.

Thank you for any and all responses

- Joeltrane

---

### Post by MidnightGrey on 2013-06-16
> **joeltrane said:**
> steeldriver,

I have made the changes to correct the file version as you had mentioned. I am not sure how to run the entire script as super user. Do I just put something like this at the beginning:

```


#! /bin/bash 
sudo su

Everything else?

``` 

What steeldriver meant was to remove all 'sudo' from your script, and ask the person running the script to run as administrator, ie; if the script was called MyScriptNoAdmin.sh, they would call:
```
 sudo ./MyScriptNoAdmin.sh 
```

---

> 
[quote]you will need to handle whatever version number is returned by the link rather than hardcoding it

I am not sure where to begin with this. I apologize for my ignorance everyone. I am just not sure how to specify the version number rather then hardcoding it.

- Joeltrane[/QUOTE]

A quick look at the website suggest that the links themselfs are static so even if they release a new version, you would have to manually edit the wget url.
Simply modifying your original script to the new version would fix it.

---

### Post by steeldriver on 2013-06-16
Yes it looks like the URL is a php redirector, so you will likely need to change that anytime the maintainer changes the version / webpage, however you're probably going to need to rename the file anyway (the wget -O option - that's an 'oh' not a 'zero'), so you can choose a version-independent name e.g.

```
wget **-O repetierHostLinux.tgz** 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw=='
```

or using the long form

```
wget **--output-document=repetierHostLinux.tgz** 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw=='
```

Then you can just do

```
tar -xvf repetierHostLinux.tgz
```

If you want to get fancy, you could try piping the wget straight to tar so you don't even care what the filename is (note that in this case you will need to tell tar explicitly that it is in gzip format using the 'z' option, since it won't have a filename extension to go by)

```
wget **-O-** 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==' | tar x**z**vf **-**
```

---

### Post by prodigy_ on 2013-06-16
> **steeldriver said:**
> Also the usermod command will likely need to be run with 'sudo' as well - in fact it would be better (imho) to remove the 'sudo' everywhere inside the script and instead run the whole script as 'sudo'
It's worth noting that **$(whoami)** will return "root" when run with sudo. To get the name of the logged on user you need something like ```
$(who -m | cut -d' ' -f 1)
```

---

### Post by Cheesemill on 2013-06-16
Instead of getting the name of the user you can check the user id, this will be 0 for root.
You can then use something like this at the beginning of your script...
```
#!/bin/sh

if [ $(id -u) != 0 ]
  then echo "This script must be run with root privileges. Please launch it using...\nsudo ./scriptname.sh"
  exit
fi

## Continue with rest of script here.
echo "Rest of script"
```

```
$ ./root_check.sh
This script must be run with root privileges. Please launch it using...
sudo ./scriptname.sh

$ sudo ./root_check.sh
Rest of script

```

---

### Post by joeltrane on 2013-06-16
Hello friends,

I have made some adjustments. Thank you steeldriver your advice

```

wget **-O-** 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==' | tar x**z**vf **-**
```

This was deffinately what I was looking for, this is way more streamlined then before. I have actually seen tar > | xzvf - before but was not entirely sure how it functioned, thank you for being an excellent teacher!

Also, thank you prodigy_, you just saved me a lot of confusion later on. I presume that if we left it the way I had it, some poor soul wouldnt be able to install it because they didnt have access to root user.

cheesemill, thank you for that advice however I have still not had any success downloading repetier host with my script yet any way.

If anyone can take a look and let me know if they see why the download won't work I would be greatful for any advice.

Thanks everyone,

Joeltrane


```
#! /bin/bash

sudo apt-get update
sudo apt-get install wget
wget --version

sudo apt-get install mono-complete # add any flags you might need

wget -O- 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==' | tar xzvf -
cd RepetierHost
sh configureFirst.sh

usermod -a -G dialout $(who -m | cut -d' ' -f 1)
```

---

### Post by steeldriver on 2013-06-16
how are you running the script? what part doesn't work exactly? can you post any error messages?

---

### Post by joeltrane on 2013-06-17
steeldriver,

I made a newbie mistake and tried to run it in the terminal from the wrong directory.

Never the less I got to the completeion of the mono install and after the script ran, I saw no repetier host.

I suspect that 
```

$(who -m | cut -d' ' -f 1)
```

Is responsible.


Do you have any thoughts? atleast it is starting to make some magic happen! Very excited! :-) Thanks for everyones help so far! I am learning so much.

- Joeltrane

---

### Post by steeldriver on 2013-06-17
Well you should get a downloaded / untarred RepetierHost directory regardless of whether the usermod command (or the 'who' command inside it) worked - you should also get a list of all the files that are being extracted from the tar archive scrolling through the terminal - did you see that?

However maybe I was wrong to suggest moving the sudos out of the script since it does complicate the usermod. So how about taking a step back to

```

#! /bin/bash

sudo apt-get update
sudo apt-get install wget
wget --version

sudo apt-get install mono-complete # add any flags you might need

[COLOR=#0000ff]wget -O- 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==' | tar xzvf -
[/COLOR]cd RepetierHost
[COLOR=#0000ff]sudo[/COLOR] [COLOR=#0000ff]./[/COLOR]configureFirst.sh

[COLOR=#0000ff]sudo [/COLOR]usermod -a -G dialout $(whoami)

```

Note that I changed [COLOR=#0000ff]sh configureFirst.sh[/COLOR] to [COLOR=#0000ff]./configureFirst.sh[/COLOR] - you shouldn't second guess the appropriate shell interpreter for a script (in particular, sh on Ubuntu links to a dash shell, which doesn't support all of the syntax of the bash shell)

Also note that this requires the user you're trying to add to 'dialout' already be a member of 'sudo' - if they're not, you'll need to manually add them first (in which case you may as well manually add them to 'dialout' instead)

Hope this helps

---

### Post by MidnightGrey on 2013-06-17
Hey i did some poking around in this earlier but didnt have time to post.
Not that it matters much but the install instructions ask for mono development package only,
so you can change
```
sudo apt-get install mono-complete
```
to
```
sudo apt-get install mono-devel
``` if you like.

Again it doesnt make much of a difference as mono-complete comes with mono-devel anyways.

---

### Post by joeltrane on 2013-06-18
Hello everyone,

\\:D/**-- I have resolved the issue --**\\:D/

First let me thank everyone for your help, without you this wouldnt have been possible. ):P

I first discovered at which point things were going awry when looking through my terminal. I saw that repetier and slicer were registering as downloading and attempting to install. Eventually I stumbled upon this:
```
RepetierHost/Slic3r/var/spool.png
RepetierHost/Slic3r/var/time.png
RepetierHost/Slic3r/var/wrench.png
RepetierHost/version.txt
Installing slic3r source version
Configuration finished.
Make sure, your user has permission to connect to the serial port.
For debian and clones use:
usermod -a -G dialout yourUserName
IMPORTANT: The host works natively with the source version for linux.
Check https://github.com/alexrj/Slic3r/wiki/Running-Slic3r-from-git-on-GNU-Linux
on how to resolve all dependencies. You can omit the 'Get slic3r' section.

Debian/Ubuntu like linux detected. You can try to
install needed software automatically. You can do this any time later
by running installDependenciesDebian.
Shall I try to install required modules [y/n]?^C
```

So I discovered that there were dependencies issues and went to the github page.

After that, I implemented all of the recommendations that the author had made:
```

# Install dependencies through the package manager
sudo apt-get install git build-essential libgtk2.0-dev libwxgtk2.8-dev libwx-perl libmodule-build-perl libnet-dbus-perl
sudo apt-get install cpanminus

sudo apt-get install curl # There is a fair chance that your distribution will not have the cpanminus package
curl -L http://cpanmin.us | sudo perl - --sudo App::cpanminus

git clone https://github.com/alexrj/Slic3r.git # Get Slic3r
cd Slic3r

sudo cpanm Boost::Geometry::Utils Math::Clipper \ # This is the command to install all of the dependencies through cpanm
    Math::ConvexHull Math::ConvexHull::MonotoneChain Math::Geometry::Voronoi Math::PlanePath Moo Wx XML::SAX
```

and made the revision to mono as suggested by MidnightGrey, thank you! I realized that adding a bunch of bloated and uneeded software is probably considered rude. Not to mention it takes way longer to finish installing.

The Whole thing ended up looking like this:

```
#! /bin/bash

sudo apt-get update
sudo apt-get install wget
wget --version

sudo apt-get install mono-devel # add any flags you might need

# Install dependencies through the package manager
sudo apt-get install git build-essential libgtk2.0-dev libwxgtk2.8-dev libwx-perl libmodule-build-perl libnet-dbus-perl
sudo apt-get install cpanminus

sudo apt-get install curl # There is a fair chance that your distribution will not have the cpanminus package
curl -L http://cpanmin.us | sudo perl - --sudo App::cpanminus

git clone https://github.com/alexrj/Slic3r.git # Get Slic3r
cd Slic3r

sudo cpanm Boost::Geometry::Utils Math::Clipper \ # This is the command to install all of the dependencies through cpanm
    Math::ConvexHull Math::ConvexHull::MonotoneChain Math::Geometry::Voronoi Math::PlanePath Moo Wx XML::SAX

wget -O- 'http://www.repetier.com/?wpdmact=process&did=MzUuaG90bGluaw==' | tar xzvf -
cd RepetierHost
sudo ./configureFirst.sh

sudo usermod -a -G dialout $(whoami)
```


Then I made a second script so anyone could place the script in their directory of choice (in my case, the Desktop) and simply double click it with the mouse to launch Repetier Host.

```

#!/bin/sh
cd /home/$(whoami)/Desktop/Slic3r/RepetierHost
mono RepetierHost.exe -home /home/$(whoami)/Desktop/Slic3r/RepetierHost&

```

Now I can try connecting with a printer.

One question, would: "wget --version" work because I must already have wget installed or is that the valid command to get the latest version?

Thanks again everyone! You folks literally took me from the ground up so far in learning about shell scripting!

-- Joeltrane

---

### Post by flickerfly on 2013-09-29
When I was new to shell scripting, I loved it when people came through and suggested improvement to my code. Here is a revised version with lots of checks and stuff added. It also takes care of some things that I don't think were required or could be done in ways that would be easier to maintain in the future (such as using apt-get for as much as possible. I also added the 3D dependencies; libxmu-dev, freeglut3-dev. I've tested the script to make sure it runs without problems, but I haven't yet tested the software much so please let me know if I missed a depend or something.

I also checked to be sure Slic3r wasn't already downloaded since that can be the biggest download. You can easily change versions of the software in the dlslic3r and dlrephost variables.

```
#! /bin/bash

# Directory:
# You may want to be sure to run this in the directory you want everything to 
# fall into. I used '~/bin'

# Objective:
# My objective is to handle as much within the apt-get and installer scripts of 
# the softwares as possible targetting Ubuntu 13.04 or newer

#Check for newer versions of slic3r here: http://dl.slic3r.org/linux/ 
#I'm linking the 64-bit, you may want the 32-bit
dlslic3r='http://dl.slic3r.org/linux/slic3r-linux-x86_64-0-9-10b.tar.gz'

#Check for newer versions of Repetier Host here: http://www.repetier.com/download/
#I'm linking 0.90D
dlrephost='http://www.repetier.com/?wpdmact=process&did=NDAuaG90bGluaw=='

# Install all the dependencies (an update shouldn't be required). 
# Includes the 3D preview depends (libxmu-dev freeglut3-dev)
# If root, don't bother with sudo
if [ "$(id -u)" != "0" ]; then
  sudo apt-get -y install wget mono-devel git build-essential libgtk2.0-dev libwxgtk2.8-dev libwx-perl libmodule-build-perl libnet-dbus-perl libxmu-dev freeglut3-dev
else
  apt-get -y install wget mono-devel git build-essential libgtk2.0-dev libwxgtk2.8-dev libwx-perl libmodule-build-perl libnet-dbus-perl libxmu-dev freeglut3-dev
fi

# Get Slic3r if you haven't already
if [ ! -f ${dlslic3r##*/} ]; then
  wget $dlslic3r
fi
tar zxvf echo ${dlslic3r##*/}

# The Repetier installer will get the required module for you (just say "y" when it asks)

#I don't worry about downloading it multiple times, it is small and the download isn't easily parsed
wget -O- $dlrephost | tar xzvf -
cd RepetierHost

# Run the Repetier config
# Must be run with root permissions

echo '--->We are about to configure Repetier Host. If this is your first time, please say "Yes" when it asks you if you "Shall I try to install required modules?".'
read -p "Press Enter to continue" yn

if [ "$(id -u)" != "0" ]; then
  sudo ./configureFirst.sh
  username=`whoami`
else
  ./configureFirst.sh
  username=`whoami`
fi

# Make sure current user has dialout group access

echo "Checking if you are in the dialout group."
if [ ! `grep ${username} /etc/group|grep -c dialout` ]; then
  echo "Adding user ${username} to the dialout group."
  if [ "$(id -u)" != "0" ]; then
    sudo adduser $username dialout
  else
    adduser $username dialout
  fi
fi
```

---

### Post by flickerfly on 2013-09-29
Another little tidbit for you guys, you can create an .desktop file to put on your desktop that will run the repetierHost including a pretty logo! :-)

You'll need to change USERNAME to your username as those files aren't smart enough to deal with ~ and I'm not actually scripting this. If there is some interest, it could be added to the script above pretty easily from this code.

```
wget -O ~/bin/RepetierHost/RepetierLogo.png [http://reprap.org/mediawiki/images/2/27/Repetier-logo-v.0.29.png](http://reprap.org/mediawiki/images/2/27/Repetier-logo-v.0.29.png)
echo "[Desktop Entry]
Name=Repetier
Exec=mono RepetierHost.exe -home ~/bin/RepetierHost&
Type=Application
StartupNotify=true
Comment=Repetier
Path=/home/USERNAME/bin/RepetierHost/
Icon=/home/USERNAME/bin/RepetierHost/RepetierLogo.png
Comment[en_US.UTF-8]=Repetier Host
Name[en_US]=Repetier
" >> ~/Desktop/Repetier.desktop
chmod +x ~/Desktop/Repetier.desktop
```

---

### Post by flickerfly on 2014-08-30
For those wanting to use the script with the 1.03 version of RepetierHost, replace line 18 that sets the dlrephost variable with the following.

dlrephost='http://www.repetier.com/?wpdmact=process&did=NDQuaG90bGluaw=='

The new version now includes a Repetrie-Host.desktop file so you no longer need that script, but you will want to move it out of the RepetierHost directory to ~/Desktop or somewhere useful.

I tested it on 14.04 briefly, but haven't done more than just be sure it will start up.

---

