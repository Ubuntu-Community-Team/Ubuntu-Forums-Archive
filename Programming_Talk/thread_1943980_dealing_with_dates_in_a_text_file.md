---
title: "dealing with dates in a text file"
date: 2012-03-20
forum: Programming Talk
---

### Post by dunryc on 2012-03-20
hi guys im trying to write a bash script that grabs expired domain names it leaves me with the following outpiut in a text file 

> 
1, [www.test.com](www.test.com) Expiration Date:17-jun-2013
2, [www.test.net](www.test.net) Expiration Date:29-mar-2013
3, [www.test.org](www.test.org) Expiration Date:26-Jul-2012 04:00:00 
4, [www.test.biz](www.test.biz)  Expiration Date:Mar 26 23:59:59  2012
5, [www.test.info](www.test.info) Expiration Date:27-Jul-2012 07:56:43 



Im hoping to try to normalise all the dates to the format displayed in the first 2 lines and remove the times so the file looks unfirom can any one give me a heads up ? 

Thanks for looking

---

### Post by codemaniac on 2012-03-20
The below would remove all the time stamps from the input file date.dat

```
sed 's/[0-9][0-9]:[0-9][0-9]:[0-9][0-9]//g' date.dat
```

---

### Post by Vaphell on 2012-03-20
your example
```
$ echo "1, www.test.com Expiration Date:17-jun-2013
2, www.test.net Expiration Date:29-mar-2013
3, www.test.org Expiration Date:26-Jul-2012 04:00:00
4, www.test.biz Expiration Date:Mar 26 23:59:59 2012
5, www.test.info Expiration Date:27-Jul-2012 07:56:43"\
| sed -r 's/[0-9]{2}:[0-9]{2}:[0-9]{2}//'\
| while read ln
do
  txt=${ln%:*}
  dt=${ln#*:}
  echo $txt: $( date -d "$dt" '+%d %b %Y' )
done

1, www.test.com Expiration Date: 17 Jun 2013
2, www.test.net Expiration Date: 29 Mar 2013
3, www.test.org Expiration Date: 26 Jul 2012
4, www.test.biz Expiration Date: 26 Mar 2012
5, www.test.info Expiration Date: 27 Jul 2012
```

if you have that data in file go with
```
while read ...
do
...
done < <( sed -r ... input_file )
```

cosntruct the date format you want, you can find format options with **date --help **

---

