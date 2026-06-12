---
title: "How to grep multiple lines at once"
date: 2007-10-19
forum: Programming Talk
---

### Post by flummoxed on 2007-10-19
Hi, I'm trying to grep an HTML file that has links to several downloads. An example of a link looks like this:

```
 Download: <a class="ulink" href=
"http://ftp.gnu.org/gnu/binutils/binutils-2.17.tar.bz2">http://ftp.gnu.org/gnu/binutils/binutils-2.17.tar.bz2</a>
```

So I want to grep for things starting with 

```
 Download: <a class="ulink" href= "http://*"
```

but since the download beginning is on a different line, I can't seem to do it. Is there any way to get grep to search for concatenated
strings or something like that?

Thanks

---

### Post by slavik on 2007-10-19
use perl or pythong to write a script, grep processes input line by line.

---

### Post by flummoxed on 2007-10-19
I was already working on a Python script, but I was wondering if grep could do some magic. I guess not, lol.

Anyways, I've figured out how to do it in Python. But now my dilemma is I want to remove all the crap, other than the URL. Every download link is different, so I can't just use rstrip() and lstrip() to remove generic stuff. Is there any way to use wildcards in python? Like... remove all text from this point to that point, type thing?

---

### Post by ghostdog74 on 2007-10-19
```

awk '/Download/&&$0!~/http/{
       getline l;
       start=index(l,">")
       end = index(l,"<")
       print substr(l,start+1,end-start-1)
    }' "file"

```
output:
```

# ./test.sh
http://ftp.gnu.org/gnu/binutils/binutils-2.17.tar.bz2


```


direct conversion to Perl:

```

while (<>) {
    chomp;    
    if (/Download/ && $_ !~ /http/) {
		if ($getline_ok = (($_ = <>) ne '')) {
			chomp; 
		}
        $l = $_;
        $start = index($l, '>');
        $end = index($l, '<');
        print substr($l, $start + 1, $end - $start - 1);
    }
}

```

---

### Post by geirha on 2007-10-19
For HTML you could consider using the HTMLParser. Maybe something like this?

```

from HTMLParser import HTMLParser

class MyHTMLParser(HTMLParser):
    def __init__(self):
        HTMLParser.__init__(self)
        self.getanchor= False
    def handle_data(self, data):
        if 'Download: ' in data:
            self.getanchor= True
    def handle_starttag(self, tag, attrs):
         if self.getanchor and tag == 'a':
             print dict(attrs)['href']
             self.getanchor= False

if __name__ == '__main__':
    parser= MyHTMLParser()
    parser.feed( file('foo.html').read() )

```

grep -A1 will display the matching line plus 1 line after that one. So using multiple greps is possible too.

---

### Post by slavik on 2007-10-19
the perl version:

```

print $_."\n" for(join('',<>) =~ /href=\"(.*?)\"/g);

```

---

### Post by ronocdh on 2009-10-26
I know I'm resurrecting a dead thread here, but try this format:
```
**command1** | grep "**x**\\|**y**\\|**z**"
```
E.g.
```
di | grep "Filesystem\\|md\\|mnt"
```

---

### Post by ghostdog74 on 2009-10-26
> **ronocdh said:**
> I know I'm resurrecting a dead thread here, but try this format:
```
**command1** | grep "**x**\\|**y**\\|**z**"
```
E.g.
```
di | grep "Filesystem\\|md\\|mnt"
```

and how does that solve the problem? please look at first post to see the problem description. don't bump up a thread and not solve the problem.

---

### Post by xir_ on 2009-12-09
> **ronocdh said:**
> I know I'm resurrecting a dead thread here, but try this format:
```
**command1** | grep "**x**\\|**y**\\|**z**"
```
E.g.
```
di | grep "Filesystem\\|md\\|mnt"
```

Brilliant this helped me loads. Thanks

---

### Post by bkuebler on 2011-04-11
> **ronocdh said:**
> I know I'm resurrecting a dead thread here, but try this format:
```
**command1** | grep "**x**\\|**y**\\|**z**"
```
E.g.
```
di | grep "Filesystem\\|md\\|mnt"
```
Now it's my turn to resurrect a dead thread, but this helped me out greatly as well...

---

### Post by bashologist on 2011-04-12
I write download scripts like every week. I love doing this so I gotta try.
```
perl -0 -n -e 'print "$_\n" foreach /Download:\s*<a.*?href=\n?"(.*?)"/isg' test.txt
```
Wrote that in just a few seconds.

You could then pipe the output to wget if the output looks like what you're wanting.
```
perl -0 -n -e 'print "$_\n" foreach /Download:\s*<a.*?href=\n?"(.*?)"/isg' test.txt | wget -i -
```

---

### Post by slavik on 2011-04-13
Should've been closed in 2009 ...

---

