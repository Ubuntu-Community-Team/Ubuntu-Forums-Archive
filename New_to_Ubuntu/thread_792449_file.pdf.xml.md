---
title: "file.pdf.xml"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by OZFive on 2008-05-12
Okay I am having a issue here folks and I need some guidance.  I have a file that is sent to me by an employee of mine and it is not readable by anything I can find cause for some reason it has a .xml tag on it.

He scans his paper at home,
Saves it as PDF,
Selects file.pdf,
Sends it to me via Yahoo eMail,
I receive file.pdf.xml

I just at my wits end here folks and need some of that famous Ubuntu help!

---

### Post by SunnyRabbiera on 2008-05-12
well did you try to remove the .xml tag after you save the file?

---

### Post by OZFive on 2008-05-12
Yeah tried that one.  No joy.

---

### Post by SunnyRabbiera on 2008-05-13
something must be happening on his end then, it might be because of yahoo too.

---

### Post by OZFive on 2008-05-13
I had the same exact thought that for some reason, some how Yahoo is screwing wiht the files cahnging them for some reason.  But I am sure there is a solution somewhere...

---

### Post by OZFive on 2008-05-13
Anyone else want to venture a guess here?

---

### Post by Monicker on 2008-05-13
Need more info.  How is he converting the file to pdf?  Is the xml file you received binary or does it actually contain ASCII xml data?  Have him send you a pdf file downloaded from the internet, to see if the same thing happens to it.

There are different versions of the pdf format, and perhaps something is being misinterpreted somewhere along the path.

---

### Post by Linux&amp;Gsus on 2008-05-13
Ask him if he can zip the pdf and send it then. Maybe that helps.

Cheers,
Steve

---

### Post by OZFive on 2008-05-13
> **Monicker said:**
> Need more info.  How is he converting the file to pdf?  Is the xml file you received binary or does it actually contain ASCII xml data?  Have him send you a pdf file downloaded from the internet, to see if the same thing happens to it.

There are different versions of the pdf format, and perhaps something is being misinterpreted somewhere along the path.

We tried .jpeg .gif. and .bmp  ALL come with the .xml conv

This is some of what I get...
> 
This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
<?mso-application progid="Word.Document"?>
&#8722;
<w:wordDocument w:macrosPresent="no" w:embeddedObjPresent="no" w:ocxPresent="no" xml:space="preserve">
<w:ignoreElements w:val="http://schemas.microsoft.com/office/word/2003/wordml/sp2"/>
&#8722;
<o:DocumentProperties>
<o:Author
<o:Created>2008-05-12T23:44:00Z</o:Created>
<o:LastSaved>2008-05-12T23:44:00Z</o:LastSaved>
<o:Pages>1</o:Pages>
<o:Words>0</o:Words>
<o:Characters>0</o:Characters>
<o:Lines>1</o:Lines>
<o:Paragraphs>1</o:Paragraphs>
<o:CharactersWithSpaces>0</o:CharactersWithSpaces>
<o:Version>11.0000</o:Version>
</o:DocumentProperties>
&#8722;
<w:fonts>
<w:defaultFonts w:ascii="Times New Roman" w:fareast="Times New Roman" w:h-ansi="Times New Roman" w:cs="Times New Roman"/>
</w:fonts>
&#8722;
<w:styles>
<w:versionOfBuiltInStylenames w:val="4"/>
<w:latentStyles w:defLockedState="off" w:latentStyleCount="156"/>
&#8722;
<w:style w:type="paragraph" w:default="on" w:styleId="Normal">
<w:name w:val="Normal"/>
&#8722;
<w:rPr>
<wx:font wx:val="Times New Roman"/>
<w:sz w:val="24"/>
<w:sz-cs w:val="24"/>
<w:lang w:val="EN-US" w:fareast="EN-US" w:bidi="AR-SA"/>
</w:rPr>
</w:style>

&#8722;
<w:style w:type="table" w:default="on" w:styleId="TableNormal">
<w:name w:val="Normal Table"/>
<wx:uiName wx:val="Table Normal"/>
<w:semiHidden/>
&#8722;
<w:rPr>
<wx:font wx:val="Times New Roman"/>
</w:rPr>
&#8722;
<w:tblPr>
<w:tblInd w:w="0" w:type="dxa"/>
&#8722;
<w:tblCellMar>
<w:top w:w="0" w:type="dxa"/>
<w:left w:w="108" w:type="dxa"/>
<w:bottom w:w="0" w:type="dxa"/>
<w:right w:w="108" w:type="dxa"/>
</w:tblCellMar>
</w:tblPr>
</w:style>
&#8722;
<w:style w:type="list" w:default="on" w:styleId="NoList">
<w:name w:val="No List"/>
<w:semiHidden/>
</w:style>
</w:styles>
&#8722;
<w:docPr>
<w:view w:val="print"/>
<w:zoom w:percent="100"/>
<w:doNotEmbedSystemFonts/>
<w:attachedTemplate w:val=""/>
<w:defaultTabStop w:val="720"/>
<w:punctuationKerning/>
<w:characterSpacingControl w:val="DontCompress"/>
<w:optimizeForBrowser/>
<w:validateAgainstSchema/>
<w:saveInvalidXML w:val="off"/>
<w:ignoreMixedContent w:val="off"/>
<w:alwaysShowPlaceholderText w:val="off"/>
&#8722;
<w:compat>
<w:breakWrappedTables/>
<w:snapToGridInCell/>
<w:wrapTextWithPunct/>
<w:useAsianBreakRules/>
<w:dontGrowAutofit/>
</w:compat>
&#8722;
<wsp:rsids>
<wsp:rsidRoot wsp:val="00852BB2"/>
<wsp:rsid wsp:val="006E6C41"/>
<wsp:rsid wsp:val="007A069C"/>
<wsp:rsid wsp:val="00852BB2"/>
<wsp:rsid wsp:val="00F960C4"/>
</wsp:rsids>
</w:docPr>
&#8722;
<w:body>
&#8722;
<wx:sect>
<w:p wsp:rsidR="006E6C41" wsp:rsidRDefault="006E6C41"/>
&#8722;
<w:sectPr wsp:rsidR="006E6C41">
<w:pgSz w:w="12240" w:h="15840"/>

</wx:sect>
</w:body>
</w:wordDocument>


We have not tried the zip of the file yet and that might be something we can try but I am anticipating a file.zip.xml

---

### Post by Monicker on 2008-05-13
Did you check the file contents to see if its binary or ascii data?  Could you attach one of the xml files to a post here?

---

### Post by Rytron on 2008-05-13
> **Linux&Gsus said:**
> Ask him if he can zip the pdf and send it then. Maybe that helps.

Cheers,
Steve

I agree with Linux&Gsus, adding the file to an archive may solve the problem. If zip doesn't work try 7zip,rar,etc.

---

### Post by OZFive on 2008-05-13
We will try a zip later today.

I edited and pasted the contents of the file on a post in page one in anticipation of the request.

---

### Post by Monicker on 2008-05-13
The contents of the file you posted looks to be an MS Word xml document.  Are you sure the sender is converting them to pdf properly?


EDIT: I just sent myself a pdf file from Yahoo to my gmail account and it arrived in the proper format.

---

