---
title: "Tunnel trouble"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by thechosenone2 on 2014-10-23
Hi! I've encountered on the some problems while reading the book about Ubuntu " Robin Nixon - Ubuntu Up and Running ". Shortly speaking,It concerns using the terminal:
  He gives the following examples of bash code:
 1)
     **find / -name qwert*  **// This instructions should seek for any files which names contain the letters 'qwert'. In my terminal It does not actually work:
[IMG]http://s017.radikal.ru/i401/1410/98/aeb289023650.png[/IMG]

2) Then he teaches how to use the "tunnel" and gives the following ex:
    
    **find / -name qwerty | more **  //Here he says that it leads to the next result: Firstly 'find' finishes it's job and shows all err-messages, Then all useful information (stdout) passes to the 'more' and then more displays the useful information (if it exist). But I have the result that differs from what he says: stdout appears among the err-messages. 
[IMG]http://s49.radikal.ru/i125/1410/b7/9282f87fa894.png[/IMG]



Please,explain me how It really should be. Thanks.

---

### Post by steeldriver on 2014-10-23
Either you're misreading the book, or it's not very good

In the first case, the failure to quote the search string **qwe*** has  allowed the shell to expand it as a file glob - so it's matching a file called **qwerty~ **that happens to be in the current directory. You should always quote such expressions when using the find command e.g.

```

find / -name "que*"

```
or
```

find / -name 'que*'

```

The second issue is the choice of the filesystem root directory / as the starting point for the search - if you'd searched starting from somewhere in your home directory (which you own) you wouldn't have permission problems like those e.g.

```

find **~**/ -name "que*" | more

```

BTW **|** represents a **pipe** not a tunnel (the terminology is important - the word **tunnel** is used for something else)

---

