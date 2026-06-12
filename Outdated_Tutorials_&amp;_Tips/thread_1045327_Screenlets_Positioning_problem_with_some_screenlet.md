---
title: "Screenlets: Positioning problem with some screenlets"
date: 2009-01-20
forum: Outdated Tutorials &amp; Tips
---

### Post by killmepl on 2009-01-20
If your screenlet dont remember its position after restart log off or something else, then here is aid.

1. 
```
~/.config/Screenlets/[name_of_screenlet]/default/[name_of_screenlet].ini
```

In this file are x and y coordinates - that can help.
But if no, then

2.
```
/usr/share/screenlets/[name_of_screenlet]/[name_of_screenlet]Screenlet.py
```

search for
```

	# constructor
	def __init__(self, **keyword_args):
		screenlets.Screenlet.__init__(self, uses_theme=True,width=int(**XXX**), height=int(**XXX**), **keyword_args)
```

and instead of XXX write smaller number. Save. And be happy, because when restarted, you can place that modified screenlet and it wont jump anywhere else.

I had that problem with NowPlaying screenlet. When I wanted to place it near right side of screen it was ok until log off, restart screenlets, restart of computer, next time I turned it on it was 50-100px on the left, and again i had to manually place it on right place.
I searched over the net to find nothing, so had to do this on my own, so i hope this will be useful.


GL HF, k

PS sorry for my english :<

---

