---
title: "Another sed question"
date: 2013-05-17
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-05-17
Hi Guys,

I've been playing with sed and have something I need some help understanding.

I have some text that looks like this:

```
[ ] Turn on rice cooker @ 16:30
```

I would like to put a ; after the ].
At first I thought I could use:

```

sed -e 's/[ ]/[ ];/'

```

But I ended up with:

```

[[ ];] Turn on rice cooker @ 16:30

```

I tried:
```

sed -e 's/[]/[];/'

```
and got an error message that 
```
sed: -e expression #1, char 9: unterminated `s' command


```

What is the best way to add the semi colon?

---

### Post by Lars Noodén on 2013-05-17
You have to escape the square brackets in the first part of the regex to get them treated as individual characters.  Or else sed will think you are looking for the set of characters listed between them.

```

sed -e 's/\[ \]/[ ];/'

```

Also, mind the space(s).

---

### Post by GrouchyGaijin on 2013-05-17
Thank you Lars!

---

### Post by Lars Noodén on 2013-05-17
You're welcome.  If you want to see more of what square brackets are and how they work when not escaped check out this link:

[http://www.regular-expressions.info/posixbrackets.html](http://www.regular-expressions.info/posixbrackets.html)

---

### Post by GrouchyGaijin on 2013-05-19
Hi Lars (or anyone passing by),

I have another question for you.

I run a script that uploads video to YouTube.  The script returns the url for the video.

I have everything before the part I need stripped out with a sed command and then I want to add:

```

{youtube}important_part_of_the_url?rel=0{/youtube}

```

I've almost got it.

I've set the command as:
```


test.txt | sed 's/^.*=//'| sed 's/$/?rel=0/'| sed 's/^/{youtube} /' | sed 's/$/{\/\youtube}/' >


```

The thing is, that puts a space after the {youtube} and before the url starts.

Example:
```

{youtube} eRXvk7cb3VE?rel=0{/youtube}

```

Do you know how I can get rid of that space?

---

### Post by Lars Noodén on 2013-05-19
I'm not clear on what the sample input would be and the desired output.  But you can write the sed lines in two other ways:

```

# this
cat test.txt | sed 's/^.*=//' -e 's/$/?rel=0/' -e 's/^/{youtube} /' -e  's/$/{\/\youtube}/' 

# or this 
cat test.txt | sed 's/^.*=//; s/$/?rel=0/; s/^/**{youtube} /**; s/$/{\/\youtube}/' 

```

As for the space, it looks like you are adding it on purpose. Check the boldfaced part of the second example above for the location.  Try removing the trailing space.

---

### Post by trent.josephsen on 2013-05-19
That's because you have a space in your repl string:
```
sed 's/^/{youtube} /'
                  ^-- right here
```

You can do multiple sed commands in a single line by separating them with ; -- no need for four pipes or a cat.
```
sed -e 's/^.*=//; s/$/?rel=0/; s/^/{youtube}/; s/$/{\/\youtube}/' test.txt
```
However, you can also do this in a single replacement:
```
sed -e 's#^.*=\(.*\)#{youtube}\1?rel=0{/youtube}#' test.txt
```
which will turn a file full of [https://www.youtube.com/watch?v=2IHxFRROHCA](https://www.youtube.com/watch?v=2IHxFRROHCA) into a list of {youtube}2IHxFRROHCA?rel=0{/youtube} (which is what I assume you're going for).

(ninja edit -- too slow)

---

### Post by Vaphell on 2013-05-19
drop ?rel=0 too, it's junk. video id is that 11 char long string, you can take advantage of that. Probably you can extract it easily with grep
```
grep -oP '[A-Za-z0-9_-]{11}'
```

---

### Post by GrouchyGaijin on 2013-05-19
Thanks Guys,

 I didn't realize I had put that space in.
The ?rel=0 is so that when someone is done watching a particular video I've embedded on the website they don't see a bunch of other "related" videos as suggestions.  I *think* that with just the 11 character string, those suggestions pop up at the end of a clip.

---

### Post by Vaphell on 2013-05-19
probably but you still don't need to store that rel, in a file with a bunch of video ids it's nothing more than a redundant information and a waste of space.
```
videoid1&rel=0
videoid2&rel=0
videoid3&rel=0
...
```
Add it only when you need it, loop that will do that is trivial, eg
```
while read v_id
do
  # generate html page links here or whatever
  url="http://youtube/**${v_id}**?rel=0"
  echo $url
done < video_ids.txt
```

---

### Post by GrouchyGaijin on 2013-05-19
Actually the end goal is to have the {youtube}url?rel=0{/youtube} copied to my clipboard so I can paste it into the CMS when I post a new article with a video link.
I'm not sure how to  automatically  copy the data I want.  I'm trying to look that up right now.

---

### Post by GrouchyGaijin on 2013-05-19
Thanks for the help guys!
I found that:

```

xclip -in -selection c 

```

does what I want.
That combined with the help you guys gave me has made life just a tad bit easier.

---

