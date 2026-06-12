---
title: "Alternative to frameset tags for affiliate programs"
date: 2009-02-27
forum: Programming Talk
---

### Post by JoeDively on 2009-02-27
I am have a problem with some of my affiliate programs.

Instead of linking directly to their programs I like to have a domain for each one so I can do better in the search engines.

Lately I have been getting code from the affiliate sites to place on my default www page something like below.

{!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"}
{HTML}
{HEAD}
	{META http-equiv="Content-Type" content="text/html; charset=ISO-8859-1"}
	{TITLE}my affiliate page{/TITLE}
{/HEAD}
{FRAMESET rows="100%,*" border=0 frameborder=0 framespacing=0}
	{FRAME name=top src="http://www.xyz.com/affiliatename" noresize}
{/FRAMESET}
{/HTML}

This works but of course I lose all the details about items that are selling and every link clicked then just stays with the same source code as far as search engine spiders are concerned. 

Is there a way to use some parsed program to pull in this data from the affiliate link so that it looks to the search engine spiders like it resides on my domain rather then on an affiliate site.

The other option is to take all their pages and load them in but since they do give me metatag and content control of the pages at the true affiliate link 
[http://www.xyz.com/affiliatename](http://www.xyz.com/affiliatename)

It seems like a huge job to load in several hundred pages of items for sale and keep the pages updated.

I am thinking there has to be a way to just pull this content to the page using some parsed pgp or perl routine.

Any help would be appreciated

Thanks
Joe

---

