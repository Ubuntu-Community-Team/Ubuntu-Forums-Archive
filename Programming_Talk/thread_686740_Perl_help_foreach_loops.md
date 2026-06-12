---
title: "Perl help foreach loops"
date: 2008-02-03
forum: Programming Talk
---

### Post by vicpascow on 2008-02-03
Hopefully an easy perl question...


i have two foreach loops breaking apart different arrays:

foreach $product (@array1) {
   chomp($product);
   ($list1,$list2,$list3)=split(/ /,$product);				
}

foreach $product2 (@array2) {
   chomp($product2);
   ($lista,$listb,$listc)=split(/\|/,$product2);	
}



i want to be able to find out if anything in $list2 is contained in $listc.  if it is, i want to print the string from product2 that contains this match.  i am having problem accessing the lists OUTSIDE of their foreach loops.  

any help?

thanks 1 000 000!

---

### Post by shawnhcorey on 2008-02-03
> **vicpascow said:**
> Hopefully an easy perl question...


i have two foreach loops breaking apart different arrays:

foreach $product (@array1) {
   chomp($product);
   ($list1,$list2,$list3)=split(/ /,$product);				
}

foreach $product2 (@array2) {
   chomp($product2);
   ($lista,$listb,$listc)=split(/\|/,$product2);	
}



i want to be able to find out if anything in $list2 is contained in $listc.  if it is, i want to print the string from product2 that contains this match.  i am having problem accessing the lists OUTSIDE of their foreach loops.

I'm not sure what you mean by "the string from product2" but I think this is closer to what you want:

```
foreach $product (@array1) {
   chomp($product);
   ($list1,$list2,$list3)=split(/ /,$product);

   foreach $product2 (@array2) {
      chomp($product2);
      ($lista,$listb,$listc)=split(/\|/,$product2);

      if( $listc =~ /$list2/ ){
         print "$product2\n";
     }

   }
}
```

---

### Post by vicpascow on 2008-02-03
this will cycle through the second foreach loop for every line in the first foreach loop, though.  right?

i want this to be able to work with huge datasets.

---

### Post by shawnhcorey on 2008-02-03
> **vicpascow said:**
> this will cycle through the second foreach loop for every line in the first foreach loop, though.  right?

i want this to be able to work with huge datasets.

This is a general purpose solution.  Unless there is additional information you can take advantage of, you stuck with it.

On the other hand, does $listc contain $list2 or is it equal to it?  If so, you can sort both lists and compare them in a linear fashion.  If not, can you break $listc into multiple lists and compare them in the same fashion?


Linear comparison of sorted lists:

```
$i = 0;
$j = 0;
while( $i < @list1 && $j < @list2 ){
    if( $list1[$i] lt $list2[$j] ){
        $i ++;
    }elsif( $list1[$i] gt $list2[$j] ){
        $j ++;
    }else{
        print "$list1[$i] $list2[$j]\n";
        $i ++;
        $j ++;
    }
}
```

Mayhaps you can give some example data?  Say 10 lines from each list?  (Don't use real data; create some that has the characteristics of real data but is fake.  You don't want to give propriety data in an open forum.)

---

### Post by vicpascow on 2008-02-04
I want to return the line, not just the count.  Thanks for the continued help.



array 1:

aaa bbb c123
ddd eee f456
fss sdf g432
gds dfg h124
dgs jghdfg h323522
fgsgdsf fg 89ffd


array 2:

dsfa|sdfsdf|erge214
fasdf|hjgh|qwe12
af|eee|dfsdf342
dfa|bbb|fsdfs32
fs|df|fd


etc.  thanks!

---

### Post by shawnhcorey on 2008-02-04
This program should give you reasonable speed:

```
#!/usr/bin/perl
# --------------------------------------
#
#   Title: Get It
# Purpose: Demonstration of retrieving data via embedded keys.
#
#    Name: getit
#    File: getit
# Created: February  4, 2008
#
# Copyright: Copyright 2008 by Mr. Shawn H. Corey.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, version 3 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

# --------------------------------------
# Pragmas

require 5.8.0;

use strict;
use warnings;

# --------------------------------------
# Version
our $VERSION = '1.0.0';

# --------------------------------------
# Modules
use Data::Dumper;
use Getopt::Long;
use Pod::Usage;
use POSIX;

# --------------------------------------
# Configuration Parameters

$Data::Dumper::Sortkeys = 1;
$Data::Dumper::Indent   = 1;
$Data::Dumper::Maxdepth = 0;

# --------------------------------------
# Variables

my %Key_Hash = ();
my $Max_Len = 0;    # Maximum length of the keys.
my $Min_Len = 1e6;  # Minimum length of the keys.

# Documentation levels
my $DOC_USAGE = 0;
my $DOC_HELP  = 1;
my $DOC_MAN   = 2;

# --------------------------------------
# Subroutines

# --------------------------------------
#        Usage: print_documentation( $documentation_level );
#      Purpose: Print the usage, help, or man documentation.
#      Returns: Does not return.
#   Parameters: $documentation_level
#             :   0 == usage
#             :   1 == help
#             :   other == man
# Side Effects: none
#       Throws: no exceptions
#     Comments: none
#     See Also: n/a
#
sub print_documentation {
  my $level = shift @_;

  # print the usage documentation
  if( $level == $DOC_USAGE ){
    pod2usage(
      -exitval => 2,
      -verbose => 99,
      -sections => 'USAGE',
    );
  }

  # print the help documentation
  if( $level == $DOC_HELP ){
    pod2usage(
      -exitval => 2,
      -verbose => 99,
      -sections => 'NAME|VERSION|USAGE|REQUIRED ARGUMENTS|OPTIONS',
    );
  }

  # print the man documentation
  pod2usage(
    -exitval => 2,
    -verbose => 2,
  );
}

# --------------------------------------
#        Usage: initialize_program();
#      Purpose: To do those tasks that can only be done at run time.
#      Returns: none
#   Parameters: none
# Side Effects: none
#       Throws: no exceptions
#     Comments: none
#     See Also: n/a
#
sub initialize_program {

  # Check command-line options
  unless( GetOptions(
    usage => sub { print_documentation( $DOC_USAGE ); },
    help  => sub { print_documentation( $DOC_HELP  ); },
    man   => sub { print_documentation( $DOC_MAN   ); },
  )){
    print_documentation( $DOC_USAGE );
  }

  # Skip POD data
  while( <DATA> ){
    last if m{ \A __DATA__ }msx;
  }

}

# --------------------------------------
#        Usage: create_key_hash();
#      Purpose: The key hash holds all possible keys.  This gives quick access
#               to them.
#      Returns: none
#   Parameters: none
# Side Effects: %Key_Hash is loaded.
#       Throws: no exceptions
#     Comments: none
#     See Also: n/a
#
sub create_key_hash {

  %Key_Hash = ();

  while( <DATA> ){
    last if m{ \A __DATA__ }msx;
    chomp;
    my ( undef, $key ) = split /\s+/, $_;  # split on whitespace
    $Key_Hash{$key} = 1;
    my $len = length( $key );
    $Max_Len = $len if $Max_Len < $len;
    $Min_Len = $len if $Min_Len > $len;
  }

  # print Dumper \%Key_Hash;
  return;
}

# --------------------------------------
#        Usage: scan_data();
#      Purpose: Scan the second data set and output any that have partial keys.
#      Returns: none
#   Parameters: none
# Side Effects: none
#       Throws: no exceptions
#     Comments: none
#     See Also: n/a
#
sub scan_data {

  while( <DATA> ){
    last if m{ \A __DATA__ }msx;
    chomp;
    my ( undef, undef, $item ) = split /\|/, $_;
    for my $index ( 0 .. length( $item ) - $Min_Len ){
      for my $len ( $Min_Len .. $Max_Len ){
        my $key = substr( $item, $index, $len );
        if( $Key_Hash{$key} ){
          print "$item ($key) : $_\n";
          last;
        }
      }
    }
  }

  return;
}

# --------------------------------------
# Main

initialize_program();

create_key_hash();
scan_data();


__END__

=head1 NAME

getit - Demonstration of retrieving data via embedded keys.

=head1 VERSION

This document refers to getit, version 0.0.0

=head1 USAGE

  getit [<options>] [<file>] ...
  getit --usage|help|man

=head1 REQUIRED ARGUMENTS

=head1 OPTIONS

=over 4

=item --usage

Print a brief usage message.

=item --help

Print usage, required arguments, and options.

=item --man

Print the manual page.

=back

=head1 DESCRIPTION

This program is for demonstration purposes.
Adopt it to your needs.

=head1 DIAGNOSTICS

=head1 CONFIGURATION AND ENVIRONMENT

=head1 DEPENDENCIES

=head1 INCOMPATIBILITIES

=head1 BUGS AND LIMITATIONS

=head1 SEE ALSO

=head1 ORIGINAL AUTHOR

Mr. Shawn H. Corey

=head2 Contributing Authors

(Insert your name here if you modified this program or its documentation.)

=head1 COPYRIGHT & LICENCES

Copyright 2008 by Mr. Shawn H. Corey.

=head2 Software Licence

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

=head2 Document Licence

Permission is granted to copy, distribute and/or modify this document under the
terms of the GNU Free Documentation License, Version 1.2 or any later version
published by the Free Software Foundation; with the Invariant Sections being
ORIGINAL AUTHOR, COPYRIGHT & LICENCES, Software Licence, and Document Licence.

You should have received a copy of the GNU Free Documentation Licence
along with this document; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA

=head1 ACKNOWLEDGEMENTS

=head1 HISTORY

  $Log$

=cut

__DATA__
aaa bbb c123
ddd eee f456
fss sdf g432
gds dfg h124
dgs jghdfg h323522
fgsgdsf fg 89ffd
__DATA__
dsfa|sdfsdf|erge214
fasdf|hjgh|qwe12
af|eee|dfsdf342
dfa|bbb|fsdfs32
fs|df|fd
```

---

### Post by samdc on 2008-02-05
I don't really understand what you are trying to do.  It would be helpful if you could also include an output sample based on your input sample.

But anyway, my idea is for you to use a hash to create a data structure with list2 as keys when you loop thru array1.  This way the only thing you will need to do when you loop thru array2 list is to do a lookup in that hash.

Here's an example:
```

# this is a data structure to hold your list2 data
# typically a hash is used in this regard
my $list2_hash = {};

foreach my $product (@array1) {
	chomp($product);
	my ($list1, $list2, $list3) = split(/\s+/, $product);
	$list2_hash->{$list2}++; # save list2 as key
}

foreach my $product2 (@array2) {
	chomp($product2);
	($lista, $listb, $listc) = split(/\|/, $product2);
	
	# now lookup the data structure, specifying listc as key
	if (exists $list2_hash->{$listc}){
		print $product2, "\n";
	}
}

```

Hope that helps.

---

### Post by ghostdog74 on 2008-02-05
if you can use awk
```

#!/bin/sh
awk 'BEGIN{FS="[ |]"}
FNR==NR{
 a[$2] = $0
 next
}
{
  print a[$3]
}
' file1 file2

```
otherwise, here's the equivalent perl code
```

$[ = 1;			# set array base to 1
$FS = ' ';		# set field separator
$, = ' ';		# set output field separator
$\ = "\n";		# set output record separator
$FS = '[ |]';
line: while (<>) {
    chomp;	# strip record separator
    @Fld = split($FS, $_, -1);
    if (($.-$FNRbase) == $.) {
	$a{$Fld[2]} = $_;
	next line;
    }
    print $a{$Fld[3]};
}
continue {
    $FNRbase = $. if eof;
}

```

---

### Post by vicpascow on 2008-02-10
Thanks all.

Regarding samdc's post:

is there a way I can make this search case-insensitive?

meaning some of listc's values use capitals, and don't appear.

i tried:
if (exists $list2_hash->{$listc**/i**}){

but this did not work...

---

### Post by shawnhcorey on 2008-02-10
> **vicpascow said:**
> Thanks all.

Regarding samdc's post:

is there a way I can make this search case-insensitive?

Yes

---

### Post by samdc on 2008-02-12
> **vicpascow said:**
> Thanks all.

Regarding samdc's post:

is there a way I can make this search case-insensitive?

meaning some of listc's values use capitals, and don't appear.

i tried:
if (exists $list2_hash->{$listc**/i**}){

but this did not work...

Sorry vicpascow.  I got busy.  Yes.  There is a way, and it is very simple, store all keys as uppercase, then when you lookup, make sure to uppercase listc, here goes....

```

# this is a data structure to hold your list2 data
# typically a hash is used in this regard
my $list2_hash = {};

foreach my $product (@array1) {
	chomp($product);
	my ($list1, $list2, $list3) = split(/\s+/, $product);
	$list2_hash->{uc $list2}++; # save list2 as key, uppercase it
}

foreach my $product2 (@array2) {
	chomp($product2);
	($lista, $listb, $listc) = split(/\|/, $product2);
	
	# now lookup the data structure, specifying listc as key, uppercase first
	if (exists $list2_hash->{uc $listc}){
		print $product2, "\n";
	}
}

```

---

### Post by shawnhcorey on 2008-02-12
> **samdc said:**
> Sorry vicpascow.  I got busy.  Yes.  There is a way, and it is very simple, store all keys as uppercase, then when you lookup, make sure to uppercase listc, here goes....

You're both missing the fact that the OP stated the key from the first file had to pattern match the second, NOT match it exactly.

Also, a correction to my code:

```
# --------------------------------------
#        Usage: scan_data();
#      Purpose: Scan the second data set and output any that have partial keys.
#      Returns: none
#   Parameters: none
# Side Effects: none
#       Throws: no exceptions
#     Comments: none
#     See Also: n/a
#
sub scan_data {

  while( <DATA> ){
    last if m{ \A __DATA__ }msx;
    chomp;
    my ( undef, undef, $item ) = split /\|/, $_;
KEYS_LOOP:
    for my $index ( 0 .. length( $item ) - $Min_Len ){
      my $max = length( $item ) - $index;
      $max = $Max_Len if $max > $Max_Len;
      for my $len ( $Min_Len .. $max ){
        my $key = substr( $item, $index, $len );
        if( $Key_Hash{$key} ){
          print "$item ($key) : $_\n";
          last KEYS_LOOP;
        }
      }
    }
  }

  return;
}

```

---

### Post by samdc on 2008-02-18
> **shawnhcorey said:**
> You're both missing the fact that the OP stated the key from the first file had to pattern match the second, NOT match it exactly.


Ok, I missed that detail, if that's the case then you can use the grep trick as follows.  Again, I apologize, this code is untested.  But the idea about grep is that,the expression returns true if any of keys is contained in your $list2.  Also as you noticed I have modifier* i *for case insensitive.  Try....

```

# this is a hash to hold your list2 as keys
my $list2_hash = {};

foreach my $product (@array1) {
	chomp($product);
	my ($list1, $list2, $list3) = split(/\s+/, $product);
	$list2_hash->{$list2}++; # save list2's
}

foreach my $product2 (@array2) {
	chomp($product2);
	($lista, $listb, $listc) = split(/\|/, $product2);
	
	# now lookup the hash, using grep
	if (grep $listc =~ /$_/i, keys %$list2_hash){
		print $product2, "\n";
	}
}

```

---

