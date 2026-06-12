---
title: "Trying to arrange or float HTML &quot;div&quot; blocks; please help! (Hopefully an easy fix.)"
date: 2009-12-04
forum: Programming Talk
---

### Post by newagelink on 2009-12-04
The problem I'm having can be seen with [my reading list]("http://www.danielbridges.info/pages/books.shtml") at the very top: I wish to
[LIST]
[*]float the banner on the left
[*]have the webpage "menu" links on the right
[*]have the horizontal rule underneath it all, to clearly divide the "menu bar" from the webpages that load it (via SSI, which I've been told is better than using frames that break with search engines)
[/LIST]

The page source is public; the relevant bit seems to be: [HTML]<style type="text/css">
   oops {text-decoration:line-through;}
   .sub {list-style-type:upper-roman; content:counters(li+1);}
   body {text-align:left}
   blockquote {background-color: white}
   .bib {color: green}
  </style>
</head>

<body>
 <div>
  <div style="float:left">
   <a href="http://www.realhealthcarerespectslife.com/">
    <img alt="realhealthcarerespectslife.com" src="../img/prolife/banner-KeepAbortionOut_460x81.jpg" width="460" height="81">

   </a>
  </div>
  <div>
   <ul class="nav">
    <li><a href="contact.shtml">Contact <abbr title="Information">Info.</abbr></a></li>
    <li><a href="faithexcerpts.shtml">Faith Excerpts</a></li>
    <li><a href="fortcook.shtml">Fortune Cookies</a></li>

    <li><a href="links.shtml">Links</a></li>
    <li><a href="catholicquestions.shtml">Questions Concerning Christianity</a></li>
    <li><a href="quot.shtml">Quotations</a></li>
    <li><a href="perf.shtml">Past Performances</a></li>
    <li><a href="profile.shtml">Profile</a></li>
    <li><a href="books.shtml">My Reading List</a></li>

    <li class="last"><a href="../index.shtml">Home</a></li>
   </ul>
  </div>
  <hr>
</div>
[/HTML]
I have noticed that, if the text is large enough, the horizontal rule is bumped down to divide the entire thing, as desired. But when the text is smaller, I have the problem I mentioned: the horizontal rule goes after the text but only covers half the screen, stopping beside (rather than beneath) the image.
Any help you can give me would be greatly appreciated! Thank you for your time.

---

