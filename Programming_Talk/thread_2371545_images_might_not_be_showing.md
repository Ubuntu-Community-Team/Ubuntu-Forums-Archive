---
title: "images might not be showing"
date: 2017-09-15
forum: Programming Talk
---

### Post by TheodoreP on 2017-09-15
I'm having a few issues with my website, the background images and plus and minus images aren't showing up for me on the live site and the developer tools inside firefox say it's because of a 403 forbidden error. Anyone wanna try and help me solve this issue. If so please visit [http://www.theodorepr.com/](http://www.theodorepr.com/).

The local version of my site that I work with on my laptop works perfectly, it's just the live version that refuses to show me the backgrounds and images.

If you would also like to critique my site, I'm always welcome to them.

---

### Post by SeijiSensei on 2017-09-15
The Apache process runs as the user www-data.  That user must have full read and list privileges on the website's files and directories.

---

### Post by TheodoreP on 2017-09-15
It does cause the site run it just wont retrieve the images from the assets folder, so I guess I'll modify the question to, I would like to know if what the site looks like to others.

---

### Post by norobro on 2017-09-16
From here it looks like you should be getting a 404 - Not found.

---

### Post by TheodoreP on 2017-09-16
I just checked my assets/backgrounds folder and my images are in there......? Using the firefox developer tools it says 403 forbidden error.

---

