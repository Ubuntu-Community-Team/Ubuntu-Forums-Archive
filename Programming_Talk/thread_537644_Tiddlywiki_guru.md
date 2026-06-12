---
title: "Tiddlywiki guru"
date: 2007-08-29
forum: Programming Talk
---

### Post by in_flu_ence on 2007-08-29
I am looking for a tiddlywiki guru for assistance in getting a tiddlywiki to display the pages as the way I want to.

Anyone?

Thanks

---

### Post by PhilWhitehouse on 2007-08-30
Hi in_flu_ence,

I'd like to try and help you. I work with Jeremy Ruston, the original creator of TiddlyWiki, for a company called Osmosoft ([http://www.osmosoft.com](http://www.osmosoft.com)) in London, and we have several people here with specialist knowledge of TiddlyWiki.

What are you trying to achieve?

All the best,
Phil

---

### Post by in_flu_ence on 2007-08-30
HI, it is a simple problem.

I was trying to check out the way how I can automatically close a 'page'/tiddler when I open another. 

e.g. in the osmosoft page that I click from the link. How can I close the 'What are you doing?' & 'staff blog' tiddler when I open the 'events' tiddler/page?

is there an automatic way?

Thanks.

P.S. Tiddlywiki is a nice creation. Don't give it up by any chance.

Harris

---

### Post by PhilWhitehouse on 2007-08-31
Hi Harris,

Yep, there is a solution. 

I'm assuming you're using version 2.2 or later of TiddlyWiki, which features 'Backstage' functionality. If not, let me know and I'll provide alternative instructions.

You need to import a tiddler called SinglePageModePlugin from a site called TiddlyTools. Here's a step by step:

1. Check out this page: [http://www.tiddlytools.com/#SinglePageModePlugin](http://www.tiddlytools.com/#SinglePageModePlugin) (just to read about what's about to happen)

2. Go back to your TiddlyWiki file, click on the 'Backstage' link, and click on 'Import'.

3. Select 'file' from the first drop down, and then enter the URL: [http://www.tiddlytools.com/](http://www.tiddlytools.com/) and then click Open.

4. Select (default) from the drop down menu, and click Open.

5. Check the box next to SinglePageModePlugin, scroll to the bottom and uncheck the box at the bottom of the page next to "Keep these tiddlers linked to this server....". Click on import.

6. Click on Done, and then click on Close (to close the Backstage area).

7. Save changes to your TiddlyWiki, then reload.

8. Click on Options, then click on Advanced Options, and check the box next to "Display one tiddler at a time". Then close the tiddler to save your changes.

9. You're done! Click and test.

One thing to be wary of is that you can now click the back button to return to the previous "page". If you do this when editing a tiddler, the browser won't save your changes. But it sounds as though you're the only editor, so you're the only person that needs to be aware of this.

Let me know if you have any problems. There are also some other areas you might find helpful:

[http://groups.google.com/group/TiddlyWiki](http://groups.google.com/group/TiddlyWiki)
[http://groups.google.com/group/TiddlyWikiDev](http://groups.google.com/group/TiddlyWikiDev)

All the best,
Phil

---

### Post by in_flu_ence on 2007-08-31
Many Thanks.

I am apparently using version 2.1.3. Sad to say I am bad in keeping track of updates.

Any further instruction for that?

Cheers
Harris

---

### Post by PhilWhitehouse on 2007-08-31
Not to worry, upgrading is (usually) a trivial exercise. Make sure you save a backup, then follow the instructions here:

[http://www.tiddlywiki.com/#HowToUpgrade](http://www.tiddlywiki.com/#HowToUpgrade)

Let me know if you have any problems,

Phil

---

### Post by in_flu_ence on 2007-08-31
Many thanks again. It does work by using the import plugin since I think I might have deleted some part of the code (e.g. the tagging system).

Btw, is there a possibility/plugin that I can 'click' to hide the tags as well as the sidebar which shows the 'timeline' etc.?

I aim to minimise the number of manual changes to ensure more smooth upgrade in the next releases.

---

### Post by PhilWhitehouse on 2007-09-03
Hi Harris,

I'm pretty sure there's a way to meet your needs. I think at this point the best thing you can do is head over to the TiddlyWiki community, who'll have a lot more useful information than I have at my disposal! They're a really helpful bunch, and will be able to walk you through the various options and their implications:

[http://groups.google.com/group/TiddlyWiki](http://groups.google.com/group/TiddlyWiki)

Hopefully see you there!

All the best,
Phil

---

### Post by in_flu_ence on 2007-09-03
Thanks Phil.

---

