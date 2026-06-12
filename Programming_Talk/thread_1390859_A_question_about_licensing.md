---
title: "A question about licensing"
date: 2010-01-26
forum: Programming Talk
---

### Post by MarcDam on 2010-01-26
I've written a program that uses some data from Wikipedia's pages. When i read their terms of use ([http://wikimediafoundation.org/wiki/Terms_of_Use](http://wikimediafoundation.org/wiki/Terms_of_Use)) it sounds like all i need to do is provide a link to the page where i've taken the text along with a link to the CC-BY-SA license ([http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/))... Here is a screenshot of what i've done.
[[IMG]http://i279.photobucket.com/albums/kk141/Master-Techo/th_jElementsScreenshot.png[/IMG]](http://s279.photobucket.com/albums/kk141/Master-Techo/?action=view&current=jElementsScreenshot.png) 
So what i want to know is if there is anything else i need to do to be allowed to release it or if i can release it as it is now?

I hope you can help me :)

Marc

P.S. I didn't know in what forum to post this but this sounded like the best place to do it.

---

### Post by nvteighen on 2010-01-26
> **MarcDam said:**
> I've written a program that uses some data from Wikipedia's pages. When i read their terms of use ([http://wikimediafoundation.org/wiki/Terms_of_Use](http://wikimediafoundation.org/wiki/Terms_of_Use)) it sounds like all i need to do is provide a link to the page where i've taken the text along with a link to the CC-BY-SA license ([http://creativecommons.org/licenses/by-sa/3.0/](http://creativecommons.org/licenses/by-sa/3.0/))... Here is a screenshot of what i've done.
[[IMG]http://i279.photobucket.com/albums/kk141/Master-Techo/th_jElementsScreenshot.png[/IMG]](http://s279.photobucket.com/albums/kk141/Master-Techo/?action=view&current=jElementsScreenshot.png) 
So what i want to know is if there is anything else i need to do to be allowed to release it or if i can release it as it is now?

I hope you can help me :)

Marc

P.S. I didn't know in what forum to post this but this sounded like the best place to do it.

Hm... what you really need a link to the wiki's article **revision** from where you took the data + "Contributors" as attribution.

If you happen to release this application to the public, you'll have to use the same license for your whole application... and CC-BY-SA is a disastrous license for software. So, to avoid that you better separate the data into a self-contained file and make your application just read that data from disk... using a file doesn't makes the reading application a derivative work of that read file. Then, in the copyright file, state the licenses separately.

---

### Post by MarcDam on 2010-01-26
I can't seem to find the revision page for the articles, I can only find the history page. Are they the same?
And why isn't a URL to the page good enough? According to the terms of use> Attribution: To re-distribute a text page in any form, provide credit to the authors either by including **a) a hyperlink (where possible) or URL to the page or pages you are re-using,** b) a hyperlink (where possible) or URL to an alternative, stable online copy which is freely accessible, which conforms with the license, and which provides credit to the authors in a manner equivalent to the credit given on this website, or c) a list of all authors. (Any list of authors may be filtered to exclude very small or irrelevant contributions.) This applies to text developed by the Wikimedia community. Text from external sources may attach additional attribution requirements to the work, which we will strive to indicate clearly to you. For example, a page may have a banner or other notation indicating that some or all of its content was originally published somewhere else. Where such notations are visible in the page itself, they should generally be preserved by re-users. a link to the page is good enough...

The data from Wikipedia is in a separate .class file but it's bundled within the same .jar file.

And why is CC-BY-SA a "disastrous" license for software?

---

### Post by nvteighen on 2010-01-26
> **MarcDam said:**
> I can't seem to find the revision page for the articles, I can only find the history page. Are they the same?
And why isn't a URL to the page good enough? According to the terms of use a link to the page is good enough... 

To get the revision page, go to "History" and click on the date or your wished revision.

The thing is that the page can change quickly and Wikipedia does offer a way to link to the revision permanently, so it's preciser and much helpful if someone wants to know where you got the stuff from. The actual link you're using is actually the revision's.

> 
The data from Wikipedia is in a separate .class file but it's bundled within the same .jar file.


Hm... that's beyond my legal knowledge... I don't know how a .jar would be considered for these effects. Sorry.

> 
And why is CC-BY-SA a "disastrous" license for software?


Because it's meant for creative artistic works rather than software. It leaves a lot of loopholes for different kinds of abuse, like e.g. patents or even trademarking or just by not defining what "attribution" actually is (you yourself are trapped in this issue), while the BSD tells you that attribution is to keep the copyright notices intact (same for GPL). It's usually better to use specifically designed licenses, as they have a reason to exist. CC-BY-SA is great for drawings, literature, etc. (I myself use it for that :)).

---

### Post by MarcDam on 2010-01-26
Thanks for the help :)

I can know see why CC-BY-SA is bad for software. I will look into using either BSD or GPL as a license for my code.

When linking you're saying i should link to [http://en.wikipedia.org/w/index.php?title=Hydrogen&oldid=339059726](http://en.wikipedia.org/w/index.php?title=Hydrogen&oldid=339059726) instead of [http://en.wikipedia.org/wiki/Hydrogen](http://en.wikipedia.org/wiki/Hydrogen) ?

I hope someone else can answer my question about whether a .class file inside a .jar file counts as a separate file...

---

### Post by wmcbrine on 2010-01-26
If the whole program is like that, I don't see where you even need to give Wikipedia credit. Those are just basic facts, with no creative content. Any source would give the same figures. They're part of nature, not copyrightable subject matter.

---

### Post by nvteighen on 2010-01-27
> **wmcbrine said:**
> If the whole program is like that, I don't see where you even need to give Wikipedia credit. Those are just basic facts, with no creative content. Any source would give the same figures. They're part of nature, not copyrightable subject matter.

You're right! I thought the program included parts of the encyclopedia article, but after looking again to the screenshot, I see there's only data. 

For the record, a little explanation on why there's no need on dealing with copyright here:

Copyright doesn't apply to the content (patents do), but to the form of expressing some content. To be allowed to copy text from Wikipedia, you need a copyright license, no matter how creative or not it is to just present some data. Of course, that just retrieving the data (the content) isn't liable under copyright law...

For example, if Wikipedia tells you that the Hydrogen's atomic number is 1, and you present that information in your application, you don't need a license to do it. But, if you copy the Wikipedia's table and present the table in exactly the same way or very close to it, you need permission because you're taking the form of how the content was expressed.

I recall someone telling me: "Two authors can write the exactly same ideas in two different books and no copyright be violated if both used different words". That roughly shows the idea behind copyright.

So, forget about this... Though an informal "thank you" word to Wikipedia won't hurt ;)

---

### Post by MarcDam on 2010-01-27
I think I'll keep the link to the Wikipedia pages just in case, but i see your point.

Thank you for all your help :)

---

