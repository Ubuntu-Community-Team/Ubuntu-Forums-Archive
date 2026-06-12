---
title: "Removing trailing comma"
date: 2010-06-08
forum: Programming Talk
---

### Post by hannaman on 2010-06-08
I have a command that gets information on a user account from a database and displays it similar to this format:

```
U   A    O     Username      Profilename     Some other text
_   _    _     ________      ___________     _______________
U   A    O     user          profile_1       junk.junk.junk
U   A    O     user          profile_2       I don't care
Returned number something

```
I want to feed the profile names to another command that takes a comma separated list of profiles.  I am able to get the list, but awk statement:
```
*command* | awk '$4 ~ /*user*/ { print $5 }{ OFS="," }'
```
I get the list with a trailing comma like:
```
profile_1,profile_2,
```
I have been able to remove the trailing comma with sed using:
```
*command* | awk '$4 ~ /*user*/ { print $5 }{ OFS="," }' | sed 's/,*$//'
```
Even though this works, sed complains of a "missing newline at end of standard input".
I have tried to remove the trailing comma with awk using either sub or gensub, but I have been unsuccessful.
Does anyone know of a cleaner way of getting a comma separated list without the trailing comma like this?

Thanks

---

### Post by hannaman on 2010-06-08
OK, I got this work but it is a little ugly:
```
*command* | awk '$4 ~ /*user*/ { print $5 }{ OFS="," }' | awk 'sub(/,+$/,"")'
```

I would like to do this with a single awk statement, but it works and doesn't spit out any errors.

---

### Post by trent.josephsen on 2010-06-08
> **hannaman said:**
> OK, I got this work but it is a little ugly:
```
*command* | awk '$4 ~ /*user*/ { print $5 }{ OFS="," }' | awk 'sub(/,+$/,"")'
```

I would like to do this with a single awk statement, but it works and doesn't spit out any errors.

In Perl you could do
```
*command* | perl -nae 'push @ary, $F[4] if $F[3] =~ /user/; END { print join(",", @ary), $/ }'
```

Perhaps an Awk guru can suggest how to achieve the same in that language (probably more concisely).

---

### Post by Compyx on 2010-06-08
Unfortunately awk doesn't have a join() function, although it has a split() function.

I'd do something like this, similar to the perl version: I store the profiles in an array and then print all elements, except the last, with a comma attached and then print the last element without the comma attached (simulating a join() function):
```

command | awk \
    '$4 ~ /user/ { p[i++] = $5 } \
     END { for (k = 0; k < i - 1; k++) { printf "%s,", p[k] } print p[k] }'

```

It's ugly, but it's a single awk invocation ;)

---

### Post by geirha on 2010-06-08
You are currently using a regex to match the username, I'm guessing you really want to do a string comparison instead. $4 ~ /user/ will match "user", "userA" and "superuser" etc. If you compare it as two strings instead, it will only match "user": ```
awk '$4 == "user" { ... }'
```

---

### Post by DaithiF on 2010-06-08
no neater than the preceding solutions, but for variety:
```
command | awk '$4 == "user" { print $5}' | sed -e :a -e 'N;s/\n/,/;ta'
```

---

### Post by hannaman on 2010-06-08
> **geirha said:**
> You are currently using a regex to match the username, I'm guessing you really want to do a string comparison instead. $4 ~ /user/ will match "user", "userA" and "superuser" etc. If you compare it as two strings instead, it will only match "user": ```
awk '$4 == "user" { ... }'
```

Thanks for that information.  Since the command that I run only shows information for the user that I specify, I am only matching the username to exclude header and footer data.

---

