---
title: "Nifty Gmail Checker (checkgmail)"
date: 2005-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by poofyhairguy on 2005-10-12
Written By [arnieboy]("http://ubuntuforums.org/member.php?u=12261")

Checkgmail is a nifty perl program which sits in your system tray and checks your gmail account. looks almost like its windows counterpart.
there are other alternatives like the firefox gmail checker (got to have firefox open for that), kcheckgmail (the latest version has dependency problems with ubuntu libs) and the gdesklets sidecandy gmail checker which also is pretty good. but if u want a gmail checker which sits unobtrusively in ur system tray and works flawlessly u should check this one out. Herez how to install it:
first download the compressed file from a mirror of your choice:
```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.3.tar.bz2?download
```
Now do the following:
```
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev make manpages-dev autoconf automake1.9 libtool flex bison gcc
```
Next do the following:
```
sudo perl -MCPAN -e 'install Bundle::LWP'
sudo perl -MCPAN -e 'install Crypt::Simple'
sudo perl -MCPAN -e 'install XML::Simple'
sudo perl -MCPAN -e 'install Crypt::SSLeay'

```All the above commands will configure your system and ask a bunch of simple questions which should be easy enough to answer (in my case almost all of them were defaults). They will install the perl modules.
Now do the following:
```
tar -xjf checkgmail-1.3.tar.bz2
```
now a folder called checkgmail-1.3 will be created in your home folder and inside it will be the checkgmail perl binary which u need to add to system-->preferences-->sessions-->startup programs 
The path of the executable would be */home/user_name/checkgmail-1.3/checkgmail*
U can also open a nautilus window and double click on /home/user_name/checkgmail-1.3/checkgmail to make it run (or run it from terminal). next time u boot in to GNOME it will start automatically and u will see how nifty and unobtrusive it is. 
**please note:** "user_name" is the name of your user account.

EDIT: this is a tip for those who dont share their comps with others. dont log out of gmail in your web browser (just close the browser window) and everytime gmailchecker informs u of new mail, one single click on the icon will take you to your inbox without your having to type your user name and password in the browser again.

---

### Post by zeroverse on 2005-10-13
Thanks.  The script works great.  It would be awesome if you could click on individual emails to go directly to them, but I'm impressed nevertheless.

---

### Post by Adder on 2005-10-13
Thank you Poofy. That worked like a charm.

---

### Post by majikstreet on 2005-10-13
This was great on hoary, still great on breezy :P

---

### Post by gasparov on 2005-10-14
Hi,
```
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running install for module HTML::Tagset
Running make for S/SB/SBURKE/HTML-Tagset-3.04.tar.gz
  Is already unwrapped into directory /home/gas/.cpan/build/HTML-Tagset-3.04
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Running make for G/GA/GAAS/HTML-Parser-3.45.tar.gz
  Is already unwrapped into directory /home/gas/.cpan/build/HTML-Parser-3.45
  Has already been processed within this session
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

```

what am I missing?...i do have build-essential

---

### Post by Adam Lee on 2005-10-14
It seems this checker only checks mails in Inbox.
I label most of my emails because I get 20 different emails every hour and only few actually goes in to inbox.

---

### Post by daviddehoog on 2005-10-14
[QUOTE=Adam Lee]It seems this checker only checks mails in Inbox.
I label most of my emails because I get 20 different emails every hour and only few actually goes in to inbox.[/QUOTE]

Evolution can handle gmail accounts (through POP3) ...

Alternatively, use fetchmail to pull your gmail down with POP3, and use a standard desktop mail checker to monitor your Maildir ?

Not as snazzy as the googlechecker ... but functional :)

Cheers
David

---

### Post by hanzj on 2005-10-14
I ran:
> sudo perl -MCPAN -e 'install Crypt::Simple'

And I'm getting this output:
> --21:40:31--  [ftp://ftp.perl.org/pub/CPAN/authors/id/P/PM/PMQS/CHECKSUMS.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/P/PM/PMQS/CHECKSUMS.gz)
  (try: 5) => `-'
Connecting to ftp.perl.org|163.143.1.21|:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Retrying.

--21:40:36--  [ftp://ftp.perl.org/pub/CPAN/authors/id/P/PM/PMQS/CHECKSUMS.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/P/PM/PMQS/CHECKSUMS.gz)
  (try: 6) => `-'
Connecting to ftp.perl.org|163.143.1.21|:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Retrying.


On and on it goes retrying. But to no avail. 


I then tried the next step:

>  sudo perl -MCPAN -e 'install XML::Simple'

I got the following output:
> 
CPAN: Storable loaded ok
Going to read /home/hanzj/.cpan/Metadata
  Database was generated on Thu, 13 Oct 2005 22:00:32 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: LWP::UserAgent loaded ok
Fetching with LWP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
LWP failed with code[500] message[]
Fetching with Net::FTP:
  [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)

Trying with "/usr/bin/lynx -source" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)

Looking up ftp.perl.org
Making FTP connection to ftp.perl.org
Looking up ftp.perl.org
Making FTP connection to ftp.perl.org
Can't Access `ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz'
Alert!: Unable to access document.

lynx: Can't access startfile

System call "/usr/bin/lynx -source "ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz"  > /home/hanzj/cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar"
returned status 1 (wstat 256)
Warning: expected file [/home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz] doesn't exist

Trying with "/usr/bin/ncftpget" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
Remote host has closed the connection.
Remote host has closed the connection.
Remote host has closed the connection.
ncftpget: cannot open ftp.perl.org: remote host closed control connection.

System call "cd /home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM && /usr/bin/ncftpget "ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz" "
returned status 1 (wstat 256)
Warning: expected file [/home/hanzj/cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz] doesn't exist

Trying with "/usr/bin/wget -O -" to get
    [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
--01:49:52--  [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
           => `-'
Resolving ftp.perl.org... 163.143.1.21
Connecting to ftp.perl.org|163.143.1.21|:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Retrying.

--01:49:53--  [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
  (try: 2) => `-'
Connecting to ftp.perl.org|163.143.1.21|:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Retrying.

I cancel the process by pressing Ctrl-C. Then I run the command again. The final part out the output says:
> 
--01:52:18--  [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz)
  (try:20) => `-'
Connecting to ftp.perl.org|163.143.1.21|:21... connected.
Logging in as anonymous ...
Error in server response, closing control connection.
Giving up.


System call "/usr/bin/wget -O - "ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz"  > /home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar"
returned status 1 (wstat 256)
Warning: expected file [/home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz] doesn't exist
Issuing "/usr/bin/ftp -n"
Not connected.
Local directory now /home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Not connected.
Bad luck... Still failed!
Can't access URL [ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz](ftp://ftp.perl.org/pub/CPAN/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz).

Please check, if the URLs I found in your configuration file () are valid.
The urllist can be edited. E.g. with 'o conf urllist push ftp://myurl/'

Could not fetch authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz
Giving up on '/home/hanzj/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz'
Note: Current database in memory was generated on Thu, 13 Oct 2005 22:00:32 GMT



What's going on?

---

### Post by mustang on 2005-10-14
This is probably a dumb question but is there a way to modify the script so that instead of single clicking, double clicking on the system tray icon would open up your gmail account in a browser?

---

### Post by _Kris_ on 2005-10-17
Will there be a feature in the future to add a PROXY server?
The Gmail checker can't reach gmail when I'm @ work :( 

Thx!

---

### Post by craigmac on 2005-10-17
Could I offer the apt-get package gmail-notify?

Works like a treat and there is no need to do any PERL scripting or any setting up. Maybe I am missing something (or just lucky) but it was a doddle to install for me in Breezy.

Actually looks better than the Windows version and putting it into my Preferences->Sessions->Startup Programs as gmail-notify means that it starts when Gnome starts. 

Hope I haven't rained on the parade. I have to admit that the method listed was really daunting for me but I got it to sporadically work in Kubuntu Hoary. I much prefer gmail-notify (and Gnome in general TBH). 

For me - it just works :)

---

### Post by mustang on 2005-10-19
Hi, 

is it possible to have the gmail checker remember my password or is it intentionally disabled? This wasn't a problem with the previous version

---

### Post by christooss on 2005-10-23
poofyharyguy there is checkgmail 1.4 avalible.

Anyone who had 1.3 installed just extract checkgmail-1.4 and remove checkgmailo-1.3 map and than change startup program map.

---

### Post by dominik on 2005-11-11
what about installing it on kubuntu? i did the installation, but when i try open checkmail it just opens the file in an editor?!

---

### Post by scflymedic on 2005-11-11
Hello all,
I've installed gmail-notifier through synaptic.  My question is which file do I add to the start-up menu.  For some reason I couldn't get the original method to work as I kept getting a failed test XML...blah, blah, blah.  Although, if there is a method to do a complete uninstall, I would be willing to try.  Thanks in advance!
Chuck

EDIT: This is the command that is having the failures.  sudo perl -MCPAN -e 'install XML::Simple'

---

### Post by baraider on 2005-11-16
fresh breezy install and i follow everything... i only need to get XML:simple to install and i'm good

Thanks for the help


================================
andy@ubuntu:~/checkgmail-1.4$ perl checkgmail
CheckGmail v1.4
Copyright \uffff 2005 Owen Marshall

Warning: XML::Simple not found ...

CheckGmail requires the above packages to run
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) and try again ...

===========================================
I only have trouble when i tried to install XML::Simple

=====================================
andy@ubuntu:~/checkgmail-1.4$ sudo perl -MCPAN -e 'install XML::Simple' 
CPAN: Storable loaded ok 
Going to read /home/andy/.cpan/Metadata
  Database was generated on Wed, 16 Nov 2005 10:50:38 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/andy/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz ok
Scanning cache /home/andy/.cpan/build for sizes
XML-Simple-2.14/
XML-Simple-2.14/t/
XML-Simple-2.14/t/1_XMLin.xml
XML-Simple-2.14/t/lib/
XML-Simple-2.14/t/lib/TagsToUpper.pm
XML-Simple-2.14/t/6_ObjIntf.t
XML-Simple-2.14/t/1_XMLin.t
XML-Simple-2.14/t/srt.xml
XML-Simple-2.14/t/4_MemShare.t
XML-Simple-2.14/t/3_Storable.t
XML-Simple-2.14/t/7_SaxStuff.t
XML-Simple-2.14/t/A_XMLParser.t
XML-Simple-2.14/t/0_Config.t
XML-Simple-2.14/t/subdir/
XML-Simple-2.14/t/subdir/test2.xml
XML-Simple-2.14/t/2_XMLout.t
XML-Simple-2.14/t/5_MemCopy.t
XML-Simple-2.14/t/8_Namespaces.t
XML-Simple-2.14/t/test1.xml
XML-Simple-2.14/t/desertnet.src
XML-Simple-2.14/t/9_Strict.t
XML-Simple-2.14/Changes
XML-Simple-2.14/MANIFEST
XML-Simple-2.14/lib/
XML-Simple-2.14/lib/XML/
XML-Simple-2.14/lib/XML/Simple/
XML-Simple-2.14/lib/XML/Simple/FAQ.pod
XML-Simple-2.14/lib/XML/Simple.pm
XML-Simple-2.14/META.yml
XML-Simple-2.14/maketest
XML-Simple-2.14/README
XML-Simple-2.14/Makefile.PL
Removing previously used /home/andy/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

Checking installed modules ...
XML::SAX is installed, it will be used by the test suite
Checking if your kit is complete...
Looks good
Writing Makefile for XML::Simple
cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........ok 13/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........ok 60/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
t/2_XMLout........ok 103/196Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 4/38Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

========================================

---

### Post by baraider on 2005-11-16
Found the answer for my own question....i need to force install XML::Simple

perl -MCPAN -e shell
cpan> force install XML::Simple

Working great now...thanks

---

### Post by cwhitmore75 on 2005-12-15
Doh... figured it out... NM.  Thanks.  

When entering the following command:

```
sudo perl -MCPAN -e 'install XML::Simple'
```

I get the following error:

```
christian@mainbox:~/checkgmail-1.3$ sudo perl -MCPAN -e 'install XML::Simple'
CPAN: Storable loaded ok
Going to read /home/christian/.cpan/Metadata
  Database was generated on Thu, 15 Dec 2005 10:06:21 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/christian/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.1 4.tar.gz ok
Scanning cache /home/christian/.cpan/build for sizes
XML-Simple-2.14/
XML-Simple-2.14/t/
XML-Simple-2.14/t/1_XMLin.xml
XML-Simple-2.14/t/lib/
XML-Simple-2.14/t/lib/TagsToUpper.pm
XML-Simple-2.14/t/6_ObjIntf.t
XML-Simple-2.14/t/1_XMLin.t
XML-Simple-2.14/t/srt.xml
XML-Simple-2.14/t/4_MemShare.t
XML-Simple-2.14/t/3_Storable.t
XML-Simple-2.14/t/7_SaxStuff.t
XML-Simple-2.14/t/A_XMLParser.t
XML-Simple-2.14/t/0_Config.t
XML-Simple-2.14/t/subdir/
XML-Simple-2.14/t/subdir/test2.xml
XML-Simple-2.14/t/2_XMLout.t
XML-Simple-2.14/t/5_MemCopy.t
XML-Simple-2.14/t/8_Namespaces.t
XML-Simple-2.14/t/test1.xml
XML-Simple-2.14/t/desertnet.src
XML-Simple-2.14/t/9_Strict.t
XML-Simple-2.14/Changes
XML-Simple-2.14/MANIFEST
XML-Simple-2.14/lib/
XML-Simple-2.14/lib/XML/
XML-Simple-2.14/lib/XML/Simple/
XML-Simple-2.14/lib/XML/Simple/FAQ.pod
XML-Simple-2.14/lib/XML/Simple.pm
XML-Simple-2.14/META.yml
XML-Simple-2.14/maketest
XML-Simple-2.14/README
XML-Simple-2.14/Makefile.PL
Removing previously used /home/christian/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

Checking installed modules ...
XML::SAX is installed, it will be used by the test suite
Checking if your kit is complete...
Looks good
Writing Makefile for XML::Simple
cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    Not Installed
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/ local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........ok 16/122Unable to recognise encoding of this document at /usr /local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/sha re/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/l ocal/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML /SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....skipped
        all skipped: no XML::Parser
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 test and 1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/454 subtests failed, 98.90% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force
```

Any suggestions? The results of proceeding after this step is a binary that does nothing when you double click it. It wont run from terminal either.

Thanks in advance.

---

### Post by arnieboy on 2005-12-15
try what baraider it (in the post above urs) it might help.

---

### Post by Mguel on 2005-12-18
[**Dooglus **described another method]("http://ubuntuforums.org/showpost.php?p=372215&postcount=106") which is much faster and simple IMHO.

Besides from being faster, I believe it's safer, since you don't have to configure anything (answer questions at perl config).

You have to download a file, extract it (you can do it using nautilus context menu), add a line to checkgmail, and finally install a few libraries, what can be done using the apt-get, or you can use synaptic is you want more detail on what you are installing.

With the sudo perl -MCPAN -e 'install ... method, there where lots of things that I wasn't sure the correct answer (I'm very new to linux), so I just selected the default... but that broke my synaptic :( , [the same that happended to **lynng**]("http://ubuntuforums.org/showpost.php?p=559120&postcount=108")

So here is the link and quote of the post by **Dooglus **
[http://ubuntuforums.org/showpost.php?p=372215&postcount=106](http://ubuntuforums.org/showpost.php?p=372215&postcount=106)
[QUOTE=Dooglus]I found a much easier way to install this, using existing ubuntu packages rather than all that CPAN stuff.  It means you don't need to install any build tools or compile anything, and the only stuff you need to install as root are official ubuntu packages.  I run breezy, so I can't say whether this will work on hoary or not.  Please let me know if I missed anything here - if so, I'll correct it.

In the following instructions, replace "/home/user" with any path you like.

Download the source for checkgmail from sourcefource, as before from```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.4.tar.bz2?download
```Save the file into /home/user.

cd to /home/user and extract the tar file, using```
tar xfj checkgmail-1.4.tar.bz2
```This will make a new directory called checkgmail-1.4 in the current directory.

Breezy is missing one of the Perl modules you need for some reason, so we'll need to get it from CPAN.  We can store it locally, however, like this:```
cd /home/user/checkgmail-1.4 && mkdir Crypt && wget -O Crypt/Simple.pm http://search.cpan.org/src/KASEI/Crypt-Simple-0.06/Simple.pm
```

We need to tell the checkgmail script where to find our local copy of Simple.pm:
cd to /home/user/checkgmail-1.4 and edit the "checkgmail" script to make the first line say```
#!/usr/bin/perl -w -I/home/user/checkgmail-1.4
```

Then all you need to do is ```
sudo apt-get install libwww-perl libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-ssleay-perl libfreezethaw-perl libgtk2-trayicon-perl libxml-simple-perl
```and you're done.  To run the checker, just run```
/home/user/checkgmail-1.4/checkgmail
```[/QUOTE]

I hope this also makes installations of checkgmail easier for others, so more ppl can use it, since I think it's a **really great** app (simple, small, unobtrusive, but with the options enough so you can make it work the way you want, ie command line which permit sound notification, and other stuff).

Best regards,
Mguel

---

### Post by tntc1978 on 2006-02-20
I can only agree with #20 (Mguel) Dooglus' method is alot easier... :-)

---

### Post by phibxr on 2006-02-20
It's working great here. Thanks!

---

### Post by christooss on 2006-02-20
> I can only agree with #20 (Mguel) Dooglus' method is alot easier...

And its working on Dapper too

---

### Post by adam.tropics on 2006-02-21
Both methods worked ok, plus, this also makes a decent mail notification tool for those of us using thunderbird with gmail. Just delete 'firefox %u' in preferences for the default browser, and ensure that in your gmail settings, messages are archived once downloaded. It is no longer clickable in the sense that it doesn't open the gmail webpage, but it still gives needed information and saves running thunderbird all the time. Practicle and better looking than the alternatives i have so far seen.thanks

---

### Post by christooss on 2006-02-21
Gmail notifier extension for Firefox has a Noifier like this to. It rises up when new mail is in Gmail. Very nice. Even thought its saying in Preferences (Only Windows) but I disabled it after installing checkgmail :P

Bye

---

### Post by Krashalot on 2006-02-22
Fresh (and updated) install of Breezy. Using checkgmail-1.6
Followed all the various methods of getting this thing installed. I had to force install XML::Simple. Also added the -I/home/<myname>/checkgmail to the first line of the checkgmail script.
Output is this:

Use of uninitialized value in subroutine entry at ./checkgmail line 937.
Use of uninitialized value in string at ./checkgmail line 950.
Use of uninitialized value in subroutine entry at ./checkgmail line 960.
Use of uninitialized value in subroutine entry at ./checkgmail line 970.
Use of uninitialized value in subroutine entry at ./checkgmail line 983.
Use of uninitialized value in string at ./checkgmail line 992.
Could not find checkgmail.xml in ./ at ./checkgmail line 1002
A thread exited while 2 threads were running.

---

### Post by arnieboy on 2006-02-22
Please ignore this howto. I need to write an updated one. 
poofyhairguy: can u please send this thread to jail?

---

### Post by sailor420 on 2006-02-23
It still seems to work fine, for me, I just did it last night--though I did use the new version of checkgmail.

---

### Post by Mguel on 2006-03-05
Is there a way to have the  the tray icon background transparent?

Thanks,
Mguel

---

### Post by charlieg on 2006-03-27
I always get 503, service not available.  Sure enough, accessing [http://mail.google.com/mail/feed/atom](http://mail.google.com/mail/feed/atom) gives me a 503 after logging in.

Is anybody else suffering from this right now?

](*,)

---

### Post by charlieg on 2006-03-27
[QUOTE=Mguel]Is there a way to have the  the tray icon background transparent?[/QUOTE]
Yes, edit the icons.  Here, I've done it for you.  Download these (I just put them in the checkmail folder) and set custom icons.

---

### Post by sailor420 on 2006-03-28
[QUOTE=charlieg]I always get 503, service not available.  Sure enough, accessing [http://mail.google.com/mail/feed/atom](http://mail.google.com/mail/feed/atom) gives me a 503 after logging in.

Is anybody else suffering from this right now?

](*,)[/QUOTE]

Yes, in several different versions, in Dapper and Breezy, on different computers, on different networks. I've also heard of people having problems with other gmail  checking clients as well. Seems like google changed something on their end that has left the clients hanging...

---

### Post by BobSongs on 2006-05-16
Hey Poofyhairguy;

Don't give up on this tutorial. It just needs a few tweaks.

I'm working on rewriting it now. I can send you the text when I'm satisfied and you can paste into the original spot.

The tutorial's problem is that it's static while the files are updated all the time. My method may be a bit more difficult for the new user, but detailed enough to help her/him get it installed and functionning.

What do you say? I'll send it to you via PM when I'm done. You look it over and decide.

---

### Post by BobSongs on 2006-06-08
Okay; having re-examined my proposed tutorial I have come to the conclusion that the original tutorial doesn't need much in the way of modification. Replace the first code of the tutorial to:```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.9.2.tar.bz2?download
```

That should make it work just fine in Breezy.

:-D

Edit: Here's a revamped version of the tutorial, somewhat reduced and with the correct file names:

[SIZE="3"]**Here's a step by step to install the GMail checker in Breezy Badger (5.10).**[/SIZE]

Place the following into the address bar of your browser:

```
http://prdownloads.sourceforge.net/checkgmail/checkgmail-1.9.2.tar.bz2?use_mirror=kent
```

Save the file to your desktop.

Open a terminal and paste in the following:

```
sudo apt-get install lynx ncftp libgtk2-trayicon-perl openssl libssl-dev make manpages-dev autoconf automake1.9 libtool flex bison gcc
```

Now, paste in the following lines

```
sudo perl -MCPAN -e 'install Bundle::LWP'
sudo perl -MCPAN -e 'install Crypt::Simple'
sudo perl -MCPAN -e 'install XML::Simple'
sudo perl -MCPAN -e 'install Crypt::SSLeay'
```

Unarchive the GMail checker to your home folder

```
tar jxvf ~/Desktop/checkgmail-1.9.2.tar.bz2 -C ~
```

Add GMail to system start:

[INDENT]System -> Preferences -> Sessions -> Startup Programs tab -> Add button -> Browse button[/INDENT]

Browse your way to your home folder, roughly

[INDENT]/home/{USERNAME}/checkgmail-1.9.2/checkgmail[/INDENT]

Replace {USERNAME} with your home name.

To start it immediately do Ctrl + F2.

Click the [**Run with file...**] button. Browse your way to the same folder. Then click Run.

---

### Post by vinnie1 on 2006-06-10
Hi
 I really liked this checkgmail programme so I decided to try it out on the Dapper 
6.06 Release. I used the latest version of checkgmail (1.92) and everything worked as per the original instructions.

 Just thought I would let everyone know.
:D

---

### Post by siman on 2006-12-13
checkgmail seems to be in the repos now - maybe a mod should make a note in the original post... i neraly installed checkgmail, but stumbled upon it

 apt-get install checkgmail

---

