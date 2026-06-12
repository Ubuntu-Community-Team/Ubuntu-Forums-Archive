---
title: "[SOLVED] Offline Browsers."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-04
Is there any offline browsers available for ubuntu to mirror a website to view it offline.

---

### Post by kellemes on 2008-06-04
> **rraj.be said:**
> Is there any offline browsers available for ubuntu to mirror a website to view it offline.

You can use FireFox and check "Work Offline" in the file-menu.
Or isn't this what you mean?

---

### Post by rraj.be on 2008-06-04
No i just want download a set of entire website to my harddisk so that i can have all the links connected properly.

so that even if i am not having internet connection i can brows that website as i if am having internet connection.

---

### Post by jeffus_il on 2008-06-04
wget used recursively should download a whole site to disk them you can open it using any browser.
```
wget -r http://url_of_website/
```

Also see ```
man wget
```

---

### Post by rraj.be on 2008-06-04
wget will just download all pages.

But i wont get any active page effects.

when i click a link in that it will take me to the website alone and not to the page that i have already downloaded to  my computers local hard dive

---

### Post by jeffus_il on 2008-06-04
Right, I don't know of a solution.
Either the links in the pages must be relative, or you need a utility which will run through all and update them, or there should be some form or redirection to a file when the browser is presented with the address of the site you have downloaded. For the last, support should be built into the browser or implemented by a plugin.

---

### Post by rraj.be on 2008-06-04
In windows there is a appliction called offline browser itself.

is something like that there in ubuntu

---

### Post by Archmage on 2008-06-04
I honestly don't get your point.

If you have all pages already downloaded and set up corretly, than you can browse offline with EVERY browser at this webpage. The browser will simply use the links to your offline-pages.

I you haven't download them correctly and they pages are still linking to the internet, than this is the problem and you need to change this. (E.g. using the correct parameter of wget.)

---

### Post by jeffus_il on 2008-06-04
These guys have a linux version:
[http://www.httrack.com/](http://www.httrack.com/)
Post if it's any good!

---

### Post by jeffus_il on 2008-06-04
Oh! it's in the repository, no need to download from the site, there are others as well in the repo if you search for "offline browser" in synaptic.
You need to have universe checked in repositories.
This is the method it implements:
> HTTrack arranges the original site's relative  link-structure. Simply open a page of the "mirrored" website in your browser, and you can browse the site  from link to link, as if you were viewing it online.

---

### Post by rraj.be on 2008-06-04
yes.

its very usefull.

i had found it in synaptic P-M.

along with there is also 

```
webhttrack

wwwofle.
```

---

### Post by jeffus_il on 2008-06-04
> **Archmage said:**
> I honestly don't get your point.

If you have all pages already downloaded and set up corretly, than you can browse offline with EVERY browser at this webpage. The browser will simply use the links to your offline-pages.

I you haven't download them correctly and they pages are still linking to the internet, than this is the problem and you need to change this. (E.g. using the correct parameter of wget.)

Here:
       > Wget can follow links in HTML and XHTML pages and create local versions of remote web sites, fully recreating the directory structure of the orig&#8208;
       inal site.  This is sometimes referred to as &#8216;&#8216;recursive downloading.&#8217;&#8217;  While doing that, Wget respects the Robot Exclusion Standard
       (/robots.txt).  Wget can be instructed to convert the links in downloaded HTML files to the local files for offline viewing.
From the man page: 
> 
-k
 --convert-links
           After the download is complete, convert the links in the document to make them suitable for local viewing.  This affects not only the visible
           hyperlinks, but any part of the document that links to external content, such as embedded images, links to style sheets, hyperlinks to non-
           HTML content, etc.

           Each link will be changed in one of the two ways:

           *   The links to files that have been downloaded by Wget will be changed to refer to the file they point to as a relative link.

               Example: if the downloaded file /foo/doc.html links to /bar/img.gif, also downloaded, then the link in doc.html will be modified to point
               to ../bar/img.gif.  This kind of transformation works reliably for arbitrary combinations of directories.

           *   The links to files that have not been downloaded by Wget will be changed to include host name and absolute path of the location they point
               to.

               Example: if the downloaded file /foo/doc.html links to /bar/img.gif (or to ../bar/img.gif), then the link in doc.html will be modified to
               point to [http://hostname/bar/img.gif](http://hostname/bar/img.gif).

           Because of this, local browsing works reliably: if a linked file was downloaded, the link will refer to its local name; if it was not down&#8208;
           loaded, the link will refer to its full Internet address rather than presenting a broken link.  The fact that the former links are converted
           to relative links ensures that you can move the downloaded hierarchy to another directory.

           Note that only at the end of the download can Wget know which links have been downloaded.  Because of that, the work done by -k will be per&#8208;
           formed at the end of all the downloads.


---

