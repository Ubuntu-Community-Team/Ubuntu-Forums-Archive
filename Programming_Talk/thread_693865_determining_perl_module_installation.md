---
title: "determining perl module installation"
date: 2008-02-11
forum: Programming Talk
---

### Post by DouglasAWh on 2008-02-11
Ok, I'm having a frustrating time with Perl in Windows.  Unfortunately, moving this to Linux is not really an option.  Anyway, I've seen [http://www.cpan.org/misc/cpan-faq.html#How_installed_modules](http://www.cpan.org/misc/cpan-faq.html#How_installed_modules), but I'm not exactly sure what I'm looking at in perllocal.pod.  Here's my file 

[php]
=head2 Thu Jan 10 11:34:59 2008: C<Module> L<ActiveState::Utils|ActiveState::Utils>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.04>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:06 2008: C<Module> L<HTML::Tagset|HTML::Tagset>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.10>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:20 2008: C<Module> L<Tcl|Tcl>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.89>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:38 2008: C<Module> L<URI|URI>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.35>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:59 2008: C<Module> L<HTML::Parser|HTML::Parser>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.56>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:37:53 2008: C<Module> L<DBI|DBI>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.601>

=item *

C<EXE_FILES: dbiproxy dbiprof dbilogstrip>

=back

=head2 Thu Jan 10 11:38:21 2008: C<Module> L<ActiveState::RelocateTree|ActiveState::RelocateTree>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: bin/reloc_perl>

=back

=head2 Thu Jan 10 11:38:45 2008: C<Module> L<ActivePerl::DocTools|ActivePerl::DocTools>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.02>

=item *

C<EXE_FILES: bin/ap-update-html bin/ap-user-guide>

=back

=head2 Thu Jan 10 11:39:11 2008: C<Module> L<XML::Parser|XML::Parser>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.36>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:18 2008: C<Module> L<Text::Reform|Text::Reform>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.11>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:29 2008: C<Module> L<Digest::SHA1|Digest::SHA1>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.11>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:56 2008: C<Module> L<Tkx|Tkx>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: tkx-ed tkx-prove>

=back

=head2 Thu Jan 10 11:40:06 2008: C<Module> L<Term::ReadKey|Term::ReadKey>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.30>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:40:59 2008: C<Module> L<LWP|LWP>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 5.808>

=item *

C<EXE_FILES: bin/lwp-request bin/lwp-mirror bin/lwp-rget bin/lwp-download>

=back

=head2 Thu Jan 10 11:41:41 2008: C<Module> L<DBD::SQLite|DBD::SQLite>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.13>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:42:08 2008: C<Module> L<Win32::AuthenticateUser|Win32::AuthenticateUser>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.02>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:45:57 2008: C<Module> L<libwin32|libwin32>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.26.0.2>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:06 2008: C<Module> L<XML::Simple|XML::Simple>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.18>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:17 2008: C<Module> L<Unicode::String|Unicode::String>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.09>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:24 2008: C<Module> L<Text::Autoformat|Text::Autoformat>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.13>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:31 2008: C<Module> L<Term::ReadLine::Perl|Term::ReadLine::Perl>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.0302>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:45 2008: C<Module> L<MIME-Base64-Scripts|MIME-Base64-Scripts>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.00>

=item *

C<EXE_FILES: encode-base64 decode-base64 encode-qp decode-qp>

=back

=head2 Thu Jan 10 11:47:52 2008: C<Module> L<MD5|MD5>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.03>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:59 2008: C<Module> L<IO::String|IO::String>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.08>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:12 2008: C<Module> L<HTML-Tree|HTML-Tree>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.23>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:19 2008: C<Module> L<Font::AFM|Font::AFM>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.19>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:47 2008: C<Module> L<File::CounterFile|File::CounterFile>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:58 2008: C<Module> L<Digest::MD4|Digest::MD4>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.5>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:07 2008: C<Module> L<Digest::MD2|Digest::MD2>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.03>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:15 2008: C<Module> L<Digest::HMAC|Digest::HMAC>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.01>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:23 2008: C<Module> L<Data::Dump|Data::Dump>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.08>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:44 2008: C<Module> L<Archive::Zip|Archive::Zip>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.20>

=item *

C<EXE_FILES: bin/crc32>

=back

=head2 Thu Jan 10 11:49:56 2008: C<Module> L<ActiveState::Scineplex|ActiveState::Scineplex>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.01>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:51:01 2008: C<Module> L<ActivePerl::PPM|ActivePerl::PPM>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 4.01>

=item *

C<EXE_FILES: bin/ppm bin/ppm-shell>

=back

=head2 Thu Jan 10 11:51:09 2008: C<Module> L<ActivePerl::Config|ActivePerl::Config>

=over 4

=item *

C<installed into: C:\TEMP\perl-----------------------------------------please-run-the-install-script----------------------------------------\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.02>

=item *

C<EXE_FILES: >

=back
[/php]

The main thing is, what exactly is the name of the module?  I'm trying to install [http://search.cpan.org/~rsavage/DBIx-MSSQLReporter-1.04/lib/DBIx/MSSQLReporter.pm](http://search.cpan.org/~rsavage/DBIx-MSSQLReporter-1.04/lib/DBIx/MSSQLReporter.pm) , but I'm not sure how that would show up in the .pod file.  Would it just show up as DBIx::MSSQLReporter?

Thanks!

---

### Post by DouglasAWh on 2008-02-11
I managed to get pmtools ([http://use.perl.org/articles/06/01/13/1950245.shtml](http://use.perl.org/articles/06/01/13/1950245.shtml)) installed on my ubuntu box, now I need to figure out how to use it...and install it on the the Windows box, it would seem.

EDIT: Ok, I figured out that you just type the pm command in the terminal, but is the below all the commands?

> 
    * pmpath - show the module's full path
    * pmvers - get a module version number
    * pmdesc - get a module description
    * pmall - get all installed modules pmdesc descriptions
    * pmdirs - print the perl module path, newline separated
    * plxload - show what files a given program loads at compile time
    * pmload - show what files a given module loads at compile time
    * pmexp - show a module's exports
    * pminst - find what's installed
    * pmeth - list a class's methods, recursively
    * pmls - long list the module path
    * pmcat - cat the module source through your pager
    * pman - show the module's pod docs
    * pmfunc - show a function source code from a module
    * podgrep - grep in pods of a file
    * pfcat - show pods from perlfunc
    * podtoc - list table of contents of a podpage
    * podpath - show full path of pod file
    * pods - list all standard pods and module pods
    * sitepods - list only pods in site_perl directories
    * basepods - list only normal "man-page" style pods
    * faqpods - list only faq pods
    * modpods - all module pods, including site_perl ones
    * stdpods - list standard pods, not site_perl ones 


---

### Post by ghostdog74 on 2008-02-11
I used ActiveState Perl on windows. the PPM manager makes it easy to install packages. you might want to try that in future.

---

### Post by DouglasAWh on 2008-02-13
how do I use PPM?  I've got ActiveState installed.

---

### Post by DouglasAWh on 2008-02-13
ok, at the end of the day, I think I still need to install a module.  I'm looking at [http://perlhelp.web.cern.ch/PerlHelp/faq/ActivePerl-faq2.html](http://perlhelp.web.cern.ch/PerlHelp/faq/ActivePerl-faq2.html), but if I type in PPM (in Windows) I just get 

```

C:\Documents and Settings\commtesa>ppm
No Perl script found in input

C:\Documents and Settings\commtesa>search *
search.bat internal error: Quantifier follows nothing in regex; marked by <-- HE
RE in m/* <-- HERE / at (eval 3) line 238.


C:\Documents and Settings\commtesa> ppm search *
No Perl script found in input

```

The "How do I use PPM?" section of the FAQ seems to think that the command line should just take PPM commands once PPM is typed, but this does not appear to be the case in Windows.

---

### Post by ghostdog74 on 2008-02-13
> **DouglasAWh said:**
> ok, at the end of the day, I think I still need to install a module.  I'm looking at [http://perlhelp.web.cern.ch/PerlHelp/faq/ActivePerl-faq2.html](http://perlhelp.web.cern.ch/PerlHelp/faq/ActivePerl-faq2.html), but if I type in PPM (in Windows) I just get 

```

C:\Documents and Settings\commtesa>ppm
No Perl script found in input

C:\Documents and Settings\commtesa>search *
search.bat internal error: Quantifier follows nothing in regex; marked by <-- HE
RE in m/* <-- HERE / at (eval 3) line 238.


C:\Documents and Settings\commtesa> ppm search *
No Perl script found in input

```

The "How do I use PPM?" section of the FAQ seems to think that the command line should just take PPM commands once PPM is typed, but this does not appear to be the case in Windows.

when you install activestate Perl on windows, it should have included the ppm path for you. If not, you can include the path in your PATH system variable on windows. I will leave you to that. After you download the PPM from the [PPM zip archives]("http://www.activestate.com/PPMPackages/zips/6xx-builds-only/"), unzip the module to a directory and from the DOS prompt, change to the directory where you unzipped the module, type
```

c:\>ppm install <module.ppd>

```
that's basically it.

---

### Post by DouglasAWh on 2008-02-18
for the record, this is what my new perllocal.pod looks like

```

=head2 Thu Jan 10 11:34:59 2008: C<Module> L<ActiveState::Utils|ActiveState::Utils>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.04>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:06 2008: C<Module> L<HTML::Tagset|HTML::Tagset>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.10>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:20 2008: C<Module> L<Tcl|Tcl>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.89>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:38 2008: C<Module> L<URI|URI>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.35>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:35:59 2008: C<Module> L<HTML::Parser|HTML::Parser>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.56>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:37:53 2008: C<Module> L<DBI|DBI>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.601>

=item *

C<EXE_FILES: dbiproxy dbiprof dbilogstrip>

=back

=head2 Thu Jan 10 11:38:21 2008: C<Module> L<ActiveState::RelocateTree|ActiveState::RelocateTree>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: bin/reloc_perl>

=back

=head2 Thu Jan 10 11:38:45 2008: C<Module> L<ActivePerl::DocTools|ActivePerl::DocTools>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.02>

=item *

C<EXE_FILES: bin/ap-update-html bin/ap-user-guide>

=back

=head2 Thu Jan 10 11:39:11 2008: C<Module> L<XML::Parser|XML::Parser>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.36>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:18 2008: C<Module> L<Text::Reform|Text::Reform>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.11>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:29 2008: C<Module> L<Digest::SHA1|Digest::SHA1>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.11>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:39:56 2008: C<Module> L<Tkx|Tkx>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: tkx-ed tkx-prove>

=back

=head2 Thu Jan 10 11:40:06 2008: C<Module> L<Term::ReadKey|Term::ReadKey>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.30>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:40:59 2008: C<Module> L<LWP|LWP>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 5.808>

=item *

C<EXE_FILES: bin/lwp-request bin/lwp-mirror bin/lwp-rget bin/lwp-download>

=back

=head2 Thu Jan 10 11:41:41 2008: C<Module> L<DBD::SQLite|DBD::SQLite>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.13>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:42:08 2008: C<Module> L<Win32::AuthenticateUser|Win32::AuthenticateUser>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.02>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:45:57 2008: C<Module> L<libwin32|libwin32>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 0.26.0.2>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:06 2008: C<Module> L<XML::Simple|XML::Simple>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.18>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:17 2008: C<Module> L<Unicode::String|Unicode::String>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.09>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:24 2008: C<Module> L<Text::Autoformat|Text::Autoformat>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.13>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:31 2008: C<Module> L<Term::ReadLine::Perl|Term::ReadLine::Perl>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.0302>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:45 2008: C<Module> L<MIME-Base64-Scripts|MIME-Base64-Scripts>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.00>

=item *

C<EXE_FILES: encode-base64 decode-base64 encode-qp decode-qp>

=back

=head2 Thu Jan 10 11:47:52 2008: C<Module> L<MD5|MD5>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.03>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:47:59 2008: C<Module> L<IO::String|IO::String>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.08>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:12 2008: C<Module> L<HTML-Tree|HTML-Tree>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 3.23>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:19 2008: C<Module> L<Font::AFM|Font::AFM>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.19>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:47 2008: C<Module> L<File::CounterFile|File::CounterFile>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.04>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:48:58 2008: C<Module> L<Digest::MD4|Digest::MD4>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.5>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:07 2008: C<Module> L<Digest::MD2|Digest::MD2>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 2.03>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:15 2008: C<Module> L<Digest::HMAC|Digest::HMAC>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.01>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:23 2008: C<Module> L<Data::Dump|Data::Dump>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.08>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:49:44 2008: C<Module> L<Archive::Zip|Archive::Zip>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.20>

=item *

C<EXE_FILES: bin/crc32>

=back

=head2 Thu Jan 10 11:49:56 2008: C<Module> L<ActiveState::Scineplex|ActiveState::Scineplex>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.01>

=item *

C<EXE_FILES: >

=back

=head2 Thu Jan 10 11:51:01 2008: C<Module> L<ActivePerl::PPM|ActivePerl::PPM>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 4.01>

=item *

C<EXE_FILES: bin/ppm bin/ppm-shell>

=back

=head2 Thu Jan 10 11:51:09 2008: C<Module> L<ActivePerl::Config|ActivePerl::Config>

=over 4

=item *

C<installed into: C:\Perl\lib>

=item *

C<LINKTYPE: dynamic>

=item *

C<VERSION: 1.02>

=item *

C<EXE_FILES: >

=back



```

---

### Post by DouglasAWh on 2008-02-18
> **ghostdog74 said:**
> 
```

c:\>ppm install <module.ppd>

```
that's basically it.

Ok, I unzipped the module, but I don't see a ppd file anywhere.

> 
 Directory of C:\Documents and Settings\commtesa\Desktop\DBIx-MSSQLReporter-1.04
\DBIx-MSSQLReporter-1.04\DBIx-MSSQLReporter-1.04

02/18/2008  12:36 PM    <DIR>          .
02/18/2008  12:36 PM    <DIR>          ..
10/27/2005  02:34 PM               360 Build.PL
10/28/2005  03:36 AM             1,469 Changes.txt
02/18/2008  12:36 PM    <DIR>          examples
02/18/2008  12:36 PM    <DIR>          lib
10/27/2005  02:34 PM               709 Makefile.PL
10/28/2005  03:47 AM               221 MANIFEST
10/27/2005  02:34 PM                33 MANIFEST.SKIP
10/28/2005  03:47 AM               457 META.yml
10/27/2005  02:34 PM             1,752 README
02/18/2008  12:36 PM    <DIR>          t
               7 File(s)          5,001 bytes
               5 Dir(s)  16,595,918,848 bytes free



the 't' dir has to *.t files, examples has three *.pl files and lib has a *.pm file.  I'm thinking the *.pm file is the way to go, but not sure.

EDIT: Went ahead and tried to install the .pm file, but this is what I got:

> 
C:\Documents and Settings\commtesa\Desktop\DBIx-MSSQLReporter-1.04\DBIx-MSSQLRep
orter-1.04\DBIx-MSSQLReporter-1.04\lib\DBIx>ppm install MSSQLReporter.pm
Downloading ActiveState Package Repository packlist...done
Updating ActiveState Package Repository database...done
Syncing site PPM database with .packlists...done
ppm install failed: Can't find any package that provides MSSQLReporter.pm


This is what the .pm file looks like

[php]
package DBIx::MSSQLReporter;

# Name:
#	DBIx::MSSQLReporter.
#
# Documentation:
#	POD-style documentation is at the end. Extract it with pod2html.*.
#
# Tabs:
#	4 spaces || die.
#
# Author:
#	Ron Savage <ron@savage.net.au>
#	Home page: http://savage.net.au/index.html
#
# Licence:
#	Australian copyright (c) 1999-2002 Ron Savage.
#
#	All Programs of mine are 'OSI Certified Open Source Software';
#	you can redistribute them and/or modify them under the terms of
#	The Artistic License, a copy of which is available at:
#	http://www.opensource.org/licenses/index.html

use strict;
use vars qw($AUTOLOAD $VERSION @ISA @EXPORT @EXPORT_OK);

use Carp;
use DBI qw(:sql_types);

require Exporter;

@ISA = qw(Exporter);
# Items to export into callers namespace by default. Note: do not export
# names by default without a very good reason. Use EXPORT_OK instead.
# Do not simply export all your public functions/methods/constants.

@EXPORT		= qw();

$VERSION	= '1.04';

# -----------------------------------------------------------------

# Preloaded methods go here.

# -----------------------------------------------------------------

# Encapsulated class data.
# This is a list of attributes the user
# can use when calling DBIx::MSSQLReporter -> new().
# I call these standard attributes, as opposed
# to non-standard attributes which the user
# should not refer to in the call to new().
#
# Reference:
#	Object Oriented Perl
#	Damian Conway
#	Manning
#	1-88477-779-1
#	Chapter 3
{
	my(%_attribute) =
	(	# Name		=> default
		_connexion	=> '',
	);

	# Return the default for any attribute.
	sub _default_for
	{
		my($self, $attribute) = @_;

		$_attribute{$attribute};

	}	# End of _default_for.

	# Return the standard attributes.
	sub _standard_keys
	{
		keys(%_attribute);

	}	# End of _standard_keys.

	# Tested, to some extent, with SQL Server and Postgres.
	# Authors:
	#	Dominique Cretel <dominique.cretel@sema.be>
	#	Ron Savage <ron@savage.net.au>
	my(%_field_type) =
	(
		'-1'	=> 'Text',
		'1'		=> 'Char',
		'2'		=> '2 - unknown',
		'3'		=> 'Decimal',
		'4'		=> 'Integer',
		'5'		=> 'Smallint',
		'6'		=> '6 - unknown',
		'7'		=> 'Double precision',
		'8'		=> 'Double precision',
		'9'		=> 'Date',
		'10'	=> 'Time',
		'11'	=> 'Datetime/Timestamp',
		'12'	=> 'Varchar',
		'13'	=> '13 - unknown',
		'14'	=> '14 - unknown',
		'15'	=> '15 - unknown',
		'16'	=> '16 - unknown',
		'17'	=> '17 - unknown',
		'18'	=> '18 - unknown',
		'19'	=> '19 - unknown',
		'20'	=> '20 - unknown',
	);

	# Return readable type for numeric type.
	sub _field_type
	{
		my($self, $field) = @_;

		$_field_type{$field};
	}

}	# End of encapsulated class data.

# ------------------------------------------------------------------------
# Execute any SQL command.

sub do
{
	my($self, $sql)	= @_;
	my($dbh)		= $self -> {'_dbh'};
	my($sth)		= $dbh -> prepare($sql) or croak $DBI::errstr;

	$sth -> execute() or croak $DBI::errstr;

	$sth;

}	# End of do.

# ------------------------------------------------------------------------
# Drop a database.

sub dropDB
{
	my($self, $dbName) = @_;

	my($dbh)	= $self -> {'_dbh'};
	my($result)	= $dbh -> do("drop database $dbName");

	croak $DBI::errstr if (! $result);

}	# End of dropDB.

# ------------------------------------------------------------------------
# Drop a table.

sub dropTable
{
	my($self, $tableName) = @_;

	my($dbh)	= $self -> {'_dbh'};
	my($result)	= $dbh -> do("if exists (select * from sysobjects where id = object_id(N'[dbo].[$tableName]') and OBJECTPROPERTY(id, N'IsUserTable') = 1) drop table [dbo].[$tableName]");

	croak $DBI::errstr if (! $result);

}	# End of dropTable.

# -----------------------------------------------------------------
# Get the names of all user databases.
# $sysDbCount is the number of system database names to ignore, 4 by default.

sub get_dbNames
{
	my($self, $sysDbCount)	= @_;
	$sysDbCount				= 4 if (! $sysDbCount);
	my($dbh)				= $self -> {'_dbh'};

	# See MS SQL Server 7.0/Books On Line/(Search) sysdatabases/(Result) sysdatabases (T-SQL).
	# dbId	Name
	#	1	master
	#	2	tempDb
	#	3	model
	#	4	msDb
	#	?	msSqlWeb
	my($araRef)	= $dbh -> selectcol_arrayref("select * from master.dbo.sysdatabases where dbid > $sysDbCount") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_dbNames.

# -----------------------------------------------------------------
# Get the names of all fields in the given table.

sub get_fieldNames
{
	my($self, $tableName)	= @_;
	my($dbh)				= $self -> {'_dbh'};
	my($sth)				= $self -> do("select * from $tableName where 1 = 0");
	my($name)				= $sth -> {NAME};
	my(@type)				= map{$self -> _field_type($_)} @{$sth -> {TYPE} };
	my($precision)			= $sth -> {PRECISION};

	($name, \@type, $precision);

}	# End of get_fieldNames.

# -----------------------------------------------------------------
# Get the names of all user tables in the current database.

sub get_tableNames
{
	my($self)	= @_;
	my($dbh)	= $self -> {'_dbh'};
	my($araRef) = $dbh -> selectcol_arrayref("select name from sysobjects where OBJECTPROPERTY(id, N'IsUserTable') = 1") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_tableNames.

# -----------------------------------------------------------------
# Get the names of all user views in the current database.

sub get_viewNames
{
	my($self)	= @_;
	my($dbh)	= $self -> {'_dbh'};
	my($araRef) = $dbh -> selectcol_arrayref("select name from sysobjects where OBJECTPROPERTY(id, N'IsView') = 1 and objectProperty(id, N'IsMSShipped') = 0") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_viewNames.

# -----------------------------------------------------------------
# Get the names of all system databases.
# $sysDbCount is the number of system database names to recognize, 4 by default.

sub get_sysDbNames
{
	my($self, $sysDbCount)	= @_;
	$sysDbCount				= 4 if (! $sysDbCount);
	my($dbh)				= $self -> {'_dbh'};

	# See MS SQL Server 7.0/Books On Line/(Search) sysdatabases/(Result) sysdatabases (T-SQL).
	# dbId	Name
	#	1	master
	#	2	tempDb
	#	3	model
	#	4	msDb
	#	?	msSqlWeb
	my($araRef)	= $dbh -> selectcol_arrayref("select * from master.dbo.sysdatabases where dbid <= $sysDbCount") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_sysDbNames.

# -----------------------------------------------------------------
# Get the names of all system tables in the current database.

sub get_sysTableNames
{
	my($self)	= @_;
	my($dbh)	= $self -> {'_dbh'};
	my($araRef) = $dbh -> selectcol_arrayref("select name from sysobjects where OBJECTPROPERTY(id, N'IsSystemTable') = 1") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_sysTableNames.

# -----------------------------------------------------------------
# Get the names of all system views in the current database.

sub get_sysViewNames
{
	my($self)	= @_;
	my($dbh)	= $self -> {'_dbh'};
	my($araRef) = $dbh -> selectcol_arrayref("select name from sysobjects where OBJECTPROPERTY(id, N'IsView') = 1 and objectProperty(id, N'IsMSShipped') = 1") or croak $dbh -> errstr;
	@$araRef	= map{lc} sort @$araRef;

	$araRef;

}	# End of get_sysViewNames.

# ------------------------------------------------------------
# Convert a hash reference into an HTML table.
# $sep separates the values of different rows in each column.
# It defaults to $;.

sub hash2Table
{
	my($self, $hashRef, $sep, $keyRef)	= @_;
	$sep								= $; if (! $sep);

	# By default, the columns are displayed in the order
	# specified by $keyRef, where $keyRef is a reference
	# to a hash, and in that hash the keys are the column
	# names and the sort order is given by the 'order' subkey.
	# Eg:
	#	my(%key) =
	#	(
	#		hostName	=>
	#			{
	#				data	=> '',
	#				order	=> 1,
	#			},
	#		userName	=>
	#			{
	#				data	=> '',
	#				order	=> 2,
	#			},
	#		dbName		=>
	#			{
	#				data	=> '',
	#				order	=> 3,
	#			},
	#	);

	# If the 2nd parameter is not a hash,
	# fabricate a hash to sort on.
	my(@key) = sort(keys(%$hashRef) );

	if (ref($keyRef) ne 'HASH')
	{
		$keyRef = {};

		my($order) = 0;
		my($key);

		for $key (@key)
		{
			$order++;
			$$keyRef{$key}	= {};
			$$keyRef{$key}{'order'}	= $order;
		}
	}

	# Determine the column order.
	@key = sort {$$keyRef{$a}{'order'} cmp $$keyRef{$b}{'order'} } @key;

	# The keys will be the column headings.
	my($html) = "\n<table border=1>\n\t<tr>\n";
	my($key);

	for $key (@key)
	{
		$html .= "\t\t<th>$key</th>\n";
	}

	$html .= "\t</tr>\n";

	# Get the # of rows of data.
	my(@row)	= keys(%$hashRef);
	@row		= split(/$sep/, $$hashRef{$row[0]});
	my($row);

	# Display each row.
	for $row (0 .. $#row)
	{
		$html .= "\t<tr>\n";

		# Display the row in sorted order.
		for $key (@key)
		{
			my(@field) = split(/$sep/, $$hashRef{$key});
			$html .= "\t\t<td>" . $field[$row] . "</td>\n";
		}

		$html .= "\t</tr>\n";
	}

	# The '\n's just make the output easy to debug.
	$html .= "</table>\nRow count: " . ($#row + 1) . "\n";

	# Return the HTML.
	$html;

}	# End of hash2Table.

# -----------------------------------------------------------------

sub new
{
	my($class, %arg)	= @_;
	my($self)			= bless({}, $class);

	for my $attr_name ($self -> _standard_keys() )
	{
		my($arg_name) = $attr_name =~ /^_(.*)/;

		if (exists($arg{$arg_name}) )
		{
			$$self{$attr_name} = $arg{$arg_name};
		}
		else
		{
			$$self{$attr_name} = $self -> _default_for($attr_name);
		}
	}

	$self -> {'_sql'} = '';
	$self -> {'_dbh'} = DBI->connect($self -> {'_connexion'},
										{
											PrintError	=> 0,
											RaiseError	=> 0,
										}) || croak "Can't connect: $DBI::errstr\n";
	$self -> {'_dbh'} -> {LongReadLen} = 65534;

	return $self;

}	# End of new.

# ------------------------------------------------------------------------
# Execute a select command.
# Return the hash ref of the data.
# This can be passed straight to hash2Table.
# $sep separates the values of different rows in each column.
# It defaults to $;.

sub select
{
	my($self, $sql, $sep)	= @_;
	$sep					= $; if (! $sep);
	$self -> {'_select'}	= {};
	my($sth)				= $self -> do($sql);

	my($rowRef, $key);

	# Build a hash, $self -> {'_select'}, where the keys are the column headings,
	# ie the field names, and the values are the column data, separated by $sep.
	while ( ($rowRef = $sth -> fetchrow_hashref() ) )
	{
		for $key (keys(%$rowRef) )
		{
			$$rowRef{$key}				= 'NULL'				if (! defined($$rowRef{$key}) );
			$self -> {'_select'}{$key}	.= "$sep$$rowRef{$key}"	if (defined($self -> {'_select'}{$key}) );
			$self -> {'_select'}{$key}	= $$rowRef{$key}		if (! defined($self -> {'_select'}{$key}) );
		}
	}

	$sth -> finish();

	$self -> {'_select'};

}	# End of select.

# -----------------------------------------------------------------

sub DESTROY
{
	my($self) = @_;

	$self -> {'_dbh'} -> disconnect();

}	# End of DESTROY.

# -----------------------------------------------------------------
# Fabricate accessors and mutators on-the-fly.

sub AUTOLOAD
{
	no strict 'refs';

	my($self, $newval) = @_;

	# Was it a get... method?
	if ($AUTOLOAD =~ /.*::get(_\w+)/)
	{
		my($attributeName)	= $1;
		*{$AUTOLOAD}		= sub { return $_[0] -> {$attributeName}; };
		return $self -> {$attributeName};
	}

	# Was it a set... method?
	if ($AUTOLOAD =~ /.*::set(_\w+)/)
	{
		my($attributeName)	= $1;
		*{$AUTOLOAD}		= sub { $_[0] -> {$attributeName} = $_[1]; return; };
		$self -> {$1}		= $newval;
		return;
	}

	# Must have been a mistake then...
	croak "No such method: $AUTOLOAD";

}	# End of AUTOLOAD.

# -----------------------------------------------------------------

# Autoload methods go after =cut, and are processed by the autosplit program.

1;

__END__

=head1 NAME

DBIx::MSSQLReporter - An module to connect Perl to MS SQL Server and MS Data Engine

=head1 SYNOPSIS

See the programs in the examples/ directory. They have been updated to run against MS SQL Server V 8.

Warning: I could not get any of the MSDE examples to work with MS SQL Server V 8.

Note: sql8-Demo-3.pl is a CGI script.

=head1 DESCRIPTION

C<DBIx::MSSQLReporter> encapsulates the connection between Perl and MS SQL Server.

C<DBIx::MSSQLReporter> was written so that I could teach myself about MS SQL Server and
MSDE, and as part of my Perl tutorial series.

It should be clear from the name that this module is database-engine-specific. If you
plan on writing code which is independent of any particular database, look elsewhere.

See the URI, below, for my demos sql7Demo[23].pl, which both use this module.

sql7Demo2.pl is a command-line program. sql7Demo3.pl is a CGI script.

Lastly, note that this module has a chequered future: I may well re-write it to fit
under the umbrella of DBIx::Easy, or someone else working independently may have
already released such a module.

=head1 INSTALLATION

You install C<DBIx::MSSQLReporter>, as you would install any perl module,
by running these commands:

	perl Makefile.PL
	make
	make test
	make install

=head1 CONSTRUCTOR new

The constructor takes 1 parameter and 1 value for that parameter.

It croaks if it can't connect. Otherwise it returns an object you can use thus:

	my($reporter) = DBIx::MSSQLReporter -> new(connexion => $connect);
	print join("\n", @{$reporter -> get_viewNames()}), "\n\n";

=head1 METHOD do($sql)

It croaks if it can't prepare() and execute() the given SQL.

It returns a statment handle, which you need for things like:

	my($sth) = $reporter -> do($sql);
	$sth -> dump_results();
	$sth -> finish();

dump_results() is built-in to DBI.

=head1 METHOD dropDB($dbName)

It croaks if it can't drop the given database.

	$reporter -> dropDB($dbName);

=head1 METHOD dropTable($tableName)

It croaks if it can't drop the given table.

	$reporter -> dropTable($tableName);

=head1 METHOD get_dbNames($sysDbCount)

It returns a sorted list of user database names, all in lower case.

$sysDbCount is optional. It defaults to 4, which means this method ignores the 4
system tables. See get_sysDbNames(), below.

	my($dbName) = $reporter -> get_dbNames();
	print "User databases: \n";
	print join("\n", @$dbName), "\n\n";

=head1 METHOD get_fieldNames($tableName)

It returns a list of references to the names, types, and precisions, of the fields
in the given table.

	my($fieldName, $fieldType, $fieldPrecision) = $reporter -> get_fieldNames($tableName);
	print join("\n", map{"Field: $$fieldName[$_]. Type: $$fieldType[$_]. Precision: $$fieldPrecision[$_]"} 0 .. $#{$fieldName}), "\n\n";

=head1 METHOD get_tableNames()

It returns a sorted list of user table names, all in lower case. Recall, the DSN
specified the database.

	my($tableName) = $reporter -> get_tableNames();
	print "User tables: \n";
	print join("\n", @$tableName), "\n\n";

=head1 METHOD get_viewNames()

It returns a sorted list of user view names, all in lower case. Recall, the DSN
specified the database.

	my($viewName) = $reporter -> get_viewNames();
	print "User views: \n";
	print join("\n", @$viewName), "\n\n";

=head1 METHOD get_sysDbNames($sysDbCount)

It returns a sorted list of system database names, all in lower case. On my system,
I get master, model, msDb and tempDb.

$sysDbCount is optional. It defaults to 4, which means this method returns the 4
system tables. See get_dbNames(), above.

	my($sysDbName) = $reporter -> get_sysDbNames();
	print "System databases: \n";
	print join("\n", @$sysDbName), "\n\n";

=head1 METHOD get_sysTableNames()

It returns a sorted list of system table names, all in lower case. Recall, the DSN specified
the database.

	my($sysTableName) = $reporter -> get_sysTableNames();
	print "System tables: \n";
	print join("\n", @$sysTableName), "\n\n";

=head1 METHOD get_sysViewNames()

It returns a sorted list of system view names, all in lower case. Recall, the DSN
specified the database.

	my($sysViewName) = $reporter -> get_sysViewNames();
	print "System views: \n";
	print join("\n", @$sysViewName), "\n\n";

=head1 METHOD hash2Table($select, $sep, $keyRef)

Convert a hash reference, as returned by $reporter -> select($sql), into an HTML
table. See select(), below, for details.

	my($html) = $reporter -> hash2Table($select);

$sep is optional. It separates the values of different rows in each column. It
defaults to $;.

$keyRef is optional. It is a hash reference used to specify the order of columns.
It defaults to sorting the keys of %$select.

If you wish to use $keyRef, prepare it thus:

	my(%key) =
	(
		hostName	=>
			{
				someData	=> '',
				order		=> 2,
			},
		userName	=>
			{
				someData	=> '',
				order		=> 1,
			},
	);

	my($html) = $reporter -> hash2Table($select, $;, \%key);

	The key 'order' is used to order the keys 'hostName' and 'userName', which are
	presumed to appear as keys in %$select.

	The key 'someData' is ignored.

=head1 METHOD select($sql, $sep)

It croaks if it can't prepare() and execute() the given SQL.

$sep is optional. It defaults to $;.

It returns a reference to a hash, which hold the results of the select.

The keys of the hash are the names of the fields, which can be used for column
headings.

The values of the hash are the values of the fields, which can be used for the
column data. The values in each column are, by default, separated by Perl's $;
variable.

	my($select) = $reporter -> select($sql);

Warning: select() selects the whole table. Ideally we'd use DBIx::Recordset to page
thru the table, but I had too many problems with various versions of DBIx::Recordset.

If you have binary data containing $;, you I<E<lt>mustE<gt>> set $sep to something
else. Of course, with binary data, there may be no 'safe' character (string) which
does not appear in your data.

Alternately, store your binary data in files, and put the file name or URI in the
database.

The hash reference can be passed straight to hash2Table for conveting into an HTML
table. Eg:

	my($html) = $reporter -> hash2Table($select);
	print $html;

=head1 AUTHOR

C<DBIx::MSSQLReporter> was written by Ron Savage I<E<lt>ron@savage.net.auE<gt>> in 2000.

Source available from http://savage.net.au/Perl.html.

=head1 LICENCE

Australian copyright (c) 1999-2002 Ron Savage.

	All Programs of mine are 'OSI Certified Open Source Software';
	you can redistribute them and/or modify them under the terms of
	The Artistic License, a copy of which is available at:
	http://www.opensource.org/licenses/index.html

=cut

[/php]


Ok, it looks like I dd the install, but I still can't find a log file.  I'd like to have confirmation that it installed correctly before proceeding.  Thank you!

```

C:\Documents and Settings\commtesa\Desktop\DBIx-MSSQLReporter-1.04\DBIx-MSSQLRep
orter-1.04\DBIx-MSSQLReporter-1.04\lib\DBIx>perl -MCPAN -e shell

cpan shell -- CPAN exploration and modules installation (v1.9205)
ReadLine support enabled


cpan> install DBIx::MSSQLReporter
CPAN: Storable loaded ok (v2.18)
Going to read C:\Perl\cpan\Metadata
  Database was generated on Wed, 13 Feb 2008 11:30:50 GMT
Use of uninitialized value $_ in transliteration (tr///) at C:/Perl/lib/File/Spe
c/Win32.pm line 141.
Use of uninitialized value $_ in pattern match (m//) at C:/Perl/lib/File/Spec/Wi
n32.pm line 143.
CPAN: LWP::UserAgent loaded ok (v2.036)
CPAN: Time::HiRes loaded ok (v1.9711)
Fetching with LWP:
  http://ppm.activestate.com/CPAN/authors/01mailrc.txt.gz
Going to read C:\Perl\cpan\sources\authors\01mailrc.txt.gz
............................................................................DONE

Use of uninitialized value $_ in transliteration (tr///) at C:/Perl/lib/File/Spe
c/Win32.pm line 141.
Use of uninitialized value $_ in pattern match (m//) at C:/Perl/lib/File/Spec/Wi
n32.pm line 143.
Fetching with LWP:
  http://ppm.activestate.com/CPAN/modules/02packages.details.txt.gz
Going to read C:\Perl\cpan\sources\modules\02packages.details.txt.gz
  Database was generated on Mon, 18 Feb 2008 11:30:54 GMT
............................................................................DONE

Use of uninitialized value $_ in transliteration (tr///) at C:/Perl/lib/File/Spe
c/Win32.pm line 141.
Use of uninitialized value $_ in pattern match (m//) at C:/Perl/lib/File/Spec/Wi
n32.pm line 143.
Fetching with LWP:
  http://ppm.activestate.com/CPAN/modules/03modlist.data.gz
Going to read C:\Perl\cpan\sources\modules\03modlist.data.gz
............................................................................DONE

Going to write C:\Perl\cpan\Metadata
Running install for module 'DBIx::MSSQLReporter'
Running make for R/RS/RSAVAGE/DBIx-MSSQLReporter-1.04.tgz
CPAN: Digest::SHA loaded ok (v5.45)
Checksum for C:\Perl\cpan\sources\authors\id\R\RS\RSAVAGE\DBIx-MSSQLReporter-1.0
4.tgz ok
Scanning cache C:\Perl/cpan/build for sizes
............................................................................DONE

CPAN: Archive::Tar loaded ok (v1.38_01)
DBIx-MSSQLReporter-1.04
DBIx-MSSQLReporter-1.04/META.yml
DBIx-MSSQLReporter-1.04/Changes.txt
DBIx-MSSQLReporter-1.04/MANIFEST
DBIx-MSSQLReporter-1.04/MANIFEST.SKIP
DBIx-MSSQLReporter-1.04/README
DBIx-MSSQLReporter-1.04/Build.PL
DBIx-MSSQLReporter-1.04/Makefile.PL
DBIx-MSSQLReporter-1.04/examples
DBIx-MSSQLReporter-1.04/examples/sql8-Demo-2.pl
DBIx-MSSQLReporter-1.04/examples/sql8-Demo-1.pl
DBIx-MSSQLReporter-1.04/examples/sql8-Demo-3.pl
DBIx-MSSQLReporter-1.04/lib
DBIx-MSSQLReporter-1.04/lib/DBIx
DBIx-MSSQLReporter-1.04/lib/DBIx/MSSQLReporter.pm
DBIx-MSSQLReporter-1.04/t
DBIx-MSSQLReporter-1.04/t/test.t
DBIx-MSSQLReporter-1.04/t/pod.t
CPAN: File::Temp loaded ok (v0.18)
CPAN: Module::Build loaded ok (v0.280801)

  CPAN.pm: Going to build R/RS/RSAVAGE/DBIx-MSSQLReporter-1.04.tgz

Checking if your kit is complete...
Looks good
Warning: prerequisite DBD::ADO 2.91 not found.
Warning: prerequisite Test::Pod 0 not found.
Writing Makefile for DBIx::MSSQLReporter
Could not read 'C:\Perl\cpan\build\DBIx-MSSQLReporter-1.04-OJoOT3\META.yml'. Fal
ling back to other methods to determine prerequisites
---- Unsatisfied dependencies detected during ----
----    RSAVAGE/DBIx-MSSQLReporter-1.04.tgz   ----
    DBD::ADO [requires]
    Test::Pod [requires]
Shall I follow them and prepend them to the queue
of modules we are processing right now? [yes] yes
Running make test
  Delayed until after prerequisites
Running make install
  Delayed until after prerequisites
Running install for module 'DBD::ADO'
Running make for S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz
Checksum for C:\Perl\cpan\sources\authors\id\S\SG\SGOELDNER\DBD-ADO-2.96.tar.gz
ok
DBD-ADO-2.96/
DBD-ADO-2.96/Changes
DBD-ADO-2.96/ex/
DBD-ADO-2.96/ex/Enums.patch
DBD-ADO-2.96/ex/Local/
DBD-ADO-2.96/ex/Local/DBD/
DBD-ADO-2.96/ex/Local/DBD/ADO/
DBD-ADO-2.96/ex/Local/DBD/ADO/DSN.pm
DBD-ADO-2.96/ex/OpenSchema.pl
DBD-ADO-2.96/ex/Provider.pl
DBD-ADO-2.96/lib/
DBD-ADO-2.96/lib/DBD/
DBD-ADO-2.96/lib/DBD/ADO/
DBD-ADO-2.96/lib/DBD/ADO/Const.pm
DBD-ADO-2.96/lib/DBD/ADO/GetInfo.pm
DBD-ADO-2.96/lib/DBD/ADO/TypeInfo.pm
DBD-ADO-2.96/lib/DBD/ADO.pm
DBD-ADO-2.96/Makefile.PL
DBD-ADO-2.96/MANIFEST
DBD-ADO-2.96/MANIFEST.SKIP
DBD-ADO-2.96/META.yml
DBD-ADO-2.96/README
DBD-ADO-2.96/t/
DBD-ADO-2.96/t/01base.t
DBD-ADO-2.96/t/02ads.t
DBD-ADO-2.96/t/02cxn.t
DBD-ADO-2.96/t/04os.t
DBD-ADO-2.96/t/05gi.t
DBD-ADO-2.96/t/06ti.t
DBD-ADO-2.96/t/07q.t
DBD-ADO-2.96/t/11prep.t
DBD-ADO-2.96/t/12bind.t
DBD-ADO-2.96/t/12ins_b.t
DBD-ADO-2.96/t/12ins_q.t
DBD-ADO-2.96/t/13count.t
DBD-ADO-2.96/t/14rows.t
DBD-ADO-2.96/t/15large.t
DBD-ADO-2.96/t/18bc.t
DBD-ADO-2.96/t/19misc.t
DBD-ADO-2.96/t/21sth.t
DBD-ADO-2.96/t/23null.t
DBD-ADO-2.96/t/25curs.t
DBD-ADO-2.96/t/27lob.t
DBD-ADO-2.96/t/29timeout.t
DBD-ADO-2.96/t/31txn.t
DBD-ADO-2.96/t/41ddtbl.t
DBD-ADO-2.96/t/42ddcol.t
DBD-ADO-2.96/t/43ddpk.t
DBD-ADO-2.96/t/44ddfk.t
DBD-ADO-2.96/t/45ddst.t
DBD-ADO-2.96/t/51qi.t
DBD-ADO-2.96/t/DBD_TEST.pm
DBD-ADO-2.96/ToDo

  CPAN.pm: Going to build S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz

Argument "6.42_01" isn't numeric in numeric ge (>=) at Makefile.PL line 27.

Configuring DBD::ADO ...

>>> Remember to actually *READ* the README file!
>>> And re-read it if you have any problems.

*** You're using Microsoft Visual C++ compiler or similar but
    the LIB and INCLUDE environment variables are not both set.

    You need to run the VCVARS32.BAT batch file that was supplied
    with the compiler before you can use it.

    A copy of vcvars32.bat can typically be found in the following
    directories under your Visual Studio install directory:
        Visual C++ 6.0:     vc98\bin
        Visual Studio .NET: vc7\bin

    Find it, run it, then retry this.

    If you think this error is not correct then just set the LIB and
    INCLUDE environment variables to some value to disable the check.
Warning: No success on command[C:\Perl\bin\perl.exe Makefile.PL]
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
  SGOELDNER/DBD-ADO-2.96.tar.gz
  C:\Perl\bin\perl.exe Makefile.PL -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Running install for module 'Test::Pod'
Running make for P/PE/PETDANCE/Test-Pod-1.26.tar.gz
Checksum for C:\Perl\cpan\sources\authors\id\P\PE\PETDANCE\Test-Pod-1.26.tar.gz
ok
Test-Pod-1.26/
Test-Pod-1.26/t/
Test-Pod-1.26/t/spaced-directives.pod
Test-Pod-1.26/t/unknown-directive.t
Test-Pod-1.26/t/spaced-directives.t
Test-Pod-1.26/t/pod/
Test-Pod-1.26/t/pod/good-pod-script
Test-Pod-1.26/t/pod/no_pod.pod
Test-Pod-1.26/t/pod/good.pod
Test-Pod-1.26/t/empty-file.pod
Test-Pod-1.26/t/cut-outside-block.pod
Test-Pod-1.26/t/good.t
Test-Pod-1.26/t/item-ordering.pod
Test-Pod-1.26/t/all_pod_files.t
Test-Pod-1.26/t/selftest.t
Test-Pod-1.26/t/unknown-directive.pod
Test-Pod-1.26/t/item-ordering.t
Test-Pod-1.26/t/00-load.t
Test-Pod-1.26/t/load.t
Test-Pod-1.26/t/missing-file.t
Test-Pod-1.26/t/pod.t
Test-Pod-1.26/t/cut-outside-block.t
Test-Pod-1.26/Changes
Test-Pod-1.26/MANIFEST
Test-Pod-1.26/Pod.pm
Test-Pod-1.26/Makefile.PL
Test-Pod-1.26/META.yml

  CPAN.pm: Going to build P/PE/PETDANCE/Test-Pod-1.26.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for Test::Pod
Could not read 'C:\Perl\cpan\build\Test-Pod-1.26-lShI5s\META.yml'. Falling back
to other methods to determine prerequisites
'nmake' is not recognized as an internal or external command,
operable program or batch file.
  PETDANCE/Test-Pod-1.26.tar.gz
  nmake -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running make for R/RS/RSAVAGE/DBIx-MSSQLReporter-1.04.tgz
  Has already been unwrapped into directory C:\Perl\cpan\build\DBIx-MSSQLReporte
r-1.04-OJoOT3

  CPAN.pm: Going to build R/RS/RSAVAGE/DBIx-MSSQLReporter-1.04.tgz

Warning: Prerequisite 'DBD::ADO => 2.91' for 'R/RS/RSAVAGE/DBIx-MSSQLReporter-1.
04.tgz' failed when processing 'S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz' with 'writem
akefile => NO 'C:\Perl\bin\perl.exe Makefile.PL' returned status 65280'. Continu
ing, but chances to succeed are limited.
Warning: Prerequisite 'Test::Pod => 0' for 'R/RS/RSAVAGE/DBIx-MSSQLReporter-1.04
.tgz' failed when processing 'P/PE/PETDANCE/Test-Pod-1.26.tar.gz' with 'make =>
NO'. Continuing, but chances to succeed are limited.
'nmake' is not recognized as an internal or external command,
operable program or batch file.
  RSAVAGE/DBIx-MSSQLReporter-1.04.tgz
  nmake -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Could not read 'C:\Perl\cpan\build\DBD-ADO-2.96-M2P1gn\META.yml'. Falling back t
o other methods to determine prerequisites
Failed during this command:
 SGOELDNER/DBD-ADO-2.96.tar.gz                : writemakefile NO 'C:\Perl\bin\pe
rl.exe Makefile.PL' returned status 65280
 RSAVAGE/DBIx-MSSQLReporter-1.04.tgz          : make NO
 PETDANCE/Test-Pod-1.26.tar.gz                : make NO


```

---

### Post by DouglasAWh on 2008-02-20
ok, here's the latest:

```

cpan> install DBD::ADO
Running install for module 'DBD::ADO'
Running make for S/SG/SGOELDNER/DBD-ADO-2.96.tar.gz
  Has already been unwrapped into directory C:\Perl\cpan\build\DBD-ADO-2.96-Cxyo
uJ
  'C:\Perl\bin\perl.exe Makefile.PL' returned status 65280, won't make
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install

```

I installed Visual C++ Express because of some compiling errors that were discussed in another thread (I think...may have been on another forum).  Still doesn't work though.  Ugh.

---

### Post by DouglasAWh on 2008-02-20
more perl troubles:

```

cpan> install Test::Pod
Running install for module 'Test::Pod'
Running make for P/PE/PETDANCE/Test-Pod-1.26.tar.gz
  Has already been unwrapped into directory C:\Perl\cpan\build\Test-Pod-1.26-q50
VDk
Could not make: Unknown error
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible

```

seems to be of the same vein:
```

cpan> install YAML::XS
Running install for module 'YAML::XS'
Running make for I/IN/INGY/YAML-LibYAML-0.26.tar.gz
Fetching with LWP:
  http://ppm.activestate.com/CPAN/authors/id/I/IN/INGY/YAML-LibYAML-0.26.tar.gz
Fetching with LWP:
  http://ppm.activestate.com/CPAN/authors/id/I/IN/INGY/CHECKSUMS
Checksum for C:\Perl\cpan\sources\authors\id\I\IN\INGY\YAML-LibYAML-0.26.tar.gz
ok
YAML-LibYAML-0.26/
YAML-LibYAML-0.26/Changes
YAML-LibYAML-0.26/inc/
YAML-LibYAML-0.26/inc/Module/
YAML-LibYAML-0.26/inc/Module/Install/
YAML-LibYAML-0.26/inc/Module/Install/Base.pm
YAML-LibYAML-0.26/inc/Module/Install/Can.pm
YAML-LibYAML-0.26/inc/Module/Install/Fetch.pm
YAML-LibYAML-0.26/inc/Module/Install/Include.pm
YAML-LibYAML-0.26/inc/Module/Install/Makefile.pm
YAML-LibYAML-0.26/inc/Module/Install/Metadata.pm
YAML-LibYAML-0.26/inc/Module/Install/TestBase.pm
YAML-LibYAML-0.26/inc/Module/Install/Win32.pm
YAML-LibYAML-0.26/inc/Module/Install/WriteAll.pm
YAML-LibYAML-0.26/inc/Module/Install.pm
YAML-LibYAML-0.26/inc/Spiffy.pm
YAML-LibYAML-0.26/inc/Test/
YAML-LibYAML-0.26/inc/Test/Base/
YAML-LibYAML-0.26/inc/Test/Base/Filter.pm
YAML-LibYAML-0.26/inc/Test/Base.pm
YAML-LibYAML-0.26/inc/Test/Builder/
YAML-LibYAML-0.26/inc/Test/Builder/Module.pm
YAML-LibYAML-0.26/inc/Test/Builder.pm
YAML-LibYAML-0.26/inc/Test/More.pm
YAML-LibYAML-0.26/lib/
YAML-LibYAML-0.26/lib/YAML/
YAML-LibYAML-0.26/lib/YAML/LibYAML.pm
YAML-LibYAML-0.26/lib/YAML/XS.pm
YAML-LibYAML-0.26/LibYAML/
YAML-LibYAML-0.26/LibYAML/api.c
YAML-LibYAML-0.26/LibYAML/config.h
YAML-LibYAML-0.26/LibYAML/dumper.c
YAML-LibYAML-0.26/LibYAML/emitter.c
YAML-LibYAML-0.26/LibYAML/lib/
YAML-LibYAML-0.26/LibYAML/lib/YAML/
YAML-LibYAML-0.26/LibYAML/lib/YAML/XS/
YAML-LibYAML-0.26/LibYAML/lib/YAML/XS/LibYAML.pm
YAML-LibYAML-0.26/LibYAML/LibYAML.xs
YAML-LibYAML-0.26/LibYAML/loader.c
YAML-LibYAML-0.26/LibYAML/Makefile.PL
YAML-LibYAML-0.26/LibYAML/parser.c
YAML-LibYAML-0.26/LibYAML/perl_libyaml.c
YAML-LibYAML-0.26/LibYAML/perl_libyaml.h
YAML-LibYAML-0.26/LibYAML/ppport.h
YAML-LibYAML-0.26/LibYAML/ppport_sort.h
YAML-LibYAML-0.26/LibYAML/reader.c
YAML-LibYAML-0.26/LibYAML/scanner.c
YAML-LibYAML-0.26/LibYAML/test.pl
YAML-LibYAML-0.26/LibYAML/writer.c
YAML-LibYAML-0.26/LibYAML/yaml.h
YAML-LibYAML-0.26/LibYAML/yaml_private.h
YAML-LibYAML-0.26/Makefile.PL
YAML-LibYAML-0.26/MANIFEST
YAML-LibYAML-0.26/META.yml
YAML-LibYAML-0.26/README
YAML-LibYAML-0.26/t/
YAML-LibYAML-0.26/t/alias.t
YAML-LibYAML-0.26/t/api.t
YAML-LibYAML-0.26/t/blessed.t
YAML-LibYAML-0.26/t/boolean.t
YAML-LibYAML-0.26/t/bug-pvf.t
YAML-LibYAML-0.26/t/bug-stack.t
YAML-LibYAML-0.26/t/changes.t
YAML-LibYAML-0.26/t/code.t
YAML-LibYAML-0.26/t/data/
YAML-LibYAML-0.26/t/data/basic.t
YAML-LibYAML-0.26/t/dump.t
YAML-LibYAML-0.26/t/empty.t
YAML-LibYAML-0.26/t/error.t
YAML-LibYAML-0.26/t/file.t
YAML-LibYAML-0.26/t/glob.t
YAML-LibYAML-0.26/t/load.t
YAML-LibYAML-0.26/t/null.t
YAML-LibYAML-0.26/t/private.t
YAML-LibYAML-0.26/t/quote.t
YAML-LibYAML-0.26/t/ref-scalar.t
YAML-LibYAML-0.26/t/regexp.t
YAML-LibYAML-0.26/t/string_nulls.t
YAML-LibYAML-0.26/t/tags.t
YAML-LibYAML-0.26/t/TestYAML.pm
YAML-LibYAML-0.26/t/TestYAMLTests.pm
YAML-LibYAML-0.26/t/utf8.t
YAML-LibYAML-0.26/t/yaml_tests.yaml

  CPAN.pm: Going to build I/IN/INGY/YAML-LibYAML-0.26.tar.gz

The required 'nmake' executable not found, fetching it...
Fetching 'Nmake15.exe' from download.microsoft.com... done!
Checking if your kit is complete...
Looks good
Prototype mismatch: sub main::prompt: none vs ($;$) at C:/Perl/lib/ExtUtils/Make
Maker.pm line 187
Writing Makefile for YAML::XS::LibYAML
Writing Makefile for YAML::LibYAML
Could not read 'C:\Perl\cpan\build\YAML-LibYAML-0.26-VqahGm\META.yml'. Falling b
ack to other methods to determine prerequisites

Microsoft (R) Program Maintenance Utility   Version 1.50
Copyright (c) Microsoft Corp 1988-94. All rights reserved.

cp lib/YAML/LibYAML.pm blib\lib\YAML\LibYAML.pm
cp lib/YAML/XS.pm blib\lib\YAML\XS.pm
        nmake -f Makefile all -nologo
cp lib/YAML/XS/LibYAML.pm ..\blib\lib\YAML\XS\LibYAML.pm
        cl -c  -I.  -nologo -GF -W3 -MD -Zi -DNDEBUG -O1 -DWIN32 -D_CONSOLE -DNO
_STRICT -DHAVE_DES_FCRYPT -DUSE_SITECUSTOMIZE -DPRIVLIB_LAST_IN_INC -DPERL_IMPLI
CIT_CONTEXT -DPERL_IMPLICIT_SYS -DUSE_PERLIO -DPERL_MSVCRT_READFIX -MD -Zi -DNDE
BUG -O1    -DVERSION=\"\"  -DXS_VERSION=\"\"  "-IC:\Perl\lib\CORE"  -DHAVE_CONFI
G_H -DYAML_DECLARE_EXPORT api.c
'cl' is not recognized as an internal or external command,
operable program or batch file.
NMAKE : fatal error U1077: 'C:\WINDOWS\system32\cmd.exe' : return code '0x1'
Stop.
NMAKE : fatal error U1077: 'C:\WINDOWS\system32\cmd.exe' : return code '0x2'
Stop.
  INGY/YAML-LibYAML-0.26.tar.gz
  nmake -- NOT OK
Warning (usually harmless): 'YAML' not installed, will not store persistent stat
e
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 INGY/YAML-LibYAML-0.26.tar.gz                : make NO

```

---

