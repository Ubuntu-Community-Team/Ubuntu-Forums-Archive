---
title: "Coconut - flexible livecd image builder ;)"
date: 2008-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by sashz on 2008-01-21
I wrote a build script that is intended for the edubuntu-ru project. The idea is inspired from opensuse kiwi build system. You can use this script to create  your personal livecd with favourite packages. The script has not finished yet, so don't criticize me so much. 

The build script simplifies creating livecd (installation) disks from binary deb packages according to the specified configuration. The configuration is a XML file with list of installation packages and tasks, the bootloader configuration and the repository information.  Unlike the programs of Reconstructor type, coconut does not modify cd images. It builds their itself :)

SVN repository  with current version are located to [https://www.edubuntu-ru.org/svn/coconut/trunk/]("https://www.edubuntu-ru.org/svn/coconut/trunk/")

Command line parameters:

```
coconut [-h|--help][-m|--sub-architecture <subarch>][-d|--build-directory <dir>][-l|--language <lang>][-k <key file>] <config.xml>

```

Where,

-h  -  Help
-m subarch - Hardware sub architecture (for example, “lpia” for “i386&#8243; architecture). It is not specified by default.
-d dir - Directory where the  system will be built (current by default).
-l lang - Recommended system localization
-k keyfile - Public authorization key  of additional repositories 
config.xml - Configuration file of building system 

Get the build script from  the SVN repository:
```
svn co https://www.edubuntu-ru.org/svn/coconut/trunk/

```

Check that all necessary additional packages are installed. They are listed in the beginning of  coconut.py file or below:

*For all targets:* debootstrap, rsync, python, procps, squashfs-tools
*For i386,amd64 PC:* sbm, syslinux, gfxboot, gfxboot-theme-ubuntu
*For powerpc PS3:* ps3-kboot
*For powerpc OpenFirmware:* yaboot

For example on i386/amd64
```
sudo apt-get install debootstrap rsync python procps squashfs-tools sbm syslinux gfxboot gfxboot-theme-ubuntu

```

Go to  the work directory:
```
cd trunk

```

Configuration samples are located to the config directory. To create an sample livecd, type:

```
sudo ./coconut.py config/config-example.xml

```

**Attention!** Before creating you  need  check the path of repository. Check a path attribute of  repository in the configuration file.

Depend on  CPU performance the building can take some time. After the creating is finished, the bootable ISO image will be located to  in directory build-<image name>-<architecture>.

**Note:** Currently cross-build is not supported. You have to use the host  that is the same as target.

Configuration sample:
```
<image name="base">
    <boot type="livecd">
        <title>Ubuntu Base Live CD</title>
        <description>This is an Ubuntu Base Live CD.

For the default live system, enter "live".  To verify the CD for errors, enter "check".  To run memtest86+, enter "memtest"
</description>
        <release url="http://edubuntu-ru.org"/>
        <gfxboot name="bootlogo" background="0xB6875A"/>
        <menu default="live" timeout="300" prompt="1">
            <label name="live" kernel="/casper/vmlinuz" append="file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --">^Start or install Ubuntu</label>
            <label name="check" kernel="/casper/vmlinuz" append="boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --">^Check CD for defects</label>
            <label name="memtest" kernel="/install/memtest" append="-">^Memory test</label>
            <label name="hd" localboot="0x80" append="-">^Boot from first hard disk</label>
        </menu>
    </boot>
    <repository suite="gutsy" path="http://dk.archive.ubuntu.com/ubuntu">
        <component name="main"/>
        <component name="restricted"/>
    </repository>
    <repository suite="gutsy" path="http://dk.archive.ubuntu.com/ubuntu">
        <component name="universe"/>
        <component name="multiverse"/>
    </repository>
    <packages>
        <package name="minimal^"/>
        <package name="standard^"/>
        <package name="mc"/>
        <package name="elinks"/>
    </packages>
    <packages type="livecd">
        <package name="casper"/>
        <package name="lupin-casper"/>
    </packages>
    <packages arch="i386">
        <package subarch="i386" name="linux-generic"/>
        <package subarch="lpia" name="linux-lpia"/>
    </packages>
    <packages arch="amd64">
        <package name="linux-generic"/>
    </packages>
</image>
```

---

### Post by Mary.Riley on 2008-02-05
That looks really useful. What kind of success have you had with it yet?

---

