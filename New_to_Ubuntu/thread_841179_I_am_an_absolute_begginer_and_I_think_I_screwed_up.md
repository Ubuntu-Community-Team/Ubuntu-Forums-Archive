---
title: "I am an absolute begginer and I think I screwed up"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by DarknessEnemy on 2008-06-26
Hi everybody, I got a problem and I hope your wisdom could beat out my mistake. 

I was installing cinelerra. and I suddenly got a mistake. and I got this: 

E: Type '<html>' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.                                 

(Sorry, I need to know how to write on CODE mode)

I found in this forum a solution but didn't worked. what else could it be?

THanks in advance.

---

### Post by wormser on 2008-06-26
Post the results of the following command.

```
gedit /etc/apt/sources.list
```

---

### Post by _sphinx_ on 2008-06-26
```
cat /etc/apt/sources.list.d/akirad.list
```
post the output. I think that would be necessary.

---

### Post by DarknessEnemy on 2008-06-26
```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

# Treviño’s Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs…
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy universe
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu hardy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by DarknessEnemy on 2008-06-26
```
                              <html>

                                 <head>
                                 <style>

                                 a:link { font-family: arial, verdana; font-sizw: 11px; color: #000000; text-decoration: none; }
a:visited { font-family: arial, verdana; font-sizw: 11px; color: #000000; text-decoration: none; }
a:active { font-family: arial, verdana; font-sizw: 11px; color: #000000; text-decoration: none; }
a:hover { font-family: arial, verdana; font-sizw: 11px; color: #000000; text-decoration: underline; }

  font { font-family: arial, verdana; font-sizw: 11px; color: #000000; text-decoration: none; }

  td{ font-family: arial, verdana; font-sizw: 10px; text-decoration: none; }
  table{ font-family: arial, verdana; font-sizw: 11px; text-decoration: none; }
  body { background-color: #F0F0F0; scrollbar-face-color: #6E788C; scrollbar-shadow-color: #696969; scrollbar-highlight-color: #cfcfcf; scrollbar-3dlight-color: #cccccc; scrollbar-darkshadow-color: #808080; scrollbar-track-color: #9B9FA7; scrollbar-arrow-color: #000000 }

  .title { font-family: arial, verdana; font-size: 9pt; font-weight: normal; }
  .distributers { font-family: arial, verdana; font-size: 11pt; font-weight: normal; }
  .info { font-family: arial, verdana; font-size: 8pt; font-weight: normal; }
  .design { font-family: arial, verdana; font-size: 8pt; font-weight: normal; }

  .menu { border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 8pt; font-weight: normal; }
  .cellheader { border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 20pt; font-weight: normal; color: #F1F1F1; }
  .scellheader { border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 15pt; font-weight: normal; color: #F1F1F1; }
  .bigcellheader { border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid;  font-family: verdana, arial; font-size: 30pt; font-weight: normal; color: #F1F1F1; link: #F1F1F1; vlink: #F1F1F1; }

  .tblheader { background-color: #AAAAAA; border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 14pt; font-weight: normal; }
  .tdshade1 { background-color: #DDDDDD; border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 10pt; font-weight: normal; }
  .tdshade2 { background-color: #EEEEEE; border-top: 1px #374646 solid; border-left: 1px #374646 solid; border-right: 1px #374646 solid; border-bottom: 1px #374646 solid; font-family: verdana, arial; font-size: 10pt; font-weight: normal; }


  </style>

     </head>

     <body bgcolor="#ffffff">

     <table bgcolor=#ffffff link=#0000ee vlink=#0000ee text=#000000 border=0 align="center" width="100%">
     <tr class=cellheader>
     <td bgcolor=#788298><center><b>This Account Has Been Suspended</b></center></td>
     </tr>
     </table>
     Please contact the billing/support department as soon as possible.
     </html>

```

---

### Post by wormser on 2008-06-26
Where did you get the directions to add that repository?  It looks like you only got the first part of the command.  The correct directions are [here]("http://cinelerra.org/getting_cinelerra.php#ubuntu").  You will probably have to delete that file first. This will just move it with the following command.

```
sudo mv /etc/apt/sources.list.d/akirad.list /etc/apt/sources.list.d/akirad.list.old
```Then set up the repository.

```
sudo wget http://repository.akirad.net/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
``````
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key  add - && sudo apt-get update
``````
sudo apt-get update
```Now you can install the package you wanted.

---

### Post by Elfy on 2008-06-26
You need to delete the file and start again with the commands, run each command seperately in terminal

```
sudo rm /etc/apt/sources.list.d/akirad.list
sudo wget http://repository.akirad.net/dists/hardy.list -O /etc/apt/sources.list.d/akirad.list
wget -q http://repository.akirad.net/dists/akirad.key -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by IbnKuldun on 2008-06-26
That last one, which is presume is */etc/apt/sources.list.d/akirad.list* does not look right at all, and is most definitely causing the problem. It seems that you downloaded a html file instead.

Try this, first remove that file as it is corrupt.

```

sudo rm /etc/apt/sources.list.d/akirad.list

```

and then try the procedure you listed in your first post again. I just tested it so it should work.

---

### Post by DarknessEnemy on 2008-06-26
Il install it later, its pretty late and gotta resume my abs XD.

Anyway thanks, Thanks a lot!!! What got me scared is that the synaptic manager didn't worked. I will install it. BUt right now, I got some stuff to do.

Really, really. Thanks a lot!!! XD

BTW: What a fast answer!!! I was about to check at the dawn.

---

