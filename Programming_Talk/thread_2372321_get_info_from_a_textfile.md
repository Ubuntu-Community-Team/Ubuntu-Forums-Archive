---
title: "get info from a textfile"
date: 2017-09-23
forum: Programming Talk
---

### Post by cazz on 2017-09-23
Hi, I have got a new TP-Link HS110 that I was going to monitor how much power a computer use.

With a script I get alot of information that save to a text file 

The textfile look like this.

```
"emeter":{"get_realtime":{"current":1.539196,"voltage":231.709784,"power":343.191153,"total":0.113000,"err_code":0}}}
```

That only thin I need is "343.191153" to save it in a MySQL database with timestamp

I guess I can use regex but I'm not good in that and have try to use it before with no luck.

can someone help me how to get that information I need to a variable in bash

---

### Post by steeldriver on 2017-09-23
Are you sure it doesn't begin with a left brace? that would make it valid json I think - allowing you to use `jq` i.e. given

```

$ cat file
{"emeter":{"get_realtime":{"current":1.539196,"voltage":231.709784,"power":343.191153,"total":0.113000,"err_code":0}}}

```

then

```

$ cat file | jq '.emeter.get_realtime.power'
343.191153

```

or

```

$ var=$(cat file | jq '.emeter.get_realtime.power')
$ echo "$var"
343.191153

```

---

### Post by cazz on 2017-09-23
ohh thanks alot :D

---

### Post by The Cog on 2017-09-23
steeldriver is probably right about the leading { which would enable using jq. 
But if there is no leading { then here is a possible solution:
```
cat filename | grep -o '"power":[0-9.]*' | tr -dc '0-9.'
```
It uses grep to pick out "power": followed by number, then passes this through tr which deletes all non-numeric characters.

---

### Post by cazz on 2017-09-23
Ahh thanks good to know that :)

---

### Post by steeldriver on 2017-09-23
. . . or you could use grep's Perl Compatible regular Expression (PCRE) mode

```

grep -oP '"power":\K[\d.]+' filename

```

---

### Post by The Cog on 2017-09-23
And I finally found a sed one:
```
sed -E 's/.*"power":([0-9.]*).*/\1/' filename
```

---

