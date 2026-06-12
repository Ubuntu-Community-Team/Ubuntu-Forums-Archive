---
title: "HTML read difference between Windows, Mac OS, and Ubuntu"
date: 2007-04-04
forum: Programming Talk
---

### Post by kvk on 2007-04-04
Hi folks~

I run a small website, and have recently switched to Ubuntu from Windows. The website platform with the host is Windows, and I write the pages in .asp. I notice that when the site is brought up in Ubuntu, the text colors, fonts, and some of the spacings on pages are different, all of which make things hard to read.

I need to fix this! Any ideas why this might be so and how to correct it?

Thanks so much!

---

### Post by Mirrorball on 2007-04-05
Post the address here and I'll have a look at it.

---

### Post by ibanezix on 2007-04-05
I think the difference is not between Operating Systems (Windows, MacOS, Ubuntu) but between browsers (Internet Explorer, Firefox, Opera, etc.) as each browser has its own way to interpret the code that you write. I also run the website of the company I work for, and making it appear the same in all browsers was a real pain.

Many websites appear differently in different browsers and some (even some of big companies/organisations) are unreadable in anything else than IE, which is quite irritating for users of other browsers, but I cannot say I don't understand the habit of web developers to only check their pages in IE, as it has the greatest market share. 

My suggestion is to check your site in IE, Opera, Firefox and Safari (at least) in order to make sure that it is at least usable in all. Until the day that all browsers and all developers comply to standards, that is.

---

### Post by kvk on 2007-04-05
Thanks for the replies. Yes, it makes sense that the browser is the critical piece of the puzzle. I'll have to get Safari and Opera and check it in those as well, and then see how I can modify it to be at least decent in all of them. Given my rudimentary html, this will be interesting!

The site is [www.krayvankirk.com;](www.krayvankirk.com;) I appreciate you taking a peek at it, Mirror! 

Thanks!

---

### Post by ssam on 2007-04-05
if a page is written in valid HTML then it has a better chance of looking the same on modern browsers.

[http://validator.w3.org/check?uri=http%3A%2F%2Fwww.krayvankirk.com%2Fhome.asp&charset=%28detect+automatically%29&doctype=Inline](http://validator.w3.org/check?uri=http%3A%2F%2Fwww.krayvankirk.com%2Fhome.asp&charset=%28detect+automatically%29&doctype=Inline)

gives 20 errors

---

### Post by LaRoza on 2007-04-05
If you use CSS, test your pages in different versions of the same browser. One of my pages looks great in IE7 but is a mess in IE6, because of the lack of support for CSS2 properties.

Always validate also, Firefox has an add-on you can use called "Web Developer" which has many useful tools, including a validator, or rather a link to one, W3's.

---

### Post by kvk on 2007-04-05
What a great tool! I can learn a ton from that, provided I can understand the analyses.

Thanks for the help! I really appreciate it.

KVK

---

### Post by Mirrorball on 2007-04-05
> **kvk said:**
> I run a small website, and have recently switched to Ubuntu from Windows. The website platform with the host is Windows, and I write the pages in .asp. I notice that when the site is brought up in Ubuntu, the text colors, fonts, and some of the spacings on pages are different, all of which make things hard to read.
Which page needs fixing? I think all of them are OK. Maybe they look different in IE, but a page doesn't have to look identical in all browsers. Try to make them look the same in lynx. ;)
By the way, here is a great article if you want to improve your web designer skills:
[http://www.456bereastreet.com/lab/developing_with_web_standards/](http://www.456bereastreet.com/lab/developing_with_web_standards/)

---

### Post by kvk on 2007-04-05
Thanks for the link! it looks really good.

Hopefully I can sit down and read it through this weekend and get everything straightened out in the CSS and then remove all the little band-aids I've got stuck into all the pages. It's really not complex at all for anyone who knows what they're doing- I'm just stumbling my way through it all.

KVK

---

