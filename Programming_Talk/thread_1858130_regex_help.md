---
title: "regex help"
date: 2011-10-11
forum: Programming Talk
---

### Post by craigbennet3 on 2011-10-11
Good afternoon,

I have a log file that has several space-separated fields that I am trying to modify in a script, using sed. One of the fields is also enclosed by " <" and "> " (quotes used for clarity, they are not part of the field). All other fields are "atomic", in that they do not contain spaces. The field that is enclosed by < > contains a string that may contain zero or more spaces. I need to either change the field separator, or, better yet, change the spaces within this field into underscores. If the solution involves changing the field separator, a comma may not be used because some of my other fields already contain commas. The tab character would be a good candidate for an alternative separator.

Example:
```
1316888300.168 0 10.200.18.128 TCP_DENIED/401 380 GET http://url.example.com?thiscode=R61UBH9&prod=someprod&ver=1.0&li=en&loc=us - NONE/- - OTHER-NONE-NONE-NONE-NONE-NONE-NONE <IW_srch,6.7,"1","-",-,-,-,"-","-",-,-,-,"-","-",-,"-","-",-,-,IW_srch,-,"-","-","Generic Search Engine Traffic","Search Engine","-","-",125.48,0,-,"-","-"> -
```And what I need is:
```
1316888300.168 0 10.200.18.128 TCP_DENIED/401 380 GET http://url.example.com?thiscode=R61UBH9&prod=someprod&ver=1.0&li=en&loc=us - NONE/- - OTHER-NONE-NONE-NONE-NONE-NONE-NONE <IW_srch,6.7,"1","-",-,-,-,"-","-",-,-,-,"-","-",-,"-","-",-,-,IW_srch,-,"-","-","Generic_Search_Engine_Traffic","Search_Engine","-","-",125.48,0,-,"-","-"> -
```Note that
```
"Generic Search Engine Traffic","Search Engine
```became
```
"Generic_Search_Engine_Traffic","Search_Engine
```I swear, I just can not get my head around this problem. I can draw a DFA that appears to accomplish this simple task, but darned if I can convert it into a regular expression that works with sed. I'd write a script to do this, but these log files are huge. I figure sed would be the most efficient. Would someone care to take the time to explain the steps towards this RE?

Thanks,
Craig

---

### Post by gmargo on 2011-10-11
I would do it with a perl script.
```

#!/usr/bin/perl -w
use strict;
use warnings;

while (my $line = <>)
{
    if ($line =~ /^(.*?)<([^>]+)>(.*)/s)
    {
        my ($lead, $bracketed, $rest) = ($1,$2,$3);
        $bracketed =~ s/ /_/g;
        print "$lead"."<".$bracketed.">".$rest;
    }
    else
    {
        print $line;
    }
}

```
This assumes only one "<>" section per line.

---

### Post by CaKiwi on 2011-10-12
Or use gawk

```
gawk -F"(<|>)" '/<.*>/ {gsub(/ /,"_",$2);print $1 "<" $2 ">" $3;next}1' file1 > file2
```

---

### Post by craigbennet3 on 2011-10-12
gmargo - Unfortunately one of the other fields is a URL, and it can contain < and > characters. It will not contain, to the best of my knowledge either string " <" or "> ".

CaKiwi - I thought of using awk as well, but again the problem is not knowing the search/substitute patterns to use. The command you provided seems to do more than replace spaces because the output file size after running it is smaller than the input file. If we are doing a simple character for character replacement the file sizes should be identical. Unfortunately the smallest file I have is over three million lines long, and the difference is only ~24,000 bytes, so finding the missing 24,000 bytes out of 1.6 GB is going to be quite arduous at best. But, you've given me something to study, and I appreciate that.

Thanks to both of you, as well as to whomever moved this thread to the correct spot.

---

### Post by Vaphell on 2011-10-12
finding offending lines shouldn't be too hard, naive approach from the top of my head
```
while IFS= read line; do echo "${#line}"; done < source.file > source_lenghts.txt
while IFS= read line; do echo "${#line}"; done < modified.file > modified_lenghts.txt
diff source_lenghts.txt modified_lenghts.txt

```
lines where lengths don't match are the lines where regex fails.

also consider producing small sample files for testing purposes (few k lines) so you don't have to test your regexes on few million long source file.

---

### Post by CaKiwi on 2011-10-13
To change only the fields bracketed by " <" and "> ", add spaces in the -F and the print
```
gawk -F"( <|> )" '/<.*>/ {gsub(/ /,"_",$2);print $1 " <" $2 "> " $3;next}1' file1 > file2
```

Maybe the different file sizes is due to different EOL characters

Check by using ```
od -c file1 | head
od -c file2 | head
```

Use Vaphell's suggestion to check line lengths or use gawk
```
gawk '{print NR,length}' file1 > l1
gawk '{print NR,length}' file2 > l2
diff l1 l2
```

---

### Post by craigbennet3 on 2011-10-13
Well I am certainly learning new things here! Thank you all.

First, my apologies to everyone because I failed to mention that I did take the first hundred lines from one of the files for testing purposes. Naturally everything works fine with it. File size remains the same from one to the other, and the substitutions are performed as expected. I  will be happy to supply whatever is asked for if anyone needs additional examples. I did modify the data in my original post so that any identifying info was set to a generic value.

[SIZE=2]**CaKiwi**[/SIZE],
That was my first thought, and I thought I tried that before replying back, but I am getting completely different results today, so I have no idea what I did yesterday. But that brings the file size difference down to 39 bytes, and thanks to Vaphell's script I think I see where the problem is. The field delimiters can be applied in either order, so a line that contains "> some_characters <" is matching as well as " < some_characters >". Is there a way to apply the delimiter so that it only matches "> " if preceded by " <"? (Again quotes only used for clarity) One of the before and after lines are included below:

Original:
```
1316546839.560 139 10.200.81.126 TCP_MISS/200 988 GET http://www.msnbc.msn.com/proxy/proxy.asmx/GetWSXml?DestinationKey=VideoRadCall&Passkey=&Parameters=<params><param><name>GetAd</name><value></value></param><param><name>PG</name><value>msv8bt</value></param><param><name>cachebust</name><value>10169.08794486735</value></param></params> "DC\JohnDoe@dc.com" DIRECT/www.msnbc.msn.com text/xml DEFAULT_CASE_11-DC_Default_Policy-DC_Default_Identity-NONE-NONE-NONE-DefaultGroup <IW_news,5.9,"1","-",-,-,-,"-","-",-,-,-,"-","-",-,"-","-",-,-,IW_news,-,"-","-","Unknown","Unknown","-","-",56.86,0,-,"-","-"> -
```Modified:
```
1316546839.560 139 10.200.81.126 TCP_MISS/200 988 GET http://www.msnbc.msn.com/proxy/proxy.asmx/GetWSXml?DestinationKey=VideoRadCall&Passkey=&Parameters=<params><param><name>GetAd</name><value></value></param><param><name>PG</name><value>msv8bt</value></param><param><name>cachebust</name><value>10169.08794486735</value></param></params <"DC\JohnDoe@dc.com"_DIRECT/www.msnbc.msn.com_text/xml_DEFAULT_CASE_11-DC_Default_Policy-DC_Default_Identity-NONE-NONE-NONE-DefaultGroup> IW_news,5.9,"1","-",-,-,-,"-","-",-,-,-,"-","-",-,"-","-",-,-,IW_news,-,"-","-","Unknown","Unknown","-","-",56.86,0,-,"-","-"
```**[SIZE=2]Vaphell[/SIZE]**,
Your script to get the line lengths takes 20 minutes to run, which tells me I definetly do not want to use a bash script to do my modifications!

Again, THANKS to everyone for their time!

---

### Post by gmargo on 2011-10-13
> **craigbennet3 said:**
> gmargo - Unfortunately one of the other fields is a URL, and it can contain < and > characters. It will not contain, to the best of my knowledge either string " <" or "> ".


It is simple to adjust the bracket string in the perl script:
```

#!/usr/bin/perl -w
use strict;
use warnings;

while (my $line = <>)
{
    if ($line =~ /^(.*?) <([^>]+)> (.*)/s)
    {
        my ($lead, $bracketed, $rest) = ($1,$2,$3);
        $bracketed =~ s/ /_/g;
        print "$lead"." <".$bracketed."> ".$rest;
    }
    else
    {
        print $line;
    }
}

```Here is an alternative idea.  Instead of looking for ' <','> ', try looking for double-quoted phrases, and space-escape them:
```

#!/usr/bin/perl -w
use strict;
use warnings;

while (my $line = <>)
{
    my ($lead, $bracketed, $rest) = ("","",$line);
    while ($line =~ /([^"]*)"([^"]*)"(.*)/s)
    {
        ($lead, $bracketed, $rest) = ($1,$2,$3);
        $bracketed =~ s/ /_/g;
        print "$lead".'"'.$bracketed.'"';
        $line = $rest;
    }
    print $rest;
}

```

---

### Post by Vaphell on 2011-10-13
well, bash is a flexible, all around tool, not specialized in particular tasks. I suspected there can be a performance hit because of that, but I didn't think it is that bad :) So it appears once again that picking the right tool for the job is half of success :)
out of curiosity, how long does awk way of getting line lengths take?

---

### Post by craigbennet3 on 2011-10-13
I agree - I've never found anything that couldn't be done with bash (or csh/ksh for that matter). I would just assume that bash would be the slowest, gawk faster, and sed the fastest, which is why I wanted to go with sed. Being a stream editor I would assume it would be limited by disk access speed, but regular expression back references should play a factor as well (my gut feeling).

FWIW, "gawk '{print NR,length}' file1 > l1" takes about three minutes. The file has 3,729,646 lines in it, and that's the small one. The largest one I have is 6.5 GB with 15,427,836 lines, and I'm told these files can be up to 10 GB in size. Gonna be one huge table. I may be able to convince the powers that be to break them up into a table per week or per month. In fact we may have to...

---

### Post by CaKiwi on 2011-10-13
Here's another attempt, very lightly tested
```
{
  i=match($0," <") 
  if(i==0) {print;next}
  printf substr($0,1,i)
  a1=substr($0,i+1)
  i=match(a1,"> ")
  if(i==0) {print a1;next}
  a2=substr(a1,1,i)
  gsub(/ /,"_",a2);
  print a2 substr(a1,i+1)
}

```

---

### Post by craigbennet3 on 2011-10-15
Thanks CaKiwi,

I just wanted to let y'all know that I will be out until 26 October, so I may not get a chance to test this. I will have remote access, but not sure if I will have time. I will definitely get back in touch, but wanted you to know that I am not ignoring you.

Craig

---

### Post by craigbennet3 on 2011-10-26
Hi **CaKiwi**

I am back, and getting back into this. I'm not sure I understand your last post. Is that a bash script, or is it a gawk action string? Either way I'm not sure how to implement it.

Thanks,
Craig

---

### Post by CaKiwi on 2011-10-27
It's gawk program. You can use it as a a gawk action string by making it into 1 line and placing a ; at the end of each statement. Or put it in a file, prog.awk say, and run it with
```
gawk -f prog.awk file1 > file2
```

---

### Post by craigbennet3 on 2011-11-17
Hi CaKiwi,

I'm afraid that one gives me an error after processing several hundred lines: "fatal: not enough arguments to satisfy format string" The line is then output to the screen, but it is truncated, with the field it seems to indicate as being the one that caused the error shown, and the subsequent field missing from the output. Yet, in the file, that line does contain the proper amount of fields, as does all surrounding lines.

On a completely different note, I was given access to the system that generates these access logs, and I was able to create a custom output template. So I have negated my need for this regular expression, although I would still like to know how to solve this problem. But I'm behind as it is, so I probably won't get to devote too terrible much time to it, as can be seen by the tardiness of this reply.

BTW, so far for the month of November, as of midnight local time, I have 22,586,738 records. These are gonna be some big tables!

CaKiwi, I really appreciate you sticking with me on this, and I hate to abandon this as unfinished, but I don't have much choice. I hope to be able to repay you in kind some day.

Thanks,
Craig

---

### Post by CaKiwi on 2011-11-17
I guess this is of only academic interest now but if you post the line of your file in question and a few lines on either side I will take a look at it.

---

