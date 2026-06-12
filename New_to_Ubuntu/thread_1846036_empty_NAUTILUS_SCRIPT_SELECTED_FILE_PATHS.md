---
title: "empty NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by jmgl on 2011-09-18
hello guys,

I am trying to learn bash and finding some problems. I would just like to make a script which runs in gnuplot all the gnuplot scripts with extension, "*.gnuplot", selected in Nautilus.

To do it I started by something which I thought was going to be easier, and make a small program which list in another file, "files.txt", the files selected in Nautilus with extension "*.cfn". But, even before that, I wanted to do it with only one file. My mega-simple (and wrong) script looks like this:

```

#!/bin/bash
cd ~/Work/Programming/Bash/callFromNautilus/
echo "hello World" > files.txt
echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" >> files.txt

```So I was expecting that, after changing the rights of the ".sh" file and setting the "Open with other application" -> "use a custom command", when I double click a file "file1.cfn" I obtained a file called "files.txt" with two lines:
hello World
path/to/file/files1.cfn

Instead I only get the hello World sentence plus an empty extra line. I have tried so many things that I have found in the Internet, but all of them seem to give me the same result. In the documentation I found that NAUTILUS_SCRIPT_SELECTED_FILE_PATHS should give me the path of the files which are called separated by a "return", but I should be doing something wrong because that is not what I obtain.

A particular issue that also surprise me is that, if instead of
```

echo "hello World" > files.txt

```I write
```

echo "hello World" > >files.txt

```I obtain several lines of "hello World" when open several files at the same time (assuming that the file, files.txt, was empty at the start). That surprises me since I was expecting calling only once the script with all the paths of the files in NAUTILUS_SCRIPT_SELECTED_FILE_PATHS, instead of running several times the same script, as it seems is happening.

As you can see my understanding of the matter is really bad, but I have not found a documentation that covers such a naive issues...

I would really appreciate if someone could give me a small help here.

Thank you very much in advance,

Regards,

jmgl

---

