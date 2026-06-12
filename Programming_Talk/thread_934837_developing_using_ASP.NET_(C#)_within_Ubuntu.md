---
title: "developing using ASP.NET (C#) within Ubuntu"
date: 2008-10-01
forum: Programming Talk
---

### Post by ozPATT on 2008-10-01
Hello all, I was just wondering if it was possible to develop ASP.NET websites using C# on my ubuntu machine.. I currently develop using PHP and MySQL, so have my laptop set up for that, but I was just wondering how I can develop and test using C#, if it is even possible.. is it best just to get some asp.net hosting and develop using that?

---

### Post by Tatty on 2008-10-01
The linux port of .NET is called Mono.  There is a development suite in the repos called mono-develop which you can use to develop.  When it comes to testing I am not sure.

I cannot give any more info than that I am afraid as that is all I know, but here is a good place to start looking for info [https://help.ubuntu.com/community/MonoDevelopmentHowto](https://help.ubuntu.com/community/MonoDevelopmentHowto)

---

### Post by ozPATT on 2008-10-01
cool thanks, I will check it out :D

---

### Post by Sycron on 2008-10-01
How programs are developed in Ubuntu/linux ? especially gnome applications.

---

### Post by cybertechx on 2008-10-03
> **Sycron said:**
> How programs are developed in Ubuntu/linux ? especially gnome applications.

so many, but my favourite is F-Spot

Is written in C# on the Mono platform and released under the GNU GPL.

---

### Post by Joeb454 on 2008-10-03
Moved to programming talk

---

### Post by zac smith on 2013-01-09
ask for some sample c# codes to genenrate QR CODE in [[COLOR=#000000]ASP.NET web services[/COLOR]]("http://www.barcodelib.com/csharp/barcode_symbologies/qrcode.html"), please!

---

### Post by dsfweaaw on 2013-01-31
See this source code for[ generating QR Code barcodes in C#]("http://www.onbarcode.com/csharp/qr-code-generator.html"):

  using System;
   using System.Collections.Generic;
   using System.Text;
   using OnBarcode.Barcode;
   using System.Drawing.Imaging;
   using System.Drawing;


   QRCode qrcode = new QRCode();

   // Barcode data to encode
   qrcode.Data = "ONBARCODE";
   // QR-Code data mode
   qrcode.DataMode = QRCodeDataMode.AlphaNumeric;
   // QR-Code format mode
   //qrcode.Version = QRCodeVersion.V10;

   /*
   * Barcode Image Related Settings
   */
   // Unit of meature for all size related setting in the library. 
   qrcode.UOM = UnitOfMeasure.PIXEL;
   // Bar module size (X), default is 3 pixel;
   qrcode.X = 3;
   // Barcode image left, right, top, bottom margins. Defaults are 0.
   qrcode.LeftMargin = 0;
   qrcode.RightMargin = 0;
   qrcode.TopMargin = 0;
   qrcode.BottomMargin = 0;
   // Image resolution in dpi, default is 72 dpi.
   qrcode.Resolution = 72;
   // Created barcode orientation.
   //4 options are: facing left, facing right, facing bottom, and facing top
   qrcode.Rotate = Rotate.Rotate0;

   // Generate QR-Code and encode barcode to gif format
   qrcode.ImageFormat = System.Drawing.Imaging.ImageFormat.Gif;
   qrcode.drawBarcode("C:\\qrcode.gif");

   /*
   You can also call other drawing methods to generate barcodes
             
   public void drawBarcode(Graphics graphics);
    
   public void drawBarcode(string filename);
    
   public Bitmap drawBarcode();
    
   public void drawBarcode(Stream stream);
             
   */
You can also find many other code, like code for[ generating QR Code barcode in .NET]("http://www.onbarcode.com/products/net_barcode/barcodes/qrcode.html"), code for[ generating QR Code barcode in Java]("http://www.onbarcode.com/products/java_barcode/barcodes/qrcode.html"), ect.

---

### Post by snip3r8 on 2013-02-02
Is there any reason you would want to switch from php development to C#? what do you wish to gain from this switch?

---

### Post by AdjunctBlack on 2013-02-02
> **snip3r8 said:**
> Is there any reason you would want to switch from php development to C#? what do you wish to gain from this switch?

I cannot speak for the OP, but here are a few reasons why I personally prefer to develope web apps on both Windows and Linux using Mono/C#/ASP.NET MVC

1. Mono is much faster than PHP
2. I find LINQ is easier to use than direct queries to any particular SQL DB
3. C# is a much cleaner and well thought out language than PHP.  The people behind C# actually have experience with designing programming languages.


These are my current reasons....but he/she may just want to learn something new....
....or...the poster may find themselves in a situation like mine...where I prefer working with Linux...but am currently developing in a Microsoft shop..so why not learn one of the common demoninators between the two?  It is my belief that the Mono community will eventually be the stewards of the CLR anyway...MS does not seem to interested in the .NET community these days...

---

### Post by Trevelyanlee on 2013-05-20
I only use c# to develop my barcode generating dll console, and following is a short sample code of [qr code generating in c#]("http://www.rasteredge.com/how-to/csharp-imaging/barcode-generating-qrcode/"), also pdf 417, datamatrx, code 39, code 128, [upc-a]("http://www.rasteredge.com/how-to/csharp-imaging/barcode-generating-upca/"), upc-e etc are offered, share with all those free source.

---

### Post by alexalexabc on 2013-09-26
> **Tatty said:**
> The linux port of .NET is called Mono.  There is a development suite in the repos called mono-develop which you can use to develop.  When it comes to testing I am not sure.

I cannot give any more info than that I am afraid as that is all I know, but here is a good place to start looking for info [https://help.ubuntu.com/community/MonoDevelopmentHowto](https://help.ubuntu.com/community/MonoDevelopmentHowto)
hello, if so, can this [[COLOR=#000000]ASP.NET[/COLOR]]("http://www.keepautomation.com/how_to/aspnet/") websites using [[COLOR=#000000]C#[/COLOR]]("http://www.keepautomation.com/how_to/csharp/") on ubuntu  machine?

---

### Post by leona2 on 2014-05-26
what am i using now is this [[COLOR=#000000]c# barcode guide [/COLOR]]("http://www.keepautomation.com/guide/csharp_barcode_generator.html")

---

### Post by cathyhill on 2014-06-03
> **leona2 said:**
> what am i using now is this [[COLOR=#000000]c# barcode creating guide [/COLOR]]("http://www.keepdynamic.com/csharp-barcode-generator/qr-code.shtml")

I thought this thread has been hijacked by the barcode creating issues.:guitar:

---

