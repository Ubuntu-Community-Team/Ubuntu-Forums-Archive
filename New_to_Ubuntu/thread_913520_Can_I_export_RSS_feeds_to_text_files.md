---
title: "Can I export RSS feeds to text files?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by littletinman on 2008-09-07
I use Lifera Feed Reader and i need need to export all the posts from my Google websites into text files, so that i can bring them to school on a thumb drive. I'm researching Google, and i need all that info. Is there a way i can quickly export all those posts?

---

### Post by Cheesehead on 2008-09-07
Right-click on a feed in Liferea. Select 'properties'. Copy the feed URL (usually ending in .rss or .xml or some such).
Download the feed URL.  (for example, command line 'wget URL')

A feed is just an XML file, and so you'll wind up with a bunch of XML files (one per URL, of course). Put those on your USB stick.

Some web servers require special headers in the request before they actually send the feed to you; instead they'll send you a redirect or File Not Found when you try to download the URL. I don't know of an easy way around those...

---

