---
title: "a lot of problems in this script"
date: 2012-05-30
forum: Programming Talk
---

### Post by jumbobits on 2012-05-30
I am trying to make a shell script in ubuntu to automatically download all images in an album (not large albums) on imgur by just doing a command like

imgur-dl [album ID here]

then i wanted to set that up as a global command and make another script that will accept a user id and run imgur automatically, and auto downloading normal links as well.

So far imgur-dl works perfectly (2nd easiest part)

/usr/bin/imgur-dl
```

#!/bin/bash

curl -silent http://imgur.com/a/$@ |
#download page

grep http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* |
#grab imgur image links

grep href |
#grab only the good links

grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z]* |
#grab only actual links

uniq > a.temp
#filter duplicates and write the wget link file

wget --quiet -i a.temp
#download links

rm a.temp

```The tricky section for me is getting the reddit page to parse and hand off 1 at a time to imgur-dl.I am trying to do this by parsing the website separately for every type of link. a third type of link isn't even in there yet, but it should be fairly easy.

I think the issue is either or all trying to cat file contents into a variable, not setting up a while loop properly or something with the way i used the stat command. either way, this is very frustrating.

the error i get is

```
./reddit-dl: line 21: stat -c%s c.temp: No such file or directory
``````

#!/bin/bash

curl --silent http://www.reddit.com/user/$@/submitted/ |
#dump site

#start getting direct links
grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* | uniq > b.temp
#grab direct links and drop duplicates
wget --quiet -i b.temp
#download direct links


#start album loop
curl --silent http://www.reddit.com/user/$@/submitted/ |
#grab site
grep -o http://imgur\.com/a/[a-zA-Z0-9]* | uniq | sed -e 's/^...................//' > c.temp
#grab links and hoosier filter to c.temp

filesize="stat -c%s c.temp"

while [ 2 < "$filesize" ]
do

head -n1 c.temp > d.temp
#output the first line in c.temp to d.temp

imglink="cat d.temp"
#try to put the contents of d.temp into a variable

cat d.temp

imgur-dl "$imglink"
#try to download said album

sed 1d c.temp > c.temp
#remove the first line of c.temp

done

rm *.temp


```This is a reference album link [http://imgur.com/a/7DUjm](http://imgur.com/a/7DUjm)

here is a reference user page [http://www.reddit.com/user/Inkbath/submitted/](http://www.reddit.com/user/Inkbath/submitted/)

and help for a newbie would be great.

---

### Post by Vaphell on 2012-05-30
```
filesize=$( stat -c%s c.temp )
```

```
while [ 2 -lt "$filesize" ]
```
or
```
while (( 2 < filesize ))
```

---

### Post by jumbobits on 2012-05-30
Thanks for the reply.

I made your recommended change and some others as well.

```
#!/bin/bash

curl --silent http://www.reddit.com/user/$@/submitted/ |
#dump site

#start getting direct links
grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* | uniq > b.temp
#grab direct links and drop duplicates
wget --quiet -i b.temp
#download direct links

#start album loop
curl --silent http://www.reddit.com/user/$@/submitted/ |
#grab site
grep -o http://imgur\.com/a/[a-zA-Z0-9]* | uniq | sed -e 's/^...................//' > c.temp
#grab links and hoosier filter to c.temp

filesize=$( stat -c%s c.temp)

while [ 2 -lt "$filesize" ]
do

head -n1 c.temp > d.temp
#output the first line in c.temp to d.temp

imglink=$( cat d.temp)
#try to put the contents of d.temp into a variable

echo $imglink
imgur-dl "$imglink"
#try to download said album


sed 1d c.temp >> c.temp
#remove the first line of c.temp

done

#rm *.temp

```

Here is what happens

```
rm *.*
bender@bender-VPCF23EFX:~/cjm3350/as_promised$ ./reddit-dl Inkbath
7DUjm
7DUjm
7DUjm
7DUjm
^C
bender@bender-VPCF23EFX:~/cjm3350/as_promised$ ls
6RJ82h.jpg    ADMs2.jpg.1  cC7qd.jpg     CnALs.jpg.1  d0vka.jpg.1  I5RUE.jpg.1  jTa1s.jpg.2   LPkpB.jpg    OHkFPh.jpg.1  trHr5h.jpg.1  vXpj2.jpg.2   wPWPP.jpg     xtZNy.jpg.1   Zcuczh.jpg.2
6RJ82h.jpg.1  ADMs2.jpg.2  cC7qd.jpg.1   CnALs.jpg.2  d0vka.jpg.2  I5RUE.jpg.2  l7LJTh.jpg    LPkpB.jpg.1  OHkFPh.jpg.2  trHr5h.jpg.2  WnoQRh.jpg    wPWPP.jpg.1   xtZNy.jpg.2   Zcucz.jpg
6RJ82h.jpg.2  ajxWS.jpg    cC7qd.jpg.2   cO0MP.jpg    d1kYi.jpg    jJt6H.jpg    l7LJTh.jpg.1  LPkpB.jpg.2  OHkFP.jpg     trHr5.jpg     WnoQRh.jpg.1  wPWPP.jpg.2   xYjVc.jpg     Zcucz.jpg.1
6RJ82.jpg     ajxWS.jpg.1  cChsPh.jpg    cO0MP.jpg.1  d1kYi.jpg.1  jJt6H.jpg.1  l7LJTh.jpg.2  mXGzr.jpg    OHkFP.jpg.1   trHr5.jpg.1   WnoQRh.jpg.2  xGeTAh.jpg    xYjVc.jpg.1   Zcucz.jpg.2
6RJ82.jpg.1   ajxWS.jpg.2  cChsPh.jpg.1  cO0MP.jpg.2  d1kYi.jpg.2  jJt6H.jpg.2  l7LJT.jpg     mXGzr.jpg.1  OHkFP.jpg.2   trHr5.jpg.2   WnoQR.jpg     xGeTAh.jpg.1  xYjVc.jpg.2   zm3Ij.jpg
6RJ82.jpg.2   a.temp       cChsPh.jpg.2  c.temp       d.temp       JL28l.jpg    l7LJT.jpg.1   mXGzr.jpg.2  pKqut.jpg     ubczz.jpg     WnoQR.jpg.1   xGeTAh.jpg.2  yu0Jc.jpg     zm3Ij.jpg.1
ADMs2"        b.temp       cChsP.jpg     CvCVO.jpg    GFo8A.jpg    JL28l.jpg.1  l7LJT.jpg.2   nHwI8.jpg    pKqut.jpg.1   ubczz.jpg.1   WnoQR.jpg.2   xGeTA.jpg     yu0Jc.jpg.1   zm3Ij.jpg.2
ADMs2".1      BvUFH.jpg    cChsP.jpg.1   CvCVO.jpg.1  GFo8A.jpg.1  JL28l.jpg.2  LPkpBh.jpg    nHwI8.jpg.1  pKqut.jpg.2   ubczz.jpg.2   wPWPPh.jpg    xGeTA.jpg.1   yu0Jc.jpg.2
ADMs2".2      BvUFH.jpg.1  cChsP.jpg.2   CvCVO.jpg.2  GFo8A.jpg.2  jTa1s.jpg    LPkpBh.jpg.1  nHwI8.jpg.2  reddit-dl     vXpj2.jpg     wPWPPh.jpg.1  xGeTA.jpg.2   Zcuczh.jpg
ADMs2.jpg     BvUFH.jpg.2  CnALs.jpg     d0vka.jpg    I5RUE.jpg    jTa1s.jpg.1  LPkpBh.jpg.2  OHkFPh.jpg   trHr5h.jpg    vXpj2.jpg.1   wPWPPh.jpg.2  xtZNy.jpg     Zcuczh.jpg.1

```


i think there is a problem with the way i am using c.temp and d.temp, and it doesnt appear to do anything right.

ill post more info in a bit after some more testing

---

### Post by jumbobits on 2012-05-30
Here is my "debug" version

I also just realized that >> appends to the end of files and not replaces them, so i fixed that. i also realized that the reference link has only 1 album link on it, ill try to find another, better one in a bit.

reddit-dl
```
#!/bin/bash

curl --silent http://www.reddit.com/user/$@/submitted/ |
#dump site

#start getting direct links
grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* | uniq > b.temp
#grab direct links and drop duplicates
echo "download normal links below"
echo "."
cat b.temp
echo "."
wget --quiet -i b.temp
#download direct links

#start album loop
curl --silent http://www.reddit.com/user/$@/submitted/ |
#grab site
grep -o http://imgur\.com/a/[a-zA-Z0-9]* | uniq | sed -e 's/^...................//' > c.temp
#grab links and hoosier filter to c.temp

echo "initial un modified c.temp"
echo "."
cat c.temp
echo "."

filesize=$( stat -c%s c.temp)

while [ 2 -lt "$filesize" ]
do

echo "start of while loop"

head -n1 c.temp > d.temp
#output the first line in c.temp to d.temp

imglink=$( cat d.temp)
#try to put the contents of d.temp into a variable

echo "send $imglink imgur-dl"
imgur-dl "$imglink"
#try to download said album

echo "contents of c.temp before sed"
echo "."
echo "."
cat c.temp
echo "."
echo "."
sed 1d c.temp > c.temp
#remove the first line of c.temp
echo "contents of c.temp after sed"
echo "."
echo "."
cat c.temp
echo "."
echo "."

echo "end of while loop"

done

#rm *.temp
```/usr/bin/imgur-dl
```
#!/bin/bash

echo "begin download album - $@"

curl -silent http://imgur.com/a/$@ |
#download page

grep http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* |
#grab imgur image links

grep href |
#grab only the good links

grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z]* |
#grab only actual links

uniq > a.temp
#filter duplicates and write the wget link file

wget --quiet -i a.temp
#download links

rm a.temp

echo "done download album - $@"

```After running a link through with more than 1 album, the script will set the first line as the variable like I want, download it nearly fine (it grabs both higher and lower res versions of the pic, but i can fix that), then finally when it goes to remove the first line after downloading, it eats the whole file (or at least the contents).



as of this posting, this link is perfectly safe, just pics of cars and scenic images, kinda relaxing after being tortured by the shell.  and only some of the album links will work because it only grabs the first reddit page and albums with higher res images get a slide show or 1 image at a time view, which will probably be a pain in the *** to get working. Although i may be able to grep the thumbnail ids and somehow relink them to the real images, but thats later, i need to get this working first.


```

bender@bender-VPCF23EFX:~/cjm3350/as_promised$ ./reddit-dl PenisWUBWUBWUBPenis
download normal links below
.
.
initial un modified c.temp
.
tpNvn
dxNAd
CZYgg
dxNAd
EBtjU
.
start of while loop
send tpNvn imgur-dl
begin download album - tpNvn
done download album - tpNvn
contents of c.temp before sed
.
.
tpNvn
dxNAd
CZYgg
dxNAd
EBtjU
.
.
contents of c.temp after sed
.
.
.
.
end of while loop
start of while loop
send  imgur-dl
begin download album - 
done download album - 
contents of c.temp before sed
.
.
.
.




```


[COLOR=Red]edit[/COLOR]:



i finally got it to properly cycle through the entire list, but now once it is done, it will just loop forever, trying to pass no arguments to imgur-dl. could it be that my logic for the while loop is also including 0  when comparing the file size to the integer? (i read it as "while 0 is less than the filesize of c.temp" or is it really saying less than or equal to?)

```


#!/bin/bash

curl --silent http://www.reddit.com/user/$@/submitted/ |
#dump site

#start getting direct links
grep -o http://i\.imgur\.com/[a-zA-Z0-9]*\.[a-zA-Z0-9]* | uniq > b.temp
#grab direct links and drop duplicates
echo "download normal links below"
echo "."
cat b.temp
echo "."
wget --quiet -i b.temp
#download direct links

#start album loop
curl --silent http://www.reddit.com/user/$@/submitted/ |
#grab site
grep -o http://imgur\.com/a/[a-zA-Z0-9]* | uniq | sed -e 's/^...................//' > c.temp
#grab links and hoosier filter to c.temp

echo "initial un modified c.temp"
echo "."
cat c.temp
echo "."

filesize=$( stat -c%s c.temp)

while [ 0 -lt "$filesize" ]
do

echo "start of while loop"

head -n1 c.temp > d.temp
#output the first line in c.temp to d.temp

imglink=$( cat d.temp)
#try to put the contents of d.temp into a variable

echo "send $imglink imgur-dl"
imgur-dl "$imglink"
#try to download said album

echo "contents of c.temp before sed"
echo "."
echo "."
cat c.temp
echo "."
echo "."
sed -i 1d c.temp
#remove the first line of c.temp
echo "contents of c.temp after sed"
echo "."
echo "."
cat c.temp
echo "."
echo "."

echo "end of while loop"

done

#rm *.temp


```

---

### Post by Vaphell on 2012-05-31
you overengineered it :) you don't have to manually cut and paste line by line, *while read x; do ...; done < file* will do it for you

```

while read -r imglink
do
  echo img-dl "$imglink"
done < c.temp
rm c.temp


-- output --
img-dl tpNvn
img-dl dxNAd
img-dl CZYgg
img-dl dxNAd
img-dl EBtjU

```

---

### Post by jumbobits on 2012-05-31
that is a much more elegant solution than what i was doing for sure

---

