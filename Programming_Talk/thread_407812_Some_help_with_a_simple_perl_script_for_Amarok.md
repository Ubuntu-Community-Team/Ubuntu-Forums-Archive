---
title: "Some help with a simple perl script for Amarok?"
date: 2007-04-12
forum: Programming Talk
---

### Post by ortazel on 2007-04-12
I have a music server running Ubuntu, and using Amarok as the mp3 player. To avoid getting up and changing the song every time, I downloaded [this](http://www.whizziwig.com/wp-content/static/code/afp3.pl) perl script which allows me to control Amarok through Putty. I had to change a couple of things in the script (adding --user <username> to the dcop command), but at this point I have it working for simple commands- pause, next/prev etc.
However, the script also has support for searching for a particular artist/album and automatically adding everything it finds to the playlist. This would be really useful; unfortunately the code is broken. When it adds the files to Amarok's playlist, the location given is, for example, "./media/music/music.mp3". Amarok doesn't take kindly to the period at the beginning of that, and any entry I manually add from the collection sidewindow would take the form "/media/music/music.mp3".

How can I make the perl script strip out that period at the beginning of the URL?

Edit- here's the relevant code section for those who don't want to download a random script-
```
if ($options{'a'}){
    print "Searching Artists ...\n" unless $options{'q'};
    push(@tables, "artist");
    $search_column = "artist.name";
    push(@clauses, "tags.artist=artist.id");
} elsif ($options{'A'}){
    print "Searching Albums ..." unless $options{'q'};
    push(@tables, "album");
    $search_column = "album.name";
    push(@clauses, "tags.album=album.id")
} elsif ($options{'g'}){
    print "Searching Genres ...\n" unless $options{'q'};
    push(@tables, "genre");
    $search_column = "genre.name";
    push(@clauses, "tags.genre=genre.id");
} else {
    print "Searching Files/URLs ...\n" unless $options{'q'};
    $search_column = "tags.url";
}

$join = "AND";
$join = "OR" if $options{'o'};

#print "FOR: \n" unless $options{'q'};
foreach $q (@ARGV){
    push(@clauses, " $search_column LIKE '%$q%' ");
    print "\t $q" unless $options{'q'};
    print " $join" unless ($q eq $ARGV[-1] || $options{'q'});
    print "\n" unless $options{'q'};
}

$query = "select url from " .
    join(",", @tables) . 
    " WHERE " .
    join(" $join ", @clauses);


print "Query : $query\n" unless $options{'q'};

my @urls;
open(QUERY, "dcop amarok collection query \"$query\"|");
while(<QUERY>){
    chomp();
#    print "Found: $_\n" unless $options{'q'} &&
#	($options{'r'} || $options{'n'});
    push(@urls, $_);
}

if(@urls > 0){
    @urls = List::Util::shuffle(@urls) if ($options{'r'});
    @urls = @urls[0 .. $options{'n'}-1] if $options{'n'};

    print "Adding ", @urls+0, " URLs\n" unless $options{'q'};
    foreach $u (@urls){
	print "Adding: $u\n" if $options{'v'};
    }

    system("dcop", "amarok", "playlist", "addMediaList", "[", @urls, "]");
    (sleep(2) && system("dcop", "amarok", "playlist", "playByIndex", "0")) if $options{'c'};
}
```

---

### Post by wdk on 2007-04-12
All you should have to do is add this:

```

s/^\.//;

```

to the line following the chomp() command. 
All it does is search for a "." at the beginning of the line and replace it with nothing.

Good luck!

---

