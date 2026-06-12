---
title: "Commandline Perl and Newlines"
date: 2009-03-16
forum: Programming Talk
---

### Post by Hase on 2009-03-16
Trying to get a list of domains from some logs. 

Why does this print the data I want but no line breaks: 

```
cat LOGFILE | perl -ne 'print m!(https?://[^/]+)!'
```
 

And this prints line breaks but only the character “1” (yes, I know it matches...) on each line:

```
cat LOGFILE | perl -ne 'print m!(https?://[^/]+)!."\n"'
```

I can do this but why does the behavior change between the first two?:

```
cat LOGFILE | perl -ne 'print m!(https?://[^/]+)!; print "\n"'
```

---

### Post by unutbu on 2009-03-16
When you say
```

print m!(https?://[^/]+)!
```

print can take a list of arguments, so "m!(https?://[^/]+)" is called in an array context.
So "m!(https?://[^/]+)" returns an array whose elements are all the parenthetical groups with matches. Since your regexp has only one parenthetical group, it returns an array with only one element.

print then concatenates all the elements in the array.

In the second command, 
```

print m!(https?://[^/]+)!."\n"

```

"m!(https?://[^/]+)!" is concatenated with the string "\n". Only scalars can be concatenated with strings. So "m!(https?://[^/]+)!" is now being called in a scalar context. In a scalar context the match operator returns true (1) if a match has been found, and returns false (0) otherwise. 

You could fix the second command by using a comma (to make a list) instead of a period (concatentation operator):```


cat LOGFILE | perl -ne 'print m!(https?://[^/]+)!,"\n"'
```

---

