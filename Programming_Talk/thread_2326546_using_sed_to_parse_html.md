---
title: "using sed to parse html?"
date: 2016-06-02
forum: Programming Talk
---

### Post by rebeltaz on 2016-06-02
I have got the biggest headache!

I hope I am posting this to the right forum... I am trying to parse an html file using sed in a bash script. My problem is that I need to strip everything up to a particular tag, but the "everything" in this case includes tabs, spaces, newlines and linebreaks.

The html that I am working on is:
```

 
    <div id="filters">
        <input type="hidden" name="filter-search-previous" value="">
        <input type="text" class="form-control" name="filter-search" placeholder="Search..." value="">

        <select class="form-control" name="filter-sort">
            <option >Newest products first</option>
            <option >Sort by expiry ascending</option>
            <option >Sort by expiry descending</option>
            <option >Sort by price (lowest first)</option>
            <option >Sort by price (highest first)</option>
        </select>
 
 
        <button type="button" class="btn btn-warning" style="top: -1px; position: relative; margin-left: 10px;" onclick="refresh_products(0)">Refresh / Search</button>
 
    </div>
    
    <div id="box-container-inner" style="position: relative">

        <div class="box" id="product_1208750">
        <div class="img-container">

```

Now, what I want to do is to strip out everything up to, and including [ <div id="box-container-inner" style="position: relative"> ]. I have tried the following commands:

```

sed -i 's/.*<div id="box-container-inner" style="position: relative">//' output.txt

sed -i 's/[\s\S]*<div id="box-container-inner" style="position: relative">//' output.txt

```

The first one just deletes that one line, and the second one doesn't do anything. Can someone help me with this? Either that or send me a bottle of aspirin! Thanks :)

---

### Post by steeldriver on 2016-06-02
Why try to use the 's' command for this? Use the 'd' (delete) command on the whole range between the start of the file and the text

```

sed '0,/<div id="box-container-inner" style="position: relative">/d' output.txt

```

---

### Post by rebeltaz on 2016-06-02
Honestly? Didn't know about the 'd' command, but... that will work for that scenario, but I am also going to need to removed data from a tag to the end as well several lines in between. Is there no way for sed to select newlines?

---

### Post by vasa1 on 2016-06-03
If you're going to do a lot of work involving modifying html, you may want to look at something like [XMLStarlet]("http://manpages.ubuntu.com/manpages/xenial/en/man1/xmlstarlet.1.html"):```
       XMLStarlet is a set of command line utilities (tools) which can be used
       to transform, query, validate, and edit XML documents and files using
       simple set of shell commands in similar way it is done for plain text
       files using UNIX grep, sed, awk, diff, patch, join, etc commands. This
       set of command line utilities can be used by those who deal with many
       XML documents on UNIX shell command prompt as well as for automated XML
       processing with shell scripts.

```
I might add that there are quite a few articles cautioning about parsing html using regex. Here's just one: [http://stackoverflow.com/a/1733489](http://stackoverflow.com/a/1733489)

---

### Post by rebeltaz on 2016-06-03
Since I never could find/get a way to do what I was asking (and I posted this request to three different forums!) I went about it a different way. Instead of stripping out the unnecessary lines, I pulled out the lines that I needed and wrote them to a separate file. I was then able to parse THAT file instead. 

Yeah... I have read the cautionary warnings, and I do understand the reasoning behind them. In my cases, though, I'm never parsing general HTML code. My scripts are designed to wget a single page and then parse data out of that known code. Of course, if the site changed the page, it will break the script, but pages (hopefully) don't normally change that often and if they do, I'll just modify the script. These  are all only for personal use anyway, so I don't have to worry about keeping users happy :)

Having said that, though, I will take  a look at XMLStarlet. It does sound interesting. Generally speaking, I like dealing with default programs rather than installing additional packages, but if the incentive is strong enough... 

Thank you :)

---

