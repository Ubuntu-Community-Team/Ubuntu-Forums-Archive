---
title: "[SOLVED] Quick question about exporting Jar files from eclipse, images not showing"
date: 2008-02-29
forum: Programming Talk
---

### Post by th3james on 2008-02-29
Hi guys

Im trying to export a Jar file from eclipse, and I'm having exactly the same problem i had last time i tried to do it (about a year ago!). I managed to fix it back then, but i can't for the life of me remember how!
Basically, when i create a jar file using the export wizard in eclipse, none of my images show up, even though they are in the Jar file. Is it something to do with the classpath? the images are located in /img/ of the root of the jar.

TIA

James

---

### Post by th3james on 2008-02-29
Don't worry, worked it out!
for anyone with the same problem, make sure you're calling your images using this method:
```

        // create a URL to get the image
        java.net.URL imgURL = getClass().getResource("/img/theimageyouwant.png");

         // insert the URL, rather than the address
	private Image titleImg = Toolkit.getDefaultToolkit().getImage(imgURL);
```

---

