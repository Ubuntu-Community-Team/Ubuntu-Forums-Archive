---
title: "Cat-like command to dump text from START to END for Bush Video Archive?"
date: 2007-05-10
forum: Programming Talk
---

### Post by kentbye on 2007-05-10
I'm working on screen scraping the WhiteHouse.gov for a website that I'm helping out with, and I have a question.

Is there a commandline program or grep options that will display the text between two strings -- like the text between "<!-- BEGIN -->" & "<!-- END -->" ?

I'm trying to isolate the transcript text that appears between these two flags.

cat will dump the text
grep will also search for strings on a line.
But is there anything out there that will output everything in between into a file?

We're downloading the public domain streaming videos from WhiteHouse.gov, and transcoding them so that they're more accessible, and we wanted to also match up these videos with the transcripts.

Here's a sample page, and look at the page source to see the "<!-- BEGIN -->" & "<!-- END -->" tags:
[http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html](http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html)

It will be integrated into a full-blown George W. Bush video archival collection, and this will make it a lot easier to search for video quotes for people to remix.

Here's a sampling of some of the videos so far: 
[http://political-videos.blip.tv/](http://political-videos.blip.tv/)

Thanks,
-Kent.

---

### Post by jamescox84 on 2007-05-10
Here's a script I just wrote, could a python script like this do what you want.

```

#!/usr/bin/env python

# file: gettrans

import sys
import urllib 

if __name__ == '__main__':
    if len(sys.argv) != 3:
        print 'usage: %s <url> <outputfile>' % sys.argv[0]
        sys.exit()
    
    f = urllib.urlopen(sys.argv[1])
    page_source = f.read()
    f.close()

    start_tag = '<!-- BEGIN -->'
    end_tag = '<!-- END -->'

    start = page_source.find(start_tag) + len(start_tag)
    end = page_source.find(end_tag)

    transcript = page_source[start: end]

    try:
        f = open(sys.argv[2], 'w')
        f.write(transcript)
        f.close()
    except IOError:
        print 'Could not open %s' % sys.argv[2]

```

Use like this:
```

./gettrans http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html transcript.html

or

python gettrans http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html transcript.html

```

gettrans will need execute permistion.

---

### Post by cwaldbieser on 2007-05-10
> **kentbye said:**
> I'm working on screen scraping the WhiteHouse.gov for a website that I'm helping out with, and I have a question.

Is there a commandline program or grep options that will display the text between two strings -- like the text between "<!-- BEGIN -->" & "<!-- END -->" ?

I'm trying to isolate the transcript text that appears between these two flags.

cat will dump the text
grep will also search for strings on a line.
But is there anything out there that will output everything in between into a file?

We're downloading the public domain streaming videos from WhiteHouse.gov, and transcoding them so that they're more accessible, and we wanted to also match up these videos with the transcripts.

Here's a sample page, and look at the page source to see the "<!-- BEGIN -->" & "<!-- END -->" tags:
[http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html](http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html)

It will be integrated into a full-blown George W. Bush video archival collection, and this will make it a lot easier to search for video quotes for people to remix.

Here's a sampling of some of the videos so far: 
[http://political-videos.blip.tv/](http://political-videos.blip.tv/)

Thanks,
-Kent.

Assuming the file is "test.txt":
```

$ sed -n '/<!-- START -->/,/<!-- END -->/p' test.txt | grep -v -e '<!-- START -->' -e '<!-- END -->' 

```
The sed command only prints lines between the markers (inclusive).  The grep -v filters out the marker lines.

---

### Post by kentbye on 2007-05-10
Great!  Thanks.
I got it to work with the python script.
And I extended the code in order to make make the start_tag and end_tag input arguments (shown down below)

And for some reason the sed command didn't do anything.
Is it supposed to output to a file?

I did the following:
```
axel http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html;
sed -n '/<!-- START -->/,/<!-- END -->/p' 20070131-1.html | grep -v -e '<!-- START -->' -e '<!-- END -->';

```
And there is nothing that is output.

I renamed the "gettrans" file to "parse", and did a 
```
chmod +x parse
```

And here is the code for inputting the start and end tags:
```
#!/usr/bin/env python

# file: parse

import sys
import urllib 

if __name__ == '__main__':
    if len(sys.argv) != 5:
        print 'usage: %s <url> <start_tag> <end_tag> <outputfile>' % sys.argv[0]
        sys.exit()
    
    f = urllib.urlopen(sys.argv[1])
    page_source = f.read()
    f.close()

    start_tag = sys.argv[2]
    end_tag = sys.argv[3]

    start = page_source.find(start_tag) + len(start_tag)
    end = page_source.find(end_tag)

    transcript = page_source[start: end]

    try:
        f = open(sys.argv[4], 'w')
        f.write(transcript)
        f.close()
    except IOError:
        print 'Could not open %s' % sys.argv[4]
```

Here's what I entered to make it run:
```
parse 20070430-2.html '<!-- BEGIN -->' '<!-- END -->' 20070430-2.txt
```

Thanks again,
-Kent.

---

### Post by jamescox84 on 2007-05-11
Oh, this make my heart swell with joy when I see such things. The Free Software thing really working. Thanks for making use of my script, and for giving back you modifications. I know the program is probably only useful to you, but who knows.

---

### Post by cwaldbieser on 2007-05-11
> **kentbye said:**
> Great!  Thanks.

And for some reason the sed command didn't do anything.
Is it supposed to output to a file?

I did the following:
```
axel http://www.whitehouse.gov/news/releases/2007/01/20070131-1.html;
sed -n '/<!-- START -->/,/<!-- END -->/p' 20070131-1.html | grep -v -e '<!-- START -->' -e '<!-- END -->';

```
And there is nothing that is output.

-Kent.

Oops.  It should have been:
```

$ sed -n '/<!-- BEGIN -->/,/<!-- END -->/p' 20070131-1.html | grep -v -e '<!-- BEGIN -->' -e '<!-- END -->';

```
I typed "START" instead of "BEGIN" without thinking.

---

