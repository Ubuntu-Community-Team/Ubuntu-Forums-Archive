---
title: "pdf pages different widths: mogrify -resize 1200 doesn't work"
date: 2013-10-11
forum: New to Ubuntu
---

### Post by afc888ny on 2013-10-11
I would like to add in certain pages containing answers to a pdf file of Chapter 3 of a Calculus book scan.  I am on a lubuntu 13.04 platform on a Samsung netbook.  Unfortunately, when I concatenate the pages with the answers, the pages with the answers (croped segments of pages) always shows up as a different width than the other pages. I would like all pages to have uniform width.  
 

 I execute this in three parts, first I create and put all the jpg files I want to make into an ebook(chapter) in a folder /home/a/Documents/Calc03PrProject/1200Produce folder.  I I then enter into terminal:
 

 [SIZE=1]a@a-NC210-NC110:~/Documents/Calc03Project/1200Produce$ mogrify -verbose -format png -resize 1200 -quality 100% *.jpg[/SIZE]
 [SIZE=1]Calc03-000.jpg JPEG 1200x1696 1200x1696+0+0 8-bit DirectClass 900KB 0.130u 0:00.129[/SIZE]
 [SIZE=1]Calc03-000.jpg=>Calc03-000.png JPEG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.876MB 2.370u 0:02.370[/SIZE]
 [SIZE=1]Calc03-001.jpg JPEG 1200x1696 1200x1696+0+0 8-bit DirectClass 801KB 0.120u 0:00.129[/SIZE]
 [SIZE=1]Calc03-001.jpg=>Calc03-001.png JPEG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.528MB 2.320u 0:02.330[/SIZE]

 [SIZE=1]...[/SIZE]
 

 The reason I use the mogrify command rather than the convert command (imagemajick) is because I have a netbook and whenever someone converts more than 20 files at the same time on a netbook, you get a memory error message and the whole process crashes.  
 

 I then move the above pdf files into a subfolder ToBind.  I check permissions with ls -la and it shows the product pdf files are &#8220;-rw-rw-r-- 1 a a  903885 10[FONT=Arial, sans-serif]&#26376;[FONT=Liberation Serif, Times New Roman, serif] [/FONT][/FONT]11 11:25 Calc03-043.pdf&#8221;.  To be on the safe side, I change this with chmod 777 *.png.  I then enter the second mogrify command:
 

 [SIZE=1]a@a-NC210-NC110:~/Documents/Calc03Project/1200Produce$ cd ToBind[/SIZE]
 [SIZE=1]a@a-NC210-NC110:~/Documents/Calc03Project/1200Produce/ToBind$ mogrify -verbose -format pdf *.png[/SIZE]
 [SIZE=1]Calc03-000.png PNG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.879MB 0.200u 0:00.199[/SIZE]
 [SIZE=1]Calc03-000.png=>Calc03-000.pdf PNG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.892MB 1.530u 0:01.480[/SIZE]
 [SIZE=1]Calc03-001.png PNG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.528MB 0.190u 0:00.199[/SIZE]
 [SIZE=1]Calc03-001.png=>Calc03-001.pdf PNG 1200x1696 1200x1696+0+0 8-bit DirectClass 1.544MB 1.490u 0:01.440[/SIZE]
 &#8230;
 

 I then run &#8220;pdftk *.pdf cat output CalcCh03.pdf&#8221; and get a pdf file with pages of different widths.
 [SIZE=1]a@a-NC210-NC110:~/Documents/Calc03Project/Produce/ToBind$ pdftk *.pdf cat output CalcCh03.pdf[/SIZE]
 [SIZE=1]a@a-NC210-NC110:~/Documents/Calc03Project/Produce/ToBind$ [/SIZE] 
 

 [SIZE=3]Is resizing jpg pages into 1200 width then turning them into pdf pages in order to produce an ebook that has congruent widths something that computers simply can't do yet?  Do I have a false expectation on what a computer is capable of??[/SIZE]
 

 [SIZE=3]What can I do to make all pages in this pdf file a congruent width?[/SIZE]
 

 [SIZE=3]Andrew[/SIZE]

---

### Post by afc888ny on 2013-10-12
Anyone out there?

---

