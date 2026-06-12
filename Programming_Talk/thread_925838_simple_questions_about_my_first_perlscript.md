---
title: "simple questions about my first perlscript"
date: 2008-09-21
forum: Programming Talk
---

### Post by cmay on 2008-09-21
hi.
i was trying to write a simple perl script to install the media codecs in ubuntu hardy. i have both amd64 and i386 type pc so i thought i would try to write this as a perl script. i have no experience none what so ever with perl . my question is how is the task of installing  these codecs best done. there must be a better way of doing it than this. 

[PHP]#!/usr/bin/perl 
#cmay 2008: should install the restrictive media codecs 
my $userinput;
my $amd64="sudo apt-get upgrade && sudo apt-get install medibuntu-keyring && sudo apt-get install w64codecs libdvdcss2";
my $i386="sudo apt-get  upgrade && sudo apt-get install medibuntu-keyring && sudo apt-get install w32codecs libdvdcss2";
########################################################################################################################
print " this script installs the media codecs for ubuntu hardy \n";
print " are your computer amd 64 or i386 \ntype [amd64] or [i386] \n";
while($userinput = <stdin>)
{
chomp $userinput;
if($userinput eq "amd64")
{
 exec($amd64);
}
if($userinput eq "i386")
{
  exec($i386);
}else{
	print "usage: installs media codecs for ubuntu hardy\n";
	print "this application expects typed in [amd64] or [i386]\n"; 
	print "invalid input recieved \ntype exit to quit or choose computer type to continue \n ";
	
  }
}
exec("sudo apt-get upgrade");

print "done installing the media  codecs for ubuntu hardy \n";[/PHP]

thanks for reading this.

---

### Post by ghostdog74 on 2008-09-21
is there a must for writing it in Perl?
it seems to me you are calling apt-get from inside Perl. Why not just call them from the shell?
```

#/bin/bash
choice=$1
sudo apt-get  upgrade 
sudo apt-get install medibuntu-keyring 
case $choice in
 amd64 ) 
      sudo apt-get install w64codecs libdvdcss2
 i386 ) 
      sudo apt-get install w32codecs libdvdcss2"
esac

```

---

### Post by cmay on 2008-09-21
thanks 
i have no reason to use perl other than i want to learn perl and write something i can use as i learn. but i would be very happy if i can borrow the snippet you provided. i do not see that well so i do not like to install tings from command line. i use synaptic instead. but if i can save some mistyping by doing one simple script i ,can maybe use again then i will try write it. i am just not so used to shell scripting and i find bash a bit hard to learn for some reason. 
thanks for the answer.

---

### Post by pp. on 2008-09-21
I don't know if you realise this, but your posts are very hard to understand. If you tried to write in real English, I would not have to try so hard to understand what you are trying to say, and I possibly could think of anything to say which might be useful to you.

---

### Post by Martje_001 on 2008-09-21
> **pp. said:**
> I don't know if you realise this, but your posts are very hard to understand. If you tried to write in real English, I would not have to try so hard to understand what you are trying to say, and I possibly could think of anything to say which might be useful to you.
I disagree..

BASH is much easier to learn than Perl. And I would learn Python instead of perl if I were you.

---

### Post by monkeyking on 2008-09-21
> **pp. said:**
> I don't know if you realise this, but your posts are very hard to understand. If you tried to write in real English, I would not have to try so hard to understand what you are trying to say, and I possibly could think of anything to say which might be useful to you.
I understand his post, but I don't understand yours...

To the original poster,
you should use a shell script for anything that you would normally do at the commandline.

I do perl programming once in a while,
but only for text parsing.

good luck

---

### Post by slavik on 2008-09-21
> **cmay said:**
> hi.
i was trying to write a simple perl script to install the media codecs in ubuntu hardy. i have both amd64 and i386 type pc so i thought i would try to write this as a perl script. i have no experience none what so ever with perl . my question is how is the task of installing  these codecs best done. there must be a better way of doing it than this. 

[PHP]#!/usr/bin/perl 
#cmay 2008: should install the restrictive media codecs 
my $userinput;
my $amd64="sudo apt-get upgrade && sudo apt-get install medibuntu-keyring && sudo apt-get install w64codecs libdvdcss2";
my $i386="sudo apt-get  upgrade && sudo apt-get install medibuntu-keyring && sudo apt-get install w32codecs libdvdcss2";
########################################################################################################################
print " this script installs the media codecs for ubuntu hardy \n";
print " are your computer amd 64 or i386 \ntype [amd64] or [i386] \n";
while($userinput = <stdin>)
{
chomp $userinput;
if($userinput eq "amd64")
{
 exec($amd64);
}
if($userinput eq "i386")
{
  exec($i386);
}else{
	print "usage: installs media codecs for ubuntu hardy\n";
	print "this application expects typed in [amd64] or [i386]\n"; 
	print "invalid input recieved \ntype exit to quit or choose computer type to continue \n ";
	
  }
}
exec("sudo apt-get upgrade");

print "done installing the media  codecs for ubuntu hardy \n";[/PHP]

thanks for reading this.

There are several mistakes in your script.
1. exec() does not work the way you think it works. if exec() is successful it never returns.

2. Why ask the user for input? You can find out the architecture and the Ubuntu release directly

Here's a better version (There are other mistakes here most likely ... I don't know what uname -m on a 32bit system outputs):
[php]#!/usr/bin/perl 
#cmay 2008: should install the restrictive media codecs 
my $arch = `uname -m`;
my $hardy = `cat /etc/lsb-release | grep hardy`;
my $x86_64="apt-get install -y medibuntu-keyring w64codecs libdvdcss2";
my $i386="apt-get install -y medibuntu-keyring w32codecs libdvdcss2";

print "This script installs the media codecs for Ubuntu Hardy Heron\n";
if ($hardy eq "") {
  print "Ubuntu Hardy Heron not detected. Exiting ...\n";
  die;
}
else {
  print "Ubuntu Hardy Heron detected. Continuing ...\n";
  if($arch eq "x86_64") {
   print "64bit architecture detected.\n";
   `$x86_64`;
  }
  elsif($arch eq "i386") {
   print "32bit architecture detected.\n";
    `$i386`;
  }else{
     print "Unknown architecture detected. Exiting ...\n";
     die;
  }

  print "Done installing the media  codecs for Ubuntu Hardy Heron\n";
}
[/php]

---

### Post by cmay on 2008-09-22
> There are several mistakes in your script.
1. exec() does not work the way you think it works. if exec() is successful it never returns.

2. Why ask the user for input? You can find out the architecture and the Ubuntu release directly

Here's a better version (There are other mistakes here most likely ... I don't know what uname -m on a 32bit system outputs):
thank you  very much.
i was puzzled by it since it would work in c. i did write it in c first actually.

i have tried writing small scripts to customize my ubuntu since i have poor vision at times. so when i have these periods when i i cant see that well i do not like to use the commandline so much. which is why i choose perl over python since i cant see well enough to use the languages where white space is part of the syntaxt. so it is a perl script i have written for practical reasons just as is i have small bash script to install the programs i always install when i am on a fresh ubuntu installation. i have more than one computer an i test run beta distros sometime so i also reinstall many times more often than others do. it would make my life more easy to do certain things i have to do anyway with scripting i guess.
thanks for the input

---

