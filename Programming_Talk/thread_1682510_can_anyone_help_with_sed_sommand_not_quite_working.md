---
title: "can anyone help with sed sommand not quite working...almost, but not quite yet"
date: 2011-02-06
forum: Programming Talk
---

### Post by thaitang on 2011-02-06
Hi gang,

I am trying to create some batch commands for many html pages I need to re-format.

I am trying the number 2b in this example to wrap anchor tags around the number that will be referenced in the footnotes.

I am trying to use the h/H hold command, but I have never tried using it before and it is not yet working.

From the sed help file example it uses the 'g/G' to extract whatever is in the hold buffer.

So basically, each of my html pages have pages numbers of text referring to the original text book numbers and used to reference each pages footnotes. So I want sed, each time it finds a page number to hold that page number in 'h/H' and then check each line after for '2b' or any number in which the line does not begin with '<' (already formatted with HTML tags) and wrap the number in anchor tags according to the last page number held in HOLD. 

Most pages have multiple page references, so every time sed encounters a new page number, it should re-write the HOLD space with new page number and begin applying that to each anchor, until of course another new page number is encountered.

I thought I had that with:
```
sed -i -e '/[0-9]\{1,3\}$/{h;};/^</!s/\([0-9]\{1,3\}[b]\{,1\}\)/\<a href="g\1End" name="g\1Txt"><font size=-1">[g:\1]<\/font><\/a>/g' 1.html
```but for this line of text:
```
From old Ikshváku's  2b line he came,
```I get:
```
From old Ikshváku's  <a href="g2bEnd" name="g2bTxt"><font size=-1">[g:2b]</font></a> line he came,
```It looks like 'g/G' is not what I need to extract whatever is (hopefully) in the HOLD space. Can anyone help me out here?

appreciated.
tt

---

### Post by Vaphell on 2011-02-06
is there any particular reason why you want to do this with a sed one-liner?

I'd write a bash/perl/python script using simpler constructs if i were you. More lines but much easier to grasp. Tricks with hold buffer are not exactly intuitive.

---

### Post by thaitang on 2011-02-06
> is there any particular reason why you want to do this with a sed one-liner?I guess we go with what we know.
> I'd write a bash/perl/python script using simpler constructsIf I had any of those tools in my toolbox perhaps I wouldn't be doing this with sed. But I use sed very regularly and usually I get done what I need, and I hope I still will, if anyone can help with the hold command usage here.

cheers,
tt

---

### Post by gmargo on 2011-02-06
I don't see any way to use the hold buffer directly as the replacement in a substitute.  I was able to come up with a method that sort of works, but it only replaces the first instance per line.  This would be much easier in perl or even awk.

This would have been easier given a more complete example of input and expected output. Also keep in mind that your page-number pattern will trigger for any line that ends in a number.

Here it is as a sed script. 
```

/[0-9]\{1,3\}$/ {
        # Print early so we can edit the line
        p
        # Isolate page number
        s/\([0-9]\{1,3\}\)$/\n\1/
        s/.*\n\(.*\)/\1/
        # Put into Hold space
        h
        # move on without printing again
        d
}

/^</! {
    # paste newline and page number
    G
    s/[0-9]\{1,3\}[b]\{,1\}\(.*\)\n\(.*\)$/\<a href="g\2End" name="g\2Txt"><font size=-1">[g:\2]<\/font><\/a>\1/;

    # Remove newline/page number if there was no match
    s/\n\(.*\)$//;
};

```And... using my favorite tool... Here's a perl script that works for all matches on a line:
```

#!/usr/bin/perl -w
use strict;
use warnings;

my $page = "0";

while (<>)
{
    s/[[:space:]]+\z//s;

    if (/([0-9]{1,3})$/)
    {
        $page = $1
    }
    elsif (!/^</ && /\b[0-9]{1,3}b?/)
    {
        s/\b[0-9]{1,3}b?\b/<a href="g${page}End" name="g${page}Txt"><font size=-1">[g:${page}]<\/font><\/a>/g;
    }

    print "$_\n";
}

```

---

