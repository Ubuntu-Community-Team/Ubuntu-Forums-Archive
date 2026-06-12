---
title: "from perl to python"
date: 2008-03-03
forum: Programming Talk
---

### Post by helphope on 2008-03-03
Hi everybody

I've got a perl script which indexes words by page: for instance

item1 - 1,4,6
item2 - 5,9,23
item3 - 7,,44,8

The numbers are the page numbers where the items/words are written

Now I'd like ot turn the perl script (which I don't understand - maybe just a bit) into python (which I've started studying); if someone, please, can help me in understanding the following per script

```

my $page_number = 1;
my %idx;

while(<>) {
        for my $word ( split(/\s+/) ) {
                $idx{$word}{$page_number} = 1;
        }
        $page_number++ if ( /\014/ );
}

foreach my $word (sort keys %idx) {
        printf "%-20s ", $word;
        print comma_sep(sort {$a <=> $b} keys %{$idx{$word}});
        print "\n";
}

sub comma_sep {
        my $ret = "";
        foreach (@_) { $ret .= $_ . ", "; }
        chop $ret;                                       
        chop $ret;
        return $ret;
}
```

Maybe split(/\s+/) is the split funciton applied to a regex?
CHop is a remove function?
Thanks a lot

---

