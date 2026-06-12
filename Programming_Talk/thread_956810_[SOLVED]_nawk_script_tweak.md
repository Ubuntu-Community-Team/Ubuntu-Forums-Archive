---
title: "[SOLVED] nawk script tweak"
date: 2008-10-23
forum: Programming Talk
---

### Post by onytz on 2008-10-23
Hello all,
I have a nawk script giving me almost the results I want. 
I call it from the command-line with:

	```
 nawk -f xmlSR.awk args.xml
```
	 
args.xml is:
	
	[HTML]<figure><graphic url="foo1.bar"/></figure>:<figure rend="big"><graphic url="foo1.bar"/></figure>
<figure><graphic url="foo2.bar"/></figure>:<figure rend="big"><graphic url="foo2.bar"/></figure>[/HTML]
    
xmlSR.awk is:

	```
BEGIN {FS=":";n=1
	while (getline<"source.xml">0)
		line[n++]=$0
	}
	{for (i=1; i<n; i++) {
		temp=line[i]
		gsub($1, $2, temp)
		print temp}
	}
```	
and source.xml is:

	[HTML]<root>
 <parent><child/></parent>
 <parent><figure><graphic url="foo1.bar"/></figure></parent>
 <parent><figure><graphic url="foo2.bar"/></figure></parent>
 <parent><figure><graphic url="foo3.bar"/></figure></parent>
 <parent><figure><graphic url="foo4.bar"/></figure></parent>
</root>[/HTML]
	
When I invoke the script, I get the following output:

	[HTML]<root>
 <parent><child/></parent>
 <parent><figure rend="big"><graphic url="foo1.bar"/></figure></parent>
 <parent><figure><graphic url="foo2.bar"/></figure></parent>
 <parent><figure><graphic url="foo3.bar"/></figure></parent>
 <parent><figure><graphic url="foo4.bar"/></figure></parent>
</root>
<root>
 <parent><child/></parent>
 <parent><figure><graphic url="foo1.bar"/></figure></parent>
 <parent><figure rend="big"><graphic url="foo2.bar"/></figure></parent>
 <parent><figure><graphic url="foo3.bar"/></figure></parent>
 <parent><figure><graphic url="foo4.bar"/></figure></parent>
</root>[/HTML]
	
But all I want is one root element with the two modified figure elements as its children, like so:

	[HTML]<root>
 <parent><child/></parent>
 <parent><figure rend="big"><graphic url="foo1.bar"/></figure></parent>
 <parent><figure rend="big"><graphic url="foo2.bar"/></figure></parent>
 <parent><figure><graphic url="foo3.bar"/></figure></parent>
 <parent><figure><graphic url="foo4.bar"/></figure></parent>
</root>[/HTML]
	
In English, I want to do a single search and replace on source.xml using all the colon-separated fields in args.xml. Any suggestions? Thanks in advance!

---

### Post by ghostdog74 on 2008-10-23
```

awk 'BEGIN{FS=":"}
FNR==NR{
    org=$2
    sub(/.*url=\"/,"",$2)
    sub(/\"\/><\/figure>/,"",$2)
    _[$2]=org    
  next
}
/url=/{    
    o=$0
    sub(/.*url=\"/,"")
    sub(/\"\/><\/figure>.*$/,"")
    if ( $0 in _ ){
        print "<parent><figure>" _[$0] "</parent>"
    }else{
        print o
    }
    next
}1
' args.xml source.xml

```
output:
```

 # ./test.sh
<root>
 <parent><child/></parent>
<parent><figure><figure rend="big"><graphic url="foo1.bar"/></figure></parent>
<parent><figure><figure rend="big"><graphic url="foo2.bar"/></figure></parent>
 <parent><figure><graphic url="foo3.bar"/></figure></parent>
 <parent><figure><graphic url="foo4.bar"/></figure></parent>
</root>



```

---

### Post by onytz on 2008-10-24
Thanks!

---

