---
title: "MP3 Search Perl- Problem dealing with spaces"
date: 2010-05-14
forum: Programming Talk
---

### Post by Holmes89 on 2010-05-14
I'm trying to make a script that will go through my music folder and subfolders and get an accurate account of my music. I'm having problems dealing with spaces within directories. This seems like a simple problem but I can't seem to figure it out, could anyone help? Below is my code. Thanks in advance!
```

#!/usr/bin/perl -w                                                                          

use LWP::Simple;
use DBI();


#@files = <~/Music/*>;                                                                      
$path='~/Music/';
open (MUSICFILE, '>music.dat');
file_rec($path);
close(MUSICFILE);

sub file_rec{
    my $new_path=$_[0];
    my @new_files=glob($new_path.'*');
    foreach $file (@new_files){
        print("$file\n");
        if(-d $file){
            file_rec($file.'\/');
        }
        else{
            $file=~m/(.*)\.[mp3|m4a]/;
            if($1){
                print MUSICFILE "$1\n" ;
            }
        }
    }
}

```

---

### Post by gmargo on 2010-05-14
**glob** splits on whitespace.  **bsd_glob** does not split on whitespace.

Modify your code to add
```

use File::Glob ':glob';

```and use "bsd_glob" in place of "glob".

One other thing:  ALWAYS write perl code using:
```

use strict;
use warnings;

```These will always save you pain.

---

### Post by Holmes89 on 2010-05-14
Thank you very much! There is so much to learn with Perl but thanks to people like you it's been pretty easy picking up!

---

