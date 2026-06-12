---
title: "Newbie Questions"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by kturcotte on 2012-10-19
I'm trying to install Nvidia drivers and Crashplan on ubuntu 12.10. I've downloaded them, but when I open the install files, all I get are text files. This is what I get for Crashplan:
"Welcome to CrashPlan for Linux!
------------------------------------------------------------------------

To install CrashPlan run the installer in this directory:

./install.sh

and follow the instructions.


To uninstall CrashPlan run the uninstaller in this directory with
the path that you installed CrashPlan to:

./uninstall.sh /usr/local/crashplan

When uninstalling CrashPlan, you will have the option of removing the
application, but preserving the backup data you are storing for others
for use by a future installation of CrashPlan.  Please read uninstall
instructions carefully when running the script above."

When I try to open install.sh, I just get anoterh text file that says:
"
# copy the desktop launcher into place
if [ -d "/home/${SRC_USER}/Desktop" ] ; then
    DESKTOP_LAUNCHER="/home/${SRC_USER}/Desktop/${APP_BASENAME}.desktop"
    
    # which icon are we using? custom if it exists
    DESKTOP_ICON_PATH=${TARGETDIR}/skin/icon_app_128x128.png
    if [ -f ${TARGETDIR}/skin/custom/icon_app_64x64.png ] ; then
        DESKTOP_ICON_PATH=${TARGETDIR}/skin/custom/icon_app_64x64.png
    fi
    if [ -f ${TARGETDIR}/skin/custom/icon_app_128x128.png ] ; then
        DESKTOP_ICON_PATH=${TARGETDIR}/skin/custom/icon_app_128x128.png
    fi
    
    # use 'su' only if we're operating as root
    if [ "${USERNAME}" == "root" ] ; then
        su ${SRC_USER} -c "cp scripts/${APP_BASENAME}.desktop ${DESKTOP_LAUNCHER}"
        su ${SRC_USER} -c "chmod +x ${DESKTOP_LAUNCHER}"
        su ${SRC_USER} -c "sed -imod \"s|Exec=.*|Exec=${GUISCRIPT}|\"  ${DESKTOP_LAUNCHER} && rm -rf ${DESKTOP_LAUNCHER}mod"
        su ${SRC_USER} -c "sed -imod  \"s|Icon=.*|Icon=${DESKTOP_ICON_PATH}|\" ${DESKTOP_LAUNCHER} &&  rm -rf ${DESKTOP_LAUNCHER}mod"
    else
        cp scripts/${APP_BASENAME}.desktop ${DESKTOP_LAUNCHER}
        chmod +x ${DESKTOP_LAUNCHER}
        sed -imod "s|Exec=.*|Exec=${GUISCRIPT}|" ${DESKTOP_LAUNCHER} && rm -rf ${DESKTOP_LAUNCHER}mod
        sed -imod "s|Icon=.*|Icon=${DESKTOP_ICON_PATH}|" ${DESKTOP_LAUNCHER} && rm -rf ${DESKTOP_LAUNCHER}mod
    fi
fi

# Check for max_user_watches and suggest updating if necessary.  Many distros use 8192 by default
# so we use this value as a baseline.
INOTIFY_WATCHES=`cat /proc/sys/fs/inotify/max_user_watches`
if [[ $INOTIFY_WATCHES -le 8192 ]]; then
  echo ""
  echo "Your Linux system is currently configured to watch $INOTIFY_WATCHES files in real time."
  echo "We recommend using a larger value; see the CrashPlan support site for details"
  echo ""
fi

# Start the servce
${INITSCRIPT} start

# call out the "service has been started" by creating a pause
echo ""
echo "${APP_BASENAME} has been installed and the Service has been started automatically."
echo ""
echo -n "Press Enter to complete installation. "
read ENTER

echo ""
echo "Important directories:"
echo "  Installation:"
echo "    ${TARGETDIR}"
echo "  Logs:"
echo "    ${TARGETDIR}/log"
echo "  Default archive location:"
echo "    ${MANIFESTDIR}"

# if we installed as root make sure they see 'sudo' in front of the Engine start
SUDO_PREFIX="sudo "
if [ "${USERNAME}" != "root" ] ; then
    SUDO_PREFIX=""
fi
echo ""
echo "Start Scripts:"
echo "  ${SUDO_PREFIX}${INITSCRIPT} start|stop"
echo "  ${GUISCRIPT}"

echo ""
echo "You can run the ${APP_BASENAME} Desktop UI locally as your own user or connect"
echo "a remote Desktop UI to this Service via port-forwarding and manage it"
echo "remotely. Instructions for remote management are in the readme files"
echo "placed in your installation directory:"
echo "  ${TARGETDIR}/doc"
echo ""
if [ "x${DISPLAY}" != "x" ] ; then
    echo -n "Would you like to start ${APP_BASENAME}Desktop? (y/n) [y] "
    read reply
    if [ "x${reply}" == "x" ] ; then
        reply=y
    fi
    case ${reply} in
        [yY] | [yY][eE][sS])
            # use 'su' only if we're operating as root
            if [ "${USERNAME}" == "root" ] ; then
                su ${SRC_USER} -c "${GUISCRIPT}"
            else
                ${GUISCRIPT}
            fi
            ;;
    esac
fi

echo ""
echo "To start the Desktop UI:"
if [ "x${BINSDIR}" != "x" ] ; then
    echo "  ${BINSDIR}/${APP_BASENAME}Desktop"
else
echo "  ${GUISCRIPT}"
fi

echo ""
echo "Installation is complete. Thank you for installing ${APP_BASENAME} for Linux."
echo """

There is a large (19.3 MB) file called CrashPlan_3.2.1.cpi However, it seems to think this is a video file. What do I do?

---

### Post by Metaxa on 2012-10-19
Have you right clicked on the installer,

Properties -> Permissions

and check if " Allow executing this file as program "?


Start with that.



Metaxa

---

### Post by kturcotte on 2012-10-19
> **Metaxa said:**
> Have you right clicked on the installer,

Properties -> Permissions

and check if " Allow executing this file as program "?


Start with that.



Metaxa

I did that. However, it seems to want to open it with the Ubuntu Software Center, which doesn't know what to do with it.

---

### Post by 2F4U on 2012-10-20
Did you follow the instructions? Open a terminal and change to the folder where the software has been extracted. Then type

```
sudo ./install.sh
```

This should start the installation process.

---

### Post by kturcotte on 2013-01-21
> **2F4U said:**
> Did you follow the instructions? Open a terminal and change to the folder where the software has been extracted. Then type

```
sudo ./install.sh
```This should start the installation process.

I gave up on this before, but I have GOT to do this. Windows just will NOT allow me to do what I need to do, and Linux will. However, I am COMPLETELY and TOTALLY new to Linux. I am used to a complete GUI, and know nothing about command lines or anything. Unfortunately, I'm going to need step by step directions, and to be talked to like I'm 5 lol

---

### Post by 64Buntu on 2013-01-21
find out where you put the file (Nivida drivers) for example if they were in the downloads folder you would open terminal (ctrl+alt+t)quick way and type

```
cd Downloads
```
then type 
```
sudo ./install.sh
```

to change directory type 'cd' then the name of the folder and to find all the folders in the current directory type 'ls'

---

### Post by grahammechanical on 2013-01-21
Excuse me but may I ask a question? Why are you downloading Nvidia drivers and trying to install them? The usual procedure even for those of us who have used Ubuntu for a long, long time is to go to System Settings>Software Sources and open the Additional Drivers tab.

There you will find 8 video drivers to choose from. You may be using the Nouveau open source driver. It is the default. The others would be proprietary (Nvidia). Just select one and click Apply.

Oh, do you think that you can provide a link to where you downloaded Crashplan from? We might need to check for ourselves the install instructions.

Is this the thing?

[http://www.crashplan.com/consumer/download.html?os=Linux]("http://www.crashplan.com/consumer/download.html?os=Linux")

No install instructions on that page. Not such good customer service, then.

What do you not like about the Backup utility that comes ready installed with Ubuntu?

Regards.

---

### Post by kturcotte on 2013-01-21
> **64Buntu said:**
> find out where you put the file (Nivida drivers) for example if they were in the downloads folder you would open terminal (ctrl+alt+t)quick way and type

```
cd Downloads
```then type 
```
sudo ./install.sh
```to change directory type 'cd' then the name of the folder and to find all the folders in the current directory type 'ls'

 That worked! Thank you so much!!! Now, how do I point Crashplan to my NAS to backup FROM it? I can't even seem to access it at all through Linux.

---

### Post by 64Buntu on 2013-01-21
just installed to get point of view if you cannot open crash plan use the command line

```
/usr/local/bin/CrashPlanDesktop
```

---

### Post by kturcotte on 2013-01-21
> **64Buntu said:**
> just installed to get point of view if you cannot open crash plan use the command line

```
/usr/local/bin/CrashPlanDesktop
```

 I've got Crashplan open just fine. Now just sot sure how to start backup FROM my NAS.

---

### Post by 64Buntu on 2013-01-21
Oh to add if you want rock solid backup you can use the daja-dup backup tool that uses Ubuntu one no install required!

---

### Post by kturcotte on 2013-01-21
> **64Buntu said:**
> Oh to add if you want rock solid backup you can use the daja-dup backup tool that uses Ubuntu one no install required!

 Is that going to allow me to backup 6 TBs (Yes, I said 6 TBs, and I'm serious lol)?

---

### Post by 64Buntu on 2013-01-21
urm wow that is a lot!

No it can only backup 5gb i belive.

---

### Post by kturcotte on 2013-01-21
> **64Buntu said:**
> urm wow that is a lot!

No it can only backup 5gb i belive.

 I know it's a lot. Crashplan allows unlimited data, and this machine will be running 24/7 on a 5 Mbps up connection. Still, I realize, it's going to take awhile.

---

### Post by kturcotte on 2013-01-30
Now the issue is that neither Crahplan, or even Linux can see my networked drives. Is there something I have to do to enable this maybe? Windows sees the automatically (Just won't let me backup from them).

---

