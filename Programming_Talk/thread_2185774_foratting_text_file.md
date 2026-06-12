---
title: "foratting text file"
date: 2013-11-04
forum: Programming Talk
---

### Post by peter_brickles on 2013-11-04
HI Guys i am requesting a file from omdb.com using wget the results return in the following format 


[HTML]

{"Title":"Distant"
"Year":"2002"
"Rated":"12"
"Released":"20 Dec 2002"
"Runtime":"1 h 50 min"
"Genre":"Drama"
"Director":"Nuri Bilge Ceylan"
"Writer":"Nuri Bilge Ceylan
 Cemil Kavukçu"
"Actors":"Muzaffer Özdemir
 Emin Toprak
 Zuhal Gencer
 Nazan Kirilmis"
"Plot":"After his wife leaves him
a photographer has an existential crisis and tries to cope with his cousin's visit."
"Poster":"http://ia.media-imdb.com/images/M/MV5BMTI2MzcxMzc5M15BMl5BanBnXkFtZTcwNDM4NzUyMQ@@._V1_SX300.jpg"
"imdbRating":"7.4"
"imdbVotes":"8
949"
"imdbID":"tt0346094"
"Type":"movie"
"Response":"True"}

[/HTML]

what i need to to format them so all sections are on one line ie 



[HTML]

{"Title":"Distant"
"Year":"2002"
"Rated":"12"
"Released":"20 Dec 2002"
"Runtime":"1 h 50 min"
"Genre":"Drama"
"Director":"Nuri Bilge Ceylan"
"Writer":"Nuri Bilge Ceylan Cemil Kavukçu"
"Actors":"Muzaffer Özdemir Emin Toprak  Zuhal Gencer Nazan Kirilmis"
"Plot":"After his wife leaves him a photographer has an existential crisis and tries to cope with his cousin's visit."
"Poster":"http://ia.media-imdb.com/images/M/MV5BMTI2MzcxMzc5M15BMl5BanBnXkFtZTcwNDM4NzUyMQ@@._V1_SX300.jpg"
"imdbRating":"7.4"
"imdbVotes":"8
949"
"imdbID":"tt0346094"
"Type":"movie"
"Response":"True"}

[/HTML]

can any one see a way off accomplising this either sed awk etc from the cli ?

---

### Post by steeldriver on 2013-11-04
You could set the awk record separator to be newline-followed-by-double-quote, and split into colon-separated fields, then gsub any newlines in the second field

```

$ awk 'BEGIN {RS="\n\""; ORS=RS; FS=":"; OFS=FS} {gsub("\n"," ", $2); print}' imdb.txt
{"Title":"Distant"
"Year":"2002"
"Rated":"12"
"Released":"20 Dec 2002"
"Runtime":"1 h 50 min"
"Genre":"Drama"
"Director":"Nuri Bilge Ceylan"
"Writer":"Nuri Bilge Ceylan  Cemil Kavukçu"
"Actors":"Muzaffer Özdemir  Emin Toprak  Zuhal Gencer  Nazan Kirilmis"
"Plot":"After his wife leaves him a photographer has an existential crisis and tries to cope with his cousin's visit."
"Poster":"http://ia.media-imdb.com/images/M/MV5BMTI2MzcxMzc5M15BMl5BanBnXkFtZTcwNDM4NzUyMQ@@._V1_SX300.jpg"
"imdbRating":"7.4"
"imdbVotes":"8 949"
"imdbID":"tt0346094"
"Type":"movie"
"Response":"True"}

```

---

### Post by drmrgd on 2013-11-04
edit: never mind.  I see what you're trying to do now.  I missed the quotes around the text you wanted to put on one line.

Steeledriver's got it!

---

