---
title: "perl File::Find not recursive"
date: 2010-04-17
forum: Programming Talk
---

### Post by Xender1 on 2010-04-17
I am using File::Find to get all the files from a certain directory. By default File::Find is recursive and will enter each subdirectory. Reading perldoc i found the no_chdir can make it not recursive yet it still is being recursive for me. here is what i have:
```

#!/usr/bin/env perl
use warnings;
use strict;
use File::Find;

$File::Find::no_chdir = 0;

my $dir = '/home/username/Documents';

find (\&search, $dir);

sub search {
	if (-f $_) {
		print "$File::Find::name ";
        }
}

```

anyone see why or is there another way to do this that is simpler?

---

### Post by Cracauer on 2010-04-17
I got into a habit of calling

popen("gfind ...", "rb");

in pretty much any language and on any OS, including those that have the fts library.  And I always use GNU find for this. My life is too short to figure out how to control some random filesystem traversal library, and just as you sometimes that only ends with you saying what you want and it still not doing it. Is it a bug? Who knows.

The target of that popen might be code doing stuff on file directly, or it might go into a hashtable or list if I want to use language facilities to further filter the collection. Just don't forget to check error codes and if you have a GUI thing capture stderr and display it to the user.

Not answering your question, I know, just my two cents.

---

### Post by gmargo on 2010-04-17
You have misinterpreted the function of **no_chdir**.  If no_chdir is set, then the function does not alter the current working directory during the traversal.  Recursion is not affected, and there is no option similar to **find(1)**'s -maxdepth option.

The only way I can see to easily do what you want is to use the 'preprocess' option to remove directories from the list.

```

#!/usr/bin/env perl
use warnings;
use strict;
use File::Find;
      
my $dir = "$ENV{HOME}/Documents";

find ({ wanted     => \&search,
        preprocess => \&filter_dirs,
      }, $dir);

sub search {
        if (-f $_) {
                print "$File::Find::name  ";
        }
}         

sub filter_dirs
{
    my @inlist = @_;
    my @outlist;

    foreach (@inlist)
    {
        push @outlist, $_ if ! -d $_;
    }
    return @outlist;
}

```

---

### Post by shawnhcorey on 2010-04-18
if you want to list the files in a single directory, use glob() instead:

```
#!/usr/bin/perl

use strict;
use warnings;

for my $dir ( @ARGV ){
  my @files = grep { ! -d } glob "$dir/*";
  print "files in $dir:\n";
  print "\t$_\n" for @files;
}

```

---

### Post by Xender1 on 2010-04-18
is there a way to use glob so that instead of the full path name it is relative to the directory its searching? so for example /home/username/Documents is what we search, and the files returns as file1.txt file2.txt as opposed to /home/username/Documents/file1.txt etc...?

---

### Post by gmargo on 2010-04-18
You can use basename() (see **File::Basename** man page) to separate the filename from the directory name.

---

### Post by shawnhcorey on 2010-04-18
> **Xender1 said:**
> is there a way to use glob so that instead of the full path name it is relative to the directory its searching? so for example /home/username/Documents is what we search, and the files returns as file1.txt file2.txt as opposed to /home/username/Documents/file1.txt etc...?

You can use chdir to change to each directory:
```
#!/usr/bin/perl

use strict;
use warnings;

use Cwd;
my $save_cwd = cwd();

for my $dir ( @ARGV ){
  chdir $dir or ( warn "could not change to $dir: $!\n" and next );
  my @files = grep { ! -d } glob '*';
  print "files in $dir:\n";
  print "\t$_\n" for @files;
}
chdir $save_cwd;

```

---

