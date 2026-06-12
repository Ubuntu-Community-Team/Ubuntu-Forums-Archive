---
title: "HOWTO Keep Up To Date on Dialup Internet"
date: 2006-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by golfbuf on 2006-06-15
[SIZE="3"]**HOWTO Keep Ubuntu Dapper Up To Date on Dialup Internet**[/SIZE]

I find trying to keep my Ubuntu up to date using a dialup internet connection a challenge.  My ISP has a disconnect rule that cuts me off after 3 hours.  When we have some really big updates, like openoffice.org or the kernel, I have difficulty finding time to get them downloaded.  Also, when a new version is issued, it takes days of downloading to upgrade.  I've developed some scripts to improve my dialup connection issues that enable me to leave my pc on line overnight, downloading unattended.  I usually can download about 130 MB each night, so have been able to keep up with dapper development.  In the morning, all I have to do is open a terminal and enter "sudo apt-get dist-upgrade" and all the packages are already there.

While the various dialers (kppp, wvdial, pppconfig, network connector) claim to have the ability to reconnect, my experience is that this feature fails regularly.  I've used my experiences to create some scripts that work for me to deal with disconnects and enable me to download new packages and updates overnight.  These scripts are presented in this HOWTO.

The general thrust behind these scripts is they always are checking for that undetected disconnect or dead connection, and when it's found, they kill the connection and start over.

[SIZE="3"]**PREPARATION**[/SIZE]
 
This wiki assumes you have a working modem.  If not, check out the DialupModemHOWTO ubuntu wiki page for tips.  I've always found the best help comes from using [linmodems.org]("http://www.linmodems.org") mailing list.

I presume you are familiar with wvdial and have used "sudo wvdialconf /etc/wvdial" to create your configuration file in /etc/wvdial.conf.  If not, try "man wvdial|wvdialconf|wvdial.conf" for help.

We need a way to monitor internet activity.  For KDE, I prefer kmodemlights, which is available on kde-apps.org.  My dapper package should be available here [ATTACH]11285[/ATTACH].  For gnome, it's possible to use the System Monitor, with Network checked in the properties dialog.

I use sudo a lot, so have edited /etc/sudoers to change the last line from:
 
%admin ALL=(ALL) ALL

to:

%admin ALL=(ALL) NOPASSWD: ALL

This makes it possible to act as root without having to enter my password each time.  This applies to the scripts I use, which have lines like "sudo wvdial" in them.  Be aware that this action weakens the security of your system by making it more vulnerable to any admin user mistakenly damaging the system.  So, if security concerns you, don't use these tips.

[SIZE="3"]GETTING A RELIABLE CONNECTION[/SIZE]

I use wvdial to connect and created a script to reconnect if disconnected.  In my experience, this is better than relying on any of the various network tools (wvdial, pon, network connection, kppp).  A primary issue I encounter in linux is the inability for pppd to recognize disconnects.  It may be caused by the modem driver or perhaps pppd itself.  These scripts help to recognize disconnects as well as redial.

First, edit /etc/ppp/options and select:

lcp-echo-interval 17
lcp-echo-failure 3

These will assure that pppd will die if something disconnects your modem for 3 successive echo attempts, spaced 17 seconds apart.

Next, since wvdial sometimes tries to reconnect and other times does not, we will use it in a script, rather than by itself.  So, it's better to make it give up on everything.  Edit /etc/wvdial.conf and add:

Abort on Busy = true
Abort on No Dialtone = true
Auto Reconnect = false
Dial Attempts = 1

If you are using a conexant modem, also add this to your /etc/wvdial.conf:

Dial Command = ATW2DT

If you are using a smartlink (slmodem) modem, you may need to add this to your /etc/wvdial.conf:

Stupid Mode = true

Now, create this script named "dialer" in your ~/scripts directory:

<<<<<<<<< script "dialer" starts on next line >>>>>>>>>>>>>>>
#!/bin/bash

SUCCESS=1

while [ $SUCCESS -eq 1 ] ; do

  until ( netstat -i | grep ppp ) ; do
    # first kill any leftover or hung wvdial processes
    pidof wvdial && sudo killall -s KILL wvdial
    if ( ! pidof wvdial >> /dev/null 2>&1 ) ; then
       sudo wvdial >> $HOME/.wvdiallog 2>&1 &
    fi

    # if you don't want an xterm to popup, comment out the next 3 lines
    if ( ! pidof xterm >> /dev/null 2>&1 ) ; then
       xterm -e tail -f $HOME/.wvdiallog &
    fi

    # Watch your connection time, change the seconds on the next line to be 5 s longer than your normal connection time
    sleep 45s

    if ( ping -c1 www.yahoo.com >> /dev/null 2>&1 ) ; then
       xmessage -timeout 5 "Connection Speed `grep CON ~/.wvdiallog | tail -n1 | awk '{ print $2 }'` bps" &
       # if you are using KDE, uncomment the next kdialog line, and comment the preceeding xmessage line
       #kdialog -passivepopup "Connection Speed `grep CON $HOME/.wvdiallog | tail -n1 | awk '{ print $2 }'` bps" 5 &

    fi
  done

  sleep 1m

  # some ISP's disconnect when idle, the next line will ping once per minute to keep your connection active
  ping -c1 www.yahoo.com

done
<<<<<<<<<<<<<< script "dialer" ends on previous line >>>>>>>>>>>>>>>>>>>>
 
You can create this script by copying the above lines into a file and saving the file by the name dialer into a (new) sub-directory named scripts in your home directory.  Make sure this script is executable "chmod +x dialer".  Here's a copy [ATTACH]11283[/ATTACH].

You ought to make a backup copy of this script, in case you modify it and it stops working.  Then you can go back to the original version and start over.  I use a terminal and nano to work on scripts, but an editor like gedit or kate will also work and they have the advantage of using syntax coloring to highlite the commands and loops.  In these "bash" scripts you can comment out (inactivate) a line by adding a "#" symbol to the beginning of the line.  The script has some comments in it about things you should check or change, so take the time to read it and test it.

Basically this is a script that runs forever once it's started.  It checks every minute to see if pppd appears in netstat.  If it does, the script just pings once yahoo.com and waits another minute to check again.  If pppd does not appear, it first kills any abandoned wvdial, then starts a fresh wvdial connection.  It keeps a log in ~/.wvdiallog and it runs an xterm to show what that log says, just so you can see if somethings not working correctly.  Once connected, it will create a popup to show connection speed, as determined by wvdial.

I keep this script in a directory in my home called scripts and it is named dialer.  To start this script, just open a terminal and enter "bash ~/scripts/dialer".  To stop the connection, just use the kill commands:

sudo killall -s KILL dialer
sudo killall -s TERM wvdial
sudo killall -s KILL pppd

So, in my kmodemlights applet settings, on the Device tab:

Device:        ppp0
Lockfile:      /var/lock/LCK..modem
Connect:       ~/scripts/dialer
Disconnect:    sudo killall -s KILL dialer ; sudo killall -s TERM wvdial ; sudo killall -s KILL pppd

Your lockfile should reflect the name of the modem in /etc/wvdial.conf.  Mine is /dev/modem.  But, if you had /dev/ttySHSF0, then your Lockfile would be /var/lock/LCK..ttySHSF0.  This lockfile is important to make the lights flash and timer work, so make sure you get the correct file.  If your modem is running and the lights don't work, look at /var/lock to see what file exists and use that name.

For gnome, it's possible to create a custom launcher on the panel, something with a name like "Internet Connect", a command "~/scripts/dialer" and and Icon like "kppp.xpm" to start the connection, and a second launcher to disconnect, perhaps with a name "Internet Disconnect" a command "sudo killall -s KILL dialer ; sudo killall -s TERM wvdial ; sudo killall -s KILL pppd" and any Icon you like.  Now you can start your connection by hitting the Internet Connect icon and disconnect by hitting the Internet Disconnect icon.

Once you have everything set up, it's important to adjust the "sleep 45s" line in the script to match your modem - ISP connection time.  Use a stopwatch if necessary to measure the time it takes from when you initiate the script until you are connected.  Add 5 seconds and use the result to replace "45" with the appropriate value.

[SIZE="3"]**DOWNLOADING UPDATES UNATTENDED**[/SIZE]

If you want to download updates and other files when you are sleeping, the following script can be used.  But, you will also want to disable the automatic updating that comes with (k)ubuntu.  Edit the files /etc/apt/apt.conf.d/10periodic and /etc/apt/apt.conf.d/15adept-periodic-update to change the line:

APT::Periodic::Update-Package-Lists "1";

to:

APT::Periodic::Update-Package-Lists "0";

This will disable the daily "apt-get update" run by Gnome or KDE.

Next, create the following file "download.sh" in your ~/scripts directory:

<<<<<<<<<<<<<< script download.sh begins on next line >>>>>>>>>>>>>>>>>>>>
#!/bin/bash
# list desired additional packages to download (space separated and quotes " at both ends)
# for example, use PKGS="linux-i386 lilypond" to get all linux-386 and lilypond and all
# dependencies downloaded.
# also uncomment the wget line after the apt-get update (below) if you have listed any 
# individual PKGS to download
PKGS=""

# don't change this SUCCESS variable, it's necessary to test for completing the download
SUCCESS=0

# this "until" loop will run until all the commands that are strung together with "&& \"
# between it and SUCCESS=1 successfully complete
until [ $SUCCESS -eq 1 ] ; do

# start dial up
until ( netstat -i | grep ppp ) ; do
 # first kill any leftover or hung wvdial processes
 if ( pidof wvdial ) ; then
    killall -s TERM wvdial
    killall -s KILL pppd
 fi
 if ( ! pidof wvdial >> /dev/null 2>&1 ) ; then
    sudo wvdial >> $HOME/.wvdiallog 2>&1 &
 fi
 if ( ! pidof xterm >> /dev/null 2>&1 ) ; then
    xterm -e tail -f $HOME/.wvdiallog &
 fi
 # Watch your connection time, change the seconds on the next line to be 5 s longer than your normal connection time
 sleep 45s
 if ( ping -c1 www.yahoo.com >> /dev/null 2>&1 ) ; then
    xmessage -timeout 5 "Connection Speed `grep CON ~/.wvdiallog | tail -n1 | awk '{ print $2 }'` bps" &
    # if you are using KDE, uncomment the next kdialog line, and comment the preceeding xmessage line
    #kdialog -passivepopup "Connection Speed `grep CON $HOME/.wvdiallog | tail -n1 | awk '{ print $2 }'` bps" 5 &
 fi
done

# start updates
date
sudo apt-get update

# uncomment the following "sudo wget" line if you have listed any individual PKGS 
# above to download.  otherwise, leave the next line commented
#sudo wget -c -P/var/cache/apt/archives --no-dns-cache --progress=dot:binary --timeout=50 -t4  `apt-get -qq --print-uris -d -y install $PKGS | grep -E ftp:\|http: | awk '{print$1}' | sed -e "s#'##g"` && \
date && \
sudo apt-get --force-yes -y --ignore-missing -d -o Acquire::Retries=4 -o Acquire::http::Timeout=60 -o Acquire::ftp::Timeout=60 dist-upgrade && \
date && \
sudo apt-get --force-yes -y --ignore-missing -d -o Acquire::Retries=4 -o Acquire::http::Timeout=60 -o Acquire::ftp::Timeout=60 upgrade && \
date && \
SUCCESS=1

# If you also want to download some other software using wget, edit the following lines to
# your desired values.  Then, place the wget line and the following URL line just above the
# above line SUCCESS=1.  The example following will use wget to download the file
# http://us.releases.ubuntu.com/releases/kubuntu/dapper/kubuntu-6.06-desktop-i386.iso
# into the directory $HOME/downloads/kubuntu.  So, if you wanted to download picasa into
# your ~/downloads/picasa directory, you would edit the -P/$HOME/downloads/kubuntu to
# -P/$HOME/downloads/picasa and the URL on the second line might be something like
# http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb
# Also, notice the symbols "&& \" at the end of the URL line .. don't delete these by
# accident when you paste in your new URL.
#
#wget -c -P$HOME/downloads/kubuntu --no-dns-cache --progress=dot:binary --timeout=50 -t4 \
#http://us.releases.ubuntu.com/releases/kubuntu/dapper/kubuntu-6.06-desktop-i386.iso && \

done

# stop ppp connection:
sudo killall -s TERM wvdial
sudo killall -s KILL download.sh
sudo killall -s KILL pppd

# uncomment this last line if you want to shutoff your computer when it's finished
#sudo /sbin/shutdown -h now
<<<<<<<<<< script download.sh ends on previous line >>>>>>>>>>>>>>>>>>>>>

You can create this script by copying the above lines into a file and saving the file by the name downloads.sh in your ~/scripts sub-directory.  Make sure this script is executable "chmod +x downloads.sh".  Also, make sure the line #sudo wget -c -P/var/cache/apt/archives --no-dns-cache --progress=dot:binary --timeout=50 -t4  `apt-get -qq --print-uris -d -y install $PKGS | grep -E ftp:\|http: | awk '{print$1}' | sed -e "s#'##g"` && \ has no line breaks in it.  It has to be all on one line.  If your editor makes line breaks by default for long lines, then you might have to set the configuration to not use hard breaks to wrap.  Here's a package containing this file [ATTACH]11284[/ATTACH].

You ought to make a backup copy of this script, in case you modify it and it stops working.  Then you can go back to the original version and start over.  I use a terminal and nano to work on scripts, but an editor like gedit or kate will also work and they have the advantage of using syntax coloring to highlite the commands and loops.  In these "bash" scripts you can comment out (inactivate) a line by adding a "#" symbol to the beginning of the line.  The script has some comments in it about things you should check or change, so take the time to read it and test it.

You should edit this script to use the same number of sleep seconds as you determined for the dialer script.  It should be 5 sec more than the time it normally takes to connect.

Basically this script does the following: first, it checks if a network connection exist, if not, it starts a connection with the same commands as the ~/scripts/dialer script; next, it starts a loop that will run over and over until successfully completed and terminated by the SUCCESS=1 line; once the loop completes successfully, it stops your ppp connection and will shutdown your computer using the command "shutdown -h now".  To download Ubuntu updates, it will first run "apt-get update", next it will run "apt-get -d dist-upgrade" and then "apt-get -d upgrade" to download the all the updates. You might wonder about the other options on these lines: --force-yes and -y are used to answer any questions that might otherwise interupt the script; --ignore-missing is to avoid a situation where one particular package might be missing from the repository and prevents the update from succeeding; -o Acquire::Retries=4 is to cut off the number of retries to prevent apt-get from just sitting there without downloading; -o Acquire::http::Timeout=60 -o Acquire::ftp::Timeout=60 are to timeout after 60 seconds if the file doesn't want to download.  These options cause the download to fail, and this causes the loop to start over.  This way, if things stall (for example, when a repository closes for syncing), this script will continue on and start again when the files are available again.  This is the same reason to use both dist-upgrade and upgrade.  When a repository is missing a particular file, it's not possible to dist-upgrade, but upgrade will still run and fetch everything else.

It's also possible to download specific packages.  Edit the script and enter them in the PKGS variable between the quote symbols.  Separate them with a space.  For example, PKGS="checkinstall kde-devel kde-devel-extras" will download the 3 packages (checkinstall, kde-devel, kde-devel-extras) and their dependencies.  You also have to uncomment the line

#sudo wget -c -P/var/cache/apt/archives --no-dns-cache --progress=dot:binary --timeout=50 -t4  `apt-get -qq --print-uris -d -y install $PKGS | grep -E ftp:\|http: | awk '{print$1}' | sed -e "s#'##g"` && \

The download will be done using "sudo wget" and saved into the /var/cache/apt/archives directory.  You might wonder why not just use "apt-get -d install $PKGS" instead.  The problem with this is that if you already have some of the packages or dependency packages on your cdrom, the script will hang when apt-get tries to get you to load your CD.  This is probably an apt-get bug, but I don't know any other way to deal with it.

If you also want to download some other file, using wget, just copy and uncomment the example above the line SUCCESS=1 and edit it for your desired download directory and the proper URL.  For example to download picasa, you would have something like:

wget -c -P$HOME/downloads/picasa --no-dns-cache --progress=dot:binary --timeout=50 -t4 \
http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb && \
SUCCESS=1

If there were two files to download, you could add two sets of the wget/url lines just before SUCCESS=1.  For example, to get picasa and opera, you would use something like this:

wget -c -P$HOME/downloads/picasa --no-dns-cache --progress=dot:binary --timeout=50 -t4 \
http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_2.2.2820-5_i386.deb && \
wget -c -P$HOME/downloads/opera --no-dns-cache --progress=dot:binary --timeout=50 -t4 \
http://mirror.olnevhost.net/pub/opera/linux/854/final/en/i386/shared/opera_8.54-20060330.6-shared-qt_en_etch_i386.deb && \
SUCCESS=1

You can string together as many wget/url lines as you want.

Take note of the symbols "&& \" at the end of some lines.  These symbols tie together one line to the next in a continuous string.  It's this string that must be successfully completed for the loop "until [ $SUCCESS -eq 1 ] ; do" through the line "SUCCESS=1" to work properly.  If you make a mistake and leave off the "&&" symbol, the loop will not repeat itself.  So, if the initial pass through fails to download something, it will just be skipped.  Some lines do not have the "&&" symbol at the end.  For example, "apt-get update" does not, because it will always fail if even one of your repositories in /etc/apt/sources.list is unreachable.  You don't want the script to stop at that point.  Also, the line "wget -c -P$HOME/downloads/picasa --no-dns-cache --progress=dot:binary --timeout=50 -t4 \" does not have the "&&".  This is because this line is continued on the next line by the "\" symbol at the end.

Also, I have found that some URL's have symbols in them that /bin/bash doesn't like, and the script won't work correctly.  For example, I tried the URL http://download.mozilla.org/?product=firefox-1.5.0.4&os=win&lang=en-US to get the latest win32 firefox, and it stopped the script from reconnecting after my ISP hungup.  I don't know how to deal with this, yet (except to not use it for such an odd URL).

Because of this, I advise you to keep an unused original (for example, download.sh.orig) untouched, so you can go back if you make a mistake editing download.sh.

The way to use this file is to open a terminal and enter the command ~/scripts/download.sh.  The terminal will stay open and scroll the output of what it's doing.  If it's not finished when you come back and you want to kill it, just go to that terminal and hit Control-c (hold CONTROL key down and hit the "c" at the same time) on your keyboard to kill it.  You may have to do this several times.  If the dialup is still running, stop the ppp connection with:

sudo killall -s TERM wvdial
sudo killall -s KILL download.sh
sudo killall -s KILL pppd


[SIZE="3"]**KEEPING A LOCAL REPOSITORY**[/SIZE]

To use my archive script, you need to have "dpkg-dev" installed.

There used to be a debian package to sort outdated packages from a local repository, but it stopped working when apt was updated for Breezy.  I made my own script to move packages from /var/cache/apt/archives, unmangle any mangled filenames, and discard the obsolete packages.  This script is archive.sh:

<<<<<<<<<< script archive.sh begins on next line >>>>>>>>>>>>>>>>
#!/bin/bash

## enter the location of apt-get deb files:
DEBCACHE=/var/cache/apt/archives
## enter the location of local archive and rejects:
LOCALARCHIVE=$HOME/backups/dapper.updates
REJECTS=$HOME/backups/dapper.rejects

[[ ! -d $LOCALARCHIVE ]] && mkdir -p $LOCALARCHIVE
[[ ! -d $REJECTS ]] && mkdir -p $REJECTS
countadded=0
countremoved=0
countmangled=0
startwith=$((`ls $LOCALARCHIVE | wc -l`-2))    # use this for oversize archives where 'ls' fails
countnondeb=0

echo -e "\nstarting to update saved debs at $(date)"
echo "moving debs from $DEBCACHE to $LOCALARCHIVE"
sudo mv -f $DEBCACHE/*.deb $LOCALARCHIVE/
sudo chown -R $USER: $LOCALARCHIVE

for debianfile in $LOCALARCHIVE/* ; do

## skip it if it's not a debian file:
FILECHECK=`file $debianfile | cut -d" " -f2-4`
if [[ $FILECHECK == "Debian binary package" ]] ; then
ActualPackage=`dpkg -I $debianfile | grep " Package:" | head -n1 | awk '{ print$2 }'`
ActualVersion=`dpkg -I $debianfile | grep " Version:" | head -n1 | awk '{ print$2 }' | cut -d: -f2-`
ActualArch=`dpkg -I $debianfile | grep " Architecture:" | head -n1 | awk '{ print$2 }'`
ActualName=`echo $ActualPackage\_$ActualVersion\_$ActualArch\.deb`
## check if it's in the current apt cache and if so, copy it to the archive
cacheversion=`apt-cache policy $ActualPackage | grep " Candidate:" | awk '{ print$2 }' | cut -d: -f2-`
if [[ $ActualVersion == $cacheversion ]] ; then
countadded=$((countadded + 1))
## unmangle any mangled file names
isitmangled=`basename $debianfile`
if [[ $isitmangled != $ActualName ]] ; then
echo "file name is mangled, so moving it from $isitmangled >>>>>>>>>>>>> $ActualName"
countmangled=$((countmangled + 1))
mv -f $LOCALARCHIVE/$isitmangled $LOCALARCHIVE/$ActualName
fi
else
echo "$ActualName does not match $cacheversion ............................. removing"
countremoved=$((countremoved + 1))
mv -f $debianfile $REJECTS
fi
else
echo "$debianfile is not a debian file .. so removing"
mv -f $debianfile $REJECTS
countnondeb=$((countnondeb + 1))
fi

done

## make the packages file for the archive:
cd $LOCALARCHIVE && rm -f Packages.gz
echo -e "\nscanning packages and making new Packages file"
dpkg-scanpackages . /dev/null | gzip --best > Packages.gz

## replace the MD5SUMS
cd $LOCALARCHIVE && rm -f MD5SUMS.txt
echo -e "\nmaking md5sum list"
find . -exec md5sum {} ';' | sed -n '/MD5SUMS.txt/!p' >> MD5SUMS.txt

echo -e "\nstarted with $startwith in $LOCALARCHIVE"
echo "ended with $countadded in $LOCALARCHIVE"
echo "removed $countremoved debs from $LOCALARCHIVE to $REJECTS"
echo "removed $countnondeb non debians from $LOCALARCHIVE to $REJECTS"
echo "unmangled $countmangled file names in $LOCALARCHIVE"
echo -e "\nfinished at $(date)"
exit 0
<<<<<<<<<< script archive.sh ends on previous line >>>>>>>>>>>>>>

You can create this script by copying the above lines into a file and saving the file by the name archive.sh in your ~/scripts sub-directory.  Make sure this script is executable "chmod +x archive.sh".  Here's a package containing this file [ATTACH]11282[/ATTACH].

You ought to make a backup copy of this script, in case you modify it and it stops working.  Then you can go back to the original version and start over.  I use a terminal and nano to work on scripts, but an editor like gedit or kate will also work and they have the advantage of using syntax coloring to highlite the commands and loops.  In these "bash" scripts you can comment out (inactivate) a line by adding a "#" symbol to the beginning of the line.  The script has some comments in it about things you should check or change, so take the time to read it and test it.

Basically, this script just moves the deb files from /var/cache/apt/archives into ~/backups/dapper.updates directory, then fixes any mangled names, moves any obsolete debians to ~/backups/dapper.rejects directory, scans the debians to create a Packages.gz and MD5SUMS.txt and gives the count of new and displaced packages.

To use this archive script, just open a terminal and enter ~/scripts/archive.sh.  It's a bit slow, taking as much as 25 minutes for a 1.5 GB repository on my pc.  There isn't always output on the terminal when it's running, so don't assume it's died .. just give it enough time to finish.  You'll see output of any files moved to the rejects directory as well as any mangled filenames.  Take a look at these to be sure some package you wanted didn't get dumped by mistake.  They are still saved in the ~/backups/dapper.rejects directory.  When you're sure you don't want anything from there, you have to empty it yourself .. in a terminal, the command "rm -f ~/backups/dapper.rejects/*" will work.  Once you have run it, you should edit your /etc/apt/sources.list and at the top, add:

# local
deb file:/home/<your username>/backups/dapper.updates/ ./

Make sure you replace <your username> with what you get by running "echo $USER" in a terminal.

Now, the next time you run "apt-get update", this local repository will show up.

When I get 700 MB of archives, I generally burn it to a CD and start over with an empty directory.  You can use "sudo apt-cdrom add" to add CD's to your /etc/apt/sources.list.

Here's another tip on how to make a Packages.gz file in any directory.  Once you have a Packages.gz, you can add that directory to your /etc/apt/sources.list as explained above.  Edit your ~/.bashrc file and add the following lines, in this order:

alias md5here='find . -exec md5sum {} '\'';'\'' | sed -n '\''/MD5SUMS.txt/!p'\'' >> MD5SUMS.txt'
alias scanhere='dpkg-scanpackages . /dev/null | gzip -9 > Packages.gz ; rm -f MD5SUMS.txt ; md5here'

Now, if you have created a directory of your own packages, just open a terminal and cd into that directory, then issue the command "scanhere".  You will also get a file name MD5SUMS.txt that will contain the checksums for each file within that directory.  This is useful for checking for damaged files with the command "md5sum -c MD5SUMS.txt".  See "man md5sum" for information.  If you just wanted the MD5SUMS.txt created, you would issue "md5here" at the command prompt, instead of "scanhere".  This is useful if your burning a data CD and want to be able to check file integrity on the CD.  By the way, most linux distros have an "md5sum.??" file somewhere in the top directory of their CD's, so you can mount them and check integrity of individual files.

Hope this improves your downloading as much as it did mine.

---

### Post by Matchless on 2006-06-16
Hi Golfbuf,
             This is fantastic. I have downloaded all and the kmodemlights was something I was looking for as well! I really appreciate the time you put in on the script for the local repo. I can already see these with a nice icon to run them when required etc! I will try then during the coming week. Thanks again

---

### Post by golfbuf on 2006-06-18
BTW, all the scripting I know can be learned in about an hour from this article:

[http://www.linuxfocus.org/English/September2001/article216.shtml](http://www.linuxfocus.org/English/September2001/article216.shtml)

regards,

---

### Post by Cariboo1938 on 2006-08-09
Hello golfbuf,
I hope I do not bother you with my Dial-Up story. I installed Ubuntu a few days ago and with the help of the "DialupModemHowto" I got wvdial set up. Starting/closing the connection in a terminal with 'pon/poff' works fine. But I wanted to be a bit more fancy and installed "kppp". Insallation and configuration was easy but it does not connect. Here are error messages I get each time after dialing to my IP:
The pppd daemon died unexpectedly!
Exit status: 16
Details
Aug  9 18:30:30 localhost pppd[9705]: pppd 2.4.4b1 started by owner, uid 1000
Aug  9 18:30:30 localhost pppd[9705]: using channel 4
Aug  9 18:30:30 localhost pppd[9705]: Using interface ppp0
Aug  9 18:30:30 localhost pppd[9705]: Connect: ppp0 <--> /dev/ttyS4
Aug  9 18:30:30 localhost pppd[9705]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x97098204> <pcomp> <accomp>]
.
.
Aug  9 18:30:57 localhost pppd[9705]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x97098204> <pcomp> <accomp>]
Aug  9 18:31:00 localhost pppd[9705]: LCP: timeout sending Config-Requests 
Aug  9 18:31:00 localhost pppd[9705]: Connection terminated.
Aug  9 18:31:00 localhost pppd[9705]: Modem hangup
Aug  9 18:31:00 localhost pppd[9705]: Exit.

This config request('sent [LCP ConfReq'), which seems to be an option in configuring kppp (I checked man pppd line 496 ff), obviously causes the problem. I talked to the Internet Provider (Telus) about this but I was told that they do not support troubleshooting for Linux systems. I wonder if Kmodemlights is also I dialer I could use on my 64bit architcture if the problem with kppp can not be solved.
I would appreciate if you would find the time to answer me.
Kind regards
Juergen

---

### Post by Cariboo1938 on 2006-08-10
Hi golfbuf,
I solved my Dial-Up issue...
I uninstaled kppp..
I installed gnome-ppp..
It is simpler in the graphics, but it works great, it is fast and stable...
that's all it needs
Juergen

---

### Post by chuckman78 on 2006-12-10
Hello.

 I am an Ubuntu user who have been benefited from your great dialup scripts for keeping updated using a dialup modem:

<http://www.ubuntuforums.org/showthread.php?t=197300>

I specially like the second script "DOWNLOADING UPDATES UNATTENDED". I used to use it under dapper and also under edgy with great results. The problem is   that recently, and who knows why, this script doesn't work anymore; it starts and gets the conection with my ISP perfectly and begins downloading updates but if for any reason the connection gets interrupted, the script wont retry to dial a new connection and keep updating. 

The other script (Getting a reliable connection) works great, it dials and connects to my ISP and if for any reason the connection is lost the script re-engages it.

I have tried with a fresh script from the forum thread, thinking that I could have corrupted the script with any change, but that does not work either. Maybe you are using an updated script for edgy? Please if you could share any info of this I would truly appreciate that. Thanks for or your help on making life easier for the whole dialup users around the globe!

Regards,

Carlos.

---

### Post by golfbuf on 2006-12-12
OK, I do not know what the problem might be.  But, I have been developing improvements in this script and have a newer version.  I have been testing this since edgy came out and it works ok for me.  Please try it and see if it reconnects.

It is download.edgy.sh.tar.bz2

regards,

---

### Post by chuckman78 on 2006-12-13
Hi golfbuf.

First of all, THANKS A LOT for answering! 

This script works for me, it reconnects after losing the connection with the ISP and keeps trying to download the updates until it gets them all. Thought, I have some issues that I hope you could clear:

1.- Ok, I got the update debs... How do I get them installed (It looks like the script get the needed files into /home/user/download/packages but doesnt install them, right)? Issueing an "sudo apt-get upgrade" after the script is over won't work because the files aren't at /var/cache/apt/archives, right? I got around this making a local repo from the /home/user/download/packages and using "sudo apt-get upgrade" but how did you inteded it to work?).
2.- Could you give us an explanation of what is the script doing? I believe it bassically makes hidden lists of the files needed to get downloaded and then get them, am I right?

I hope I am not asking too much, I just want to learn so I wont need the to get the fish from others just catch it myself (and hopefully teach others to fish too). Thanks in advance for your time and help.

Regards,

Carlos.

---

### Post by golfbuf on 2006-12-13
Yes, I had a couple problems with the earlier version .. sometimes apt-get would hang and not download, and the list of desired packages could not tolerate any grammar errors.  So, I decided to use wget for all downloads.  Now, when you run "bash scripts/download.edgy.sh", the script will do a upgrade and dist-upgrade command to create a list of update package URLs in your ~/.dl-debs-list and use wget to download from that file.  If you have some additional packages to download, you can edit the script and add them into the PKGS variable, and they will likewise be downloaded into ~/downloads/packages

There is also a place to enter source packages, called SRCS.  The script adds the build dependency packages into ~/.dl-debs-list, and the source URLs into ~/.dl-srcs-list.  wget downloads into ~/downloads/sources

Likewise for any other non debian download that you have a URL for.  You just add them to the OTHER variable list.  The script creates a ~/.dl-other-list and uses wget to download them into ~/downloads/other.  For example, this is what I enter to get the latest openoffice linux and then win versions:

SRCS="http://mirrors.isc.org/pub/openoffice/stable/2.1.0/OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
http://mirrors.isc.org/pub/openoffice/stable/2.1.0/OOo_2.1.0_Win32Intel_install_en-US.exe"

This script can parse the PKGS, SRCS, OTHER variables and wget will skip any non-valid ones and keep downloading the valid ones.  That's an improvement over the earlier script.

I think wget does a better job of recognizing a stalled download and breaking the stall versus apt-get.  wget also does not mangle file names, as apt-get does.

Once you have your debs in ~/downloads/packages, you can move them to /var/cache/apt/archives/ or into your local repository.  I have a local repository in ~/backups/edgy.updates/.  After I do "mv ~/downloads/packages/*deb ~/backups/edgy.upates/" I use my archive.sh script to sweep up any other packages from /var/cache/apt/archives/ and rebuild my edgy.updates repository (purge obsolete, unmangle file names, and create a new Packages.gz list).  Then, I just "apt-get update" and "apt-get dist-upgrade" to install them.

regards,

---

### Post by chuckman78 on 2006-12-13
> **golfbuf said:**
> Yes, I had a couple problems with the earlier version .. sometimes apt-get would hang and not download, and the list of desired packages could not tolerate any grammar errors.  So, I decided to use wget for all downloads.  Now, when you run "bash scripts/download.edgy.sh", the script will do a upgrade and dist-upgrade command to create a list of update package URLs in your ~/.dl-debs-list and use wget to download from that file.  If you have some additional packages to download, you can edit the script and add them into the PKGS variable, and they will likewise be downloaded into ~/downloads/packages

There is also a place to enter source packages, called SRCS.  The script adds the build dependency packages into ~/.dl-debs-list, and the source URLs into ~/.dl-srcs-list.  wget downloads into ~/downloads/sources

Likewise for any other non debian download that you have a URL for.  You just add them to the OTHER variable list.  The script creates a ~/.dl-other-list and uses wget to download them into ~/downloads/other.  For example, this is what I enter to get the latest openoffice linux and then win versions:

SRCS="http://mirrors.isc.org/pub/openoffice/stable/2.1.0/OOo_2.1.0_LinuxIntel_install_en-US.tar.gz
http://mirrors.isc.org/pub/openoffice/stable/2.1.0/OOo_2.1.0_Win32Intel_install_en-US.exe"

This script can parse the PKGS, SRCS, OTHER variables and wget will skip any non-valid ones and keep downloading the valid ones.  That's an improvement over the earlier script.

I think wget does a better job of recognizing a stalled download and breaking the stall versus apt-get.  wget also does not mangle file names, as apt-get does.

Thanks for the explanation, it looks like I was getting it right. By the way, great job with the improvements made to the script!

> **golfbuf said:**
> Once you have your debs in ~/downloads/packages, you can move them to /var/cache/apt/archives/ or into your local repository.  I have a local repository in ~/backups/edgy.updates/.  After I do "mv ~/downloads/packages/*deb ~/backups/edgy.upates/" I use my archive.sh script to sweep up any other packages from /var/cache/apt/archives/ and rebuild my edgy.updates repository (purge obsolete, unmangle file names, and create a new Packages.gz list).  Then, I just "apt-get update" and "apt-get dist-upgrade" to install them.

I also use your archive.sh script and make a local repo from ~/backups/edgy.updates. By the way, have you made any modifications to archive.sh?

Thnks for all your help and time.

Regards,

Carlos

---

### Post by golfbuf on 2006-12-14
> **chuckman78 said:**
> I also use your archive.sh script and make a local repo from ~/backups/edgy.updates. By the way, have you made any modifications to archive.sh?

Nothing substantive.  If you're lazy, you might want to  add this near the top:

mv ${HOME}/downloads/packages/*deb ${HOME}/backups/edgy.updates/

The reason I haven't done this is because you need to wait until all the packages are fully downloaded.  So, I check the output of my terminal to be sure all were fully downloaded before deciding whether to move them to the archive.  I haven't figured out a way to do this yet.

However, I did add this to my ~/.bashrc, so all I have to do is do "mvbu" in a konsole:

alias mvbu='mv ${HOME}/downloads/packages/*deb ${HOME}/backups/edgy.updates/'

I'm also testing a different command to unmangle file names, but this has no effect except perhaps speed.

regards,

---

### Post by chuckman78 on 2006-12-14
Ok,golfbuf. Thanks a lot for the info. 

Regards,

Carlos.

---

### Post by Sepero on 2007-09-16
Wow, that howto is a lot of text for something so simple. :(

This is the way I kept my computer up to date for several years:

Open 2 terminals

In the first terminal, run:
while true; do wvdial; done # or "pppd call provider" instead of "wvdial"

In the second terminal, run:
while true; do apt-get update&& apt-get upgrade -yd&& break; done



The first terminal stays connected to the internet infinitely. The second downloads updates & upgrades, and it exits(breaks) the loop when finished. Run these before you go to bed, stop them in the morning Ctrl-C.

EDIT:
The second command only downloads the upgrades. After they finish downloading, you obviously have to run "apt-get upgrade -y" to actually make them install.

---

### Post by chuckman78 on 2007-09-16
Sepero.

Thanks for the info. The good thing about Golfbuf script is that it alouds to install other packages, not only those in the upgrade path. It also, because of the use of wget, handles some weird problems you might get when using apt-get to handle the downloading.

Anyway, your formula is very simple and really usefull!

Regards,

Carlos.

---

