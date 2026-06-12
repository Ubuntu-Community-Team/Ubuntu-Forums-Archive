---
title: "Html: Borders down the side of webpage"
date: 2007-09-04
forum: Programming Talk
---

### Post by b0ng0 on 2007-09-04
I am writing my report for work in HTML and it would look well snazzy if I could put continous borders down the left and right sides of the page. I am just looking for some HTML code that would do this, I have the images already.

Just looking to have some colour down the sides to box the main content in. Thanks.

---

### Post by LaRoza on 2007-09-04
> **b0ng0 said:**
> I am writing my report for work in HTML and it would look well snazzy if I could put continous borders down the left and right sides of the page. I am just looking for some HTML code that would do this, I have the images already.

Just looking to have some colour down the sides to box the main content in. Thanks.

```

body
{
    border-right-color:#000000;
    border-right-width:2px;
    border-right-style:ridge;

    border-left-color:#000000;
    border-left-width:2px;
    border-left-style:ridge;
}

```

Add this to a style sheet, external would probably be best.

Fiddle with it after writing the report.

Of course, you can change the color, width, and style, this is just an example. Also, you will can alter the padding or margins to set them right.

-EDIT I don't know how your markup is, but I am assuming it is plain XHTML (h1-h6, p, ul, ol). Put it all in a div, and apply the style to that instead of the body. You can then give the div the dimensions you want, and have better control.

---

### Post by b0ng0 on 2007-09-04
Thanks works a treat. Just added the border properties into the body section of style before the main document code.

---

### Post by LaRoza on 2007-09-04
Glad it helped.

---

