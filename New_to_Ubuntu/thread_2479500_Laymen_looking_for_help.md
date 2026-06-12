---
title: "Laymen looking for help"
date: 2022-09-26
forum: New to Ubuntu
---

### Post by kenm1971 on 2022-09-26
[COLOR=#141414][FONT=&quot]I have very limited knowledge of Linux ... Let's just say if I can't find a step-by-step.. Well, I'm not able..[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Sometimes even with one 
I still can't do it..[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Like now..[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]My switch is down and Allied wants a service contract to send me a copy of the OE firmware that it came with..[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]But I have an open source builder for most all their stuff !!!! I just can't figure out why its not working..[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]It is set up to basically to be a one-command build.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]But I get error after error as I go about fixing its issue..[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]I have added links to the network pkg for the x510.. below and the builder and my old firmware (that gives me "bad release header") and won't install[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot][h=3][Allied Telesis firmware builder - Google Drive]("https://drive.google.com/drive/folders/1TS2iP3MOuApFNuAemQ3BwqmivLfH7PcU?usp=sharing")[/h]
[COLOR=#8C8C8C][IMG]https://ssl.gstatic.com/docs/doclist/images/drive_2022q3_32dp.png[/IMG] drive.google.com[/COLOR]


[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]If someone could help me with it I would be grateful,[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Thanks in advance, Ken[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot](the how-to I got with it.. )[/FONT][/COLOR]


[COLOR=#141414][FONT=&quot]-----------------------------[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]The enclosed tarball contains:[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]- chroot, this provides the toolchain[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]- buildsys, a tool for building a set of packages[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]- the cached download directory (dl) that buildsys usually generates[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot](with all the GPL code and some BSD code too).[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]- The wrapper scripts necessary for building.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]- this README.txt[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]To build the main release[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]-------------------------[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]1] build requirements[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]1.1] to get a complete replica of an official release you will need[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]to scp or tftp "/pkg/network*.pkg" from your switch and place it into[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]the dl directory (this is our proprietary package (squashfs image)[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]containing the switch driver, protocols etc...).[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]To get access to this file you will need to create a shell script[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]on the device and activate it:[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]awplus#edit copy.sh[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]#insert the following text[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]cp /pkg/*.pkg /flash/[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]#Activate the script. This will copy the package to the flash directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# (Ensure you have ample space left on your device)[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]awplus#activate copy.sh[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Use your preferred method to copy the file off the switch.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]1.2] Chroot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]The build is done in a gentoo chroot. The chroot is provided as a[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot].deb package located at chroot/awplus-chroot6_20150223-1atl2_all.deb[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]On debian based systems, this can just be installed. If your Linux[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]system is not debian based, you can still install the chroot[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]manually using the following steps:[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Create a temporary working directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ mkdir tmpchroot[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ cd tmpchroot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Extract the debian package into the temporary directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ ar x path/awplus-chroot6_20150223-1atl2_all.deb[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]# ls will show a control.tar.* and data.tar.gz[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Install the chroot. This will extract the data to /chroot/20170112d[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo tar -C / -xSpf tmpchroot/data.tar.*[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Run the post-install script.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ tar -zxf control.tar.gz ./postinst[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo bash postinst[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Remove the temporary working directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ cd ..[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ rm -rf tmpchroot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]Be careful not to manually delete the installed chroot as it mounts[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]your home directory inside when doing builds, so there is a danger[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]that you will accidentally erase your home directory. Make sure any[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]mounted directories are unmounted first.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]1.3] Userchroot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Build userchroot which allows using a chroot without being the root user:[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ cd scripts[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ gcc -o userchroot userchroot.c[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# The chroot.py scripts expect userchroot to live in /usr/bin[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo cp userchroot /usr/bin/[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]# Give userchroot suid privileges to allow it to work[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo chmod u+s /usr/bin/userchroot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]NOTE:[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Toolchain patches and build options are in the chroot tarball, under[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]/chroot/20170112d/usr/local/portage[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-libs/uclibc[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-devel/binutils[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-devel/gcc[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-devel/gdb[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-devel/insight[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]sys-kernel/linux-headers[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]NOTE: 20170112d is the date of the portage release file that the[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]chroot was created from.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]1.4 Build scripts.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]The scripts in the scripts directory are used to kick off the[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]build process. They need to be somewhere in your path.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]Alternatively you can add the scripts directory to your path.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]1.5 tftpboot directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]The build process attempts to mount the directory /tftpboot inside[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]the chroot to copy the release output to. If this directory doesn't[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]exist, you will need to create it.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo mkdir /tftpboot[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]$ sudo chmod a+rwx /tftpboot[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]2][/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]cd into the buildsys directory[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]buildsys x510 -- network=import[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]This should give you a file called "x510-5.4.8-$(whoami).rel"[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]which is a fully fledged release.[/FONT][/COLOR]

[COLOR=#141414][FONT=&quot]For other platforms, replace x510 with the name of the platform.[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]The names required to build various platforms can be derived from[/FONT][/COLOR]
[COLOR=#141414][FONT=&quot]the names of the .lua files in the root of the buildsys directory.[/FONT][/COLOR]

---

### Post by Irihapeti on 2022-09-27
*Thread moved to **New to Ubuntu** as it's a request for support.*

---

### Post by oldfred on 2022-09-28
Everything computer related has required firmware updates many related to Spectre virus, repoline, RETBleed -  firmware update needed
You are showing files [COLOR=#141414][FONT=&amp]20150223 & [/FONT][/COLOR][COLOR=#141414][FONT=&amp]20170112d or very old files.
Any Ubuntu over 5 years old is also outdated, unless you have paid for longer term support.

Better to spend the money & get updated current files.
[/FONT][/COLOR]

---

