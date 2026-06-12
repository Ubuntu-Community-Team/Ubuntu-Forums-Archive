---
title: "Install latest Beryl svn from packages repository!"
date: 2006-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Treviño on 2006-10-18
**EDIT**: *_Beryl is no more developed_, the latest git builds for edgy and feisty are available at the repos below, but they aren't maintened anymore.*

[Beryl 0.1.1 is coming]("http://blog.beryl-project.org/?p=11"), but the new fork isn't no more much daily-updated like the previous compiz-quinn... Though, «we» like to stay updated...
So, considering there's some people who love to update, and that beryl need testers for new features included in SVN (isn't it? :confused:), I decided to open a little repository in which I'll upload the latest beryl svn snapshots...
Now, while our great developers are coding, we can have in our PCs their latest works!

Those are the lines you've to add to your /etc/apt/sources.list (select between edgy and dapper)
```
# Treviño's Ubuntu dapper Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages... Thanks to foxy123
deb http://download.tuxfamily.org/3v1deb dapper beryl-svn
deb-src http://download.tuxfamily.org/3v1deb dapper beryl-svn
``````
# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
``````
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, compiz and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs...
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```Trust me using [FONT=Courier New]KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -[/FONT]

Simply update your Ubuntu machine to have the new greatest features of Beryl (as always much stable)...!

Packages are called [FONT=Courier New]package_upstream-version+svn-date-svn-version_i386.deb[/FONT]
Actually I've used the "standard" package names, anyway I could also rename them to *-svn to make my debs alternative to official Beryl (also if, considering that there are two different repo, it shouldn't be a problem)...
The updates have no a precise plan... I simply will try to update when there are new things... 

Bewlow you find the "makedebs" script file I wrote to update, rebuild and mantain the packages; try it if you simply want to compile beryl in your PC or if you want make another repository (especially for other arch)...

```
#!/bin/bash
# makedebs script for easy compiling and building deb packages for beryl git
#
# (c) 2006-2007 Treviño - Released under GPLv2 Terms
#
#  USAGE
#  You should simply run this script to create and your beryl git
#  tree and package it, but there are also some "advanced" tasks:
#
#    ./makedebs                   performs all the tasks (sync and package)
#    ./makedebs update            just sync the local data to remote git
#    ./makedebs build             try to build the needed items
#    ./makedebs <item>            build only the <item> (if needed)
#    ./makedebs rebuild <item>    force a rebuild of the <item>
#    ./makedebs repack <item>     force a repack of the <item>
#
#   To change the content of a package (or applying patch) you can add
#   some bash script files called "pkgxtra.sh" on each <item> dir to
#   perform extra tasks after that each package has been compiled
#
#   To Package an <item> file not included yet on the $DISTRODIR you can
#   add an "<item>/debian" tree to your $DISTRODIR_USER folder (see below)
#

packager="Trevi"
packager_email="trevi55@gmail.com"
package_sufix="3v1ubuntu"

#to test settings-dump properly
export DISPLAY=""

DEFPREFIX="/usr"
MYPREFIX=${PREFIX:-$DEFPREFIX}
DISTRODIR="distro-specific-build-files"
DISTRODIR_USER="distro-specific-build-files-user"
PRIOPKGS="beryl-core beryl-settings-bindings beryl-plugins"
GITURL="git://anongit.beryl-project.org"
GITWEB="http://gitweb.beryl-project.org"

#for i in $(find |grep "\.git/remotes/origin"); do echo $i; perl -i -p -e 's/git./anongit./' $i; done
#sed -i -e 's;git://git\.;git://anongit.;' ${file}

autogenpkg_cmd="./autogen.sh --prefix=$MYPREFIX"
buildpkg_cmd="fakeroot dpkg-buildpackage -b -us -uc"
repkg_cmd="fakeroot ./debian/rules binary"

git_items="$(wget -q -O - "$GITWEB/?a=project_index"|grep "^beryl/" | cut -d' ' -f1)"

if [ -z "$git_items" ]; then
    echo "There are problems while retrieving the beryl items list; exiting..."
    exit 2;
fi

mkdir -p "beryl"

if [ -z "$(which git-clone)" ]; then
    echo -e "\nYou must install the 'git-core' package in order to use needed git tools\n"
    exit 2
fi

for git_item in $git_items; do
    git_item_name="$(basename $git_item)"
    if [ ! -d "$git_item/.git" ]; then
        echo -e "\n\033[4mNo $git_item_name git folder found! Downloading...\033[0m"
        cd "beryl"
        if ! git-clone $GITURL/$git_item; then
            echo "There are problems retrieving git data for $git_item_name. Skipping..."
            #exit 2;
        fi
        echo ""
        cd ../
    elif [ -d "$git_item" ]; then
        cd "$git_item"
        if ! git-log &> /dev/null; then
            echo "The $git_item_name git directory isn't here, please remove the '$git_item' dir and run again this script."
            echo "Whould you like this script make this (all your '$git_item' data will be removed)?"
            read -p " [Y/n]: " -n1 continue;
            if [ "$continue" != "$(echo Y | tr [:upper:] [:lower:])" ]; then
                echo ''
                exit 2
            else
                cd ../
                rm -rf "$git_item"
                if ! git-clone $GITURL/$git_item; then
                    echo "There are problems retriving git data for $git_item_name. Skipping..."
                    #exit 2;
                fi
            fi
        else
            if [ -z "$(echo $* | grep -wE "batch|noupdate|build")" ]; then
                echo -e "\n\033[4mUpdating the $git_item_name package...\033[0m"
                if ! git-pull origin; then
                    report="$report\n\033[4mGIT PULL FAILED\033[0m"
                    sleep 3
                fi
            fi
        fi
        cd ../..
    else
        echo "There are some errors with build directories, please report this to the Author"
        exit 2
    fi
done

if [ -n "$(echo $* | grep -wE "update|pull")" ]; then
    exit 0;
fi

cd "beryl"

if [ -f "./VERSION" ]; then
    . "./VERSION"
    base_ver="$VERSION"
    VERSION=""
fi

function git_commit() {
    #git-log|grep -m1 commit|cut -d' ' -f2
    git-rev-parse HEAD
}

function git_commit_date () {
    date -d "$(expr "$(git-log|grep "Date" -m1)" : "Date:[ ]\+\(.*\)[+-]\{1\}[0-9]\{4\}")" +"%Y%m%d"
}

function errorcontrol() {
    item="$1"
    if [ -z "$(echo $* | grep "batch")" ]; then
        echo -e "\nProblems occurred while building $item packages... Continue Building?"
        read -p " [Y/n]: " -n1 continue;
        if [ "$continue" != "$(echo Y | tr [:upper:] [:lower:])" ]; then
            echo -e "$report\n";
            exit 2
        fi
    else
        echo -e "\nProblems occurred while building $item packages. Skipping as requested..."
    fi
}

function buildpkg() {
    rm -f ../*.deb

    if [ -f "./VERSION" ]; then
        . "./VERSION"
        base_comp_ver="$VERSION"
        VERSION=""
    fi

    if [ -z "$base_comp_ver" ]; then
        if [ -n "$base_ver" ]; then
            base_comp_ver="$base_ver"
        else
            base_comp_ver=$(dpkg-parsechangelog|grep --max-count=1 -F "Version:" |cut -d" " -f2|sed "s/-[0-9]ubuntu[0-9]/-1/");
        fi
    fi

    base_comp_ver=$(echo "$base_comp_ver" | sed 's/-svn//g');

    if [ -n "$(echo $* | grep "repack")" ]; then
        action="repack"
    elif [ -n "$(echo $* | grep "rebuild")" ]; then
        action="rebuild"
    else
        action="build"
    fi

    build="0"
    if ( [ $action = "rebuild" ] || [ $action = "build" ] ); then
        tstpkg="$(cat debian/control |grep "^Package:" -m1| cut -d" " -f2)"
        for oldpkg in ../../debs/${tstpkg}_*.deb; do
            pkgbuild="$(expr "$(dpkg-deb --field "$oldpkg" Version)" : ".\+~${package_sufix}\([0-9]\+\)")"
            if ( [ -n "$pkgbuild" ] && [ "$pkgbuild" -ge "$build" ] ); then
                build=$(($pkgbuild + 1))
            fi
        done
    fi

    #".\++git[0-9]\{8\}-r\([0-9]\+\)~3v1ubuntu[0-9]\+" -> beryl-core_0.3+git20070401-r1~3v1ubuntu5

    source_package=$(dpkg-parsechangelog|grep --max-count=1 -F "Source:" |cut -d" " -f2)

    if [ -f "/etc/lsb-release" ]; then
        distro="$(cat /etc/lsb-release|grep DISTRIB_CODENAME | cut -d'=' -f2)"
    fi

    if [ -z "$distro" ]; then
        distro="unstable";
    fi

    version="${base_comp_ver}+git$(git_commit_date)~${package_sufix}${build}"
    echo -e "$source_package ($version) $distro; urgency=low\n\n  * Upgrade to GIT commit $(git_commit)\n\n -- $packager <$packager_email>  $(LANG=en_US date +"%a, %d %b %Y %T %z")\n" > "./debian/changelog"
    sed "$(cat "../$DISTRODIR_ITEM/$item/debian/control" | grep "^Maintainer:" -n -m1 | cut -d':' -f1)cMaintainer: $packager <$packager_email>" "../$DISTRODIR_ITEM/$item/debian/control" > "./debian/control"
    cat "../$DISTRODIR_ITEM/$item/debian/changelog" >> "./debian/changelog"

#     if ( [ -f "./VERSION" ] && [ ! -f "./VERSION.base" ] ); then
#         mv -v "./VERSION" "./VERSION.base"
#         cp -v "./VERSION.base" "./VERSION"
#         perl -i -p -e "s/VERSION=.*/VERSION=$version/" "./VERSION"
#     fi

    if [ $action = "repack" ]; then
        cmd2run="$repkg_cmd"
    else
        cmd2run="$buildpkg_cmd"
    fi

    if ! $cmd2run; then #fakeroot dh_gencontrol -u"-v$version"
        errorcontrol $item
        report="$report\nBUILD FAILED for $item"
        return 2
    fi

    if [ -f pkgxtra.sh ]; then
        chmod +x pkgxtra.sh
        echo -e "\nRunning extra scripts for $item..."
        if ! ./pkgxtra.sh $action; then
            errorcontrol $item
            report="$report\nBUILD FAILED for extrascripts on $item"
            return 2
        fi
    fi

    mv -f ../*$package_sufix*.deb ../../debs/
    mkdir -p ../../debs-old
    mv -f ../*.changes ../../changelogs &> /dev/null

    for package in $(cat debian/control |grep Package| cut -d" " -f2); do
        for deb in $(find ../../debs/ -maxdepth 1 -type f | grep "${package}_.*\.deb"); do
            if  [ -z $(dpkg-deb --field "$deb" Version | grep -F "$version") ]; then
                mv -f "$deb" ../../debs-old;
            fi
        done
    done

    rm -rf ./debian

#     if [ -f "./VERSION.base" ]; then
#         mv -v "./VERSION.base" "./VERSION"
#     fi
}

mkdir -p ../changelogs ../debs
#rm -f ../debs/*.deb

ITEMS="$PRIOPKGS"

for beryldir in $DISTRODIR/* $DISTRODIR_USER/*; do
    if [ -n "$(echo $beryldir | grep -F "$DISTRODIR_USER")" ]; then
        itemdir="${beryldir/$DISTRODIR_USER\//}"
    else
        itemdir="${beryldir/$DISTRODIR\//}"
    fi

    if ( [ -d $beryldir ] && [ -d $beryldir/debian ] && [ -f $itemdir/autogen.sh ] ); then
        
        for userberyldir in $*; do
            if ( [ "$userberyldir" = "$itemdir" ] ); then
                USERITEMS="$USERITEMS $itemdir"
            fi
        done
        
        found="false"
        for item in $ITEMS; do
            if [ "$item" = "$itemdir" ]; then
                found="true"
            fi
        done
        
        if [ "$found" != "true" ]; then
            ITEMS="$ITEMS $itemdir";
        fi
    fi;
done;

if [ "$USERITEMS" != "" ]; then
    ITEMS="$USERITEMS"
fi


for item in $ITEMS; do
    cd $item
    chmod +x autogen.sh &> /dev/null

    rm -rf ./debian
    #ln -s ../$DISTRODIR/$item/debian
    if [ -d "../$DISTRODIR/$item/debian" ]; then
        DISTRODIR_ITEM="$DISTRODIR"
    elif [ -d "../$DISTRODIR_USER/$item/debian" ]; then
        DISTRODIR_ITEM="$DISTRODIR_USER"
    else
        report="$report\nNo debian files for $item"
        errorcontrol "$item"
    fi
    
    cp -ar ../$DISTRODIR_ITEM/$item/debian ./

    if [ ! -e ./.build-done ]; then
        echo 0 > "./.build-done";
    fi

    latest_ver="$(cat ./.build-done)"

    if [ "$(git_commit)" != "$latest_ver" ]; then
        echo -e "\nBuilding $item..."
        if $autogenpkg_cmd && buildpkg; then
            report="$report\n$item built OK"
            if [ "$item" = "beryl-core" ]; then
                wait
                echo -e "\a"
                if ! (sudo dpkg -i ../../debs/{beryl-dev,libberyl}*.deb && wait); then
                    errorcontrol "$item"
                fi
            fi
            echo "$(git_commit)" > ./.build-done
        else
            report="$report\nBUILD FAILED for $item"
            wait
            errorcontrol "$item"
        fi
    else #elif [ "$(git_commit)" = "$latest_ver" ]; then
        if ( [ -n "$(echo $* | grep "rebuild")" ] || [ -f "./.rebuild" ] ); then
        #|| ( [ "$DISTRODIR_ITEM" = "$DISTRODIR" ] ) && [ "$(cd ../$DISTRODIR_ITEM && git_commit_date)" -gt "$(git_commit_date)" ]
            echo -e "\nRebuilding $item..."
            if make clean && buildpkg rebuild; then # && make clean ?
                rm -f "./.rebuild"
                report="$report\n$item rebuilt OK"
            else
                report="$report\nREBUILD FAILED for $item"
                errorcontrol "$item"
            fi
        elif ( [ -n "$(echo $* | grep "repack")" ] || [ -f "./.repack" ] ); then
            echo -e "\nRepacking $item..."
            rm -f "./.repack"
            buildpkg repack;
            report="$report\n$item repackaged OK"
        else
            report="$report\n$item already built"
        fi
    fi
    cd ../
done

echo -e "\n$report\n";

```I hope you'll like this...
Anyway you could always download the *latest version* of this ***script*** from [here]("http://3v1n0.tuxfamily.org/xtra/makedebs.tar.gz") (*old* script for svn is stil [here]("http://3v1n0.tuxfamily.org/xtra/makedebs.tar.gz")).

***More informations and updates*** in the [beryl-project.org original thread]("http://forum.beryl-project.org/topic-5473-bery-svn-snapshots-unofficial-ubuntu-repository").
Bye...! :wink:

---

### Post by domino on 2006-10-18
Nice how-to and thanks for the small repo :). I tried to import the key from term and got this error. So I imported from Synaptic and it imported fine. I'm running Edgy.

sudo: pam_authenticate: Conversation error

---

### Post by Mystique on 2006-10-18
something wrong with the repo?

apt-get error:
301 Moved Permanently

on the website, the .deb are there...

greet
mel

---

### Post by Treviño on 2006-10-18
Considering that basically packages for dapper and edgy are basically the same, I'm using the same file in the repository using an .htacess file to redirect....

Please let me know if they don't work... You can use the dapper repo anyway...!

---

### Post by plueken on 2006-10-18
Thanks a lot!  This works great!  I use Dapper, and I'd tried compiling from the Beryl SVN before, but I'd always had too many problems and gave up.  Your repo worked fine, and I'm enjoying all of the new benefits of the SVN 1.1.

Now I just have to wait for the REAL version 1.1 to come out, and then see how much longer until I can get my hands on onestone's experimental Burn animation.

---

### Post by ThePresident on 2006-10-18
First, let me say thanks for putting this together. Upon trying to upgrade, I come up with this:

```
W: Failed to fetch http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.1-1+svn20061017-r671-3v1ubuntu0_all.deb
  404 Not Found


W: Failed to fetch http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins_0.1.1-1+svn20061017-r671-3v1ubuntu0_i386.deb
  404 Not Found
```

Hoo boy, what have I done?

---

### Post by PriceChild on 2006-10-18
I'm adding this to my collection of guides linked to in my sig.

---

### Post by Treviño on 2006-10-18
**ThePresident**, do an apt-get update... I've updated my repository and that files aren't no more in...
Then re-upgrade... It must fix!

**[[COLOR=#D40000][B]**[/COLOR]]("http://ubuntuforums.org/member.php?u=43712")PriceChild[/B], many thanks :)

---

### Post by ThePresident on 2006-10-18
> ThePresident, do an apt-get update... I've updated my repository and that files aren't no more in...
Then re-upgrade... It must fix!


Yes, that fixed it.  Thanks a bunch, this should be fun!

---

### Post by linuxmad on 2006-10-18
Treviño, 
Will you add the fire effect to your debs?? ...Please don't say no:-k

---

### Post by Treviño on 2006-10-18
When it will be added to the svn it will be done, btw if anyone want it now I could make an extra package or i could add it to the standard packag....

---

### Post by linuxmad on 2006-10-18
> btw if anyone want it now I could make an extra package or i could add it to the standard packag...

Yes ...:D I really would like to try this effect.. If you can, please do add it..;)

---

### Post by Treviño on 2006-10-18
> **linuxmad said:**
> ..

Yes ...:D I really would like to try this effect.. If you can, please do add it..;)
Added in the repo... Simply upgrade your package and you'll have the... Fire! :D

---

### Post by linuxmad on 2006-10-19
Treviño...thanks You're the MAN!!!!:p

---

### Post by linuxmad on 2006-10-19
This fire effect really ROCKS...
:cool: :cool: :cool: 

..Still, and apart from that I can't get beryl to start automatically. The icon bar starts but not beryl. I have to right click the icon and select reload the window manager, after that it works. Is anyone else having this?

---

### Post by ww2 on 2006-10-19
Newbie question: if I install XGL + Beryl stable, can I easily upgrade to this afterwards?

---

### Post by ThePresident on 2006-10-19
>  	Newbie question: if I install XGL + Beryl stable, can I easily upgrade to this afterwards?

Sure, why not?  I did just that - followed **Treviño's** instructions and off like a flash (or as flashy as a P3 can get, anyway:p ).

---

### Post by ww2 on 2006-10-19
> **ThePresident said:**
> Sure, why not?  I did just that - followed **Treviño's** instructions and off like a flash (or as flashy as a P3 can get, anyway:p ).

Noticed any speed/stability improvement?

In a period of 1 hour I got two hardlocks that forced me to reset X with ctrl + alt + backspace -- and my card is not a X series one. In terms of speed, though, everything is smooth.

That's mostly the reason why I'm considering the upgrade... but if it makes matters worse, I prefer not do anything and learn how to mess with the setup I already have.

Opinions?

---

### Post by ThePresident on 2006-10-19
Well, here's what I'm running, so you can get a sense of what I'm dealing with:

Dell Dimension 4100 (866mhz P3), 512mb RAM, Nvidia MX400 video card

This thing is literally a piece from here and a piece from there.  To say I might have a few speed issues isn't exactly a fair review, because you can see what I'm working with.  I'm keeping all this in mind as I go.

That being said, if I had a few problems with 0.1...0.1.1 seems to have resolved them.  Performance is pretty much flawless, and I'd love to see how this looks on a newer/faster machine...since it looks pretty good right now on this junker!

I am having the same problem as **linuxmad** though, and from looking around, I think it's a dbus config issue...but I'm waiting for an answer from the professionals on that one!  For the moment, I'll just reload the window manager once I start up...which frankly isn't all that often.  Overall I'm quite pleased with the upgrade...but as always, YMMV.

---

### Post by ww2 on 2006-10-19
Well, I'm also having that issue with 0.1, so it's not endemic to the SVNs. Probably something easy to fix?

By the way, after you upgraded, did you lose any configuration whatsoever, or had to modify anything?

---

### Post by Treviño on 2006-10-19
> **ww2 said:**
> Well, I'm also having that issue with 0.1, so it's not endemic to the SVNs. Probably something easy to fix?

By the way, after you upgraded, did you lose any configuration whatsoever, or had to modify anything?
You lose your configuration... Make a backup of ~/.beryl if you want...
Anyway consider that the configuration file use the same rules, so you could import the old file to the new configuration (editing by hand I mean..)

---

### Post by proctor on 2006-10-19
All went well for me, I had similar problems as ThePresident but after updating & upgrading a few times :P Its looking good. Appreciate the effort, was wondering how to get the daily svn's:D  

Good work, lovin the progress of the fork.

---

### Post by Treviño on 2006-10-20
For beryl users, today ***beryl 0.1.1 has been released***... 
For svn repository users, there are no too much news, for others I think many!

Anyway the svn repo will be updated in next days, of course...

Just... *Upgrade *;)

---

### Post by dentaku65 on 2006-10-23
> **Treviño said:**
> For beryl users, today ***beryl 0.1.1 has been released***... 
For svn repository users, there are no too much news, for others I think many!

Anyway the svn repo will be updated in next days, of course...

Just... *Upgrade *;)

Last upgrade of this morning broke beryl ](*,) 

```
beryl: '/usr/lib/beryl/libsettings.so' plugin version does not match beryl version.
beryl: Couldn't load plugin 'settings'
```

Grazie to fix this! ;)

---

### Post by Treviño on 2006-10-23
I didn't get that, anyway I'm reupdating.......

---

### Post by dentaku65 on 2006-10-23
> **Treviño said:**
> I didn't get that, anyway I'm reupdating.......


mmm, many people have got this problem in today's upgrade, see beryl forum too:
[http://yep.it/?qv6pr3](http://yep.it/?qv6pr3)

ciao

---

### Post by Treviño on 2006-10-23
I knew...
The latest packages are ok... That bug was due to some errors in svn ;)

---

### Post by dentaku65 on 2006-10-23
> **Treviño said:**
> I knew...
The latest packages are ok... That bug was due to some errors in svn ;)

yes fixed! ;)

---

### Post by Treviño on 2006-10-24
I've updated the 'makdebs' script to make it work with latest svn directory tree...
Look on first page, or downoad it from [http://3v1n0.tuxfamily.org/xtra/makdebs.tar.gz](http://3v1n0.tuxfamily.org/xtra/makdebs.tar.gz) ;)

---

### Post by Shadowline on 2006-10-24
I'm trying the script and I get a strange error (for me it's strange)....


Checked out external at revision 84.

Checked out revision 799.
shadowline@blackhorse:~$ ./makedebs: 27: Syntax error: "(" unexpected


any ideas ?

---

### Post by Treviño on 2006-10-25
You should use bash for running that scirpt...
Read in the main thread in beryl forum how to fix that ;)

---

### Post by dutchmega on 2006-10-26
Great! The SVN-version is better, before this I got weird bugs like black windows in gedit when resizing and such.

---

### Post by pichalsi on 2006-10-30
nice i hope this fixes the thing, when i ctrl alt F1 to console and ctrl alt f7 back to X i get only black screen and cursor...

---

### Post by dentaku65 on 2006-10-30
Is very good the svn version... I have a little issue that happening sometimes when I reboot the machine, the problem regarding emerald that hog memory and blink is own interface; I have to killall emerald then reload it to get it works.

---

### Post by Treviño on 2006-10-30
> **dentaku65 said:**
> Is very good the svn version... I have a little issue that happening sometimes when I reboot the machine, the problem regarding emerald that hog memory and blink is own interface; I have to killall emerald then reload it to get it works.
Sometimes I get the same.... Simply (re)post it in the bug-tracker ;)

---

### Post by migla on 2006-11-08
Tonight I keep getting this message when trying to update beryl-plugins-data:

> Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb](http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb)  Size mismatch

Is this problem at my end or in the repo?

And thank you for this great repository. Always eagerly awaiting updates.

---

### Post by jharris on 2006-11-08
I'm getting the same problem:
> W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb](http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb)
  Size mismatch

---

### Post by jharris on 2006-11-08
I manually downloaded the deb and found that it is actually corrupt. Is the any chance of getting this fixed?

Cheers
Jay

---

### Post by CowzRule on 2006-11-08
After doing "sudo apt-get update" then "sudo apt-get upgrade". I get the following:

> Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb](http://3v1n0.tuxfamily.org/pool/dapper/beryl-svn/beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb)  Size mismatch

Any thoughts?

Thanks

---

### Post by cocoapunk on 2006-11-08
Thanks a lot 3v1n0 :)
Just a quick question (this might be better suited for beryl forums, but I'm not sure if its due to ubuntu X configuration or if this is a default X setting in 7.1, since it never happened in 6.9):
Can I have shift+backspace not do the same thing as crtl+alt+backspace (as in restart gdm/X)?

Thanks

---

### Post by hikaricore on 2006-11-08
> **jharris said:**
> I manually downloaded the deb and found that it is actually corrupt. Is the any chance of getting this fixed?

Cheers
Jay

Same results here, didn't really read the end of this topic until now but found the same results you did:

> [hikaricore@devistate:/media/devistate (103.0 Mb)]$ sudo dpkg -i beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb
(Reading database ... 156850 files and directories currently installed.)
Preparing to replace beryl-plugins-data 0.1.1-0ubuntu1 (using beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb) ...
Unpacking replacement beryl-plugins-data ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/beryl/emboss.png')
Errors were encountered while processing:
 beryl-plugins-data_0.1.3+svn20061108-r1090-3v1ubuntu0_all.deb


Looks like we'll have to wait for an update >.<

hope it's ok to run beryl svn without the plugin data.. lol time to find out

---

### Post by foxy123 on 2006-11-09
It looks like Dapper packages are build against newer libc6 library and do not install on a standard Dapper :(

I tried the script, it works OK, but I cannot figure out how to skip building packages I do not need.

---

### Post by BLTicklemonster on 2006-11-11
BLARGH!!!

```
ticklemonster@ticklemonster:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  beryl beryl-plugins beryl-settings 
The following packages will be upgraded:
  beryl-core beryl-dev beryl-manager beryl-plugins-data 
4 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 2013kB of archives. After unpacking 989kB will be freed.
Do you want to continue? [Y/n/?] y
Err http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-core 0.1.3+svn20061110-r1119-3v1ubuntu0
  404 Not Found
Err http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-dev 0.1.3+svn20061110-r1119-3v1ubuntu0
  404 Not Found
Err http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-manager 0.1.3+svn20061110-r1117-3v1ubuntu0
  404 Not Found
Err http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-plugins-data 0.1.3+svn20061110-r1118-3v1ubuntu0
  404 Not Found
ticklemonster@ticklemonster:~$ 

```

---

### Post by BLTicklemonster on 2006-11-11
That Trevino...he's a swell feller, don't you all think so?

---

### Post by Treviño on 2006-11-13
This is OT here... There's nothing related to my repositories... Just to the list!

All the files available in my repos hare under the sun's light... Just look at the falcon's html front-end!

---

### Post by Ago12 on 2006-11-13
Yep, I have never got problems of this kind with Trevino's repo...

---

### Post by foxy123 on 2006-11-16
as Dapper svn packages are uninstallable on a standard Dapper, is it possible to fix the script to make it work under new svn structure? I currently get the following error:
```
 svn: PROPFIND request failed on '/trunk'
svn: PROPFIND of '/trunk': 405 Method Not Allowed (http://svn.beryl-project.org)

```
would be much appreciated :)

---

### Post by Treviño on 2006-11-16
Ok... I'll reupload it...
Grab it from the first page!

---

### Post by darrenm on 2006-11-16
Trevino - Firstly thanks for the great packages.

Are you going to put Beryl-vidcap in there soon?

Thanks!

---

### Post by Treviño on 2006-11-16
It's a problem to add vidcap...
becouse it needs extra package that aren't still packaged under edgy, so I should name them, but I whouldn't use a wrong name, so I must ask/wait the beryl team...

---

### Post by foxy123 on 2006-11-16
> **Treviño said:**
> Ok... I'll reupload it...
Grab it from the first page!

oh, thanks a lot. When will you do it? It is still an old version on the first page...

---

### Post by Treviño on 2006-11-16
No... It's updated... Check it!

---

### Post by darrenm on 2006-11-16
> **foxy123 said:**
> as Dapper svn packages are uninstallable on a standard Dapper, is it possible to fix the script to make it work under new svn structure? I currently get the following error:
```
 svn: PROPFIND request failed on '/trunk'
svn: PROPFIND of '/trunk': 405 Method Not Allowed (http://svn.beryl-project.org)

```
would be much appreciated :)

Try 

svn co svn://svn.beryl-project.org/beryl/trunk/ beryl

---

### Post by foxy123 on 2006-11-16
> **Treviño said:**
> No... It's updated... Check it!
it still does not work for me, goes into a loop:
```
svn: PROPFIND request failed on '/beryl/trunk'
svn: PROPFIND of '/beryl/trunk': 405 Method Not Allowed (http://svn.beryl-project.org)
ln: creating symbolic link `.beryl/trunk/makedebs' to `.././makedebs': No such file or directory
No svn folder found! Downloading it...
svn: PROPFIND request failed on '/beryl/trunk'
svn: PROPFIND of '/beryl/trunk': 405 Method Not Allowed (http://svn.beryl-project.org)
ln: creating symbolic link `.
```
and over and over again

---

### Post by ajm2005 on 2006-11-16
:)

---

### Post by Treviño on 2006-11-17
If you alread have a beryl svn directory tree, please (re)move it away...
I'm using exactly the script linked and posted on first page

---

### Post by foxy123 on 2006-11-17
> **Treviño said:**
> If you alread have a beryl svn directory tree, please (re)move it away...
I'm using exactly the script linked and posted on first page
I think I have already tried to run the script form a different directory, but let me try to remove all my old beryl-svn stuff.

---

### Post by foxy123 on 2006-11-17
> **foxy123 said:**
> I think I have already tried to run the script form a different directory, but let me try to remove all my old beryl-svn stuff.

no, I have the same loop, the makedebs going over and over again. I cannot even stop it: it resumes after Ctrl+C and 'killall makedebs'. Only closing a terminal shuts it down. And it does not download anything from svn... ANy idea?

---

### Post by Treviño on 2006-11-17
Sorry... I saw that I used a wrong svn url (wrong protocol), try to take the new script from the first page (I haven't updated the linked script, yet... Use the posted one).

Right url is svn://svn.beryl-project.org/beryl/trunk/ (no [http://.](http://.)....)

Bye...

---

### Post by McQuaid on 2006-11-17
Can you update beryl-dbus?  (currently the 15th)

I'm getting this error:

libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libdbus.so' plugin
Reloading all options.

and the dbus plugin is not showing up as an option in beryl settings.

---

### Post by foxy123 on 2006-11-17
> **Treviño said:**
> Sorry... I saw that I used a wrong svn url (wrong protocol), try to take the new script from the first page (I haven't updated the linked script, yet... Use the posted one).

Right url is svn://svn.beryl-project.org/beryl/trunk/ (no [http://.](http://.)....)

Bye...
no, it's even worse, sorry... closing terminal does not kill the looping script :)

---

### Post by foxy123 on 2006-11-18
> **foxy123 said:**
> no, it's even worse, sorry... closing terminal does not kill the looping script :)
OK, I have copied and pasted the script from the first page and it started all right but then it got into a loop again:
```

...
A    trunk/aquamarine/admin/ylwrap
 U   trunk/aquamarine/admin
Checked out external at revision 605780.

Checked out revision 1267.
ln: creating symbolic link `.beryl/trunk/makedebs' to `.././makedebs': No such file or directory
foxy@neclaptop:~/CVS$ No svn folder found! Downloading it...

Fetching external item into 'trunk/beryl-vidcap/seom'
Checked out external at revision 88.


Fetching external item into 'trunk/aquamarine/admin'
Checked out external at revision 605780.

Checked out revision 1267.
ln: creating symbolic link `.beryl/trunk/makedebs' to `.././makedebs': No such file or directory
No svn folder found! Downloading it...

Fetching external item into 'trunk/beryl-vidcap/seom'
Checked out external at revision 88.


Fetching external item into 'trunk/aquamarine/admin'
Checked out external at revision 605780.

Checked out revision 1267.
ln: creating symbolic link `.beryl/trunk/makedebs' to `.././makedebs': No such file or directory
No svn folder found! Downloading it...


```

the same thing happens with the uploaded script (I guess you have updated it already).

---

### Post by Jonathan2007 on 2006-11-18
Thanks for this repository. I am attempting to get Beryl/Aquamarine installed with X.org 7.1 and Mepis.

---

### Post by foxy123 on 2006-11-19
it looks like the script does not see .svn directory and running itself over and over again

---

### Post by Rob2687 on 2006-11-19
The makefile in trunk already has a nice little script to build debs for you.
All you need to do is check out trunk and run **make all-debs**.

---

### Post by Treviño on 2006-11-21
Yes... That works... Anyway my script is more complete and dedicated to them who want to create another distro for others archs or debian based systems...

Anyway I've put the repo in digg, if anyone want share it... [http://digg.com/linux_unix/Get_always_the_latest_Beryl_stuff_in_you_Ubuntu_box_without_compiling](http://digg.com/linux_unix/Get_always_the_latest_Beryl_stuff_in_you_Ubuntu_box_without_compiling)

---

### Post by foxy123 on 2006-11-21
> **Treviño said:**
> Yes... That works... Anyway my script is more complete and dedicated to them who want to create another distro for others archs or debian based systems...

Anyway I've put the repo in digg, if anyone want share it... [http://digg.com/linux_unix/Get_always_the_latest_Beryl_stuff_in_you_Ubuntu_box_without_compiling](http://digg.com/linux_unix/Get_always_the_latest_Beryl_stuff_in_you_Ubuntu_box_without_compiling)

yes, the script is great and more convenient. It preserves old debs in case there are some bugs in the current svn, which is nice

I had to change some directories in the script to make it work for me. For some reasons it downloads svn into truck folder but looks for .svn in beryl/truck. So change it to truck, but now debs and debs-old folder is created outside the directory I am running script from. It is not a big deal though.

---

### Post by firedrops on 2006-11-21
```
firedrops@echelon:~$ sudo apt-get dist-upgrade
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
Calculando Actualização... Pronto
Os seguintes pacotes serão actualizados:
  beryl beryl-core beryl-dev beryl-manager beryl-plugins beryl-plugins-data
  beryl-settings libberylsettings-dev libberylsettings0
9 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário fazer o download de 2013kB/2577kB de arquivos.
Depois de descompactar, 8192B adicionais de espaço em disco serão utilizados.
Você deseja continuar [Y/n]? y
Obter:1 http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-plugins-data 0.1.3+svn20061121-r1336-3v1ubuntu0 [1722kB]
Obter:2 http://3v1n0.tuxfamily.org edgy/beryl-svn beryl-plugins 0.1.3+svn20061121-r1336-3v1ubuntu0 [291kB]
Obtidos 2013kB em 2s (748kB/s)               
Falha ao obter http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/beryl-plugins-data_0.1.3+svn20061121-r1336-3v1ubuntu0_all.deb  Tamanho incorrecto
Falha ao obter http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/beryl-plugins_0.1.3+svn20061121-r1336-3v1ubuntu0_i386.deb  Tamanho incorrecto
E: Impossível obter alguns arquivos, execute talvez apt-get update ou tente com --fix-missing?

```

Since it's in portuguese, I'll sum it up: it fails to obtain the packages because of incorrect file size. I updated yesterday with no problems so I really don't know what's the problem ](*,) 

very good job anyway :mrgreen:

---

### Post by Treviño on 2006-11-21
Fixed......
Don't forget to digg :P

---

### Post by firedrops on 2006-11-21
thx for fast support 8)

---

### Post by Treviño on 2006-11-24
***_WARNING - IMPORTANT UPDATE_***

Starting from tomorrow (or a few more) **the &#8220;old&#8221; repositories won't work anymore**!
I had to change the repositories links due to some new tuxfamily rules, so _**you must update your sources.list**_ (also for the "standard" 3v1n0 repository that I maintain if you want)

Those are the **new repositories** you *must* use:
```
# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

Maybe some of you have also just been updated by the latest beryl update from my repo with a debconf screen...
This:
[img]http://img222.imageshack.us/img222/8554/screenshot76hy1.png[/img]
Typos a part (fixed), it says what you need to do... I found this as the better solution I could use to notify the many users using this repo!
So, don't worry! It's just a news!

The others repositories and the latest news on it will always be at the same page of the html front-end: [http://3v1n0.tuxfamily.org/dists/edgy](http://3v1n0.tuxfamily.org/dists/edgy)

Check for updates also on the [wiki page](http://wiki.beryl-project.org/index.php/Install/Ubuntu/SVN_Snapshots_Repository)

---

### Post by partriv on 2006-11-24
I have used your new repositories and installed the updates, and while beryl has upgraded, it broke my emerald install, citing the following error message:

emerald-theme-manager: error while loading shared libraries: libemeraldengine.so.0: cannot open shared object file: No such file or directory

any idea what might cause this?  and how i can reload it?  thanks!

---

### Post by Treviño on 2006-11-24
Have you installed libemeraldengine0? :o

---

### Post by partriv on 2006-11-25
it was installed before, when i was running 0.1.1, then i did an update using your repo, 'something happened', and the library went away (i knew this because this is what it said when i tried to run beryl-manager).  

i went into my package manader and repaired the broken install, now i have 0.1.3 from your repo and everything is working GREAT!! :-)  thanks!

it's actually running better than before :)

---

### Post by hikaricore on 2006-11-25
Just a note if anyone else noticed serious beryl slowdown when you updated, the desktop cube plugin now has a transparent cube option which gets enabled by default.  :)  It looks really sweet... but if you're using an integrated intel chipset like myself this drops you to about 5fps... roflmfao, took me a few days to figure out what the hell was wrong.  I also personally disabled the lighting option, not sure if this is new or not but I don't remember seeing it and it was killing me too.

--Aaron

---

### Post by leech on 2006-11-25
> **Treviño said:**
> ***_WARNING - IMPORTANT UPDATE_***

Starting from tomorrow (or a few more) **the “old” repositories won't work anymore**!
I had to change the repositories links due to some new tuxfamily rules, so _**you must update your sources.list**_ (also for the "standard" 3v1n0 repository that I maintain if you want)

Those are the **new repositories** you *must* use:
```
# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn
```

Maybe some of you have also just been updated by the latest beryl update from my repo with a debconf screen...
This:
[img]http://img222.imageshack.us/img222/8554/screenshot76hy1.png[/img]
Typos a part (fixed), it says what you need to do... I found this as the better solution I could use to notify the many users using this repo!
So, don't worry! It's just a news!

The others repositories and the latest news on it will always be at the same page of the html front-end: [http://3v1n0.tuxfamily.org/dists/edgy](http://3v1n0.tuxfamily.org/dists/edgy)

Check for updates also on the [wiki page](http://wiki.beryl-project.org/index.php/Install/Ubuntu/SVN_Snapshots_Repository)

I'm not entirely sure why, but when I updated mine, I didn't get any of the text within the window, it just said "do you agree to the changement" which is an odd way of putting it.  I only just now was able to see your post on it and fix my repositories, this was yesterday that I saw the message.

Thanks for the great packages, with the exception of a few weird things going on, Beryl is working great.

Leech

---

### Post by Dr. Nick on 2006-11-25
Yeah, not sure if it was just the timing of it all but I got the box with no text aswell. Transparent wasnt enabled by default for me though, but enabling it makes it look very cool

---

### Post by hikaricore on 2006-11-26
> **Dr. Nick said:**
> Yeah, not sure if it was just the timing of it all but I got the box with no text aswell. Transparent wasnt enabled by default for me though, but enabling it makes it look very cool

I'm starting to think transparency replaced some other option that wasn't actually in existance anymore and I mistakenly had it checked, as I havn't been able to reproduce my original issue this is my best guess.

---

### Post by kekojeep on 2006-11-26
I'm trying to compile latest Beryl from svn, but it seems that svn.beryl-project.org is offline? When i try 

svn co svn://svn.beryl-project.org/trunk/ beryl

I get an error saying it can't connect to svn.beryl-project.org

Any tips? Where can I find the source to compile it on x64?

[ ]'s

---

### Post by ximian on 2006-11-26
> **kekojeep said:**
> I'm trying to compile latest Beryl from svn, but it seems that svn.beryl-project.org is offline? When i try 

svn co svn://svn.beryl-project.org/trunk/ beryl

I get an error saying it can't connect to svn.beryl-project.org

Any tips? Where can I find the source to compile it on x64?

[ ]'s
Same here when i "cd beryl/" then "svn update" i get svn: Unknown hostname 'svn.beryl-project.org', so i take it is down for some reason,been this way for a couple of days i think....anyone know more it would help alot...Thanks

---

### Post by hcteks on 2006-11-26
I'm kind of a nix newb, but i know enough to figure most stuff out. this has confused me though, i've added the lines to my sources.list, added the key, then sudo apt-get update just displays a list, i don't see it update/download/install anything? does someone want to dumb-up the install process for me? ](*,)

---

### Post by xfile087 on 2006-11-26
> **hcteks said:**
> I'm kind of a nix newb, but i know enough to figure most stuff out. this has confused me though, i've added the lines to my sources.list, added the key, then sudo apt-get update just displays a list, i don't see it update/download/install anything? does someone want to dumb-up the install process for me? ](*,)


Once you've done apt-get update you just need to do 

> sudo apt-get install beryl beryl-manager emerald-themes and it will install beryl

---

### Post by hcteks on 2006-11-27
Okay, it installed, but when I do beryl-manager, it loads up, shows the beryl splash screen, then logs me out? my computer is a HP dv2000 laptop, nvidia geforce go 6150, 100gb hdd, amd turion 64 x2

---

### Post by CowzRule on 2006-11-27
> **hcteks said:**
> I'm kind of a nix newb, but i know enough to figure most stuff out. this has confused me though, i've added the lines to my sources.list, added the key, then sudo apt-get update just displays a list, i don't see it update/download/install anything? does someone want to dumb-up the install process for me? ](*,)
You also needed to do```
sudo apt-get upgrade
```

---

### Post by kop316 on 2006-11-27
I got the transparency to work, but in soem of the videos, the windows pop out of the cube when it is rotated, and mine does not do that. Does anyone know what the issue is?

---

### Post by hikaricore on 2006-11-27
> **kop316 said:**
> I got the transparency to work, but in soem of the videos, the windows pop out of the cube when it is rotated, and mine does not do that. Does anyone know what the issue is?

The plugin that does that effect is called "A 3D World".  It should be included in the svn.  I've got it on my system.

---

### Post by kvonb on 2006-11-27
I added the repos at the head of this thread and got this:

```
Failed to fetch http://ubuntu.compiz.net/dists/edgy/Release.gpg  Could not connect to ubuntu.compiz.net:80 (195.14.0.203). - connect (111 Connection refused)
Failed to fetch http://ubuntu.compiz.net/dists/edgy/main-edgy/i18n/Translation-en_US.bz2  Could not connect to ubuntu.compiz.net:80 (195.14.0.203). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```I'm VERY confused, do I use the instructions at the top of this thread or the one near the end?

Thanks, KEv :)

EDIT: I just got a Beryl/Emerald update notification, but I'm a bit leary to update with those errors from apt-get update.  Also do I still need to install those extra things at the beginning?

EDIT2:

I guess I just remove the "ubuntu.compiz.net" repos as I no longer need these?

---

### Post by kvonb on 2006-11-28
UPDATE:

Went ahead and did the updates, all is working perfectly :)

The only problem I had is this (see attachment), which was solved by doing the "fix broken" in synaptic.

Many thanks for your work on this :)

---

### Post by hikaricore on 2006-11-28
Oh incase no one else noticed, beryl svn might be a little slow being updated.  The hard drive for the [http://beryl-project.org/](http://beryl-project.org/) site bit the dust on sunday.

---

### Post by trinaryouroboros on 2006-11-28
Hey I got Beryl by itself rockin, can someone relay a method to get transparency like svn working in 64-bit?

:confused:

---

### Post by darrenm on 2006-11-29
> **kop316 said:**
> I got the transparency to work, but in soem of the videos, the windows pop out of the cube when it is rotated, and mine does not do that. Does anyone know what the issue is?

Do you have an ATi card?

---

### Post by d3v1ant_0n3 on 2006-11-29
> **hikaricore said:**
> Just a note if anyone else noticed serious beryl slowdown when you updated, the desktop cube plugin now has a transparent cube option which gets enabled by default.  :)  It looks really sweet... but if you're using an integrated intel chipset like myself this drops you to about 5fps... roflmfao, took me a few days to figure out what the hell was wrong.  I also personally disabled the lighting option, not sure if this is new or not but I don't remember seeing it and it was killing me too.

--Aaron

I've found that if you turn the 'opacity during move' to around 75, and 'opacity when not moving' at 100, then turn the fade time right down, I don't get that much of a performance hit- it's not really noticable when scroll-wheel rotating, and it looks super pretty when manually rotating.

---

### Post by Treviño on 2006-11-30
**kvonb**, update emerald before...

---

### Post by Sailfish on 2006-11-30
No eye rolling.  I am very new to Ubuntu!  Editing the source list seems to be the first order of business.  There seems to be a lot there and most of it is commented.  I traced the links to see what was "live" and what wasn't...  Now I have decided I want to link to Trevino for my Beryl install.  What should my sources.lst look like once edited?  This could be a long and painfull process for me#-o

---

### Post by Sailfish on 2006-11-30
Ignore last post...  I got it figured out...  Sometimes I get a lazy and pray for help.

---

### Post by kvonb on 2006-12-02
OK, just got the latest updates to 0.1.3.  All works well, but the Beryl splash screen says 0.1.2!  It is a different colour, it's now orange instead of Blue, does this indicate a problem with the update?

Regards, KEv :)

---

### Post by Sailfish on 2006-12-02
I have Beryl up and going now with two issues.  Issue one is window transparency.  When I grab them by the title bar, they don't do it.  I suspect that there is a control in the Beryl Manager that I can't find.  Could someone point me the right way?  2nd is the Cube desktop.  I found the controls for this but am unable to generate a cube...  Pointers for this would be most welcome as well?  Good day all!

---

### Post by heartsmagic on 2006-12-03
Today i upgraded to beryl-svn via Treviño's repos, it is working charmy, thank you.

---

### Post by jbernardo on 2006-12-04
Thanks for the script! After finding out I needed to call it from outside a beryl dir, I was able to build beryl-* and emerald-* packages for my amd64, and they run fine!
My next step will be to see which of the reps have the source for aquamarine (or if there is a repository with the amd64 binary).
Thanks!

---

### Post by Treviño on 2006-12-04
To build aquamarine you should just have a "debian" directory for it... You could add one to your "./beryl/trunk/distro-specific-build-files-user" directory as is done for other packages...

---

### Post by eXisor on 2006-12-06
I'm getting a '404 not found' on all the 20061205 debs. Any idea what's up?

---

### Post by hikaricore on 2006-12-06
This happens every so often when the repository list doesn't link to the most recent versions of the packages.  If you absolutely can't stand not having the most bleeding edgy version of beryl installed you can simply download the files you need from: [http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/](http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/)

Otherwise wait till tomorrow and it should have been corrected by then.  :P

---

### Post by eXisor on 2006-12-06
hikaricore: Thanx for the explanation.

Waiting a day is no problem, just as long as it's not an all or nothing situation (i.e that some beryl packages upgraded but since the 404's did not the next reboot will kill beryl).

Thanx anyway.

---

### Post by hikaricore on 2006-12-06
> **eXisor said:**
> hikaricore: Thanx for the explanation.

Waiting a day is no problem, just as long as it's not an all or nothing situation (i.e that some beryl packages upgraded but since the 404's did not the next reboot will kill beryl).

Thanx anyway.

I've had 404's happen multiple times, only once did this actually mess up beryl and it was easily corrected by manually downloading the latest plugin package from the repository's http listing. :)

The problem with the repository update is gone now btw.

--Aaron

---

### Post by Treviño on 2006-12-06
Sorry again for this, but my update scripts (and the falcon repository builder) some times make me angry...
All has been fixed at about 5pm Gtm+1 time :P

---

### Post by eXisor on 2006-12-07
No sweat hikaricore & trevino. I exercised a bit of patience and got the updates after your fix.

Thanx, trevino, for providing this service.

---

### Post by hikaricore on 2006-12-07
Nooooo they fixed glxsnow!!!  now you have to toggle it instead of it starting automaticly... those bas****!

---

### Post by jb88 on 2006-12-07
Im new with ubuntu so can you please make it simple.
ive just added the info to the list file as instructed in post 1 of this thread. when i go to update it comes up with
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
ive copied and pasted exactly as instructed. im using Dapper (i think, the LTS verson)
any help would be appreciated.

---

### Post by orlandopozo on 2006-12-07
The Burn (Fire) effect is there

Beryl Setting Manager -> Animations -> Minimize Effect -> Burn

I am having problem with the window manager, the title bars disappeared.

I thought it was emerald, but emerald is running properly.

Any help?

---

### Post by orlandopozo on 2006-12-07
> **linuxmad said:**
> Treviño, 
Will you add the fire effect to your debs?? ...Please don't say no:-k

----

The Burn (Fire) effect is there

Beryl Setting Manager -> Animations -> Minimize Effect -> Burn

I am having problem with the window manager, the title bars disappeared.

I thought it was emerald, but emerald is running properly.

Any help?

---

### Post by foxy123 on 2006-12-08
> **orlandopozo said:**
> ----

The Burn (Fire) effect is there

Beryl Setting Manager -> Animations -> Minimize Effect -> Burn

I am having problem with the window manager, the title bars disappeared.

I thought it was emerald, but emerald is running properly.

Any help?
did you try:
```
killall emerald
emerald --replace &
```
it helps sometimes

---

### Post by adds2one on 2006-12-08
aptitude, apt-get and synaptic cannot find libldap-2.3-0 in your repository or in the uni.klu repository and your link to download it on the first page of this post is broken. 

Where else can I find this and is it neccessary?

---

### Post by mlw4428@gmail.com on 2006-12-08
I'm running Ubuntu Dapper and I tried your repositories and when doing the apt-get update I get the following error message:

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/dapper/Release](http://download.tuxfamily.org/3v1deb/dists/dapper/Release)  Unable to find expected entry  beryl-svn/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/Release](http://3v1n0.tuxfamily.org/dists/dapper/Release)  Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Here are my repository lists:

#SVN
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper beryl-svn
#END OF SVN

Could someone provide a fix? Would the Edgy ones work on Dapper? I upgraded to Edgy and didn't like it, so I downgraded. If not and Dapper isn't supported by this repository anymore are there other places to get the SVN repo? Thanks!

---

### Post by mlw4428@gmail.com on 2006-12-08
> **mlw4428@gmail.com said:**
> I'm running Ubuntu Dapper and I tried your repositories and when doing the apt-get update I get the following error message:

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/dapper/Release](http://download.tuxfamily.org/3v1deb/dists/dapper/Release)  Unable to find expected entry  beryl-svn/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/Release](http://3v1n0.tuxfamily.org/dists/dapper/Release)  Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Here are my repository lists:

#SVN
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper beryl-svn
#END OF SVN

Could someone provide a fix? Would the Edgy ones work on Dapper? I upgraded to Edgy and didn't like it, so I downgraded. If not and Dapper isn't supported by this repository anymore are there other places to get the SVN repo? Thanks!

The edgy repositories didn't work for me (same error as above). Can someone help me out with this? Thanks!

---

### Post by foxy123 on 2006-12-08
> **mlw4428@gmail.com said:**
> I'm running Ubuntu Dapper and I tried your repositories and when doing the apt-get update I get the following error message:

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/dapper/Release](http://download.tuxfamily.org/3v1deb/dists/dapper/Release)  Unable to find expected entry  beryl-svn/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/Release](http://3v1n0.tuxfamily.org/dists/dapper/Release)  Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Here are my repository lists:

#SVN
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) dapper beryl-svn
#END OF SVN

Could someone provide a fix? Would the Edgy ones work on Dapper? I upgraded to Edgy and didn't like it, so I downgraded. If not and Dapper isn't supported by this repository anymore are there other places to get the SVN repo? Thanks!

Dapper packages do not work due to some dependency problem. I am not sure if Treviño still compiles them. You'd better use his script to build them yourself. It is very easy. You just run the script and that's it. It does not compile the last package (a decoration manager for Metacity) due to unmet dependency.

---

### Post by mlw4428@gmail.com on 2006-12-08
What dependencies do I need to build it for myself using the script?

---

### Post by foxy123 on 2006-12-08
> **mlw4428@gmail.com said:**
> What dependencies do I need to build it for myself using the script?

frankly speaking I do not remember. Try to run it and then figure out what to install. Or maybe Treviño could help.

---

### Post by Infomaniac on 2006-12-10
Hey everyone

I just saw on the Beryl project site that they´ve released 0.1.3 officially yesterday.

I was using the 0.1.3 that I got from this repo. 

My question is: Will it automatically upgrade to this official stable release?

Thanks in advance

---

### Post by Get_Ya_Wicked_On on 2006-12-10
No. It is a SVN repo...

---

### Post by mlw4428@gmail.com on 2006-12-10
Does anyone out there know where to get svn builds of Beryl for Dapper? If not could someone compile em? I'm working on it...but I've got too many damned dependency issues that I'm trying to nail down. 

If someone already has this setup would you post a deb somewhere or PM me and I'll be glad to post it. Thanks!

---

### Post by kvonb on 2006-12-12
....erm

How come I can't change Emerald themes since the last update?

Methinks something went bad :(.

---

### Post by hikaricore on 2006-12-12
I've noticed this for the last 2 updates I've done.  I thought it was because I install heilodor, but alas it's not just me.

---

### Post by kvonb on 2006-12-12
It seems they changed it to be more like Windows, you have to change the theme, click on "apply", then restart X!

Oh joy!

---

### Post by hikaricore on 2006-12-13
> **kvonb said:**
> It seems they changed it to be more like Windows, you have to change the theme, click on "apply", then restart X!

Oh joy!

No no no.... windows crashes when you hit apply.

:)

But seriously, I've actually tried that, to no avail.  I think there might be an issue with the build we're using right now.

---

### Post by kvonb on 2006-12-13
OK, now the cube ends and Skydome have vanished!  I don't get it, do they just forget and leave bits out?  I'd hate to see them fix a car: Oh we got the wipers working but we forgot to put the engine back in!

Switched back to non-SVN, all fixed :)

---

### Post by Shadowline on 2006-12-14
kvonb and anyone else that runs into this.... Enable the png and svg plugins to get your skydome and cube images back.
:-D

---

### Post by kvonb on 2006-12-14
One problem that I have had with the SVNs and also now with the "Official" release, is that the menu and text pop-ups on web pages appear UNDERNEATH the browser window and I can't click on them!  It is a real nuisance because it makes it unusable.  I have to use beryl-manager to reload the window manager a few times to fix it.  It also happens with ALL the menus, they appear below the current window not just Firefox :confused:.  I believe this started with the last 3 updates.  Any ideas anyone?

Regards, Kev :)

---

### Post by Treviño on 2006-12-14
> **Shadowline said:**
> kvonb and anyone else that runs into this.... Enable the png and svg plugins to get your skydome and cube images back.
:-D
That's the right solution... New png plugin should be selected; and svg if you use svg graphics too...

Regarding **dapper**, if anyone has time/wish of making debs using my makedebs script, simply he can use it and then contact me to share the files to be hosted...

Bye!

---

### Post by foxy123 on 2006-12-14
> **Treviño said:**
> That's the right solution... New png plugin should be selected; and svg if you use svg graphics too...

Regarding **dapper**, if anyone has time/wish of making debs using my makedebs script, simply he can use it and then contact me to share the files to be hosted...

Bye!

I use your script on Dapper, but I am not sure if the debs will be alright as I think they should be built in a clean environment. However I can send you them for testing. Let me know. My last build is fron Dec 10.

---

### Post by Treviño on 2006-12-14
Could you come on #ubuntu ?
If there call "Trevinho"; I'll be there; you could send me the files via dcc... Or Msn if you prefer...

---

### Post by foxy123 on 2006-12-14
> **Treviño said:**
> Could you come on #ubuntu ?
If there call "Trevinho"; I'll be there; you could send me the files via dcc... Or Msn if you prefer...

ok, I'm there

---

### Post by Treviño on 2006-12-14
Me Too.. If I don't reply, send the files via DCC anyway ;)

---

### Post by foxy123 on 2006-12-14
> **Treviño said:**
> Me Too.. If I don't reply, send the files via DCC anyway ;)

I tried twice to no avail

---

### Post by mrastas on 2006-12-14
Hi and thanks for the repos.

Have you guys tried to change resolution with xrandr while running beryl?

It does not do well. :confused: 

I really need that to switch my resolution on laptop, so that i can connect basic projector on my vga output and show my beryl effects in a business meeting. 8)

---

### Post by foxy123 on 2006-12-16
I submitted yesterday the beryl-svn debs to Treviño. If you want to try them, please add
```
 deb http://download.tuxfamily.org/3v1deb dapper beryl-svn
```
in your sources.list. Please let me know if they work for you as I am not sure.

---

### Post by eXisor on 2006-12-27
Anyone else have no panel shadows with the latest update?

Is this just a default setting they changed? If so, where do i go to change it back?

---

### Post by foxy123 on 2006-12-27
> **eXisor said:**
> Anyone else have no panel shadows with the latest update?

Is this just a default setting they changed? If so, where do i go to change it back?

I think it depends on the theme. But I use a Dec. 25 snapshot at the moment.

---

### Post by eXisor on 2006-12-27
Hmm. Tried that but it doesn't appear to be theme dependent. It's the 27/12 update that doesn't cast panel shadows onto the desktop anymore. 

Windows still cast and everything else seems fine.

Anyone else tried 27/12?

---

### Post by foxy123 on 2006-12-27
> **eXisor said:**
> Hmm. Tried that but it doesn't appear to be theme dependent. It's the 27/12 update that doesn't cast panel shadows onto the desktop anymore. 

Windows still cast and everything else seems fine.

Anyone else tried 27/12?

yes, I've just compiled from svn and panel shadow is gone. To get  it back, go to Beryl Settings Manager/Visual Effects/Window Decoration/Misc. Options/Appearance and tick Draw shadows on panel-type windows.

---

### Post by eXisor on 2006-12-27
foxy123:

Cheers, that's the setting!

---

### Post by klep on 2007-01-08
> **foxy123 said:**
> yes, I've just compiled from svn and panel shadow is gone. To get  it back, go to Beryl Settings Manager/Visual Effects/Window Decoration/Misc. Options/Appearance and tick Draw shadows on panel-type windows.

thanks foxy, i came looking for this thread to see whether anyone else had also lost their panel shadows and am happy to see someone has already provided the solution!

---

### Post by el-sio on 2007-01-09
Hi there !

I am desperately trying to get Beryl working on my edgy pPC arch, but with the regular packages (not SVN) I get this error while launching beryl-settings :

```
el-sio@rivendell:~$ beryl-settings 

** ERROR **: no d_ for a_active_plugins
aborting...
Abandon (core dumped)

```

I decided to go for the SVN version which might have solved the problem so I tried to use your repo but I receive the following error :

```
Impossible de récupérer http://download.tuxfamily.org/3v1deb/dists/edgy/Release  Unable to find expected entry  beryl-svn/binary-powerpc/Packages in Meta-index file (malformed Release file?)
```

Is it a problem on my side or on the repo ? I am kind of a newbe (Ok not "quite" let's say completely) but I think pPC architecture can be easily forgotten during an update (rhaa exotic arch using bastards ;p ).

Thanks for your help !

---

### Post by eXisor on 2007-01-13
Today's update seems to have killed beryl settings manager. Beryl and Emerald are both working, but I can't get to the beryl settings.

This is the message I get in xsession-errors:

```
beryl: Plugin 'snap' can't be activated because plugin 'wobbly' is already providing feature 'edgeresistance'
Couldn't initialise snap. This should not happen!
```

Anyone else getting this?

---

### Post by L3oN on 2007-01-13
Fix it trying to install " beryl-settings-bindings " (I hope ;) )

---

### Post by baobab68 on 2007-01-14
I've added Trevino's SVN Beryl Repository to my sources.list recently and I've had a couple of successful updates.

Today's update however hasn't worked. It seems like the following file in the update was corrupt:

W: Failed to fetch [http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/beryl-plugins_0.1.5+svn20070114-r2648+3v1ubuntu0_i386.deb](http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/beryl-plugins_0.1.5+svn20070114-r2648+3v1ubuntu0_i386.deb)
  Size mismatch


I downloaded the .DEB file manually and tried to install but GDebi reports:

"The package might be corrupted or you might not have permission to open the file"

Can anyone more experience in Ubuntu please tell me if there is a way to revert the latest update? I've switched back to Metacity in the meantime as Beryl is currently dead without plugins.

Trevino - has there been a compile problem concerning Beryl-Plugins?

Regards and thanks
bao

---

### Post by cgrenier on 2007-01-14
I have the same problem.  Will it at least be fixed by the next update?

---

### Post by baobab68 on 2007-01-14
I have been wondering if perhaps Trevino's repository is all scripted and maybe if the next SVB update compiles cleanly it will all work again.

I miss my Beryl   :-)

Is there no way to revert the latest update using some aptitude feature?

---

### Post by int on 2007-01-14
> **baobab68 said:**
> I have been wondering if perhaps Trevino's repository is all scripted and maybe if the next SVB update compiles cleanly it will all work again.

I miss my Beryl   :-)

Is there no way to revert the latest update using some aptitude feature?

Trevino's repository for beryl is working again..

---

### Post by Treviño on 2007-01-14
Sorry for this... My uploading script maybe failed :P

---

### Post by foxy123 on 2007-01-14
> **Treviño said:**
> Sorry for this... My uploading script maybe failed :P

Have you fixed it? I had to put beryl-settings-bindings into PRIOPKGS to make it build beryl-settings, but I am not sure if there are any other changes needed.

---

### Post by mid_night gypsy on 2007-01-14
Foxy123
 Yes, The problems is fixed.You need to install Python 2.5 min. and Beryl settings Bindings.If windows don't wobbly,go to BSM window management  and turn off snapping windows.
                                                                                      Hope this help,gypsy

---

### Post by baobab68 on 2007-01-14
Trevino - after a quick couple of updates this morning, and turning off the snap plugin, all is good again.

Thanks for the prompt response.

bao

---

### Post by Hendrixski on 2007-01-14
I've been playing around with Beryl all day, I first installed it a few months ago and it would always crash.  Today I updated everything in beryl and it would crash before it started, so I updated my ATI drivers, and now it works pretty well.  I just can't get it to switch desktops for some odd reason.

Would I benefit from adding any other updates?

---

### Post by eXisor on 2007-01-14
L3on: Thanx, that did it.

---

### Post by lotacus on 2007-01-15
Um, I had 1.3 installed and it wouldn't work with Edgy AMD64+ATI. Then I installed 1.4 which wasn't in any repo's at the time and everything worked nice. So now I see 1.5 in the repo and wondering if anyone has a changelog.

---

### Post by dgorchak on 2007-01-18
Maybe someone ran into this problem? I'm running Feisty (all latest packages), luckily I found **taskbar-compiz** package for KDE that replaces the default one. It's a modified taskbar plugin for kicker that doesn't display windows from all viewports (original one does).
This package is from 3v1n0's repository, so ... maybe I can ask here? Adding this plugin to kicker crashes it ... and I have no idea how to fix this problem.


Can it be because of version mismatch?

taskbar-compiz/edgy uptodate 0.1+3v1ubuntu0
kdebase-bin/feisty uptodate 3.5.5a.dfsg.1-1ubuntu18

---

### Post by dhayashi on 2007-01-18
Greetings,

Its been a while since i updated my beryl install - but today I tried installing the updates and got this message after most of the packages got installed.

> (Reading database ... 106041 files and directories currently installed.)
Preparing to replace beryl-plugins 0.1.3~0beryl1 (using beryl-plugins_0.2.0+svn20070118-r2838+3v1ubuntu0+svn20070118-r2839+3v1ubuntu0_i386.deb) ...
Unpacking replacement beryl-plugins ...
dpkg: error processing beryl-plugins_0.2.0+svn20070118-r2838+3v1ubuntu0+svn20070118-r2839+3v1ubuntu0_i386.deb (--install):
 trying to overwrite `/usr/lib/beryl/libdbus.so', which is also in package beryl-dbus
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 beryl-plugins_0.2.0+svn20070118-r2838+3v1ubuntu0+svn20070118-r2839+3v1ubuntu0_i386.deb

it then errors out - any ideas on how to force this package to install - i'm guessing its getting hung up on the overwrite. ](*,) 

Thanks

dhayashi

---

### Post by brazzmonkey on 2007-01-19
same here

---

### Post by telperion on 2007-01-19
before update to 0.2.0  uninstall 
**beryl-dbus**

now dbus is in beryl-plugins package, uninstall beryl-dbus, then upgrade

---

### Post by brazzmonkey on 2007-01-19
alrigthy then. this does work. thanks telperion !
beryl-settings seems broken, though.

---

### Post by SIZABANTU on 2007-01-19
I have 64BIT system AMD ,were do i get the svn packages :-k  Thank you guys  :mrgreen:

---

### Post by eXisor on 2007-01-20
trevino: 

I'm getting an error in the mailcap file (the emerald entry) when I use some apps (wxdfast is one) . 

Has this been reported before? If so, apologies for the nag, but the matter persists.

The beryl bug system ticket is closed and reckons there is something wrong with the way you package/create the .deb.

Ticket #546 - Invalid lines in /etc/mailcap on Ubuntu [http://bugs.beryl-project.org/ticket/546](http://bugs.beryl-project.org/ticket/546)

Could you please take a look and maybe respond to the ticket is it isn't .deb related?

---

### Post by Treviño on 2007-01-20
That's not a my bug... It's due to beryl official debian data... It should have been fixed on past days, but I'm not sure of it (no problems in kubuntu :P)...

Regarding amd64 debs, there are some on [http://forum.beryl-project.org/viewtopic.php?f=43&t=955](http://forum.beryl-project.org/viewtopic.php?f=43&t=955)

---

### Post by eXisor on 2007-01-20
Trevino:

[quote='Trevino'](no problems in kubuntu [/quote]

So your /etc/mailcap file in kubuntu is hunky dory? (On gnome a visual check of the affected lines clearly shows them to be borked, but since I don't have x/kubuntu I can't easily check those).

[quote='Trevino']It's due to beryl official debian data[/quote]
 
Hmmm. I think I see your point. Correct me if I am wrong, but I'd guess the appropriate string for insertion into the mailcap file is wrong/broken somewhere in a file, and you're saying it isn't your file, that you take it straight from their svn.

Tell you what I'll do, I'll download the source from their svn and see if i can find the string.

Edit: Update:

I found the incorrect string. It's in both occurrences (is the entire content of actually) of a file called emerald.mime. It seems to be used for the debian build, as you said, but I don't know why it exists in two places.

The contents of emerald.mime should change to 
```
application/x-emerald-theme; nametemplate=%s.emerald
```

I updated the bug report with this data, so hopefully it'll be sorted soon. Thanx anyway Trevino. Great service you're doing us here.

---

### Post by dgorchak on 2007-01-26
Got this nasty problem again

> $ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in <module>
    import berylsettings
ImportError: No module named berylsettings


---

### Post by pwk on 2007-01-26
beryl-settings fix (worked for me):

sudo ln -s /usr/lib/python-support/beryl-settings-bindings/python2.5/berylsettings.so /var/lib/python-support/python2.4/berylsettings.so

---

### Post by dgorchak on 2007-01-27
> **pwk said:**
> beryl-settings fix (worked for me):

sudo ln -s /usr/lib/python-support/beryl-settings-bindings/python2.5/berylsettings.so /var/lib/python-support/python2.4/berylsettings.so

Thank you man, but ... 
```
$ sudo ln -s /usr/lib/python-support/beryl-settings-bindings/python2.5/berylsettings.so /var/lib/python-support/python2.4/berylsettings.so
ln: creating symbolic link `/var/lib/python-support/python2.4/berylsettings.so' to `/usr/lib/python-support/beryl-settings-bindings/python2.5/berylsettings.so': File exists

```

I've searched through Beryl forums, but this didn't help me. I got this error ~2-3 weeks ago and replaced beryl-settings with some old version from the repo. Now there is no way to repeat that fix - the working file is replaced with some new versions :confused:

---

### Post by pwk on 2007-01-27
There are some other suggestions here: [http://justanothertechblog.blogspot.com/2007/01/quick-fix-for-beryl-svn-settings.html](http://justanothertechblog.blogspot.com/2007/01/quick-fix-for-beryl-svn-settings.html)

---

### Post by dgorchak on 2007-01-27
Thanks! That worked, but a bit not as described.
I've copied berylsettings.so to /var/lib/python-support/python2.5/ (not 2.4)

---

### Post by megamaced on 2007-01-28
First of all, thanks for the Dapper SVN repository. The latest version (0.2.0 at time of writing) is easily the most stable yet.

Is it at all possible to include Aquamarine & Heliodor in the Dapper SVN repo?
Or can I use the script in the first thread to compile them for me?

Thanks

---

### Post by baobab68 on 2007-01-28
I've been on hols for a couple of weeks. Updated to the latest Beryl from Trevino's repo this morning - I'm now on 0.2 but I can no longer find the Tile plugin. Did it not make the cut for 0.2?

bao

---

### Post by telperion on 2007-01-29
> **megamaced said:**
> First of all, thanks for the Dapper SVN repository. The latest version (0.2.0 at time of writing) is easily the most stable yet.

Is it at all possible to include Aquamarine & Heliodor in the Dapper SVN repo?
Or can I use the script in the first thread to compile them for me?

Thanks

[http://forum.ubuntu-it.org/index.php/topic,45451.0.html](http://forum.ubuntu-it.org/index.php/topic,45451.0.html)

---

### Post by dgorchak on 2007-01-29
After the last update I got new problem - no plugins loading :(

$ beryl-settings
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/lib3d.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libanimation.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libannotate.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libbench.so' plugin
libberylsettings: Couldn't get vtable from '/usr/lib/beryl/libblurfx.so' plugin

and so on? My bad or smth went wrong?

---

### Post by foxy123 on 2007-01-29
> **megamaced said:**
> First of all, thanks for the Dapper SVN repository. The latest version (0.2.0 at time of writing) is easily the most stable yet.

Is it at all possible to include Aquamarine & Heliodor in the Dapper SVN repo?
Or can I use the script in the first thread to compile them for me?

Thanks

Unfortunately both require dev libraries, which I do not have on my system.

---

### Post by Guillaumeb on 2007-01-29
OK beryl is all messed up again after today's numerous updates, Now I get a package broken and I have no idea which one it is. i suspect it is Beryl-Plugin-extra from what I observe from the synaptic manager

The update notifier told me to run apt-get install -f I did so, to receive the following error

root@laptop:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  python-all python2.5 python2.5-minimal
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  beryl-plugins-extra
The following NEW packages will be installed:
  beryl-plugins-extra
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/83.6kB of archives.
After unpacking 270kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 104367 files and directories currently installed.)
Unpacking beryl-plugins-extra (from .../beryl-plugins-extra_0.2.0+svn20070129-r3400+3v1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/beryl-plugins-extra_0.2.0+svn20070129-r3400+3v1ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/beryl/libshowdesktop.so', which is also in package beryl-plugins-nonfree
Errors were encountered while processing:
 /var/cache/apt/archives/beryl-plugins-extra_0.2.0+svn20070129-r3400+3v1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


When opening Synaptic it says I have one broken package. I go to the filter, check the Broken box, click on OK and then nada, I dunno which package is broken. I mean which package beryl took  the pleasure to break.

Anyone encountered this error?

---

### Post by svasie on 2007-01-30
Had the same problem. After updating beryl packages it wouldn't find any plugins.

Solved it uninstalling and then installing again all beryl related packages.

---

### Post by xplode_me on 2007-01-30
Latest SVN goodness: [http://digg.com/linux_unix/Beryl_s_new_3D_animations](http://digg.com/linux_unix/Beryl_s_new_3D_animations)

---

### Post by telperion on 2007-01-30
> **foxy123 said:**
> Unfortunately both require dev libraries, which I do not have on my system.


Patch to compile Heliodor on Dapper
files :
trunk/heliodor/configure.ac configure.ac
trunk/distro-specific-build-files/heliodor/debian/control


```
diff ~/beryl/trunk/heliodor/configure.ac configure.ac ~/mc-trunk/trunk/heliodor/configure.ac
25c25
<             libmetacity-private >= 2.15.21 \
---
>             libmetacity-private \

diff ~/beryl/trunk/distro-specific-build-files/heliodor/debian/control ~/mc-trunk/trunk/distro-specific-build-files/heliodor/debian/control
5c5
< Build-Depends: debhelper (>= 5), cdbs, autotools-dev, pkg-config, beryl-dev, libgtk2.0-dev (>= 2.8.0), libxrender-dev, libwnck-dev, libpango1.0-dev, libgconf2-dev, libmetacity-dev (>= 2.15.21), libgnomeui-dev, libgnome-desktop-dev, libgnome-window-settings-dev
---
> Build-Depends: debhelper (>= 5), cdbs, autotools-dev, pkg-config, beryl-dev, libgtk2.0-dev (>= 2.8.0), libxrender-dev, libwnck-dev, libpango1.0-dev, libgconf2-dev, libmetacity-dev, libgnomeui-dev, libgnome-desktop-dev
```

---

### Post by megamaced on 2007-01-30
Aquamarine is the obvious choice for KDE users as it integrates far better then Emerald. But what benefits does Heliodor bring for GNOME users? Is Heliodor better then Emerald?

---

### Post by Guillaumeb on 2007-01-30
Solution that worked for me:

Uninstall/reinstall

Go to Synaptic Manager
Search for beryl
mark all components for uninstallation
Apply
Reboot
Go to Synaptic Manager
Search for beryl
Mark all components for installation
Apply
Reboot

---

### Post by baobab68 on 2007-01-31
Hi all

I sorted out my tile problem and my settings manager problem with a remove of all Beryl packages, reboot, reinstall all Beryl pacakages, reboot.

Now, however, I notice a new Beryl feature and am not sure where to turn it off.

When I point the mouse to the title bar of a window, a small thumbnail of the window appears at the mouse pointer. I know this is meant to happen when I point to a minimised window, but I didn't think it should happen for a displayed window...

Any suggestions?

bao

---

### Post by foxy123 on 2007-01-31
I have to stop building Dapper beryl-svn packages for Trevino's repository. The beryl-settings-bindings now requires higher version of python-support than installed in Dapper. Therefore the script fails now after building beryl-core.

---

### Post by megamaced on 2007-01-31
> **foxy123 said:**
> I have to stop building Dapper beryl-svn packages for Trevino's repository. The beryl-settings-bindings now requires higher version of python-support than installed in Dapper. Therefore the script fails now after building beryl-core.

Noooooo!!!! Oh god kill me now.....!!!! :(

---

### Post by Treviño on 2007-02-01
Foxy it should be fixed now, retry again :P

---

### Post by foxy123 on 2007-02-02
> **Treviño said:**
> Foxy it should be fixed now, retry again :P

was it fixed in the script or in svn? I will try over weekend.

---

### Post by foxy123 on 2007-02-02
No I cannot build it:
```
dpkg-checkbuilddeps: Unmet build dependencies: python-support (>= 0.5.3)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

Problems occurred while building beryl-settings-bindings packages... Continue Building?
 [Y/n]: Y
beryl-core built OK
 
```

---

### Post by Milamber_Cubed on 2007-02-05
Hi!

I'm trying to use the script on the first post to compile debs for dapper (I have installed python 2.5 into /python2.5) but keep getting the following error:

```

Building beryl-core...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: macro `AM_PATH_PYTHON' required but not defined
autoreconf: aclocal failed with exit status: 1

Problems occurred while building beryl-core packages... Continue Building?
 [Y/n]: n
BUILD FAILED for beryl-core

```

Any chance you could point me in the right direction? I'm sure there is just some package that I haven't installed.

---

### Post by Treviño on 2007-02-05
Try to install some python-dev packages (and maybe python-support or something else...); I unfortunately don't know the exact package :|

Foxy, maybe you could try to build it again (there are official builds for dapper, so I think it's compilable)... However if you've installed the python-support package, and you've still compilation problems you can always force the compilation editing the file beryl/trunk/distro-specific-build-files/beryl-set
tings-bindings/debian/control removing or changing the "python-support (>= 0.5.3)" string.

---

### Post by Milamber_Cubed on 2007-02-05
> **Treviño said:**
> Try to install some python-dev packages (and maybe python-support or something else...); I unfortunately don't know the exact package :|

Foxy, maybe you could try to build it again (there are official builds for dapper, so I think it's compilable)... However if you've installed the python-support package, and you've still compilation problems you can always force the compilation editing the file beryl/trunk/distro-specific-build-files/beryl-set
tings-bindings/debian/control removing or changing the "python-support (>= 0.5.3)" string.

In case it helps... 

I managed to get past the error I was getting before, having had a look in the python.m4 file, but am now stuck with other errors :(. Anyway.... to the point

I downloaded the pythion 2.5 tarball - [http://www.python.org/ftp/python/2.5/Python-2.5.tgz](http://www.python.org/ftp/python/2.5/Python-2.5.tgz) - and then did the following:

```

tar xzf Python2.5.tgz
cd Python2.5
./configure --prefix=/python2.5
make
make install

```

it all went without a hitch. I don't know if there is some way for me to package this up as a deb, but I see no reason for it not working for anyone else.

After examining the /usr/share/aclocal*/python.m4 files, if found that if you compile and install python2.5 to a non-standard location (/python2.5 in my case) then you can force the configure scripts to find that version of python by setting an environment variable:

```

export PYTHON=/python2.5/bin/python2.5

```

and that might solve any python dependency problems.

Still cant get beryl to compile, but thought this might be helpful.... maybe not :)

---

### Post by Tryke on 2007-02-13
> **Milamber_Cubed said:**
> Hi!

I'm trying to use the script on the first post to compile debs for dapper (I have installed python 2.5 into /python2.5) but keep getting the following error:

```

Building beryl-core...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: macro `AM_PATH_PYTHON' required but not defined
autoreconf: aclocal failed with exit status: 1

Problems occurred while building beryl-core packages... Continue Building?
 [Y/n]: n
BUILD FAILED for beryl-core

```

Any chance you could point me in the right direction? I'm sure there is just some package that I haven't installed.

I ran into this, and the problem was that when I installed automake, apt-get installed 1.4 by default. remove that, and install automake1.9 to fix the problem.

---

### Post by ernstblaauw on 2007-03-20
Is it corect, that also fo rEdgy no new updates appear?
If so, does someone know another repo for Beryl svn?

---

### Post by Treviño on 2007-03-20
The repo is actually alive and working but beryl has now moved to git, and devs doesn't provide updates since some days, so I can't upload no new packages...
Just stay tuned! :)

---

### Post by ernstblaauw on 2007-03-21
> **Treviño said:**
> The repo is actually alive and working but beryl has now moved to git, and devs doesn't provide updates since some days, so I can't upload no new packages...
Just stay tuned! :)
Thanks for all your work :-)! I'll wait!

---

### Post by Dougga on 2007-03-30
This looks like a great resource, thanks.
I did run into a problem though.
Take a look...

Checking svn for updates...
At revision 4514.

Building beryl-core...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: macro `AM_PATH_PYTHON' required but not defined
aclocal: configure.ac: 22: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1

Any ideas on how to fix this?
Thanks

---

### Post by megamaced on 2007-04-06
Just like to say thanks to whoever upgraded Beryl to 0.3 in the Dapper GIT repo!

---

### Post by hype on 2007-05-17
I cant find a post concerning Feisty's repo.

After todays update from trevi's repo (beryl-plugins and beryl-plugins-data, or something like that), i get an error when loading beryl:
```
** (beryl-manager:5883): WARNING **: Beryl a reçu un signal de terminaison 11
Avertissement du gestionnaire de fenêtres : «  » trouvé dans la base de données de configuration n'est pas une valeur correcte pour la combinaison de touches « toggle_shaded »
```

 I then removed ~./beryl, and beryl loads fine. But i get HUGE lags: movement are not fluid like just minutes before.
 And when trying to activate the "Performance" plugin to see ho much fps i get, beryl crashes, and gives this error, again.

_EDIT: Quick translation of the error:_
"WARNING: Beryl received a terminate signal 11
Warning from window manager: «  » found in the configuration database isnt a valid value for the key combo « toggle_shaded »"

Edit2:
[B]Well, i did remove ~/.beryl and re-did my previous config. After a reboot all seems quite good; i also noticed some new goodness. :)
Works great now, thank for these packages![/B]

---

### Post by Paul S on 2007-05-25
This is a great script, thanks for providing it.

Maybe something is changed, but it fails now:

paul :~/Desktop$ bash ./makedebs
There are problems while retrieving the beryl items list; exiting...

Is there something I can do to get it working?

---

### Post by foxy123 on 2007-05-25
> **Paul S said:**
> This is a great script, thanks for providing it.

Maybe something is changed, but it fails now:

paul :~/Desktop$ bash ./makedebs
There are problems while retrieving the beryl items list; exiting...

Is there something I can do to get it working?

Beryl development has stopped. We all are waiting for commcomp - Community Compiz

---

### Post by nemanaldin on 2007-05-26
hi
i installed this version of beryl but when i rotate a cube beryl crashed and i should restart my gdm 
and this version of beryl use 100% of my cpu memory when it run 
any body can help me
thanks and sorry for my bad english

---

### Post by nemanaldin on 2007-05-29
nobody here to help me

---

### Post by era506 on 2007-08-03
Hi!
I want to try the svn version of beryl so I can use the widget plug in. So, I installed it using treviño's repo but it crashes when I try to modify something in the beryl settings, then, even if I re-start X it won't work any more. 
I have searched all day (I mean all day, since I woke up in the morning to right now!) in this forums and other websites, I have tried every "solution" I find here or there but I can't get it to work. How can I do it? Can someone explain me how? (I'm not too newbie, been using ubuntu for almost a year)
I have Ubuntu Feisty, Nvidia geforce 7300gs. I'm desperate! 
Thanks in advance!

---

### Post by Paul S on 2007-08-04
> **era506 said:**
> Hi!
I want to try the svn version of beryl so I can use the widget plug in. So, I installed it using treviño's repo but it crashes when I try to modify something in the beryl settings, then, even if I re-start X it won't work any more. 
I have searched all day (I mean all day, since I woke up in the morning to right now!) in this forums and other websites, I have tried every "solution" I find here or there but I can't get it to work. How can I do it? Can someone explain me how? (I'm not too newbie, been using ubuntu for almost a year)
I have Ubuntu Feisty, Nvidia geforce 7300gs. I'm desperate! 
Thanks in advance!

You should switch to compiz-fusion, using Trevino's repository.  A lot of bugs have been fixed in compiz-fusion, whereas beryl was abandoned at the last version.  Development is continuing under the name compiz-fusion .. see opencompositing.org for info.

HTH

---

### Post by fooman on 2007-08-04
> **era506 said:**
> Hi!
I want to try the svn version of beryl so I can use the widget plug in. So, I installed it using treviño's repo but it crashes when I try to modify something in the beryl settings, then, even if I re-start X it won't work any more. 
I have searched all day (I mean all day, since I woke up in the morning to right now!) in this forums and other websites, I have tried every "solution" I find here or there but I can't get it to work. How can I do it? Can someone explain me how? (I'm not too newbie, been using ubuntu for almost a year)
I have Ubuntu Feisty, Nvidia geforce 7300gs. I'm desperate! 
Thanks in advance!

i had similar issues.

using synaptic,  i searched for beryl and uninstalled all beryl/emerald packages.

then in my home directory, i deleted the *.beryl* folder.

back to synaptic...reinstalled beryl, emerald, and beryl-manager

all was working fine after that.  :)

---

### Post by Lolo Uila on 2007-11-05
> **Paul S said:**
> This is a great script, thanks for providing it.

Maybe something is changed, but it fails now:

paul :~/Desktop$ bash ./makedebs
There are problems while retrieving the beryl items list; exiting...

Is there something I can do to get it working?

So, is there a way to fix this problem. I have tried Compiz-Fusion and it's crap! It's really slow and laggy compared to Beryl, and the settings manager is terrible.

I'd really like to try and compile my own git version of Beryl from the latest/last sources, but I don't know how. I'd really appreciate some help on this.

Thanks, Tim

---

