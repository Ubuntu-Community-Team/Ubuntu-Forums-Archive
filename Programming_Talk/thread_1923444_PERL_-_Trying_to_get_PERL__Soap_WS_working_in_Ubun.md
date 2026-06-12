---
title: "PERL - Trying to get PERL / Soap WS working in Ubuntu"
date: 2012-02-10
forum: Programming Talk
---

### Post by A4orce84 on 2012-02-10
Hey Eveyone,

Trying to get my PERL script (which uses SOAP) working in my Ubuntu, but keep getting the following error message:

```
aahmad@aahmad-lt:~/Desktop/Gomez/GomezWebServiceExamples$ perl gomezws.pl
Can't locate SOAP/Data/Builder.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at gomezws.pl line 15.
BEGIN failed--compilation aborted at gomezws.pl line 15.
aahmad@aahmad-lt:~/Desktop/Gomez/GomezWebServiceExamples$

```

Did some research and found a few things about installing SOAP:
[http://forums.fedoraforum.org/showthread.php?t=61221](http://forums.fedoraforum.org/showthread.php?t=61221)


But nothing has worked so far. Any help would be greatly appreciated.

Thanks!


--Asif

---

### Post by TheFu on 2012-02-10
Your issue is with perl, not ubuntu.

Mixing OS perl with cpan perl modules is dangerous.

If you are a perl programmer, then you probably do not want to use the Ubuntu packages for anything related to perl  Check out Perlbrew which will let you have complete perl install separate from old versions of perl that Ubuntu uses out of necessity.  Perlbrew lets you switch between different perl versions as needed too.  Follow these instructions: [http://perlbrew.pl/](http://perlbrew.pl/)
Further, perlbrew will let you install cpan modules into the specific version of perl that you choose and not screw with the OS perl modules.

Then you will want to understand CPAN.  Lots of perl programmers use cpanminus, cpanm, for that interface.  [http://search.cpan.org/~miyagawa/App-cpanminus-1.5007/lib/App/cpanminus.pm]("http://search.cpan.org/%7Emiyagawa/App-cpanminus-1.5007/lib/App/cpanminus.pm") is the current version.

If you just want to ignore my suggestions and solve this 1 problem (which will lead to other problems soon enough), then 
$ sudo cpan -i SOAP::Data::Builder
should be all you need. This should follow all the dependencies and install them too.  I really recommend that you do not do this until after you get perlbrew working so you don't mix cpan modules with Ubuntu-perl stuff. Also, if you use perlbrew, then you won't need root/sudo.

---

### Post by A4orce84 on 2012-02-12
Thanks TheFu! I'm trying to get perlbrew setup, but's not working as I thought it would. I see the following output:

```
aahmad@aahmad-lt:~$ curl -kL http://install.perlbrew.pl | bash
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   920  100   920    0     0    809      0  0:00:01  0:00:01 --:--:-- 10952

## Download the latest perlbrew

## Installing perlbrew
The perlbrew is installed as:

    ~/perl5/perlbrew/bin/perlbrew

You may trash the downloaded /tmp/perlbrew-31656 from now on.

Perlbrew environment initiated under ~/perl5/perlbrew

Append the following piece of code to the end of your ~/.bash_profile and start a
new shell, perlbrew should be up and fully functional from there:

    source ~/perl5/perlbrew/etc/bashrc

For further instructions, simply run `perlbrew` to see the help message.

Happy brewing!

## Installing patchperl

## Done
```

Tried googling if there is write-up on how to set it up in Ubuntu, but so far I have come up with nothing. Any help would be greatly appreciated!

Thanks.

--Asif

---

### Post by A4orce84 on 2012-02-12
So update got it installed and working. Still seeing the same error when I try to compile my PERL package though.

Do I need to switch PERL or what do I need to do specifically so everything is working correctly?

--Asif

---

### Post by shawnhcorey on 2012-02-13
You're missing the module. Try this and then re-run.
```
cpan SOAP::Data::Builder
```

---

### Post by TheFu on 2012-02-13
Did you properly setup your perlbrew environment?
What does 
$ which perl 

return?  Somthing like ~/perl5/perlbrew/perls/perl-5.10.1/bin/perl is expected.

$ perlbrew use
returns what?

When you invoke your script(s), which perl is being used?  Do you need to change the first line to be 
#!perl 
or
#!/usr/bin/env perl

After you are certain you have the correct perlbrew setup, then you probably want to use cpanm to install CPAN modules as necessary.  You can easily switch between different versions of perl and the entire environments using perlbrew.

---

### Post by A4orce84 on 2012-02-18
I think so, here is the output to my commands:


```
aahmad@aahmad-lt:~$ which perl
/home/aahmad/perl5/perlbrew/perls/perl-5.14.2/bin/perl
aahmad@aahmad-lt:~$ perlbrew use
Currently using perl-5.14.2
aahmad@aahmad-lt:~$ 
```


When I invoke my script I see the following error:


aahmad@aahmad-lt:~/Desktop/Gomez/GomezWebServiceExamples$ perl gomezws.pl
Can't locate SOAP/Lite.pm in @INC (@INC contains: /home/aahmad/perl5/perlbrew/perls/perl-5.14.2/lib/site_perl/5.14.2/i686-linux /home/aahmad/perl5/perlbrew/perls/perl-5.14.2/lib/site_perl/5.14.2 /home/aahmad/perl5/perlbrew/perls/perl-5.14.2/lib/5.14.2/i686-linux /home/aahmad/perl5/perlbrew/perls/perl-5.14.2/lib/5.14.2 .) at gomezws.pl line 13.
BEGIN failed--compilation aborted at gomezws.pl line 13.
aahmad@aahmad-lt:~/Desktop/Gomez/GomezWebServiceExamples$ 


Line #13 in my gomezws.pl file states:


```
use SOAP::Lite ( +trace => 'fault', maptype => {} );
```


If anyone needs any additional information, please let me know! =)

Thanks again!


--Asif

---

### Post by A4orce84 on 2012-02-19
Ttt

---

### Post by TheFu on 2012-02-20
> **A4orce84 said:**
> 
aahmad@aahmad-lt:~/Desktop/Gomez/GomezWebServiceExamples$ perl gomezws.pl
Can't locate SOAP/Lite.pm in @INC (@INC contains: /home/aahmad/perl5/perlbrew ...... 

There's the error from your output.  
Perl is pretty good at telling you the current error.
Did you try to install that module?

---

### Post by A4orce84 on 2012-02-22
I'm not sure how to honestly? If it was the soap one that was pasted earlier, I tried that but it still does not work to no avail. =(

---

### Post by A4orce84 on 2012-02-25
Anyone?

---

### Post by A4orce84 on 2012-02-27
Ttt

---

