---
title: "IE's drop-down box over div problem in &quot;overlib&quot; Javascript library"
date: 2009-01-16
forum: Programming Talk
---

### Post by zpzpzp on 2009-01-16
I am having a problem using this line of implementation:
overlib('<div align=\'left\' id=\'contentarea\'></div>', BGCOLOR, '#AAAAAA', FGCOLOR, '#c3d9ff', TEXTCOLOR, '#000000', TEXTSIZE, '13px', WIDTH, 600, HAUTO, VAUTO);
Is there a way to get around the problem in IE where the drop down box is always on top of div, like illustrated on this page:
[http://esdi.excelsystems.com/wsexmp/divdrp.pgm?wsnum=00110](http://esdi.excelsystems.com/wsexmp/divdrp.pgm?wsnum=00110)

I have tried several things, including the following piece of code:
overlib('<iframe id=\"theframe\" src=\"\" class=\"frmcls\"></iframe><div align=\'left\' id=\'contentarea\'></div>', BGCOLOR, '#AAAAAA', FGCOLOR, '#c3d9ff', TEXTCOLOR, '#000000', TEXTSIZE, '13px', WIDTH, 600, HAUTO, VAUTO);
And then in the html page I added the followong:
<script>
positionDiv('contentarea', 'theframe');  //this function is shown on this page: [http://esdi.excelsystems.com/wsexmp/DIVDRP.pgm?task=showinst&wsnum=00110](http://esdi.excelsystems.com/wsexmp/DIVDRP.pgm?task=showinst&wsnum=00110)
</script>

However I have not been able to get desired result.

Could you please advise me on this issue? Is there a way to solve this problem in overlib?

Thanks in advance,

Paul

---

### Post by cl333r on 2009-01-17
I haven't tried to debug your issue, but have you tried using the Z index CSS property?

[http://www.w3schools.com/Css/tryit.asp?filename=trycss_zindex2](http://www.w3schools.com/Css/tryit.asp?filename=trycss_zindex2)

---

### Post by zpzpzp on 2009-01-19
> **cl333r said:**
> I haven't tried to debug your issue, but have you tried using the Z index CSS property?

[http://www.w3schools.com/Css/tryit.asp?filename=trycss_zindex2](http://www.w3schools.com/Css/tryit.asp?filename=trycss_zindex2)

Thanks for your reply cl333r.

I followed the code on the link that you provided, but unfortunately it doesn't work.

Inside of the "overlib" javascript library the div container's z index is set to 1000:
```
id = (id || 'overDiv'), frm = (frm || o3_frame), zValue = (zValue || 1000);
```

I set the div's z-index to 1000, but the only difference I could see was that the background color of the popup window is gone...

Anyone has any suggestions please?

Thanks in advance,

Paul

---

