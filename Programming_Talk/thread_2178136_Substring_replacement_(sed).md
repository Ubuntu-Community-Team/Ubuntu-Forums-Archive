---
title: "Substring replacement (sed?)"
date: 2013-10-02
forum: Programming Talk
---

### Post by OrangeMadness on 2013-10-02
Hello,

I need to keep account of a few IP addresses in a text file.

The format of the text file is:


```
0433:10.20.30.1
0435:10.20.30.2
0439:10.20.30.3
```

I need to be changing, say, 0435 to 10.20.30.10
Closest I could get is replacing the whole second line but this is not fixed, 0435 could some day be found in the 5th.

How can I ask the replacement of the line which starts with 0435, to the new line 0435:10.20.30.10 ?

Thanks in advance

---

### Post by Vaphell on 2013-10-02
```
sed '/^0435/ s/:.*/:10.20.30.10/'
```

---

### Post by OrangeMadness on 2013-10-03
Your command works perfectly, thanks

I have been playing a little bit with this, for sakes of learning  - using this tool: [http://regexpal.com/](http://regexpal.com/)

By using the regular expression:

\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b

I do get a match for the IP address, so shouldnt 
```

sed '/^0435/ s/\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b/:10.20.30.10/' 

```
also work ? It doesn't!

---

### Post by Vaphell on 2013-10-03
it works fine but not with sed. Different tools are on different levels of evolution when it comes to regex support :)

grep with perl flavor of regexes which is the most beefy of all
```
$ echo "0433:10.20.30.1
0435:10.20.30.2
0439:10.20.30.3" | grep -P '\b\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}\b'
0433:**10.20.30.1**
0435:**10.20.30.2**
0439:**10.20.30.3**
```

sed simply doesn't support \d class, you have to use [0-9] instead.
```
$ echo "0433:10.20.30.1
0435:10.20.30.2
0439:10.20.30.3" | sed -r '/^0435/ s/\b[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\b/10:20:30:10/'
0433:10.20.30.1
0435:10:20:30:10
0439:10.20.30.3
```

also sed behaves differently with and without -r parameter. sed by default treats many regex syntax characters ( {}()+| ) as ordinary ones, eg
```
$ echo abc | sed 's/([a-c])+/=/g'  # does nothing because ()+ are treated literally
abc
$ echo abc | sed 's/\([a-c]\)\+/=/g'  # works because ()+ are escaped which switches them to regex meaning
= 
$ echo abc | sed -r 's/([a-c])+/=/g'   # works because -r switches ()+ to regex meaning, escaping will make them literal 
=
```
-r simply makes expressions cleaner if you go beyond basics.

---

### Post by OrangeMadness on 2013-10-17
Returning but to this post to refresh my memory when I need to sort something out with sed.
This post and regexpal.com with the quick reference is all i need for my simple tasks :)

Thank you, your kung fu is strong!

---

