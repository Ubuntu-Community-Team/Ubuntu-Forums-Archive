---
title: "Opera, Firefox, and Flash"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by BGThree on 2008-05-06
I installed opera just to see how it is, but Flash is not working.  I already installed Flash for Firefox and it works just fine.  

Do I have to install a different copy of Flash for every browser I have?  Or is there some way to tell Opera that I already have Flash installed?

Thanks for any help and please let me know if you need more info from me :)

---

### Post by Enternald on 2008-05-06
I think you must, because diferent browser uses diferent modules. In example in windows you have to use flash player in opera IE7 Firefox. Some pages have automatical redirect where download flash player. Just go to adobe.com and read more.

---

### Post by Kinst on 2008-05-06
No. Opera goes hunting for the flashplayer.so file in your firefox folder (/home/you/.mozilla/plugins).

The problem is it's confusing and screws up easily. Go to the page opera:plugins to see all the ones opera finds and doesn't use properly.

---

### Post by BGThree on 2008-05-06
In the opera preferences>advanced>content>plug in options it lists three plug ins:

NS4PluginProxy - Proxy plugin for netscape 4 plugins - /usr/lib/opera/plugins/libnpp.so

Shockwave Flash - Shockwave Flash 9.0r124 - /usr/lib/mozilla/plugins/flashplugin-alternative.so

Shockwave Flash- Shockwave Flash 9.0r124 - /usr/lib/flashplugin-nonfree/libflashplayer.so


Regarding the first Flash plugin in this list, as far as I can tell that directory does not exist - my .mozilla directory only contains: extensions and firefox

Regarding the second Flash plugin, that pathway appears to be correct

Any idea how to make opera recognize the flash player?  More than anything this is just an educational experience for me - I'm actually quite happy with Firefox as it is.

---

### Post by dstin1 on 2008-05-06
get the beta version of opera [here]("http://www.opera.com/products/desktop/next/")

then follow these [instructions]("http://sysblogd.wordpress.com/2007/08/01/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/#comment-5142") this worked flawlessly for my to get flash working with opera.

---

