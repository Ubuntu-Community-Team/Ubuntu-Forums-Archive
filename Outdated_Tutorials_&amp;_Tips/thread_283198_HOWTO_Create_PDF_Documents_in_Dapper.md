---
title: "HOWTO: Create PDF Documents in Dapper"
date: 2006-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by dbott67 on 2006-10-23
[COLOR=Blue]*UPDATE (April 9, 2007): According to others, this also works in Edgy & Feisty.*[/COLOR]

In OpenOffice, there is a command in the File menu 'Export as PDF'.  For other applications, you will need to do the following:

1. Install cups-pdf
```
sudo apt-get install cups-pdf
```2. A hack to allow Dapper to create PDF Printer (from [here]("https://launchpad.net/distros/ubuntu/+source/cups-pdf/+bug/42147"))
```
sudo chmod +s /usr/lib/cups/backend/cups-pdf
```3. Configure CUPS for the PDF printer.
  - Select **SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER**
  - Select **LOCAL PRINTER**
  - Use detected printer: **PDF PRINTER**
  - Select Print Driver: 
    - Manufacturer: **Generic**
    - Model: **Postscript Color Printer**
    - Name: **postscript-color-printer-rev3b**
  - Click APPLY
4. When printing from any application, select the newly created **postscript-color-printer-rev3b** printer to generate PDF files.

Output files are stored in your home directory under **/PDF** subirectory.  

To change the default location of the PDF output:
[quote=dowdberry]Edit the **/etc/cups/cups-pdf.conf** file
```
gksudo gedit /etc/cups/cups-pdf.conf
```Search for:
```
Out ${HOME}/PDF
```and change to something more meaningful:
```
Out ${HOME}/my_print_to_pdf_folder
```and restart:
```
sudo /etc/init.d/cupsys restart
```[/quote]

-Dave

---

### Post by ahbazan on 2006-11-16
FYI- looks like this trick works in Edgy as well.

Just use driver name postscript-color-printer-rev4

---

### Post by BLTicklemonster on 2006-11-16
Is there a way that one might open a pdf file and manipulate it in ubuntu?

---

### Post by dbott67 on 2006-11-16
Not that I'm aware of.  You would need to copy the text from the PDF into OpenOffice, edit it, and then export it as a new PDF.

The problem is that the original PDF may have been created in a program using some unique fonts & layouts that could get lost when copying over to OpenOffice.

-Dave

---

### Post by BLTicklemonster on 2006-11-16
:( oh well.

---

### Post by stalefries on 2006-11-16
I hear that Abiword will be having, or currently has, a PDF import plugin. I'll go see if I can find out which version that's in.

---

### Post by dpm on 2006-11-17
> **dbott67 said:**
> 
Output files are stored in your home directory under **/PDF** subirectory.

-Dave

Is there a way to change this default location?

---

### Post by dowdberry on 2006-11-17
looks in the /etc/cups/cups-pdf.conf file

Search for:
Out ${HOME}/PDF

and change to something more meaningul:
Out ${HOME}/my_print_to_pdf_folder

and restart:
/etc/init.d/cupsys restart

---

### Post by dpm on 2006-11-18
> **dowdberry said:**
> looks in the /etc/cups/cups-pdf.conf file

Search for:
Out ${HOME}/PDF

and change to something more meaningul:
Out ${HOME}/my_print_to_pdf_folder

and restart:
/etc/init.d/cupsys restart

Worked wonders, thanks.

**dbott67**, could you please add this to the original guide?

and maybe also note that you need to restart the cups service as sudo, as some people might not know this (most people I know just copy and paste the instructions given):

```
[COLOR=Red]sudo[/COLOR] /etc/init.d/cupsys restart
```Cheers

---

### Post by dbott67 on 2006-11-18
Done... thanks dowdberry & desp.

-Dave

---

### Post by tubunu on 2006-11-18
You can easily create a PDF file with OpenOffice.org Writer. Just create your document and hit export directly as PDF. :)

---

### Post by dbott67 on 2006-11-18
> **tubunu said:**
> You can easily create a PDF file with OpenOffice.org Writer. Just create your document and hit export directly as PDF. :)

Yes... it says so the very first line in the post:  :)
[quote=dbott67]**In OpenOffice, there is a command in the File menu 'Export as PDF'.** For other applications, you will need to do the following:[/quote]

However, if you wanted to create a PDF from Firefox or Evolution or any other application, you would need to follow the HOWTO.

-Dave

---

### Post by Tibor60 on 2006-12-20
It works fine with 1 page from Firefox, but if several pages, I always have the same problem:
the last row of the page is divided horizontally and the missing lower part is on the next page. I tried to play with the page setup, margins, printer properties, but nothing help...

Can somebody help me?

---

### Post by dbott67 on 2006-12-20
Can you post a screenshot?  I'm not sure I can picture the problem... what website are your trying to print from?

Here's a screenshot of the PDF output of this page.

-Dave

---

### Post by Gen2ly on 2007-03-17
Appreciate the info.  I was trying to save a webpage to print a little bit later.  This tutorial today helped me do that on Efty. :)

---

### Post by dannyboy79 on 2007-03-28
if I own the real version of Adobe Acrobat 5.0 Pro (or is it 6.0? )which has the distiller installed in Win XP Pro (which allows a person to print anything to pdf from any app) and I am sharing that printer, is there a way that I can use the distiller on WinXP Pro to print to pdf within ubuntu, dapper or edgy? Or do I have to follow your guide to print to pdf from anywhere? I haven;'t tried it yet but I suppose all I would have to do is try.

---

### Post by dbott67 on 2007-03-28
> **dannyboy79 said:**
> if I own the real version of Adobe Acrobat 5.0 Pro (or is it 6.0? )which has the distiller installed in Win XP Pro (which allows a person to print anything to pdf from any app) and I am sharing that printer, is there a way that I can use the distiller on WinXP Pro to print to pdf within ubuntu, dapper or edgy? Or do I have to follow your guide to print to pdf from anywhere? I haven;'t tried it yet but I suppose all I would have to do is try.

You could always try it... I don't know if it will work though.  Let us know hoe you make out.

-Dave

---

### Post by motin on 2007-04-06
> **ahbazan said:**
> FYI- looks like this trick works in Edgy as well.

Just use driver name postscript-color-printer-rev4

As well as in Feisty. Driver name is simply "postscript color" however.

---

### Post by dannyboy79 on 2007-04-09
> **motin said:**
> As well as in Feisty. Driver name is simply "postscript color" however.

you should make a new post and call it the same thing for the title but with Fiesty otherwise many people won't ever see this since the title say Dapper.

---

### Post by dbott67 on 2007-04-09
I updated the title on the first post to include Edgy & Feisty.

-Dave

---

### Post by kagashe on 2007-05-05
> Configure CUPS for the PDF printer.
- Select SYSTEM > ADMINISTRATION > PRINTERS > NEW PRINTER
- Select LOCAL PRINTER
- Use detected printer: PDF PRINTER
- Select Print Driver:
- Manufacturer: Generic
- Model: Postscript Color Printer
- Name: postscript-color-printer-rev3b
- Click APPLYI don't see "Generic" in the list of Manufacturers on Feisty.

kagashe

---

### Post by dbott67 on 2007-05-05
> **kagashe said:**
> I don't see "Generic" in the list of Manufacturers on Feisty.

kagashe

It's there on my Feisty system (see attached screenshot).

-Dave

---

### Post by kagashe on 2007-05-05
Now I can see it.

I don't know whether it was really there after I installed cups-pdf. Perhaps you have to restart cupsys after changing permissions.

kagashe

---

### Post by craigsn on 2007-07-05
I have feisty installed, the amd64 bit version. I followed the directions to install the cupspdf driver. When I print, the output was blank in the PDF file. Any suggestions?

Thanks

---

### Post by Oldbones on 2007-08-07
found the [original]("http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html") first.  I should note that I don't believe code unless it comes from this forum.

<--- from out of left field 
  Can QA Engineers get jobs with open source?

Oldbones

---

### Post by Gen2ly on 2007-08-07
> **Oldbones said:**
> found the [original]("http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html") first.  I should note that I don't believe code unless it comes from this forum.

<--- from out of left field 
  Can QA Engineers get jobs with open source?

Oldbones

Nice, Ubuntu has a nice QA team.  I have Ubuntu on my other laptop that I'm not using at the moment.  The laptop I'm using now is using a seperate distro, and I lately discovered what can happen if a QA team doesnt' exist.  It's just bad policy nowadays to be without one.  I'm becoming more interested in QA and am trying to learn more about it.

---

### Post by JulianF on 2007-08-09
Thanks Dbott, that worked perfectly. I was pulling my hair out over getting PDFs produced 

Cheers
Julian F

---

### Post by dbott67 on 2007-08-09
> **Oldbones said:**
> found the [original]("http://www.ubuntugeek.com/how-to-create-pdf-documents-in-ubuntu.html") first.  I should note that I don't believe code unless it comes from this forum.

The "original" did come from these forums --- 7 months after it was written (and virtually word-for-word).

The thing that bothers me about the aforementioned site is this:

1. He does not appear to be related to the real "Ubuntu-geek" (Ryan, the guy who started these forums).  Kind of like Steve Jobs starting a site called "www.bill-gates.com".

2. The site seems to be "borrowing" (some) uncredited content from other sites (such as this one; word-for-word, no less).  The part that bothers me is that the culprit is running an ad-sponsored site (which is generating a small amount of money) based upon writings that were not created by the site owner and is not credited to the original site or poster.

I realize that much of the "knowledge" that I have gained has come from reading other posts, but I generally try to credit the OP whenever possible (definitely if I copy and paste their answer --- which is essentially what was done with this HOWTO.

@JulianF: You're welcome.  Glad it worked.

-Dave

---

### Post by dannyboy79 on 2007-08-09
> **dbott67 said:**
> The "original" did come from these forums --- 7 months after it was written (and virtually word-for-word).

The thing that bothers me about the aforementioned site is this:

1. He does not appear to be related to the real "Ubuntu-geek" (Ryan, the guy who started these forums).

2. The site seems to be "borrowing" (some) uncredited content from other sites (such as this one; word-for-word, no less).  The part that bothers me is that the culprit is running an ad-sponsored site (which is generating a small amount of money) based upon writings that were not created by the site owner and is not credited to the original site or poster.

I realize that much of the "knowledge" that I have gained has come from reading other posts, but I generally try to credit the OP whenever possible (definitely if I copy and paste their answer --- which is essentially what was done with this HOWTO.

@JulianF: You're welcome.  Glad it worked.

-Dave
i agree with you, I hate people that don't credit other's or document the source of the info IF it didn't come from there own hard work.

---

### Post by yangli on 2007-09-24
Cool. Works perfectly on my machine. Thanks a lot.

---

### Post by gnulab on 2010-12-22
> **BLTicklemonster said:**
> Is there a way that one might open a pdf file and manipulate it in ubuntu?

you could try pdfedit

---

