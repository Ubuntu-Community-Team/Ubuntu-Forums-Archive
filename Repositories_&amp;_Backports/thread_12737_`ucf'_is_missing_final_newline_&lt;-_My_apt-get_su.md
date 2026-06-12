---
title: "`ucf' is missing final newline &lt;- My apt-get suddenly doesn't work"
date: 2005-01-26
forum: Repositories &amp; Backports
---

### Post by IrIT on 2005-01-26
Hi all! :D

First of all, nice distro, nice community! \\:D/ 

Yesterday i wantet to install gFTP. So as always, i typed: 'Sudo apt-get install gFTP'
But after it has downloaded, i get the following error, when it's trying to install: 

> /var/cache/apt/archives/gftp-text_2.0.17-6_i386.deb (--unpack):
 files list file for package `ucf' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (1)

I just thought, that it was only gFTP i had problems with. 
But now i have discovered, that no matter what program i try to install, i get the samme error :(

I'm completly new to linux, so maybe this is a very stupid question. 

Also, sorry for my bad english. But english isn't mu native language.

---

### Post by IrIT on 2005-01-27
Aren't there anyone who can help me? Or do i have to reinstall Ubuntu?

---

### Post by fng on 2005-03-13
i have the same problem :(

---

### Post by az on 2005-03-13
Try:

sudo dpkg --clear-avail

Did you have any nasty (non-official) repositories in your list?  How about unofficial packages? (like skype or ymessenger)

---

### Post by fng on 2005-03-14
That didnt work.  Still the same error.

I only had backports + wesnoth as "unofficial repos".  I commented those, run an apt-get update but still the same problem.

---

### Post by oxlarge on 2005-09-16
I had a similar problem after fsck corrupted some of my files during a fix, and the way that I got around the problem was by moving the entire /var/lib/dpkg/info to /var/lib/dpkg/info_moved, and create a new info dir. I then successfully installed a random pkg (the 'acct' pkg) using synaptic. Since this worked fine, I moved the acct files in the new info dir to the info_moved directory, and then moved the entire info_moved directoy back to info. Phew. 

That is to say:

# mv /var/lib/dpkg/info/ /var/lib/dpkg/info_moved

# mkdir /var/lib/dpkg/info

<installed the acct pkg using synaptic>

# mv /var/lib/dpkg/info/*  /var/lib/dpkg/info_moved

# rm /var/lib/dpkg/info

# mv /var/lib/dpkg/info_moved /var/lib/dpkg/info

Voila

---

### Post by Schuler on 2006-06-23
I attempted to do this, but it appears that after updating to "Dapper", I no longer have permission to access/alter most files.

So far for me, Ubuntu = ](*,)

---

### Post by Fyre2012 on 2006-07-10
I'm having similar issues with my Dell Inspiron 8200 laptop.

Did a fresh clean install... first thing i did was upgrade everything the update manager flagged (about 90 updates), i let it fly, new kernel, then x stops booting.

Got the same error as IrIT, except i'm getting it trying to apt-get install nvidia-glx  to reconfig X... nice recursive bug of DOOM

I'll post if i come up with a solution

=)

---

### Post by hordur on 2006-10-19
Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.

---

### Post by vstoos on 2007-04-22
I found resolution of this problem here [http://finkproject.org/faq/usage-fink.php](http://finkproject.org/faq/usage-fink.php)

Google forever!

---

### Post by zasf on 2007-04-28
I also was affected, here is the [launchpad bug #108189]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189").

Here is how I fixed it:

[INDENT]**1)** First I basically followed what ourdour suggested[/INDENT]
```
mv /var/lib/dpkg/info /var/lib/dpkg/info_old
mkdir /var/lib/dpkg/info
apt-get update && apt-get -f install
mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
rm -f /var/lib/dpkg/info
mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info
```

[INDENT]**2)** I ended up with apt complaining about seriuos things[/INDENT]
```
dpkg: serious warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `oclock' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ttf-bengali-fonts' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxau6' missing, assuming package has no files currently installed.
[...]

```
for about 500 packages and I also noticed that if I reinstalled each package, apt would not complain any more, so I wrote this script (where apt.txt contains the above messages):

```
matteo@z2:~$ cat fix.sh 
#!/bin/bash

if [ `id -u` != "0" ]; then
        echo "Sorry, you are not root."
        exit 1
fi

# octal escape sequence
# \47 = "'"
# \140 = "`"

list=""

for i in $(cat apt.txt | awk 'BEGIN { FS=" |\047|\140" } { print $10 }' )
do
        echo $i
        case $i in
        "linux-headers-2.6.20-12" | "linux-image-2.6.20-12-generic" | "linux-headers-2.6.20-12-generic" | "linux-restricted-modules-2.6.20-12-generic" | "linux-restricted-modules-2.6.20-12-generic");;
        "coreutils" | "debianutils");;
        "perlapi-5.8.7" | "liblocale-gettext-perl");;
        "dpkg" | "diveintopython");;
        "libpam0g");;
        * ) list="$list $i";;
        esac
done

echo $list
apt-get --reinstall install $list

```

wich basically lists packages for reinstall. Note that apt still might complain (packages no longer available, etc), to avoid this include such packages in the 'case' loop. After a bit of running the script, you'll fix apt.

I know it's a workaround but better than having a broken system.

---

### Post by lmarzulo on 2007-05-11
There is an easy way to fix this problem without having those serious warnings. I did it and it worked out fine. I found the solution in the following web site: [http://finkproject.org/faq/usage-fink.php](http://finkproject.org/faq/usage-fink.php)

I'll just copy it here:

> I can't install or remove anything, because of a problem with a "files list file".

A: Typically these errors take the form:

[QUOTE]files list file for package packagename contains empty filename

or

> files list file for package packagename is missing final newline

This can be fixed, with a little work. If you have the .deb file for the offending package currently available on your system, then check its integrity by running

> dpkg --contents full-path-to-debfile
        

e.g.

> dpkg --contents /sw/fink/debs/libgnomeui2-dev_2.0.6-2_darwin-powerpc.deb

If you get back a listing of directories and files, then your .deb is OK. If the output is something other than directories and files, or if you don't have the .deb file, you can still proceed because the error doesn't interfere with builds.

If you have been installing from the binary distribution or you know for sure that the version in the binary distribution is the same as what you have installed (e.g. by checking the package database), then you can get a .deb file by running sudo apt=get install --reinstall --download-only packagename . Otherwise you can build one yourself by running fink rebuild packagename , but it won't install yet.

Once you have a valid .deb file, then you can reconstitute the file. First become root by using sudo -s (enter your administrative user password if necessary), and then use the following command:

> dpkg -c full-path-to-debfile | awk '{if ($6 == "./"){ print "/."; } \
else if (substr($6, length($6), 1) == "/")\
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}'\ 
> /sw/var/lib/dpkg/info/packagename.list

e.g.

> dpkg -c /sw/fink/debs/libgnomeui2-dev_2.0.6-2_darwin-powerpc.deb | awk \
'{if ($6 == "./") { print "/."; } \
else if (substr($6, length($6), 1) == "/") \
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}' \ 
> /sw/var/lib/dpkg/info/libgnomeui2-dev.list

What this does is to extract the contents of the .deb file, remove everything but the filenames, and write these to the .list file.[/QUOTE]

In my case, the dpkg/info directory was not in /sw/var/lib/dpkg/info. It was in /var/lib/dpkg/info instead.

I hope that helps. Altough I found the solution in another web site, when I googled for the solution, I found this thread and, since this forum has always been the savior for my problems I decided to register and post it so that the solution can be found by everyone.

---

### Post by SSmythie on 2007-11-29
I only needed to remove the offending package's information files:

> cd /var/lib/dpkg/info

# (effectively) hide the corrupt package's information files by moving them out of this directory (in my case it was ntfs-config)

> sudo mkdir info_hidden
> sudo mv ntfs* info_hidden

I could now install and uninstall applications again.

Details:
I had to run the fsck utility, but can't really blame that utility because it was just trying to repair damages done when I had to do a hard reset of my OS: Ubuntu 7.10 64-bit.

I read the hints/solutions already submitted, but found that I only had to hide the offending packages; not the entire contents of the /var/lib/dpkg/info folder.

---

### Post by Fredizdman on 2008-09-03
> **hordur said:**
> Hello.

I had a similar problem with another package.
I spent a lot of time trying to fix and I finally managed to do it.
Here's what I did:
1. Edit the file /var/lib/dpkg/status , look for the listing for the broken package, remove the info for that package.
2. mv /var/lib/dpkg/info /var/lib/dpkg/info_old
3. mkdir /var/lib/dpkg/info
4. apt-get update, apt-get -f install
5. mv /var/lib/dpkg/info/* /var/lib/dpkg/info_old/
6. rm -f /var/lib/dpkg/info
7. mv -f /var/lib/dpkg/info_old /var/lib/dpkg/info

I don't know if all the steps are necessary, maybe 1 and 4 are enough.



This solution worked for me. (libhtml-tree-perl) was the offending package. I only did steps 1 and 4 just to see and it did work.

---

### Post by inzpektor on 2009-01-02
Same problem here!

I'm running Ubuntu off of a USB-stick, and there must have been a small connection-glitch, anyway it suddenly remounted it ( my / ) as read-only, and I had to reboot into LiveCD and fsck the d... thing from there.

After successful fsck'ing :-), it had put ~800 files from /var/lib/dpkg/info into /lost+found with the #<number>-names that are *so useful*.  So what I wanted was to have the /var/lib/dpkg/info files regenerated from scratch based on the packages in /var/lib/dpkg/status.

I made this script that will download the .deb files for each and every package in /var/lib/dpkg/status, extract the control files, and put them in an info-dir in the current directory.  All you then have to do is to copy these files ( ./info/* ) to /var/lib/dpkg/info.

[B]Beware, it runs for some time and consumes a lot of bandwidth (basically, the entire codebase for your system is downloaded once again!)
[/B]

---

### Post by ben_l on 2009-01-06
.

---

