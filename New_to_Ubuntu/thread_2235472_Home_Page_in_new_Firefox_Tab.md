---
title: "Home Page in new Firefox Tab"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by david228 on 2014-07-21
It may be quite obvious and I have missed it, but:

When I open Firefox it goes to the page I have set in the preferences, however, when I then open a new tab it loads a page showing 9 smaller windows of websites.

How do I make Firefox New Tab default to my Home Page? I can't seem to find an obvious solution.

Thank you.

---

### Post by Dennis N on 2014-07-21
There are directions for doing that here:

[https://support.mozilla.org/en-US/kb/new-tab-page-show-hide-and-customize-top-sites](https://support.mozilla.org/en-US/kb/new-tab-page-show-hide-and-customize-top-sites)

> 
    In the Location bar, type about:config and press Enter.
        The about:config "This might void your warranty!" warning page may appear. Click I'll be careful, I promise! to continue to the about:config page. 
    Type browser.newtab.url in the search box.
    Double-click the browser.newtab.url preference and change the url from about:newtab to about:blank. Alternately, you can change it to about:home for the Firefox Google home page, or **type in your preferred home page**, for example google.com.
    Click OK and close the about:config tab. 


---

### Post by david228 on 2014-07-21
Thank you **Dennis N**. That got me most of the way. I have now set it to a blank page but I am unable to set it to where I want.

From the preferences page I originally set the home page as: file:///home/david/HomePage/HomePage.HTM by running the HTM file within the directory HomePage then telling preferrences "Use Current Page". So I am trying to load the homepage from my hard drive rather than internet.

If I copy the specific line "file:///home/david/HomePage/HomePage.HTM" from the preferrences box I get an error: 

The address isn't valid
The URL is not valid and cannot be loaded.
 Web addresses are usually written like [http://www.example.com/](http://www.example.com/)
Make sure that you're using forward slashes (i.e. /).

Perhaps there is a syntax issue in my line but I don't understand what. (Alas, I am only just starting on the road to using the CLI and have a long way to go yet in understanding CLI commands, arguments and syntax).

---

### Post by david228 on 2014-07-21
OK. Ignore my last message.

 I was looking through the whole list of Browser. options (from the instructions above) and down near the bottom was the line that loads the original home page when firfox is first run. The difference was that it did not have the word "about" in the line like "about:blank" that did work. So I copied in the line "file:///home/david/HomePage/HomePage.HTM" with nothing else and it worked.

So thank you again **Denis N**, your reply did set me off on the right path and I have now sorted out the problem.

And I am glad it was not an obvious tick box I missed.

---

### Post by Bucky Ball on 2014-07-21
Easy. Install the add-on New Tab Hompage, unless that is the add-on you're already talking about. ;)

Just go to Firefox add-ons and do a search for it, then install. Your new tabs will then open to YOUR homepage. Most infuriating when they don't!

---

### Post by Dennis N on 2014-07-21
Unfortunately, I missed your last 2 posts.  Well, I do exactly the same thing as you - use a local file for my home page. 

For anyone interested, you can set an HTML file on your computer to be your home page by opening the file first, then go to: 
Preferences > General > Startup > Home Page and click on **Use Current Page**. (see attached screenshot). 
The address will appear in the address window. You would use that same address when using the steps from post #2 to make the new tab page to open there too. 

But, not much good unless your local home page does something. If you know some basic HTML coding from school, you can make a local website of personalized directories of websites you visit and other custom contents. Lots of fun and room for creativity.

Good Luck.

---

### Post by Bucky Ball on 2014-07-22
Could you please use the default font size when simply posting, thanks, and not large font.Overly large text (along with bold) in a post is often considered to be shouting. I have edited your posts accordingly.  ;)

---

