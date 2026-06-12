---
title: "parsing text with python regex tk#2"
date: 2009-08-28
forum: Programming Talk
---

### Post by crownedzero on 2009-08-28
I'm trying to make some sense of a python program I'm attempting to write. The more I think about it the more confused I'm finding myself.

So I have a wall-o-text. I need to break it into strings. Each string begins with '*AAA1' and continues until the next instance of 'AAA1'.

Vendor1 transaction:
```
*AAA1*D25Vendor1*AAA850*1KM00*1KNSA*1KP15184854-1*1KT090105*G6UN*G6WZZ*G6XOHDS*ALE010*AL4090105*00CShipMethod*A00ST*A0BCustomer1*A10CustomerAddress*A1BCustomerCity*A11CustomerState*A1CCustomerZip*A12CustomerCountry*1DH1*1D71*1DJEA*1D899*1DKUP*13G679145758581*156SK*16VStyle*16WSZ*1HG6*1H6BO*1HLBrownWalnut*1HMZZ*1HUM*13PF*13TProductDescription*AMC1
```

Vendor2 transaction:
```
*AAA1*D25Vendor2*AAA850*1KM00*1KNSA*1KP1007764050*1KT090105*190IA*19B500767*AY9N*0A305*0A660*0AKTerms*ALE001*AL4090128*ALE010*AL4090121*A00BY*A0BTSC*A0192*ABY1272*1DH10*1D71*1DJEA*1D825*1DKIN*13G7472062*156VN*16VJD0185*16WUP*1HG679145773751*1DH20*1D71*1DJEA*1D825*1DKIN*13G7472070*156VN*16VJD0185*16WUP*1HG679145773768*1DH30*1D71*1DJEA*1D825*1DKIN*13G7472088*156VN*16VJD0185*16WUP*1HG679145773775*1DH40*1D71*1DJEA*1D825*1DKIN*13G7472096*156VN*16VJD0185*16WUP*1HG679145773782*1DH50*1D71*1DJEA*1D825*1DKIN*13G7472101*156VN*16VJD0185*16WUP*1HG679145773799*1DH60*1D71*1DJEA*1D828*1DKIN*13G7472119*156VN*16VJD0186*16WUP*1HG679145773805*1DH70*1D71*1DJEA*1D825*1DKIN*13G7472127*156VN*16VJD0186*16WUP*1HG679145773812*1DH80*1D71*1DJEA*1D825*1DKIN*13G7472135*156VN*16VJD0186*16WUP*1HG679145773829*1DH90*1D71*1DJEA*1D825*1DKIN*13G7472143*156VN*16VJD0186*16WUP*1HG679145773836*1DH100*1D71*1DJEA*1D825*1DKIN*13G7472151*156VN*16VJD0186*16WUP*1HG679145773843*1DH110*1D71*1DJEA*1D825*1DKIN*13G7472169*156VN*16VJD0188*16WUP*1HG679145775168*1DH120*1D71*1DJEA*1D825*1DKIN*13G7472177*156VN*16VJD0188*16WUP*1HG679145775175*1DH130*1D71*1DJEA*1D825*1DKIN*13G7472185*156VN*16VJD0188*16WUP*1HG679145775182*1DH140*1D71*1DJEA*1D825*1DKIN*13G7472193*156VN*16VJD0188*16WUP*1HG679145775199*1DH150*1D71*1DJEA*1D825*1DKIN*13G7472208*156VN*16VJD0188*16WUP*1HG679145775205*AMC15
```


For each string I need to find the vendor tagged '*D25', each string needs to be handled differently based on that qualifier. Vendor1 sends information tagged differently than Vendor2 so it will be re.compiled differently.

I would like it to then write to a delimited file the data for the following tags.

Vendor1:
*D25Vendor1
*1KP15184854-1
*1D899
*13G679145758581
*16VJD3193

Vendor2:
*D25Vendor2
*1KP1007764050
*1D825*16VJD0185*1HG679145773751
*1D825*16VJD0185*1HG679145773768
*1D825*16VJD0185*1HG679145773775
*1D825*16VJD0185*1HG679145773782
*1D825*16VJD0185*1HG679145773799
*1D828*16VJD0186*1HG679145773805
*1D825*16VJD0186*1HG679145773812
*1D825*16VJD0186*1HG679145773829
*1D825*16VJD0186*1HG679145773836
*1D825*16VJD0186*1HG679145773843
*1D825*16VJD0188*1HG679145775168
*1D825*16VJD0188*1HG679145775175
*1D825*16VJD0188*1HG679145775182
*1D825*16VJD0188*1HG679145775199
*1D825*16VJD0188*1HG679145775205

with the end result being something like:
Vendor1,15184854-1,67914578581,JD3193,99
Vendor2,1007764050,679145773751, JD0185, 25
Vendor2,1007764050,679145773768, JD0185, 25
Vendor2,1007764050,679145773775, JD0185, 25
Vendor2,1007764050,679145773782, JD0185, 25
Vendor2,1007764050,679145773799, JD0185, 25
Vendor2,1007764050,679145773805, JD0185, 25
Vendor2,1007764050,679145773812, JD0185, 25
Vendor2,1007764050,679145773829, JD0185, 25
Vendor2,1007764050,679145773836, JD0185, 25
Vendor2,1007764050,679145773843, JD0185, 25
Vendor2,1007764050,679145775168, JD0185, 25
Vendor2,1007764050,679145775175, JD0185, 25
Vendor2,1007764050,679145775182, JD0185, 25
Vendor2,1007764050,679145775205, JD0185, 25

I've gone around in circles on this for the last month. Any help would be greatly appreciated.

---

### Post by crownedzero on 2009-08-28
I've trashed and restarted a dozen times or more so I'll post where I'm going with this and hopefully get some help/feedback.

```

import re

open, read, assign text, close

string = re.compile(string pattern)

for string in text():
    qualifier = re.compile(vendor pattern)
    if qualifier == 'Vendor1':
        data = re.compile((D25 tag)(1KP tag)(13G tag)(16V tag)(1D8 tag))
        append data to new text
    elif qualifier == 'Vendor2':
        data = re.compile ((D25)(1KP)(1HG)(16V)(1D8))
        item = re.compile ((1HG))
        for item in string():
            append data to new text

```

I've taken off more than I can handle for sure but it only makes sense to learn dealing with something I actually encounter on a day to day basis.

---

### Post by DaithiF on 2009-08-28
this isn't particularly pretty, but might give you some ideas:
```
import re

fh = open('data')
data = fh.read()
fh.close()

vendor_patterns = { 
    'Vendor1': ['1KP(.*?)\*', '1D8(.*?)\*.*?13G(.*?)\*.*?16V(.*?)\*'],
    'Vendor2': ['1KP(.*?)\*', '1D8(.*?)\*.*?16V(.*?)\*.*?1HG(.*?)\*'] }

records = data.split('*AAA1')
for record in records:
    vendorhits = re.findall('\*D25(.*?)\*', record)
    if vendorhits: 
        vendor = vendorhits[0]
        patterns = vendor_patterns[vendor]
        if patterns:
            firstfields = re.findall(patterns[0], record)
            secondfields = re.findall(patterns[1], record)
            for output in secondfields:
                print "%s:%s:%s" % ( vendor, firstfields[0], ':'.join(output))
    

```

```
Vendor1:15184854-1:99:679145758581:Style
Vendor2:1007764050:25:JD0185:679145773751
Vendor2:1007764050:25:JD0185:679145773768
Vendor2:1007764050:25:JD0185:679145773775
Vendor2:1007764050:25:JD0185:679145773782
Vendor2:1007764050:25:JD0185:679145773799
Vendor2:1007764050:28:JD0186:679145773805
Vendor2:1007764050:25:JD0186:679145773812
Vendor2:1007764050:25:JD0186:679145773829
Vendor2:1007764050:25:JD0186:679145773836
Vendor2:1007764050:25:JD0186:679145773843
Vendor2:1007764050:25:JD0188:679145775168
Vendor2:1007764050:25:JD0188:679145775175
Vendor2:1007764050:25:JD0188:679145775182
Vendor2:1007764050:25:JD0188:679145775199
Vendor2:1007764050:25:JD0188:679145775205

```

---

### Post by kimo9909 on 2009-08-28
I thought that Python does not use {} but instead uses indentation.  Is this a special instance?

---

### Post by Mirge on 2009-08-28
> **kimo9909 said:**
> I thought that Python does not use {} but instead uses indentation.  Is this a special instance?

He's creating a dictionary/hash/associative array, which is denoted using braces. He's not marking the start/end of a block.

---

### Post by kimo9909 on 2009-08-28
> **Mirge said:**
> He's creating a dictionary/hash/associative array, which is denoted using braces. He's not marking the start/end of a block.


Awesome...ty for the quick reply!  I just started reading Beginning Python Visualization by Shai Vaingast but I haven't gotten that far yet.  I truly hope to get good enough to work on a project for Ubuntu with Python!  :)

---

### Post by DaithiF on 2009-08-28
> **kimo9909 said:**
> I thought that Python does not use {} but instead uses indentation.  Is this a special instance?

you mean this bit?
```
vendor_patterns = { 
    'Vendor1': ['1KP(.*?)\*', '1D8(.*?)\*.*?13G(.*?)\*.*?16V(.*?)\*'],
    'Vendor2': ['1KP(.*?)\*', '1D8(.*?)\*.*?16V(.*?)\*.*?1HG(.*?)\*'] }

```
the { } here are not to act as statement / block delimiters, they create a dictionary object.  And yes, Python does use indentation to define blocks of code

---

### Post by Mirge on 2009-08-28
> **kimo9909 said:**
> Awesome...ty for the quick reply!  I just started reading Beginning Python Visualization by Shai Vaingast but I haven't gotten that far yet.  I truly hope to get good enough to work on a project for Ubuntu with Python!  :)

No worries

---

### Post by crownedzero on 2009-08-29
> **DaithiF said:**
> this isn't particularly pretty, but might give you some ideas:
```
import re

fh = open('data')
data = fh.read()
fh.close()

vendor_patterns = { 
    'Vendor1': ['1KP(.*?)\*', '1D8(.*?)\*.*?13G(.*?)\*.*?16V(.*?)\*'],
    'Vendor2': ['1KP(.*?)\*', '1D8(.*?)\*.*?16V(.*?)\*.*?1HG(.*?)\*'] }

records = data.split('*AAA1')
for record in records:
    vendorhits = re.findall('\*D25(.*?)\*', record)
    if vendorhits: 
        vendor = vendorhits[0]
        patterns = vendor_patterns[vendor]
        if patterns:
            firstfields = re.findall(patterns[0], record)
            secondfields = re.findall(patterns[1], record)
            for output in secondfields:
                print "%s:%s:%s" % ( vendor, firstfields[0], ':'.join(output))
    

```

```
Vendor1:15184854-1:99:679145758581:Style
Vendor2:1007764050:25:JD0185:679145773751
Vendor2:1007764050:25:JD0185:679145773768
Vendor2:1007764050:25:JD0185:679145773775
Vendor2:1007764050:25:JD0185:679145773782
Vendor2:1007764050:25:JD0185:679145773799
Vendor2:1007764050:28:JD0186:679145773805
Vendor2:1007764050:25:JD0186:679145773812
Vendor2:1007764050:25:JD0186:679145773829
Vendor2:1007764050:25:JD0186:679145773836
Vendor2:1007764050:25:JD0186:679145773843
Vendor2:1007764050:25:JD0188:679145775168
Vendor2:1007764050:25:JD0188:679145775175
Vendor2:1007764050:25:JD0188:679145775182
Vendor2:1007764050:25:JD0188:679145775199
Vendor2:1007764050:25:JD0188:679145775205

```

As far as I can tell this is scales just by adding new definitions, amirite? It's my weekend but I'll definitely give this a shot on production data on Monday.

---

### Post by crownedzero on 2009-08-29
> **kimo9909 said:**
> I thought that Python does not use {} but instead uses indentation.  Is this a special instance?

Kind of a moot point but if I recall correctly Python's allure was taking the syntax out so one could in fact just code. But i noted in the latest release they seem to be bringing syntax into play.

print ('Hello World') vs print 'Hello World'; I didn't care for it so I didn't tinker around much after that before going back go my previous version.

---

### Post by crownedzero on 2009-08-31
Wow, you have no idea how much of a time saver this is. I updated it for each of our vendors and ran it against this morning's wall-o-text. Granted, initially all the fields weren't the required info but after some changes to the regex patterns I had a nice neat and orderly column of useful info.

---

