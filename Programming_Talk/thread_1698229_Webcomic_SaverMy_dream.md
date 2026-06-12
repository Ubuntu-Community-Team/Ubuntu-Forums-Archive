---
title: "Webcomic Saver:My dream"
date: 2011-03-02
forum: Programming Talk
---

### Post by gearactua on 2011-03-02
Ok I read a lot of webcomics. Theres some really good stuff out there and I love rereading old stuff-sometimes stuff that isn't online anymore. My problem is that individually saving each comic any time a new one comes out is a nightmare-and that's not even mentioning going through the archives of long running comics like OOTS.

Now I recognize that this could be averted by just purchasing some-but that isn't always an option-besides the fact I've lived with a thief who let's in thieves, Ive moved countless times, and...OH YEAH! got flooded out. My USB and my laptop are most of what I have past half rotted clothes and the books I had JUST put on shelves. So please no grief over not wanting to pay the artist-I'm grabbing what's free only-and making sure I wont lose it.

Now over the past few months I've discovered several comic saver programs-none of them more than a 5 on a 1 to 10. That says nothing about the programmers but rather more about apache security. The idea this-

A program that through the simplest means of definition and interaction will download archives of web comics and then maintain up to date status so long as internet connection is maintained-perhaps even be able to start from last taken and check for new pages.

Not exactly difficult to understand, but application seems to be a major stumbling block.

In the next few posts I will be talking about programs I've found, their stumbling blocks and problems I as both a User and specifically a Linux user have faced.

---

### Post by gearactua on 2011-03-02
Woofy
This was a bit of my last hoorah on Windows Vista-No bad-mouthing Vista here, I liked it-I had a short email conversation with the guy when I was trying to get a "Definition" for a comic to work. So far as I can tell the story is this. He wrote the program in Perl. It visits the website and uses next or back buttons (depending on the version) to move frome page to page and uses the definition to search the source code for the page to find the link for the img file. It then saved the image to your disk.

This was the best one I've come across even if it didn't work all that well. If you could understand exactly what you needed for your definition and then were able to put it in the right folder the right way and the leave it alone AND not have it crash-It worked beautifully. The end result was a masterpiece but the road was a trans-dimensional maze lined with singularities. As well, unfortunately this is a windows only operation. I've tried configuring Wine but as the program just barely reached version 1.0 before the programmer left (too busy according to him which I can understand) it doesn't seem to be the best option.

[http://code.google.com/p/woofy/](http://code.google.com/p/woofy/)

Comic Saver

Based on XUL a seemingly short lived firefox XML interface project, this was more of a mess than Woofy and didn't seem to do anything. I believe it was designed to work in a windows environment as well and as I've just reinstalled 10.04 (Maverick plays hell with my Nvidia) not everything is back up so I haven't yet tried running it under a Wine firefox. 

[http://www.softpedia.com/get/Internet/Internet-Applications-Addons/Mozilla-Extensions/Comic-Saver.shtml](http://www.softpedia.com/get/Internet/Internet-Applications-Addons/Mozilla-Extensions/Comic-Saver.shtml)

Wget

I thought this little bugger would be my salvation, but Apache brought hell home with it.

The first thing you'll be likely to try is-

wget [http://www.server.com/dir/*.gif](http://www.server.com/dir/*.gif)

When you try to understand why it didn't work you'll find in the manual that "http retrieval does not support globbing" which means that it wont just download that whole directory so you try-

wget -r -l1 --no-parent -A.gif [http://www.server.com/dir/](http://www.server.com/dir/)

-which doesn't work either. After some more searching you'll find out two things-
robot.txt and user agent. So you try to specify user agent- Im not a bot! I'm Mozilla! Didn't work. Ok... I'm Opera/9.80 (X11; Linux x86_64; U; Ubuntu/10.10 (maverick); pl) Presto/2.7.62 Version/11.01-Crap!
403! 403! 403!!!

What's going on here? I have no idea.
Now lets say I just try something simple-

wget [http://www.placewiththething.com/comicpagetypestuff/20110122.jpg](http://www.placewiththething.com/comicpagetypestuff/20110122.jpg)

IT WORKED!-but I don't know all the image file names-and the index page is blocked. So I could use that, but I'd need to parse the individual links from the source code-HOW DO I EVEN DO THAT?

So this is a case of walking into invisible brick walls. You have to hit them to even know they're there. It' a good shot-but making something it can use is the key.

[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)

Dosage

This particular program is old and oldschool. Terminal access only-not much of a problem-but how do I even use it?
The webpage dealing with its set up and use is archived at-

[http://www.linux.com/archive/feed/118809](http://www.linux.com/archive/feed/118809)

After reading what I can make out on the page' this is more of a consolidation reader than a saver-and though it's probably well built  it has two major flaws: Lack of Usability, and being outdated. 2007 may not seem like long time ago but many websites may have changed styles 7 or eight times since then, not to mention Ubuntu itself. It's a good idea, but it isn't what is needed, and it's old and unsupported.

Where to go from here
A combination of Woofy techniques with Linux tools like wget seems to be the best bet-but I'm not even sure where to begin.

I'd like to start brainstorming so I've gathered what information I can here and Ill add more as I better understand what needs to be done.

---

### Post by GenBattle on 2011-03-02
This sort of thing needs some sort of python/perl/whatever script that crawls pages, looks for a particular element in the DOM, or retrieves comics based on a particular url encoding (most comics use the same URL day-to-day but change the date stamp).

Course such a system would be a little simplistic, and would require another set of code for each webcomic you want to download. Penny Arcade would have to be parsed in a different way to CAD.

That said, it should be simple to at least get started; python allows for scraping web pages in around 10-20 lines of code, then it's just the parsing structure you need to work out.

If you wanted to get complex you could work out some sort of schema to create config files that specify how each site should be parsed, so you don't have to update the code base as much. Downloading comics without visiting the page will strip away some of the ad revenue for the artists who fund their work through advertisements on the comic pages.

---

### Post by Ranko Kohime on 2011-05-04
I don't know if you've ever used iStrip on the Mac, but THAT is the program I'm looking for on Linux.

It doesn't make webpages, but it downloads the images to it's own folder system for display within the program.  Not perfect for archival, but it flat out worked except for those occasions when the author completely re-designed their site.

I have to agree with the comment on dosage.  I can't wrap my mind around it.

I'm subscribing to this thread to see what you come up with.  Cheers.  :)

---

### Post by gearactua on 2011-05-09
To tell the truth, as with most things I shortly put this aside until I came back to it-which I knew I would eventually. Since my previous post I have upgraded my system to 11.04. All this means is that out of sheer simplicity, I will be writting in Python 2.7.1.
Some of the people on the #python channel on the freenode IRC network pointed me to lxml and will be studying that in order to 'scrape' web pages for relevant data. I continue to wonder how to create a gui even as I war with the simple tasks.
Post upgrade, some of my earlier problems have disappeared but I still know very little. I will attempt to keep this thread updated as I progress.

---

### Post by wmcbrine on 2011-05-11
Many strips offer an RSS feed with each strip as an enclosure. This makes things much easier than trying to scrape a web page. For strips with no feed, I'd just create a feed first, via a service like page2rss.com.

---

### Post by sweetleaf on 2011-05-11
For the scraping part of your project, it might be helpful to look at the code for these two:

[Webcomic Reader]("http://userscripts.org/scripts/show/59842") for Greasemonkey

AWN [Comics]("http://wiki.awn-project.org/Comics!") applet

---

