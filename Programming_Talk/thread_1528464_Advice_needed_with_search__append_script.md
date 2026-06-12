---
title: "Advice needed with search / append script"
date: 2010-07-10
forum: Programming Talk
---

### Post by jimmy the saint on 2010-07-10
I am compiling a list of items and their various attributes into a spreadsheet to be converted into a searchable webpage spreadsheet (using Trellis).  I have a basic one up and running, but now I have hit a wall with how to simply finish adding the last bit of info and I was hoping i could get some advice on putting together a simple script to search for a list of items against a set of 4 html pages.

The situation:  I have a list of 380 items.  There are 4 webpages with a plethora of data about various other items, and what items are related to them.  I need to know if each of the 380 items in my list show up at all on any of those 4 webpages.

My Thoughts so far:  I can save the webpages as html and put together a script to search for each of the items in my list and append "yes" if they show up or "no" if they don't.  

The problem is that I don't know how to write even the simplest of bash (or any other) scripts.  Can someone point me in the right direction?  I would imagine grep and cat would be sufficient.  Am I right about that?  

Any advice or tips to put me in the right direction would be appreciated.  Thanks!

---

### Post by ju2wheels on 2010-07-10
```

#!/bin/bash
cd /tmp;
wget -m -nd http://somewebsite.com/index.html

if grep "searchterm" index.html > /dev/null; then
    echo "searchterm index.html yes" >> /tmp/searchresults.txt
else
    echo "searchterm index.html no" >> /tmp/searchresults.txt
fi

```

Just a quick example, but you can add looping to get the final result you are looking for.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by jimmy the saint on 2010-07-10
Thanks!

One question

Would there be a way to append the YES or NO to the source list file next to the term?
For example, the origional list file would end up looking like

```
Term YES
Term NO
Term NO
Term YES
```

---

### Post by ju2wheels on 2010-07-11
```

#!/bin/bash

SEARCHTERMS="/path/to/searchterms.txt";
WEBPAGES="/path/to/webpagelist.txt";
RESULTSFILE="/path/to/results.txt";

while read searchTerm; do
    blnFound=0;
    
    while read webPage; do
	tempFile=`mktemp`;
	
	if ! wget -q "${webPage}" -O "${tempFile}"; then
	    echo "ERROR: Failed to download ${webPage} to temp file ${tempFile}...";
	    exit 1;
	fi
	
	if grep "${searchTerm}" "${tempFile}" > /dev/null; then
	    blnFound=1;
	    
	    echo "${searchTerm} yes" >> "${RESULTSFILE}";
	    
	    break;
	fi
	
    done < "${WEBPAGES}"
    
    if [ "${blnFound}" == "0" ]; then
	echo "${searchTerm} no" >> "${RESULTSFILE}";
    fi
    
done < "${SEARCHTERMS}"

```

Alternatively, if you really want to modify the original file with the search terms, change the echo's above to output only yes or no, and then add this to the end of the above:

```

tempFile=`mktemp`;

paste "${SEARCHTERMS}" "${RESULTSFILE}" > "${tempFile}";

mv "${tempFile}" "${SEARCHTERMS}";

```

Note: none of the above is tested...

---

