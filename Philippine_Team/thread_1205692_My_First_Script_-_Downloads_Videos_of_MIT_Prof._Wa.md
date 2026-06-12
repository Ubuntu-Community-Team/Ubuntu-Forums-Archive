---
title: "My First Script - Downloads Videos of MIT Prof. Walter Lewin - High School Physics"
date: 2009-07-06
forum: Philippine Team
---

### Post by dannybuntu on 2009-07-06
UPDATED: I've added the -c option to wget

Hi, guys, just thought I'd share with you my first bash script. I know it's crude - hopefully you could teach me a thing or two (better yet a hundred). :)

This script would make a folder in your home directory and download 35 videos of Massachussets (did I spell that right?) Institute of Technology's Open Courseware for High School Physics by Prof. Walter Lewin. 

The school I went to when I was in high school had a specialized curriculum which did not benefit me the joy of being taught High School Physics so I decided to start learning some from the best.

It downloads 3.6 GB of mp4 video and their corresponding transcript from the Internet Archive.

Got it from here: [http://ocw.mit.edu/OcwWeb/Physics/8-01Physics-IFall1999/CourseHome/index.htm](http://ocw.mit.edu/OcwWeb/Physics/8-01Physics-IFall1999/CourseHome/index.htm)

And it took my pldt plan 999 to download that approximately 36 hours. 

Suggestions/corrections are very much appreciated. 

Hope others would do the same for any topic. Kakapagod pala gumawa ng script. 

```
#!/bin/bash
# MIT Open Courseware - High School Physics Course Downloader 2009
# This Script is a simple script which would download the Massachussets Institute
# of Technology Open Courseware Physics High School Course for Free - Legally
# This script is made by Daniel Andrei "dannybuntu" R. Garcia and is freely modifiable, redistributable,
# and is provided without any guarantees whatsoever. 
#  
# The script author cannot be held liable for any damage that this script will make directly and 
# indirectly to your system for any reason. The content that is going to be downloaded is provided and owned by MIT.
# Failure of this script to download because of the
# unavailability of the content on MIT's servers is not the script writer's fault.
# Usage and/or execution of this script would henceforth be seen as an agreement to the above terms and conditions.
   
clear
echo INITIALIZING MIT_HSPHYSICS COURSE DOWNLOADER
cd ~
mkdir MIT_HSPHYSICS
cd MIT_HSPHYSICS
#
#
# LECTURE 1
mkdir HSPHYSICS_Lecture_1
cd HSPHYSICS_Lecture_1
clear
echo Downloading Lecture 1 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/1.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/6CF81A2E-9863-498E-8A22-8308184E9254/0/8_011999L01.pdf
cd ..
# LECTURE 2
mkdir HSPHYSICS_Lecture2
cd HSPHYSICS_Lecture2
clear
echo Downloading Lecture 2 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/2.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/A2CF20EE-FC35-4044-AFC0-998B4EBB75E7/0/8_011999L02.pdf
cd ..
# LECTURE 3
mkdir HSPHYSICS_Lecture3
cd HSPHYSICS_Lecture3
clear
echo Downloading Lecture 3 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/3.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/7D93C9F7-0DA6-4EBD-88F1-F074FBD40ACE/0/8_011999L03.pdf
cd .. 
# LECTURE 4
mkdir HSPHYSICS_Lecture4
cd HSPHYSICS_Lecture4
clear
echo Downloading Lecture 4 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/4.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/8173198E-C1A2-46C3-BB76-44F5C48FD6EA/0/8_011999L04.pdf
cd ..
# LECTURE 5
mkdir HSPHYSICS_Lecture5
cd HSPHYSICS_Lecture5
clear
echo Downloading Lecture 5 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/5.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/FAC25A9F-7FCA-4EC3-BCD3-0C93E301FF63/0/8_011999L05.pdf
cd ..
# LECTURE 6
mkdir HSPHYSICS_Lecture6
cd HSPHYSICS_Lecture6
clear
echo Downloading Lecture 6 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/6.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/75EABA20-A0EB-4EAD-8C77-283C89D590AC/0/8_011999L06.pdf
cd ..
# LECTURE 7
mkdir HSPHYSICS_Lecture7
cd HSPHYSICS_Lecture7
clear
echo Downloading Lecture 7 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/7.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/98AF239F-E1FF-4B7F-90D4-DC9BF1975B23/0/8_011999L07.pdf
cd ..
# LECTURE 8
mkdir HSPHYSICS_Lecture8
cd HSPHYSICS_Lecture8
clear
echo Downloading Lecture 8 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/8.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/7E33EBE4-D7BF-4756-AFA0-6FF406A793B4/0/8_011999L08.pdf
cd ..
# LECTURE 9
mkdir HSPHYSICS_Lecture9
cd HSPHYSICS_Lecture9
clear
echo Downloading Lecture 9 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/9.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/3EFE752C-D610-43D9-B501-A1ECFA71BE7B/0/8_011999L09.pdf
cd ..
# LECTURE 10 
mkdir HSPHYSICS_Lecture10
cd HSPHYSICS_Lecture10
clear
echo Downloading Lecture 10 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/10.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/3453A781-51B9-4103-B108-F6FDE9D8826E/0/8_011999L10.pdf
cd ..
# LECTURE 11
mkdir HSPHYSICS_Lecture11
cd HSPHYSICS_Lecture11
clear
echo Downloading Lecture 11 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/11.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/6109D77D-416A-43A1-9928-FCBC5C364DAA/0/8_011999L11.pdf
cd ..
# LECTURE 12
mkdir HSPHYSICS_Lecture12
cd HSPHYSICS_Lecture12
clear
echo Downloading Lecture 12 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/12.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/F39F7569-AE51-465E-82E5-3D8BF56F8013/0/8_011999L12.pdf
cd ..
# LECTURE 13
mkdir HSPHYSICS_Lecture13
cd HSPHYSICS_Lecture13
clear
echo Downloading Lecture 13 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/13.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/793FF83C-DD5D-4477-A56D-A6BE92E3E39B/0/8_011999L13.pdf
cd ..
# LECTURE 14
mkdir HSPHYSICS_Lecture14
cd HSPHYSICS_Lecture14
clear
echo Downloading Lecture 14 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/14.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/309CEB36-AD74-42C4-900B-33F87FDAB987/0/8_011999L14.pdf
cd ..
# LECTURE 15
mkdir HSPHYSICS_Lecture15
cd HSPHYSICS_Lecture15
clear
echo Downloading Lecture 15 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/15.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/96A267AB-14E5-4A79-BF51-56D4863DBAAA/0/8_011999L15.pdf
cd ..
# LECTURE 16
mkdir HSPHYSICS_Lecture16
cd HSPHYSICS_Lecture16
clear
echo Downloading Lecture 16 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/16.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/943BB68D-996C-4322-B915-1767A1EB9051/0/8_011999L16.pdf
cd ..
# LECTURE 17
mkdir HSPHYSICS_Lecture17
cd HSPHYSICS_Lecture17
clear
echo Downloading Lecture 17 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/17.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/093C0162-B733-414E-88BE-64EC05A98920/0/8_011999L17.pdf
cd ..
# LECTURE 18
mkdir HSPHYSICS_Lecture18
cd HSPHYSICS_Lecture18
clear
echo Downloading Lecture 18 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/18.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/98A8C13D-B09D-482F-ACA5-0E8215A88F3F/0/8_011999L18.pdf
cd ..
# LECTURE 19
mkdir HSPHYSICS_Lecture19
cd HSPHYSICS_Lecture19
clear
echo Downloading Lecture 19 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/19.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/AE959D3F-0714-4418-8099-BDFF2203B050/0/8_011999L19.pdf
cd ..
# LECTURE 20
mkdir HSPHYSICS_Lecture20
cd HSPHYSICS_Lecture20
clear
echo Downloading Lecture 20 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/20.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/B0866A36-91B3-4807-853A-5AC4A394652F/0/8_011999L20.pdf
cd ..
# LECTURE 21
mkdir HSPHYSICS_Lecture21
cd HSPHYSICS_Lecture21
clear
echo Downloading Lecture 21 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/21.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/E37CF64E-0F8C-49FE-90E1-65A0CFD9E4C6/0/8_011999L21.pdf
cd ..
# LECTURE 22
mkdir HSPHYSICS_Lecture22
cd HSPHYSICS_Lecture22
clear
echo Downloading Lecture 22 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/22.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/0072384E-EE99-4AF2-8AB7-78F59D2D0265/0/8_011999L22.pdf
cd ..
# LECTURE 23
mkdir HSPHYSICS_Lecture23
cd HSPHYSICS_Lecture23
clear
echo Downloading Lecture 23 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/23.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/E1A8E05A-F49D-47F1-90D3-9147B669533B/0/8_011999L23.pdf
cd ..
# LECTURE 24
mkdir HSPHYSICS_Lecture24
cd HSPHYSICS_Lecture24
clear
echo Downloading Lecture 24 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/24.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/96BEFC1A-189E-469D-B4A6-3895E917968F/0/8_011999L24.pdf
cd ..
# LECTURE 25
mkdir HSPHYSICS_Lecture25
cd HSPHYSICS_Lecture25
clear
echo Downloading Lecture 25 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/25.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/4FEC6844-A8E3-46A6-99F1-1F229AF246E6/0/8_011999L25.pdf
cd ..
# LECTURE 26
mkdir HSPHYSICS_Lecture26
cd HSPHYSICS_Lecture26
clear
echo Downloading Lecture 26 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/26.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/CED18670-7D9B-4D4A-AA07-7106CD3A696C/0/8_011999L26.pdf
cd ..
# LECTURE 27
mkdir HSPHYSICS_Lecture27
cd HSPHYSICS_Lecture27
clear
echo Downloading Lecture 27 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/27.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/F6541142-0575-46EB-B093-B4C804FECB96/0/8_011999L27.pdf
cd ..
# LECTURE 28
mkdir HSPHYSICS_Lecture28
cd HSPHYSICS_Lecture28
clear
echo Downloading Lecture 28 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/28.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/320F761F-4B41-4C4B-91D0-3A394F2736A8/0/8_011999L28.pdf
cd ..
# LECTURE 29
mkdir HSPHYSICS_Lecture29
cd HSPHYSICS_Lecture29
clear
echo Downloading Lecture 29 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/29.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/D771729D-CF82-4750-8CC3-7AA69235C483/0/8_011999L29.pdf
cd ..
# LECTURE 30
mkdir HSPHYSICS_Lecture30
cd HSPHYSICS_Lecture30
clear
echo Downloading Lecture 30 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/30.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/C4C8B33F-E9C8-4101-B59E-8CEC4A6B05B5/0/8_011999L30.pdf
cd ..
# LECTURE 31
mkdir HSPHYSICS_Lecture31
cd HSPHYSICS_Lecture31
clear
echo Downloading Lecture 31 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/31.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/1D136972-5DF2-4DE5-A98A-168ACA84BB8D/0/8_011999L31.pdf
cd ..
# LECTURE 32
mkdir HSPHYSICS_Lecture32
cd HSPHYSICS_Lecture32
clear
echo Downloading Lecture 32 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/32.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/8F9D04DB-A5E5-4ED8-8A9F-265866ACDCEB/0/8_011999L32.pdf
cd ..
# LECTURE 33
mkdir HSPHYSICS_Lecture33
cd HSPHYSICS_Lecture33
clear
echo Downloading Lecture 33 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/33.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/F2AB5C50-DCFD-402A-AC20-777F09F545F4/0/8_011999L33.pdf
cd ..
# LECTURE 34 
mkdir HSPHYSICS_Lecture34
cd HSPHYSICS_Lecture34
clear
echo Downloading Lecture 34 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/34.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/E181A47E-DC2C-414E-8F19-6162AA97D9FC/0/8_011999L34.pdf
cd ..
# LECTURE 35
mkdir HSPHYSICS_Lecture35
cd HSPHYSICS_Lecture35
clear
echo Downloading Lecture 35 Video and Transcript
wget -c http://www.archive.org/download/MIT8.01F99/35.mp4
wget -c http://ocw.mit.edu/NR/rdonlyres/Physics/8-01Physics-IFall1999/4026C253-C479-4E98-AD52-AE300C31BF41/0/8_011999L35.pdf
cd ..
# END


```

---

### Post by guitar_man on 2009-07-06
Ang tagal nun sir danny,,,


Sa site din ng MIT ako nag-advance lesson(cram session) dati....
Maganda mga video nila.

:lolflag:

---

### Post by kiminaiseah on 2009-07-06
medyo padagdag nung wget with wget -c

para pag na disconnect ka ma iiresume mo sya

---

### Post by dannybuntu on 2009-07-06
> **kiminaiseah said:**
> medyo padagdag nung wget with wget -c

para pag na disconnect ka ma iiresume mo sya

Thanks :) 

I will update na - after I take a bath :)

---

### Post by dannybuntu on 2009-07-06
> Ang tagal nun sir danny,,,


Sa site din ng MIT ako nag-advance lesson(cram session) dati....
Maganda mga video nila.

Hmmm. Sige, try ko suggestion ni kiminaiseah, para may resume function.

---

