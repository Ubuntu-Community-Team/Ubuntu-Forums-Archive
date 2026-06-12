---
title: "String extraction."
date: 2009-07-30
forum: Programming Talk
---

### Post by kodalisrikanth on 2009-07-30
Hi,

I have some problem with extracting the text from the logs.
Here is the log file looks like.

linenumber:INFO |Date|time|name|s=sessionid>..garbage.
[COLOR="Red"]Example:
69736:INFO |2009/07/17|15:26:59|p=Helloworld|s=A376B050AD83524106D7023 F45233DD> Session "A376B050AD83524106D7023F45233DD" created.[/COLOR]

Here,
Linenumber values are 1,2,3 ...etc
INFO,Date,time,sessionid are fixed size.
name is variable size.

I want to retrieve all the fields(Line number, Date, Time, Sessionid from this log file)


work done:
Tried awk,
[COLOR="Red"]grep -n 'created\|disposed' /opt/tomcat/logs/catalina.out | awk '{print $1}'[/COLOR]
But, this is giving the output in this format.
Linenumber:INFO

I tried with print$2,$3 .. but no luck.

Please help me out.


Thanks,
Srikanth.

---

### Post by unutbu on 2009-07-30
Save this in ~/bin/parse_log.py
[PHP]#!/usr/bin/env python
__usage__='''
test.py < /opt/tomcat/logs/catalina.out
echo '69736:INFO |2009/07/17|15:26:59|p=Helloworld|s=A376B050AD83524106D7023 F45233DD> Session "A376B050AD83524106D7023F45233DD" created.' | test.py
'''
import sys
for line in sys.stdin:
    ln_info,date,time,name,session=line.split('|')
    ln,info=ln_info.split(':')
    name=name[2:]
    sessionid=session.split('>')[0][2:]
    print ln,info,date,time,name,sessionid
    
[/PHP]
Make it executable:
[PHP]chmod 755 ~/bin/parse_log.py[/PHP]

Run it like this:

[PHP]test.py < /opt/tomcat/logs/catalina.out[/PHP]

---

### Post by kodalisrikanth on 2009-07-30
Yahooooooooooooooooooo ..

It is working .. thank you very much for your help. I am trying to work it on shell script. But, this worked for me. Thanks alot. 

I am trying this from morning. Thanks once again.

Srikanth.

---

### Post by ibuclaw on 2009-07-30
Sorry, couldn't resist. :)

This will do the exact same job.

```

#!/usr/bin/env perl

use strict;
use warnings;

my @files = @ARGV;

if(@files)
{
    foreach my $file (@files)
    {
        open FILE, "< $file" or warn "Can't open $file: $!";
        next if $@;
        process_file(\*FILE);
        close FILE;
    }
}
else
{
    process_file(\*STDIN);
}

sub process_file
{
    my ($fh) = @_;
    while(my $line = <$fh>)
    {
        my ($ln_info,$date,$time,$name,$session) = split /\|/, $line;
        my ($ln,$info) = split ':', $ln_info;
        my $sessionid = (split '=', (split '>', $session)[0])[1];
        $name = (split '=', $name)[1];

        print "$ln $info $date $time $name $sessionid\n";
    }
}

```

Usage is:
```
parse_log.pl [file1 ...]
cat [file1 ...] | parse_log.pl
parse_log.pl < stdin

```

Regards
Iain

---

### Post by ghostdog74 on 2009-07-30
> **kodalisrikanth said:**
> 
work done:
Tried awk,
[COLOR="Red"]grep -n 'created\|disposed' /opt/tomcat/logs/catalina.out | awk '{print $1}'[/COLOR]
But, this is giving the output in this format.
Linenumber:INFO

I tried with print$2,$3 .. but no luck.

Please help me out.


Thanks,
Srikanth.
that's because you didn't specify a field delimiter.
also, no need to use grep when you use awk

```

awk  'BEGIN{FS="[|]|[ ]"}
/created/{
    sub(/:.*/,"",$1)
    print $1,$3,$4,$(NF-1)
}'  OFS="|" file


```

---

### Post by kodalisrikanth on 2009-08-01
Thank you very much for your response. I really appreciate that. :):)

---

