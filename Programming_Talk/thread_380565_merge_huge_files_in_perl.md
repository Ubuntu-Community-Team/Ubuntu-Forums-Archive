---
title: "merge huge files in perl"
date: 2007-03-09
forum: Programming Talk
---

### Post by monkeyking on 2007-03-09
I need to merge some huge files in the gigabyte size.

The files are huge flat textfiles,

They all essentialy have the same number of rows,
The leftmost colomn is the "key"/id  and the "new" file to be merged should have the leftmost colomn removed, and then be attached to the original file such that the row is matched to the key/id.

I can't read everything into the memory and then rearrange.

But it seems like massive overkill/underkill to write the file back to the harddisk each time I extend a row.

Does anyone have an idea how solve this in a clever way.

---

### Post by LotsOfPhil on 2007-03-10
How about the Tie module?  [http://perldoc.perl.org/Tie/File.html](http://perldoc.perl.org/Tie/File.html)

From the Description:
"Tie::File represents a regular text file as a Perl array. Each element in the array corresponds to a record in the file. The first line of the file is element 0 of the array; the second line is element 1, and so on.
The file is not loaded into memory, so this will work even for gigantic files.
Changes to the array are reflected in the file immediately.
Lazy people and beginners may now stop reading the manual."

---

### Post by monkeyking on 2007-03-11
Thanks,
looks like what I need.

---

### Post by pbernedo on 2007-07-10
Hi,

I wrote a litle script to merge files in perl but is very slow in comparison to sort


sort --merge file1 file2 file3 ....

perl_merger.pl file1 file2 file3

where perl_merger.pl is:


-----------------------------------------------------------------
[COLOR="Blue"]use Tie::File;

my @files = @ARGV;
my $count = scalar @files;

#print "merging $count files \n";

my %hash_ties = ();
my $hash_pointers = ();
for my $file (@files){
#create arrays.
	my @array =();
#store reference in a hash
	$hash_ties{$file} = \@array;
	$hash_pointers{$file} = 0;
	tie  @array, 'Tie::File', $file, recsep => "\n";		 
}

my $something_is_there = 1;
my $lines =0;
while ($something_is_there){
	my $min_line = "zzzzzzzzzzz";
	my $min_file = "";
	$something_is_there = 0;
	for my $file (@files){
		if (defined @{$hash_ties{$file}}[$hash_pointers{$file}]){			
			if ( @{$hash_ties{$file}}[$hash_pointers{$file}] lt $min_line ){
				$min_file = $file;
				$min_line = @{$hash_ties{$file}}[$hash_pointers{$file}];
			};
			$something_is_there=1;
		}
	}
	if ($something_is_there){
		print $min_line."\n";
		$hash_pointers{$min_file}++;
	}
}

for my $file (@files){
	untie $hash_ties{$file};
}[/COLOR]

-----------------------------------------------------------------

any thoughts on how to make it faster?

thank you,

Percy

---

