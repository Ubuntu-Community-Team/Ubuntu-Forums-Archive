---
title: "OpenSubtitles retriever for Ubuntu: how to finish the script ..."
date: 2010-10-22
forum: Programming Talk
---

### Post by honeybear on 2010-10-22
Please find the script that retrieve a list of url, but how to make it download the right idmovie link or rar or zip of the *.nfo *.sub/*.txt file ... ?


```
 
#!/bin/sh

cd 
mkdir tmp
TMP=`mktemp`
TMPFILE="$HOME$TMP"
destinataire=$(zenity --entry --title "Search Subtitle" --text "Title"  --entry-text "" ) ; echo "You entered: $destinataire"
[ "$destinataire" = "" ] && exit
THEYEAR=$(zenity --entry --title "Search Subtitle" --text "The year of the movie:"  --entry-text "1990" ) ; echo "You entered: $THEYEAR"
[ "$THEYEAR" = "" ] && exit
THESTRING=`echo "$destinataire" | sed 's/\ /+/g'`
THEURL="http://www.opensubtitles.org/en/search2/sublanguageid-all/movieyearsign-1/movieyear-${THEYEAR}/moviename-${THESTRING}"
#Format
#http://www.opensubtitles.org/en/search2/sublanguageid-all/moviename-${THESTRING}
#http://www.opensubtitles.org/en/search2/sublanguageid-all/movieyearsign-1/movieyear-199x/moviename-the+name
wget -k "$THEURL" -O $TMPFILE
cat "$TMPFILE"  | grep -o 'http:[^"]*' |  grep idmovie
rm "$TMPFILE"












```

---

### Post by geirha on 2010-10-23
You can't realisticly parse html with tools like grep and sed. Look for some API first, and if there isn't any, use a language that has an htmlparser, like perl or python.

It took me less than a minute to find they did have an API:
[http://trac.opensubtitles.org/projects/opensubtitles/wiki/XMLRPC](http://trac.opensubtitles.org/projects/opensubtitles/wiki/XMLRPC)

I don't know if there's a usable tool for working with that in the shell though, you'll have to research a bit. Python and perl probably have some.

---

### Post by honeybear on 2010-10-23
> **geirha said:**
> You can't realisticly parse html with tools like grep and sed. Look for some API first, and if there isn't any, use a language that has an htmlparser, like perl or python.

It took me less than a minute to find they did have an API:
[http://trac.opensubtitles.org/projects/opensubtitles/wiki/XMLRPC](http://trac.opensubtitles.org/projects/opensubtitles/wiki/XMLRPC)

I don't know if there's a usable tool for working with that in the shell though, you'll have to research a bit. Python and perl probably have some.

Thank you. well I am not informatician. I have not notions about python, perl, not long long coding... simple end user, that's why I make it simple using bash... well, bash/sh is still powerful though... is there maybe something like qnapi for english ?

---

### Post by joopbraak on 2011-05-15
> **honeybear said:**
> Please find the script that retrieve a list of url, but how to make it download the right idmovie link or rar or zip of the *.nfo *.sub/*.txt file ... ?
It already exists...

[http://gnome-look.org/content/show.php/download_opensubtitle?content=68085](http://gnome-look.org/content/show.php/download_opensubtitle?content=68085)

I updated it to make it work in Ubuntu and incorporate the useragent check that opensubtitles now does.

Just save it with a name like "Download subtitle" in your ".gnome2/nautilus-scripts" folder and make it executable. Now all you have to do is right click on the movie and choose "Scripts/Download subtitle". The subtitle is automatically saved in the same folder with the same name as the movie (apart from the extension of course).

```

#!/usr/bin/env python

# Download subtitles from opensubtitles.org (nautilus version)
# Default language is english, to change the language change sublanguageid parameter
# in the searchlist.append function

# Carlos Acedo (carlos@linux-labs.net)
# Inspired on subdownloader
# License GPL v2

import os
import struct 
import subprocess
from xmlrpclib import ServerProxy, Error


def hashFile(name): 
      try: 
                longlongformat = 'q'  # long long 
                bytesize = struct.calcsize(longlongformat) 
                    
                f = open(name, "rb") 
                    
                filesize = os.path.getsize(name) 
                hash = filesize 
                    
                if filesize < 65536 * 2: 
                       return "SizeError" 
                 
                for x in range(65536/bytesize): 
                        buffer = f.read(bytesize) 
                        (l_value,)= struct.unpack(longlongformat, buffer)  
                        hash += l_value 
                        hash = hash & 0xFFFFFFFFFFFFFFFF #to remain as 64bit number  
                         
    
                f.seek(max(0,filesize-65536),0) 
                for x in range(65536/bytesize): 
                        buffer = f.read(bytesize) 
                        (l_value,)= struct.unpack(longlongformat, buffer)  
                        hash += l_value 
                        hash = hash & 0xFFFFFFFFFFFFFFFF 
                 
                f.close() 
                returnedhash =  "%016x" % hash 
                return returnedhash 
    
      except(IOError): 
                return "IOError"

# ================== Main program ========================

server = ServerProxy("http://api.opensubtitles.org/xml-rpc")
peli = os.environ['NAUTILUS_SCRIPT_SELECTED_FILE_PATHS'].strip('\n')

try:
    myhash = hashFile(peli)
    print myhash
    size = os.path.getsize(peli)
    session =  server.LogIn("","","en","OS Test User Agent")
    print session
    token = session["token"]
    
    searchlist = []
    searchlist.append({'moviehash':myhash,'moviebytesize':str(size)})
    
    moviesList = server.SearchSubtitles(token, searchlist)
    print(moviesList)
    if moviesList['data']:
        kdialog_items = []
        for item in moviesList['data']:
            kdialog_items += [item['SubFileName'],item['LanguageName'],item['MatchedBy']]
    
        args = ['zenity','--list','--width=750','--height=700','--text=Select subtitle',]
        args += ['--column=File name','--column=Lang','--column=Mathed by']
    
        resp = subprocess.Popen(args+ kdialog_items,stdout=subprocess.PIPE).communicate()[0].strip('\n')

        if resp != '':
            index = 0
            data = moviesList['data']
            
            while index < len(data) and data[index]['SubFileName'] != resp:
                index += 1

            sub = data[index]
            
            subFileName = os.path.splitext(os.path.basename(peli))[0] + os.path.splitext(sub['SubFileName'])[1]
            subDirName = os.path.dirname(peli)
            subURL = sub['SubDownloadLink']
            
            response = os.system("wget -O - '{0}' | gunzip > '{1}'".format(subURL, os.path.join(subDirName,subFileName)))
            
            if response != 0:
                os.system('zenity --error --text="An error occurred downloading or writing the subtitle"')
        
    else:
        os.system('zenity --error --text="No subtitles found"')
    
    server.Logout(session["token"])
except Error, v:
    os.system('zenity --error --text="An error occurred"')

```

---

