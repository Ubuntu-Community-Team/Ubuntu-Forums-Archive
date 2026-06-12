---
title: "&quot;Loading forever--video never starts"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by rashby3 on 2008-08-09
Here is a link to a Stephen Colbert video that my brother sent me:

[http://www.thedailyshow.com/video/index.jhtml?videoId=116827&title=headlines-welcome-home](http://www.thedailyshow.com/video/index.jhtml?videoId=116827&title=headlines-welcome-home)

When I click on it in Firefox in Windows, it says "Loading" for a few seconds and then the video starts.

When I click on it in Firefox in Ubuntu, it says "Loading" permanently, and there is nothing I can do to get the video to start. There are no error messages or pop-ups telling me I need to install some plug-in. It just stays in the "Loading" state forever.

Anyone have any suggestion? I am able to watch some videos on my Ubuntu laptop, but not this one or others from the same site.

Thanks very much.

---

### Post by SZ07 on 2008-08-09
I think it might be a flash problem. Are other flash videos playing correctly? It works on my computer but I'm running flash 10 beta 2.

Try this:
Remove flash player by typing the following in the terminal
```
sudo apt-get remove flashplugin-nonfree
```

Then reinstall flash
```
sudo apt-get install flashplugin-nonfree
```

This might fix your problem. If it doesn't, then you might want to install Flash 10 Beta 2 (note that it is beta software and does not work perfectly) by following this guide: [http://tombuntu.com/index.php/2008/07/22/test-drive-adobe-flash-player-10-beta-2-in-ubuntu/](http://tombuntu.com/index.php/2008/07/22/test-drive-adobe-flash-player-10-beta-2-in-ubuntu/)

---

### Post by Crafty Kisses on 2008-08-09
If Flash is a no go, you might want to try Gnash, which is the OpenSource alternative.

```
sudo apt-get install gnash
```

---

