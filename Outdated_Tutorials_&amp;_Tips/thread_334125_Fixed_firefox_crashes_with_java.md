---
title: "Fixed: firefox crashes with java"
date: 2007-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by jdmicklos on 2007-01-08
Hello All, 

Many of you have been experiencing crashes with Java and Firefox. I have figured out was specifically my problem. Hopefully this helps you. 

Your useragent for you browser may be incorrect. For one reason or another, mine was set to opera. 

Go to: [http://www.cambiaresearch.com/cambia3/myuseragent/](http://www.cambiaresearch.com/cambia3/myuseragent/) to see your useragent. 

If you are using firefox 1.5, the useragent:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20061031
seems to work fine with java.

In your address bar, type in about:config. Once that loads, right click on the screen New->String. Title the string: 
general.useragent.override

The value of the string is a true mozilla firefox useragent string. As I said, firefox 1.5 seems to like the string:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.7) Gecko/20061031
for its user agent. 

Test it out, go to [http://www.cambiaresearch.com/cambia3/myuseragent/](http://www.cambiaresearch.com/cambia3/myuseragent/) to see if it updated your useragent. Then procede to test out java. 

For me at least, ](*,) has turned into :-D  
I hope this helps you out as well!

-Jonathan Micklos

---

