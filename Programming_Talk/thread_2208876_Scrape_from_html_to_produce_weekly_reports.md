---
title: "Scrape from html to produce weekly reports"
date: 2014-03-02
forum: Programming Talk
---

### Post by mehmetaergun on 2014-03-02
I'm tasked with producing weekly reports from a wordpress website for a volunteer organization. I would like to automate this task and learn some coding along the way. (The task is really easy and doing it by hand takes not too much time, but I see this as a very good opportunity to learn coding on a script level.)

So far, all I could do was to get a list of links from the website and put them in a single html file. I would like to next convert parts of this html into a document. But I don't know where to start and I have (as you can see) minimal understanding of scripts and coding; I was hoping you could give me some pointers and guidance... 

Here's the format of the weekly reports that I want to produce:
[COLOR=#333333][FONT=Georgia]**February 18, 2014. **[/FONT][/COLOR][[COLOR=#1155cc][FONT=Georgia]**_"Kaos GL&#8217;s Military Brochure for Homosexuals"_**[/FONT][/COLOR]]("http://lgbtinewsturkey.com/2014/02/18/turkish-military-regulations-for-homosexuals/")
[COLOR=#000000][FONT=Georgia]*"The health checks of persons to be drafted into the military are conducted according to the procedures and principles of the Turkish Armed Forces Health Capability Regulations. Articles 17/3, 17/3- D/4 of the Appendix of Diseases and Disorders of the aforementioned regulations define psychosexual disorder and advanced psychosexual disorder.*[/FONT][/COLOR]"

Here's the code I got working so far. It gets the links and outputs them into a single html file:
```

#!/bin/bash

# Set the current month interactively
# Warning: This script executes arbitrary user input.
# In real-world code, you should never pass unsanitized user input directly to eval because doing so can provide a vector for arbitrary code execution.
echo "Enter the current year in YYYY format"
read DATE_YYYY
echo "Enter the current month in MM format"
read DATE_MM
echo "Enter the range of the days you need to retrieve (inclusive) in DDDD format (instead of DD-DD)"
read DATE_RANGE
DIGIT12=$(echo $DATE_RANGE | cut -c 1,2)
DIGIT34=$(echo $DATE_RANGE | cut -c 3,4)

# Set the Wordpress address
WEBBY='http://lgbtinewsturkey.com'
HOST_WEBBY='lgbtinewsturkey'

# Set file name for links to be saved to on step 1
SAVE_FILE='lgbtinews-weekly.html'

# Set python path for Step 2 if Mac OS X (NEEDED for BeautifulSoup)
# Commented because couldn't figure out BeautifulSoup..
#if [ "$(uname -s)" == "Darwin" ]
#    then
#    PYTHON_X='/opt/local/bin/python2.7'
#    else
#    PYTHON_X=$(which python)
#fi

# Step 1
# Get that month's URLs, trim them, save them to a single file
curl --silent "${WEBBY}/${DATE_YYYY}/${DATE_MM}/" | 
    # insert line breaks
    tr ">" "\n" | 
    # find only this month's lgbtinews links
    grep "${HOST_WEBBY}" | 
    grep $DATE_MM | 
    # output the links only
    perl -lne 'm!(http://.*\/)!; print $1' | 
    grep -v wordpress |
    sort | 
    uniq | 
    grep -v page | 
    # blank lines not needed 
    awk NF | 
    # first line not needed
    awk ' NR > 1 ' | 
    # get the links in range we are interested in
    awk -F/ -v firstdate=${DIGIT12} -v seconddate=${DIGIT34} '{ if ($6 >= firstdate && $6 <= seconddate) print $0 }' |
    # download the links you received with curl to single html file
    xargs -I {} curl {} >> $SAVE_FILE

```

Here's one of the news items, as an example to what I'm trying to parse: 
[http://lgbtinewsturkey.com/2014/02/18/turkish-military-regulations-for-homosexuals/](http://lgbtinewsturkey.com/2014/02/18/turkish-military-regulations-for-homosexuals/)

Basically, I would like to have a script that goes to the links I get thru the above script, get the link itself, the date, the title, and the first paragraph of the news item, and write them in a text file. I would appreciate any help.

---

### Post by SeijiSensei on 2014-03-02
I don't know how complex this task is, but I would recommend [PHP]("http://www.php.net/") as the language.  You can read entire web pages into a string or an array of lines, then parse it for whatever information you want to extract.  There are many languages that can do this, like Perl and python for instance, but PHP has a lot of built-in functions that work with HTML that can simplify the job.

Once upon a time I created a site about the Open Golf Championship, better known as the "British Open."  I wrote little PHP scripts that scraped weather data, pairings and schedules, and scores from a variety of sites.  It was pretty easy to do, and I hadn't programmed much since taking FORTRAN in college some 40+ years ago.

If the sites you want to monitor offer [RSS feeds]("http://en.wikipedia.org/wiki/RSS"), you should look into using those. RSS uses XML, a language for which PHP also has parsers.

---

### Post by mehmetaergun on 2014-03-03
> **SeijiSensei said:**
>  I wrote little PHP scripts that scraped weather data, pairings and schedules, and scores from a variety of sites. 

Would you be able to share those (or, any ideas for keywords I could use to find similar scripts)?

---

### Post by Jake_Paine on 2014-03-04
I would also recommend PHP for this, WordPress creates RSS feeds automatically which possibly provides a lot of the information you require already? - [http://lgbtinewsturkey.com/feed/](http://lgbtinewsturkey.com/feed/)

The PHP parser you would want to look into is - [http://uk3.php.net/xml](http://uk3.php.net/xml)

---

### Post by SeijiSensei on 2014-03-04
> **mehmetaergun said:**
> Would you be able to share those (or, any ideas for keywords I could use to find similar scripts)?

I'm afraid I don't have them any more.  This was well over a dozen years ago for a site that no longer exists.

---

### Post by mehmetaergun on 2014-03-04
Thanks a lot for the pointers! I'll look into this.

---

### Post by Habitual on 2014-03-04
[http://bournetoraiseshell.com/article.php?story=20100813204255221](http://bournetoraiseshell.com/article.php?story=20100813204255221)

---

### Post by mehmetaergun on 2014-03-04
> **Habitual said:**
> [http://bournetoraiseshell.com/article.php?story=20100813204255221](http://bournetoraiseshell.com/article.php?story=20100813204255221)

Links forwards to their index page

---

### Post by Habitual on 2014-03-04
> **mehmetaergun said:**
> Links forwards to their index page

fixed. 
Thanks for pointing that out.

---

### Post by mehmetaergun on 2014-03-04
thanks for the link!

---

### Post by Habitual on 2014-03-04
> **mehmetaergun said:**
> thanks for the link!

You're very welcome.

---

### Post by ssam on 2014-03-05
The python beautiful soup library is very helpful for parsing HTML [http://www.crummy.com/software/BeautifulSoup/](http://www.crummy.com/software/BeautifulSoup/)

---

