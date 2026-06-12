---
title: "Problem regarding use of &quot;ls&quot; in perl script"
date: 2010-07-05
forum: Programming Talk
---

### Post by QaRahul on 2010-07-05
Hello,
  I am trying to write a script to search for a file type pattern in a directory using PERL script and I do have some questions. First lets take a look at the code :
```

sub GetFileList
{
    my $type = shift @_;
    my $dir  = shift @_;    //complete path    
    
    print "LOG:: Switching Directory to $dir\n";
    
    $type = "*.$type";
    print "LOG:: Search for file type : $type \n";
    
    chdir ($dir);
    my @files = qx(ls $type 2>&1);
    
    return @files;
}

```

I have following question:

The above function works fine in case there are already existing files with the pattern. For ex, if I look for a file type txt, and it is there in the folder it returns the file. But suppose that I seach for cfg file and it is not there in directory I get a file named "ls: cannot access *.cfg: No such file or directory" in the directory and it returns me nothing.

Please help.

---

### Post by Some Penguin on 2010-07-05
As is usual in Perl, TMTOWTDI.  And in this case, there are multiple built-in ways of doing it, so I don't recommend a method which involves firing up a shell process which in turn fires up an 'ls' process.

The simpler option is to use globs.

```

my @fileNameList = <*.$type>;

```provided that you have previously verified that $type is sane.  In your case, this is probably all you need.

A more flexible way (e.g. if you wanted to use regexes for case-insensitivity) would look something like

```

use Symbol;

my $dir_fh = gensym();
opendir($dir_fh, $dir_name);
my @file_entries = readdir $dir_fh;
closedir($dir_fh);

for my $file_entry (@file_entries) {
  if ((-f "$dir_name/$file_entry") && ($file_entry =~ /\Q$suffix\E$/i)) {
    # -f:  normal file, not directory, not symlink
    # \Q, \E:  quote, so $suffix = 'blah.blah' is fine; the period will be quoted
    # and will only match periods, not any character
    # /i means case-insensitive
    #
    # could also do this using grep, rather than a for loop
    # $dir_name/$file_entry because readdir gives relative results
  }
}

```

---

### Post by QaRahul on 2010-07-15
Thanx [Some Penguin]("http://ubuntuforums.org/member.php?u=963358").

---

