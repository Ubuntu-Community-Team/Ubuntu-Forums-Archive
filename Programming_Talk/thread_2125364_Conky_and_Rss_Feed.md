---
title: "Conky and Rss Feed"
date: 2013-03-13
forum: Programming Talk
---

### Post by PantherStu on 2013-03-13
Hi all.
I hope I'm posting this in the right place.

I am in the process of writing my new conky script, and I am wanting to put a "word of the day" script in.
So I decided I could just use conky's built in rss function for this
so 
```

${color}${rss http://www.wordthink.com/feed 720 item_titles 1}
```
And this works great for the title, however when i use it for the descrtipton (ie definition)
```

${color}${rss [http://www.wordthink.com/feed](http://www.wordthink.com/feed) 720 item_desc 1}
```

I end up with 2 problems that I'd like to sort out.

1. Description is too long and there fore stretches conky across my whole screen. no ability to word wrap the rss feed
2. the rss function in conky doesn't format so you end up with something like below in your conky including all symbols "<b>" etc
```
<p><b>Placid</b> (plac·id) <i>adj.</i>* 1. Satisfied; complacent.* 2. Undisturbed by tumult or disorder; calm or quiet.</p>
```

So what I am wondering is does any1 have a way I could use either a bash script or curl to parse this info back into my conky script.

Any help is appreciated (I am very new to scripting)

---

### Post by greenpeace on 2013-03-13
Hey, 

You can definitely use Lua[1] or Bash[2] to process the RSS a little before displaying it.  If I remember correctly, there is very good support for Lua scripts in Conky, and the language has a load of relevant features.. [3]

Parsing RSS in bash might be a bit of a headache, although your needs aren't too complicated.  Perhaps a simple solution might be easier![4]

Hope that helps!
Gp


[1] [http://www.lua.org/](http://www.lua.org/)
[2] [http://how-to.wikia.com/wiki/How_to_add_an_RSS_feed_to_Conky/conky-rss.sh](http://how-to.wikia.com/wiki/How_to_add_an_RSS_feed_to_Conky/conky-rss.sh)
[3] [http://stackoverflow.com/questions/6570291/lua-patterns-how-to-remove-unwanted-string-within-a-string](http://stackoverflow.com/questions/6570291/lua-patterns-how-to-remove-unwanted-string-within-a-string)
[4] [http://stackoverflow.com/questions/443991/how-to-parse-rss-feeds-xml-in-a-shell-script](http://stackoverflow.com/questions/443991/how-to-parse-rss-feeds-xml-in-a-shell-script)

---

### Post by PantherStu on 2013-03-13
Beautiful, Thanks
After reading through posts you linked to, this is what I ended up with in my conkyrc
```


Word of the Day
${hr}
${color}${font Sawasdee:bold:size=14}${rss http://www.wordthink.com/feed 300 item_titles 1}${font}
${execi 300  curl -s http://www.wordthink.com/feed/ | grep description |sed -e :a -e 's/<[^>]*>//g;/</N' |sed -e 's/[ \t]*//' |sed -e 's/\(.*\)/ \1/' |sed -e 's/\.//' |sed -e 's/\"//' |sed -e 's/\"//' |head -n $((1 + 2)) |tail -n $((1))|fold -s50}

```

which looks like
 [IMG]http://img836.imageshack.us/img836/9417/wotdconky.png[/IMG]

Thanks for all the help

---

### Post by RaHorakhty on 2013-03-15
imagine what it would look like if you had oxy-moronic pics in the background

---

