---
title: "HOWTO: Disable new preview plane for ctrl-tab switching in Minefield 3.6a1pre"
date: 2009-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by MaxIBoy on 2009-05-28
Okay, newer Minefield builds have an amazing new feature. I'm not exactly sure what it's called, but it's really cool. Instead of a list of tabs, you get something like this:
[img]http://img11.imageshack.us/img11/5413/200905280850191280x800s.png[/img]

I'm all for it! It's a great way to see what each tab is. 

However, by default, Minefield enables this for control-tab switching as well. In my opinion, the old system was much better for control-tab switching-- you get a full-size preview of each tab as you select it in turn. An even bigger crime of the design is that the selector seems to switch through the previews at random every time you hit the tab button. (It displays them in the same order as they appear on the top bar, but switches between the tabs in order of most recently accessed, which is very confusing.) 

My googling turned up nothing, so I was left with no other option but to randomly poke around in about:config. I was lucky though, it's fairly straightworward.


Go into about:config. If you get a pop-up saying that this could void your warranty, pause to consider that the pop-up is absolutely correct. Then click OK.

In the "filter" field, type "ctrlTab." You should see something like this:
[img]http://img135.imageshack.us/img135/940/aboutconfigbrowserctrlt.png[/img]

Simply double-click "browser.ctrlTab.previews" so it goes from "true" to "false," and you're done. The preview panel still works if you click on it, but it works the old way if you use control-tab switching.

---

