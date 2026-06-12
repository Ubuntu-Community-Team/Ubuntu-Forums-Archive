---
title: "Bluefish editor Ubuntu"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Muhammad Ahmed on 2011-09-28
I am using bluefish editor on ubuntu and experiencing a problem and just dont understand it...i wrote in it





<br /><br /><br /><br /><font size="5"><u><font face="ubuntu">Technical Skills:</u><br />

The problem is it is showing it as bold , i have not set any basefont tag also im a beginner so please help.Before this i have some text on the page in bold and now everything i write comes in BOLD please help....I dont think its the app fault

---

### Post by ewz on 2011-09-28
Hiya I'm at work so I cant test it in Bluefish yet 

Have you tested the page in a few different browsers to see if its a rendering issue? 
also you could check your doctype, 

I pasted it into notepad using XHTML 1.0 Transitional
and looks fine to me, im on a Windows Client at the moment though.

I haven't used Blufis for sometime it tended to be a bit outdated, I have been using Komodo Edit and its great :-) 

sorry I can't be of more help, if still you can't figure it out I will try it when I get home :-)

opps Thought I would mention some of your html tags are depreciated, though they still should work how they are suppose to. eg: the u tag, font size, font face. but as I said they still should work they way they are suppose to.

---

### Post by scruffyeagle on 2011-09-28
> **Muhammad Ahmed said:**
> I am using bluefish editor on ubuntu and experiencing a problem and just dont understand it...i wrote in it

<br /><br /><br /><br /><font size="5"><u><font face="ubuntu">Technical Skills:</u><br />

The problem is it is showing it as bold , i have not set any basefont tag also im a beginner so please help.Before this i have some text on the page in bold and now everything i write comes in BOLD please help....I dont think its the app fault

I haven't done any HTML yet under Linux/Ubuntu/Gnome. I've installed, but haven't actually used Bluefish, although I'm bound to at some point. My thought of the moment is that the browser is getting default font info from somewhere, and that's why it's all showing up as bold. Perhaps if you specify a basefont, it would become the default for the page?

---

### Post by ewz on 2011-09-29
Hi I re did your code using CSS which is the preferred way these days 
also I noticed you are using the Ubuntu font, only Ubuntu distros and maybe a few others have that font installed, if you want people other than Ubuntu uses to see that font you need to use google web fonts to link the font to your website have a look here: [http://www.google.com/webfonts#HomePlace:home](http://www.google.com/webfonts#HomePlace:home)

also have a look at this site: [http://www.w3schools.com/](http://www.w3schools.com/)  it's a great resource for building websites :-) 

Sample Code: there are other ways to add CSS to webpages this is just one using div tags 

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title><!-- Insert your title here --></title>
    <link href='http://fonts.googleapis.com/css?family=Ubuntu' rel='stylesheet' type='text/css'>
    <style type="text/css">
    body{
     font-family: 'Ubuntu', sans-serif;
    }
    #title{
        text-decoration: underline;
        font-size: 24px;
    }
</style>
</head>
<body>
    <div id="title">
    <br /><br /><br /><br /><p>Technical Skills:</p>
    </div>
</body>
</html>

---

### Post by AlexDudko on 2011-09-29
Search your code for an opening ```
<b>
``` tag and for a closing one - ```
</b>
```
If there's no closing one all text, which follows the opening tag will be bold.

---

### Post by scruffyeagle on 2011-10-14
That's a good suggestion about making sure all <b> tags have corresponding </b> closers. I've made that mistake in the past, and discovered I'd made that particular error, after 15 or 20 minutes of scouring code.

For EVERY <b>, there should be a </b>.
If you count all the "<b>" tags, then count all the </b> tags, the numbers should be equal. If they're not, then you just need to discover which one didn't get its closer.

---

