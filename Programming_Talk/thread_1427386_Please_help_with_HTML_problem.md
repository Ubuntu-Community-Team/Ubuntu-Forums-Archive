---
title: "Please help with HTML problem"
date: 2010-03-11
forum: Programming Talk
---

### Post by jasperyate on 2010-03-11
never done html before. having a problem with this html code, the little pics get cut off at the bottom, but only in the context of the rest of the code. also the title="..." stuff shows up when you scroll over it in an emulator, but when i send it (its an email template) to my email it just gives the adress...

```
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
          <base href="https://www.knockemdead.com/" />
  <meta http-equiv="content-type" content="text/html; charset=utf-8" />
  <meta name="robots" content="index, follow" />
  <meta name="keywords" content="knock em dead, yate, martin yate, Martin Yate, knock, em dead, Knock em Dead, knock 'em dead, knockemdead, Knock'Em Dead, knockemdead.com, Resumes, resume, job search, Job Search Advice, Resume Writing Services, FREE Resume Advice, resume advice, resume writing advice, free resume samples, free sample resumes, free resume sample, free sample resume, free, sample, resume, free resume, free sample resume, resume samples, resume advice, how to write resume, resume articles, resume tips" />
  <meta name="title" content="404 - KnockemDead" />
  <meta name="author" content="Administrator" />
  <meta name="description" content="You need a resume and you need it NOW. Outperform the competition with a target-job-focused resume that maximizes your hit ratio in the resume databases, resonates with human eyes and gets results." />

        
<link rel="shortcut icon" href="/templates/rt_chromatophore_j15/images/favicon.ico" />
<link href="/templates/rt_chromatophore_j15/css/rokmoomenu.css" rel="stylesheet" type="text/css" />
<link href="/templates/rt_chromatophore_j15/css/template_css.css" rel="stylesheet" type="text/css" />

<link href="/templates/rt_chromatophore_j15/css/template_colors.php?theme=%2C%23263248%2C%23d1d4de%2C%2395ad2a%2C%23ffffff%2C%236e7791%2C%23e1e3f0" rel="stylesheet" type="text/css" />
<link href="/templates/rt_chromatophore_j15/css/colorchooser.css" rel="stylesheet" type="text/css" />
<link href="/templates/rt_chromatophore_j15/css/mooRainbow.css" rel="stylesheet" type="text/css" />
<link href="/templates/rt_chromatophore_j15/rokzoom/rokzoom.css" rel="stylesheet" type="text/css" />
<style type="text/css">
    div.wrapper { margin: 0 auto; width: 780px;padding:0;}
    td.leftcol { width:156px;padding:0;}
    td.rightcol { width:0px;padding:0;}
</style>    
<script type="text/javascript">
    window.templatePath = '/templates/rt_chromatophore_j15';
    window.currentTheme = 'Blueberry Lime:,#263248,#d1d4de,#95ad2a,#ffffff,#6e7791,#e1e3f0';
</script>
<script type="text/javascript" src="/templates/rt_chromatophore_j15/rokzoom/rokzoom.js"></script>
<script type="text/javascript" src="/templates/rt_chromatophore_j15/js/rokmoomenu.js"></script>
<script type="text/javascript" src="/templates/rt_chromatophore_j15/js/mootools.bgiframe.js"></script>
<script type="text/javascript">

</script>
<script language="JavaScript" src="https://seal.networksolutions.com/siteseal/javascript/siteseal.js" type="text/javascript"></script>
    </head>
    <body id="ff-helvetica" class="f-default  latch">
   
        <div id="page-bg">

            <!--begin main wrapper-->
            <div id="mainbody" class="wrapper">
                <!--begin header-->

                <div id="header">
                    
                                    </div>
                <!--end header-->
                <div id="main-shadow">
                    <div id="main-shadow2">
                        <div class="side-shadow1">
                            <div class="side-shadow2">
                                <div id="iefix">
                                    <div id="horiz-menu" class="moomenu">

            
<BR>&nbsp;<BR>
<BR>&nbsp;<BR>

<OpenTracking/>
<!--  Do NOT delete previous line if you want to get statistics on the number of opened emails -->


<CustomBlock name="letter.intro" title="Personalization">
    <Greeting/>
</CustomBlock>

<BR>&nbsp;<BR>

This is a test of the Constant Contact Email service. I think it's pretty damn good that I got this far with the html because I've never used it before. It's not the most attractive email interface, but it's something and it has all the website links built into the header.

<BR>&nbsp;<BR>

Sincerely,

Martin Yate

<BR>&nbsp;<BR>

<A HREF="http://twitter.com/martinyate">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/3.png" title="Follow Martin on Twitter">
</A>

<A HREF="http://www.facebook.com/profile.php?id=643029190">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/4.png" title="Visit Martin on Facebook">
</A>

<BR>&nbsp;<BR>


</body>

<BR>&nbsp;<BR>

</html>
```

any help would be greatly appreciated

---

### Post by gordintoronto on 2010-03-11
"the little pics get cut off at the bottom, but only in the context of the rest of the code."

I can't figure out what this means. It is quite probable that the flaw is in one of the stylesheets, not this bit of HTML.


"also the title="..." stuff shows up when you scroll over it in an emulator, but when i send it (its an email template) to my email it just gives the adress.."

Emulator?  Send it? Send what?

You have a huge number of style sheets, I think you need to start out with something a lot simpler, maybe work through the tutorials at w3.org.

---

### Post by era86 on 2010-03-11
You need to break up that code a bit, you can't expect us to know the context it's in by dumping it into a single code block.

Like godintoronto said, if images are getting cutoff, you may have an absolute height set in a stylesheet somewhere and the images are in a div that is floating past the end.  This sounds like a stylesheet problem.

You might also have a tag not ended somewhere.

Honestly, the possibilties are endless.  Help us help you by being a bit more specific. :)

---

### Post by jasperyate on 2010-03-11
thanks guys. and sorry, i don't know the first thing about html so i don't know what's relevant or how to present it. i'll do some more fooling around with it to see if i can isolate the code and get some more info but it sounds like its a bit beyond me.

---

### Post by MrCanzine on 2010-03-11
Your issue is with an anchor <a> tag css style, it's causing your images to be a specific height.  Add ```
style="height:32px"
``` just after the <A in the following:

<A HREF="http://twitter.com/martinyate">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/3.png" title="Follow Martin on Twitter">
</A>

<A HREF="http://www.facebook.com/profile.php?id=643029190">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/4.png" title="Visit Martin on Facebook">
</A>

Making them:
<A style="height:32px" HREF="http://twitter.com/martinyate">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/3.png" title="Follow Martin on Twitter">
</A>

<A style="height:32px" HREF="http://www.facebook.com/profile.php?id=643029190">
<img src="http://origin.ih.constantcontact.com/fs052/1102328924224/img/4.png" title="Visit Martin on Facebook">
</A>

---

### Post by jasperyate on 2010-03-12
turns out the picture cropping was a result of style sheets (whatever those are) that were not of my own making and so they cut off the images for some reason. 

I ended up scrapping that code and writing the whole thing myself, which has turned out pretty well so far, the images are full and properly spaced, but I'm having the same problem with the hover over text:

i take it that the command 

```
<title="text">
```is meant to display a message when you hover over a link-like the pictures that i linked to- because that's what it does when I open up the html in a web page.

but this is a template for an email newsletter format, and when i send it to myself to test how it appears in email clients, I get a gibberish looking url in the hover-over text. the links in the images wotk properly though.

so i'd like the proper text to appear when I hover over the images. this is the form of the code I'm using now for the picture/links:

```
<A HREF="url"><img src="image link" title="text"></A>
```

EDIT: Thanks for the help everyone

---

### Post by era86 on 2010-03-12
I think you are referring to the alt text of the image right?  No actual popup on mouseover.  If so, you can specify in the image tag the following:

```

<img src="/path/to/image" alt="text to appear on hover" />

```

---

### Post by jasperyate on 2010-03-12
The ALT= doesn't work either. The title= seemed to have worked; when i plug in the whole code into textedit and save it as html, then open it with firefox, it displays correctly, and when i hover over the images the text i want does appear (this is using title="text"). 

but when i send the same exact html in an email, the hover over text doesn't work. is it just something about html with emails?

---

### Post by era86 on 2010-03-12
> **jasperyate said:**
> The ALT= doesn't work either. The title= seemed to have worked; when i plug in the whole code into textedit and save it as html, then open it with firefox, it displays correctly, and when i hover over the images the text i want does appear (this is using title="text"). 

but when i send the same exact html in an email, the hover over text doesn't work. is it just something about html with emails?

Eh.. I'm not surprised.  Might be a browser issue?  Which browser are you using?  Check out this thread: [http://www.webmasterworld.com/forum21/3585.htm](http://www.webmasterworld.com/forum21/3585.htm)

---

