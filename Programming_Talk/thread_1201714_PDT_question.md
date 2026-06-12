---
title: "PDT question"
date: 2009-07-01
forum: Programming Talk
---

### Post by Mirge on 2009-07-01
Anybody have any problems getting "Generate Getters and Setters" to work for PHP in Eclipse PDT?

An older Zend tutorial said to right-click, go to source, and click generate getters & setters... but that didn't even exist on mine. And trying the keyboard shortcut for it didn't work either. Would be super convenient if it does work... any thoughts?

---

### Post by Mirge on 2009-07-01
Been playing around with it, but still no go... any ideas?

---

### Post by Mirge on 2009-07-01
Oook disregard. I installed Zend Studio 6.1.2 trial... and it works flawlessly there. And it actually seems to be quite a bit snappier too! Shame it costs $399.... but I'm sure I'll end up buying after my 30-day trial is over.

---

### Post by Mirge on 2009-07-02
OK, talking to myself again :) but I'll try anyway...

I re-installed PDT 2.1.0, got SVN working for it, got it all set up how I like... installed the plugin "PHP Source", which is a "Generate Getters/Setters" plugin. It works, but I can't change it at all... what's generated. Any thoughts?

I looked deep into the .jar file, and found a templates/ directory... edited the .tpl files to format them how I wanted... re-compressed the whole directory structure using jar -cf blah.jar blah/ ....... then when I copy that over my plugins/blah.jar, Eclipse dies while loading with an error that's too fast to see, and nothing is shown in the console.

The plugin I'm talking about can be found at: [http://pdt.plugins.e-surf.pl/](http://pdt.plugins.e-surf.pl/)
Updates Site: [http://pdt.plugins.e-surf.pl/updates/](http://pdt.plugins.e-surf.pl/updates/)

Please help if you can... this is the last thing I need working til I'm free of buying Zend Studio :P.

---

