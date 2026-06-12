---
title: "HOWTO: Build HTPC using Linux Ubuntu"
date: 2010-08-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Superdude_123 on 2010-08-01
Before I get started, here are 10 facts that I want to point out:

1) This is my first How To.
2) This guide assumes a minimal (mostly) understanding of Linux from the reader (but I assume you can learn right?).
3) I don't baby step you all the way, I do reference you to other place to follow some instructions elsewhere.
4) Your debating on chossing a Windows approach or a Linux approach, and the idea behind this guide is to show you how easy/hard it was to get it to work.
5) I am not promoting any company or product (but Linux).
6) From start to finish, after Ubuntu was installed, this would take someone 30-45 min, maybe an hour + for a Linux newbie.
7) XBMC is the media software used here, but it should be noted that it was not setup to load at boot, but a simple click of a mouse will open it. The benefit here is that the system is also a fully functioning PC.
8) No passwords are required at boot, since the idea of minimal use of a keyboard was key.
9) Configuring XBMC is not covered here.
10) Obtaining SPDIF audio out and HDMI video out, and also obtaining simultaneous SPDIF and Analog audio out (nice to do for some amplifiers) were achieved with Ubuntu 9.10 and XBMC, but are not covered here.

Ok, so now out with the prep talk, lets get this show on the road :popcorn:


Hardware:

ASUS M4N98
AMD Phenom II X4 945 (over kill for most applications)
OCZ 4GB DDR3 memory (could have been made less)
Western Digital Caviar Black 2TB SATA2 (could have been made less)
Samsung DVD Writer SATA
Gigabyte GeForce GT 240 600MHZ 1GB HDMI DVI VGA PCI-E Video Card (chosen for the HDMI for my TV, and the fact that GeForce drivers are known to work well with Linux over ATI drivers....but I will admit I have had good luck with ATI lately)
Silverstone Lascala LC10B-E Black HTPC ATX Case (I chose ATX as experience has taught me to be wary of mATX power supplies)
Antec Truepower New 750W Modular Power Supply (should have gone smaller, down to a 550 W or so)
Pcusa Vista Remote Control
Gigabyte GK-KM7500 Wireless Multimedia Keyboard & Mouse Combo

While I'm on the subject of hardware, I will say how everything turned out. I've had no problems with anything, except from time to time, the remote control jams and I need to reboot the system. I also had bought a Dlink wireless network card, but after having a slow connection and frequent drops, I just hard wired a wire through the house (well worth it at the end as speeds are excellent). I've also had to move the wireless keyboard + mouse receiver to the front of the system (tucked next to the box via a 3 ft USB extension cable) since reception was poor.

Now the HOWTO:


Install Ubuntu 9.10 64 bit

Install and activated restricted drivers (system->administration->hardware drivers)

Reboot

Install ssh (for remote access and using SFTP over the network...see note 1 bellow) by: sudo apt-get install ssh [Not a required step]

Install samba server and setup shared music/video folder by following the guide at:  [https://help.ubuntu.com/9.10/internet/C/networking-shares.html](https://help.ubuntu.com/9.10/internet/C/networking-shares.html) [Not a required step]

Install mp3 codec by opening an mp3 and having ubuntu search on its own (ya its the lazy man's way of doing it, but it works!)

The samba config file is modified with: sudo gedit /etc/samba/smb.conf to that described in note 2, and also know that this allows anonymous downloading from your system over a network, but anonymous uploading/deleting is banded

Restarted samba with: sudo /etc/init.d/samba restart

Installed DVD playback by following sudo apt-get install ubuntu-restricted-extras (had to install java, and to select ok I used the arrow keys) and  sudo /usr/share/doc/libdvdread4/install-css.sh

Reboot

Installed xbmc following [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher)

Setup remote control with lric: sudo apt-get install lirc


Extra Steps:


Installed ripit with: sudo apt-get install ripit  [ripit is used to automatically rip your CD's]

Configured ripit config file with: sudo gedit /etc/ripit/config (see note 3 for the config file)

Saved the changes to the config file by: ripit --save

Install lame for mp3 codec by: sudo apt-get install lame

Installed easy tag (nice program to work with mp3's that were not tagged correctly by ripit) by: sudo apt-get install easytag

Installed k3b (similar to Nero in Windows) to burn cd's/dvd's by: sudo apt-get install k3b


Note 1: SFTP is used to transfer music, pictures, or videos over the network in a secure fashion, this is can be done with various SFTP clients in either a Windows/Mac system, or with any Linux system. Also note, that SSH can be used to get you out of a jam or remotely administer the system, either from your network, or outside of it. SSH can also be used as a method of typing commands in the system if the PC doesn't have a keyboard.

Note 2:


#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned hereuser
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = Ubuntu-user

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = share

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

wins support = no
[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[Music]
path = /home/user/Music
available = yes
browsable = yes
public = yes
writable = yes

[Videos]
path = /home/user/Videos
available = yes
browsable = yes
public = yes
writable = yes

[Pictures]
path = /home/user/Pictures
available = yes
browsable = yes
public = yes
writable = yes

Note 3:


#####
#
# RipIT 3.8.0 configuration file.
#
# For further information on ripit configuration / parameters
# and examples see the manpage or the README provided with ripit
# or type ripit --help .


#####
#
# Ripping device & path.
#

# cddevice: Define ripping device if other than /dev/cdrom.
# Default: /dev/cdrom

cddevice=/dev/cdrom

# scsidevice: Device name for special devices if the non ripping
# commands should be executed on a different device node. This might
# be useful for some old SCSI devices. If not set the cddevice will
# be used.
# Example: /dev/sr18
# Default: not set

scsidevice=

# output: Path for audio files. If not set, $HOME will be used.
# Default: not set

output=/home/user/riped_music_from_ripit

# directory permissions: Permissions for directories.
# Default: 0755

dpermission=0755

# file permissions: Permissions for sound and log files.
# If not set, uses the default system settings.
# Default: not set

fpermission=


#####
#
# Ripping options.
#

# ripper: select CD ripper
# 0 - dagrab
# 1 - cdparanoia
# 2 - cdda2wav
# 3 - tosha
# 4 - cdd
# Default: cdparanoia

ripper=1

# ripopt: User definable options for the CD ripper.
# Default: not set

ripopt=

# span: Rip only part of a single track or the merged track-interval.
# Possible values: any in the format hh:mm:ss.ff-hh:mm:ss.ff
# Example: rip first 30s of each track: 0-30
# Default: not set

span=

# paranoia: Turn "paranoia" on or off for dagrab and cdparanoia.
# Possible values: 0 - no paranoia, 1 - use paranoia
#                  2 - switch paranoia off if ripping fails on one
#                      track and retry this track without paranoia
# Default: 1 - use paranoia

paranoia=1

# ghost: Analyze the wavs for possible gaps, split the wav into
# chunks of sound and delete blank tracks.
# Possible values: 0 - off, 1 - on
# Default: off

ghost=0

# prepend: Enlarge the the chunk of sound by a number of
# seconds at the beginning (if possible).
# Possible values: any positive number and zero; precision in
# tenths of seconds. Be aware of low numbers.
# Default: 2.0

prepend=0

# extend: Enlarge the the chunk of sound by a number of
# seconds at the end (if possible).
# Possible values: any positive number and zero; precision in
# tenths of seconds. Be aware of low numbers.
# Default: 2.0

extend=0

# resume: Resume a previously started session.
# Possible values: 0 - off, 1 - on
# Default: off

resume=0

# overwrite: Default behaviour of Ripit is not to overwrite existing
# directories, a suffix will be added if directory name exists.
# Use option overwrite to prevent this and either overwrite a previous
# rip or force Ripit to quit or even eject the disc. If ejection is
# chosen, the disc will be ejected even if option eject has not been
# switched on.
# Possible values: n - off, y - on,
#                  q - quit, e - quit and force ejection
# Default: off

overwrite=n


#####
#
# Encoding options
#

# encode: Encode the wavs.
# Possible values: 0 - off, 1 - on
# Default: on

encode=1

# coder: Select encoders for audio files:
# 0 - Lame (mp3)
# 1 - Oggenc (ogg)
# 2 - Flac (flac)
# 3 - Faac (m4a)
# 4 - mp4als (als)
# 5 - Musepack (mpc)
# Multiple encoders can be selected by giving a comma-separated list
# Example: coder=0,0,1,2 encodes CD twice to mp3, ogg and flac files
# Default: Lame

coder=0

###
#
# lame (mp3) encoder options
#

# qualame: Sets audio quality for lame encoder in cbr (lame-option -q)
# and vbr (lame-option -V) mode, comma separated list.
# Possible values: 0...9, off
# 0: higest quality
# 9: lowest quality
# Can be set to "off" if all options are passed to --lameopt.
# Example: qualame=off,off
# Note: default value is the same for cbr and vbr,
# although vbr-default should be 4.
# Default: 5

qualame=0

# lameopt: Additional options for lame encoder, comma separated list.
# Example: lameopt=-b 128,--preset extreme
# Default: not set

lameopt=

# vbrmode: Enable variable bitrate for lame encoder.
# Possible values: "old" or "new"
# Default: not set

vbrmode=

# bitrate: Sets bitrate for lame encoder.
# Possible values: 32...320, off
# Should be set to "off" if vbr is used
# Default: 128

bitrate=320

# maxrate: Sets maximum bitrate for lame (when using vbr) and oggenc.
# Possible values: 0 - off, 32...320
# Default: 0

maxrate=0

# preset: Use lame presets. To set the "fast" switch, use --vbrmode new.
# Possible values: medium, standard, extreme, insane
#
# medium: 160kbps
# standard: 192kbps
# extreme: 256kbps
# insane: 320kbps
#
# Default: not set

preset=

###
#
# oggenc (ogg) encoder options
#

# qualoggenc: Sets audio quality for oggenc.
# Possible values: 1..10, off
# 1: lowest quality
# 10: highest quality
# Can be set to "off"
# Default: 3

qualoggenc=off

# oggencopt: Additional options for oggenc, comma separated list.
# Default: not set

oggencopt=

###
#
# flac (lossless) encoder options
#

# quaflac: Sets audio compression for flac encoder
# Possible values: 0...8, off
# 0: lowest compression
# 8: highest compression
# Can be set to "off"
# Default: 5

quaflac=off

# flacopt: Additional options for flac encoder, comma separated list.
# Default: not set

flacopt=

###
#
# faac (m4a) encoder options
#

# quafaac: Sets audio quality for faac encoder
# Possible values: 10...500, off
# 10: lowest quality
# 500: highest quality
# Can be set to "off"
# Default: 100

quafaac=off

# faacopt: Additional options for faac encoder, comma separated list.
# Default: not set

faacopt=

###
#
# mp4als (als) encoder options
#

# quamp4als: Would set compression level for mp4als, but mp4als does not
# accept any options (?).
# Default: 0

quamp4als=0

# mp4alsopt: Additional options for mp4als encoder, none are accepted,
# comma separated list.
# Default: not set

mp4alsopt=

###
#
# Musepack (mpc) encoder options
#

# musenc: The encoder name on the command line
# Possible values: any
# Example: musenc=mppenc for older versions
# Default: mpcenc

musenc=mpcenc

# quamuse: Sets audio quality for Musepack encoder
# Possible values: 0...10, off
# 0: lowest quality
# 10: highest quality
# Can be set to "off"
# Default: 5

quamuse=off

# museopt: Additional options for Musepack encoder,
# comma separated list.
# Default: not set

museopt=


#####
#
# Trackname and directory template
#

# dirtemplate: Template for directory structure
# The template can be created using any legal
# character, including slashes (/) for multi-level
# directory-trees, and the following variables:
# $album
# $artist
# $iletter
# $genre
# $quality
# $suffix
# $trackname
# $tracknum
# $year
# $trackno
#
# The variable $iletter is the initial letter of
# the artist variable, the $quality is the quality
# according to the encoding format defined by $suffix.
# The variable $quality reflects the encoder options,
# not the arguments of option --quality which may be set
# to off. The variable $trackno is the total number of tracks
# of the release.
#
# dirtemplate is an array, for each encoder a different
# dirtemplate may be defined (i. e. for each encoder state
# a line starting with dirtemplate=...).
#
# Example:
# dirtemplate="$suffix/hard_path/$iletter/$artist/$year - $album"
#
# The double quotes (") are mandatory!
# Default: "$artist - $album"

dirtemplate="$artist - $album"

# tracktemplate: Template for track names
# "tracktemplate" is used similarly to "dirtemplate"
# Default:  "$tracknum $trackname"

tracktemplate="$tracknum $trackname"

# infolog: Log certain operations to file
# (e.g. system calls, creation of dirs/files)
# Possible values: filename (full path, no ~ here!)
# Default: not set

infolog=

# lowercase: Convert filenames to lowercase
# Possible values: 0 - off, 1 - on
# Default: off

lowercase=0

# uppercasefirst: Convert filenames and tags to uppercase first,
# not recommended. To be used on the command line only if CDDB entry
# is in uppercase.
# Possible values: 0 - off, 1 - on
# Default: off

uppercasefirst=0

# underscore: Replace blanks in filenames with underscores
# Possible values: 0 - off, 1 - on
# Default: off

underscore=0

# chars: Exclude special characters in file names and path.
# Note: following characters will always be purged:
#  ; > < " and \015 .
# Side note: if calling this option on the command line without
# argument, following characters will be purged:  |\:*?$  plus
# blanks and periods at beginning and end of file names and directories.
# This is identical to the word NTFS passed as argument to the command
# line or stated here in the config file. The word HFS will purge colons
# only plus blanks and periods at beginning of file names and
# directories.
#
# No need to escape the special characters here in the config file.
# Possible values: HFS, NTFS, none, any (?)
# Default: not set

chars=

# playlist: Create m3u playlist with or without the full path
# in the filename.
# Possible values: 0 - off,
                   1 - on with full path
#                  2 - on with no path (filename only)
# Default: on (with full path)

playlist=1


#####
#
# Audio file tagging
#

# year-tag: State a year (mp3, m4a) or a date (ogg, flac) tag.
# Possible values: integer
# Default: not set

year=

# comment-tag: State a comment (mp3, m4a, mpc) or a
# description (ogg, flac) tag. To write the cddbid used for freedb
# or the MusicBrainz discid into the comment, use the word "cddbid"
# or "discid".
# Possible values: discid, cddbid or any string
# Default: not set

comment=

# utftag: Use Lame-tags in UTF-8 or convert them
# (but not the filenames) from Unicode to ISO8859-1.
# Use when your mp3-audio player doesn't support Unicode tags.
# Recommended with Lame.
# Possible values: 0 - off, 1 - on
# Default: on

utftag=1


#####
#
# CDDB options
#

# mb: Access MusicBrainz DB via WebService::MusicBrainz module instead
# of the http protocol (see below).
# Possible values: 0 - off, 1 - on
# Default: off

mb=0

# CDDBHOST: Specifies the CDDB server
# Possible values: freedb.org, freedb2.org or musicbrainz.org
# Note: Full name of the server used is $mirror.$CDDBHOST, except for
# freedb2.org (no mirror) and musicbrainz.org has freedb as default
# mirror.
# E.g. default server is freedb.freedb.org
# Default: freedb.org

CDDBHOST=freedb.org

# mirror: Selects freedb mirror
# Possible values: "freedb" or any freedb mirrors
# See [www.freedb.org](www.freedb.org) for mirror list
# Note: Full name of the server used is $mirror.$CDDBHOST
# E.g., default server is freedb.freedb.org
# Default: freedb

mirror=freedb

# transfer: Set transfer mode for cddb queries
# Possible values: cddb, http
# Note: CDDB servers freedb2.org and musicbrainz.org may need transfer
# mode http.
# Default: cddb

transfer=cddb

# proto: Set CDDP protocol level
# Possible values: 5, 6
# Protocol level 6 supports Unicode (UTF-8)
# Default: 6

proto=6

# proxy: Address of http-proxy, if needed
# Default: not set

proxy=

# mailad: Mail address for cddb submissions
# Valid user email address for submitting cddb entries
# Default: not set

mailad=

# archive: Read and save cddb data on local machine
# Possible values: 0 - off, 1 - on
# Default: off

archive=0

# submission: Submit new or edited cddb entries to
# freeCDDB
# Possible values: 0 - off, 1 - on
# Default: on

submission=1

# interaction: Turns on or off user interaction in cddb dialog
# Possible values: 0 - off, 1 - on
# Default: on

interaction=1


#####
#
# LCD options
#

# lcd: Use lcdproc to display status on LCD
# Possible values: 0 - off, 1 - on
# Default: off

lcd=0

# lcdhost: Specify the lcdproc host
# Default: localhost

lcdhost=localhost

# lcdport: Specify port number for localhost
# Default: 13666

lcdport=13666


#####
#
# Distributed ripping options
#

# sshlist: Comma separated list of remote machines ripit shall use
# for encoding. The output path must be the same for all machines.
# Specify the login (login@machine) only if not the
# same for the remote machine. Else just state the
# machine names.
# Default: not set

sshlist=

# scp: Copy files to encode to the remote machine.
# Use if the fs can not be accessed on the remote machines
# Possible values: 0 - off, 1 - on
# Default: off

scp=0

# local: Turn off encoding on local machine, e.g. use only remote
# machines.
# Possible values: 0 - off, 1 - on
# Example: local=0 (off) turns off encoding on the
# local machine
# Default: on

local=1


#####
#
# Misc. options
#

# verbosity: Run silent (do not output comments, status etc.) (0), with
# minimal (1), normal without encoder msgs (2), normal (3), verbose (4)
# or extremely verbose (5).
# Possible values: 0...5
# Default: 3 - normal

verbose=3

# eject: Eject cd after finishing encoding.
# Possible values: 0 - off, 1 - on
# Default: off

eject=1

# ejectcmd: Command used to eject and close CD tray.
# Possible values: string
# Example: /usr/sbin/cdcontrol for FreeBSD
# Default: eject

ejectcmd=eject

# ejectopt: Options to command used to eject or close CD.
# Possible values: string or "{cddev}" to design the CD
# device.
# Note: Don't use options -t / close or eject,
#       RipIT knows when to eject or load the tray
# Default: {cddev}

ejectopt={cddev}

# quitnodb: Give up CD if no CDDB entry found.
# Useful if option --loop or --nointeraction are on.
# Default behaviour is to let operator enter data or to use default
# artist, album and track names.
# Possible values: 0 - off, 1 - on
# Default: off

quitnodb=0

# execmd: Execute a command when done with ripping. Quote the command
# if needed.
# Possible values: none - off, string - on
# Example: execmd="get_cover -a \"$artist\" -r \"$album\""
# Default: off

execmd=

# book: Create an audiobook, i. e. merge all tracks into one single
# file, option --ghost will be switched off and file suffix will be
# m4b. Make sure to use encoder faac, ripit will not check that.
# A chapter file will be written for chapter marks.
# Possible values: 0 - off, 1 - on
# Default: off

book=0

# loop: Continue with a new CD when the previous one is done.
# Option --eject will be forced. To start ripping process immediately
# after ejection of previous disc, use experimental argument 2. Ripit
# will restart as child process, one might see the prompt and it will
# be necessary to manually terminate the process! Do not use!
# Possible values: 0 - off, 1 - on, 2 - immediate restart, experimental
# Default: off

loop=1

# halt: Powers off machine after finishing encoding
# Possible values: 0 - off, 1 - on
# Default: off

halt=0

# nice: Sets "nice" value for the encoding process
# Possible values: 0..19 for normal users,
#                  -20..19 for user "root"
# Default: 0

nice=0

# nicerip: Sets "nice" value for the ripping process
# Possible values: 0..19 for normal users,
#                  -20..19 for user "root"
# Default: 0

nicerip=0

# threads: Comma separated list of numbers giving maximum
# of allowed encoder processes to run at the same time
# (on each machine when using sshlist).
# Possible values: comma separated integers
# Default: 1

threads=1

# md5sum: Create file with md5sums for each type of sound files.
# Possible values: 0 - off, 1 - on
# Default: off

md5sum=0

# wav: Don't delete wave-files after encoding.
# Possible values: 0 - off, 1 - on
# Default: off

wav=0

# normalize: Normalizes the wave-files to a given dB-value
# (default: -12dB)
# See [http://normalize.nongnu.org](http://normalize.nongnu.org) for details.
# Possible values: 0 - off, 1 - on
# Default: off

normalize=0

# normcmd: Command to be used to normalize.
# Possible values: string
# Example: normalize-audio (when using Debian)
# Upstream default: normalize

# We are running Debian so set to normalize-audio
normcmd=normalize-audio

# normopt: Options to pass to normalize
# Possible values: -a -nndB   : Normalize to -nn dB, default is -12dB,
#                  Value range: All values <= 0dB
#                  Example    : normalize -a -20dB *.wav
#                  -b         : Batch mode - loudness differences
#                               between individual tracks of a CD are
#                               maintained
#                  -m         : Mix mode - all track are normalized to
#                               the same loudness
#                  -v         : Verbose operation
#                  -q         : Quiet operation
# For further options see normalize documentation.
# Default: -b
# The -v option will be added by default according to RipITs verbosity

normopt=-b

# cdtoc: Create a toc file to burn the wavs with
# cd-text using cdrdao or cdrecord (in dao mode).
# Possible values: 0 - off, 1 - on
# Default: off

cdtoc=0

# inf: Create inf files to burn the wavs with
# cd-text using wodim or cdrecord (in dao mode).
# Possible values: 0 - off, 1 - on
# Default: off

inf=0

---

### Post by cave_man() on 2011-01-30
Hello Superdude_123,

Thank you for taking the time to post this how to. I am working on a very similar HTCP. In fact I found your post by searching for pcusa.

I have a pcusa remote that I have not been able to get working. Could you provide more detail on what you did to get yours working? Could you post your /etc/lirc/hardware.conf file?

I am running Ubuntu 10.10. I have installed LIRC. When I run irw and press buttons on my pcusa mce remote I don't see anything on the terminal.

Thank you

---

### Post by Superdude_123 on 2011-01-30
I just installed it and it worked right away with XBMC. It doesn't work at the moment in just ubuntu, and I didn't care to make it work directly, so in short, its only acting as a XBMC remote.

Here's the file you wanted


# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="false"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="lirc_dev lirc_mceusb"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

---

### Post by cave_man() on 2011-01-31
Hello again Superdude_123,

I'm still not getting any love from my psusa remote, even after setting up my hardware.cofig file like yours. Could you post your /etc/lirc/lircd.conf file? Could you tell me what version of Ubuntu you are running?

Thanks again.

---

### Post by Superdude_123 on 2011-01-31
I'm running 9.10, since at the time 10.04 had problems with XBMC.

Here's the file:



#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

---

