---
title: "How to Create Local Repository on Hard Disk"
date: 2005-03-15
forum: Repositories &amp; Backports
---

### Post by asundaresan on 2005-03-15
Hi,

I have installed ubuntu on a machine that does not have internet access. However I'd like to install and update packages. Is there any way I can download the whole repository (or a substantial part of it) from somewhere and copy that to the hard disk. I imagine that I can then set it in /etc/apt/sources.list.

- what do i download?
- where can i download it from?

is there any difference between apt for debian and apt for ubuntu other than the repository?

aravind.

---

### Post by Aurels on 2005-03-16
That's a good question, i'm really interested on using a 'local repository' too.

---

### Post by graabein on 2005-03-17
I also have no internet at home. I've copied the repos from the Warty install CD onto my harddrive and got that to work. I'd like to download the universe...  :-k 

Here are some links to read up on the basics... I don't know the difference between Debian and Ubuntu packages as I'm rather new to Linux myself. I have in fact not installed an application yet because of package dependencies... If you don't count Neverball data files, hehe.

[http://www.debian.org/doc/manuals/repository-howto/repository-howto.html](http://www.debian.org/doc/manuals/repository-howto/repository-howto.html)
[http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by oracledarren on 2005-03-17
I asked this question here and I am struggling to find where the answer is.

The basic answer I think you are looking for is once you have installed a machine with all the good stuff you want to want to be able to transfer that in some way so that it can be installed on another previously installed machine.

All of the downloaded files are stored in /var/cache/apt which you can copy to a cd or dvd but there is a file you need to create before doing it called packages.

If you look at the posts I have made and look for the one that says creating a sources cd you will find the answer there.

So I cant be more help just now, but I gotta fly  :sad:

---

### Post by izut on 2005-03-18
I'll describe a few steps I made to construct my personal repository. My current setup is:

- Ubuntu 'Warty' installed with Internet access (at work)
- Ubuntu 'Warty' installed without Internet access (at home)

Using the usual Ubuntu repositories, I updated the system and installed some packages I wanted (ruby, apache, mysql, etc). You don't need to install that on the host system, just use the apt-get's download only option. All files downloaded from repositories are in the /var/cache/apt/archives directory in the host system. I did these steps:

1. Created /opt/repo directory (could be the home directory)
2. Created the directory /opt/repo/binary (copied from Debian specs)
3. Copied all debs from my update from /var/cache/apt/archives to /opt/repo/binary
4. Executed dpkg-scanpackages like this:
# pwd
/opt/repo
# dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz
5. Burned a CD with its contents

For use that in my standalone host, I did this:
# apt-cdrom add
...

I think it's all.

Cya.

---

### Post by alex-gurgel on 2005-03-18
Hey !!!! I've looking for this !!!! And only see an answer here !

Very thanks !!!

---

### Post by Aurels on 2005-03-20
OK. Fine!

---

### Post by Maniak on 2005-03-26
OK - here is a slightly different setup to play/help me with. I have a couple of computers on a network at home. I am using dial-up to connect to the net. I don't want to have to download the patches/upgrades/new programs twice (or more) - what do I need to change from the above posts to turn my /var/chache/apt/archives into a local respository for the other computer(s) on the network? Or is there another way to update all computers on the network?

---

### Post by marcolino on 2005-03-30
thanks it works great.

---

### Post by urbandryad on 2005-09-30
Can you do this for a USB flash drive instead of a CD? I don't have a CD burner. :(

---

### Post by Brad wilkinson on 2005-10-01
[QUOTE=Maniak]OK - here is a slightly different setup to play/help me with. I have a couple of computers on a network at home. I am using dial-up to connect to the net. I don't want to have to download the patches/upgrades/new programs twice (or more) - what do I need to change from the above posts to turn my /var/chache/apt/archives into a local respository for the other computer(s) on the network? Or is there another way to update all computers on the network?[/QUOTE]

You want to read up on a thing called apt-proxy. It allows you to set one of your machines as a proxy (for apt-get) so any of your local machines go through it to get to the repositories on the net. anything that one machine requests is cached for other machines to get localy, instead of using the internet.

IMO if you have two or more machines using Ubuntu/debian and update them often, it is only polite to set up apt-proxy. somone has to pay for the server bandwidth.

---

### Post by bluhound on 2005-10-14
I got this out from [http://puggy.symonds.net/~rajesh/localdeb.html](http://puggy.symonds.net/~rajesh/localdeb.html).

1. Create a file overridefile (u can give any name to this file) with the contents of the directory (list of deb filenames in that directory)

          * cd /var/pkgs/helix
          * find . -name "*.deb" > overridefile

      Now the 'overridefile' should look something like this :

      ./aalib1_1.2-helix1_i386.deb
      ./abiword_0.7.10-helix1_i386.deb
      ./bonobo_0.23-helix4_i386.deb
      ./codecommander_0.9.7-helix1_i386.deb
      ./eog_0.5-helix1_i386.deb

There are other options which u can specify in the override file 
which I don't need.  man dpkg-scanpackages for further details on this.


   2. dpkg-scanpackages . overridefile > Packages

   3. Add the following in /etc/apt/sources.list

      deb file:/var/pkgs/helix ./

   4. apt-get update

Now you can do apt-get install < any package from that directory > :-)

---

### Post by chrisblack on 2005-10-24
I've a similar issue - pc at home no internet connection (winmodem!!!) but internet connection at work

However I've no ubuntu at work, and no chance of installing it, so is there anyway I can download and burn the repositories to CD, so I can add the CD at home?

Or perhpas the unofficial 5.04 add-on cd is what I need??

Thanks

Chris

---

### Post by khirsha on 2005-10-24
I've some PC with kubuntu installed on, that are not connected to the net, that i like to mantain updated.
I use the program [COLOR="Blue"]**"debmirror"**[/COLOR] (you find it in the official repositories) to mantain a copy of the repositories of i386 acrhitecture without source package in a external HD.

[B]"debmirror -v --host=archive.ubuntu.com --method=http --root=ubuntu --arch=i386 --dist=hoary,hoary-updates,hoary-security --section=main,multiverse,restricted,universe --nosource --passive hoary
"[/B]
  It works very well, i've just some problem with the signature of the release file of the security section so i've to append the option --ignore-release-gpg

It takes about 9,9 GB of disc space.

---

### Post by UbuWu on 2005-10-24
[QUOTE=chrisblack]
However I've no ubuntu at work, and no chance of installing it, so is there anyway I can download and burn the repositories to CD, so I can add the CD at home?
[/QUOTE]

If you have a dvd burner at work, burn the dvd's from this page and you will have the whole repositories on dvd (main, universe and multiverse):
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

---

### Post by chrisblack on 2005-10-24
> If you have a dvd burner at work, burn the dvd's from this page and you will have the whole repositories on dvd (main, universe and multiverse):
[http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)

Thanks

Thats pretty cool - however, I've no dvd drive (only cdrom) on my pc at home... any other suggestions??

---

### Post by No_Code on 2005-10-27
One thing you may want to try in the absence of a DVD burner is to download the ISO images and mount them over the loopback. Note, you do NOT necessarily need to burn them to make it work on your system. The following steps will allow you to use an ISO image without burning it to a physical disk and inserting that disk:

sudo modprobe loop
sudo mkdir /mnt/mountpoint
sudo mount -o loop diskimage.iso /mnt/mountpoint

Of course, substitute in the proper information for mountpoint and diskimage.iso, and you should be in business!

---

### Post by libertyaikido on 2005-11-22
[QUOTE=khirsha][B]"debmirror -v --host=archive.ubuntu.com --method=http --root=ubuntu --arch=i386 --dist=hoary,hoary-updates,hoary-security --section=main,multiverse,restricted,universe --nosource --passive hoary
"[/B]
  It works very well, i've just some problem with the signature of the release file of the security section so i've to append the option --ignore-release-gpg

It takes about 9,9 GB of disc space.[/QUOTE]

Have you found a resolution to the gpg signature problem?  It would be nice to have a complete (feature-wise) mirror.

---

### Post by lotusleaf on 2005-11-22
[**"HOWTO: Custom repo (local or remote)"**](http://www.ubuntuforums.org/showthread.php?t=42862)

---

### Post by libertyaikido on 2005-11-23
[QUOTE=lotusleaf][**"HOWTO: Custom repo (local or remote)"**](http://www.ubuntuforums.org/showthread.php?t=42862)[/QUOTE]

I'm not sure I understand how that link provided a resolution to the signature problem.

The signature problem occurs when trying to mirror a remote Ubuntu repository to a local directory using debmirror.  The thread provided doesn't deal with mirroring Ubuntu repositories.  It only deals with creating a local repository of whatever .debs you may have lying around.

I need a complete (including digital signatures) mirror of a remote Ubuntu i386 repository sitting on my hard drive for network installs.  Any idea how to resolve the signature problem?

---

### Post by lotusleaf on 2005-11-24
[QUOTE=libertyaikido]I'm not sure I understand how that link provided a resolution to the signature problem.[/QUOTE]

I was responding to the original post and directly addressing the topic of this thread, not later posts in this thread. A number of people have missed the howto I linked to because when searching the forums they would search for "respository" rather than "repo". I've posted this link to the howto to duplicate threads of the initial topic of this thread.

I hope you find a solution for what you're looking for, sorry but I hadn't followed the entire flow of discussion, and the branching out to other issues.

---

### Post by vavoem on 2006-05-09
](*,)  screwed up sorry

---

### Post by popey on 2006-10-30
Just in case anyone finds this thread I thought I'd post this here:- 

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

---

### Post by 67comet on 2006-10-30
I'm also reading around trying to see how to add /media/IAUDIO_A2/binary/ to my apt on a networkless box ..

Hear to the grind stone,
Justin

---

### Post by speeddemon8803 on 2007-04-13
> **urbandryad said:**
> Can you do this for a USB flash drive instead of a CD? I don't have a CD burner. :(

mmhmm..your computer can boot from a flash drive right?

if so..extract the iso image...to the usb flash drive...restart...set bios to boot from flash drive..bam!

I actually found this out by mistake! heh!

---

### Post by goats_not_bombs on 2007-07-29
For USB, and all other media besides CD, here is a workaround that I came up with:

// Get the packages:
// How I did this was download the server CD as ISO and mounted it but other options are previously posted.
// First thing that I do is copy the files that I want on to the hard drive, but this is not manditory.

mkdir (the directories that you want to mount to:  most likely in the /media directory)

// Mounts the filesystem
cd to the directory that you want to mount from
 sudo modprobe loop
 sudo mount [ubuntu-7.04-server-i386.iso] [/media/iso/] -t iso9660 -o loop

// Changes the logical link for cdrom that apt-cdrom uses
// Change the cdrom pointer to the mounted directory that you want to get the package info
// remember ln (link making utility) is backwards in usage. 
  cd to /
    ls -l
    you should see  =>  lrwxrwxrwx   1 root root    11 2007-07-27 04:48 cdrom -> media/cdrom
    sudo rm -f cdrom 
    sudo ln -s /media/iso cdrom

// use apt-cdrom as the installer
// *note: if you don't use sudo with this command, you will have to remount
 sudo apt-cdrom add -d /media/iso

//  Run your package manager
  apt-get update    // at the command prompt
  System -> Administration -> Synaptics Package Manager  // for the GUI


#####################

// *** I don't think that this step needs to happen but here it is just in case
cd to /dev
 ls -l | less
 // you should see  =>  rwxrwxrwx 1 root root           4 2007-07-29 08:02 cdrom -> scd0
 sudo rm -f cdrom
 ln -s -i /media/iso cdrom

---

### Post by Angus77 on 2008-05-07
I love living in Japan:

```
21.1 GiB will be downloaded into archive.
Downloading 25096 archive files using 20 threads...
Begin time: Thu May  8 09:38:52 2008
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Thu May  8 09:43:43 2008
```

21.1 GiB in 15 minutes!  WOOHOO!

---

### Post by arun.in on 2008-10-22
Check
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/]("http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/")

---

### Post by mardangga on 2009-06-03
> **goats_not_bombs said:**
> For USB, and all other media besides CD, here is a workaround that I came up with:

// Get the packages:
// How I did this was download the server CD as ISO and mounted it but other options are previously posted.
// First thing that I do is copy the files that I want on to the hard drive, but this is not manditory.

mkdir (the directories that you want to mount to:  most likely in the /media directory)

// Mounts the filesystem
cd to the directory that you want to mount from
 sudo modprobe loop
 sudo mount [ubuntu-7.04-server-i386.iso] [/media/iso/] -t iso9660 -o loop

// Changes the logical link for cdrom that apt-cdrom uses
// Change the cdrom pointer to the mounted directory that you want to get the package info
// remember ln (link making utility) is backwards in usage. 
  cd to /
    ls -l
    you should see  =>  lrwxrwxrwx   1 root root    11 2007-07-27 04:48 cdrom -> media/cdrom
    sudo rm -f cdrom 
    sudo ln -s /media/iso cdrom

// use apt-cdrom as the installer
// *note: if you don't use sudo with this command, you will have to remount
 sudo apt-cdrom add -d /media/iso

//  Run your package manager
  apt-get update    // at the command prompt
  System -> Administration -> Synaptics Package Manager  // for the GUI


#####################

// *** I don't think that this step needs to happen but here it is just in case
cd to /dev
 ls -l | less
 // you should see  =>  rwxrwxrwx 1 root root           4 2007-07-29 08:02 cdrom -> scd0
 sudo rm -f cdrom
 ln -s -i /media/iso cdrom

Gee.... Thanks goats_not_bombs.
This is what I'm looking for. B4 I read this thread, I've already set everything like what's you write on this thread, except change the symbolic link for cdrom. I'm don't know how to change the default cdrom to directory that I want (like /mnt/cdrom). And now, I know the problem. I've never expect the problem just the symbolic link (God, Jesus!!).
Btw, really thx for this thread. N sorry 4 my poor english. You're really helpful.

---

