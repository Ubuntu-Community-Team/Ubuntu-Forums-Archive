---
title: "Replace link with JavaScript"
date: 2009-06-18
forum: Programming Talk
---

### Post by .Maleficus. on 2009-06-18
I installed Greasemonkey a few days ago so I figured I'd try out JavaScript.  What I can't seem to figure out is a way to replace the text after 'href=' to something else.  Here's what I'm doing so far.

[php]var thumbs = new Array(20);
for (i = 0; i < 21; i++) {
	thumbs[i] = document.getElementById('tDataImage' + i);
	// Replace the 'href' in thumbs[i]
}[/php]
If I'm going about this all wrong, I'm on day one of JavaScript so don't yell too loud :).

Thanks.

---

### Post by Tibuda on 2009-06-18
```
[thumbs[i].href = 'http://link/to/somewhere/';]("http://www.w3schools.com/htmldom/prop_anchor_href.asp")
```

---

### Post by Mirge on 2009-06-18
If you need to do a bit heavier lifting, I'd recommend the jQuery library in a hurry. [http://www.jquery.com/](http://www.jquery.com/). It'll change the way you think about Javascript :).

---

### Post by .Maleficus. on 2009-06-18
> **Mirge said:**
> If you need to do a bit heavier lifting, I'd recommend the jQuery library in a hurry. [http://www.jquery.com/](http://www.jquery.com/). It'll change the way you think about Javascript :).
I'm sure I'll use it in the future, but I'd like to get my head wrapped around the simple things first :D.

@danielrmt - Sorry, that didn't work for me.  I get the same link as before.  It's my fault though - the link I'm trying to edit is actually a child of tDataImage.  I just replaced it with 'thumbs[i].lastChild.href = 'http://www.google.com' and it worked fine.  Thanks guys!  Now all I need to do is figure out how to dynamically change the link with regex...

---

### Post by Tibuda on 2009-06-18
> **.Maleficus. said:**
> @danielrmt - Sorry, that didn't work for me.  I get the same link as before.  It's my fault though - the link I'm trying to edit is actually a child of tDataImage.  I just replaced it with 'thumbs[i].lastChild.href = 'http://www.google.com' and it worked fine.  Thanks guys!  Now all I need to do is figure out how to dynamically change the link with regex...

I thought tDataImage1, tDataImage2... were the <a> tags.

I also recommend jQuery. If you work with CSS, it will be easy to learn.

---

### Post by .Maleficus. on 2009-06-18
> **danielrmt said:**
> I thought tDataImage1, tDataImage2... were the <a> tags.

I also recommend jQuery. If you work with CSS, it will be easy to learn.
I did too until I inspected a little further with Firebug.  Which is probably why my first attempts didn't work :rolleyes:.  While I reply to this, I have another question, regarding regex and replacing.

The point of the script I'm writing is to bypass the "middle" page of Google Images (so after clicking the thumbnail it takes me directly to the full view).  The original link on the thumbnail always starts with '/imgres?imgurl=' and then the actual link.  After the link to the full picture, the next part starts with '&imgrefurl'.  What I want to do is delete the first '/imgres...' part and then everything after '&imgrefurl', effectively leaving me with only the link to the full view.  Unfortunately, I have no idea how to do this.  To simplify things a little, I made a RegExp object with like this.
[php]var regex = new RegExp('/imgres?imgurl=');[/php]
And tried to use it like this.
[php]thumbs[i].lastChild.href.replace(regex, '');[/php]
But it didn't work.  Am I even on the right track?

---

### Post by Mirge on 2009-06-18
Post a full URL with imgres in it, so I can see specifically what you're doing please :).

---

### Post by .Maleficus. on 2009-06-18
[http://images.google.com/imgres?imgurl=http://hisham.cc/files/2007.07.05.gvim.png&imgrefurl=http://www.hisham.cc/articles/2007/07/05/gvim-hurray&usg=__DP34QvZLTz9UNVVIoZ4jzW9tfLU=&h=916&w=852&sz=183&hl=en&start=1&um=1&tbnid=Yts6ufDOMbeYGM:&tbnh=147&tbnw=137&prev=/images%3Fq%3Dgvim%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN%26um%3D1](http://images.google.com/imgres?imgurl=http://hisham.cc/files/2007.07.05.gvim.png&imgrefurl=http://www.hisham.cc/articles/2007/07/05/gvim-hurray&usg=__DP34QvZLTz9UNVVIoZ4jzW9tfLU=&h=916&w=852&sz=183&hl=en&start=1&um=1&tbnid=Yts6ufDOMbeYGM:&tbnh=147&tbnw=137&prev=/images%3Fq%3Dgvim%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN%26um%3D1)

Basically any page after you click the thumbnail of a Google image.  I starting thinking that I was going about it wrong and should instead be searching for 'http...' and then the ending '.jp(e)g/png/bmp/etc' but again, not knowing JS or regex makes this difficult :).

---

### Post by Mirge on 2009-06-18
```

<html>
<head>
<title>Testing JS Regex</title>
<script type="text/javascript">
function Loaded() {
    var url = document.links[0].href;
    alert("Link: " + url);

    var regex = new RegExp(".+?imgurl=(.+)");
    var m = regex.exec(url);
    alert(m[1]);
}
</script>
</head>
<body onload="Loaded();">
This is the only link on the page, so it'll be document.links[0].href to access the URL.
<a href="http://images.google.com/imgres?imgurl=http://hisham.cc/files/2007.07.05.gvim.png&imgrefurl=http://www.hisham.cc/articles/2007/07/05/gvim-hurray&usg=__DP34QvZLTz9UNVVIoZ4jzW9tfLU=&h=916&w=852&sz=183&hl=en&start=1&um=1&tbnid=Yts6ufDOMbeYGM:&tbnh=147&tbnw=137&prev=/images%3Fq%3Dgvim%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:eek:fficial%26sa%3DN%26um%3D1" id="image_url">View Image</a>
</body>
</html>

```

Just something I threw together quick. It's simple enough that it somewhat explains itself though.

I create a regular <a href=...> link to an image, using the exact example you posted.

Then I extract that link with document.links[0].href because it's the only link... it was easy.

Then I create a RegExp object, execute it.. storing the matches in the "m" array. m[1] contained the bit that I wanted.. m[0] being the entire URL.

Hope this helps.

---

### Post by Can+~ on 2009-06-18
> **.Maleficus. said:**
> [http://images.google.com/imgres?imgurl=http://hisham.cc/files/2007.07.05.gvim.png&imgrefurl=http://www.hisham.cc/articles/2007/07/05/gvim-hurray&usg=__DP34QvZLTz9UNVVIoZ4jzW9tfLU=&h=916&w=852&sz=183&hl=en&start=1&um=1&tbnid=Yts6ufDOMbeYGM:&tbnh=147&tbnw=137&prev=/images%3Fq%3Dgvim%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN%26um%3D1](http://images.google.com/imgres?imgurl=http://hisham.cc/files/2007.07.05.gvim.png&imgrefurl=http://www.hisham.cc/articles/2007/07/05/gvim-hurray&usg=__DP34QvZLTz9UNVVIoZ4jzW9tfLU=&h=916&w=852&sz=183&hl=en&start=1&um=1&tbnid=Yts6ufDOMbeYGM:&tbnh=147&tbnw=137&prev=/images%3Fq%3Dgvim%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN%26um%3D1)

> Animal porn horse porn dog porn zoo porn. From Bestiality porn zoo sex private photo and movies.
      Zoo porn. Animal porn dog porn horse porn zoo porn.

:-s

---

### Post by Mirge on 2009-06-18
Hahahahaha WOW I didn't even notice... that's just wrong..

---

### Post by .Maleficus. on 2009-06-19
...Oh wow.

Anyways...

Thanks for the code Mirge.  I'm trying to adapt it to my script, which I still can't get working :D.  This is my current code, I'll explain what I'm trying to accomplish.

[php]var thumbs = new Array(20);
var regex = [".+?imgurl=(.+)", "\&imgrefurl=.+?"]  //[1]
for (i = 0; i < 21; i++) {
	thumbs[i] = document.getElementById('tDataImage' + i);
	link = thumbs[i].lastChild.href  //[2]
	for (j = 0; j < regex.length; j++) {
		var k = new RegExp(regex[j]);  //[3]
		var newLink = k.exec(link);  //[4]
		thumbs[i].lastChild.href = newLink;  //[5]
	}
}[/php]
[1]  Not only do I need the first part gone (the code you gave me), but I also need everything after the URL, ie, the '&imgrefurl...' part, so I made an array of both regex's.  From what I gather of regex, I need to escape the &, and then after that I _think_ I have the literal 'imgrefurl=', unless I need to escape that too.  Because your code matched everything before 'imgurl=' with '.+', I added that to the end in hopes of it matching everything after 'imgrefurl='.

[2]  Pretty simple, I made a variable with the old link so I could manipulate it later.

[3]  Made a RegExp object with the first string of my array so I can execute that in line [4].  Repeat in 'for' loop with the second string from my array.

[5]  Replace 'link' with the regex I just executed.

After all of this is done, I am left with a link pointing to 'http://images.google.com/&imgrefurl=h'.  I guess it's keeping the URL I'm trying to get rid of.

Thanks again for all your help so far.

---

### Post by Mirge on 2009-06-19
Take my code, save it as test.html or something...and open it in your browser.

Pay specific attention to the array element alert()'d ... **alert(m[1])**

---

### Post by .Maleficus. on 2009-06-19
> **Mirge said:**
> Take my code, save it as test.html or something...and open it in your browser.

Pay specific attention to the array element alert()'d ... **alert(m[1])**
After posting I realized that that was the part I was ignoring and it was the key :D.

---

### Post by Mirge on 2009-06-19
;)

---

### Post by .Maleficus. on 2009-06-19
Well, I got it to work.  I'm sure it could be improved but for now I'm happy.  Here's the final code (for now).
[php]// ==UserScript==
// @name			GoogleImageFull
// @author			.Maleficus.	
// @description			Bypass Google's middle page in Google Images
// @include			http://images.google.com/images*q=*
// ==/UserScript==

var thumbs = new Array(20);
var regex = [".+?imgurl=(.+)", "(.+)\&imgrefurl=?"]
var newLink;
for (i = 0; i < 21; i++) {
	thumbs[i] = document.getElementById('tDataImage' + i);
	link = thumbs[i].lastChild.href
	for (j = 0; j < regex.length; j++) {
		var k = new RegExp(regex[j]);
		newLink = k.exec(link);
		if (j == 0) {
			link = newLink[1];
		}
	}
	thumbs[i].lastChild.href = newLink[1];
}[/php]

---

### Post by Mirge on 2009-06-19
Glad you got it all working :).

---

### Post by .Maleficus. on 2009-06-19
> **Mirge said:**
> Glad you got it all working :).
Thanks again for all the help.  I'll probably revise it so that the number of tDataImages is dynamic, rather than me assuming there will be 20 thumbnails, but for my purposes it works great.

---

