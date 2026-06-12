---
title: "Does anyone have experience with Javascript and Firefox?"
date: 2008-01-17
forum: Programming Talk
---

### Post by Metallion on 2008-01-17
This might not be exactly programming but I didn't see a webdesign forum so I guess it's close enough.

I've got a simple Javascript for printing a menu on the page. It pretty much only does document.write() and for some reason it's not showing up in firefox. It works just fine in both konquerer and opera though. I was wondering if anyone knows what I should do to get firefox to work as well... I figure it must be some tiny setting. I already checked if Javascript is enabled in ff and it is.

The site's over here:
[http://users.telenet.be/Metallion/site/template.html](http://users.telenet.be/Metallion/site/template.html)

And here's the script:
[http://users.telenet.be/Metallion/site/script/script.js](http://users.telenet.be/Metallion/site/script/script.js)

The firefox toolbar tells me that there are no errors in the script.

---

### Post by chewearn on 2008-01-17
On line 8 of your html:
```
<script type="text/javascript" src="script/script.js" /> 
```It should read:
```
<script type="text/javascript" src="script/script.js"></script> 
```

---

### Post by naugiedoggie on 2008-01-17
> **Metallion said:**
> This might not be exactly programming but I didn't see a webdesign forum so I guess it's close enough.

I've got a simple Javascript for printing a menu on the page. It pretty much only does document.write() and for some reason it's not showing up in firefox. It works just fine in both konquerer and opera though. I was wondering if anyone knows what I should do to get firefox to work as well... I figure it must be some tiny setting. I already checked if Javascript is enabled in ff and it is.

The site's over here:
[http://users.telenet.be/Metallion/site/template.html](http://users.telenet.be/Metallion/site/template.html)

And here's the script:
[http://users.telenet.be/Metallion/site/script/script.js](http://users.telenet.be/Metallion/site/script/script.js)

The firefox toolbar tells me that there are no errors in the script.

Hello,

One of those simple but annoying errors.  This line:


```
<script type="text/javascript" src="script/script.js" />
```

You can't do that.  It has to be 

```
<script type="text/javascript" src="script/script.js"></script>
```

The missing </script> tag borks up everything that follows that line.  FF is just prissy enough to punish you for your mistake.  Some other browsers will "compensate" for it.

Thanks.

mp

---

