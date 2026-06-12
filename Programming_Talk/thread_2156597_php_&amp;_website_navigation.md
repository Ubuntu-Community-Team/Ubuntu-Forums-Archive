---
title: "php &amp; website navigation"
date: 2013-06-22
forum: Programming Talk
---

### Post by conradin on 2013-06-22
Hello All, 
I am a Chemist, and researcher. I have a website :[http://icn2.umeche.maine.edu/faculty/rasaiah/homepage.html](http://icn2.umeche.maine.edu/faculty/rasaiah/homepage.html)
I want to show my top 10 research papers on "web of science" via a link on my site, but the web of science is a peroxided web service. URLs do not redirect to the correct location, and persons outside of the University, or some place scribed to Web of Science, cannot access the page I would like to show off. 

Ah, so i thought I would know what to do: Use php, and use a code block like this:
```

<?php
// Download the target file
#$target = "http://www.google.com";
$target = "http://libraries.maine.edu/auth/auth.asp?db=Web+of+Science";
#$target = "http://apps.webofknowledge.com.prxy4.ursus.maine.edu/CitationReport.do?product=WOS&search_mode=CitationReport&SID=2BpAL2bObcKIgNP1F4D&page=1&cr_pqid=1&viewType=summary";

$downloaded_page_array = file($target);

// Echo contents of file
for($xx=0; $xx<count($downloaded_page_array); $xx++)
    echo $downloaded_page_array[$xx];
?>

```

This works fine, for the target site, which gets the validation cookie from the server, provided you can pass the validation process. Google, also works fine if you were to uncomment and try it.
what doesnt work so well, is the rather long url. 

My plan is to let my server on campus, load the proxied web page, and get validated. Then display the desired webpage on my site once the server is validated.
Un fortunately, the URL [http://apps.webofknowledge.com.prxy4.ursus.maine.edu/CitationReport.do?product=WOS&search_mode=CitationReport&SID=2BpAL2bObcKIgNP1F4D&page=1&cr_pqid=1&viewType=summary](http://apps.webofknowledge.com.prxy4.ursus.maine.edu/CitationReport.do?product=WOS&search_mode=CitationReport&SID=2BpAL2bObcKIgNP1F4D&page=1&cr_pqid=1&viewType=summary)

redirects to a search, rather than an actual web page. what I need is:
1. Goto [http://libraries.maine.edu/auth/auth.asp?db=Web+of+Science](http://libraries.maine.edu/auth/auth.asp?db=Web+of+Science)  so my server can get validated.
2. redirect to the long URL (which will be like doing the search)
3. click the search button : :[http://images.webofknowledge.com.prxy4.ursus.maine.edu/WOKRS510B3_1/images/search.gif](http://images.webofknowledge.com.prxy4.ursus.maine.edu/WOKRS510B3_1/images/search.gif)
4. Get the citation report: which has this format "Create<SP>Citation<SP>Report" (as a regex example, I also want to click this link)

I can do 1 and 2 no problem, but i need some help on the clicking of buttons with php.
can anyone see a problem with my reasoning? Can some one give me a code example to help me get this done?

---

### Post by Gav_UK on 2013-06-22
I can't view the actual search page, but I'm guessing it's got a form with an action.

Can't you get the form action and field names from the page source, and then pass those variables straight to the action script as a query string, so you're dealing with the organ grinder rather than the monkey?

---

### Post by conradin on 2013-06-22
> **Gav_UK said:**
> I can't view the actual search page, but I'm guessing it's got a form with an action.

Can't you get the form action and field names from the page source, and then pass those variables straight to the action script as a query string, so you're dealing with the organ grinder rather than the monkey?

I have no idea what youre saying. 
But, I included an example that will work as the target. I have access to all the info that I believe is needed, what I am uncertain about is methodology, and what functions can perform this task.

---

### Post by Gav_UK on 2013-06-22
I may not have understood exactly what you require, but I read it to say you want to retrieve search results from the link you posted (which redirected me to here[ http://umainesystem.summon.serialssolutions.com/search]("http://ubuntuforums.org/view-source:http://umainesystem.summon.serialssolutions.com/search")). If that is the case you can simply add ?s.q=whatever to the end of the URL (e.g. [http://umainesystem.summon.serialssolutions.com/search?s.q=test](http://umainesystem.summon.serialssolutions.com/search?s.q=test))

---

### Post by SeijiSensei on 2013-06-22
The general solution for these problems is to use [session cookies]("http://www.php.net/manual/en/book.session.php").  Add code to your site that places a cookie in the user's browser, then store the required authentication codes in the $_SESSION array.  When your search form POSTs to the server, you would consult the session array, pull the authentication codes, and issue the appropriate request in the background.

Your search form would look something like this:

```

<form action='some URL' method='post'>
<input type='hidden' name='<?php echo session_name()?>' value='<?php echo session_id()?>'>

[the form itself]

<input type='submit' value='Search'>
</form>


```

You could avoid cookies and include the authentication information in the form itself as a hidden field, but that is pretty insecure.  Anyone using View Source could see the information.

---

### Post by conradin on 2013-06-24
I'll think more about what you have said SejiSan.
So i should host the form, filled out, my self, then automate the submission? That is what you're saying?

---

### Post by SeijiSensei on 2013-06-24
I thought that was what you were asking, that you wanted to create a web page that could be used to perform the search, get the relevant article from Web of Science, then display the result to the person making the search.

Rereading your original post, I understand now you want to have URLs that will retrieve the papers from Web of Science.  Session cookies are a solution for that method as well.  We could go further down this road, but I'm not sure that it's the correct approach.

Frankly I think it would be much simpler for you to download copies of all the papers you want to distribute and put them on your own site.  Unless you had to transfer copyright in the papers to Web of Science, this seems far simpler than a convoluted web application.  I'm also not sure that UofM would be comfortable with the approach you propose since it might violate the University's license.  Presumably you would be providing unauthorized access to a service provided under license. We'd also be skirting around the edges of the Forum's [provisions]("http://ubuntuforums.org/misc.php?do=showrules") on circumventing terms of service and equivalent legal restrictions.

If they are your papers, and you own the copyrights, then just put the papers themselves on your site.

---

