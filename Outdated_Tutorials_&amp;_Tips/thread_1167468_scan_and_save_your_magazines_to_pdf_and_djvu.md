---
title: "scan and save your magazines to pdf and djvu"
date: 2009-05-22
forum: Outdated Tutorials &amp; Tips
---

### Post by stinger30au on 2009-05-22
Here's how I do my scanning and hopefully someone might learn from my experiences thus for from the last 5 months

First off, start off with a copy of Ubuntu Linux from [www.ubuntu.com]("http://www.ubuntu.com/")
you can download it via torrent or ftp or even request a free cd copy of it or hunt and see if there is a Linux user
group and maybe someone there will have a copy they will gladly let you have a copy of

the choice is yours if you want to install ubuntu to internal hdd or usb memory stick or what ever. Theres tons
of ways to do it. Help is at [www.ubuntuforums.org]("http://www.ubuntuforums.org/") or you can email me. Im no expert at it but I have installed
it to external hdd, external thumbdrive, dual boot off one hdd and dual hdd too.

And for what we want to do you could even argue the fact that you dont even need to install ubuntu 

anyhow

so once ubuntu is installed, in using 9.04 currently on one and 8.04 on the other you need to fireup shell

shell is the command line, just like OS9 or messy, oops , msdos, only shell is much more powerful

with a bit of luck you can plug your usb scanner in and ubuntu will recognise it and were in business. If it
doesn't work and you need to install drivers.... don't ask me. I have no idea. Ask at [www.ubuntuforums.org]("http://www.ubuntuforums.org/")

ok, now we need to install the scanner software that I use its called "gscan2pdf" it is an open-source bit of
gear and it does exactly what I need standing on is head

its homepage is here
[http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/)

to install it from shell type in

sudo apt-get install gscan2pdf

while your at it , install pdftk as well, its the PDF slicer/dicer/boxer I use to manipulate all my PDF files with

sudo apt-get install pdftk

and we will also need pdf2djvu so once we have our high quality PDF we can convert to djvu at 400 dpi and save
mobs of space and have very detailed documents as well
soa gin from shell we type in

sudo apt-get install pdf2djvu

ok well that's all the tools we need

lets go scanning

fire-up gscan2pdf and click the scan button. With a bit of luck your usb scanner will be auto-magically
picked and you will see it and some settings to change

my main scanner im using is a HP scan-jett 6300 with 25 sheet adf &#150; automatic document feeder &#150; like a fax
machine for the ones whodon'tt know what an adf is.

I can select the speed I want to scan at I always select the fastest

next is resolution I always select 300

next is the mode of scan we have 

line-art
half-tone
grey-scale
colour

line-art is essentially a black and white scan with very little difference in the colour of black/grey
this is great to use on pages that are essentially just plain black. DONT USE THIS MODE IF PHOTOS ARE ON THE
PAGE. They look horrid in this mode. This mode takes up only  a little space.

half-tone will take a very dark black original piece of paper and when scan turn it in to a very dull looking
grey picture on your pc. Who knows they you will ever need this mode for.

Grey scale. Use this mode if you have a black/white mag or newspaper and there's photos on the page. This mode
will give you quite good looking b/w reproduction and looks magic.this mode takes up a fair-bit of space,
but not as bad as full colour

full colour.... well I think this is self explanatory

ok so here's how I crank out a scanned magazine

scan about 10 to 20 pages and then save

now when saving there is a number of options to save your scanned pages youuu can save aindividualll page or
save the entire lot and you have the choice as to wehter or not you use jpeg or a feotherer formats as well.

>From my experiments I have found that when saving to PDF I use the compression method of jpeg.
Jpeg is a "lossy format" so to combat the loss of quality I save at 84% quality. If I save at 85% quality the file
size jumps to amazing proportions, so I leave it at 84%
so repeat this scanning process for your book and you will wind up with your data saved in a directory and file
names that look like this

my.magazine.part1.pdf
my.magazine.part2.pdf
my.magazine.part3.pdf
my.magazine.part4.pdf
my.magazine.part5.pdf

ok so for argument sake we will say that each file was 20 pages in it and is 20 megabyte long so when all joined
together we will have a single PDF 100meg long and all pages in numerical order

so to archive this we fire-up shell again and go in to the directory where we saved our files and fire-up pdftk

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

pdftk lets us do all sorts of groovy stuff to PDF files. We are going to use it to join our individual files
together and make one. It will do this standing on its head. It has numerous groove features, but I wont go in
to that here

ok so from shell we type in

pdftk my.

And now e press the tab button on our keyboard and like magic we will now have in front of our very eyes

pdftk my.magazine.part 

told you shell was powerful. It scanned the directory and magically added in the "magazine.part" for us
now we press 1 so we now have

pdftk my.magazine.part1

now we press tab button again and we now have in-front of us

pdftk my.magazine.part1.pdf

smart ain't it. For very little time/effort we are getting our files in
so no we repeat the process of hitting tab and pressing 2 3 4 5 when needed and in a matter of seconds we scan type
in this command line

pdftk my.magazine.part1.pdf my.magazine.part2.pdf my.magazine.part3.pdf my.magazine.part4.pdf my.magazine.part5.pdf

lets see you type this in on a standard windows command line and see how slowly you do it. LOL!
Next we need to tell pdftk that we are going to join all files together in to one giant file so we add this
cat output my.magazine.pdf verbose

this is the bit we add to the end of what we typed so our entire command line will read like this

pdftk my.magazine.part1.pdf my.magazine.part2.pdf my.magazine.part3.pdf my.magazine.part4.pdf
my.magazine.part5.pdf  cat output my.magazine.pdf

the verbose command at the end tells shell to echo to the screen what the program is doing. This saves you
guessing what the heck is going on. Cos if you don't do this when you press enter you get no feedback from the program

so press enter and watch the pages fly by. In a matter of seconds you will back at your command prompt with a
flashing cursor.

No look at the directory and you will see the final bit of gear called

my.magazine.pdf

open it up with document viewer and scroll down and admire the 100 page document you have pieced together.

Now.. have a lookie at the file size. I get it will be around 110 megabyte or perhaps a little more.

so. now to convert this to djvu format and keep the high quality pages but lose the file size and make it smaller

so fire-up shell and type in

pdf2djvu -o my.magazine.djvu -d400 -v my.magazine.pdf 

ok to explain this a little we have told the program that the output file will be called 

my.magazine.djvu

we told it we want it to compress using 400 dpi with this

-d400

we told it we want to see some output to the screen so we know that the heck is going on

-v

and we told it the name of our original file is
my.magazine.pdf

now press enter.

You will see something like this

aussie.coco.june.1988.pdf:

- page #1 -> #1:

  - image size: 3199x4332

  - 353010 bytes out

- page #2 -> #2:

image size: 3199x4332

(I have deleted many pages out of this bit)

  - 341857 bytes out

- page #76 -> #76:

  - image size: 3167x4332

  - 450144 bytes out

0.210 bits/pixel; 3.858:1, 74.08% saved, 105702515 bytes in, 27394816 bytes out

so you get the idea.

Now look in the directory and you will see your .djvu file and your original PDF pieces and your final PDF.

Ditch the files that are the .part1.pdf stuff and keep the pdf and djvu files.
Dont destroy the PDF files. PDF file originals are easier to work with then djvu files. So do any editing to
the PDF and then remake the djvu file.

Piece of cake.


this little script will convert all pdf files in a directory to djvu



Hope this might help someone else who wants to do their own scanning

this little script will convert all pdf to djvu in the directory

# !/bin/sh

for i in *.pdf ; do
        j=`basename $i | sed -e 's/\.pdf//'`
        pdf2djvu --dpi=400 -o $j.djvu $i
done

---

### Post by zelhar on 2009-06-21
Thanks for the detailed guide.

Why do you insert --dpi=400 when you only scan a resolution of 300dpi ?

---

### Post by stinger30au on 2009-06-22
> **zelhar said:**
> Thanks for the detailed guide.

Why do you insert --dpi=400 when you only scan a resolution of 300dpi ?

easy peasy

Djvu is a "lossy" format

this means you lose picture quality when you save pictures in this format

this is one of the main reasons the data file it creates is about 1/4 of the size and less of a pdf file

*SO*

to combat the loss of picture quality you *INCREASE* the resolution of the djvu file to 400 dpi

this makes the djvu file slighty bigger then a 300 dpi djvu file and you have quality that is almost as good as a 300 dpi pdf.

when you try it and see for yourself, you will see why the djvu files need to be saved at 400 dpi

---

