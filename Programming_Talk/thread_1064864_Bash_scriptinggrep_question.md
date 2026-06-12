---
title: "Bash scripting/grep question"
date: 2009-02-09
forum: Programming Talk
---

### Post by Nerdriot on 2009-02-09
I'm trying to pull an entire paragraph from a file, rather than just one line, but so far, I've been unable to accomplish it.

The file I'm trying to filter through is a massive html file containing several archived pages. So, essentially what I'm trying to accomplish is to use grep to find certain sections of the html, and output it to other places. Here's exactly what I'm trying to get grep to pull:

```
<p><span class="shw">Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
```

However, when I grep it, (ex: cat file | grep 'Description:'), it only shows me the single line, and multiple instances of it, since there are multiple instances of it in the file.

So my question is, does anyone know of a way where I could grep the entire paragraph?

Thanks in advance :)

---

### Post by ghostdog74 on 2009-02-09
you will need to provide more of that html page

---

### Post by Nerdriot on 2009-02-09
> **ghostdog74 said:**
> you will need to provide more of that html page

Cool, can do. Maybe just something preceding and proceeding the part that I'm trying to grep?

Here's the a whole section of the page, with a preceding and proceeding paragraph, and the thing I'm trying to grep in the middle:

```
<p><span class="shw">Contacts:</span><br/>
Webmaster: Name<br/>
Media: Name<br/>
Submissions: Name<br/>

<p><span class="shw">Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>

</div>  </div> <!-- closeheaderdiv -->
<div id="headerSection2">
<a name="top"></a>
<div id="Top">
<div id="ra-header">
<a rel="follow" href="/"><img border="0" alt="website.com" src="http://website.com/images/banner.gif" title="website.com" style="margin-left:5px;"/></a>
```

I hope that helps more. Sorry for being vague earlier. Been a hectic morning so far, lol..

---

### Post by geirha on 2009-02-09
```
grep -A3 '<p>.*Description' file
``` should give you those lines, but the best way to get the data you need is to use an html-parser. That's quite a bit more complicated though.

---

### Post by ghostdog74 on 2009-02-09
a little problem with grep -A3 is that you won't be able to grep anything more after that 3 lines. a slightly more viable approach is to your start and end markers hence i asked you to provide more html. In the below example, i had used starting marker with "Description" in the line, the end marker is the first </div> tag 
```

# awk '/Description/,/^<\/div>/' file
<p><span class="shw">Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>

</div>  </div> <!-- closeheaderdiv -->


```

---

### Post by michael_1234 on 2009-02-09
Too bad it's not well-formed xhtml; you could use an xpath query.  But, you do have loosely "structured" text, so, if you have the option to install tools that may not already be available,  install "sgrep".  It takes a starting pattern, and an ending pattern, and returns the content between.

Eg., given your input file (note the quotes),

```

$ sgrep '"Description:".."</div>"' foo.xml 
Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>

</div>


```g'luck,
-m

---

### Post by TreeFinger on 2009-02-10
look at all factors of the section you want to remove. if it differs greatly... 

anyways.

are # of lines always the same?


is the starting tag of each of these lines going to be the same?

and so on.

id probably look at the beginnin of each line and use re in python. i don't think there is some magical way to do this.

maybe you could get the byte count of that pattern per line and look for that?

---

### Post by Nerdriot on 2009-02-10
> **TreeFinger said:**
> look at all factors of the section you want to remove. if it differs greatly... 

anyways.

are # of lines always the same?


is the starting tag of each of these lines going to be the same?

and so on.

id probably look at the beginnin of each line and use re in python. i don't think there is some magical way to do this.

maybe you could get the byte count of that pattern per line and look for that?

The starting tags will be the same per each thing I'm trying to extract from the file, yeah. I'll try to explain what it does, without boring you to death with a lengthy post, lol...

Essentially, the script searches a specific site for whatever company type you're looking for, formats and saves the links to each search result, then uses wget -i <file> to go through each of the links, and then, it's supposed to filter out extra html, leaving just the company name, bio, and links to 3 of the company's major competitors.

The only issue I'm having is with this set, because grep was only pulling the one line, but maybe awk will do a better job, or sgrep.

I'm beginning to think that I should spend less time bash scripting everything, and learn a more powerful language instead...

---

### Post by Nerdriot on 2009-02-10
> **michael_1234 said:**
> Too bad it's not well-formed xhtml; you could use an xpath query.  But, you do have loosely "structured" text, so, if you have the option to install tools that may not already be available,  install "sgrep".  It takes a starting pattern, and an ending pattern, and returns the content between.

Eg., given your input file (note the quotes),

```

$ sgrep '"Description:".."</div>"' foo.xml 
Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>

</div>


```g'luck,
-m

This did EXACTLY what I was looking for. Thanks a ton!

---

### Post by Nerdriot on 2009-02-10
> **ghostdog74 said:**
> a little problem with grep -A3 is that you won't be able to grep anything more after that 3 lines. a slightly more viable approach is to your start and end markers hence i asked you to provide more html. In the below example, i had used starting marker with "Description" in the line, the end marker is the first </div> tag 
```

# awk '/Description/,/^<\/div>/' file
<p><span class="shw">Description:</span><br/>
<a href="/link/link.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link2.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>
<a href="/link/link3.html" class="ilnk" target="_top" onclick="assignParam('navinfo','method|4'+getLinkTextForCookie(this));">Link Description</a><br/>

</div>  </div> <!-- closeheaderdiv -->


```

And so did this! Wow, see, this is why I should put more effort into learning awk.

---

