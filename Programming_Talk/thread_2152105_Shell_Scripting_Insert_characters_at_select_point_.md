---
title: "Shell Scripting: Insert characters at select point in line"
date: 2013-06-06
forum: Programming Talk
---

### Post by duke.tim on 2013-06-06
I have been writing a script which collects information and then formats it in a CSV format.

I need to know how to insert a few characters after a specified column in a line. Something that to my knowledge sed and tr don't do.

The format is something like this
> name,,name2,,country,phone\n
,SomeNumbers...,,SomeNumbers...,,\n

For example this is what it should do
Before
```
,80:20:36:34563:1:,,3:45:2,,
```
Insert 6: after first comma and 12: after 3rd comma

After
```
,6:80:20:36:34563:1:,,12:3:45:2,,
```

The script can provide the line number and byte offset, I just need a tool that can insert the characters. (insert not overwrite)

---

### Post by steeldriver on 2013-06-06
You could do it with sed I think e.g. to insert INSERT after the 12th character of the 2nd line

```

$ echo -e "name,,name2,,country,phone\n,numbers...,,numbers...,,\n" | sed -r '2 s/(.{12})/&INSERT/'
name,,name2,,country,phone
,numbers...,INSERT,numbers...,,


```

---

### Post by duke.tim on 2013-06-06
Thanks for the help, I'll have to try it out.

---

