---
title: "Sed regular expressions"
date: 2010-03-09
forum: Programming Talk
---

### Post by Jimmy B on 2010-03-09
Hey there,

Im trying to search and replace some text in a file using sed with some regular expressions. Basically I have:

BGQ032L24
BGQ032N02
BGQ032N04
BGQ032N06
BGQ032N08
BGQ032N10
BGQ032N12
BGQ032N14

And I want to insert a character (underscore) between before the third last character like this:

BGQ032_L24

I tried: 
sed 's/BGQ[0-9][0-9][0-9]/BGQ[0-9][0-9][0-9]/g' file
and I get the search fine but the regular expression adds to the replacement. 

Any suggestions?

---

### Post by aquavitae on 2010-03-09
Not entirely sure what your problem is, but don't you need to add an underscore to sed:
```
sed 's/BGQ[0-9][0-9][0-9]/BGQ[0-9][0-9][0-9][COLOR="Red"]_[/COLOR]/'
```

---

### Post by Jimmy B on 2010-03-09
Perhaps im not explaining it right (and yes i forgot the _ in my post above). If I execute the command you just suggested I get as an output:

BGQ[0-9][0-9][0-9]_
BGQ[0-9][0-9][0-9]_
BGQ[0-9][0-9][0-9]_
BGQ[0-9][0-9][0-9]_
BGQ[0-9][0-9][0-9]_
 BGQ[0-9][0-9][0-9]_
 BGQ[0-9][0-9][0-9]_
 BGQ[0-9][0-9][0-9]_

When what I want it is:

BGQ032_L24
BGQ032_N02
BGQ032_N04
BGQ032_N06
BGQ032_N08
BGQ032_N10
BGQ032_N12
BGQ032_N14

---

### Post by Some Penguin on 2010-03-09
That's what capturing groups and back references are for.

---

### Post by DaithiF on 2010-03-09
Hi,
```
sed 's/BGQ[0-9]\{3\}/&_/'  somefile
```

---

### Post by DaithiF on 2010-03-09
or alternatively, if you want to work from the end of the line, ie. always insert the _ before the 3rd last character of the line (regardless of how long the line may be), then
```
sed 's/.\{3\}$/_&/' testfile

```

---

### Post by howlingmadhowie on 2010-03-09
```

howlingmadhowie% echo "BGQ123N12" | sed -e 's/\(.*\)\(.\{3\}\)/\1_\2/' 
BGQ123_N12

```

it looks nicer without the escapes:
```

sed -e 's/(.*)(.{3})/\1_\2/'

```
but it needs the escapes to work

DaithiF's second solution above is better than mine. it explicitly checks for the end of the line.

---

### Post by Jimmy B on 2010-03-09
> **DaithiF said:**
> Hi,
```
sed 's/BGQ[0-9]\{3\}/&_/'  somefile
```

Brilliant thanks guys. The escape characters that were getting me

---

