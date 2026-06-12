---
title: "[BASH] Detect whether Firefox bookmarks sidebar is open?"
date: 2014-04-20
forum: Programming Talk
---

### Post by rocket13 on 2014-04-20
I usually have the bookmarks sidebar open in Firefox, but I'm trying to
write a bash script that will open a certain web page with the
bookmarks sidebar always closed.  I can use xte to send a control-b,
which will close the sidebar if it's open (what I want), but will open
it if it was closed (not what I want.)  Is there a way my script can
detect whether the bookmarks sidebar is present, so it will only send
control-b if it is?  Or is there a better way to approach this?  Many
thanks in advance!

---

### Post by Vaphell on 2014-04-21
Sending url to firefox is trivial (firefox $url) but this ctrl+b thing is rather hard. I don't think firefox exposes its internal state via cli.

I think you'd have to make a screenshot of the window fragment where the fixed parts of 'bookmarks' gui appear and compare it to a known picture of the same region with something like this
[http://www.fmwconcepts.com/imagemagick/similar/index.php](http://www.fmwconcepts.com/imagemagick/similar/index.php)

---

### Post by ofnuts on 2014-04-21
> **rocket13 said:**
> I usually have the bookmarks sidebar open in Firefox, but I'm trying to
write a bash script that will open a certain web page with the
bookmarks sidebar always closed.  I can use xte to send a control-b,
which will close the sidebar if it's open (what I want), but will open
it if it was closed (not what I want.)  Is there a way my script can
detect whether the bookmarks sidebar is present, so it will only send
control-b if it is?  Or is there a better way to approach this?  Many
thanks in advance!

You can perhaps look at it the other way: write a FF add-on that will close the sidebar when the URL is on a a given site.

---

### Post by rocket13 on 2014-04-21
ofnuts wrote:

> You can perhaps look at it the other way: write a FF add-on that will
> close the sidebar when the URL is on a a given site. 

That sounds promising, but I've never done a FF add-on-- could you give
me a clue how to start?

---

### Post by ofnuts on 2014-04-21
[http://developer.mozilla.org/en/Extensions](http://developer.mozilla.org/en/Extensions)

---

### Post by rocket13 on 2014-04-23
I've been trying to figure out a way for certain web pages, when they
load in Firefox, to automatically toggle off the bookmarks sidebar if
it was present.  Forum member "ofnuts" suggested I try to write a
Firefox addon to do this, and though I don't know javascript (and have
never written a FF addon), I made some progress:

I was able to use the addon-sdk program to successfully make an addon
with this sample script, which does the first part of what I need,
i.e., acts only on certain URLs (in this example, pages from *.org
sites):

// Import the page-mod API 
var pageMod = require("sdk/page-mod"); 
// Create a page mod 
// It will run a script whenever a ".org" URL is loaded 
// The script replaces the page contents with a message 
pageMod.PageMod({ 
include: "*.org", 
contentScript: 'document.body.innerHTML = ' +
               ' "<h1>Page matches ruleset</h1>";' 
});

Then I found this page with examples of manipulating the sidebar:
"https://developer.mozilla.org/en-US/Add-ons/Code_snippets/Sidebar"

These snippets seemed to be just the thing, if I could make them work
with the pageMod script above (to toggle off the sidebar, rather than
replace the page contents with a message, as the sample script does).

But I haven't been able to make the sidebar snippets work, either with
the pageMod script, or in any other way.  If someone could point me
toward the next step, I would be hugely appreciative.  Many thanks in
advance!

---

