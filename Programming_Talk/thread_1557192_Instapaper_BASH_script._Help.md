---
title: "Instapaper BASH script. Help"
date: 2010-08-20
forum: Programming Talk
---

### Post by jesus.mor on 2010-08-20
Ok so I recently started using Instapaper and I'm loving it. 
When I set it up with rss feeds however there are minor annoyances with the way it shows the articles. Since it follows the links in the rss feed sometimes the article comes up with a page of navigation links and some of the comments.

What I realized was that mobile versions of website don't have those elements so Instapaper can parse the text correctly and only show the artice.. It's a pain to have to add the articles manually and mobile sites don't have rss feeds.

So I came up with this. 

```
curl m.engadget.com | grep "http://" | tr "[ ]" "[\n]" | grep "http://" | sed 's/href//g' | sed 's/=//g' | sed 's/\"//g' | sed 's/http:\/\/m.engadget.com\/media\/feedlogo.gif//g' | mail -s "" readlater@instapaper.com

``` 

This will email all the links to Instapaper but Instapaper will only use the first link. So I need a way to send each link out individually. 

Also a way to get the subject in "mail -s "" [email]blah@blah.com[/email]" to be the last couple of letters in the link.

I know this is a lot to read ;) but can you all help?

---

### Post by Rany Albeg on 2010-08-20
Hello,

If i did understand you correctly then its all about sending each link individualy in a simple 'for' loop.
Use 'last_couple' variable to write the subject.

```
for i in $(curl -s m.engadget.com | 
           grep "http://"         | 
           tr "[ ]" "[\n]"        | 
           grep "http://"         |
           sed -e 's/href//g' -e 's/=//g' -e 's/\"//g' -e 's/http:\/\/m.engadget.com\/media\/feedlogo.gif//g')
do
	last_couple=$(echo "$i"|grep -o ..$)

	# email each "$i" here
done
exit 0
```

---

### Post by geirha on 2010-08-20
Parsing xml/html with tools like the grep, sed, cut, awk, etc... is hell. [Lynx](apt:lynx-cur) can parse the html for you, and provide you with only the links.

```
lynx -dump -listonly -nonumbers http://m.engadget.com
```

EDIT:
Oh, and see [BashFAQ 1](http://mywiki.wooledge.org/BashFAQ/001) on how to parse that output.

And to get the last few bits of the url, see [BashFAQ 73](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by jesus.mor on 2010-08-20
Ok so I ended up with this.

```
lynx -dump -listonly -nonumbers http://m.engadget.com | while read -r line; do echo "$line" | mail -s "" jesus.mor14@gmail.com; done;

```

That works for sending out the URLs but I can't get the subject part right.

```

list=`lynx -dump -listonly -nonumbers http://m.engadget.com`

lynx -dump -listonly -nonumbers http://m.engadget.com | while read -r line; do echo "$line" | mail -s "$list" jesus.mor14@gmail.com; done;

```

I used that but it only used the first url as the subject.

---

### Post by geirha on 2010-08-20
In the loop, try with: 
```
subject=${line%/} subject=${subject##*/}
mail -s "$subject" jesus.mor14@gmail.com <<< "$line"
```


(«mail -s ... <<< "$line"» is, in bash, equivalent to «echo "$line" | mail -s ...» except you lose the overhead of a pipe.)

---

### Post by jesus.mor on 2010-08-20
That worked perfectly! Thank you

---

