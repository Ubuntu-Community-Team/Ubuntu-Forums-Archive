---
title: "HOWTO: Query Twitter"
date: 2009-08-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Darkade on 2009-08-16
We'll write a script that's able to do the two basic Twitter actions: 1) Review the Friend Timeline and 2) Post a new tweet; trough a bash script.
Even tough it works this is mostly a didactic exercise, since it does not provide the functionality of a proper twitter client.

This HOWTO is heavily based in the [twitter API]("http://apiwiki.twitter.com/Things-Every-Developer-Should-Know#8AcommandlineisallyouneedtousetheTwitterAPInbsp") and [this]("http://www.grymoire.com/Unix/Sed.html") sed tutorial.

_**Content:**_
[LIST]
[*]We will be using.
[*]Understandig the cURL actions
[*]Using sed and html2text to format the output
[*]Final Script (if you understand the tools, you might go straight to this)
[*]Other things that could be done
[*]sed Appendix
[/LIST]

_**We will be using:**_
[LIST=1]
[*][cURL]("http://curl.haxx.se/"): it allows us to do certain operations with URL's, like logging into a site without actually opening a browser and doing it. It's somehow similar to wget.
[*][sed]("http://www.gnu.org/software/sed/"): Sed is a filter for text. I takes an input and does an action to it line by line.
[*][html2text]("http://www.mbayer.de/html2text/"): it takes a HTML formated input and format it to a readable output
[/LIST]
Make sure you have those tree installed



_**Understandig the cURL actions**_
From now on I will be using $USER to refer to the twitter username you want to query, and $PASS for the corresponding password, when you do this you will substitute them with the corresponding ones.

*First the update:*
So, as we can read in the twitter API all we need to tweet is the following line:

```
curl --basic --user $USER:$PASS --data status=$UPDATE http://twitter.com/statuses/update.xml
```

Now let us understand what this means:
--basic means cURL will be using basic HTTP authentication, it's set up by default, but it can't hurt to use it anyway

--user $USER:$PASS are the user and password we will be using with our selected authentication method; in our case basic HTTP authentication.

--data it's the data we will be sending to the site (twitter). It's sent via POST request, which might ring some bells if you are familiar with HTML/HTTP. It just tells twitter that $UPDATE is what we want to tweet.

[http://twitter.com/statuses/update.xml](http://twitter.com/statuses/update.xml) when authenticated this site will accept a POST request, which will be used to update our status. Though it beats me why it's an XML file

Using that command you can already tweet as much as you want, but of course you'll have to write the whole line each time.


*Getting the Friend TimeLine:*

```
curl --basic --user $USER:$PASS http://twitter.com/statuses/friends_timeline.xml
```

There's not much to explain here, it also authenticates us, but this time we don't send any data, we simply fetch the friends_timeline.xml
As you might imagine if you run this command you'll end up with a pretty much unreadable XML output, this contains a lot of your friends info like: descriptions, screen names, names, avatars, and of course the tweets you read in your timeline.



_**Using sed to format the output**_
Now we have all the data we need... but we can't read it, at least not in an easy way. That's why we'll use sed to format this output (if you really want to understand this section you might want to check the sed tutorial I mentioned earlier)

First we'll run ```
curl --basic --user $USER:$PASS http://twitter.com/statuses/friends_timeline.xml > timeline
``` this creates a file named timeline, which contains the command output, this file we'll be using for a while so that we don't run out of requests to the twitter server.

Now if you check the timeline file you can se that the tweets are wrapped with <text> tags, and the authors of the tweets are between <name> tags; similar to this:
> 
<truncated>false</truncated>
<in_reply_to_status_id/>
<in_reply_to_user_id/>
<favorited>false</favorited>
<in_reply_to_screen_name/>
&#8722;
<user>
<id>000000</id>
<name>John Doe</name>
<screen_name>JDoe</screen_name>
<location>Somewhere in the world</location>
<description>Hello World</description>
.....

So if we can get rid of all the other lines and those tags we would just have the tweet and the authors in quite a readable way.

And that's just what this scary command does:
```

sed -n -e "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" -e "s/.*<text>\(.*\)<\/text>.*/<p>\1<\/p>/p" timeline

```

We are using [regular expressions]("http://en.wikipedia.org/wiki/Regular_expressions") to find the lines with <name> and <text>replace them with <h4> and <p> and drops all the other lines.
This can get complicated and this is not a sed tutorial, nor a regular expressions one, so I'll cover it briefly at the very ending in the *Sed Appendix*

Now if we pipe the result into an html2text 

```
sed -n -e "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" -e "s/.*<text>\(.*\)<\/text>.*/<p>\1<\/p>/p" timeline \
| html2text --ascii
```
We can see it formated, if this gives you proper results you might want to pipe the whole thing, like this

```

curl --basic --user $USER:$PASS http://twitter.com/statuses/friends_timeline.xml \
| sed -n -e "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" -e "s/.*<text>\(.*\)<\/text>.*/<p>\1<\/p>/p" \
| html2text --ascii

```
**NOTE: the sed command doesn't have the "timeline" at the end, this is because that was the input, now the input is the curl command we piped.**



_**Final Script**_

This script just puts together both parts, the update and the timeline fetch, it's simple and you should be able to understand it easily.
```

#!/bin/bash

case $1 in
	-u | --update ) 
			echo "Actualizar seleccion"
			curl --basic --user $USER:$PASS --data status="$2" http://twitter.com/statuses/update.xml > /dev/null
		;;
	-f | --friends )
			echo "Friends Timeline"
			curl --basic --user $USER:$PASS http://twitter.com/statuses/friends_timeline.xml \
			| sed -n -e "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" -e "s/.*<text>\(.*\)<\/text>.*/<p>\1<\/p>/p" \
			| html2text -style pretty -ascii \
			| less
		;;
esac

```

_**Other things that could be done**_
[LIST]
[*]As you might noticed here the tweet goes first followed by the author. I think it would be more readable first the author then the tweet but due to the sed nature this can't be done. Probably with awk, you'd be able to do it.
[*]Instead of using html2text you can send the sed output to an .html file, and open it in your browser. You might want to do this to store it for later or.... well store it for later :lolflag:
[*]Using sed you could also keep the avatar line of the friends_timeline.xml file. So if you do this and send the output to an .html file you'd see the avatars
[*]I didn't considered the time the tweets where done, but just like with avatars you could keep the date/time using sed. You just have to go creative with how you'd format the output (That's why I added HTML tags, they do a decent formatting work)
[*]Direct Messaging with curl is not impossible but it doesn't seem practical. Look at the Twitter API for more info.
[*]Finally the friends_timeline.xml has a lot of info you could find useful you just gotta think how to format the file.
[/LIST]

_**sed Appendix**_
As I said at the begging sed is a filter and somehow a parser of text input. The syntax we are using here
```
sed [-n] -e "s/something_to_match/something_to_write/some_other_flags" inputfile
``` does exactly that: it looks at a line, sees if a pattern match and the writes something where the pattern matched. sed does this line by line. And I should notice that there are other commands beside 's/'.

Now our actual command ```
sed -n -e "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" -e "s/.*<text>\(.*\)<\/text>.*/<p>\1<\/p>/p" timeline
```
-n means it will do it's action but won't show us the result.

-e "s/$search/$replace/p" means that is the script to execute (one of many) and that sed will  print the line if it was modified. This makes sense due to the -n. Sed prints the lines even when we said it not to.

*now the expression itself:*
.*<text>\(.*\)<\/text>.* would be $search and means
> 
match anything | followed by <text> | store whatever is here | that's followed by </text> | no matter what's next


<p>\1<\/p> would be $replace and means
> Write <p> | then write what you stored | then write </p>

It's similar for the other expression "s/.*<name>\(.*\)<\/name>.*/<h4>\1<\/h4>/p" but with <name> and <p>


Well that's it. I'll appreciate any feedback to make this better. Hope you find it useful.

---

### Post by Sonsum on 2010-05-23
I know this thread is probably long dead, but I would like to know if there's a way to remove the asterisks around the author's name in your script.

I'm working on a script of my own to read out these updates and it works great, but hearing "asterisk asterisk asterisk" before and after every tweet is a little annoying.

Thanks a ton,
Sonsum

---

