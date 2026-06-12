---
title: "Perl: CPAN module to delete file based on string."
date: 2007-04-30
forum: Programming Talk
---

### Post by divisionbyzero on 2007-04-30
Hello everyone,

I'm looking for a CPAN module that lets me delete a file based on some unique id that is part of the file name. Example: if the unique id is "1234abc", this module would let me delete a file named "20070430-1234abc.wav".

Also, I have about a thousand unique ids that I've stored in a Perl array and this module would loop through each unique id and delete that file in the filesystem if that file contains the unique id.

Can anyone recommend what they're using for this type of operation?

Thanks in advance.

---

### Post by tr333 on 2007-05-05
i don't know of any CPAN modules that will do this for you, but this can be done quite easily with regular perl:

```

# @uniqueids is the array containing the unique id for each file to be deleted
my $directory = "."; # current directoty
my @filenames = <$directory/*>; # get a list of all files in the specified directory
foreach my $filename (@filenames) {
    foreach my $id (@uniqueids) {
        if ($filename =~ /$id/) {
            unlink $filename;
        }
    }
}

```

---

