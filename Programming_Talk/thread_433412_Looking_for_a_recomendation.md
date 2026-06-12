---
title: "Looking for a recomendation"
date: 2007-05-04
forum: Programming Talk
---

### Post by ewtesterman@cox.net on 2007-05-04
I am trying to build an Ajax site, (updating my programming professors page-last update was 96 lol) so far it is working pretty well. I have two issues I need to over come, but I think they are related. 
1. I need to be able to make a call to load the initial content on the index page without using onLoad (it seems to render my other scripts useless)
2. when I update a div I would like to be able to update the nav bars as well (can I call more than one function in an href) 
I have found some info on google, but nor really what I was looking for. 

Basically I am trying to find away to automatically run these scripts when needed and I do not see how I can tie them to an event. Please don't beat me up all I have done before is C++, php, and assembly. In all of these running what I want when I want has never been an issue. Here is my index. page
```

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd"> 
<html> 
    <head> 
        <title>Dr. Stockwell's Computer Science Home Page - Spring 2007</title> 
        <meta http-equiv="content-type" content="text/html; charset=iso-8859-1"> 
        <meta name="generator" content="Bluefish 1.0.7"> 
        <link rel="stylesheet" type="text/css" href="NiftyLayout.css" media="screen"> 
        <script type="text/javascript" src="niftycube.js"></script> 
        <script type="text/javascript" src="niftyLayout.js"></script> 
        <script type="text/javascript" src="js/ajax-dynamic-content.js"></script> 
      <script type="text/javascript" src="js/ajax.js"></script>
      <script type="text/javascript" src="js/events.js"></script> 
  </head> 
    <body> 
        <div id="header"> 
            <h1>Dr. Stockwell's Computer Science Home Page</h1> 
            <div id="menu"> 
                <ul id="nav"> 
                    <li id="home" class="activelink"> 
                        <a href="javascript:ajax_loadContent('content','home.html');">Home</a></li> 
                    <li id="who"> 
                        <a href="javascript:ajax_loadContent('content','class.html');">Classes</a></li> 
                    <li id="prod"> 
                        <a href="javascript:ajax_loadContent('content','downloads.html');">Donwloads</a></li> 
                    <li id="serv"> 
                        <a href="javascript:ajax_loadContent('content','grade.html');">Grading Policy</a></li> 
                    <li id="cont"> 
                        <a href="javascript:ajax_loadContent('content','contact.html');">Contact Me</a></li> 
                </ul> 
            </div> 
        </div> 
        <div id="container"> 
            <div id="content"> 
                <div class="comments">
                </div> 
                </div> 
            <div id="side"> 
                <p><img border="0" src="bill3.jpg"></p> 
                <P>&nbsp;</P> 
                <P></UL2></P> 
                <P><img border="0" src="msfree.gif"></P> 
                <P>&nbsp;</P> 
            </div> 
            <div id="footer"> 
                <p><I><FONT size="2"><A name="DISCLAIMER">DISCLAIMER:</A> The University of Central  
                            Oklahoma recognizes the value and potential of intellectual publishing on the  
                            Internet, and so allows and encourages students, staff, and faculty to  
                            experiment with producing individual academically based WWW pages. However, the  
                            University can accept no responsibility for the contents of individual  
                            homepages, be they organization, college, or personal. The views and opinions  
                            expressed in individual pages are strictly those of the page authors, and  
                            comments on the contents of those pages should be directed to the page authors.</FONT></I></p> 
            </div> 
        </div> 
    </body> 
</html>

```

---

### Post by Blacktalon on 2007-05-11
> 1. I need to be able to make a call to load the initial content on the index page without using onLoad (it seems to render my other scripts useless)

I am kinda confused on what you are looking to do exactly, but since you said you don't want to use the onLoad, I am going to assume you are wanting it to update when clicked, and that can be done with an onClick.  That or you are wanting to do it automatically which you can refresh the page with a delay time using javascript for this, and just have it say to refresh the div name so that area is the only thing to be refreshed.

> (can I call more than one function in an href) 

Yes, I believe you can.  Again if you are using javascript can call a function inside a function, therefore you can call 2 functions with one action (but again for this you would probably want to use a onLoad to call your functions).


I hope this helped you some.

Good Luck!

---

### Post by Mirrorball on 2007-05-11
Stop right now! What will happen if someone is browsing your site with Javascript turned off? What if I want to add the downloads page to my bookmarks? This is very bad for usability and accessibility. Make it easier for yourself and use good old plain links.

---

### Post by ewtesterman@cox.net on 2007-05-11
Well I have added the ability to bookmark use back forward and all of that. I do agree that this would not usually be the best way to develop a site however this was done more so to open the eyes of our computer science department when it comes to the idea of web apps. Also I found a good method to address my original issues. I eventually realized that you can also use div to launch onload events which worked best to me so I could have things fire at different times and under different circumstances. I do appreciate your advice about usability, but again this was more so to demonstrate that a web based interface can be fast too!!. I have also added a to my scripts a redirect to those not using javascript in there browsers to the old site (until I can find a way to degrade nicely).

---

### Post by Mirrorball on 2007-05-11
OK then. If you want the page to "degrade gracefully," don't embed any Javascript in the markup. Make the site work without Javascript first and put all the Javascript in a separate file. For instance, put real content in div.content, use real links. Then change the onclick attribute of the a elements to substitute the content.

---

