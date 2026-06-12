---
title: "changing the letter color in php..."
date: 2008-08-11
forum: Programming Talk
---

### Post by Mia_tech on 2008-08-11
I have a php page which is pretty much a calendar, but the page background I want to make it black, so the the letter output also come out in black what makes it impossible to see so I put the php code inside the <font color="#ffffff"></font> tags... but the text is still coming out in black 
could someone tell me how could do this?

thanks

---

### Post by diafanos on 2008-08-11
why don't you try writing
echo "<font color=#ffffff>"

...rest of your php code...

echo "</font>"

I mean inside your php code, not before and after it

---

### Post by kostkon on 2008-08-11
> **Mia_tech said:**
> I have a php page which is pretty much a calendar, but the page background I want to make it black, so the the letter output also come out in black what makes it impossible to see so I put the php code inside the <font color="#ffffff"></font> tags... but the text is still coming out in black 
could someone tell me how could do this?

thanks
The font tags are deprecated. Why not use CSS instead to set the text colour to white. You can put the following in the head of your page:
```
<style type="text/css">
  body { color: #ffffff; }
</style>

```

---

### Post by ThinkBuntu on 2008-08-12
> **Mia_tech said:**
> I have a php page which is pretty much a calendar, but the page background I want to make it black, so the the letter output also come out in black what makes it impossible to see so I put the php code inside the <font color="#ffffff"></font> tags... but the text is still coming out in black 
could someone tell me how could do this?

thanks
Here's how to do it:

**Template Page:**```
<head>
    ...
    <link href="screen.css" rel="stylesheet" media="screen" type="text/css" />
    ...
</head>
```

**screen.css:**```

/**
 * screen.css
 * Calendar App stylesheet
 * @media screen
 */
body {
    background-color: black;
    color: white;
}

/**
 * I'm not sure if that DocBlock conforms to any 
 * standard. I just find that a few comments make
 * CSS much easier to maintain.
 */
```
Try to write the Calendar system as a floated-block layout rather than tables as well. Doing this will make it trivial to use the calendar template in different view styles.

---

