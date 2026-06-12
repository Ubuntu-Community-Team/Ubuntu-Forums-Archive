---
title: "Libre Office won't export as PDF"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-12-05
Running Ubuntu 12.04 Powerpc on an eMac G-4, 1GHZ processor, 1 GB RAM, 40 GB Hard drive.
   
  On this install I had originally loaded Libre Office 3 (don&#8217;t know if that&#8217;s the correct version number but it&#8217;s what displays when the program opens).  I thought everything worked on it till last night when I tried to export a Jpeg as a PDF file.  I tried clicking on both the PDF icon in the toolbar across the top and the &#8220;export as PDF&#8221; command in the &#8220;File&#8221; menu &#8211; neither worked. From the File command, it went to a window showing all the settings for the outgoing file with a button at the lower right that said &#8220;Export&#8221;. I clicked that and got a second window showing a default name for the file giving me a chance to re-name it, but there was no field showing where I wanted to send the file, and no button to &#8220;Save&#8221;.  I know those are supposed to be there because I watched a YouTube tutorial showing that they should be. If I clicked on the PDF icon in the toolbar, it just went to the previously mentioned second window showing the file, but with no option to direct or save it. I also tried exporting a regular text document with the same results.
   
  This software was installed through Synaptic and I didn&#8217;t tinker with any of the dependencies. Could there be a missing library or dependency that needs to be installed? On a previously installed OS, I had a version of Openoffice that had a button at the top to &#8220;Save as PDF&#8221; that was elegantly simple and worked like a charm.  Anyone know if it&#8217;s still there?

---

### Post by zombifier25 on 2012-12-05
The "Save" button was there for me. Can you post a screenshot?

It is possible that the window was too large, so the button was hidden. If so, Alt + Click to move the window around. Just a guess though.

---

### Post by Javelin Dan on 2012-12-05
Zombifier 25 – 
   
  I can certainly take a screenshot, though it will have to wait till after work this evening. That’s actually a good thought you had about the view being too large – I did think it looked like it wasn’t all displayed on the screen, but dullard that I am I never thought to adjust the view. I’ll try that first and report back. Thanks.

---

### Post by SeijiSensei on 2012-12-05
When you say you tried to export a JPEG as a PDF, do you mean you imported the graphic into Writer then tried to export the document you created?

If you want to convert graphics to PDFs, the easiest solution by far is to use Imagemagick, though it means typing a few commands at the prompt.  (I think there may be a GUI front-end for Imagemagick, but I've never used it.)

Install it with "sudo apt-get install imagemagick" then use the command:

```
convert image.jpeg image.pdf
```

That's it!

---

### Post by Javelin Dan on 2012-12-05
I apologize for not being specific. What I actually did was to scan a document via "simplescan" which automatically gets saved as a Jpeg. I then opened it with Libre Office Writer. I also tried Impress and Draw with the same results. 

Thanks for the heads-up on "Imagemajick". If I can't get Libre Office to work, I'll definitely give that a go.

---

### Post by SeijiSensei on 2012-12-05
I opened a graphic in Writer, and it came up in Draw.  To export it from there, click on the object so it is highlighted in a frame, then choose File > Export as PDF, and click the "Selection" box in the dialog that follows.  That worked for me.  

One of the most annoying aspects of Calc for me is that you cannot directly export charts.  You have to go through a convoluted process of copying the chart, dropping it into Impress, then clicking on the object and exporting it from there as, say, a PNG.  Gnumeric lets you export directly, but I don't like the look of the charts it creates as much as the ones in Calc.  

I have found the ability to save to PDF from Calc useful when exporting tables.  I select the table, export to PDF, open the PDF in GIMP, then crop the image to include just the table.  If it is too big, I can rescale the image to a more manageable size.  You can then save to PNG from within GIMP.  Make sure to use lossless compression when you write the original PDF to ensure that the text is not too blurry, especially if you need to resize the result before publication.

Examples of both types of exports appear in my blog linked below.

---

### Post by Javelin Dan on 2012-12-05
I'll try that and report back. Thanks!

---

### Post by gordintoronto on 2012-12-06
You could install cups-pdf, which lets you "print" to a PDF file from any application.

---

### Post by Javelin Dan on 2012-12-06
I actually did install cups-pdf, but don't see any option to print to pdf in the file menu. Is it a CLI application only? If so, I'll need instructions. Life got in the way and I only had time last night to go back and check to see if I could somehow scroll down or change the view - I couldn't. I'll try to post a screen shot tonight to display the screen I'm getting.

---

### Post by Impavidus on 2012-12-06
> **SeijiSensei said:**
> I opened a graphic in Writer, and it came up in Draw.  To export it from there, click on the object so it is highlighted in a frame, then choose File > Export as PDF, and click the "Selection" box in the dialog that follows.  That worked for me.  

One of the most annoying aspects of Calc for me is that you cannot directly export charts.  You have to go through a convoluted process of copying the chart, dropping it into Impress, then clicking on the object and exporting it from there as, say, a PNG.  Gnumeric lets you export directly, but I don't like the look of the charts it creates as much as the ones in Calc.  

I have found the ability to save to PDF from Calc useful when exporting tables.  I select the table, export to PDF, open the PDF in GIMP, then crop the image to include just the table.  If it is too big, I can rescale the image to a more manageable size.  You can then save to PNG from within GIMP.  Make sure to use lossless compression when you write the original PDF to ensure that the text is not too blurry, especially if you need to resize the result before publication.

Examples of both types of exports appear in my blog linked below.
This sounds ugly. There ought to be a way of exporting tables and charts, nicely cropped, to a pdf in vector format. Anything involving GIMP or png will turn it into a raster image, something you never want with text and charts. Off course I know you can use a pdf printer driver, turn you pdf into postscript (or directly use a postscript printer driver), edit your postscript in a text editor to get nice cropping/margins/clipping and convert the result back into pdf, but that's messy too, although file size stays pretty low.

---

### Post by SeijiSensei on 2012-12-06
Those options really aren't available if you are exporting charts and tables to the web.  I could use HTML tables for the latter, but WordPress doesn't make that especially easy.  The last time I created a table I had to hand-code the HTML.  As for charts, the options are basically PNG and JPEG.

I'm not the only one who uses graphics to present data tables; just take a look at Nate Silver's [538 Blog]("http://fivethirtyeight.blogs.nytimes.com/") for examples.

---

### Post by gordintoronto on 2012-12-06
> **Javelin Dan said:**
> I actually did install cups-pdf, but don't see any option to print to pdf in the file menu...

Cups-pdf installs a "printer," so you select it in the Print sub-menu.

---

### Post by Javelin Dan on 2012-12-06
OK, here are the windows I get when I try to "Export as PDF...

---

### Post by levlaz on 2012-12-06
EDIT: Forgot to mention, it makes me really happy to see that you are running 12.04 on a PPC Emac.. I have an older one at home that I rarely use anymore but ran 10.04 on it for years. :) Long Live PPC! :D 

I think the save button is hidden on the bottom as mentioned earlier. Try to click that little arrow to minimize the "filetype" -- then try to move the window up or down and you should see the save button. 

Lastly if none of that works -- click into the box where you name it and .. Name the document "whatever.pdf" and press enter it should just save at that point. (Just tried it and it worked for me)

---

### Post by Javelin Dan on 2012-12-07
Thanks levlaz - I'll check that out ASAP, which probably won't be until sometime this weekend. Thanks for the tip. I also tried to save this as a PDF out of GIMP but was unable to...don't remember exactly why at the moment. I'll look into that as well.


Yeah, I previously had Ubuntu 10.10 Ppc. installed on this box and it was quite snappy - loved that distro! 12.04 is a little more ponderous, but I went for the 5-year LTS like a ham sandwich. This is my wife's machine and she knows way less about computers than even I do, so she wants everything to "just work". I installed the Lubuntu desktop on it, and so far she's had no complaints other than the normal miscues any rookie would make on any OS. I've tried several other Ppc distros. Debian Ppc is a little too geeky for me - couldn't quite get the hang of updating through the back-ports when my browser crashed 'cause it wasn't supported anymore. I really Liked Mint Linux Ppc as it runs like the wind. But since it's Debian based, I crashed and burned that too, klutz that I am. Ubuntu has proved to be the most stable, forgiving, and goof proof distro I've found. At least I haven't screwed it up -yet!

---

### Post by Javelin Dan on 2012-12-07
gordintoronto - I did pull up my print menu and I *did* see the option to select PDF. But I'm a little cloudy on how to save the image as a PDF from that point. Please enlighten me...

---

### Post by gordintoronto on 2012-12-07
Select PDF as your "printer," and click on Print. The PDF should go into a folder in your /home, called PDF.

---

### Post by Javelin Dan on 2012-12-07
_***BINGO!!!***_   Both suggestions worked as advertised!

lavlaz - Clicking the file button had no real effect, I couldn't move the panel around, and I never could find a save button. But simply clicking "Enter" did the trick. My PDF was saved in my documents folder. What threw me was that once I named the file, it never did get titled in that window as a "PDF" even though I had selected that option on the previous panel. But it showed up in my documents folder as one. 


gordintoronto - Your solution also worked as advertised! I couldn't get my head around asking it to "print" when actually all it does is save the document as a PDF in a new file it creates in your documents file, but it did exactly that. 


Thanks to you both and all who weighed in. I now have at least two tools with which to create PDF's. Though I have to admit, I still long for Openoffice were you just clicked on the little icon to "save as PDF" and it was done. I'll go ahead and mark this puppy as _***solved!***_

---

### Post by vasa1 on 2012-12-09
> **SeijiSensei said:**
> ...  
One of the most annoying aspects of Calc for me is that you cannot directly export charts. ...
There *may* be good news according the [release notes for LibreOffice 4 (beta)]("http://wiki.documentfoundation.org/Releases/4.0.0/Beta1"):
> [fdo#30944]("https://bugs.freedesktop.org/show_bug.cgi?id=30944") Allow exporting a single chart (or other object) to different formats (PDF, SVG, PNG, JPG), target document with object size [Tomaž Vajngerl]

---

### Post by SeijiSensei on 2012-12-09
Thanks!  I'll keep an eye out, or maybe give the beta a spin.

---

### Post by levlaz on 2012-12-10
Glad to see this worked out -- hopefully this old emac will serve you well for years to come. :)

---

### Post by vasa1 on 2012-12-11
> **SeijiSensei said:**
> Thanks!  I'll keep an eye out, or maybe give the beta a spin.
I'm not brave enough but if you're interested here are two links:
[LibreOffice 4.0 Beta released ready for a marathon test]("http://www.h-online.com/open/news/item/LibreOffice-4-0-Beta-released-ready-for-a-marathon-test-1765275.html")
[LibreOffice 4.0 Test Marathon: December 14 to 19]("http://nabble.documentfoundation.org/LibreOffice-4-0-Test-Marathon-December-14-to-19-td4023197.html")

---

