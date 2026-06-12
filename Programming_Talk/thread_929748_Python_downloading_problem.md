---
title: "Python downloading problem"
date: 2008-09-25
forum: Programming Talk
---

### Post by ratmandall on 2008-09-25
```
import urllib

inurl=raw_input('Enter a url to download from: ')

fle = urllib.urlopen(inurl)

lclsve = open(url.split('/')[-1], 'w')

lclsve.write(fle.read())

fle.close()

lclsve.close()

```

When I first executed this code I downloaded an image and it saved to my home folder properly, but when ever I execute it again no matter what url I enter the file is always saved as the first file name I downloaded,
```
avatar78101_12.gif
```

Say I enter [http://google.com](http://google.com) 
It saves to my home folder as
avatar78101_12.gif
Sure when I rename it to 'filename'.html I can view it in my browser but that's not my point.

How do I make it save like e.g
```
Enter a url to download from: http://ubuntuforums.org/images/smilies/guitar.gif
```
and saves as guitar.gif in my home folder

---

### Post by Zugzwang on 2008-09-25
I have no clue why it originally worked, but in the line "lclsve = open(url.split('/')[-1], 'w')" you are splitting the contents of the "url" variable, which should be undefined since you put the path to the "inurl" variable.

---

### Post by ratmandall on 2008-09-25
> **Zugzwang said:**
> I have no clue why it originally worked, but in the line "lclsve = open(url.split('/')[-1], 'w')" you are splitting the contents of the "url" variable, which should be undefined since you put the path to the "inurl" variable.

 I can't get that line to work without it

---

### Post by ratmandall on 2008-09-25
> **Zugzwang said:**
> I have no clue why it originally worked, but in the line "lclsve = open(url.split('/')[-1], 'w')" you are splitting the contents of the "url" variable, which should be undefined since you put the path to the "inurl" variable.

I know why because I originally had inurl variable set to url thats why it says url.split I just had to change that to inurl.split and It works,
Thanks for pointing me in the right direction :)

---

