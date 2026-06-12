---
title: "Windows Fonts"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by ceil210 on 2012-02-26
My website uses a monospace font.  It shows up just fine on my Windows partition, but on Ubuntu it is all smushed and skewed.  Is there a package that installs Windows fonts so it looks better?  My forum's font is messsed up as well!  Please help me :(

---

### Post by wojox on 2012-02-26
```
sudo apt-get update; sudo apt-get install ubuntu-restricted-extras
```
Should work.

---

### Post by ceil210 on 2012-02-26
It didn't work.  Here is a screen shot of what I mean.

 [http://nerblog.net/fonts.png](http://nerblog.net/fonts.png)

---

### Post by pootan on 2012-02-27
When I go to nerblog.net I see exactly what is in your screenshot. 




Try this:

```
sudo apt-get install msttcorefonts
```
**

---

### Post by ahiung on 2012-02-27
I visited you blog, too. It seems the font is in normal mode instead of BOLD one from your screenshot.
Is the Non-BOLD your original font?

---

### Post by ceil210 on 2012-02-27
When I run:

```
sudo apt-get install msttcorefonts
```
I get:

```
uilding dependency tree       
Reading state information... Done
Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
ttf-mscorefonts-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
agardner@ubuntu:~$ 
```

---

### Post by MG&amp;TL on 2012-02-27
msttfcorefonts is part of ubuntu-restricted-extras, methinks. Do you have to set it in your browser?

---

### Post by HeroOfCanton on 2012-02-27
> **ceil210 said:**
> My website uses a monospace font.  It shows up just fine on my Windows partition, but on Ubuntu it is all smushed and skewed.  Is there a package that installs Windows fonts so it looks better?  My forum's font is messsed up as well!  Please help me :(

What font declaration are you using in your CSS? Your readers are not going to download a font to see the site correctly! You should really fix this on your website, not on the computer you are using.

[http://www.w3schools.com/css/css_text.asp](http://www.w3schools.com/css/css_text.asp)

---

### Post by ceil210 on 2012-02-27
In my CSS I have "font:monospace;"

> msttfcorefonts is part of ubuntu-restricted-extras, methinks. Do you have to set it in your browser?
how??

---

### Post by HeroOfCanton on 2012-02-27
> **ceil210 said:**
> In my CSS I have "font:monospace;"

That will create a very generic output leaving the selection of the text to the browser. You should try to be more specific with a font-family declaration like:

```
font-family:"Courier New", Courier, monospace
```[http://www.w3schools.com/cssref/pr_font_font-family.asp](http://www.w3schools.com/cssref/pr_font_font-family.asp)

---

### Post by MG&amp;TL on 2012-02-27
> **ceil210 said:**
> In my CSS I have "font:monospace;"


how??

I was actually asking the question-it wasn't rhetorical. :) Probably not, doing some gogling.

---

### Post by Simian Man on 2012-02-27
The font doesn't look bad to me in the browser or in your screenshot.  What does it look like on Windows?

---

### Post by forrestcupp on 2012-02-27
If you have access to your Windows fonts, you can create a folder named **.fonts** in your /home folder, and copy all of your Windows ttf files to it. If you do that, it may show up how you want it to.

---

### Post by grahammechanical on 2012-02-27
You can search the Ubuntu Software Centre for ttf-mscorefonts-installer.

Install the installer and it will install the Microsoft fonts but you have to accept the MS user agreement for the download to take place.

Another point to consider, most people accessing the Internet will have Microsoft fonts installed. But not all Linux users will have them installed. In this case the browser makes a substitution which may not be a very good choice, as you have seen.

You can use CSS to offer a better alternative. Such as

> font-family: FreeSans, frutiger linotype, arial;

If the browser does not find the first font it will look for the second and then third in the list.

This will give you better control over what your visitors see.

Regards.

---

