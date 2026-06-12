---
title: "UTF-8 sequence error at java script"
date: 2011-08-19
forum: Programming Talk
---

### Post by lars.modig on 2011-08-19
Hi,

I'm trying to convert my gmn (garmin forerunner tools data, [http://code.google.com/p/garmintools/]("http://code.google.com/p/garmintools/")) by using gmn2tcx ([http://braiden.org/?p=62]("http://braiden.org/?p=62").

Using this script return an error.

```
“Error
com.sun.org.apache.xerces.internal.impl.io.MalformedByteSequenceException: Invalid byte 1 of 1-byte UTF-8 sequence.
Transformation failed: Run-time errors were reported
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, ‘<' not found

^
I/O error : Invalid seek"
```

I then got the tip to try to convert the gmn file to UFT-8. Wich I did by.

```
iconv --from-code=ISO-8859-1 --to-code=UTF-8 20110801T181321.gmn -o 20110801T181321.gmn
```

But trying to convert it to tcx still fails...

```
./gmn2tcx /home/lars/2011/08/20110801T181321.gmn > /home/lars/Desktop/workout.tcx
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': '' is not a valid value of the atomic type 'xs:dateTime'.
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': Warning: No precomputed value available, the value was either invalid or something strange happend.
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Missing child element(s). Expected is ( {http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Lap ).
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Not all fields of key identity-constraint '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}ActivityIdMustBeUnique' evaluate to a node.
- fails to validate

```

I hope that someone can help me...

I attach a original gmn file and hope that someone can help me...

Br ,

Lars

---

### Post by ofnuts on 2011-08-19
> **lars.modig said:**
> Hi,

I'm trying to convert my gmn (garmin forerunner tools data, [http://code.google.com/p/garmintools/](http://code.google.com/p/garmintools/)) by using gmn2tcx ([http://braiden.org/?p=62](http://braiden.org/?p=62).

Using this script return an error.

```
“Error
com.sun.org.apache.xerces.internal.impl.io.MalformedByteSequenceException: Invalid byte 1 of 1-byte UTF-8 sequence.
Transformation failed: Run-time errors were reported
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, ‘<' not found

^
I/O error : Invalid seek"
```I then got the tip to try to convert the gmn file to UFT-8. Wich I did by.

```
iconv --from-code=ISO-8859-1 --to-code=UTF-8 20110801T181321.gmn -o 20110801T181321.gmn
```But trying to convert it to tcx still fails...

```
./gmn2tcx /home/lars/2011/08/20110801T181321.gmn > /home/lars/Desktop/workout.tcx
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': '' is not a valid value of the atomic type 'xs:dateTime'.
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': Warning: No precomputed value available, the value was either invalid or something strange happend.
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Missing child element(s). Expected is ( {http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Lap ).
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Not all fields of key identity-constraint '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}ActivityIdMustBeUnique' evaluate to a node.
- fails to validate

```I hope that someone can help me...

I attach a original gmn file and hope that someone can help me...

Br ,

LarsThe GMN file seems to contain essentially binary data, so 
1) doing UTF-8 conversion Is Not A Good Idea
2) xerces, which is an XML parser, has understandably a lot of trouble with that.

IMHO you missed something during the extraction.

---

### Post by lars.modig on 2011-08-29
You're right!

So when I try to convert my gmn files I first got a failure UTF-8 sequence error... But then I installed &#8216;libsaxonb-java&#8217; (that actually says that you don't need).

Then I could get a tcx file, but It was far from TCX. It more or less looks like a summary Not like the real TCX and Mytourbook can of course not read it.

But still I believe that my GMN files are ok due to that I can get all data using "sportwatcher",

I Hope that you can help me

Br,

Lars

---

### Post by ofnuts on 2011-08-29
> **lars.modig said:**
> You're right!

So when I try to convert my gmn files I first got a failure UTF-8 sequence error... But then I installed ‘libsaxonb-java’ (that actually says that you don't need).

Then I could get a tcx file, but It was far from TCX. It more or less looks like a summary Not like the real TCX and Mytourbook can of course not read it.

But still I believe that my GMN files are ok due to that I can get all data using "sportwatcher",

I Hope that you can help me

Br,

LarsNot unless you attach a .gmn file somewhere as well as a known good .tcx one (likely as a ZIP/TAR since these are among the allowed extensions for attached files here)

---

### Post by lars.modig on 2011-08-30
Thanks!

You can find the gmn2tcx script here [http://braiden.org/?p=62]("http://braiden.org/?p=62"). I tried to reach the creator, but without success.

Attached I included a gmn file, a tcx file exported from "Mytourbook" and one tcx file created by gmn2tcx. (They are of different date so it's not the same exercise) 

I hope that you could help. 

Braiden also mention in his post that you should run some special Java, so if that could be of help this is my output from java -version

[HTML]java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
[/HTML]

Strange !! Now when I should create the files, I again got the UTF-8 error when running the script, however I anyway attach the file that I earlier got as a TCX file with the script...

---

### Post by ofnuts on 2011-08-30
> **lars.modig said:**
> Thanks!

You can find the gmn2tcx script here [http://braiden.org/?p=62](http://braiden.org/?p=62). I tried to reach the creator, but without success.

Attached I included a gmn file, a tcx file exported from "Mytourbook" and one tcx file created by gmn2tcx. (They are of different date so it's not the same exercise) 

I hope that you could help. 

Braiden also mention in his post that you should run some special Java, so if that could be of help this is my output from java -version

[HTML]java version "1.6.0_22"
OpenJDK Runtime Environment (IcedTea6 1.10.2) (6b22-1.10.2-0ubuntu1~11.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)
[/HTML]Strange !! Now when I should create the files, I again got the UTF-8 error when running the script, however I anyway attach the file that I earlier got as a TCX file with the script...
From what I understand of thye code, it runs some "garmin_dump"  utility (without checking existence of return code....) against the  input file to produce XML. This XML is further wrapped into XML header/trailer and run trhough an XSLT processor. 

So the question is on you system if you run:
```
garmin_dump 20100904T192357.gmn
```
Do you get XML printed on the console?

---

### Post by lars.modig on 2011-08-30
yes, when I run the garmin_dump I get the attached zip file...

/Lars

---

### Post by ofnuts on 2011-08-30
> **lars.modig said:**
> yes, when I run the garmin_dump I get the attached zip file...

/LarsOne problem I see is that the "name" attribute of the <workout> at the beginning of the converted file is "ÿÿÿÿÿÿÿÿÿ" which is expressed as a sequence of 0xFF. Then the script blindly wraps the converted data with more XML, and said XML blindly declares that the wrapped  XML is UTF-8 encoded while  a sequence of 0xFF  isn't a valid UT-8 encoding.

The original file contains several sequences of 0xFF, so it's hard to guess which one is the workout name.  But this hints that maybe you can enter a name when starting a workout (the 0xFF would be a default when no name is entered).

Or you can edit the gmn2tcx file, and in the do_dump function, replace
```

  echo "<?xml version=\"1.0\" encoding=\"UTF-8\" ?>"
```by
```

  echo "<?xml version=\"1.0\" encoding=\"ISO-8858-1\" ?>"
```and see what happens

---

### Post by lars.modig on 2011-09-01
Change the gmn2tcx files returns...

```
./gmn2tcx /home/lars/2011/08/20110813T180652.gmn > /home/lars/Desktop/workout.tcx
Error 
  java.io.UnsupportedEncodingException: ISO-8858-1
Transformation failed: Run-time errors were reported
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek

```
"ÿÿÿÿÿÿÿÿÿ"

And I can sadly not add a name into the Garmin forerunner 301... Maybe the script shouldnt work for the 301?  But as mention and as you seen the overall data looks ok from the garmin_dump command. Isn't it possible to create some "subrutin" that erase or exchanges the "ÿÿÿÿÿÿÿÿÿ" to space or something else...

Br,

Lars

---

### Post by ofnuts on 2011-09-01
> **lars.modig said:**
> Change the gmn2tcx files returns...

```
./gmn2tcx /home/lars/2011/08/20110813T180652.gmn > /home/lars/Desktop/workout.tcx
Error 
  java.io.UnsupportedEncodingException: ISO-8858-1
Transformation failed: Run-time errors were reported
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek

```"ÿÿÿÿÿÿÿÿÿ"

And I can sadly not add a name into the Garmin forerunner 301... Maybe the script shouldnt work for the 301?  But as mention and as you seen the overall data looks ok from the garmin_dump command. Isn't it possible to create some "subrutin" that erase or exchanges the "ÿÿÿÿÿÿÿÿÿ" to space or something else...

Br,

LarsSorry, typo, encoding should be ISO-885**[COLOR=Red]9[/COLOR]**-1

---

### Post by lars.modig on 2011-09-01
Sadly the return is

```
./gmn2tcx /home/lars/2011/08/20110813T180652.gmn > /home/lars/Desktop/workout.tcx
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': '' is not a valid value of the atomic type 'xs:dateTime'.
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': Warning: No precomputed value available, the value was either invalid or something strange happend.
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Missing child element(s). Expected is ( {http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Lap ).
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Not all fields of key identity-constraint '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}ActivityIdMustBeUnique' evaluate to a node.
- fails to validate

```

The garmin_dump works as it looks and the only problem is this strange ÿ as you think, and it's only in the first line (as it looked in the txt file) so isn't it possible to do a garmin_dump in the script and after the first End Of Line, start the converting and having a default first row in the script?

Do you know how to do that?

One other way could maybe be to manually do the dump to a txt file as above and then erase the ÿ in that and feed that to the rest of the script. Of course I would like to have it automatically but it would be nice to be able to convert the gmn files.

Hope that you can help me.

/Lars

---

### Post by ofnuts on 2011-09-01
> **lars.modig said:**
> Sadly the return is

```
./gmn2tcx /home/lars/2011/08/20110813T180652.gmn > /home/lars/Desktop/workout.tcx
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': '' is not a valid value of the atomic type 'xs:dateTime'.
-:1: element Id: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Id': Warning: No precomputed value available, the value was either invalid or something strange happend.
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Missing child element(s). Expected is ( {http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Lap ).
-:1: element Activity: Schemas validity error : Element '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}Activity': Not all fields of key identity-constraint '{http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2}ActivityIdMustBeUnique' evaluate to a node.
- fails to validate

```The garmin_dump works as it looks and the only problem is this strange ÿ as you think, and it's only in the first line (as it looked in the txt file) so isn't it possible to do a garmin_dump in the script and after the first End Of Line, start the converting and having a default first row in the script?

Do you know how to do that?

One other way could maybe be to manually do the dump to a txt file as above and then erase the ÿ in that and feed that to the rest of the script. Of course I would like to have it automatically but it would be nice to be able to convert the gmn files.

Hope that you can help me.

/Lars

Well I think we are now at the stage where xmllint is checking the output, so if you comment out the line  
```
  XMLLINT=`which xmllint`
``` to disable the check, what do you get?

---

### Post by lars.modig on 2011-09-02
> **ofnuts said:**
> Well I think we are now at the stage where xmllint is checking the output, so if you comment out the line  
```
  XMLLINT=`which xmllint`
``` to disable the check, what do you get?

Well maybe not so surprising

```
WARN: "xmllint" not found. Will not validate XML schema.
``` 

I don't really follow what order the function calls are... Not so familiar with this scripts, but shouldn't it be some kind of main calling the different functions?  (You see that I really need your help here...)

/Lars

---

### Post by ofnuts on 2011-09-02
> **lars.modig said:**
> Well maybe not so surprising

```
WARN: "xmllint" not found. Will not validate XML schema.
```I don't really follow what order the function calls are... Not so familiar with this scripts, but shouldn't it be some kind of main calling the different functions?  (You see that I really need your help here...)

/Lars
XMLLINT outputs the XML code when all is OK. When you get the warning, you also execute CAT that instead copies its input to its output without checking. You get the warning but you should also get the XML generated.

---

### Post by lars.modig on 2011-09-02
> **ofnuts said:**
> XMLLINT outputs the XML code when all is OK. When you get the warning, you also execute CAT that instead copies its input to its output without checking. You get the warning but you should also get the XML generated.

Aha!  You where right, I created a new "workout.tcx" on my desktop (didn't realise that only). See code below. (the same file that I did the dump on earlier so allot is missing as you can see.)

```
<?xml version="1.0" encoding="UTF-8"?><TrainingCenterDatabase xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.garmin.com/xmlschemas/TrainingCenterDatabase/v2"><Activities><Activity Sport="Other"><Id/></Activity></Activities></TrainingCenterDatabase>

```


/Lars

---

### Post by lars.modig on 2011-09-25
Hi,

I was able to run a training with another name then "ÿÿÿÿÿÿÿÿÿ", but even then it was not realising that it was a TCX. So I've now instead bought a Forerunner 305 and it works. But I think it still should be possible to use the 301:a I've upload here the dump file from booth the 301:a and the 305:a (same training on the same time, me and a friend where going parallel)to compare.

---

