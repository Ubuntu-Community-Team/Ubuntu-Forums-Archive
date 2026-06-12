---
title: "Please explain this gawk!"
date: 2009-11-22
forum: Programming Talk
---

### Post by Barriehie on 2009-11-22
So I exported my FF bookmarks and needed a way to pull out just the url's to add to my whitelist.  I'm new to gawk and after thrashing around for a bit I found this [link](http://www.tek-tips.com/viewthread.cfm?qid=1441421&page=1) via google.  Can someone please explain:
```

 awk 'BEGIN{FS="<";RS=">"}/</{print $2}' /path/to/textfile 

```

I understand the FS= and RS= but what is the /</ in the middle and what is $2???  I think the $2 is the substring of the string that was examined  but I don't understand the /</.  I used:
```

gawk 'BEGIN{FS="HREF=";RS="DATE_ADDED"}/</{print $2}' /path/to/textfile

```
and it worked rather nicely on my file.  Just had to run 2 macros with emacs and some search/replace and it was done; BUT :)  I think it could've been done in one fell swoop with gawk.

TIA,
Barrie

---

### Post by iponeverything on 2009-11-22
$2 is the second field.  ($0 is whole line)

< > are the field separators.

---

### Post by ghostdog74 on 2009-11-22
are you sure that one works? here's another

```

gawk 'BEGIN{RS="</a>/";IGNORECASE=1}
{
  for(i=1;i<=NF;i++){
    if ( $i ~ /href/){
      sub(/.*href=\042/,"",$i)
      print "link: "$(i)
    }
  }
}' bookmarks.html


```

---

### Post by Barriehie on 2009-11-22
Thank you, iponeeverythig - that makes sense about the $numbers and ghostdog74 what you've posted makes a bit more sense than the one liner I found!

Barrie

---

### Post by Barriehie on 2009-11-23
Hey!  Alright I've got something useful here.  Ghostdog74 I've added to your original post and now have a way of updating my whitelist for squid automagically by exporting my bookmarks from FF!  Thanks once again for your bit of explanation.

```

#
# Gawk file to transform FF exported bookmarks
# to a line item list of URL's.
#

BEGIN { RS="/<a>/"; IGNORECASE=1 }
{
  for ( i=1; i<=NF; i++)
      {
        if ( $i ~ /href="/)
           {
                sub(/.*href=\042/,"",$i)

                #
                # Remove preceeding http(s):// and trailing /.*"
                #
                sub("http.*//", "", $i) && sub ("/.*", "", $i)

                   #
                   # Remove the local links
                   #
                   if ( $i !~ /^file/ )
                        {
                            print $(i)
                        }
           }
      }
}


```

Sample output:
```

http://www.alldatasheet.com/"
www.alldatasheet.com
 
http://hyperphysics.phy-astr.gsu.edu/hbase/hframe.html"
hyperphysics.phy-astr.gsu.edu
 
http://nte01.nteinc.com/nte/NTExRefSemiProd.nsf/$$Search"
nte01.nteinc.com
 
http://mouser.com/"
mouser.com
 
http://www.beckerelectronics.com/techpage.htm"
www.beckerelectronics.com

```

Barrie

---

