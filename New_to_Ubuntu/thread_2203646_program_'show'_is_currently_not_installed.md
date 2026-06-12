---
title: "program 'show' is currently not installed?"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by jinkeat.lim on 2014-02-04
I typed "sudo apt-get install nmh" and it installed, but I still do not have the "show" program. How do I get this?

---

### Post by sandyd on 2014-02-04
> **jinkeat.lim said:**
> I typed "sudo apt-get install nmh" and it installed, but I still do not have the "show" program. How do I get this?

try
```

/usr/bin/mh/show
```
to run show

---

### Post by jinkeat.lim on 2014-02-04
thanks, I went to that directory and see "show" in green. When I type "show -h" or "show pandas/ci/print_versions.py" it still says the program 'show' is not installed. I am using Ubuntu on VirtualBox on Win7

---

### Post by Dave_L on 2014-02-04
Unless that directory (/usr/bin/mh) is in your environment path, you'll still need to type the path in order to execute the script.

```
./show -h
```

The current directory is intentionally excluded from the path for security reasons.

---

### Post by brokenhachi on 2014-02-04
you can run "updatedb" and see if you can then use the command, as i believe /usr/bin should be default in your environment path.

if not, you can add it in ~/.bashrc like:

export PATH=${PATH}:/usr/bin

---

### Post by jinkeat.lim on 2014-02-04
I went to /usr/bin/mh and typed "./show -h", same message. Did I misunderstand?

typing "updatedb" gives me: 
updatedb: can not open a temporary file for `/var/lib/mlocate/mlocate.db'

sorry if these are basic questions

---

### Post by Dave_L on 2014-02-04
What's the output from:

```
dpkg --status nmh
dpkg --listfiles nmh
```

---

### Post by jinkeat.lim on 2014-02-04
```
jinkeatlim@jinkeatlim-VirtualBox:~$ dpkg --status nmh
Package: nmh
Status: install ok installed
Priority: optional
Section: mail
Installed-Size: 4474
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1.5-release-2
Replaces: mh
Provides: mail-reader, mh
Depends: libc6 (>= 2.11), libdb5.1, liblockfile1 (>= 1.0), libsasl2-2 (>= 2.1.24), libssl1.0.0 (>= 1.0.0), libtinfo5, netbase (>= 3.16-1)
Recommends: default-mta | mail-transport-agent
Suggests: exmh, mh-e, mh-book
Conflicts: mh
Conffiles:
 /etc/bash_completion.d/nmh e8d639078a9712af18d29ceee64e07b5
 /etc/nmh/scan.timely 6b864e7286d807be26476f7170905548
 /etc/nmh/scan.unseen 03f1dc08ba29bac4b6034bd2d350c17d
 /etc/nmh/rcvdistcomps f6302b37ff6a96bba0fd913cd420ec2a
 /etc/nmh/mhl.forward 1388b48bae0f85195a3d5083e851d56d
 /etc/nmh/scan.MMDDYY e67498fa17ccfe91f6638cb05f8d3652
 /etc/nmh/scan.mailx eac8750f746d0cb5e6699544002a4c9f
 /etc/nmh/forwcomps 9b824bb8e98919dc40d562c5f4d06674
 /etc/nmh/replcomps f320b2ea0983839fb5df632772004ae7
 /etc/nmh/mhl.format 7b1bc10ede5b8b72c5ee8ece040d1052
 /etc/nmh/mts.conf f9ce6bceaaee918388cd2cd058543f7b
 /etc/nmh/mhl.digest b0f5c8218d42516deb86fe99b5187324
 /etc/nmh/mhn.defaults b589804c9d395219788840e45dc38f79
 /etc/nmh/distcomps 4cf6135304c6d26f00ab037f28d2cb19
 /etc/nmh/digestcomps 9764fcefd27ef05d66e1ec53f853dd87
 /etc/nmh/scan.time 906ccc7f2eb867acab5ac3ce07a56a20
 /etc/nmh/components 38547b5f5aadade3133856f6ef45ec5c
 /etc/nmh/mhl.reply 738d77bf797e6357d1d3f1504200f04a
 /etc/nmh/scan.nomime 462a46aba6cabfa4d471f8638c34e97f
 /etc/nmh/scan.default 8ad0e8025239da383ebe046c7741a8ea
 /etc/nmh/MailAliases b695a4914d2b13ff3d71de765f999258
 /etc/nmh/scan.size 4457f16b3a75f33cc20c8619ae7d1f8d
 /etc/nmh/replgroupcomps e72180f9b8323067e94bf3ee75d1067f
 /etc/nmh/rcvdistcomps.outbox a647a43c5c234eaa8d73b7003edf3bfc
 /etc/nmh/mhl.body deb6a367bdd98a429aab44ed89ee2f03
 /etc/nmh/mhl.headers 5174d45b73ce74e1a54115490d44ca8a
 /etc/nmh/scan.YYYYMMDD b976b1fc09d0cfb95e20d1f3096b0e87
Description: set of electronic mail handling programs
 This is the nmh mail user agent (reader/sender), a command-line based mail
 reader that is powerful and extensible.  nmh is an excellent choice for
 people who receive and process a lot of mail.
 .
 Unlike most mail user agents, nmh is not a single program, rather it is a
 set of programs that are run from the shell.  This allows the user to
 utilize the full power of the Unix shell in coordination with nmh.  Various
 front-ends are available, such as mh-e (an emacs mode), xmh, and exmh (X11
 clients).
 .
 nmh was originally based on MH version 6.8.3, and is intended to be a
 (mostly) compatible drop-in replacement for MH.
Original-Maintainer: Nick Rusnov <nickrusnov@debian.org>
```


```
jinkeatlim@jinkeatlim-VirtualBox:~$ dpkg --listfiles nmh
/.
/etc
/etc/bash_completion.d
/etc/bash_completion.d/nmh
/etc/nmh
/etc/nmh/scan.timely
/etc/nmh/scan.unseen
/etc/nmh/rcvdistcomps
/etc/nmh/mhl.forward
/etc/nmh/scan.MMDDYY
/etc/nmh/scan.mailx
/etc/nmh/forwcomps
/etc/nmh/replcomps
/etc/nmh/mhl.format
/etc/nmh/mts.conf
/etc/nmh/mhl.digest
/etc/nmh/mhn.defaults
/etc/nmh/distcomps
/etc/nmh/digestcomps
/etc/nmh/scan.time
/etc/nmh/components
/etc/nmh/mhl.reply
/etc/nmh/scan.nomime
/etc/nmh/scan.default
/etc/nmh/MailAliases
/etc/nmh/scan.size
/etc/nmh/replgroupcomps
/etc/nmh/rcvdistcomps.outbox
/etc/nmh/mhl.body
/etc/nmh/mhl.headers
/etc/nmh/scan.YYYYMMDD
/usr
/usr/lib
/usr/lib/mh
/usr/lib/mh/rcvdist
/usr/lib/mh/mhl
/usr/lib/mh/conflict
/usr/lib/mh/rcvtty
/usr/lib/mh/rcvstore
/usr/lib/mh/spost
/usr/lib/mh/slocal
/usr/lib/mh/viamail
/usr/lib/mh/mhtest
/usr/lib/mh/post
/usr/lib/mh/ap
/usr/lib/mh/fmtdump
/usr/lib/mh/dp
/usr/lib/mh/rcvpack
/usr/share
/usr/share/doc
/usr/share/doc/nmh
/usr/share/doc/nmh/README
/usr/share/doc/nmh/NEWS.gz
/usr/share/doc/nmh/README.source
/usr/share/doc/nmh/README-ATTACHMENTS.gz
/usr/share/doc/nmh/README.developers.gz
/usr/share/doc/nmh/COPYRIGHT
/usr/share/doc/nmh/README.manpages.gz
/usr/share/doc/nmh/README.about
/usr/share/doc/nmh/COMPLETION-BASH.gz
/usr/share/doc/nmh/NEWS.Debian.gz
/usr/share/doc/nmh/FAQ.gz
/usr/share/doc/nmh/MAILING-LISTS
/usr/share/doc/nmh/MAIL.FILTERING
/usr/share/doc/nmh/COMPLETION-TCSH
/usr/share/doc/nmh/TODO.gz
/usr/share/doc/nmh/VERSION
/usr/share/doc/nmh/COMPLETION-ZSH.gz
/usr/share/doc/nmh/contrib
/usr/share/doc/nmh/contrib/replyfilter.gz
/usr/share/doc/nmh/contrib/build_nmh.gz
/usr/share/doc/nmh/contrib/nmh.spec
/usr/share/doc/nmh/README-components
/usr/share/doc/nmh/DIFFERENCES.gz
/usr/share/doc/nmh/README-HOOKS.gz
/usr/share/doc/nmh/changelog.Debian.gz
/usr/share/doc/nmh/README.SASL
/usr/share/doc/nmh/copyright
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/ap.8mh.gz
/usr/share/man/man8/install-mh.8mh.gz
/usr/share/man/man8/post.8mh.gz
/usr/share/man/man8/conflict.8mh.gz
/usr/share/man/man8/fmtdump.8mh.gz
/usr/share/man/man8/dp.8mh.gz
/usr/share/man/man7
/usr/share/man/man7/nmh.7mh.gz
/usr/share/man/man7/mh-chart.7mh.gz
/usr/share/man/man5
/usr/share/man/man5/mh-draft.5mh.gz
/usr/share/man/man5/mh_profile.5mh.gz
/usr/share/man/man5/mh-profile.5mh.gz
/usr/share/man/man5/mts.conf.5mh.gz
/usr/share/man/man5/mh-sequence.5mh.gz
/usr/share/man/man5/mh-format.5mh.gz
/usr/share/man/man5/mh-mail.5mh.gz
/usr/share/man/man5/mh-tailor.5mh.gz
/usr/share/man/man5/mh-alias.5mh.gz
/usr/share/man/man1
/usr/share/man/man1/rcvpack.1mh.gz
/usr/share/man/man1/mhmail.1mh.gz
/usr/share/man/man1/mhlist.1mh.gz
/usr/share/man/man1/unseen.1mh.gz
/usr/share/man/man1/inc.1mh.gz
/usr/share/man/man1/flist.1mh.gz
/usr/share/man/man1/folder.1mh.gz
/usr/share/man/man1/comp.1mh.gz
/usr/share/man/man1/mark.1mh.gz
/usr/share/man/man1/forw.1mh.gz
/usr/share/man/man1/rcvstore.1mh.gz
/usr/share/man/man1/flists.1mh.gz
/usr/share/man/man1/slocal.1mh.gz
/usr/share/man/man1/mhpath.1mh.gz
/usr/share/man/man1/scan.1mh.gz
/usr/share/man/man1/mhbuild.1mh.gz
/usr/share/man/man1/refile.1mh.gz
/usr/share/man/man1/pick.1mh.gz
/usr/share/man/man1/whatnow.1mh.gz
/usr/share/man/man1/mhparam.1mh.gz
/usr/share/man/man1/prompter.1mh.gz
/usr/share/man/man1/prev.1mh.gz
/usr/share/man/man1/folders.1mh.gz
/usr/share/man/man1/sortm.1mh.gz
/usr/share/man/man1/show.1mh.gz
/usr/share/man/man1/dist.1mh.gz
/usr/share/man/man1/ali.1mh.gz
/usr/share/man/man1/burst.1mh.gz
/usr/share/man/man1/new.1mh.gz
/usr/share/man/man1/msh.1mh.gz
/usr/share/man/man1/msgchk.1mh.gz
/usr/share/man/man1/send.1mh.gz
/usr/share/man/man1/rmm.1mh.gz
/usr/share/man/man1/rcvtty.1mh.gz
/usr/share/man/man1/fprev.1mh.gz
/usr/share/man/man1/mhn.1mh.gz
/usr/share/man/man1/repl.1mh.gz
/usr/share/man/man1/fnext.1mh.gz
/usr/share/man/man1/rmf.1mh.gz
/usr/share/man/man1/rcvdist.1mh.gz
/usr/share/man/man1/anno.1mh.gz
/usr/share/man/man1/whom.1mh.gz
/usr/share/man/man1/mhstore.1mh.gz
/usr/share/man/man1/next.1mh.gz
/usr/share/man/man1/mhl.1mh.gz
/usr/share/man/man1/packf.1mh.gz
/usr/share/man/man1/sendfiles.1mh.gz
/usr/share/man/man1/mhshow.1mh.gz
/usr/bin
/usr/bin/mh
/usr/bin/mh/msh
/usr/bin/mh/rmf
/usr/bin/mh/mhshow
/usr/bin/mh/burst
/usr/bin/mh/mhlist
/usr/bin/mh/mhstore
/usr/bin/mh/fnext
/usr/bin/mh/unseen
/usr/bin/mh/sendfiles
/usr/bin/mh/mhparam
/usr/bin/mh/whatnow
/usr/bin/mh/folders
/usr/bin/mh/mhmail
/usr/bin/mh/dist
/usr/bin/mh/folder
/usr/bin/mh/repl
/usr/bin/mh/rmm
/usr/bin/mh/flists
/usr/bin/mh/mark
/usr/bin/mh/sortm
/usr/bin/mh/install-mh
/usr/bin/mh/mhbuild
/usr/bin/mh/flist
/usr/bin/mh/comp
/usr/bin/mh/whom
/usr/bin/mh/fprev
/usr/bin/mh/next
/usr/bin/mh/send
/usr/bin/mh/show
/usr/bin/mh/msgchk
/usr/bin/mh/ali
/usr/bin/mh/pick
/usr/bin/mh/prompter
/usr/bin/mh/mhn
/usr/bin/mh/forw
/usr/bin/mh/scan
/usr/bin/mh/packf
/usr/bin/mh/inc
/usr/bin/mh/anno
/usr/bin/mh/mhpath
/usr/bin/mh/prev
/usr/bin/mh/refile
/usr/bin/mh/new
/usr/share/man/man7/mh.7.gz
/usr/share/man/man1/folders.1.gz
/usr/share/man/man1/flists.1.gz
```

---

### Post by Dave_L on 2014-02-04
Ok, that looks reasonable. By the way, it's helpful when posting code or output to use the [ code ] ... [ /code ] or [ quote ] ... [ /quote ] tags (without the spaces).

What about sandyd's suggestion: 

```
/usr/bin/mh/show
```

Does that also fail?

---

### Post by jinkeat.lim on 2014-02-04
yes, I tried both: 
```
/usr/bin/mh/show
```

and going to /usr/bin/mh and typing:
```
./show
```

both output: 
> show: Doesn't look like nmh is installed.  Run install-mh to do so.

As an aside, thanks for the comment on the forums posting syntax. Please let me know if I misunderstood.

---

### Post by brokenhachi on 2014-02-04
ahhh, seems that show is working but doesnt recognize the nmh package? did you try running install-mh?

if not, 
```
sudo dpkg-reconfigure nmh
```

then try again..

---

### Post by gerard on 2014-07-11
I have the sam problem with packf, Iam running debian 7.4. So it seems to be an upstream problem.

---

