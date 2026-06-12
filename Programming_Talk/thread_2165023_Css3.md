---
title: "Css3?"
date: 2013-08-02
forum: Programming Talk
---

### Post by catlover48856 on 2013-08-02
Hello my name is Brooks and I am currently aiming to create my own website through Html5, CSS3, and Javascript. However I didn't get very far before I hit a roadblock. While using Bluefish IDE it gives auto-complete options. When trying to resize my backround I decided to use "background-size" from CSS3. But it didn't give me the auto-complete option. I typed it in anyway and ran the program in firefox (Latest Version) but it didn't resize. Please help.

```

<!DOCTYPE html>
<html>
 <head>
  <title>BnJ's Personal Pc's-Colorado's Choice Custom Computers</title>
  <meta charset="utf-8">
  <meta name="description" content="BnJ's Personal Pc's finally gives the average Joe the infomation they needed to buy their very own
   computer. Making personal computers personal.">
  <style>
  h1{
  text-align:center;
  color:gray;
  padding-bottom:.5cm;}
  body {
    background-image:url(Sources/HPbackground.jpeg);
  }
  p{
  font-family:"Tlwg Typo";
  font-size:25px;
  text-align:left;
  }
  .titleB{
  background-color:greenyellow;
  background-size:3cm 2cm;<-There
  border: 5px solid darkgray;
  
  }
  
  </style>
  </head>

 <body>
 
 <div class="titleB">
   
   <h1>Welcome To BnJ's Personal Pc's!</h1>
   </div>
   
 <p>Get started below.</p>

 </body>
```

Thanks,
Brooks Rady

---

### Post by pqwoerituytrueiwoq on 2013-08-02
probably cause your background is a color not a image is why it is not working
if you really need to resize a background color use a css gradient from and to the same color
also you should have [FONT=courier new]<-there[/FONT] in a comment like this [FONT=courier new]/* <- There */[/FONT]

---

### Post by catlover48856 on 2013-08-02
Is there any other way to create a box around text then?

---

### Post by pqwoerituytrueiwoq on 2013-08-02
you mean a border? around a element that contains text?
```
<span style="border: 5px solid blue;border-radius:3px">Hello World</span>
```

---

### Post by catlover48856 on 2013-08-02
Closer... but I need to fill that box so I can see the text aginst the background. So it stands out.

---

### Post by pqwoerituytrueiwoq on 2013-08-02
apply a background color then or go fancy with a text shadow
you can use the background color of rgba(0,0,0,.65)
*IE9 and below do not support text shadow
*IE8 and below do not support rgba, a workaround is a small png background of a rgba color

if you can give me a drawing  or a edited screen-shot of what you want i can give you css to do it

---

### Post by catlover48856 on 2013-08-03
Here Is a pic. Once you see the background you'll know why I need box.[ATTACH=CONFIG]245047[/ATTACH]

---

### Post by pqwoerituytrueiwoq on 2013-08-03
You know there is a easier way right
[http://pastebin.com/KADV9jYP](http://pastebin.com/KADV9jYP)
here is a sample html file you can work with
enjoy the [COLOR=#1F0BDF]fa[/COLOR][COLOR=#3F09BF]b[/COLOR][COLOR=#5F089F]u[/COLOR][COLOR=#7F067F]l[/COLOR][COLOR=#9F045F]o[/COLOR][COLOR=#BF033F]u[/COLOR][COLOR=#DF011F]s[/COLOR] background image

---

