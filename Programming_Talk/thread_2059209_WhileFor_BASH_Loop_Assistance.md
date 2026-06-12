---
title: "While/For BASH Loop Assistance"
date: 2012-09-17
forum: Programming Talk
---

### Post by Ryan79 on 2012-09-17
Hey all :) thanks again for help with the last script!

Got a new one for you guys... I've got it partially working, but it's not downloading the full range of files:

to explain what's going on:

There's a group of radar images (7 images per location) that I need to download, so there are two variables:

Location identifier (AKQ AMA AMX APD APX...)

and 0..7

What I've got going, and partially working is as follows:

```

#! /bin/bash

## setting variables

arrLoc=(AKQ AMA AMX APD APX)
varNumber=0
LIMIT=8

## Downloading files

while [ "$varNumber -lt "$LIMIT" ]
do
     for i in $arrLoc ; do
         wget -P /home/localdir http://imageurl/"$i"_"$varNumber".png ;
      done
varNumber=$(($varNumber+1))
done

```

this partially works in that is grabs the first location, AKQ, and downloads the 7 images for that location... but then it doesn't continue through the rest of the location list... any insights?

or... is there a better way to do this? was initially looking for a way to reference 2 arrays within a for loop, but couldn't really find anything that explained how to do that; then I found a while loop and that got me this far... 

Thanks again for the help :)

---

### Post by jrog on 2012-09-17
> **Ryan79 said:**
> Hey all :) thanks again for help with the last script!

Got a new one for you guys... I've got it partially working, but it's not downloading the full range of files:

to explain what's going on:

There's a group of radar images (7 images per location) that I need to download, so there are two variables:

Location identifier (AKQ AMA AMX APD APX...)

and 0..7

What I've got going, and partially working is as follows:

```

#! /bin/bash

## setting variables

arrLoc=(AKQ AMA AMX APD APX)
varNumber=0
LIMIT=8

## Downloading files

while [ "$varNumber -lt "$LIMIT" ]
do
     for i in $arrLoc ; do
         wget -P /home/localdir http://imageurl/"$i"_"$varNumber".png ;
      done
varNumber=$(($varNumber+1))
done

```this partially works in that is grabs the first location, AKQ, and downloads the 7 images for that location... but then it doesn't continue through the rest of the location list... any insights?

or... is there a better way to do this? was initially looking for a way to reference 2 arrays within a for loop, but couldn't really find anything that explained how to do that; then I found a while loop and that got me this far... 

Thanks again for the help :)

Shouldn't your for loop begin: 

```
for i in "${arrLoc[@]}"
```?

---

### Post by Ryan79 on 2012-09-17
> **jrog said:**
> Shouldn't your for loop begin: 

```
for i in "${arrLoc[@]}"
```?

That did it!! Thanks jrog :)

---

### Post by diesch on 2012-09-17
```
wget -P /home/localdir http://imageurl/{AKQ,AMA,AMX,APD,APX}_{1..8}.png
``` should do the job, too

---

### Post by jrog on 2012-09-17
> **Ryan79 said:**
> That did it!! Thanks jrog :)
No problem; glad it worked. :)

---

