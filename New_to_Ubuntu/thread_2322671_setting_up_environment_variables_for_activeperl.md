---
title: "setting up environment variables for activeperl?"
date: 2016-04-29
forum: New to Ubuntu
---

### Post by xander2077 on 2016-04-29
recently i installed activeperl and it went without a hitch, except i am confused about one issue. the isntructions are not very detailed on how to add the PATH and MAN variables in lubuntu so i can have the program in my menu

so here are the instructions i get in the terminal

```
ActivePerl has been successfully installed at /home/stealth/ActivePerl-5.22.

Please modify your startup environment by adding:

   /home/stealth/ActivePerl-5.22/site/bin:/home/stealth/ActivePerl-5.22/bin to PATH
   /home/stealth/ActivePerl-5.22/site/man:/home/stealth/ActivePerl-5.22/man to MANPATH

For general questions or comments about ActivePerl, please
contact us at <support@activestate.com>.

```

and here are the instructions on the website for this version of activeperl

```
We suggest adding the following line to your .bash_profile file:

         PATH=$PATH:/home/<username>/bin     

Also, we suggest that you create symbolic links to the binaries:

    ln -s /home/<username>/ActivePerl-5.22/bin/perl /home/<username>/bin/perl
    ln -s /home/<username>/ActivePerl-5.22/bin/ppm /home/<username>/bin/ppm     

This will allow you to call ActivePerl with a command like:
         perl -le "Hello World!;"
```

which is vague, and doesn't really tell me anything since i am not familiar with where these entries should be appended. all searches have left me at a dead end because lubuntu is different than any of the examples i find. so where do the files exist? what are their names? and how should i correctly append them so that activeperl shows up in the menu? i need it to work so i can download additional packages and get some programs that rely on perl working.

i OFTEN have this problem when installing programs that are not packages that complete everything for you, because the tutorials or instructions say "easy as 1,2,3!" but instead of  doing that, most of the time they skip from 1 all the way to 9 and leave details out. is this that common of an issue with linux instructions? well linux is not the only thing i find this in, i also find it in a lot of other places (python, github, and a lot of other things)

that to me is hugely frustrating, since i used to be an instructor and had to give detailed presentations regularly, and to me it is anathema to not have a proper outline of instructions, huge no-no in my book. so why are there no steps 1,2,3 and a,b,c?

---

### Post by DuckHook on 2016-04-29
Your frustration is understandable. Many aspects of Linux instruction are opaque to new users. I will say that the authors likely assumed that anyone working with Perl would be sufficiently Linux-savvy that they would understand the telegraphed notes. In that sense, they were never meant to be instructions (of the step-by-step nature you were expecting), but more like short-form reminders to the already knowledgeable.
[B][I]
Re: Modifying startup environment[/I][/B]

A simple, but incomplete description of paths is: this is the way that applications find their way to the location of their own executable code. Most installation packages add their executable code into directories that are already on predefined paths, but your app apparently creates its own directory (which, because of that, won't be on your path). I assume that you want this app accessible to all users. Therefore, open up a terminal and do:```
sudo nano /etc/profile.d/myvariables.sh
```This creates a new file for you in the /etc/profile.d directory called myvariables.sh. Copy and paste the following two lines into the new file:```
export PATH=$PATH:/home/stealth/ActivePerl-5.22/site/bin:/home/stealth/ActivePerl-5.22/bin
export MANPATH=$MANPATH:/home/stealth/ActivePerl-5.22/site/man:/home/stealth/ActivePerl-5.22/man
```Linux is case-sensitive and very exacting, so the entries must be *exactly* as above. It is best to use the mouse to copy and paste what I have written into the file. Then save <Ctrl>+<o> and exit <Ctrl>+<x>.

Next, *without sudo*:```
nano ~/.bash_profile
```...and add:```
PATH=$PATH:/home/<username>/bin
```...but replace <username> with your real username (in my case: DuckHook). Again, save and exit.
[B][I]
Re: Symbolic links[/I][/B]

A *symbolic link* is a way to set a "pointer" into a directory so that the link masquerades as the real app or file. It has many uses which we won't get into here. For your purposes, simply open a terminal again, then copy and paste the two commands in your original post into the terminal, one at a time (be sure to hit the <Enter> key after each line of code has been pasted). Replace the two instances of <username> on each line with your real username (in my case: DuckHook).

You should now be good to go.

---

### Post by xander2077 on 2016-04-30
well the first two things you told me to do worked as far as i can tell,  they at least wrote to the files using nano. however the last one,  trying to create the symbolic link left me with this error message:

```
ln: failed to create symbolic link ‘/home/stealth/bin/perl’: No such file or directory
```

---

### Post by jim_deadlock on 2016-04-30
Pardon me if I'm missing something here, but isn't ActivePerl designed for Windows? You are aware that Ubuntu comes with Perl pre-installed?

---

### Post by DuckHook on 2016-04-30
> **jim_deadlock said:**
> Pardon me if I'm missing something here, but isn't ActivePerl designed for Windows? You are aware that Ubuntu comes with Perl pre-installed?Thanks for raising this Jim. It did not even occur to me to ask xander2077 why he was installing. I just automatically fell into cruise mode translating the OP's instructions for him and assuming he knew what and why he was installing.

@xander2077

Tell us what your end goal is. jim_deadlock is correct. Perl is already part of Ubuntu. Moreover, there are huge philosophical differences between Windows and Linux, not the least of which is that we rarely need to go outside the repositories for software. If you need to learn more about this, read the link to: ***Linux is not Windows*** in my signature.

---

### Post by xander2077 on 2016-04-30
> **DuckHook said:**
> I was aware of this, yes. I am just translating the OP's instructions for him and assuming he knew what and why he was installing.

im installing it for a program called mdlops, which has a perl version, but requires activeperl and the interface it has in order to download some additional dependencies that the perl script relies on to run. just having native perl is not enough, it has to be activeperl with the additional libraries.

i was thinking about why the symbolic link failed, could it be that my directory structure will have to reflect the actual folder structure instead of the one suggested? so should i put the same commands in but only edit them so they look like this instead? or does the second line need to reflect the actual perl directory (not the activeperl one) instead of being redundant?

```
ln -s /home/<username>/ActivePerl-5.22/bin/perl /home/<username>/ActivePerl-5.22/bin/perl
```

im still kind of stumped.

as a side note, no lubuntu did not come prepackaged with the perl libraries when i installed the OS that i know of, but i had to download them from the synaptic package manager and install them, however i am not sure where the directory is for that, which is probably why this is erroring out when i try to make a symbolic link. it may have been somewhat perl ready, but im not sure to what extent since i had to install the basic package myself. and now that i mentioned that i think the best way to find out where the directory for perl is, is to look in synaptic to see where the thing is installed.

```
/.
/usr
/usr/bin
/usr/bin/a2p
/usr/bin/c2ph
/usr/bin/config_data
/usr/bin/corelist
/usr/bin/cpan
/usr/bin/enc2xs
/usr/bin/find2perl
/usr/bin/h2ph
/usr/bin/h2xs
/usr/bin/instmodsh
/usr/bin/json_pp
/usr/bin/libnetcfg
/usr/bin/perlbug
/usr/bin/perldoc
/usr/bin/perlivp
/usr/bin/perlthanks
/usr/bin/piconv
/usr/bin/pl2pm
/usr/bin/pod2html
/usr/bin/pod2man
/usr/bin/pod2text
/usr/bin/pod2usage
/usr/bin/podchecker
/usr/bin/podselect
/usr/bin/prename
/usr/bin/prove
/usr/bin/psed
/usr/bin/pstruct
/usr/bin/ptar
/usr/bin/ptardiff
/usr/bin/ptargrep
/usr/bin/s2p
/usr/bin/shasum
/usr/bin/splain
/usr/bin/xsubpp
/usr/bin/zipdetails
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/perl
/usr/lib/x86_64-linux-gnu/perl/5.20.2
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B/Concise.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B/Showlex.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B/Terse.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/B/Xref.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/EXTERN.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/INTERN.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/XSUB.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/av.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/bitcount.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/charclass_invlists.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/config.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/cop.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/cv.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/dosish.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/embed.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/embedvar.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/fakesdio.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/feature.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/form.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/git_version.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/gv.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/handy.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/hv.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/hv_func.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/inline.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/intrpvar.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/iperlsys.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/keywords.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/l1_char_class_tab.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/malloc_ctl.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/metaconfig.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/mg.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/mg_data.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/mg_raw.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/mg_vtable.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/mydtrace.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/nostdio.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/op.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/op_reg_common.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/opcode.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/opnames.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/overload.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/pad.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/parser.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/patchlevel-debian.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/patchlevel.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perl.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perlapi.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perlio.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perliol.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perlsdio.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perlvars.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/perly.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/pp.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/pp_proto.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/proto.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/reentr.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/regcharclass.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/regcomp.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/regexp.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/regnodes.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/scope.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/sv.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/thread.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/time64.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/time64_config.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/uconfig.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/unicode_constants.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/unixish.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/utf8.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/utfebcdic.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/util.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/uudmap.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/vutil.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/CORE/warnings.h
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Compress
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Compress/Raw
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Compress/Raw/Bzip2.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Compress/Raw/Zlib.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Config.pod
/usr/lib/x86_64-linux-gnu/perl/5.20.2/DB_File.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Data
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Data/Dumper.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Devel
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Devel/PPPort.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Devel/Peek.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Digest
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Digest/MD5.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Digest/SHA.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Alias.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Byte.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/CJKConstants.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/CN
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/CN.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/CN/HZ.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Config.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/EBCDIC.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Encoder.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Encoding.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/GSM0338.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Guess.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/JP
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/JP.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/JP/H2Z.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/JP/JIS7.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/KR
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/KR.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/KR/2022_KR.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/MIME
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/MIME/Header
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/MIME/Header.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/MIME/Header/ISO_2022_JP.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/MIME/Name.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Symbol.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/TW.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Unicode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Unicode.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Encode/Unicode/UTF7.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/DosGlob.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/Cygwin.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/Epoc.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/Functions.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/Mac.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/OS2.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/VMS.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/File/Spec/Win32.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Filter
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Filter/Util
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Filter/Util/Call.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/GDBM_File.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Hash
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Hash/Util
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Hash/Util/FieldHash.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/I18N
/usr/lib/x86_64-linux-gnu/perl/5.20.2/I18N/Langinfo.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IO
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IO/Dir.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IO/Poll.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IPC
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IPC/Msg.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IPC/Semaphore.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IPC/SharedMem.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/IPC/SysV.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/List
/usr/lib/x86_64-linux-gnu/perl/5.20.2/List/Util
/usr/lib/x86_64-linux-gnu/perl/5.20.2/List/Util/XS.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/MIME
/usr/lib/x86_64-linux-gnu/perl/5.20.2/MIME/Base64.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/MIME/QuotedPrint.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Math
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Math/BigInt
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Math/BigInt/FastCalc.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/NDBM_File.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/O.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/ODBM_File.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Opcode.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/POSIX.pod
/usr/lib/x86_64-linux-gnu/perl/5.20.2/PerlIO
/usr/lib/x86_64-linux-gnu/perl/5.20.2/PerlIO/encoding.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/PerlIO/mmap.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/PerlIO/scalar.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/PerlIO/via.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/SDBM_File.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Storable.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Sys
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Sys/Hostname.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Sys/Syslog.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Tie
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Tie/Hash
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Tie/Hash/NamedCapture.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Time
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Time/HiRes.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Time/Piece.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Time/Seconds.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Unicode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Unicode/Collate
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Unicode/Collate.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Unicode/Collate/Locale.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/Unicode/Normalize.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/_h2ph_pre.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/arybase.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/bitsperlong.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/ioctl.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/ioctls.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/posix_types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/socket.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/sockios.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/termbits.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm-generic/termios.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/bitsperlong.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/ioctl.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/ioctls.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/posix_types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/posix_types_32.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/posix_types_64.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/posix_types_x32.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/socket.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/sockios.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/termbits.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/termios.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/unistd.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/unistd_32.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/unistd_64.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/asm/unistd_x32.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/B
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/B/B.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress/Raw
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress/Raw/Bzip2
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress/Raw/Bzip2/Bzip2.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress/Raw/Zlib
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Compress/Raw/Zlib/Zlib.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/DB_File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/DB_File/DB_File.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Data
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Data/Dumper
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Data/Dumper/Dumper.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Devel
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Devel/PPPort
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Devel/PPPort/PPPort.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Devel/Peek
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Devel/Peek/Peek.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Digest
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Digest/MD5
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Digest/MD5/MD5.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Digest/SHA
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Digest/SHA/SHA.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Byte
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Byte/Byte.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/CN
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/CN/CN.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/EBCDIC
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/EBCDIC/EBCDIC.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Encode.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/JP
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/JP/JP.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/KR
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/KR/KR.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Symbol
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Symbol/Symbol.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/TW
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/TW/TW.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Unicode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Encode/Unicode/Unicode.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/File/DosGlob
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/File/DosGlob/DosGlob.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Filter
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Filter/Util
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Filter/Util/Call
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Filter/Util/Call/Call.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/GDBM_File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/GDBM_File/GDBM_File.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Hash
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Hash/Util
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Hash/Util/FieldHash
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Hash/Util/FieldHash/FieldHash.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/I18N
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/I18N/Langinfo
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/I18N/Langinfo/Langinfo.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/IPC
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/IPC/SysV
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/IPC/SysV/SysV.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/MIME
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/MIME/Base64
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/MIME/Base64/Base64.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Math
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Math/BigInt
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Math/BigInt/FastCalc
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Math/BigInt/FastCalc/FastCalc.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/NDBM_File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/NDBM_File/NDBM_File.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/ODBM_File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/ODBM_File/ODBM_File.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Opcode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Opcode/Opcode.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/encoding
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/encoding/encoding.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/mmap
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/mmap/mmap.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/scalar
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/scalar/scalar.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/via
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/PerlIO/via/via.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/SDBM_File
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/SDBM_File/SDBM_File.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Storable
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Storable/Storable.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Sys
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Sys/Hostname
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Sys/Hostname/Hostname.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Sys/Syslog
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Sys/Syslog/Syslog.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Tie
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Tie/Hash
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Tie/Hash/NamedCapture
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Tie/Hash/NamedCapture/NamedCapture.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Time
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Time/HiRes
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Time/HiRes/HiRes.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Time/Piece
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Time/Piece/Piece.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Unicode
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Unicode/Collate
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Unicode/Collate/Collate.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Unicode/Normalize
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/Unicode/Normalize/Normalize.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/arybase
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/arybase/arybase.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/mro
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/mro/mro.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/sdbm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/sdbm/extralibs.ld
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/threads
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/threads/shared
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/threads/shared/shared.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/auto/threads/threads.so
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/byteswap-16.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/byteswap.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/endian.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/ioctl-types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/ioctls.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/pthreadtypes.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/select.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/select2.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sigaction.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sigcontext.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/siginfo.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/signum.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sigset.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sigstack.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sigthread.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/sockaddr.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/socket.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/socket2.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/socket_type.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/syscall.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/syslog-ldbl.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/syslog-path.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/syslog.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/time.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/timex.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/typesizes.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/uio.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/waitflags.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/waitstatus.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/bits/wordsize.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/encoding.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/endian.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/errno.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/features.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/gnu
/usr/lib/x86_64-linux-gnu/perl/5.20.2/gnu/stubs-64.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/gnu/stubs.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/linux
/usr/lib/x86_64-linux-gnu/perl/5.20.2/linux/ioctl.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/linux/posix_types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/linux/stddef.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/mro.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/ops.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/signal.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/stdarg.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/stdc-predef.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/stddef.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/cdefs.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/ioctl.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/select.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/socket.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/syscall.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/syslog.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/sysmacros.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/time.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/ttydefaults.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/types.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/ucontext.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/uio.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sys/wait.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/syscall.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/sysexits.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/syslimits.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/syslog.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/threads
/usr/lib/x86_64-linux-gnu/perl/5.20.2/threads.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/threads/shared.pm
/usr/lib/x86_64-linux-gnu/perl/5.20.2/time.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/wait.ph
/usr/lib/x86_64-linux-gnu/perl/5.20.2/xlocale.ph
/usr/share
/usr/share/doc
/usr/share/doc/perl
/usr/share/doc/perl/Changes.gz
/usr/share/doc/perl/changelog.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/perl
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/a2p.1.gz
/usr/share/man/man1/c2ph.1.gz
/usr/share/man/man1/config_data.1.gz
/usr/share/man/man1/corelist.1.gz
/usr/share/man/man1/cpan.1.gz
/usr/share/man/man1/enc2xs.1.gz
/usr/share/man/man1/find2perl.1.gz
/usr/share/man/man1/h2ph.1.gz
/usr/share/man/man1/h2xs.1.gz
/usr/share/man/man1/instmodsh.1.gz
/usr/share/man/man1/json_pp.1.gz
/usr/share/man/man1/libnetcfg.1.gz
/usr/share/man/man1/perlbug.1.gz
/usr/share/man/man1/perlivp.1.gz
/usr/share/man/man1/perlthanks.1.gz
/usr/share/man/man1/piconv.1.gz
/usr/share/man/man1/pl2pm.1.gz
/usr/share/man/man1/pod2html.1.gz
/usr/share/man/man1/pod2man.1.gz
/usr/share/man/man1/pod2text.1.gz
/usr/share/man/man1/pod2usage.1.gz
/usr/share/man/man1/podchecker.1.gz
/usr/share/man/man1/podselect.1.gz
/usr/share/man/man1/prename.1.gz
/usr/share/man/man1/prove.1.gz
/usr/share/man/man1/psed.1.gz
/usr/share/man/man1/pstruct.1.gz
/usr/share/man/man1/ptar.1.gz
/usr/share/man/man1/ptardiff.1.gz
/usr/share/man/man1/ptargrep.1.gz
/usr/share/man/man1/s2p.1.gz
/usr/share/man/man1/shasum.1.gz
/usr/share/man/man1/splain.1.gz
/usr/share/man/man1/xsubpp.1.gz
/usr/share/man/man1/zipdetails.1.gz

```

and this is the output from that. so far the only directory i can tell that has perl in it (the one the program wants me to point to for the symbolic link) is in an additional subfolder.

so it may be one of these two it should point to instead?

```
/usr/lib/x86_64-linux-gnu/perl
/usr/lib/x86_64-linux-gnu/perl/5.20.2
```

edit: well no that didnt work either. it says "file exists" when i point it to the correct directory, but i need to have a new symlink for activeperl to work from the start menu. and i am still not sure the point of them asking me to do this other than having it in the menu, or where it should point to since my file structure is not the same. there is no folder "/home/<username>/bin/perl" in lubuntu, it may be that way in other verions of linux, but lubuntu is vastly different. and i am not sure why that is.

---

### Post by jim_deadlock on 2016-04-30
I still think you would do better with the standard Perl. When you say libraries/dependencies, do you mean Perl modules? If so, you can easily install any necessary modules like this for example:

```
sudo cpan LWP::AuthenAgent
```

(substitute whatever modules you need)

I suspect you're over-complicating the whole issue.

-------------------
EDIT:

I found your thread on deadlystream.com - you've spent a fair amount of time and effort on this haven't you? So, I've attempted to install that script myself (just for the hell of it) and the various modules it requires. One of these required modules is Win32::API which throws the error "OS Unsupported", so I suspect this is your brick wall.

I haven't gone as far as installing ActivePerl but it does the same job as normal Perl, it's just the Windows version - yes there is a Linux version, which causes confusion because Linux already has Perl built in, so ActivePerl for Linux is redundant really. Perl is Perl, whichever version you have.

 **In a nutshell, even if you do manage to install ActivePerl properly, the script will still fail anyway due to the required Perl module Win32::API which is incompatible with Linux.**

Just to be clear, Perl/Activeperl is the 'interpreter' (program) which runs the script, the script requires the modules. It doesn't matter which of Perl/Activeperl you use, they both do the same job of running the script. Your problem is the incompatible module, not the interpreter.

I can see you've also had problems running mdlops.exe in Wine so I think this may be an unresolvable problem. The author is clearly Windows-centric. I think he has created the Perl script as an alternative to the .exe but it is still for Windows, that's why he suggests ActivePerl to run it.

By the way, there is a clue in the script itself which suggests that nobody has ever used this script in Linux. There is this line:

```
use TK::Tree;
```

... which would cause the script to fail in Linux because the correct name is Tk::Tree - Windows is case insensitive, Linux isn't.

---

### Post by xander2077 on 2016-04-30
yes that is the issue, trying to make windows stuff work in linux. now i can get it working in wine, but i found out that mdlops was not really the issue i was having, it was kotor-tool, and blender both. ktool, which runs with dotnet 2.0 i believe, was working for a while (with errors) but now i think it is broken because of the recent ubuntu updates which make it incompatible with linux, even with wine. but what the issue really was had nothing to do with mdlops. it is a simple script it does what it is supposed to. the problem was the model format was correct, but the values inside it were different from the default ones mdlops expected (it was a player made model) so i had to use a very very old script to force the import of that model. mdlops wrote it correctly, just what it saw, but the blender script to import could not interpret the data in the newest version of blender, so i had to use an older version of blender and a very old script. it is not pretty as a work around, but at least it worked. and that is usually the case when i have either very complex models with skins or player made models with extra data that usually is not contained in the mdlops output.

ktool is totally different as an issue. it took a lot of crazy workarounds to get it working, and even then it was not perfect, but now i suspect i will have to wait for a wine update for it to work again. whenever they alter how wine/linux/and windows programs "talk" to each other, it may take months to finally get it all ironed out due to the paranoid security updates that have been distributed recently. and i get why they are paranoid, but it is a pain when i jst want something to work right for once. this has been going on for months. things work, and then they get broken due to security. which is why i really would like some tools that run natively.

now i could do some backward engineering or rename the files to the appropriate name so that it doesn't brick wall, but that cant be found out unless i do something like you did and find the case discrepancy. unfortunately i cant just look inside the exe like i used to in windows and find those entries. it is somewhat easier when you are talking about files in folders, so one of my workarounds for case sensitivity is to just rename all files lower case and unify them, that way both linux and windows can read them for programs that bridge both OS's. but that only works in certain instances.

i do have win32 api running in wine so that is why mdlops works in wine, but since my blender is native to linux, i wanted to eliminate any issues that mdlops may or may not have because it is using win32. and since i was told the perl script allows it to run natively, i assumed the replier knew what they were saying. but since it needs win32, that is a non starter for me. it would be basically the same thing i am already doing in wine, no better, just redundant. why reinvent the wheel?

i suppose i should just scrub the installation then and forget it. i was wondering because even the instructions in the zip file for linux installation refer to windows start menu, so they just copy pasted that to the linux version read me (kinda lazy)

actually i am not really making it complicated, im simply going off of what i am told in the readme's, and suggestions. the real complication comes with bad information, and incomplete instructions. then it turns into wasted hours trying to do things that wont work anyway. and i hate complicated, which is why i even posted this in the first place to get to the root of the issue.

a nice side note however, is that there is a group that is making open source tools for NWN and by default they will work with KOTOR, it is called xoreos open source NWN engine, and tools. the lead dev there told me he was definitely making it linux and mac native, completely cross platform, so once i have access to those i think my days of trying to make these tools work in linux will be over.

---

### Post by jim_deadlock on 2016-04-30
Just to put this to bed entirely, I've installed ActivePerl  (Linux version) just to make sure. The GUI package manager (PPM) that comes with it (which  you were originally aiming for) does not show any of the Win32 modules.  If you want to check it for yourself, do this:

```
export PATH=$PATH:/home/stealth/ActivePerl-5.22/site/bin:/home/stealth/ActivePerl-5.22/bin
export MANPATH=$MANPATH:/home/stealth/ActivePerl-5.22/site/man:/home/stealth/ActivePerl-5.22/man
~/ActivePerl-5.22/bin/ppm &
```

You'll get the windowed PPM app, enter Win32 in the filter field and everything will disappear. If you were running ActivePerl in Windows you would see all the Win32 modules listed.

Side Note: I simply changed TK::Tree to Tk::Tree in the script to continue with the installation. I just mentioned it to show that the script was written for Windows in the first place.

---

