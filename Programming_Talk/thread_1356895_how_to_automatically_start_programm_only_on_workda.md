---
title: "how to automatically start programm only on workdays"
date: 2009-12-16
forum: Programming Talk
---

### Post by Eugene_Bondarenko on 2009-12-16
Hello,

The question is very noobish but I really need help with it since I don't have any experience with Linux programming and simply don't know basic things. 

I have lots of stuff in "startup applications". Some of that stuff requires tiny tricks to work perfectly. So for example I have to launch thunderbird like this "sleep 3 && thunderbird" because otherwise it starts retrieving emails before connection is established and thunderbird outputs a connection error for each my account.

Now I am trying to make pidgin run only on workdays. So when system starts, command should verify current day and run pidgin only if it's monday-friday today. I went googling and found "date +%u". Then I tried to apply my non-linux programming experience and came up with this
```

(date +%u)==6 || (date +%u)==7 || pidgin

```
but had no luck. Could you please help me with this.

---

### Post by apmcd47 on 2009-12-16
> **Eugene_Bondarenko said:**
> Hello,



Now I am trying to make pidgin run only on workdays. So when system starts, command should verify current day and run pidgin only if it's monday-friday today. I went googling and found "date +%u". Then I tried to apply my non-linux programming experience and came up with this
```

(date +%u)==6 || (date +%u)==7 || pidgin

```
but had no luck. Could you please help me with this.

Possibly try:```
[ $(date +%u) -eq 6 ] || [ $(date +%u) -eq 7 ] || pidgin
```
You missed off the dollar prefix - to get the output of a command you should put it inside a pair of parentheses prefixed with a dollar sign. The square brackets are the test command and numeric equality is -eq rather than == when using test.
I'd be inclined to do:
```
case $(date +%u) in
   6|7) echo no pidgin today ;;
   *)   pidgin ;;
esac
``` 
or maybe this one liner:
```
[ $(date +%u) -lt 6 ] && pidgin
```

Andrew

---

### Post by Eugene_Bondarenko on 2009-12-18
Thanks, it works great! Also thanks for going into details, this will help me write my next shell script by myself.

---

