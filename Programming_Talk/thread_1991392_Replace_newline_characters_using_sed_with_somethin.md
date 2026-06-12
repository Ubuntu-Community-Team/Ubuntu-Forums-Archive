---
title: "Replace newline characters using sed with something else."
date: 2012-05-30
forum: Programming Talk
---

### Post by YourSurrogateGod on 2012-05-30
Hello,

   I got the following file.
```
John
Bob
Tim
Alex
```
Using sed, I'd like to take that contents that I have with sed and turn it into the following:
```
John|\
Bob|\
Tim|\
Alex|\
```

Basically, take the newline character (\n\r, the file was created in Windows) and replace them with something slightly different.

This is the line of sed code that I'm using:
```
sed -e 's/\r\n/|\\\n/g' file.txt
```

Unfortunately, my little program there fails horribly and does not return anything at all.  I don't understand where I'm screwing up.  Any thoughts?

---

### Post by codemaniac on 2012-05-30
A simple awk version for you .
```
awk '{print $0 "|\\"} file.txt
```

---

### Post by papibe on 2012-05-30
> **codemaniac said:**
> ```
awk '{print $0 "|\\"} file.txt
```


awk considers \r part of the line so it does not remove it when printing:
```
awk '{print $0 "|\\"}' ./test.txt | od -a
0000000   J   o   h   n  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   B   o   b  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   T
0000020   i   m  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   A   l   e   x  [COLOR="Red"]**cr**[/COLOR]   |   \  nl
0000036

```
Replace '\n' with '$' in the sed command:
```
sed -e 's/\r$/|\\/g' ./test.txt | od -a
0000000   J   o   h   n   |   \  nl   B   o   b   |   \  nl   T   i   m
0000020   |   \  nl   A   l   e   x   |   \  nl
0000032

```
Hope it helps,
Regards.

---

### Post by YourSurrogateGod on 2012-05-30
I don't have a $ in my sed command.

---

### Post by YourSurrogateGod on 2012-05-30
> **codemaniac said:**
> A simple awk version for you .
```
awk '{print $0 "|\\"} file.txt
```

This didn't work 100%.  I added a ' after }.

But after that change, this script worked fine.  Thanks.

---

### Post by codemaniac on 2012-05-31
> **YourSurrogateGod said:**
> This didn't work 100%.  I added a ' after }.

But after that change, this script worked fine.  Thanks.

Just missed out a single quote on the above awklet. ;)

---

### Post by codemaniac on 2012-05-31
> **papibe said:**
> awk considers \r part of the line so it does not remove it when printing:
```
awk '{print $0 "|\\"}' ./test.txt | od -a
0000000   J   o   h   n  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   B   o   b  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   T
0000020   i   m  [COLOR="Red"]**cr**[/COLOR]   |   \  nl   A   l   e   x  [COLOR="Red"]**cr**[/COLOR]   |   \  nl
0000036

```
Replace '\n' with '$' in the sed command:
```
sed -e 's/\r$/|\\/g' ./test.txt | od -a
0000000   J   o   h   n   |   \  nl   B   o   b   |   \  nl   T   i   m
0000020   |   \  nl   A   l   e   x   |   \  nl
0000032

```
Hope it helps,
Regards.

Hello papibe hope you are fine and doing good .

In the above query i just tried to modify the output as user was the user was expecting .

---

