---
title: "GNUcash and Finance::quote"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Palmstroem on 2008-05-15
Hi folks,
I am having a problem with GNUcash using the stock price updating module. The program gnc-fq-dump works OK in a terminal, and GNUcash works OK but I could not get stock prices. System is Ubuntu Hardy. Any ideas what to do? From a terminal I get
```
$ gnucash -v
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

GnuCash 2.2.4
Build vom 2008-03-27, Revision r16997

```Don't know what this means :confused:

---

### Post by Palmstroem on 2008-05-15
Recently I noticed that I can call stock prices from within GNUcash only if I use Yahoo as an information source! In particular, Yahoo_Europe and others do not work. To me it appears that there is a problem with the date format. gnc-fq-dump with non-Yahoo sources always returns 0/0/2000 as the date!

Maybe there is something wrong with the gnc-fq-dump configuration? Any help welcome! :)

---

### Post by Palmstroem on 2008-05-21
I removed GNUcash and its libraries. Then I re-installed only the perl module libfinance-quote-perl, version 1.13-1. Then I downloaded the recent Finance-Quote-1.13 source. These are perl scripts: no need for compilation. However, when I run some tests I get the following errors:
```
$ ./currency.t
1..8
# Running under perl version 5.008008 for linux
# Current time local: Wed May 21 08:38:55 2008
# Current time GMT:   Wed May 21 06:38:55 2008
# Using Test.pm version 1.25
ok 1
ok 2
ok 3
ok 4
Use of uninitialized value in numeric lt (<) at /usr/share/perl5/Finance/Quote.pm line 637.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Finance/Quote.pm line 655.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 660.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 660.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 661.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 661.
not ok 5
# Failed test 5 in ./currency.t at line 27
#  ./currency.t line 27 is: ok($baseinfo{"12150.PA","success"});
Use of uninitialized value in numeric lt (<) at /usr/share/perl5/Finance/Quote.pm line 637.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Finance/Quote.pm line 655.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 660.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 660.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 661.
Use of uninitialized value in sprintf at /usr/share/perl5/Finance/Quote.pm line 661.
not ok 6
# Failed test 6 in ./currency.t at line 32
#  ./currency.t line 32 is: ok($info{"12150.PA","success"});		# Test 6
Use of uninitialized value in string eq at ./currency.t line 33.
not ok 7
# Failed test 7 in ./currency.t at line 33
#  ./currency.t line 33 is: ok($info{"12150.PA","currency"} eq "AUD");	# Test 7
Use of uninitialized value in numeric gt (>) at ./currency.t line 34.
not ok 8
# Failed test 8 in ./currency.t at line 34
#  ./currency.t line 34 is: ok($info{"12150.PA","price"} > 0);		# Test 8

```
What should I do?

---

### Post by Xiong Chiamiov on 2008-05-21
To me, those problems sound like something with the developer.

Since GNUcash was working, except for that option being disabled when the .deb maintainer compiled it, you can try downloading the source for that and running the configure with that option.

---

### Post by Palmstroem on 2008-05-21
No, I de-installed GNUcash! Finance::quote is a bunch of perl scripts running without GNUcash, just from the terminal if you like. They only need a perl environment - which is apparently found in the system. To me it sounds like an error in some date-converting module somewhere in the perl framework...:confused:

---

### Post by caughran on 2009-05-30
I've used Yahoo in the past for Canadian and US stock prices. That has continued with no problems. But now I find I can't get currency quotes -- important in Canada, since the US is our largest customer. And I've had no quotations for Canadian mutual funds for a long time--again, it stopped working. There may be a site I should point GnuCash toward, but I don't know which.

This seems to have happened at about the time I installed Jaunty over Hardy, and reinstalled Gnucash. 

Somewhere else, there were some suggestions for what to do to see why currency quotes weren't available. The first asked to call Gnucash from terminal with --debug, and get quotes. Here's the output:

```
jim@jimjanet:~$ gnucash --debug
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.16
gwenhywfar-INFO: plugin.c:  577: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  577: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  577: Plugin type "dbio" unregistered

```

That sounds like it might be the problem, if I knew where to get the plugins and how to register them.

I don't understand the outputs below.

```

jim@jimjanet:~$ gnc-fq-check
("1.16" "vwd" "yahoo_nz" "australia" "amfiindia" "usfedbonds" "aex_options" "canada" "yahoo" "adig" "aiahk" "yahoo_australia" "unionfunds" "lerevenu" "asia" "tsx" "indiamutual" "known_currencies" "fidelity_direct" "goldmoney" "tdwaterhouse" "trustnet" "ftportfolios_direct" "cominvest" "ftportfolios" "morningstar" "tdefunds" "za" "aex_futures" "fundlibrary" "stockhousecanada_fund" "yahoo_europe" "platinum" "maninv" "tsp" "financecanada" "usa" "france" "troweprice" "nasdaq" "bmonesbittburns" "yahoo_asia" "tiaacref" "troweprice_direct" "seb_funds" "greece" "fidelity" "yahoo_brasil" "fetch_live_currencies" "dwsfunds" "finland" "hex" "asegr" "brasil" "deka" "canadamutual" "nyse" "asx" "finanzpartner" "fool" "dutch" "uk_unit_trusts" "nzx" "aex" "nz" "vanguard" "europe" "bourso")

jim@jimjanet:~$ sudo gnc-fq-update
CPAN: Storable loaded ok (v2.18)
Going to read /home/jim/.cpan/Metadata
  Database was generated on Sun, 24 May 2009 10:26:54 GMT
CPAN: LWP::UserAgent loaded ok (v5.826)
CPAN: Time::HiRes loaded ok (v1.9711)

I would like to connect to one of the following sites to get 'authors/01mailrc.txt.gz':

 http://www.perl.org/CPAN/
 ftp://ftp.perl.org/pub/CPAN/

Is it OK to try to connect to the Internet? [yes] yes
Fetching with LWP:
  http://www.perl.org/CPAN/authors/01mailrc.txt.gz
Going to read /home/jim/.cpan/sources/authors/01mailrc.txt.gz
............................................................................DONE
Fetching with LWP:
  http://www.perl.org/CPAN/modules/02packages.details.txt.gz
Going to read /home/jim/.cpan/sources/modules/02packages.details.txt.gz
  Database was generated on Thu, 28 May 2009 15:27:01 GMT
...............
  New CPAN.pm version (v1.94) available.
  [Currently running version is v1.9205]
  You might want to try
    install CPAN
    reload cpan
  to both upgrade CPAN.pm and run the new version without leaving
  the current session.
.............................................................DONE
Fetching with LWP:
  http://www.perl.org/CPAN/modules/03modlist.data.gz
Going to read /home/jim/.cpan/sources/modules/03modlist.data.gz
............................................................................DONE
Going to write /home/jim/.cpan/Metadata
LWP is up to date (5.826).
Date::Manip is up to date (5.54).
HTML::Parser is up to date (3.60).
HTML::TableExtract is up to date (2.10).
Crypt::SSLeay is up to date (0.57).
Finance::Quote is up to date (1.16).

```

---

### Post by samib on 2009-11-17
> **Palmstroem said:**
> Recently I noticed that I can call stock prices from within GNUcash only if I use Yahoo as an information source! In particular, Yahoo_Europe and others do not work. To me it appears that there is a problem with the date format. gnc-fq-dump with non-Yahoo sources always returns 0/0/2000 as the date!

Maybe there is something wrong with the gnc-fq-dump configuration? Any help welcome! :)



I have just come over to GNUCASH from Microsoft Money. Have managed to get everything I need working ok. Only problem is fund quote updates. 

Have seen many threads about problems in actually obtaining readable information. 

A few more about the currency unit from Yahoo Europe being 100X larger than it should be. This is my problem but so far cannot find any thread post where this problem has been solved. 

Can anyone help with this or point me in the right direction?

---

