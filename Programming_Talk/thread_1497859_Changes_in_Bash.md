---
title: "Changes in Bash?"
date: 2010-05-31
forum: Programming Talk
---

### Post by fallenshadow on 2010-05-31
I used to be on Ubuntu 8.10 which I believe has Bash 3. Now im on Ubuntu 10.04 which has Bash 4.

I have a script which no longer works as a result of the newer Bash. 

So does anyone know of something which has been changed in Bash?

---

### Post by Linteg on 2010-05-31
There is some information [here]("http://wiki.bash-hackers.org/bash4")

---

### Post by diesch on 2010-05-31
[http://tiswww.case.edu/php/chet/bash/NEWS](http://tiswww.case.edu/php/chet/bash/NEWS) lists the changes

---

### Post by fallenshadow on 2010-05-31
Thanks guys for both of your offerings. However I am finding the first one much easier to read. :)

I will try patching up this script now... might report back later.

---

### Post by fallenshadow on 2010-06-05
Hmm... didn't really have any luck patching the script myself, mainly because I didn't write it. I don't understand some of it... is there any bash master willing to help me out?

I can post it here if ye like.

---

### Post by geirha on 2010-06-05
Try to trim the script down to the bare minimum that still shows the problem, then post that. You might even see the problem yourself when you do that.

---

### Post by fallenshadow on 2010-06-05
I think that this may be the problematic line of code. However it could be a problem with the pre-testing code above it.

Does this line look ok?

[PHP]unzip -aa -j -p ${FILE} "META-INF/MANIFEST.MF" | sed -e '/^[ \t]*$/d' > "${JAD}"[/PHP]

Need a Bash master because some of this means nothing to me! :D

---

### Post by geirha on 2010-06-05
Err, slow response from the forums today. Sorry about this double post.

---

### Post by geirha on 2010-06-05
That line appears to extract the META-INF/MANIFEST.MF file from a jar-file to stdout. The output (contents of the manifest file) is filtered through sed which removes empty lines and lines containing only whitespaces, and is finally written to a file name "$JAD" (whatever that variable holds)

If you think that line is the problematic one, add set -x before it, and set +x after it. set -x turns on a debugging mode, it will show what will actually be executed after all variables have been expanded. set +x turns off the debugging mode.
```

set -x
unzip -aa -j -p ${FILE} "META-INF/MANIFEST.MF" | sed -e '/^[ \t]*$/d' > "${JAD}"
set +x

```
For good practice, all expansions ( "$foo", "`foo`", "$(foo)", etc...) should be doublequoted. In this case ${FILE} was not, so I recommend you add quotes around it; though jar files usually don't contain any special characters that will make that break.

---

### Post by gmargo on 2010-06-05
> **fallenshadow said:**
> I think that this may be the problematic line of code. However it could be a problem with the pre-testing code above it.

You have not yet described the actual problem.

---

### Post by fallenshadow on 2010-06-07
Well the actual problem is stated above. Basically this script used to "create" (extract) a .jad file from a .jar archive. 

The debug stuff didn't really help so here is the full script.

[PHP]
# safety check 1
FILE=$1
if [ ! -f "${FILE}" ]; then
  echo "Input file '${FILE}' missing, exiting."
  exit 1
fi

# safety check 2
JAD="${FILE%.*}.jad"
if [ -f "${JAD}" ]; then
  echo "${JAD} already exists, overwrite? (y/N)"
  read tmpans
  answer=$(echo "$tmpans" | tr '[:upper:]' '[:lower:]')
  if [ "$answer" != "y" ] && [ "$answer" != "yes" ]; then
    echo "Not overwriting ${JAD}, exiting."
    exit 1
  else
    rm -f "${JAD}"
  fi
fi

# unzip the internal manifest, changing line endings to our local OS
# the sed action removes blank lines, with or without spaces/tabs
#set -x
unzip -aa -j -p "${FILE}" "META-INF/MANIFEST.MF" | sed -e '/^[ \t]*$/d' > "${JAD}"
#set +x

# generic variables
echo "MIDlet-Jar-URL: ${FILE}" >> "${JAD}"
echo "MIDlet-Info-URL: http://" >> "${JAD}"

# actual jarball size
FILESIZE=$(stat -c%s "${FILE}")
echo "MIDlet-Jar-Size: ${FILESIZE}" >> "${JAD}"

# weee
echo "Created ${JAD}."

exit 0
[/PHP]

---

### Post by geirha on 2010-06-07
You said it was a bash script, but it doesn't have a she-bang (#!/bin/bash). Though, as far as I can see, you only use features defined by POSIX, so bash3 vs bash4 should not be the issue; that script should also run with sh.

What is the actual error message?

Have you tried running that unzip line manually, on a jar-file?
```

unzip -aa -j -p foo.jar "META-INF/MANIFEST.MF"
unzip -aa -j -p foo.jar "META-INF/MANIFEST.MF" | sed -e '/^[ \t]*$/d'

```

BTW, a portable way to get the filesize is
```
filesize=$(wc -c < "$FILE")
```

---

### Post by gmargo on 2010-06-07
> **fallenshadow said:**
> Well the actual problem is stated above. 

Sorry to be a pest about this, but no, the "actual problem" has never been stated.  Your entire bug report was "I have a script which no longer works as a result of the newer Bash."

On this problematic line of code you don't say why you think it is so.  What result do you see?  And what did you expect to see?  Which half of the pipeline is not doing what you expect?  Is the MANIFEST file really there and non-zero?

---

### Post by fallenshadow on 2010-08-29
I found a program which I can run in Wine to do this task.

So I will abandon this script and mark this as solved.

---

