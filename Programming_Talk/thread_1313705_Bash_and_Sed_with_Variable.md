---
title: "Bash and Sed with Variable"
date: 2009-11-03
forum: Programming Talk
---

### Post by kingbilly on 2009-11-03
Hello,

I am trying to make a bash script to add a "template-like" structure to a new XML file

```
settings.xml

<?xml version='1.0'?><map>
</map>
```

I have this bash script that will add the 3 line template to settings.xml

```

NEWCLASS='''<object file="new" > \n
<string>new</string> \n
</object>'

# Insert a blank class
sed '1a\ $NEWCLASS' settings.xml > new_settings.xml 
```

The problem with the above code is it outputs the literal variable into new_settings

```
new_settings.xml

<?xml version='1.0'?><map>
 $NEWCLASS
</map>

```

If I try double quotes around the sed argument, I get this error
```
sed: -e expression #1, char 29: unknown command: `<'
```

Anyone able to explain how to make this work? ):P

---

### Post by Arndt on 2009-11-04
> **kingbilly said:**
> Hello,

I am trying to make a bash script to add a "template-like" structure to a new XML file

```
settings.xml

<?xml version='1.0'?><map>
</map>
```

I have this bash script that will add the 3 line template to settings.xml

```

NEWCLASS='''<object file="new" > \n
<string>new</string> \n
</object>'

# Insert a blank class
sed '1a\ $NEWCLASS' settings.xml > new_settings.xml 
```

The problem with the above code is it outputs the literal variable into new_settings

```
new_settings.xml

<?xml version='1.0'?><map>
 $NEWCLASS
</map>

```

If I try double quotes around the sed argument, I get this error
```
sed: -e expression #1, char 29: unknown command: `<'
```

Anyone able to explain how to make this work? ):P

The quoting is confusing me, but this seems to work:

```
NEWCLASS='''<object file="new" >\\
<string>new</string>\\
</object>'

TMPFILE=/tmp/sed$$

echo "1a\\" >$TMPFILE
echo "$NEWCLASS" >>$TMPFILE

# Insert a blank class
sed -f $TMPFILE settings.xml > new_settings.xml

rm -f $TMPFILE

```

Why do you have the three single quotes at the beginning, by the way? The first two result in an empty string, so they can be removed.

---

### Post by kingbilly on 2009-11-04
Thanks, it worked!

---

