---
title: "I'm looking for some OCR (Optical Character Recognition) software..."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by diablo75 on 2008-07-11
I need to scan a document into my computer and I was wondering if there are any good OCR scanning utilities out there in the world of Linux.

I saw Kooka listed, but wasn't sure if that would run on Gnome very well.  Any others out there worth taking a look at?

---

### Post by fatality_uk on 2008-07-11
Hope this helps
[http://www.linux-ocr.ekitap.gen.tr/](http://www.linux-ocr.ekitap.gen.tr/)

---

### Post by ChameleonDave on 2008-07-11
> **diablo75 said:**
> I need to scan a document into my computer and I was wondering if there are any good OCR scanning utilities out there in the world of Linux.

I saw Kooka listed, but wasn't sure if that would run on Gnome very well.  Any others out there worth taking a look at?
Try GOCR, Ocrad or Tesseract.

---

### Post by bumanie on 2008-07-11
This is an ubuntu community document about athe above three programs
[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

---

### Post by diablo75 on 2008-07-11
I'll take a look at tesseract.  Though I might also investigate some propritary software for better results too...

Thanks!

---

### Post by inibo on 2008-07-26
Does anyone know where I can get the precompiled binary?  Everything I look at here seems to be for source code.

---

### Post by nalin4linux77 on 2012-02-27
[B][SIZE=4][COLOR=Navy]Linux-intelligent-ocr-solution[/COLOR][/SIZE]
  
LIOS is a free and open source software for converting print in to text  using either scanner or a camera. It can also produce text out of  scanned images from other sources. Program is given total accessibility  for visually impaired. LIOS is written in python and we release it under  GPL3 license. LIOS will work with Debian based operating systems. LIOS  is an effort from the easy-ocr development team. There are great many  possibilities for this program. Feedback is the key to it. expecting  your feedback. [email]nalin4linux77@gmail.com[/email] and [email]sath.linux@gmail.com[/email].
  [SIZE=3][COLOR=Lime]HOW TO INSTALL[/COLOR][/SIZE]
  
Download deb file from here [http://linux-intelligent-ocr-solution.googlecode.com/](http://linux-intelligent-ocr-solution.googlecode.com/) download the latest deb package and install
What is new in LIOS-1.2
1 Cam-Scan,
2 Cam-Reader,
3 Scan-to-image-only,
4 Scan-to-images-repeatedly,
5 Introduction of py-sane, Glaid library make the program faster and efficient,
6 Multiple arguments are handled effectively,
7 Ocr a single Image,
8 Artha shortcut (alt+control+W),
9 Beta version of spell-checker,
10 Provision for submitting issues in the About Dialog.
Features
1 Single scan & Repeated Scanning,
2 Ocr Folder,
3 Ocr Pdf,
4 Ocr image only,
5 Cam-Scan and Cam-Reader,
6 Scan-for-image-only & repeatedly,
7 24 Language support (Given at the end),
8 Full GUI environment,
9 Selection of starting page number, page numbering mode and number of pages to scan,
10 Selection of Scan area, brightness, resolution and time between repeated scanning,
11 Full Auto Rotation,
12 Brightness optimizer,
13 Audio converter,
14 Easily Accessible Preferences Window,
15 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD),
16 Good text manipulation with Find, Go-To-Page, Go-To-Line, Append file, Punch File.
17 Display Preferences for Low vision,
18 Dictionary Support for English(Artha)
19 Beta version of spell-checker,
20 Provision for submitting issues,
21 And more features are in the preferences.[/B]:lolflag:
[B]
  [SIZE=3][COLOR=Navy]How to start using LIOS.[/COLOR][/SIZE][/B]

1. Scanning.

In order to start new scan, first press ctrl+n and then press f9 for  single scan or ctrl+f9 for repeated scanning. To set the scanning  preferences press ctrl+p and set the starting page number, Mode of page  numbering, double page mode if you intend to keep 2 pages at a time,  rotation to select the way in which you want the program to rotate the  images before conversion. In full automatic rotation mode, one can keep  the book in 00 90 180 and 270 degree angle. In partial rotation mode  program will scan once to find out the position of the book and then the  rotation will be kept. In manual mode one should select the angle.  partial and manual mode is faster than full auto rotation mode in ocr  process. One can select the number of pages to be scanned at a stretch  by setting number of pages in the case of repeated scanning. One can  stop all scanning process by pressing ctrl f4.
2. Cam-scan.

one can now use Hovercam or a Webcam to produce text in LIOS.  Adjustments with these devices can be made using LIOS-cam-preferences in  edit menu. This feature will help to read books and other printed  materials such as visiting cards currency and like and also it makes the  ocr process very fast and accurate. Please be specific to use devices  with auto focusing facility. remember that there is no autorotation in  this utility.so for the same reason, support of a stand for the webcam  will be highly appreciated.
3. Cam-reader.

is the utility which will give a continuous output as one moves the  webcam. First it will create the image and then will produce the text  and it will start reading. After the completion of reading, it will  repeat the process automatically. In cam-scan, one has to take the photo  and it will be converted in to text.
4. Ocr Image.

LIOS can convert image file to text which is in jpg, tif, png, pnm and bmp.
5. Ocr folder.

LIOS can convert scanned images from other sources. It can convert jpg,  jpeg, tif, tiff png, pnm, formats. To convert the images in a folder,  select scan from folder option from scan menu and then select the input  folder.
6. Ocr Pdf file.

Select Ocr pdf from scan menu and then select the input file. It is  recommended that one can use ocropus as engine more efficiently in pdf  conversion.
7. scan for image only and scan for images only repeatedly.

Help one to scan only images and it will give the user opportunity to  utilize different ocr engines conveniently. Also it avoids delay between  each scan if one does not want to listen to the output. Images will be  saved in LIOS or one can choose his own destination. Now conversion can  be done using folder option.
8. Brightness checker.

To set a n exact value of brightness or threshold is the best way to  ensure maximum efficiency out of ocr engines. To find out the best  value, go to tools menu and select brightness checker. This utility will  scan for 15 or 17 times to complete the process. After the process,  number of words detected at different values will be shone in tabs. If  you want to know the precise value only, shift tab and then tab to apply  the value.
9. Audio conversion.

LIOS can convert the text opened in LIOS to wav files. To convert the  text in to speech, go to tools menu and select audio converter.
10. Text Manipulation.

To go to page, press ctrl+g and then type the page number, and tab to  OK. In the case of double page type only odd number, for example 1 in  the case of 1-2 and 11 in the case of 11-12. One can go to any line by  pressing ctrl+l and ctrl+f will help to find any word in the document.
11. Display preferences.

display preferences in the edit menu will help to set fond size, color , italic, bold and color of the background.
12. Engines.

There are 5 engines in LIOS.out of these only cuneiform can handle 24  languages, list given at the end. All other engines can handle only  English. Cuneiform is good for speed and picture skipping ,ocropus is  good for layout analysis and pdf conversion.
13. Artha.

In order to find out the meaning of English words, first select the word  and then press alt+ctrl+w and tab to find the meaning. Caution for the  first time one has to press alt+control+w twice so as to switch on artha
14. Spell checker.

A beta version of spell checker is added to the program.press ctrl f7  and all the misspelled words will appear and one can change them.
Cuneiform support Bulgarian, Croatian, Czech, Danish, Dutch, English,  Estonian, French, German, Hungarian, Italian, Latvian, Lithuanian,  Polish, Portuguese, Romanian, Russian, Russian-English bilingual,  Serbian, Slovene, Spanish, Swedish, Turkish, and Ukrainian.
[SIZE=3][COLOR=Red]Disclaimer[/COLOR][/SIZE]

    Copyright (c) 2011-2012 LIOS Development Team 

    All rights reserved . Redistribution and use in source and binary  forms, with or without modification, are permitted provided that the  following conditions are met: 

    Redistributions of source code must retain the below copyright notice, 

    this list of conditions and the following disclaimer. 

    Redistributions in binary form must reproduce the below copyright notice, 

    this list of conditions and the following disclaimer in the  documentation and/or other materials provided with the distribution. 

    Neither the name of the nor the easyocr team names of its 

    contributors may be used to endorse or promote products derived from  this software without specific prior written permission. 

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS  "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT  LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A  PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER  OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED  TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR  PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF  LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING  NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS  SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE." 

[SIZE=4][COLOR=Lime]FREE SOFTWARE FREE SOCIETY[/COLOR][/SIZE][SIZE=4]:guitar:[/SIZE]

---

