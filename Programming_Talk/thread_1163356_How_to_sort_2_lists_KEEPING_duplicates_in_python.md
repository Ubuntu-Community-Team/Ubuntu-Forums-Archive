---
title: "How to sort 2 lists KEEPING duplicates in python?"
date: 2009-05-18
forum: Programming Talk
---

### Post by UbuKunubi on 2009-05-18
Hello folks,
Im not sure if this problem is thorny, or if im looking at this the wrong way.

What i'm trying to achieve is the deletion of duplicate images, after being 'fingered' using Edge Detection.

What I have is 2 lists of equal length, one with file names, the second holds an identifier.

Basically, I intend to delete the second instance of identifiers, leaving only originals.

using the search engines I have found only ways of removing duplicates from a list, NOT a list OF duplicates.

Can anyone help?

---

### Post by days_of_ruin on 2009-05-18
I am not sure what you mean. Just delete a list? Or delete the files the list points to?

---

### Post by ghostdog74 on 2009-05-18
in such situations, its better to give examples of your duplicates and how you want your output to be... anyway, you can try set in Python...

---

### Post by unutbu on 2009-05-18
[PHP]#!/usr/bin/env python
files=[...]
identifiers=[...]
adict={}
for filename,ident in zip(files,identifiers):
    if ident in adict:
        # remove filename
        os.unlink(filename)
    else:
        adict[ident]=1
[/PHP]

---

### Post by UbuKunubi on 2009-05-19
Thanks for your replies!

First:
Q: Re: How to sort 2 lists KEEPING duplicates in python?
I am not sure what you mean. Just delete a list? Or delete the files the list points to? 

A:I want to delete the files that the list points to.

Sample of tables used as test data:
ndsImgname=[]
ndsImgBPN=[]
ndsDupReg=[]
ndsImgname.append("filea.jpg")
ndsImgBPN.append("100")       #1
ndsImgname.append("fileb.jpg")
ndsImgBPN.append("123")       #1
ndsImgname.append("filec.jpg")
ndsImgBPN.append("122")       #1
ndsImgname.append("filed.jpg")
ndsImgBPN.append("100")       #2  !100
ndsImgname.append("filee.jpg")
ndsImgBPN.append("132")       #1
ndsImgname.append("filef.jpg")
ndsImgBPN.append("254")       #1
ndsImgname.append("fileg.jpg")
ndsImgBPN.append("123")       #2  !123
ndsImgname.append("fileh.jpg")
ndsImgBPN.append("123")       #3  !123
ndsImgname.append("filei.jpg")
ndsImgBPN.append("123")       #4  !123
ndsImgname.append("filej.jpg")
ndsImgBPN.append("99")        #1
ndsImgname.append("filek.jpg")
ndsImgBPN.append("98")        #1
ndsImgname.append("filel.jpg")
ndsImgBPN.append("122")       #2  !122
ndsImgname.append("filem.jpg")
ndsImgBPN.append("100")       #3  !100
ndsImgname.append("filen.jpg")
ndsImgBPN.append("123")       #5  !123
ndsImgname.append("fileo.jpg")
ndsImgBPN.append("21")        #1
ndsImgname.append("filep.jpg")
ndsImgBPN.append("1")         #1
ndsImgname.append("fileq.jpg")
ndsImgBPN.append("59")        #1
ndsImgname.append("fileu.jpg")
ndsImgBPN.append("564")       #1
ndsImgname.append("filer.jpg")
ndsImgBPN.append("2131")      #1
ndsImgname.append("files.jpg")
ndsImgBPN.append("100")#      #4  !100

so what I end up with a list of files that have identical BPN (blue print number).
The 1st (original) BPN is NOT go to go on the list.

I'm most likely not explaining this too well at the moment, so please bear with me.

---

### Post by imdano on 2009-05-19
> **UbuKunubi said:**
> 
A:I want to delete the files that the list points to.Do you mean actually delete the files from the filesystem, or just remove them from the list?  Either way, the code unutbu posted is going to be very close to what you want.

> so what I end up with a list of files that have identical BPN (blue print number).
The 1st (original) BPN is NOT go to go on the list.I don't quite follow this.  You want to delete the duplicate files, but also put them in a new list?  Should there be a separate list for all the groups of duplicates (i.e. a list for all dupes with BPN 100, a list for all dupes with BPN 123, etc.)?

---

### Post by UbuKunubi on 2009-05-19
Thanks for you input chaps.

Below is the solution that works as i wanted, but if someone could be kind enough to smarten it up/make it simpler I'd be grateful.

Ubu,
```

while 1:
    print "FileName",ndsImgname[p]," FileBPN=",ndsImgBPN[p]
    ntmp=ndsImgBPN[p]
    zcnt=ndsImgBPN.count(ntmp)
    print "Instance counter =",zcnt
    if zcnt==1:                         #its a sole entity, so just copy across
        print "Unique"                  
        ndsUniReg.append(ndsImgname[p]) #the file name
        ndsUniBPN.append(ndsImgBPN[p])  #and the BPN
    if zcnt>1:                          #its got duplicate BPN's
        print "Duplicate found"
        ycnt=ndsUniBPN.count(ndsImgBPN[p]) #now to count if the BPN now in question is already in the UNIQUE list
        if ycnt >= 1:
            ndsDupReg.append(ndsImgname[p])
            ndsDupBPN.append(ndsImgBPN[p])
        if ycnt<1:                          #so if the BPN does not occur at least once then
            ndsUniReg.append(ndsImgname[p]) #append the filename
            ndsUniBPN.append(ndsImgBPN[p])  #and the BPN.
    p=p+1
    if p==ndslen:
        break
print"output of Unique table:"
print "Len=",str(len(ndsUniReg)),ndsUniReg
print"Output of Duplicate Table"
print "Len=",str(len(ndsDupReg)),ndsDupReg
#the above will split the filenames into 2 lists, but I need to keep 1 of the Duplicates back as an orginal.

```

---

