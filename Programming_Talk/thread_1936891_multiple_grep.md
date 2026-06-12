---
title: "multiple grep?"
date: 2012-03-06
forum: Programming Talk
---

### Post by conradin on 2012-03-06
Hi Everyone,
I have a script that gives me host name info based on nslookup, the script works fine, but I need to narrow down what the results are. (brief example below:) Basically, Im looking for strings with the word "maine" in them as is, which I already know is every host in the range. However, I dont necessarily want every host in the range. 
What I would like to do is look for hosts with "maine" and "hp*", or "maine" and "cam*" in the hostname, and exclude everything else. But Im not really sure how to do that. 
What I dont want to do is re-scan the network, for alternate matching hosts. Though that would work it would also be slow, and probably unnecessary. 

Any thoughts, or helpful hints would be much appreciated.








```

#!/bin/bash
touch local
masq=130.111.218.
for i in `seq 0 255`;
do 
nslookup  $masq$i | grep maine >> local
done


```

---

### Post by conradin on 2012-03-07
lol, ok, I got this. 
evidently grep hasn't an AND operator. oh well. 
This site I found useful:
[http://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/](http://www.thegeekstuff.com/2011/10/grep-or-and-not-operators/)

and my script looks like this now:

```

#!/bin/bash
touch prNcams
masq=130.111.218.
	for i in `seq 0 255`;
	do 
	nslookup  $masq$i | grep -E 'hp.*maine|cam.*maine' >> prNcams
done

```

As always, if anyone has something better I would still love to hear about it!
:)

---

