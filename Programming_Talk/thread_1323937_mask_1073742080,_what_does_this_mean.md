---
title: "mask 1073742080, what does this mean ?"
date: 2009-11-12
forum: Programming Talk
---

### Post by iMisspell on 2009-11-12
Im trying to make a little perl script to watch a folder (with the code posted below).
One of the hash keys is 'mask'.
When a new folder is created, the 'mask' is 1073742080, what does that mean ?

I can get the code to do what i want, but would like to know why :)

In the end the newly created folder name will be sent to another script to do some work with it. Thats the reason for the "if check". With out that check the the 'events' is called acouple times which will not wot for me. When the events are called additional times, the 'name' key is cleared and the 'mask' numbers change.  Through a few tests, it seams that 'mask 1073742080' is always first and the new folder name is also.
Aside from wanting to know whats going on with this, id also like to know if the mask number's  1073742080 are going to be a constant.

Thanks for any help, explanation or insight.

```


#!/usr/bin/perl -w
use strict; use warnings; use diagnostics;

use Linux::Inotify2;

my $watch_folder = '/home/xx/Desktop/test';
my $inotify = new Linux::Inotify2();
$inotify->watch($watch_folder, IN_ALL_EVENTS);

while (1)
{
  # By default this will block until something is read
  my @events = $inotify->read();
  if (scalar(@events)==0)
  {
    print "read error: $!";
    last;
  }
  
  foreach (@events) {
	  
	  my $name = $_->name;
	  my $mask = $_->mask;
	  
	  if($mask eq '1073742080'){
		  print "** $name  **\n" ;
	  }
	  
	  last;
	  
	  for my $mInfo ( $_ ) {
			for my $key ( keys %$mInfo ) {
				print "$key - $mInfo->{$key} \n" ;
			}
	  }

  }
  
}


```

---

### Post by Arndt on 2009-11-12
> **iMisspell said:**
> Im trying to make a little perl script to watch a folder (with the code posted below).
One of the hash keys is 'mask'.
When a new folder is created, the 'mask' is 1073742080, what does that mean ?

I can get the code to do what i want, but would like to know why :)

In the end the newly created folder name will be sent to another script to do some work with it. Thats the reason for the "if check". With out that check the the 'events' is called acouple times which will not wot for me. When the events are called additional times, the 'name' key is cleared and the 'mask' numbers change.  Through a few tests, it seams that 'mask 1073742080' is always first and the new folder name is also.
Aside from wanting to know whats going on with this, id also like to know if the mask number's  1073742080 are going to be a constant.

Thanks for any help, explanation or insight.

```


#!/usr/bin/perl -w
use strict; use warnings; use diagnostics;

use Linux::Inotify2;

my $watch_folder = '/home/xx/Desktop/test';
my $inotify = new Linux::Inotify2();
$inotify->watch($watch_folder, IN_ALL_EVENTS);

while (1)
{
  # By default this will block until something is read
  my @events = $inotify->read();
  if (scalar(@events)==0)
  {
    print "read error: $!";
    last;
  }
  
  foreach (@events) {
	  
	  my $name = $_->name;
	  my $mask = $_->mask;
	  
	  if($mask eq '1073742080'){
		  print "** $name  **\n" ;
	  }
	  
	  last;
	  
	  for my $mInfo ( $_ ) {
			for my $key ( keys %$mInfo ) {
				print "$key - $mInfo->{$key} \n" ;
			}
	  }

  }
  
}


```

[http://search.cpan.org/dist/Linux-Inotify2/Inotify2.pm](http://search.cpan.org/dist/Linux-Inotify2/Inotify2.pm) seems to describe it well. In your case, the mask contains 'create' and 'directory'.

Maybe the man page for "inotify" will help, too.

---

### Post by dwhitney67 on 2009-11-12
Refer to the man-page for inotify.  You will see a discussion of the 'mask', which is built up using one or more predefined values.

The value in your post, 1073742080 is in decimal; it's hex equivalent is 0x40000100.

If you look in /usr/include/sys/inotify.h, the mask parameters are listed.  Your value corresponds to IN_CREATE or-ed with IN_ISDIR.

Presumably Perl has access to these constants or something similar, that you can use to programatically determine what the mask means.

---

### Post by iMisspell on 2009-11-12
Thanks for the link, Arndt; it will be a big help.
Being new to perl, i keep forgetting about the cpan site full of documentation :(

IN_CREATE
$inotify->watch($watch_folder, IN_CREATE);

worked well.

---

### Post by iMisspell on 2009-11-12
> **dwhitney67 said:**
> Refer to the man-page for inotify.  You will see a discussion of the 'mask', which is built up using one or more predefined values.

The value in your post, 1073742080 is in decimal; it's hex equivalent is 0x40000100.

If you look in /usr/include/sys/inotify.h, the mask parameters are listed.  Your value corresponds to IN_CREATE or-ed with IN_ISDIR.

Presumably Perl has access to these constants or something similar, that you can use to programatically determine what the mask means.

Great, thanks for the info.

_

---

