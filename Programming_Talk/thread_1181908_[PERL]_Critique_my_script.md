---
title: "[PERL] Critique my script?"
date: 2009-06-08
forum: Programming Talk
---

### Post by tcoffeep on 2009-06-08
In an attempt to learn more about perl, and try to get a grip on the basics, I wrote a script involving Linux From Scratch. What it does, essentially, is reads a list ( wget.list), counts how many lines, aside from blank lines, then reads it again, and downloads every line. When it finishes downloading, it then checks the md5sum against a list of md5sums ( wget.md5list ), and if it verifies, goes onto the next one. If not, it deletes the file, and the wget.log ( what i use to check against the wget.md5list ), and quits. I am very much a beginner, and this took me a few hours to scrape together, but I'm hoping someone might look over it, and shoot me some tips. :)

The Perl Script : [http://dexodro.angelfire.com/pget.pl](http://dexodro.angelfire.com/pget.pl)
The Wget List : [http://dexodro.angelfire.com/wget.list](http://dexodro.angelfire.com/wget.list)
The MD5SUM List : [http://dexodro.angelfire.com/wget.md5list](http://dexodro.angelfire.com/wget.md5list)

Thanks, ahead of time. :)

---

### Post by Greyed on 2009-06-09
Main thing that stands out in the case of style is the inconsistent spacing between function names and the parens.  You have system () and open () in some areas but then use unlink() in others.  Generally speaking parens should not have a leading space if they are attached to a function call.  They should if they are grouping items, such as in a control statement like if, while, etc.

I also think there might be a way to trim down on the loops a tad but that's more an efficiency question in a pre-optimizing context.  IE, if its working in a timely manner for you then I'm probably just trying too hard to find places to shave off cycles that don't much matter one way or the other.  ;)

---

### Post by ghostdog74 on 2009-06-09
@OP
1)if you get everything into an array,eg
```

@array=<FILE>

```
and count the number of items, you can get the number of lines in a file.

2) if you want to iterate a file, you can go back to the beginning of the file without having to reopen a filehandle to the same file by using seek/tell. Check perldoc -f seek , perldoc -f tell

3) if you want to use Perl, then use Perl. don't intermix shell tools with Perl. If you want MD5 checksum, use the module Digest::MD5. If you want to clear the screen, you can use a custom function eg
```

# 
sub clearscreen() {
for ($i=0;$i<=120;$i++){
 print "\n";
}
}

```
or if you want to use system(), then check for OS platform and issue the correct clear screen command. (this is for portability reason)

4) for getting pages of web, use LWP , no need to use wget.

---

### Post by tcoffeep on 2009-06-09
I've begun rewriting it, but I've ran into a dead end. I rewrote the entire thing, and I'm trying to download the tar.{gz,bz2} files, but am running into a wall with the md5 check. The download works using :

```

my $bin_data = get(@filenum[$b]);
@name = split(/\//,@filenum[$b]);
$filename = "${name[-1]}";

open OUT,"> $filename";
binmode OUT;
print OUT $bin_data;
close(OUT);

```

and then after the download, it checks like this :

```

my $digest = md5("$filename");
print "$digest\n";
if ($digest eq @md5list[$b] ) {
	print "Verified!\n\n";
} else {
	print "Verification failed.\n";
	die;
}

```

But what pops out : 

> 
There are 86 programs/patches to be downloaded.

autoconf-2.63.tar.bz2
 finished downloading. Verifying...
ó®2&#382;ui`&#8240;ï<§Þ¶&#732;&#8230;
Verification failed.
Died at ./pget.pl line 55.


Is it the way I'm downloading them that is screwing up the md5sum?

[EDIT]:

I tried using md5_hex instead and got this :

$digest : f3ae329e75696089ef3ca7de0fb69885
Entry in wget.md5list : 7565809ed801bb5726da0631ceab3699

[EDIT #2]:
After tinkering for about half hour with LWP, I used getstore instead, but this time :

```

There are 86 programs/patches to be downloaded.

autoconf-2.63.tar.bz2 finished downloading. Verifying...
d999288e7a7f404f4a45f4f3b2f1acb5
7565809ed801bb5726da0631ceab3699

Verification failed.
Died at ./pget.pl line 60.

```

The second md5sum being what it's looking for.

---

### Post by tcoffeep on 2009-06-09
------- HOPEFULLY THE FINAL UPDATE ----------

Nothing changed, but, curiously enough, when I md5sum the downloaded .bz2 file outside of Perl, or use the system function using md5sum, I get the correct md5sum. Any ideas?

---

### Post by unutbu on 2009-06-09
Is $filename the name of the file? If so, change
```

my $digest = md5("$filename");

```
to
```

$digest = md5($data);

```
where $data is the contents of the file. See [http://search.cpan.org/dist/Digest-MD5/MD5.pm](http://search.cpan.org/dist/Digest-MD5/MD5.pm)

---

### Post by johnl on 2009-06-09
```

echo "autoconf-2.63.tar.bz2" | md5sum
f3ae329e75696089ef3ca7de0fb69885 *-

```

You're taking the md5sum of the filename, not the file contents :)

---

### Post by tcoffeep on 2009-06-09
Oh, wow! I feel kinda stupid now.

Regardless, the script has been rewritten and updated. If you all are still willing to critique, I am willing to take some advice. :)

[http://dexodro.angelfire.com/pget.pl](http://dexodro.angelfire.com/pget.pl)

---

### Post by tcoffeep on 2009-06-11
Updated, for anyone who is interested. I think I'm making some progress. :D

The old script : [http://dexodro.angelfire.com/pget.pl](http://dexodro.angelfire.com/pget.pl)
The new script : [http://dexodro.angelfire.com/pget-beta.pl](http://dexodro.angelfire.com/pget-beta.pl)

The new lists :
[http://dexodro.angelfire.com/pget.list](http://dexodro.angelfire.com/pget.list)
[http://dexodro.angelfire.com/pget.md5list](http://dexodro.angelfire.com/pget.md5list)

---

### Post by ghostdog74 on 2009-06-11
instead of using many print statements, you can use here document. 
```

my $string = <<EOF;
*********************************
blah blah
*********************************
EOF
print $string

```
type perldoc -q "document" for more info

---

