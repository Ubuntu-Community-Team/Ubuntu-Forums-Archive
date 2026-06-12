---
title: "Beginners bash help"
date: 2011-05-07
forum: Programming Talk
---

### Post by Planetes on 2011-05-07
I'm trying to learn bash and in my attempt to dig up some resources and examples I ran into this script from [http://www.intuitive.com/wicked/showscript.cgi?060-bbcnews.sh](http://www.intuitive.com/wicked/showscript.cgi?060-bbcnews.sh)

```
#!/bin/sh

# bbcnews - report the top stories on the BBC World Service

url="http://news.bbc.co.uk/2/low/technology/default.stm"

lynx -source $url | \
  sed -n '/Last Updated:/,/newssearch.bbc.co.uk/p' | \
  sed 's/</\
</g;s/>/>\
/g' | \
  grep -v -E '(<|>)' | \
  fmt | \
  uniq

```I was hoping someone could explain some of the craziness that is going on in there.
Specifically:

'(<|>)'  

and 
's/</\
</g;s/>/>\
/g' | \ 

I vaguely understand what each of the commands do. It seems like there is a lot of handling of the text here, so i'm not certain the script is of good quality, but as I am new the author has my benefit of the doubt. I have been away for awhile so as always any help, comments, pointers, tips, tricks or all around knowledge is greatly appreciated.

---

### Post by DaithiF on 2011-05-08
> **Planetes said:**
> 
Specifically:

'(<|>)'  

  grep -v -E '(<|>)' 
suppresses (-v) lines which contain either of the characters < or >

> 
and 
's/</\
</g;s/>/>\
/g' | \ 

inserts a newline before each occurrence of < and after each occurrence of >
so basically its trying to separate out the stuff within tags into separate lines from stuff outside tags.

sed -e 's/</\n</g' -e 's/>/>\n/g' 
would have been a slightly more readable version for versions of sed which support using \n for newlines (which includes the gnu sed that comes with ubuntu and most other linux distros)

---

### Post by Planetes on 2011-05-08
I believe I understand now. Thank you for your time and explanation.

---

