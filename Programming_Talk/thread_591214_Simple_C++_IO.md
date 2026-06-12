---
title: "Simple C++ I/O"
date: 2007-10-25
forum: Programming Talk
---

### Post by joebanana on 2007-10-25
Hi. I have a simple question. I have a text file that looks something like this.

```

3
London Paris
Berlin Milano Ljubljana
Athene NewYork Amsterdam

```

Of course it can have more sets of cities or longer sets. For each line of file I will create one link list, of which an element will have a name after the city.

I tried getline(file, line, ' ') but i need to stop at '\n' too.

---

### Post by aks44 on 2007-10-25
Read the lines ('\n') in an outer loop, read the cities (' ') in an inner loop?

---

### Post by Sporkman on 2007-10-25
For example... (untested as of yet, but you get the drift)

```


main()
{
......

   char * ln = new char [MAX_LINE_LEN];

   int i;

   for ( i=0; !feof(f); ++i )
   {
      if ( !read_line(f,ln) )
      {
         // print error or whatever
      }

      // now scan stuff from ln...
   }

   delete [] ln;
}


   bool read_line ( FILE *f, char * ln )
   {
      char c;
      int i;
      for ( i=0, c=fgetc(f); c!='\n' && c!='\r' && !feof(f); ++i, c=fgetc(f) )
      {
         if ( i>=MAX_LINE_LEN )
         {
            return false;
         }
         ln[i] = c;
      }
      ln[i] = '\0';
      return true;
   }


```

---

### Post by Sporkman on 2007-10-25
...if you don't want to commit to a MAX_LINE_LEN, you can use std::string instead, and just append characters (ex: s += c), then overrunning an array won't be an issue.

---

### Post by RageOfOrder on 2007-10-25
Yup. That's really the easiest c/c++ way to do that.

If only you could use perl

```

#!/usr/bin/perl
# A perl script to parse a text file and stuff
use strict;
use warnings;

my @file = <STDIN>;
my @list, my @split, my $MAX_LEN = -1;

foreach ( @file )
{
	if( $MAX_LEN == -1 )
	{
		$MAX_LEN = $_;	
	}
	else
	{
		@split = split(/ /);
	}	
	@list = (@list, @split);

}

print "@list\n";


```

The split gives you an array (which in perl can do anything you need a C linked list to do) and then I append it to @list which contains all of the values in one long array. In case you wanted one long linked list :)

---

### Post by joebanana on 2007-10-31
I tried to did that without the whole line reading, but gave up and now I use while(fp.getline(line,MAX_LEN)) and then split line. Thx 4 replies.

---

