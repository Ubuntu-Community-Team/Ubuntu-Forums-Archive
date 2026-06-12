---
title: "Uninstall program besides using apt-get and dpkg"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by MGrowl on 2015-07-16
We usually install programs from the software center, or through the CLI with apt-get, but what about the packages that aren't supported? I installed a program, downloaded it's tar files and ran a script within, "*.install". *I know usually all you need to do is *"sudo make uninstall" *and it should remove the programs files. My problem is, the program I installed was already compiled, and I just ran the included *install*-script with the downloaded files. Now I want to uninstall it, how would I go about doing that? 

I've researched the answer and can't find a solution. Some would say to go to the software center, or the CLI with *"sudo apt-get remove/purge" *or "*dpkg -r program_name". *As I said earlier, I didn't use any repositories to install it, so the above commands do not work, and unfortunately there is no "*uninstall script" *included. 

What are my options in removing the program? Do I have to parse the install script and rm the directories/files used for the program? I'm actually trying to avoid this since I might miss some of it's files. Is there any other way to uninstall?



Btw, the program is packet tracer, downloaded through its official Cisco site. And yes, I've contacted their customer support, and they too couldn't give a proper solution. 


Here is the script I used for reference. 

```
#!/bin/bash

# Thanks to Felix Wolf (felix@bar.bz) for providing this install script.
# Thanks to Paul Fedele for providing script to check/download 32-bit library on a 64-bit machine
initInstall ()
{
echo
echo Welcome to Cisco Packet Tracer 6.2 Installation
echo
echo Read the following End User License Agreement \"EULA\" carefully. You must accept the terms of this EULA to install and use Cisco Packet Tracer.
echo "Press the Enter key to read the EULA."
echo
read cont
more eula.txt
echo "Do you accept the terms of the EULA? (Y)es/(N)o"
echo
read input    
case "$input" in
yes|YES|Yes|Y|y)
(installer);;
esac
exit 0
}

installer ()
{
SDIR=`dirname $_`
ARCHITECTURE=$(uname -m)
INSTALL_32BIT_LIBRARY=false

echo "You have accepted the terms to the EULA. Congratulations. Packet Tracer will now be installed."
read -p "Enter location to install Cisco Packet Tracer or press enter for default [/opt/pt]: " IDIR

if [ -z $IDIR ]; then
    IDIR="/opt/pt"
fi

if [ $ARCHITECTURE = "x86_64" ]; then    
    DEPENDS=$(dpkg -l | grep  yelp | tail -n 1 | cut -c1)
    if [ $DEPENDS = "i" ]; then
        TESTCONNECTION=`wget --tries=3 --timeout=15 www.cisco.com -O /tmp/testinternet &>/dev/null 2>&1`
        if [ $? != 0 ]; then
            echo -"You are not connected to the Internet. Please check your Internet connection and try again."; exit 0
        else
            INSTALL_32BIT_LIBRARY=true
        fi
    fi
fi

if [ -e $IDIR ]; then
    read -p "It appears that Packet Tracer is already installed.  Do you wish to replace it? [Yn] " NEEDREPLACE
    if [ "$NEEDREPLACE" = "y" ] || [ "$NEEDREPLACE" = "Y" ] || [ -z $NEEDREPLACE ]; then
        sudo rm -rf $IDIR
    else
        echo "Program Terminated"; exit 0
    fi
fi

QIDIR=${IDIR//\//\\\\\/}

echo Installing into $IDIR

if mkdir $IDIR > /dev/null 2>&1; then
    if cp -r $SDIR/* $IDIR; then
        echo Copied all files successfully to $IDIR
    fi
    
    sh -c "sed s/III/$QIDIR/ $SDIR/tpl.packettracer > $IDIR/packettracer"
    chmod a+x $IDIR/packettracer
    sh -c "sed s/III/$QIDIR/ $SDIR/tpl.linguist > $IDIR/linguist"
    chmod a+x $IDIR/linguist


    if touch /usr/share/applications/pt6.desktop > /dev/null 2>&1; then
        echo -e "[Desktop Entry]\nExec=PacketTracer6\nIcon=pt6\nType=Application\nTerminal=false\nName=Packet Tracer 6.2" | tee /usr/share/applications/pt6.desktop > /dev/null
        rm -f /usr/share/icons/hicolor/48x48/apps/pt6.png
        gtk-update-icon-cache -f -q /usr/share/icons/hicolor
        sleep 10
        cp $SDIR/art/app_student.png /usr/share/icons/hicolor/48x48/apps/pt6.png
        gtk-update-icon-cache -f -q /usr/share/icons/hicolor
    fi

    if [ "$INSTALL_32BIT_LIBRARY" = true ]; then
        echo "Installing 32 bit libraries for Packet Tracer."
        dpkg --add-architecture i386
        apt-get -y install lib32z1
        apt-get -y install lib32ncurses5
        apt-get -y install lib32bz2-1.0
        apt-get -y install libgcc1:i386
        apt-get -y install libstdc++6:i386
        apt-get -y install libssl-dev:i386
        apt-get -y install libqtwebkit4:i386
        apt-get -y install libqt4-scripttools:i386
    fi
else
    echo
    echo Not able to create and copy files to $IDIR
    read -p "Should we try to gain root access with sudo? [Yn] " QSD
    if [ "$QSD" = "y" ] || [ "$QSD" = "Y" ] || [ -z $QSD ]; then
        if sudo mkdir $IDIR; then
            echo Installing into $IDIR
            if sudo cp -r $SDIR/* $IDIR; then
                echo Copied all files successfully to $IDIR
            else
                echo
                echo Not able to copy files to $IDIR
                echo Exiting installation
                exit
            fi
            sudo sh -c "sed s/III/$QIDIR/ $SDIR/tpl.packettracer > $IDIR/packettracer"
            sudo chmod a+x $IDIR/packettracer
            sudo sh -c "sed s/III/$QIDIR/ $SDIR/tpl.linguist > $IDIR/linguist"
            sudo chmod a+x $IDIR/linguist

            if sudo touch /usr/share/applications/pt6.desktop; then
                echo -e "[Desktop Entry]\nExec=PacketTracer6\nIcon=pt6\nType=Application\nTerminal=false\nName=Packet Tracer 6.2" | sudo tee /usr/share/applications/pt6.desktop > /dev/null
                sudo rm -f /usr/share/icons/hicolor/48x48/apps/pt6.png
                sudo gtk-update-icon-cache -f -q /usr/share/icons/hicolor
                sleep 10
                sudo cp $SDIR/art/app_student.png /usr/share/icons/hicolor/48x48/apps/pt6.png
                sudo gtk-update-icon-cache -f -q /usr/share/icons/hicolor
            fi

            if [ "$INSTALL_32BIT_LIBRARY" = true ]; then
                echo "Installing 32 bit libraries for Packet Tracer."
                sudo dpkg --add-architecture i386
                sudo apt-get -y install lib32z1
                sudo apt-get -y install lib32ncurses5
                sudo apt-get -y install lib32bz2-1.0
                sudo apt-get -y install libgcc1:i386
                sudo apt-get -y install libstdc++6:i386
                sudo apt-get -y install libssl-dev:i386
                sudo apt-get -y install libqtwebkit4:i386
                sudo apt-get -y install libqt4-scripttools:i386
            fi
        else
            echo
            echo Not able to gain root access with sudo
            echo Exiting installation
            exit
        fi
    else
        echo
        echo Exiting installation
        exit
    fi
fi



echo
echo 
read -p "Should we create a symbolic link \"packettracer\" in /usr/local/bin for easy Cisco Packet Tracer startup? [Yn] " QC
if [ "$QC" = "y" ] || [ "$QC" = "Y" ] || [ -z $QC ]; then
    if [ "$user" != "root" ]; then
        sudo ln -sf $IDIR/packettracer /usr/local/bin
    else 
        ln -sf $IDIR/packettracer /usr/local/bin
    fi
    echo "Type \"packettracer\" in a terminal to start Cisco Packet Tracer"
else
    echo "Type \"$IDIR/packettracer\" in a terminal to start Cisco Packet Tracer"
fi

# add the environment var PT5HOME
sudo sh set_ptenv.sh $IDIR

echo
echo Cisco Packet Tracer 6.2 installed successfully
}
initInstall
exit 0


```

---

### Post by grahammechanical on 2015-07-16
I am not very good with scripts but a quick glance through that script shows that it is using apt-get to install libraries. So, you can use apt-get to remove them. Better still install Sysnaptic Package manager and use that and you will see what other applications depend on those packages and will also be removed at the same time.

The script also installs some icons and creates a couple of folders and a symbolic link.

Regards.

---

### Post by Habitual on 2015-07-16
There's some interesting stuff in the script I notice:
It assumes you don't have i386 architecture support stuff installed, (if you have installed Skype, you already have this support)
```
INSTALL_32BIT_LIBRARY=false
``` It then tests the internet connect to install this support:
```
TESTCONNECTION
    INSTALL_32BIT_LIBRARY=true
...
dpkg --add-architecture i386
apt-get -y install lib32z1
apt-get -y install lib32ncurses5
apt-get -y install lib32bz2-1.0
apt-get -y install libgcc1:i386
apt-get -y install libstdc++6:i386
apt-get -y install libssl-dev:i386
apt-get -y install libqtwebkit4:i386
apt-get -y install libqt4-scripttools:i386
```

The other files only seem to be the desktop entry at /usr/share/applications/pt6.desktop and a png probably for the same entry at 
/usr/share/icons/hicolor/48x48/apps/pt6.png

Have a look in /opt/pt

---

### Post by MGrowl on 2015-07-17
Thanks for the replies. This means my options are down to having to *"rm"  *the files right?

---

### Post by Habitual on 2015-07-17
> **MGrowl said:**
> Thanks for the replies. This means my options are down to having to *"rm"  *the files right?
I'd 
```
sudo rm -fr /opt/pt/ /usr/share/applications/pt6.desktop /usr/share/icons/hicolor/48x48/apps/pt6.png
``` and call it 'done'.

---

