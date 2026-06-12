---
title: "perl script too slow"
date: 2007-09-18
forum: Programming Talk
---

### Post by Houman on 2007-09-18
hi there;

I have a perl script that pipes the output of a process and parses it, it repeats this process a few hundred times, the odd thing is that the script slows down as times goes by, that means the time it takes for a single fork&parse increases;

the odd this is that if i remove all the parsing code so that all i have is something like this:

```

 for ($counter=0; $counter<$numite; $counter++)
    {
	my $progname=&compose($parmz,$errorratio);
	my $pid = open(README, "$progname |")  or die "Couldn't fork: $!\n";
	close README;

    }


```

it runs very fast, but once i put this in: 

```

 for ($counter=0; $counter<$numite; $counter++)
    {
	my $progname=&compose($parmz,$errorratio);
	my $pid = open(README, "$progname |")  or die "Couldn't fork: $!\n";
	[COLOR="Red"]
        while (<README>) 
	{
#	    $line= $_;    
	}[/COLOR]
	close README;

    }

```
it starts to slow down exponentially as time goes by;

this is very odd and I cant explain it, by the way, each time the executable is forked from my script it produces about 100 lines of text to be parsed (so its not that big).

please let me know if you can figure out why this script is slowing down and also if there is any way to speed it up;

regards

Houman

---

### Post by Houman on 2007-09-18
ops it seems like there was something wrong with the process i was running ( it was allocating giant chunks of memory without releasing them) I went through it with valgrind and fixed them up now things are ok;

so the script is fine, the process that is being forked is the problem , :lolflag:


regards

Houman

---

