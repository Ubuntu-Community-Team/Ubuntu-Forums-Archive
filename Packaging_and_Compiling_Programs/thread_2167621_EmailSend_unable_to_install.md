---
title: "Email::Send unable to install"
date: 2013-08-14
forum: Packaging and Compiling Programs
---

### Post by srini_vasan on 2013-08-14
Hello ,

I Use the following code in my program . Unfortunately when i compile i get the following error message.

[COLOR=#ff0000][FONT=UbuntuMono]rinidelite@vm-0:~/Applications$ perl ./test_1.pl[/FONT]
[FONT=UbuntuMono]Can't locate Email/Send.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/[/FONT]
[FONT=UbuntuMono]lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at ./test_1.pl line 7.[/FONT]
[FONT=UbuntuMono]BEGIN failed--compilation aborted at ./test_1.pl line 7.[/FONT][/COLOR]

So i decided to install the mail package Again .. Failed to install 
[COLOR=#ff0000][FONT=UbuntuMono]_cpan[1]> _**install Email::Send::Gmail**[/FONT]
[FONT=UbuntuMono]Going to read '/home/srinidelite/.cpan/Metadata'[/FONT]
[FONT=UbuntuMono]  Database was generated on Tue, 13 Aug 2013 11:29:02 GMT[/FONT]
[FONT=UbuntuMono]Running install for module 'Email::Send::Gmail'[/FONT]
[FONT=UbuntuMono]Running make for L/LB/LBROCARD/Email-Send-Gmail-0.33.tar.gz[/FONT]
[FONT=UbuntuMono]Catching error: "mkdir /home/srinidelite/.cpan/sources/authors/id/L: Permission denied at /usr/share/perl/5.14/CPAN/FTP.pm line 513\cJ" at /usr/share/perl[/FONT]
[FONT=UbuntuMono]/5.14/CPAN.pm line 391[/FONT]
[FONT=UbuntuMono]        CPAN::shell() called at /usr/share/perl/5.14/App/Cpan.pm line 295[/FONT]
[FONT=UbuntuMono]        App::Cpan::_process_options('App::Cpan') called at /usr/share/perl/5.14/App/Cpan.pm line 364[/FONT]
[FONT=UbuntuMono]        App::Cpan::run('App::Cpan') called at /usr/bin/cpan line 11[/FONT][/COLOR]

kindly help me to get out from the issues im facing it .

Thanks in Advance,
Srini

---

### Post by oldos2er on 2013-08-14
Moved to Packaging & Compiling Programs.

---

