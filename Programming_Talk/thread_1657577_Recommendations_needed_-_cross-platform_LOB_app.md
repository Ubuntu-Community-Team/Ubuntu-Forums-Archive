---
title: "Recommendations needed - cross-platform LOB app"
date: 2011-01-01
forum: Programming Talk
---

### Post by Newbie2910 on 2011-01-01
Hi, looking for some suggestions.

I am building a LOB application which will initially run on Windows but I will also need to support Linux shortly too. It is absolutely imperative that I have a single code base, I don't have the resources to maintain separate versions for Windows and Linux.

I am trying to decide whether to build this application using Silverlight/Moonlight or GTK+.

Silverlight/Moonlight Pros:

[LIST]
[*]Easy to launch from a URL and runs in a browser
[*]No need to install GTK runtime on Windows machines
[/LIST]
Silverlight/Moonlight Cons:

[LIST]
[*]This application will require Silverlight 4 and Moonlight seems to be way behind (Moonlight 4 was supposed to be out early in 2010 according to the release notes... it seems to be "stuck" at 2).
[*]Sandbox issues (though SL4 seems to allow enough "outside the box" functionality I think my app would be ok).
[/LIST]

GTK+ Pros:

[LIST]
[*]Proven windowing system, very mature, and I have played with Glade enough to know that I like that development environment
[*]Appears to have all the functionality my app would need (no sandbox issues like with browser-based apps)
[/LIST]
GTK+ Cons:

[LIST]
[*]Requires user to install a GTK runtime on  Windows machines
[*]Requires an actual application install (-vs- just navigate to a URL in a browser)
[/LIST]

What do you all recommend I do?  Or is there an alternative I haven't thought of?

Using Ubuntu 10.04 and MonoDevelop.

thanks.

---

