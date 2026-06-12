---
title: "webdesign help....sizes..."
date: 2008-01-21
forum: Programming Talk
---

### Post by hockey97 on 2008-01-21
Hi  I have been using gimp in windows to make the art for my webpage.

I now have a problme with sizes.  I created a table with x width and  y height.

I also made data cells in these cells I have the first one for a art graphic that looks like a 3d tab. In the second row new data cell I use a graphic to display in the backround.

The backround image is 420x300 which I made the data cell with width"400" heights"300"  the graphic shows but it's offest.

The 3d tab is supposed to be on top of this backround image which are 2 different rows and data cells.

what I get when displayed I got the backround image but I see the 3d tab in the middle of the backround image. It dosen't look like a table.

What do you guy's do about sizes??  How can you get stuff fit perfectly??

---

### Post by Geekkit on 2008-01-21
> **hockey97 said:**
> Hi  I have been using gimp in windows to make the art for my webpage.

I now have a problme with sizes.  I created a table with x width and  y height.

I also made data cells in these cells I have the first one for a art graphic that looks like a 3d tab. In the second row new data cell I use a graphic to display in the backround.

The backround image is 420x300 which I made the data cell with width"400" heights"300"  the graphic shows but it's offest.

The 3d tab is supposed to be on top of this backround image which are 2 different rows and data cells.

what I get when displayed I got the backround image but I see the 3d tab in the middle of the backround image. It dosen't look like a table.

What do you guy's do about sizes??  How can you get stuff fit perfectly??

You might want to check these folks out as they are masters of liquid layouts and creating layouts that resize:

[http://www.maxdesign.com.au/presentation/liquid/](http://www.maxdesign.com.au/presentation/liquid/)

For example templates that put this to practice check out:

[http://www.oswd.org/](http://www.oswd.org/)

It is generally considered bad practice to use HTML tables for creating layouts. Tables are for tabular data not for creating layouts. CSS and div elements are for creating layouts. Lastly, you should at least be trying to go with XHTML transitional although XHTML strict is better since it can be easily parsed by XML parsers and other applications that need to insert content.

---

