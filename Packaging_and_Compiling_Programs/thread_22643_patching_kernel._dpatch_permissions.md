---
title: "patching kernel. dpatch permissions"
date: 2005-03-28
forum: Packaging and Compiling Programs
---

### Post by arnieks on 2005-03-28
Hi, I am trying to get my orinoco based wireless cards in monitor mode. It looks like I may need to patch the kernel source. So I decided to install the 2.6.11 kernel and patch it with the orinoco-2.6.11-rfmon-dragorn-1.diff patch.
I was following the steps outlined in [http://www.ubuntulinux.org/wiki/Ker...geDetailedHowto](http://www.ubuntulinux.org/wiki/Ker...geDetailedHowto)
but I come unstuck at the point where I have to make a dpatch.
this is my command
sudo dpatch patch-template -p "orinoco-2.6.11-rfmon-dragorn-1" "orinoco rfmon patch" < {pathto}orinoco-2.6.11-rfmon-dragorn-1.diff > debian/patches/orinoco-2.6.11-rfmon-dragorn-1.dpatch
this is the answer I get
bash: debian/patches/orinoco-2.6.11-rfmon-dragorn-1.dpatch: Permission denied

Now I take it this is some sort of limitation of sudo?
How do I get around it?
(I am using hoary with kernel 2.6.10-5-386 at the moment)
Thanks for your help
arnie

---

### Post by jerome bettis on 2005-03-28
try doing sudo -s <enter>  then type the command.

---

### Post by arnieks on 2005-03-28
[QUOTE=jerome bettis]try doing sudo -s <enter>  then type the command.[/QUOTE]
Thanks for that, but I was just going to reply to my own email.  I fixed it by changing permissions to the user of debian/patches, and also of the patch itself.
( I realised there was no need to do it as root) 
but I will remember sudo -s for the next time I am stumped

Arnie

---

### Post by fsshl on 2005-10-05
not directly reply above threads's question, but related.

some patch problem, please help

I download  somefile.orig.tar.gz  and  somefile.diff.gz
I gunzip both files
then
patch somefile.orig.tar  somefile.diff
then it 's directory has little bit weired for me, like to see advancer's recheck
-----------------------------------------------------------------------------------------

patch util-linux_2.12p.orig.tar                      util-linux_2.12p-6ubuntu5.diff

root@etutor:~/src/somepatch#  ls
00list                 50hurd.dpatch                       fstab.example2         README.script
10agetty.dpatch        60_opt_O1.dpatch                    hwclock.sh             rejected-upstream
10cal-widechar.dpatch  70umount-disableuserremount.dpatch  lintian-override       rules
10cfdisk.dpatch        71swsusp-resume.dpatch              mime.util-linux        shlibs.local
10debian.dpatch        bsdutils.postinst                   mount.fstab            util-linux_2.12p-6ubuntu5.diff
10fstab.dpatch         bsdutils.prerm                      mount.postinst         util-linux_2.12p.orig.tar
10license.dpatch       changelog                           mount.prerm            util-linux_2.12p.orig.tar.orig
10misc.dpatch          changelog.Debian-mount.old          postinst               util-linux-locales.postinst
10mount.dpatch         conffiles                           postrm                 util-linux-locales.prerm
10sparcumount.dpatch   control                             preinst
20guesshelper.dpatch   copyright                           prerm
20xgethostname.dpatch  fdformat                            README.Debian.hwclock
root@etutor:~/src/somepatch#
-------------------------------------------------
fsshl

---

