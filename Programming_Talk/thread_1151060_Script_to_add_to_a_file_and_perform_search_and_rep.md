---
title: "Script to add to a file and perform search and replace"
date: 2009-05-06
forum: Programming Talk
---

### Post by jonobr on 2009-05-06
Hello All,

My scripting ability is really laughable, and Im wondering if someone can help with this real easy stupid question.. 
Or point me to good bash or perl examples of this.

I have a whole bunch of xml files which I need to prepare for importing to another system.

Each xml files contents contain information which needs tags added to the start and finish. I will also have to have a search and replace.

Im doing this in vi at the moment, just adding the tags and then doing a ```
:%s/this/that/g
```
however now its getting unworkable as the number of files is increasing
SO heres an example of what I was hoping to get...


file1 contains

```

<rhyme>
  <to>Mary</to>
  <from>little-lamb</from>
  <heading>Reminder</heading>
  <body>My fleece is still white as snow</body>
</note>

```

I would like to Wrap the file with another tag eg <nusery> </nusery>
eg

```

<nursery>
<rhyme>
  <to>Mary</to>
  <from>little-lamb</from>
  <heading>Reminder</heading>
  <body>My fleece is still which as snow</body>
</rhyme>
</nursery>

```

After that I would want to remove certain things, eg, the "-" in "little-lamb" to make it littlelamb.

I would if possible like to make that more flexible,
in that , I want to look for  

<from>little??????lamb</from>
I.e. anything that matches the front and the end and has a variable amount of info in the ????? and switch it to something else, e.g.
maybe littlelamb again.

<from>little dumb lamb</from>
<from>little pretty lamb</from>
<from>little supercalerfragalistic lamb</from>

all go to 
<from>littlelamb</from>

Many thanks

---

### Post by Arndt on 2009-05-06
> **jonobr said:**
> Hello All,

My scripting ability is really laughable, and Im wondering if someone can help with this real easy stupid question.. 
Or point me to good bash or perl examples of this.

I have a whole bunch of xml files which I need to prepare for importing to another system.

Each xml files contents contain information which needs tags added to the start and finish. I will also have to have a search and replace.

Im doing this in vi at the moment, just adding the tags and then doing a ```
:%s/this/that/g
```
however now its getting unworkable as the number of files is increasing
SO heres an example of what I was hoping to get...


file1 contains

```

<rhyme>
  <to>Mary</to>
  <from>little-lamb</from>
  <heading>Reminder</heading>
  <body>My fleece is still white as snow</body>
</note>

```

I would like to Wrap the file with another tag eg <nusery> </nusery>
eg

```

<nusery>
<rhyme>
  <to>Mary</to>
  <from>little-lamb</from>
  <heading>Reminder</heading>
  <body>My fleece is still which as snow</body>
</rhyme>
</nusery>

```

After that I would want to remove certain things, eg, the "-" in "little-lamb" to make it littlelamb.

I would if possible like to make that more flexible,
in that , I want to look for  

<from>little??????lamb</from>
I.e. anything that matches the front and the end and has a variable amount of info in the ????? and switch it to something else, e.g.
maybe littlelamb again.

<from>little dumb lamb</from>
<from>little pretty lamb</from>
<from>little supercalerfragalistic lamb</from>

all go to 
<from>littlelamb</from>

Many thanks

If it's XML, maybe xslt/xsltproc is the right solution.

Perl, PHP and python probably all have support for reading, modifying and writing XML. Doing it as pure text works only if you know exactly how the XML happens to be formatted.

(And it's "nursery".)

---

### Post by ghostdog74 on 2009-05-06
```

awk '
/<\/note>/{f=0;print "</rhyme>\n</nursery>";next}
/<rhyme>/{f=1;print "<nursery>";}
f{
 if($0 ~ /<from>/){
  gsub(/-| /,"")
 }
}1' file


```
output:
```

# ./test.sh
<nursery>
<rhyme>
  <to>Mary</to>
<from>littlelamb</from>
  <heading>Reminder</heading>
  <body>My fleece is still white as snow</body>
</rhyme>
</nursery>


```

---

### Post by geirha on 2009-05-07
> **jonobr said:**
> ```
:%s/this/that/g
```

You can do such substitutions on many files at once with sed.

```

sed -i 's/this/that/g' file1 file2 file3 ...
# Though, often safer to also match word start and word end, and add 
# a ~ to the -i so that it creates a backup of the original.
sed -i~ 's/\<this\>/that/g' file1 file2 file3 ...

```

---

### Post by jonobr on 2009-05-07
Excellent

Thanks for the info, Ill get to do some testing with this tday,
I appreciate your advice and assistance

Now, where is that stupid solved button...

Thanks

Jonobr

---

