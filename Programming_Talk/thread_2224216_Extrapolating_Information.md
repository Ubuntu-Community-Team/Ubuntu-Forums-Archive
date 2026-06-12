---
title: "Extrapolating Information"
date: 2014-05-15
forum: Programming Talk
---

### Post by peter_brickles on 2014-05-15
HI GUys I am querying omdbapi wich is returning some good results for me 


> [http://www.omdbapi.com/?t=Nostalgia%20for%20the%20Light](http://www.omdbapi.com/?t=Nostalgia%20for%20the%20Light)

returns 

> {"Title":"Nostalgia for the  Light","Year":"2010","Rated":"N/A","Released":"17 Mar  2011","Runtime":"90 min","Genre":"Documentary,  Drama","Director":"Patricio Guzmán","Writer":"Patricio  Guzmán","Actors":"Gaspar Galaz, Lautaro Núñez, Luís Henríquez,  Miguel","Plot":"In Chile's Atacama Desert, astronomers peer deep into  the cosmos in search for answers concerning the origins of life. Nearby,  a group of women sift through the sand searching for body  ...","Language":"Spanish, English","Country":"France, Germany, Chile,  Spain, USA","Awards":"6 wins & 5  nominations.","Poster":"http://ia.media-imdb.com/images/M/MV5BMTU1MjU1NTgxOF5BMl5BanBnXkFtZTcwOTgyNTg0NA@@._V1_SX300.jpg","Metascore":"85","imdbRating":"7.6","imdbVotes":"1,886","imdbID":"tt1556190","Type":"movie","Response":"True"}

i oulwd now like to find a nice east way to exprapolate this 

so to format as csv each field being followed by information such as 


> 


Title,Nostalgia for the Light
Year, 2010
Rated, N/A
Released,17 Mar 2011
Runtime, 90 min
Genre,Documentary, Drama
Director,Patricio Guzmán
Writer,Patricio Guzmán
Actors,Gaspar Galaz, Lautaro Núñez, Luís Henríquez, Miguel
Plot,"In Chile's Atacama Desert, astronomers peer deep into the cosmos in search for answers concerning the origins of life. Nearby, a group of women sift through the sand searching for body"
Language,Spanish, EnglishTitle,Nostalgia for the Light
Year, 2010
Rated, N/A
Released,17 Mar 2011
Runtime, 90 min
Genre,Documentary, Drama
Director,Patricio Guzmán
Writer,Patricio Guzmán
Actors,Gaspar Galaz, Lautaro Núñez, Luís Henríquez, Miguel
Plot,"In Chile's Atacama Desert, astronomers peer deep into the cosmos in search for answers concerning the origins of life. Nearby, a group of women sift through the sand searching for body"
Language,Spanish, English
Country,France, Germany, Chile, Spain, USA
Awards,6 wins & 5 nominations
Poster,[http://ia.media-imdb.com/imagesMMV5BMTU1MjU1NTgxOF5BMl5BanBnXkFtZTcwOTgyNTg0NA@@._V1_SX300.jpg](http://ia.media-imdb.com/imagesMMV5BMTU1MjU1NTgxOF5BMl5BanBnXkFtZTcwOTgyNTg0NA@@._V1_SX300.jpg)
Metascore,85
imdbRating,7.6
imdbVotes,1,886
imdbID,tt1556190
Type,movieResponse


Country,France, Germany, Chile, Spain, USA
Awards,6 wins & 5 nominations
Poster,[http://ia.media-imdb.com/imagesMMV5BMTU1MjU1NTgxOF5BMl5BanBnXkFtZTcwOTgyNTg0NA@@._V1_SX300.jpg](http://ia.media-imdb.com/imagesMMV5BMTU1MjU1NTgxOF5BMl5BanBnXkFtZTcwOTgyNTg0NA@@._V1_SX300.jpg)
Metascore,85
imdbRating,7.6
imdbVotes,1,886
imdbID,tt1556190
Type,movieResponse



---

### Post by ofnuts on 2014-05-15
Simple matter in python:

```

#! /usr/bin/python
# -*- coding: utf-8 -*-

import urllib2,urllib,json,sys

omdbURL='http://www.omdbapi.com/?t='
    
def omdbData(movieTitle):
    connection=None
    try:
        try:     
            request = urllib2.Request(omdbURL+urllib.quote(movieTitle))
            connection = urllib2.urlopen(request)
            return json.load(connection)
        except urllib2.HTTPError, e:     
            print 'HTTP error: %s' % e.msg
            return None;
        except urllib2.URLError, e:     
            print 'Cannot retrieve URL: %s' % e.reason
            return None;
        except Exception, e:
            print 'Unexpected error: %s' % e 
            return None;
    finally:
        if connection:
            connection.close()

def dumpData(jsonData):
    for k,v in jsonData.items():
        print '%s,%s' % (k,v)

if len(sys.argv) > 1:
    data=omdbData(sys.argv[1])
    dumpData(data)
else:
    print 'Usage: %s movie_title' % sys.argv[0]

```

---

### Post by peter_brickles on 2014-05-16
> **ofnuts said:**
> Simple matter in python:

```

#! /usr/bin/python
# -*- coding: utf-8 -*-

import urllib2,urllib,json,sys

omdbURL='http://www.omdbapi.com/?t='
    
def omdbData(movieTitle):
    connection=None
    try:
        try:     
            request = urllib2.Request(omdbURL+urllib.quote(movieTitle))
            connection = urllib2.urlopen(request)
            return json.load(connection)
        except urllib2.HTTPError, e:     
            print 'HTTP error: %s' % e.msg
            return None;
        except urllib2.URLError, e:     
            print 'Cannot retrieve URL: %s' % e.reason
            return None;
        except Exception, e:
            print 'Unexpected error: %s' % e 
            return None;
    finally:
        if connection:
            connection.close()

def dumpData(jsonData):
    for k,v in jsonData.items():
        print '%s,%s' % (k,v)

if len(sys.argv) > 1:
    data=omdbData(sys.argv[1])
    dumpData(data)
else:
    print 'Usage: %s movie_title' % sys.argv[0]

```

thanks ofnuts that works great is there any way we can include the year for the film eg for films that have been remade 

for example the film "True Grit" 

> 

./grabomd "True Grit"

Plot,A tough U.S. Marshal helps a stubborn young woman track down her father's murderer.
Rated,PG-13
Response,True
Language,English
Title,True Grit
Country,USA
Writer,Joel Coen (screenplay), Ethan Coen (screenplay), Charles Portis (novel)
Metascore,80
imdbRating,7.7
Director,Ethan Coen, Joel Coen
Released,22 Dec 2010
Actors,Jeff Bridges, Hailee Steinfeld, Matt Damon, Josh Brolin
Year,2010
Genre,Adventure, Drama, Western
Awards,Nominated for 10 Oscars. Another 31 wins & 85 nominations.
Runtime,110 min
Type,movie
Poster,[http://ia.media-imdb.com/images/M/MV5BMjIxNjAzODQ0N15BMl5BanBnXkFtZTcwODY2MjMyNA@@._V1_SX300.jpg](http://ia.media-imdb.com/images/M/MV5BMjIxNjAzODQ0N15BMl5BanBnXkFtZTcwODY2MjMyNA@@._V1_SX300.jpg)
imdbVotes,188,831
imdbID,tt1403865




but the url can specify 

[http://www.omdbapi.com/?t=True%20Grit&y=1969](http://www.omdbapi.com/?t=True%20Grit&y=1969)  

to give the followinbg results for the 1969 file 


> 
{"Title":"True Grit","Year":"1969","Rated":"N/A","Released":"11 Jun  1969","Runtime":"128 min","Genre":"Adventure, Western,  Drama","Director":"Henry Hathaway","Writer":"Charles Portis (novel),  Marguerite Roberts (screenplay)","Actors":"John Wayne, Glen Campbell,  Kim Darby, Jeremy Slate","Plot":"A drunken, hard-nosed U.S. Marshal and a  Texas Ranger help a stubborn young woman track down her father's  murderer in Indian  territory.","Language":"English","Country":"USA","Awards":"Won 1 Oscar.  Another 7 wins & 5  nominations.","Poster":"http://ia.media-imdb.com/images/M/MV5BMTYwNTE3NDYzOV5BMl5BanBnXkFtZTcwNTU5MzY0MQ@@._V1_SX300.jpg","Metascore":"N/A","imdbRating":"7.4","imdbVotes":"27,075","imdbID":"tt0065126","Type":"movie","Response":"True"}



thnka for you help it was more than i expected 

Pete

---

### Post by ofnuts on 2014-05-16
Not much different:
```

#! /usr/bin/python
# -*- coding: utf-8 -*-

import urllib2,urllib,json,sys

omdbURL='http://www.omdbapi.com/?'
omdbParms=['t','y']  

def omdbData(args):
    connection=None
    parms=[omdbParms[i]+'='+urllib.quote(arg) for i,arg in enumerate(args)]
    url=omdbURL+'&'.join(parms)+'&r=JSON'
    print url
    try:
        try:     
            request = urllib2.Request(url)
            connection = urllib2.urlopen(request)
            return json.load(connection)
        except urllib2.HTTPError, e:     
            print 'HTTP error: %s' % e.msg
            return None;
        except urllib2.URLError, e:     
            print 'Cannot retrieve URL: %s' % e.reason
            return None;
        except Exception, e:
            print 'Unexpected error: %s' % e 
            return None;
    finally:
        print '**** finally! ***'
        if connection:
            connection.close()

def dumpData(jsonData):
    for k,v in jsonData.items():
        print '%s,%s' % (k,v)



if len(sys.argv) <= 1:
    print 'Usage: %s movie_title [year]' % sys.argv[0]
else:
    data=omdbData(sys.argv[1:])
    dumpData(data)

```

---

