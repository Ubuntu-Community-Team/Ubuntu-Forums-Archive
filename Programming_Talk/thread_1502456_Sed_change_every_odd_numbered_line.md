---
title: "Sed change every odd numbered line"
date: 2010-06-05
forum: Programming Talk
---

### Post by theLured on 2010-06-05
I want to be able to change the lines with odd numbers(The lines don't have numbers in them). e.g. lines 1,3,5 etc.

I want to change all the 'A' to 'B'. How could I do this?

---

### Post by DaithiF on 2010-06-05
Hi,
```
sed 's/A/B/;N' somefile

```

---

### Post by Trumpen on 2010-06-05
or, if you are using gnu sed:

[php]sed '1~2 s/A/B/g' file[/php]

---

### Post by theLured on 2010-06-05
Thank you for both of your suggestions. They both work perfectly.
I am using this command now.
```
#!/bin/bash

if [ "$1" != "" ]; then
	sed 's/A/B/g;N' "$1" > "$1".bak; mv "$1".bak "$1"
	sed 's/C/D/g;N' "$1" > "$1".bak; mv "$1".bak "$1"
fi
```

I'm sure there's a better way to do several converts, but this works perfectly for me.

Once again, Thank You.

---

### Post by DaithiF on 2010-06-05
why not:
```

sed -i 's/A/B/g;s/C/D/g;N' "$i"
```(-i for in-place update of the file)

---

### Post by theLured on 2010-06-05
Thanks for the reply. I will keep it in mind, but don't really need to change it because it's quick enough for me.

I really have about 20 sed commands, so I need to see them under each other to see what I have/haven't missed.

It's all completed now and I am very happy with the results.

On a side note, I also had to move several files using sed heres how I did it.
It passes a variable to sed and gets a variable back.

```
#!/bin/bash

# I don't think these 2 lines are needed, but keeping the just in case.
dir=`dirname "$1"`
cd "$dir"
for thing in "$@"
do
	filename=`basename "${thing}"`
	new_filename=`basename "${thing}"`

	echo $filename
	new_filename=`echo "$new_filename" | sed 's/a/b/g'`
	new_filename=`echo "$new_filename" | sed 's/c/d/g'`

	mv "$filename" "$new_filename"
done
```
Once again, Thank You All.

EDIT: I just tried
sed -i '1~2 s/a/b/g' "$1"
There's only a microsecond difference when running it about 20 times, but I will use it now. Less code and faster. Thank you.

---

