---
title: "Perl folder rename script help"
date: 2010-09-14
forum: Programming Talk
---

### Post by Ralphie on 2010-09-14
I edited a rename script to make all capital letters into lowercase letters recursively on files.
Now I need to do the same to folders, can anyone help?

```

 #!/usr/bin/perl

 use warnings;
 use strict;

 use File::Find;
 find(\&capz, ".");

 sub capz {
    next if -d $_;
    next if /^\./;
    next unless /[A-Z]/;

    my $new_name = $_;
    $new_name    =~ tr/A-Z/a-z/;
    chdir($File::Find::dir);
    rename($_, $new_name) or die $!;
 }

```

Thanks!

---

### Post by myrtle1908 on 2010-09-15
You are skipping directories with this line

```
next if -d $_;
```

Comment it out.

---

### Post by Some Penguin on 2010-09-15
Two notes:

(1) As written, this script would skip a file or directory called "startsWithALowerCaseLetter".

(2) Not clear what you want to happen should there be files called "Abba" and "ABBA" in the same directory... or "Abba" and "abba", for that matter.

---

### Post by Ralphie on 2010-09-15
@myrtle1908
Just did that and I am a step closer, thank you!
But this is only working on empty folders at the moment. 
Any ideas? 

@Some Penguin
For my personal purposes I know that same names wont happen, and all files that I want changed will not start with a lowercase letter. But thank you for noting those two things for anyone who might be trying to use a similar script.

---

### Post by kurum! on 2010-09-15
```

ruby -e 'Dir["**/*[A-Z]*"].each{ |d| File.file?(d) && File.rename(d, d.downcase)}'

```

---

### Post by shawnhcorey on 2010-09-15
Try:

```
 sub capz {
    return if /^\./;
    return unless /[[:upper:]]/;

    rename($_, lc( $_ )) or die $!;
 }
```

The sub find() will change directories automatically unless you tell it otherwise.  See `perldoc File::Find`.

The POSIX pattern [[:upper:]] matches any uppercase letter in any language.  See `perldoc perlre` and `perldoc POSIX` and search for /\[\[\:upper\:\]\]/.

The sub lc() will only change uppercase letters.  See `perldoc -f lc`.

---

### Post by Ralphie on 2010-09-15
Thanks to everyone for your input and help, also for the ruby script, kurum.
I've definitely learned a few things!

---

