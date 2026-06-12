---
title: "Developing a Firefox Plugin"
date: 2009-07-31
forum: Programming Talk
---

### Post by Pyro.699 on 2009-07-31
Hey,

I looked around the forum and couldnt find anywhere else to place this so i hope this is the right section.

I have spent the past 2 weeks looking around for a add-on that will automatically highlight specified text (from list of words stored in a file). I need to to automatically find and highlight 'my word' on every page i load. So if i were to highlight the word **Ubuntu** ever time the word Ubuntu would appear on my screen (in the firefox window) it whould be highlighted via a yellow background (automatically). The list of words would be stored in a csv file (using \, to not count a seperation). I just have one question? How?

While i waited for posts to build on the topic i made requesting help to find the topic i went around figureing out how to make your own firefox plugins. I visted many sites that gave examples on how to "make your own plugin in under 10 minutes" but to no avail it has been 2 weeks and still, no plugin.

I am now asking you, my friends at ubuntu forums to please help me out, i have absolutely no knowledge on this topic (although i do have other programming experiances: python, php, etc..). So if you could provide anything that could get me closer to my goal, it would be greatly appreaciated.

Thankyou very much
~Cody Woolaver

---

### Post by wmcbrine on 2009-07-31
Grab some existing extensions and examine them. They tend to be pretty simple. An .xpi file is really a .zip file. Try unzipping one, modifying it, rebundling it, and installing it to see your changes in action. Once you've successfully done that, try bigger changes. Eventually you should develop an understanding of how extensions work, and be able to create a whole new one.

---

### Post by Pyro.699 on 2009-07-31
Oh, that's interesting, you just rename it? Any recommendations on which add-on i should look at first, to achieve what i wanna get done?

---

### Post by .Maleficus. on 2009-07-31
You could also try out Greasemonkey.  If you don't know what it is, Greasemonkey is an addon that allows you to write your own Javascript scripts that will run on certain (or all) pages.  I wrote a Greasemonkey script to change all of the links in Google Images to go directly to the full view and skip the middle "View full size" page.  It was pretty painless and is only ~25 lines of code (IIRC).  If you're interested in trying Greasemonkey, here's what a script looks like.
[php]// ==UserScript==
// @name			GoogleImageFull
// @author			.Maleficus.	
// @description			Bypass Google's middle page in Google Images
// @include			http://images.google.com/images*q=*
// ==/UserScript==

// Array to store the links of the thumbnails
var thumbs = new Array(20);
// Regex to match the portion of the link before the 'http://...' and after the '.jpg/png/etc'
var regex = [".+?imgurl=(.+)", "(.+)\&imgrefurl=?"]
var newLink;
for (i = 0; i < 21; i++) {
	// Fetch the original link of the thumbnail
	thumbs[i] = document.getElementById('tDataImage' + i);
	link = thumbs[i].lastChild.href;
	// Execute the regex's	
	for (j = 0; j < regex.length; j++) {
		var k = new RegExp(regex[j]);
		newLink = k.exec(link);
		// The regex is executed on the variable 'link', so 'link' needs to be changed
		// to the post-regex'd variable 'newLink' after the first pass so it can
		// successfully match the second pattern
		if (j == 0) {
			link = newLink[1];
		}
	}
	// The [1] element of the post-regex'd array is the new link, so take that link and replace
	// the old link in thumbs[]
	thumbs[i].lastChild.href = newLink[1];
}[/php]
It's actually 31 lines long and is mostly comments.  If you can write Javascript, you can do exactly what you're asking for.

---

### Post by Viva on 2009-07-31
It would be easier to create a grease monkey script that highlights a word than an extension.

EDIT: .Maleficus. explained it better

---

### Post by Pyro.699 on 2009-07-31
That sounds much easier than taking apart an XPI file. How exactly does it work? Cause i know javascript. Is it as simple as replaceall *string* with *<span style="background-color: yellow">string</span>*?

---

### Post by .Maleficus. on 2009-07-31
> **Pyro.699 said:**
> That sounds much easier than taking apart an XPI file. How exactly does it work? Cause i know javascript. Is it as simple as replaceall *string* with *<span style="background-color: yellow">string</span>*?
Greasemonkey scripts are pure Javascript.  If you know of a way to do it in JS, then yes (that script was my first experience with Javascript so I can't help a whole lot unfortunately).  The only special thing is the header of the file, which you can see in my example (the first 6 lines, all comments).  If you want to highlight a specific word on *every* page, the '@include' line would just be an asterisk, meaning any URL string.  After you have the code written, save it as 'some_name.user.js' and load it into Greasemonkey by doing File > Open File in Firefox (you need Greasemonkey installed first obviously).  It's a piece of cake really.

[Check out this site too.]("http://userscripts.org/")  It's a massive collection of user-made Greasemonkey scripts.  They have a script for everything really.

---

### Post by Viva on 2009-07-31
Try any of the profanity filter scripts on userscripts.org. You can acheive what you want with a little editing.

---

### Post by Pyro.699 on 2009-07-31
Holly crap that was easy xD

[php]
document.body.innerHTML= document.body.innerHTML.replace(/String/g, "<span style='background-color: #7FFF24; color: #000000'>String</span>");
[/php]

Thanks guys :)

---

### Post by Viva on 2009-07-31
Don't do innerHTML.replace. It will break some javascript.

---

### Post by Pyro.699 on 2009-07-31
what do you suggest as an alternative (im use to jquery rather than javascript xD)

---

