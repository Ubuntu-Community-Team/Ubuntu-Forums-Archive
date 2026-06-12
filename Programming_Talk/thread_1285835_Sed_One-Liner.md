---
title: "Sed One-Liner"
date: 2009-10-08
forum: Programming Talk
---

### Post by mastermindg on 2009-10-08
I need to remove spaces before and after commas in a csv, i.e.:

Neighborhood  , CHANNEL NAME  , CHANNEL#  , DESCRIPTION

some fields have more than one space so I'd need something to remove ALL spaces before and after commas but NOT between the words.

Thanks. :guitar:

---

### Post by mastermindg on 2009-10-08
To remove multiple leading/trailing spaces...

```
sed 's;^ *;;;s; *, *;,;g;s; *$;;' a.txt > b.txt
```

---

### Post by mobilediesel on 2009-10-08
> **mastermindg said:**
> I need to remove spaces before and after commas in a csv, i.e.:

Neighborhood  , CHANNEL NAME  , CHANNEL#  , DESCRIPTION

some fields have more than one space so I'd need something to remove ALL spaces before and after commas but NOT between the words.

Thanks. :guitar:

```
sed 's/\( *\)\(,\)\( *\)/\2/g'
```

It finds any number of spaces just before and just after a comma and only leaves the comma.

---

### Post by djurny on 2009-10-08
maybe

sed "s/ \+\(,\) \+/\1/g" a.txt > b.txt

?

or combined with a previous post

sed "s/ \+, \+/,/g" a.txt > b.txt


edit: too late :)

---

### Post by mastermindg on 2009-10-08
I also need something to remove any commas after the 3rd comma in a line:

```
Rock,SIRIUS XM U ,43 ,Indie,Underground,Imports
```

I've got this:

```
s/,/ /4
```

which will replace the 4th comma with a space but it would be nice to be able to replace all after the 3rd, just in case there are more commas laying around.

---

### Post by mobilediesel on 2009-10-08
> **mastermindg said:**
> I also need something to remove any commas after the 3rd comma in a line:

```
Rock,SIRIUS XM U ,43 ,Indie,Underground,Imports
```

I've got this:

```
s/,/ /4
```

which will replace the 4th comma with a space but it would be nice to be able to replace all after the 3rd, just in case there are more commas laying around.

Are you getting the input from the Sirius/XM website? I'd like to see the whole list to play with.

---

### Post by mastermindg on 2009-10-08
I'm using curl to authenticate and pull down the channel list from this url:

[http://xmro.xmradio.com/xstream/service/account/channel_lineup.jsp](http://xmro.xmradio.com/xstream/service/account/channel_lineup.jsp)

Then I'm using a Python script - html2csv.py (google it) to convert it to csv....

Then I'm using sed to remove the headers,footers, and unnecessary spaces...

Finally, I'm using an app from sourceforge - csv2xml, to convert this to xml, from which I can use to build pretty much anything.

	```
curl -s -c xmonline.cookies -d "user_id=$USER" -d "pword=$PASS" http://xmro.xmradio.com/xstream/login_servlet.jsp > xmonlinelogin.out	
	curl -b $XM_COOKIE_FILE $XM_LISTINGS_URL -o $XM_OUTPUT_FILE	
	python html2csv.py $XM_OUTPUT_FILE
	sed '1,43d;164,187d;s/\( *\)\("\)\( *\)/\2/g' $XM_HOME/temp.csv > $XM_HOME/listings.csv
	csv2xml -m=0 < $XM_HOME/listings.csv > $XM_HOME/listings.xml
```

---

### Post by DaithiF on 2009-10-08
> **mastermindg said:**
> I also need something to remove any commas after the 3rd comma in a line:

```
Rock,SIRIUS XM U ,43 ,Indie,Underground,Imports
```I've got this:

```
s/,/ /4
```which will replace the 4th comma with a space but it would be nice to be able to replace all after the 3rd, just in case there are more commas laying around.
you can't delete all commas after the 3rd directly in sed, but you can use conditional branching ('t' command)to achieve the same effect ... ie. keep on replacing the 4th occurrence of a comma until you fail to match a 4th occurrence of a comma anymore
```
echo $teststr
rock,sirius,43,indie, underground,imports,etc
echo $teststr | sed ':a;s/,/ /4;ta' 
rock,sirius,43,indie  underground imports etc

```

---

### Post by geirha on 2009-10-08
> **mastermindg said:**
> ```
s/,/ /4
```g

---

### Post by mastermindg on 2009-10-08
This is my final listing.csv:

How can I replace unicode characters ()?

"Neighborhood","CHANNEL NAME","CHANNEL#","DESCRIPTION"
"Pop","SIRIUS XM Hits 1","2","Top 40 Hits"
"Pop","40s on 4","4","Forties Pop Hits/Big Band"
"Pop","50s on 5","5","First decade of Rock n Roll"
"Pop","60s on 6","6","Sixties Pop Hits"
"Pop","70s on 7","7","Classic 70s Hits/Oldies"
"Pop","80s on 8","8","Pop Hits of the 80s"
"Pop","90s on 9","9","Nineties Pop Hits"
"Country","The Roadhouse","10","Classic Country"
"Country","Outlaw Country","12","Rockin Country/Americana"
"Country","Willies Place","13","Texas Honky Tonk Music"
"Country","Bluegrass Junction","14","Bluegrass"
"Country","The Village","15","Contemporary  Traditional Folk"
"Country","The Highway","16","Todays New Country"
"Country","Prime Country","17","80s/90s/00s Country Hits"
"Pop","Elvis Radio","18","Elvis Presley 24/7"
"Pop","20 on 20","20","Todays Hits"
"Pop","SIRIUS XM Love","23","Favorite Adult Love Songs"
"Pop","The Blend","25","Adult Hits"
"Pop","The Pulse","26","Modern Adult Contemporary"
"Pop","The Bridge","27","Classic Hits"
"Pop","Escape","28","Beautiful Music"
"Pop","BBC Radio 1","29","New British Music"
"Pop","Pop2K","30","Hits Of The 2000s"
"Christian","The Message","32","Contemporary Christian Pop Hits"
"Christian","Praise","33","Gospel"
"Christian","enLighten","34","Southern Gospel"
"Pop","Limited Engagements","39","Exclusive Limited-Run Channels"
"Rock","Deep Tracks","40","Deep Classic Rock"
"Rock","Hair Nation","41","80s Hair Bands"
"Rock","Liquid Metal","42","Heavy Metal"
"Rock","SIRIUS XM U","43","Indie, Underground, Imports"
"Rock","1st Wave","44","Classic 80s Alternative Music"
"Rock","The Spectrum","45","Adult Album Rock*"
"Rock","Classic Vinyl","46","Early Classic Rock"
"Rock","Alt Nation","47","New Alternative"
"Rock","Octane","48","New Hard Rock"
"Rock","Classic Rewind","49","Later Classic Rock"
"Rock","The Loft","50","Acoustic Eclectic Rock"
"Rock","The Coffee House","51","Acoustic Singer-Songwriters"
"Rock","Faction","52","Action Sports Music"
"Rock","Boneyard","53","Hard and Heavy Classic Rock"
"Rock","Lithium","54","Grunge  90s Alternative Rock"
"Rock","Radio Margaritaville","55","Jimmy Buffetts*Radio Station*"
"Rock","Jam On","56","Jam Bands"
"Rock","Grateful Dead","57","Grateful Dead  Family"
"Rock","E Street Radio","58","24/7 Bruce Springsteen  the E Street Band"
"Rock","Underground Garage","59","Garage Rock"
"Hip-Hop  RB","Soul Town","60","Classic Soul"
"Hip-Hop  RB","Heart  Soul","62","Adult RB Hits"
"Hip-Hop  RB","The Groove","64","Old School RB"
"Hip-Hop  RB","Backspin","65","Old Skool Rap"
"Hip-Hop  RB","Shade 45","66","Uncut/Uncensored Hip-Hop"
"Hip-Hop  RB","Hip-Hop Nation","67","Hip-Hop"
"Hip-Hop  RB","The Heat","68","Rhythmic Hits"
"Jazz  Blues","Real Jazz","70","Classic Jazz"
"Jazz  Blues","Watercolors","71","Smooth/Contemporary Jazz"
"Jazz  Blues","Spa","72","New Age"
"Jazz  Blues","Siriusly Sinatra","73","Great American Songbook"
"Jazz  Blues","B.B. Kings Bluesville","74","Blues"
"Jazz  Blues","On Broadway","75","Show tunes"
"Jazz  Blues","Cinemagic","76","Movie soundtracks and more"
"Classical","SIRIUS XM Pops","77","Popular Classical"
"Classical","Symphony Hall","78","Classical"
"Classical","Met Opera Radio","79","Opera and Classical Vocal"
"Dance","Area","80","Mainstream  Underground Club Music"
"Dance","BPM","81","Current Dance"
"Dance","The Strobe","83","Disco Music"
"Dance","SIRIUS XM Chill","84","Smooth Electronica"
"Latin  World","Caliente","85","Latin Tropical Music"
"Latin  World","The Joint","86","Reggae"
"SIRIUS XM Showcase","Bootlegs","90","Exlusive Life Performances"
"Latin  World","Viva - Online Only","91","Latin Pop"
"SIRIUS XM Showcase","Music Showcase","92","Exclusic Music"
"SIRIUS XM Showcase","Comedy Showcase","93","Exclusive Comedy"
"SIRIUS XM Showcase","Talk Showcase","94","Exclusive Talk"
"Talk, News, NPR","OutQ Radio","98","OutQ GLTB"
"Family  Health","Radio Disney","115","Radio Disney"
"Family  Health","Kids Place Live","116","All Fun for Kids"
"Religion","Catholic Channel","117","Not What Youd Expect"
"Religion","EWTN Catholic Radio","118","EWTN Global Catholic Radio Network"
"Family  Health","Doctor Radio","119","Powered by NYU Langone Medical Center"
"Talk, News, NPR","CNN","122","CNN News"
"Talk, News, NPR","HLN","123","HLN"
"Talk, News, NPR","CNBC","127","CNBC"
"Talk, News, NPR","Bloomberg Radio","129","Bloomberg Radio/Business"
"Talk, News, NPR","POTUS","130","Unfiltered Political Talk"
"Talk, News, NPR","BBC World Service","131","BBC World Service"
"Talk, News, NPR","C-SPAN Radio","132","C-SPAN Radio"
"Talk, News, NPR","XM Public Radio","133","XM Public Radio"
"Talk, News, NPR","NPR Now","134","NPR News  Conversation"
"Talk, News, NPR","World Radio Network","135","News Around the World"
"Talk, News, NPR","PRX Public Radio","136","Public Interest Programming"
"Talk, News, NPR","SIRIUS Left","137","Liberal Talk"
"Talk, News, NPR","SIRIUS Patriot","138","Conservative Talk"
"Entertainment","SIRIUS XM Stars Too","139","Great Talk Radio for Guys"
"Sports","ESPN Radio","140","Sports Talk"
"Sports","SIRIUS XM Sports Nation","143","Your Home for College Sports Talk"
"Sports","Mad Dog Radio","144","Sports Radio with Chris Russo"
"Sports","PGA TOUR Network","146","The PGA TOUR - Golf Talk"
"Comedy","Blue Collar Radio","148","All-American Comedy"
"Comedy","The Foxxhole","149","Comedy, music, and more presented by Jamie Foxx"
"Comedy","Raw Dog Comedy","150","Comedy Uncensored"
"Comedy","Laugh USA","151","Family Comedy"
"Entertainment","SIRIUS XM Stars","155","Celebrity hosts and lifestyle programming"
"Entertainment","Oprah Radio","156","Oprah Radio"
"Entertainment","Cosmo Radio","162","Fun, Fearless, Female"
"Entertainment","SIRIUS XM Book Radio","163","Books  Drama"
"Talk, News, NPR","America Right","166","Conservative Talk"
"Talk, News, NPR","America Left","167","Progressive Talk"
"Talk, News, NPR","FOX News Talk","168","FOX News Talk"
"Talk, News, NPR","The Power","169","African-American Talk"
"Religion","Family Talk","170","Christian Talk"
"Entertainment","Road Dog Trucking","171","Truckers Channel"
"Sports","MLB Home Plate","175","24/7 MLB"
"Comedy","The Virus","202","The Opie  Anthony Show - XL"
"Sports","NHL Home Ice","204","NHL Talk and Play-by-Play"
"Sports","ESPN Deportes","225","Spanish Sports Talk  Play-by-Play"
"SIRIUS XM Showcase","Sports Nation 2","226","More Sports Talk"
"Religion","FamilyNet Radio","227","Christian Talk"

---

### Post by mobilediesel on 2009-10-08
> **mastermindg said:**
> This is my final listing.csv:

How can I replace unicode characters ()?

"Neighborhood","CHANNEL NAME","CHANNEL#","DESCRIPTION"
...
"Rock","1st Wave","44","Classic 80s Alternative Music"
...

Try this
```
sed 's/[^[:print:]]//g'
```
Matches all non-printable characters and removes them.

---

