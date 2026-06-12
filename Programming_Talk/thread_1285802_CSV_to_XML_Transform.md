---
title: "CSV to XML Transform"
date: 2009-10-08
forum: Programming Talk
---

### Post by mastermindg on 2009-10-08
I've got a CSV that is formatted like below:

Neighborhood  , CHANNEL NAME  , CHANNEL#  , DESCRIPTION
Pop , SIRIUS XM Hits 1  , 2  , Top 40 Hits
Pop , 40s on 4  , 4  , Forties Pop Hits/Big Band

The first line are the tags and the following lines are the data. This is what I'd like it to be:

  <channel>
		<Neighborhood>Pop</Neighborhood>
		<CHANNEL#>2</CHANNEL#>
        	<CHANNEL_NAME>SIRIUS XM Hits 1</CHANNEL_NAME>
                <DESCRIPTION>Top 40 Hits</DESCRIPTION> 
  </channel>
.....

What would be the simplest method of accomplishing this?

---

### Post by unutbu on 2009-10-08
Well, this is not a very general solution, but it should work 
in this particular situation:

Save this to ~/bin/channel_csv2xml.py
[PHP]
#!/usr/bin/env python
import sys
import csv
csvobj=csv.reader(open(sys.argv[1]))
csvobj.next()
for fields in csvobj:
    print '''<channel>
<Neighborhood>%s</Neighborhood>
<CHANNEL#>%s</CHANNEL#>
<CHANNEL_NAME>%s</CHANNEL_NAME>
<DESCRIPTION>%s</DESCRIPTION>
</channel>
    '''%tuple([field.strip() for field in fields])[/PHP]

Make it executable:
```

chmod +x ~/bin/channel_csv2xml.py
```

Run it like this:
```

channel_csv2xml.py csvfile
```

On the csvfile you posted, the output is
```
<channel>
<Neighborhood>Pop</Neighborhood>
<CHANNEL#>SIRIUS XM Hits 1</CHANNEL#>
<CHANNEL_NAME>2</CHANNEL_NAME>
<DESCRIPTION>Top 40 Hits</DESCRIPTION>
</channel>
    
<channel>
<Neighborhood>Pop</Neighborhood>
<CHANNEL#>40s on 4</CHANNEL#>
<CHANNEL_NAME>4</CHANNEL_NAME>
<DESCRIPTION>Forties Pop Hits/Big Band</DESCRIPTION>
</channel>
    
```

---

### Post by mastermindg on 2009-10-08
Thanks for the great script!!

One problem....It's only processing the first 30 lines. It looks like this may need to be processed using chunks ? not really sure.

---

### Post by unutbu on 2009-10-08
Not sure why it is stopping after 30 lines. Could you post the first 31 lines?

---

### Post by mastermindg on 2009-10-08
I figured out why it was stopping:

Line 32: 

```
Rock , SIRIUS XM U  , 43  , Indie, Underground, Imports
```

Looks like they put a comma in the description. Is there anyway to filter out commas past the 3rd comma? 

Keep in mind that this is a product of an html parse so data will change periodically. I'm cool with leaving the tags as is since this is more for my own interests anyway.

---

### Post by mastermindg on 2009-10-08
Thanks for the help! I always enjoy learning something new. Unfortunately, I went with another solution:

csv2xml - it's a C-based app on sourceforge. It successfully parsed my file by using the header as tags.

---

### Post by Reiger on 2009-10-08
The problem seems that the delimiter here is not a comma; but " , ": i.e. some whitespace, a comma and then some more whitespace. So it looks like csv.reader is configured to use comma delimiters and this causes a hiccup in the print statement.

---

