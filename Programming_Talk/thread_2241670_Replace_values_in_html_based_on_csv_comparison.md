---
title: "Replace values in html based on csv comparison"
date: 2014-08-27
forum: Programming Talk
---

### Post by chinny on 2014-08-27
Hi all,

I've got an HTML file I need to replace certain values (containing special characters) in. I also have a csv with 2 columns. Column 1 has the old value which will match the current html content. 
The second column contains the replacement value. I'm looking for a way to do this with a bash script, awk springs to mind but I'm a bit out of my depth.
I could do an inline replacement or create a new output file - either is fine.

Samples of the kind of data I'm looking at are:

html file contains strings like *111.2222.333*

The csv file contains:

[I]111.2222.333,44.55.dd
222.3333.444,55.66.ee[/I]
etc

I would like to replace all occurrences of *111.2222.333*  with *44.55.dd* and all instances of *222.3333.444* with *55.66.ee* etc.

Could anyone suggest any solutions please? I'm happy to consider Perl, Python or anything else that will work.

---

### Post by Vaphell on 2014-08-28
```
$ cat file.html
<hmtl>
<body>
<div id="111.2222.333">something something</div>
<div id="zcbxbn">222.3333.444</div>
</body>
</html>
$ cat pairs.csv
111.2222.333,44.55.dd
222.3333.444,55.66.ee
$ while IFS=, read x y; do sed -i "s/${x//./[.]}/$y/g" file.html; done < pairs.csv
$ cat file.html
<hmtl>
<body>
<div id="44.55.dd">something something</div>
<div id="zcbxbn">55.66.ee</div>
</body>
</html>
```

---

### Post by chinny on 2014-08-28
> **Vaphell said:**
> ```
$ cat file.html
<hmtl>
<body>
<div id="111.2222.333">something something</div>
<div id="zcbxbn">222.3333.444</div>
</body>
</html>
$ cat pairs.csv
111.2222.333,44.55.dd
222.3333.444,55.66.ee
$ while IFS=, read x y; do sed -i "s/${x//./[.]}/$y/g" file.html; done < pairs.csv
$ cat file.html
<hmtl>
<body>
<div id="44.55.dd">something something</div>
<div id="zcbxbn">55.66.ee</div>
</body>
</html>
```

Many thanks for that - I'm affraid I get the following though:

***bash: read `x, ': not a valid identifier***

Edit - my bad - I accidentally added an extra comma in. Works a treat. Thank you very much!!!

---

