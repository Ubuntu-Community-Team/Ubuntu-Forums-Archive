---
title: "create text file with the date"
date: 2013-05-13
forum: Programming Talk
---

### Post by heathclf on 2013-05-13
Huge beginner here. I'd like to create a text file containing a formatted date using bash, and can't quite seem to get it.

let's say I'm trying to create a file containing the single line:

   mm/dd/yyyy-mm/dd/yyyy

I can get the date from bash like this:
```
`date +%m/%d/%Y`
```
and I think I'm supposed to be able to get tomorrow's date using the following code, but can't quite seem to get it:
```
`date +%m/%d/%Y` --date="-1 days ago"
```

I'm also not quite sure how to create / write over a one-line text file. I can create the file using cat (but I have no preference over cat / sed / vi, etc.):
```
cat > dates
```
but no text shows up in my file at all, and I can't seem to be able to close the file. I guess Crtl+Shft+D is supposed to work.

right now, if my logic worked (and it doesn't), my code would look like this:

```
$now=$(`date +%m/%d/%Y`)
$later=$(`date +%m/%d/%Y` --date="-1 days ago")

cat > dates
$now-$later
^D
```

I'm sure this is a joke for most of you guys. Any help would be greatly appreciated. Thanks!

---

### Post by steeldriver on 2013-05-13
try

```
echo $(date '+%m/%d/%Y')-$(date '+%m/%d/%Y' --date="tomorrow") > dates
```

---

### Post by heathclf on 2013-05-13
Thanks! Worked perfectly! Well...this thread's over :)

---

### Post by trent.josephsen on 2013-05-13
Just a suggestion, use %F if you can for non-display output. Big-endian dates are free of ambiguity. Otherwise, if this output is meant for human consumption, use +%x instead for a locale-appropriate date format.

---

