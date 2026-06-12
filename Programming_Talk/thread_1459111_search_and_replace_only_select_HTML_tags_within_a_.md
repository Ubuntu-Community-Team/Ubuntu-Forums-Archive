---
title: "search and replace only select HTML tags within a block of text"
date: 2010-04-21
forum: Programming Talk
---

### Post by thaitang on 2010-04-21
i think this should be the right forum to ask this question.

the short and skinny: i need to copy and paste web page content into a text file and put in my own basic HTML tags so the page can be better viewed on my Nokia 7610 phone. Regular webpages take too long to open and forever to navigate thru.

I am currently using gedit and bluefish to insert, search & replace HTML code. But there are times where I need to search for the next occurrance of a tag after a block of text and remove that tag. What tools can I use to accomplish this? 

So, for something like this: 

[HTML]<tr><td class="padleft6"><b>Thought:</b> Regular text I would like to keep.</i><td></tr>[/HTML]

I would like to be able to search for all occurrence of:

[HTML]Thought:</b>[/HTML]

find the next occurrence of '<' which would be for the '</i>' tag and remove everything from that tag '<' until the next occurrence of '<' and that would ideally remove the '</i>' tag.

Am I pissing in the wind hoping for a search tool that can do exactly that?

cheers,
tt

---

### Post by simeon87 on 2010-04-21
You could write a Python script using BeautifulSoup, see [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/) - it can be used to search and modify HTML.

---

### Post by thaitang on 2010-04-21
Thanks for the suggestion simeon87.

Since posting I looked harder in SED and it seems like it is capable of doing everything I need and then some, however, I think I might be on the brink of suicide here. I have a command that looks like it should work, but well it does not. I am certain it is user error, so if anyone can help me with this one my sanity would sure appreciate it.

```
sed "/Thought\:/s/<i><\/i><\/td><\/tr>\n\t\t\t<tr><td>.<\/td><\/tr>/<\/td><\/tr>/g" oth1.html > oth2.html
```I thought for sure it had to do with the escaping new line or tabs, but I have made this work fine: 

```
sed "/Thought\:/s/<\/tr>/<\/tr>\n\t\t\t<tr><td>.<\/td><\/tr>/g" oth1.html > oth2.html
```I have made some pretty dumb mistakes sofar trying to learn how to tame SED, but I cannot see why the first example above deos not work.

BTW, is there a way to show current col position of the cursor in either XTerm or gnomeTerm? that might be a big help.

cheers,
tt

---

### Post by howlingmadhowie on 2010-04-22
i think you could be looking for something like this:

```

$ echo '<tr><td class="bla">Thought:</b> foobar. </i></td></tr>' | sed 's|\(Thought:</b>\)\([^<]*\)<[^>]*>|\1\2|'
<tr><td class="bla">Thought:</b> foobar. </td></tr>

```

sed has the ability to store parts of a result, so here \1 refers to that matched by the first \( \) group, and \2 refers to that matched by the second.

the first group, \(Thought:</b>\), is clearly 'Thought:</b>'
the second group, \([^<]*\), is whatever follows it until a < is reached.

the third group in the search expression, <[^>*]>, matches any single html tag.

---

### Post by thaitang on 2010-04-23
hey guys things are coming slowly but surely with sed. now I have sed script files that do almost everything I need, actually they do, but still with quite a bit of manual effort.

I am trying to use a sed script inside of a bash for loop to automatically change $name variables, but I am having some problems because the file names overwrite each each iteration of the for loop, and by the end only the last name in the for list gets changed in the filename.

can someone please help me fine tune this so that somehow (with a counter I think, but I have played with counters and cannot get seem to get the desired result) the for loop goes thru and changes the name, saves the result, changes the name to the next one and using the saved file from the previous iteration.

```
#!/bin/bash
for name in BAPTISTA TRANIO HORTENSIO GREMIO GRUMIO PETRUCHIO WIDOW
do		
		#append colon after any lines that only contain name
		#put name on new line whenever a period immediately proceeds it
		#put name on new line whenever a closing bracket immediately proceeds it
		#all instances of '&#8221;' need to be substitued for '"'
		#rm any chars coming after the colon following the name
	sed -e "/^$name$/s/$name/$name\:/g" -e	"/$name/s/.$name/.\n$name\:/g" -e "/$name/s/)$name/)\n$name\:/g" -e "/$name/s/\"$name/\"\n$name\:/g" -e "s/\($name\:\).*/\1/g" -e "/$name/s/$name\:/<tr><td class=\"padleft6\"><b>$name\:<\/b><\/td><\/tr>/g" $filename1 > $filename2
done
```

All of the sed subs work fine if I call them using the sed file command. And I am pretty sure they should work here as is, since the end result I have, the name WIDOW gets changed in the file as desired. I think the rest of the names do also, but then get written over.

I know that I still need to manually enter the names into the bash script, but doing that and having the for loop correct will still save me a schwack of time.

Thanks for any help because I have never done any programming before, so lots of new ideas here that are probably in need of modification.

cheers,
tt

---

### Post by howlingmadhowie on 2010-04-23
can you post an extract from the file you're trying to modify and then the same extract, but how it should be after modification? at the moment i still don't know what you want to do and an example here would be worth a thousand words of explanation.

---

### Post by thaitang on 2010-04-23
I was a bit too hasty posting. As soon as I posted it hit me to try copying the files at the end of each iteration like so:

```
#!/bin/bash
for name in BAPTISTA TRANIO HORTENSIO GREMIO GRUMIO PETRUCHIO WIDOW
do        
        #append colon after any lines that only contain name
        #put name on new line whenever a period immediately proceeds it
        #put name on new line whenever a closing bracket immediately proceeds it
        #all instances of '”' need to be substitued for '"'
        #rm any chars coming after the colon following the name
    sed -e "/^$name$/s/$name/$name\:/g" -e    "/$name/s/.$name/.\n$name\:/g" -e "/$name/s/)$name/)\n$name\:/g" -e "/$name/s/\"$name/\"\n$name\:/g" -e "s/\($name\:\).*/\1/g" -e "/$name/s/$name\:/<tr><td class=\"padleft6\"><b>$name\:<\/b><\/td><\/tr>/g" $1 > $2
    cp $2 $1
done
```which works like a charm

cheers,
tt

---

