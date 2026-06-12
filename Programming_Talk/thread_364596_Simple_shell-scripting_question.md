---
title: "Simple shell-scripting question"
date: 2007-02-18
forum: Programming Talk
---

### Post by shandar on 2007-02-18
Hey guys, I have a simple problem that I can't find a solution for. 

I am writing a simple script to download multiple RapidShare files at once (yes, I have an account) by downloading the premium download webpage using curl. I want to filter out only the links that start with [http://rs*](http://rs*)
I've tried to do a simple grep [http://rs*](http://rs*) but it gives me the full line of every link, I just need to find the addresses. Any ideas how this can be done?

This is what I get now:
```
<p><table border="0" cellpadding="5" cellspacing="0"><td><b>Available sources</b></td><td><b>Bandwidth in use</b></td><tr><td>
<a href="http://rs59cg.rapidshare.com/files/16157060/dl/test.rar">Download via Cogent</a></td><td><font color="green">7625</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59tl2.rapidshare.com/files/16157060/dl/test.rar">Download via TeliaSonera #2</a></td><td><font color="green">7605</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59l32.rapidshare.com/files/16157060/dl/test.rar">Download via Level(3) #2</a></td><td><font color="green">7423</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59l33.rapidshare.com/files/16157060/dl/test.rar">Download via Level(3) #3</a></td><td><font color="green">7867</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59gc.rapidshare.com/files/16157060/dl/test.rar">Download via GlobalCrossing</a></td><td><font color="green">5952</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59tg.rapidshare.com/files/16157060/dl/test.rar">Download via Teleglobe</a></td><td><font color="green">5197</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59tl.rapidshare.com/files/16157060/dl/test.rar">Download via TeliaSonera</a></td><td><font color="green">8008</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59cg2.rapidshare.com/files/16157060/dl/test.rar">Download via Cogent #2</a></td><td><font color="red">9073</font> / 10000 MBit/s</td></tr><tr><td>
<a href="http://rs59l3.rapidshare.com/files/16157060/dl/test.rar">Download via Level(3)</a></td><td><font color="green">7646</font> / 10000 MBit/s</td></tr></table></p>
```And this is what I'd like to get:
```

http://rs59cg.rapidshare.com/files/16157060/dl/test.rar
http://rs59tl2.rapidshare.com/files/16157060/dl/test.rar
http://rs59l32.rapidshare.com/files/16157060/dl/test.rar
```

---

### Post by LotsOfPhil on 2007-02-18
```

#!/usr/bin/perl
$file = 'file.txt';
$file = $ARGV[0];
open(infile, "<$file") or die "Cannot open $!";
@contents = (<infile>);
close(infile);
open(outfile, ">$file") or die "Cannot open $!";
                                                                                
foreach $line (@contents) {
        chomp($line);
        if($line =~ /http/){
                $line =~ s/<a href="//;
                $line =~ s/">.*//;
        }
        print outfile "$line\n";
}
                                                                                
close(outfile);

```

---

### Post by LotsOfPhil on 2007-02-18
This assumes that your stuff is in a file and then overwrites that file.

---

### Post by lloyd mcclendon on 2007-02-18
awk is a little better suited for this,

cat <that file> | awk -F '"' ' /.*http:\/\/rs.*/{ print $2 } '

that uses the double quote as the field seperator, goes through each line and if it has the pattern [http://rs](http://rs) then it prints the 2nd field, the url which starts after the first quote and ends with the second.

---

