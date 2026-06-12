---
title: "HTML to PDF library for PHP"
date: 2012-10-25
forum: Programming Talk
---

### Post by lykwydchykyn on 2012-10-25
Howdy coders.

I need some advice on a better HTML to PDF converter for PHP.

I've got a website framework I've built where users run reports and print forms/letters from a database.  The program is designed to deliver any printables in PDF form.

Currently, I've been using [mpdf](mpdf1.com) to do this.  However, I've recently run into some frustrating limitations with the way it handles (or rather doesn't) many html tags.  On top of that, the author/maintainer recently announced that development is ended.

Now I'm trying dompdf, and it does more or less exactly what I want, except that it eats memory like a pig, and a modest report of ~100 rows times out or exceeds memory limits.  I've tried various workarounds for this, but nothing works so far.

I've investigated tcpdf, but it seems too low-level and requires me to manually lay-out the form.  I want it to take css and html and do the work for me.

Have I missed some great option, or is this what's available?  This was all I could find using Google that was (a) open source and (b) actively maintained.

---

### Post by dazman19 on 2012-10-29
i use wkhtmltopdf, i render the output to a .html file, then i call it from the command line. (install the static version from google code)

and execute it with this script

#!bin/sh
wkhtmltopdf-i386 $*

or

#!bin/sh
wkhtmltopdf-amd64 $*


dompdf is rubbish. it really is. it cant handle high colour images and its just not good.

tc and fpdf are ok but they wont do HTML nicely. and you need to make a nice wrapper class.

the only problem with wk is that it doesnt cut the pages properly. it does look good though. 

maybe make div blocks an dive into its advanced features.

WK stands for webkit, so bear that in mind when you render the html. (view it in something like safari).

---

### Post by lykwydchykyn on 2012-10-29
I've looked at it some; color images aren't an issue for my purposes, we'll be doing B&w forms.  What's critical is being able to strictly define a layout easily.  I need explicit control of page breaks, header & footer content, and margins, since they often batch-print form letters.

Can I do this with wkhtmltopdf?

---

### Post by Lars Noodén on 2012-10-29
Are your XHTML pages using print friendly or print-specific style sheets?
[http://www.w3.org/TR/CSS21/media.html#media-sheets](http://www.w3.org/TR/CSS21/media.html#media-sheets)

That will help some with the layout, though HTML was never designed to be printed (aka PDF).  It works best on the screen.

---

### Post by lykwydchykyn on 2012-10-29
> **Lars Noodén said:**
> Are your XHTML pages using print friendly or print-specific style sheets?
[http://www.w3.org/TR/CSS21/media.html#media-sheets](http://www.w3.org/TR/CSS21/media.html#media-sheets)

Yes.  Unfortunately printing directly from HTML, even with print-specific stylesheets, is complicated by browser rendering issues.

> 
That will help some with the layout, though HTML was never designed to be printed (aka PDF).  It works best on the screen.

I know that, but users want to print forms, and this is the best I can come up with from a web application.  If there's a simpler way to give them a consistently printable document across different browsers and platforms, I'm open to ideas.

---

### Post by Lars Noodén on 2012-10-29
What about having the reports generated as TeX or LaTeX and then converted to HTML and PDF?  That should give you fine control over the layout.

---

### Post by dazman19 on 2012-10-30
This seems like a cool idea TeX? LaTeX? Im gonna look into that. 

We want a way customers can customize their invoice layouts.

The only problem I have with WK is the fact that there is a lot of mucking about trying to get the line height etc sorted. You can control this with <div>'s of a fixed height, then fill them up with block elements then call a break (which you can do with WK) but your code will need to manage how many block elements of x height are loaded into a div, each div would represent a page.

I would recommend writing a class to count the height in pixels of the block elements you load into a div, once you reach a full point i would call a break and new div and continue writing there. WKHTMLTOPDF is NOT the best solution but its better than DOMPDF and HTML2PDF and it can handle massive files. I have printed 300 page statements with it, and its reasonably fast without blowing your memory limit in php.

If you have the time to write a library for FPDF or TCPDF then they might be viable options, but you wont be able to render the content to an HTML file if you choose to have an HTML and PDF output. (i think TC might have something for this but i have not looked into it).

As for extra's we put watermarks etc on the PDF at the end using PDFTK its a freaking awesome tool, once again from the command line.

---

