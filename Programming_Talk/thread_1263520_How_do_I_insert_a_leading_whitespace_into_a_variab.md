---
title: "How do I insert a leading whitespace into a variable?"
date: 2009-09-11
forum: Programming Talk
---

### Post by PryGuy on 2009-09-11
Good day!
I couldn't figure out it's gonna be that hard! Google says how to remove whitespace, and I want to insert a leading whitespace into a variable so the variable '123' would look ' 123'. Sed and awk are fine, but I'm sure this can be done in ordinary bash.

Thank you in advance!

---

### Post by Arndt on 2009-09-11
> **PryGuy said:**
> Good day!
I couldn't figure out it's gonna be that hard! Google says how to remove whitespace, and I want to insert a leading whitespace into a variable so the variable '123' would look ' 123'. Sed and awk are fine, but I'm sure this can be done in ordinary bash.

Thank you in advance!

Doesn't this do what you want?

```
var=123
var2=" $var"

```

---

### Post by PryGuy on 2009-09-11
Well, my piece of code is:

```
toLower() {
    echo "$1" | tr "[:upper:]" "[:lower:]"
}

# Read XML file
while IFS='<>' read _ starttag value endtag; do
  case "$starttag" in 
    ShareOthers) [COLOR="Red"]ShareOthers+=(`toLower "$value"`)[/COLOR];;
  esac
done < ./default.xml
```I tried, it of course, it doesn't work. It's pretty complicated...

---

### Post by Arndt on 2009-09-11
> **PryGuy said:**
> Well, my piece of code is:

```
toLower() {
    echo "$1" | tr "[:upper:]" "[:lower:]"
}

# Read XML file
while IFS='<>' read _ starttag value endtag; do
  case "$starttag" in 
    ShareOthers) [COLOR="Red"]ShareOthers+=(`toLower "$value"`)[/COLOR];;
  esac
done < ./default.xml
```I tried, it of course, it doesn't work. It's pretty complicated...

Where in your code doesn't it work? What should happen, and what does happen?

---

### Post by PryGuy on 2009-09-11
The red line is where I want to add a whitespace to a variable. Tried ShareOthers+=(`" "toLower "$value"`), doesn't work... :(

---

### Post by Arndt on 2009-09-11
> **PryGuy said:**
> The red line is where I want to add a whitespace to a variable. Tried ShareOthers+=(`" "toLower "$value"`), doesn't work... :(

I see the problem too, now. I can't explain it. It seems to be the combination of () and `` which loses the blank.

Try this:

```
    ShareOthers) value2=`toLower "$value"`; ShareOthers+=(" $value2");;

```

---

### Post by Arndt on 2009-09-11
> **PryGuy said:**
> The red line is where I want to add a whitespace to a variable. Tried ShareOthers+=(`" "toLower "$value"`), doesn't work... :(

Here is a better solution than my previous one:

 ```
   ShareOthers) ShareOthers+=(" `toLower $value`");;
```

---

### Post by PryGuy on 2009-09-11
It works, but that's strange but sed says: 'No such file or directory'.
I insert variables with this:```
sed -i '$i\   valid users = '${ShareUser[$i]}[COLOR="Red"]${ShareOthers[$i]}[/COLOR]'' ~/test.txt
```EDIT: I got it. Sed thinks space is a delimeter that separates line from filename. Quoting solved my problem:```
sed -i '$i\   valid users = '[COLOR="Red"]"[/COLOR]${ShareUser[$i]}${ShareOthers[$i]}[COLOR="Red"]"[/COLOR]'' ~/test.txt
```Thank you, Arndt!

---

