---
title: "Python link validator problem"
date: 2009-06-12
forum: Programming Talk
---

### Post by matmatmat on 2009-06-12
I have the following script:
```

import sys
import os
import re
pages = []
if len(sys.argv) > 1:
        for root, dirs, files in os.walk(sys.argv[1]):
                for f in files:
                        filename = os.path.join(root, f)
                        if (filename.endswith('.html')) or (filename.endswith('.htm')):
                                pages.append(filename)

for page in pages:
        f = open(page, "r")
        count = 1
        for line in f:
                if re.match("<a href=\"", line):
                        split1 = re.split("<a href=\"", line)[1]
                        split = re.split("\"", split1)
                        if  not os.path.exists(split[0]):
                                if not split[0].startswith("www"):
                                        print "################### Link Error ###################"
                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0])
                                        print line

                elif re.match("<a href='", line):
                        split1 = re.split("<a href='", line)[1]
                        split = re.split("'", split1)
                        if  not os.path.exists(os.path.abspath(split[0])):
                                if not split[0].startswith("www"):
                                        print "################### Link Error ###################"
                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0])
                                        print line
                

                count += 1 

```
when run:
```

$ python linkvalidator.py /home/matio/Documents/website/
################### Link Error ###################
Error with line 50 in file /home/matio/Documents/website/fun.htm, the page '06 - Track 6.mp3' doesn't exist:
<a href="06 - Track 6.mp3">Some music!</a>

################### Link Error ###################
Error with line 25 in file /home/matio/Documents/website/school_quiz.html, the page 'fun.htm' doesn't exist:
<a href="fun.htm">Back</a>

################### Link Error ###################
Error with line 11 in file /home/matio/Documents/website/imagemap/overview.htm, the page '../map.htm' doesn't exist:
<a href="../map.htm">Back to map page</a>



```
when i ls:
```

$ ls ~/Documents/website/
06 - Track 6.mp3  fun.htm            jblock.gif        miss.htm~  quote10.html   resources                student_office.htm   video.htm
art.png           fun.htm~           les.htm       mr_.htm     quote10.html~  r.png                    student_office.htm~  video.htm~
b.png             german_songs.htm   lessons.htm~      mr.htm~    quote1.html    school_quiz.html         style_change.js      videos
buddies.htm       german_songs.htm~  library.png       mrs_kane.htm       quote2.html    school_quiz.html~        style_change.js~     v_map.htm
buddies.htm~      gi.htm             main_office.htm   mrs_kane.htm~      quote3.html    school_quiz_process.js   style.htm            v_map.htm~
canteen.htm       gi.htm~            main_office.htm~  office.png         quote4.html    school_quiz_process.js~  style.htm~           year_6_2.htm
canteen.htm~      imagemap           map2.htm          overview.jpg       quote5.html    slideshow.htm            Templates            year_6_2.htm~
chapel.png        images             map.htm           parents.htm        quote6.html    slideshow.htm~           test.htm             year_6.htm
cl.htm            index.html         map.htm~          q_a.htm            quote7.html    sportshall_outside.png   tour.htm             year_6.htm~
credits.htm       interviews.htm     mblock.jpg        q_a.htm~           quote8.html    spotshall.png            video_2.htm~
css               interviews.htm~    miss.htm  quote0.html        quote9.html    stained_glass.png        video_3.htm~

```

---

### Post by matmatmat on 2009-06-12
The problem seems to be with the os.path.abspath()
& with everyone but the last it seems to think that the file (eg 'fun.htm') is in my current working dir?

---

### Post by matmatmat on 2009-06-12
Also can anyone find a way to match even if there is whitespace or text?
eg:
```

                        <li id="home"><a href="index.html"><span>Home</span></a></li>

```

EDIT:
I now have this:
```

import sys
import os
import re
pages = []
if len(sys.argv) > 1:
        for root, dirs, files in os.walk(sys.argv[1]):
                for f in files:
                        filename = os.path.join(root, f)
                        if (filename.endswith('.html')) or (filename.endswith('.htm')):
                                pages.append(filename)

lcount = 0
ecount = 0
for page in pages:
        f = open(page, "r")
        count = 1
        for line in f:
                if re.match("[\sa-zA-Z<>=\"\']+<a href=\"", line):
                        split1 = re.split("<a href=\"", line)[1]
                        split = re.split("\"", split1)
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not split[0].startswith("www"):
                                        print "################### Link Error ###################"
                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0].rstrip())
                                        print line
                                        ecount += 1
                        lcount += 1

                elif re.match("[\sa-zA-Z<>=]+<a href='", line):
                        split1 = re.split("<a href='", line)[1]
                        split = re.split("'", split1)
                        if  not os.path.exists(os.path.abspath(split[0])):
                                if not split[0].startswith("www"):
                                        print "################### Link Error ###################"
                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0])
                                        print line
                                        ecount += 1
                        lcount += 1

                count += 1        
print "################### Summary ###################"
print "%i errors in %i links" % (ecount, lcount)

```
when run it says there are 76 error (most I know are valid links) & 336 links (there are more)
it is ignoring the example I gave in the beginning of the post

---

### Post by soltanis on 2009-06-12
Whitespace: strip away with the string.strip() method.

Matching: use re.search, not re.match. I have no clue why but re.match only looks for pattern matches at the beginning of a string (leave it to python developers to develop useless regular expression functions).

---

### Post by matmatmat on 2009-06-13
Thanks, I think that I need to cd into any sub-dirs because when run on one dir with no sub-dirs it worked, how would I do that?

---

### Post by matmatmat on 2009-06-13
Thanks for the help
It now works:
```

import os
import re
pages = []
if len(sys.argv) > 1:
        for root, dirs, files in os.walk(sys.argv[1]):
                for f in files:
                        filename = os.path.join(root, f)
                        if (filename.endswith('.html')) or (filename.endswith('.htm')):
                                pages.append(filename)


lcount = 0
ecount = 0
for page in pages:
        f = open(page, "r")
        count = 1
        for line in f:
                if re.match("[\sa-zA-Z<>=\"\']*<a href=\"", line):
                        split1 = re.split("<a href=\"", line)[1]
                        split = re.split("\"", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "################### Link Error ###################"
		                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
                        lcount += 1

                elif re.match("[\sa-zA-Z<>=]*<a href='", line):
                        split1 = re.split("<a href='", line)[1]
                        split = re.split("'", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "################### Link Error ###################"
		                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
                        lcount += 1

                count += 1        
print "################### Summary ###################"
print "%i errors in %i links" % (ecount, lcount)

```
any ideas on how to improve?

---

### Post by Greyed on 2009-06-13
> **soltanis said:**
> Matching: use re.search, not re.match. I have no clue why but re.match only looks for pattern matches at the beginning of a string (leave it to python developers to develop useless regular expression functions).

Leave it to some random forum poster to declare a rather useful function is useless simply because he cannot see a use for it.

---

