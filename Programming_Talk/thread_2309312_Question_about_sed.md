---
title: "Question about sed"
date: 2016-01-09
forum: Programming Talk
---

### Post by kevdog on 2016-01-09
I'm not a sed expert but definitely not a beginner.

I've broken down my problem and I quite quite figure out why I can't match the expression #!/usr/bin/python. I'm trying to replace all occurrences of #!/usr/bin/python with #!/usr/bin/python2

Here is my simplified example:

sed -ri "s|^#!/usr/bin/python$|&2|g" setup.py

It returns:
bash: !/usr/bin/python$: event not found

It's not found because it's not matching the # symbol

If I use the expression:
sed -ri "s|#!/usr/bin/python$|&2|g" setup.py

Things work as expected, however I want to match the beginning of the line.
I'm confused what to do at this point.

---

### Post by steeldriver on 2016-01-09
That's nothing to do with sed  - it's because the shell is treating ! as a history expansion command

It should work if you change the double quotes to single quotes, I think

---

### Post by matt_symes on 2016-01-09
Hi

Use single quotes

```
sed -ri 's|^#!/usr/bin/python$|&2|g' setup.py
```
```

matthew-xu-16-04:/home/matthew:0 % echo '#!/usr/bin/python' > test.py
matthew-xu-16-04:/home/matthew:0 % sed -ri 's|^#!/usr/bin/python$|&2|g' test.py 
matthew-xu-16-04:/home/matthew:0 % cat test.py 
#!/usr/bin/python2
matthew-xu-16-04:/home/matthew:0 % 
```

I think that bash is performing command substitution in a similar way to this example.

```

matthew-xu-16-04:/home/matthew:0 % touch /test
touch: cannot touch &#8216;/test&#8217;: Permission denied
matthew-xu-16-04:/home/matthew:0 % sudo !!
sudo touch /test
[sudo] password for matthew: 
matthew-xu-16-04:/home/matthew:0 % 
```

**EDIT:**

Beaten to it :) 

And you even had the correct parlance, steeldriver. History expansion.

Kind regards

---

### Post by steeldriver on 2016-01-09
... but it's better with examples ;)

---

