---
title: "using bash to make a list of movie files with mediainfo"
date: 2014-02-04
forum: Programming Talk
---

### Post by rioguia2 on 2014-02-04
I have a directory of moviesI (avi). 

I would like to make a list of the movies using media info.

Each line on the list should contain one movie on a line with the "Complete name" and 'Mastered date" 

Ultimately, I would like the list to be sorted by the "Mastered date"

I have tried to write a bash script but have run into some issues.

First, the output looks like below.  It provides the absolute file name and I was want "20080706MVI_0011.AVI". 
Second, it provides the date from the lines between Complete name and Mastered date and I want it to ignore that information.
My bash script follows below.


```
item: /media/MY_BOOK/avi/20080706MVI_0011.AVI: /media/MY_BOOK/avi/20080706MVI_0011.AVI: AVI
Audio Video Interleave: 2.25 MiB
19s 133ms: 988 Kbps
SUN JUL 06 08:59:34 2008
item: /media/MY_BOOK/avi/20080706MVI_0012.AVI: /media/MY_BOOK/avi/20080706MVI_0012.AVI: AVI
Audio Video Interleave: 3.67 MiB
32s 0ms: 962 Kbps
SUN JUL 06 09:00:10 2008
item: /media/MY_BOOK/avi/20080706MVI_0013.AVI: /media/MY_BOOK/avi/20080706MVI_00]
```

```
#!/bin/sh

#
#Just a script to print a list of movied by Complete name and Mastered date
#

for i in /media/MY_BOOK/avi/* ; do
    printf 'item: %s: ' "$i"
    mediainfo "$i" | sed -e '/Complete name/,/Mastered date/{s/.*: //p;};d' | sed -e '$!N;s/\n/: /'
done
```

---

### Post by varunendra on 2014-02-06
> **rioguia2 said:**
> First, the output looks like below.  It provides the absolute file name and I was want "20080706MVI_0011.AVI".

How about showing us the example of How you'd like it to be? In the meanwhile, how about this -
```
#!/bin/bash
find /media/MY_BOOK/avi/ -type f -iname "*.avi" -printf 'Item : %-20.20f : %-80.80p\n' -exec mediainfo -f "{}" \; -printf '\n' | egrep 'Item|Mastered date' | sed '/$/ {N; s/\n.*: /: /}'
```

I'm sure there should be a much easier and faster code for doing this, above one just works for me.

Also, you may replace %-20.20f and %-80.80p with just %f and %p. The -20.20f makes sure the field width is exactly 20 characters, any output string longer than this would be trimmed to fit in, thus maintaining the formatting. Same for -80.80p.

---

### Post by rioguia2 on 2014-02-12
Thanks.  When i ran this, i got the following output.  I'm thinking that some basename or other bash trick is necessary.

```
Item : film.avi             : /home/dir/export/film.avi                                                       : /home/dir/export/MVI_3942.AVI]
```


I've been reading about RSYNC (which is where i hope to put the generated list to work).  During that time, I found an [explanation of generating ]("http://stackoverflow.com/questions/5456120/how-to-get-file-only-file-name-with-linux-find")a list (How to get file only file name with linux `find`) such that the files are stripped of their directory information.   A list formatted like this is [necessary to pass a list to rsync]("http://unix.stackexchange.com/questions/11163/rsync-not-using-files-from-option") (using " --files-from") to generate a comprehensive collection of movies scattered over my computer.

```
find . -type f -iname '*.avi' -printf "%f\n" > /home/dir/avi_list.txt 
```

The output looks like this:
```
DV00002.avi
MVI_4028.AVI
```

I'm still interested in using the metadata to do the search but i have obviusly got a lot to learn.

---

### Post by varunendra on 2014-02-12
So did you get what you wanted?

If not, please manually type a few example lines (or list) to show us what kind of result you want.

I'm not a bash expert, but we have a few scripting magicians here who may be able to suggest fast and simple solutions.

---

### Post by cariboo on 2014-02-13
Moved to Programming Talk

---

### Post by Vaphell on 2014-02-13
in what way you want to use the metadata to search?
also example of mediainfo output for your .avi files would be nice, i tried running it on few files and they lacked the 'mastered date' field.

---

### Post by drmrgd on 2014-02-13
This is not in bash, but since we're having a snow day today and I'm a bit bored - plus this seemed like a fun excersise - I wrote a perl script to do what you want.  The script will read in a list of avi movies and use the 'mediainfo' program to read the movie metadata into a hash.  Then the metadata is printed out in a tab delimited table containing a sorted list of movie titles and 'Mastered date' fields.  You can go to a directory containing your movies and run the script like so:

```

./media_catalog.pl *.avi #assuming you want to process all avi's in the current directory

```

For the few I had lying around, I get this:

```

$ ./media_catalog.pl *.avi
Movie   Mastered Date
MVI_0181        Sun Apr 17 01:25:06 2005
MVI_0183        Sun Apr 17 01:29:20 2005
MVI_0184        Sun Apr 17 01:29:58 2005
MVI_0185        Sun Apr 17 01:30:32 2005
Packing Day 001 Sun Apr 17 01:30:32 2005

```

I thought it might be handy to do this in perl as you'll now have a hashed data structure that you can use to print out other fields besides 'Mastered date' if you choose.  Line 92 of the program specifically creates the new hash with the movie title and Mastered date info.  We can expand that hash to contain more information if you want, and then just change how it's printed in the next code block.

Hope you find this somewhat helpful.

```

#!/usr/bin/perl
# media_catalog.pl
# Using the mediainfo program, read in a list of movies and generate an output table of
# sorted movie titles and mastered dates.
#
# For now just print out the Mastered Date field.  Can add command line options to add 
# additional metadata as needed.
#
# 2/13/2014
###########################################################################################


use warnings;
use strict;
use Getopt::Long;
use File::Basename;
use Data::Dumper;


( my $scriptname = $0 ) =~ s/^(.*\/)+//;
my $version = "v1.0.0";
my $description = <<"EOT";
Using the mediainfo program, read in a list of movies and generate an output table of sorted
movie titles and matered dates.  The mediainfo metadata is stored in a hash that can be used
to print out other movie inforamtion depending on what is required.
EOT


my $usage = <<"EOT";
USAGE: $scriptname [options] <input_file>
    -o, --output    Send output to custom file.  Default is STDOUT.
    -v, --version   Version information
    -h, --help      Print this help information
EOT


my $help;
my $ver_info;
my $outfile;


GetOptions( "output=s"    => \$outfile,
            "version"     => \$ver_info,
            "help"        => \$help )
        or print $usage;


sub help {
        printf "%s - %s\n\n%s\n\n%s\n", $scriptname, $version, $description, $usage;
        exit;
}


sub version {
        printf "%s - %s\n", $scriptname, $version;
        exit;
}


help if $help;
version if $ver_info;


# Make sure enough args passed to script
if ( scalar( @ARGV ) < 1 ) {
    print "ERROR: Not enough arguments passed to script!\n\n";
    print "$usage\n";
    exit 1;
}


# Write output to either indicated file or STDOUT
my $out_fh;
if ( $outfile ) {
        open( $out_fh, ">", $outfile ) || die "Can't open the output file '$outfile' for writing: $!";
} else {
        $out_fh = \*STDOUT;
}


#########------------------------------ END ARG Parsing ---------------------------------#########


my @files = @ARGV;
my (%metadata, %results);
my @sections;
my @headers = qw{ General Video Audio };


for my $file ( @files ) {
    (my $movie_title = basename($file) ) =~ s/\.avi//; 


    # Read in the metadata from the 'mediainfo' program
    open( my $mi_data, "mediainfo $file |" ) || die "Can't open the stream: $!";


    {
        local $/ = '';
        @sections = map { s/(General|Video|Audio)\n//; $_ } <$mi_data>;
    }


    # Store all of the metadata collected into a hash
    for my $i ( 0..$#sections ) {
        my @data = split( /\n/, $sections[$i] );
        $metadata{$headers[$i]} = {map { split( /\s+: /, $_ ) } @data}; 
    }
    $results{$movie_title} = $metadata{'General'}->{'Mastered date'};
}


# Print out a nice display of the data
print $out_fh "Movie\tMastered Date\n";
for my $title ( sort keys %results ) {
    print $out_fh "$title\t$results{$title}\n";
}

```

---

### Post by rioguia2 on 2014-02-16
Wow!  Thanks for all the responses.

Regarding the perl script, it worked great.
I copied the script into folder containing .AVI's. and made it executable (chmod +).  

I called the script like this:
```
perl media_catalog.pl -o media_catalog_output.txt *.AVI_
```

I got the following:

```

MVI_0003.AVI    TUE JUL 12 18:52:44 2011
MVI_0024.AVI    THU NOV 11 12:32:40 2010
MVI_0025.AVI    THU NOV 11 12:33:35 2010
MVI_0048.AVI    THU NOV 11 13:09:46 2010
MVI_0049.AVI    THU NOV 11 13:10:32 2010
MVI_0088.AVI    SAT NOV 20 12:07:46 2010
MVI_0090.AVI    THU AUG 25 19:44:23 2011
MVI_0091.AVI    FRI AUG 26 07:26:22 2011

```

I really appreciate you sharing your expertise.  I thought it would be great to be sorted by date so I piped it through sort [based on a suggestion]("http://javarevisited.blogspot.com/2011/08/unix-sort-command-example-tutorial.html") like this:
```
perl media_catalog.pl *.AVI | sort -nk6 > media_catalog_output.txt
```

and got it to look like this:

```
DSCN0285.AVI
Movie   Mastered Date
MVI_0467.AVI    Fri Sep 12 07:01:45 2003
MVI_1876.AVI    Tue Apr 20 20:44:59 2004
MVI_1877.AVI    Tue Apr 20 20:48:10 2004
MVI_1881.AVI    Wed Apr 21 19:20:09 2004
MVI_1902.AVI    Sat Apr 24 13:09:54 2004
MVI_3416.AVI    Sat Feb 05 09:51:27 2005

```  

Note: that your perl script helpfully recorded AVI files that didn't have the metadata (at the top of this list) so that i can just add that later.

I really appreciate your work and having seen what this can do, I wonder if it would be difficult to rename the files in YYYY_MM_DD_hh_mm_ss or to allow it to recurse through a directory tree?

I also like the way it was easy to take the output and pipe it.  Maybe leaving the perl script as it is (simple and flexible) and then just do the renaming through bash.

---

### Post by varunendra on 2014-02-17
If you are happy with the answers and have no more questions, please consider marking the thread as [SOLVED] using the "Thread Tools" link above the top post. It helps others as well by indicating that the thread contains something that works for the topic. Thanks ! :)

---

### Post by Vaphell on 2014-02-17
> I wonder if it would be difficult to rename the files in YYYY_MM_DD_hh_mm_ss or to allow it to recurse through a directory tree?

what do you mean by that because that sentence is not exactly clear?

---

### Post by drmrgd on 2014-02-17
First, to sort by date is relatively easy enough to do within the script.  I modified the original, adding a new command line option and new subroutine to sort the output data.  By using the '-s' option followed by either 'date' or 'title' you can sort the output on either of the two fields.  Using the metadata from your post above as an example:

```

$ ./media_catalog.pl -s title *.avi 
Movie           Mastered Date
MVI_0003.AVI    TUE JUL 12 18:52:44 2011
MVI_0024.AVI    THU NOV 11 12:32:40 2010
MVI_0025.AVI    THU NOV 11 12:33:35 2010
MVI_0048.AVI    THU NOV 11 13:09:46 2010
MVI_0049.AVI    THU NOV 11 13:10:32 2010
MVI_0088.AVI    SAT NOV 20 12:07:46 2010
MVI_0090.AVI    THU AUG 25 19:44:23 2011
MVI_0091.AVI    FRI AUG 26 07:26:22 2011
no data

$ ./media_catalog.pl -s date *.avi 
Movie           Mastered Date
no data
MVI_0024.AVI    THU NOV 11 12:32:40 2010
MVI_0025.AVI    THU NOV 11 12:33:35 2010
MVI_0048.AVI    THU NOV 11 13:09:46 2010
MVI_0049.AVI    THU NOV 11 13:10:32 2010
MVI_0088.AVI    SAT NOV 20 12:07:46 2010
MVI_0003.AVI    TUE JUL 12 18:52:44 2011
MVI_0090.AVI    THU AUG 25 19:44:23 2011
MVI_0091.AVI    FRI AUG 26 07:26:22 2011


```

Two things to note:

The 'no data' entry is an attempt to simulate a movie for which there is no Mastered Date metadata.  It seems to sort as expected in the above two examples, but without real test cases, it may not always work as expected.  Hard to predict all use cases :)

In order to always (I hope) properly sort by title, I decided to use the perl module "Sort::Naturally", which I can't remember whether or not is part of the core perl modules.  If you don't have it installed on your system, you may get an error along the lines of 
> 
Can't locate Sort/Naturally.pm in @INC (@INC contains: /etc/perl...


It's easy enough to install the perl module using CPAN (run 'cpan -i Sort::Naturally' and follow the prompts), or I can bail on that module and go back to the original sort method, which may or may not work depending on how titles are written (complex strings with letters and numbers need a bit more effort to sort).

Second, as with Vaphell, I'm not quite sure what you are suggesting you'd like to do next with the files.  I could probably make the input for the script be directories instead of files fairly easily and then attempt to add directory recursion without knowing the directory structure you have.  It'll be a bit of a guess on my part to get it right, though.  

We could also rename the files if you want, but I'm not quite sure I understand the naming scheme you want (maybe write an example), and this starts to get a bit big and complex.  If I understand better what you're after and I have time, I can try to hack something together.  

Anyway, here is the latest version with an improved sort routine.  Hope it helps!

```

#!/usr/bin/perl
# Using the mediainfo program, read in a list of movies and generate an output table of
# sorted movie titles and mastered dates.
#
# For now just print out the Mastered Date field.  Can add command line options to add 
# additional metadata as needed.
#
# 2/17/2014 - v1.5.0   Added sort routine and command line option to sort on either title
#                      or date field.
#
# 2/13/2014
###########################################################################################


use warnings;
use strict;
use Getopt::Long;
use File::Basename;
use Data::Dumper;


( my $scriptname = $0 ) =~ s/^(.*\/)+//;
my $version = "v1.0.0";
my $description = <<"EOT";
Using the mediainfo program, read in a list of movies and generate an output table of sorted
movie titles and matered dates.  The mediainfo metadata is stored in a hash that can be used
to print out other movie inforamtion depending on what is required.
EOT


my $usage = <<"EOT";
USAGE: $scriptname [options] <input_file>
    -o, --output    Send output to custom file.  Default is STDOUT
    -s, --sort      Field to sort the output data on (default is 'title'.  Options are 'title' or 'date'
    -v, --version   Version information
    -h, --help      Print this help information
EOT


my $help;
my $ver_info;
my $outfile;
my $sort_field = 'title';


GetOptions( "output=s"    => \$outfile,
            "version"     => \$ver_info,
            "sort=s"      => \$sort_field,
            "help"        => \$help )
        or print $usage;


sub help {
        printf "%s - %s\n\n%s\n\n%s\n", $scriptname, $version, $description, $usage;
        exit;
}


sub version {
        printf "%s - %s\n", $scriptname, $version;
        exit;
}


help if $help;
version if $ver_info;


# Make sure enough args passed to script
if ( scalar( @ARGV ) < 1 ) {
    print "ERROR: Not enough arguments passed to script!\n\n";
    print "$usage\n";
    exit 1;
}


# Write output to either indicated file or STDOUT
my $out_fh;
if ( $outfile ) {
        open( $out_fh, ">", $outfile ) || die "Can't open the output file '$outfile' for writing: $!";
} else {
        $out_fh = \*STDOUT;
}


#########------------------------------ END ARG Parsing ---------------------------------#########
my %test_hash = ( 
    "MVI_0049.AVI" =>  "THU NOV 11 13:10:32 2010", 
    "MVI_0003.AVI" =>  "TUE JUL 12 18:52:44 2011",
    "MVI_0024.AVI" =>  "THU NOV 11 12:32:40 2010",
    "MVI_0025.AVI" =>  "THU NOV 11 12:33:35 2010",
    "MVI_0088.AVI" =>  "SAT NOV 20 12:07:46 2010",
    "MVI_0090.AVI" =>  "THU AUG 25 19:44:23 2011",
    "MVI_0091.AVI" =>  "FRI AUG 26 07:26:22 2011",
    "MVI_0048.AVI" =>  "THU NOV 11 13:09:46 2010",
    "no data"      =>  "",
);


#print Dumper( \%test_hash );
#exit;


my @files = @ARGV;
my (%metadata, %results);
my @sections;
my @headers = qw{ General Video Audio };


for my $file ( @files ) {
    (my $movie_title = basename($file) ) =~ s/\.avi//; 


    # Read in the metadata from the 'mediainfo' program
    open( my $mi_data, "mediainfo $file |" ) || die "Can't open the stream: $!";


    {
        local $/ = '';
        @sections = map { s/(General|Video|Audio)\n//; $_ } <$mi_data>;
    }


    # Store all of the metadata collected into a hash
    for my $i ( 0..$#sections ) {
        my @data = split( /\n/, $sections[$i] );
        $metadata{$headers[$i]} = {map { split( /\s+: /, $_ ) } @data}; 
    }
    $results{$movie_title} = $metadata{'General'}->{'Mastered date'};
}


print $out_fh "Movie\t\tMastered Date\n";
#sort_output( \$sort_field, \%test_hash );
sort_output( \$sort_field, \%results );


sub sort_output {
    # Sort the metadate on either the title or Mastered date field
    use Time::Piece;
    use Sort::Naturally;


    my $field = shift;
    my $data = shift;


    my %sorted_data;


    if ( $$field =~ /title/i ) {
        print $out_fh "$_\t$$data{$_}\n" for ( nsort( keys %$data ) );
    }
    elsif( $$field =~ /date/i ) {
        #print "we'll sort on a date\n";
        print $out_fh "$_\t$$data{$_}\n" for ( sort {
            Time::Piece->strptime( $$data{$a}, '%cdate' ) <=> Time::Piece->strptime( $$data{$b}, '%cdate' )
            } keys %$data );
    }
    else {
        print "'$$field' is not a valid field to sort on.  Please choose either 'title' or 'date'.\n";
    }

}

```

---

### Post by drmrgd on 2014-02-17
I had a few minutes to play around tonight, and since I know I probably won't be able to touch this again for a while with upcoming stuff this week, thought I would add a rudimentary recursive directory processing routine.  I've tried a few different combinations (e.g. 

```

./mediainfo *
./mediainfo *.avi
./mediainfo ~/sandbox/media
./mediainfo .

```

and that all seems to work as far as I can tell.  This may be what you are looking for instead of having to manually traverse the directory tree looking for your .avi files.  

I also prettied up the format a bit in case the filenames start to change in length.  This will allow two neat columns no matter how long (well, within reason of course!) the names get:

```

$ ./media_catalog.pl -s date *.avi
Movie Title                  Mastered Date
MVI_0181                     Sun Apr 17 01:25:06 2005
MVI_0183                     Sun Apr 17 01:29:20 2005
MVI_0184                     Sun Apr 17 01:29:58 2005
MVI_0185                     Sun Apr 17 01:30:32 2005
Packing Day 001              Sun Apr 17 01:38:15 2005

$ ./media_catalog.pl -s date *
Movie Title                                         Mastered Date
file1                                               
file4                                               
file3                                               
file5                                               
file2                                               
MVI_0181                                            Sun Apr 17 01:25:06 2005
MVI_0183                                            Sun Apr 17 01:29:20 2005
MVI_0184                                            Sun Apr 17 01:29:58 2005
MVI_0185                                            Sun Apr 17 01:30:32 2005
Packing Day 001                                     Sun Apr 17 01:38:15 2005
This_is_some_long_name_that_I_use_as_an_example     Sun Apr 17 01:38:15 2005


```

I'm still sorting the movies without a 'Mastered Date' field to the top since you seemed to like that (and it's a bit easier :) ).

I think this covers everything but renaming the files.  Hopefully this is working as expected.  If you find any bugs, though, and I have some free time, I'm happy to mess around with it.  Enjoy!

```

#!/usr/bin/perl
# Using the mediainfo program, read in a list of movies and generate an output table of
# sorted movie titles and mastered dates.
#
# For now just print out the Mastered Date field.  Can add command line options to add 
# additional metadata as needed.
#
# 2/17/2014 - v1.5.0   Added sort routine and command line option to sort on either title
#                      or date field.
# 2/17/2014 - v2.0.0   Added the ability to load in directories and have the script recursively
#                      process the data.
#
# 2/13/2014
###########################################################################################


use warnings;
use strict;
use Getopt::Long;
use File::Basename;
use feature qw{ state };
use Data::Dumper;


( my $scriptname = $0 ) =~ s/^(.*\/)+//;
my $version = "v2.0.0";
my $description = <<"EOT";
Using the mediainfo program, read in a list of movies or a directory of movies, and generate an 
output table of sorted movie titles and Mastered dates.  The mediainfo metadata is stored in a 
hash that can be used to print out other movie inforamtion depending on what is required.
EOT


my $usage = <<"EOT";
USAGE: $scriptname [options] <input_file>
    -o, --output       Send output to custom file.  Default is STDOUT
    -s, --sort         Field to sort the output data on (default is 'title'.  Options are 'title' or 'date'
    -v, --version      Version information
    -h, --help         Print this help information
EOT


my $help;
my $ver_info;
my $outfile;
my $sort_field = 'title';


GetOptions( "output=s"    => \$outfile,
            "version"     => \$ver_info,
            "sort=s"      => \$sort_field,
            "help"        => \$help )
        or print $usage;


sub help {
        printf "%s - %s\n\n%s\n\n%s\n", $scriptname, $version, $description, $usage;
        exit;
}


sub version {
        printf "%s - %s\n", $scriptname, $version;
        exit;
}


help if $help;
version if $ver_info;


# Make sure enough args passed to script
if ( scalar( @ARGV ) < 1 ) {
    print "ERROR: Not enough arguments passed to script!\n\n";
    print "$usage\n";
    exit 1;
}


# Write output to either indicated file or STDOUT
my $out_fh;
if ( $outfile ) {
        open( $out_fh, ">", $outfile ) || die "Can't open the output file '$outfile' for writing: $!";
} else {
        $out_fh = \*STDOUT;
}


#########------------------------------ END ARG Parsing ---------------------------------#########
my @files = @ARGV;
my @files_to_process;


for my $file ( @files ) {
    @files_to_process = generate_filelist( \$file );
}


my %results = get_meta( \@files_to_process );


sort_output( \$sort_field, \%results );


sub generate_filelist {


    my $input_file = shift;
    state @filelist;


    if ( -d $$input_file ) {
        opendir( DIR, $$input_file ) || die "Can't read the directory '$$input_file': $!";
        my @dirlist = grep { ! /^\./ } readdir( DIR ); 
        my @recurs_files = map { $$input_file. "/" . $_ } @dirlist;
        for my $file ( @recurs_files ) {
            if ( -d $file ) {
                generate_filelist( \$file );
            }
            elsif ( $file =~ /\.avi$/ ) {  #assuming we only want to process .avi files
                push( @filelist, $file );
            } 
        }
    } else {
        push( @filelist, $$input_file ) if ( $$input_file =~ /\.avi$/ );
    }


    return @filelist;
}
    
sub get_meta {
    # use mediainfo to get movie metadata
    my $files = shift;


    my (%metadata, %results);
    my @sections;
    my @headers = qw{ General Video Audio };


    for my $file ( @$files ) {
        (my $movie_title = basename($file) ) =~ s/\.avi//; 


        # Read in the metadata from the 'mediainfo' program
        open( my $mi_data, "-|", "mediainfo", $file ) || die "Can't open the stream: $!";
        
        {
            local $/ = '';
            @sections = map { s/(General|Video|Audio)\n//; $_ } <$mi_data>;
        }


        # Store all of the metadata collected into a hash
        for my $i ( 0..$#sections ) {
            my @data = split( /\n/, $sections[$i] );
            $metadata{$headers[$i]} = {map { split( /\s+: /, $_ ) } @data}; 
        }
        $results{$movie_title} = $metadata{'General'}->{'Mastered date'} // '';
    }


    return %results;
}


sub sort_output {
    # Sort the metadate on either the title or Mastered date field
    use Time::Piece;
    use Sort::Naturally;


    my $field = shift;
    my $data = shift;
    my %sorted_data;


    my $cols = (col_width( $data ) + 4);
    printf $out_fh "%-${cols}s %s\n", "Movie Title", "Mastered Date";


    if ( $$field =~ /title/i ) {
        printf $out_fh "%-${cols}s %s\n", $_, $$data{$_} for ( nsort( keys %$data ) );
    }
    elsif( $$field =~ /date/i ) {
        printf $out_fh "%-${cols}s %s\n", $_, $$data{$_} for ( sort {
            Time::Piece->strptime( $$data{$a}, '%cdate' ) <=> Time::Piece->strptime( $$data{$b}, '%cdate' )
            } keys %$data );
    }
    else {
        print "'$$field' is not a valid field to sort on.  Please choose either 'title' or 'date'.\n";
    }


}


sub col_width {
    my $input = shift;
    my $width = 0;


    for my $keys ( %$input ) {
        $width = length( $keys ) if ( length( $keys ) > $width );
     }


     return $width;
 }

```

---

### Post by Caruyer on 2014-11-29
Hello.

In a first time, thank you a lot for this script !

I want to use this script with a lot of movies, and I have this error message : Odd number of elements in anonymous hash at ./[COLOR=#000000][FONT=Ubuntu Mono]media_catalog.pl[/FONT][/COLOR] line 158, <$mi_data> line 3.

Can you help me ?

Thank you.

Reyur

---

