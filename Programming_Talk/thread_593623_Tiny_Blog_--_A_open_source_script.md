---
title: "Tiny Blog -- A open source script"
date: 2007-10-27
forum: Programming Talk
---

### Post by 7Priest7 on 2007-10-27
No Code For Ubuntu Forums

---

### Post by 7Priest7 on 2007-10-27
I forgot 

[http://poeticpriest.gigacities.net/](http://poeticpriest.gigacities.net/)

That is it at work...

Please dont read post/page 9 as I am afraid it might offend some


Alex

---

### Post by smartbei on 2007-10-27
Check out page 7...
> You did not like my \"Innocent!\" poem!...

Also on page 5...
> Now they\'re a wreck...
Looks like you need to insert a stripslashes in there somewhere.

It also looks like you are banning after a single try at the password. It might make more sense to let them have three or four.

I would also recommend replacing 
> 
{password}
{secret directory}
{your website}
{your name}

With something like: (so that you would only need to change one place in the code).
[php]
define("PASSWORD","<user password>");
define("SECRET_DIRECTORY","<secret directory>");
//...
[/php]

---

### Post by 7Priest7 on 2007-10-27
I had noticed it before...
For me it was fine...

Since I decieded to publish my code I fixed it...

"Give the people what they want"

Enjoy :)


Alex

---

### Post by 7Priest7 on 2007-10-27
I could add the multiple tries...
I however would have no use...
I can delete my IP if I screw up which I ushually don't...

Those replacings those are for the person using my code...

My website has all the replacings done...

If the coder is too lazy to replace a few things then maybe they should not be in web develepment...

I would use find and replace tool...


Thanks for the ideas... :)


Alex

---

### Post by smartbei on 2007-10-27
I understand what you mean. Don't take my post as negative criticism of your mini-blog, it is meant in a positive note for whoever may wish to use the code, if they want to implement the changes.

(Yes, I know the owner of the blog can just remove the ip, but it is less conveniant)

(Yes, I know you would use find and replace to replace everything, but again, it would be more conveniant)

Anyway, thanks for posting this here, and sharing the code.

---

### Post by aks44 on 2007-10-27
Just curious: how come I only get blank pages whenever I click on a post number (the "front page" is displayed correctly)? :-\"

EDIT: lol nevermind, I just tried again and now it works... have you been fiddling with your server? :p

---

### Post by 7Priest7 on 2007-10-27
Yea I was fiddling with it...

When I added the stripslashes I accidently replaced my directory with the {secret directory}


Anyhow thanks :)


Alex

---

### Post by 7Priest7 on 2007-10-27
From what I know about google it will only index a directory if there is a link to it...
So ideally google will not see your directory...
It is however a possibility...
Also, you can polish it...
Add some css...
for me it is about the content and not the means...

Just a few tips :)


Alex

---

### Post by 7Priest7 on 2007-10-28
I added two more posts to the working blog
[http://poeticpriest.gigacities.net/](http://poeticpriest.gigacities.net/)
Now you can see how the line breaks work...

Enjoy :)


Alex

---

### Post by 7Priest7 on 2007-10-28
I added the ability to edit...
That is a very usefull feature..

Enjoy :)


Alex

---

### Post by LaRoza on 2007-10-28
<snip />

---

### Post by 7Priest7 on 2007-10-28
> **LaRoza said:**
> The code is invalid. The HTML has no root element, or two?

Your question makes little sense...

What code segment is invalid?

Yea It may not be valid html but I am not worryed


Thank You

Alex

EDIT: One Root element
[http://www.poeticpriest.gigacities.net/](http://www.poeticpriest.gigacities.net/)

It all works :)

---

### Post by LaRoza on 2007-10-28
<snip />

---

### Post by 7Priest7 on 2007-10-28
I know
Fact is
I could care less about having valid Html

W3C is too picky and they constantly change things...

I don't have the time to be a conformist

[http://www.8tt.org/](http://www.8tt.org/)  (Good host short subdomain... You can use it to host this)
[http://www.gigacities.net/](http://www.gigacities.net/) (Great host large subdomain... You can use it to host)

Those two hosts have huge space and bandwidth they allow the most expansion...


Enjoy :)


Alex

---

### Post by LaRoza on 2007-10-28
<snip />

---

### Post by 7Priest7 on 2007-10-28
[http://browsershots.org/http://poeticpriest.gigacities.net/](http://browsershots.org/http://poeticpriest.gigacities.net/)

Heh

Heh If you want my code and you want valid HTML Fix it yourself...

Like I said... I designed this for me...

I am nice enough to share it...

Do you share your subpar codes?


Alex

---

### Post by LaRoza on 2007-10-28
<snip />

---

### Post by aks44 on 2007-10-28
> **7Priest7 said:**
> <snip>
Heh If you want my code and you want valid HTML Fix it yourself...

Like I said... I designed this for me...

I am nice enough to share it...


And LaRoza is nice enough to give you advices about decent programming practices.

I guess that before trying to help you with programming stuff, we should teach you how to behave.

*plonk*

---

### Post by LaRoza on 2007-10-28
<snip />

---

### Post by 7Priest7 on 2007-10-28
[http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F%3Fpage%3D1](http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F%3Fpage%3D1)

Ehh I am working on it...

I will upload it once all pages generate valid HTML


:)


Alex

---

### Post by 7Priest7 on 2007-10-28
[http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F&charset=%28detect+automatically%29&doctype=Inline&group=0)
[http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F%3Fpage%3D1](http://validator.w3.org/check?uri=http%3A%2F%2Fpoeticpriest.gigacities.net%2F%3Fpage%3D1)

All Valid HTML

I uploaded the newest version of Tiny Blog


Alex

---

### Post by 7Priest7 on 2007-11-02
Heh for the fun of it...
```

192.12.81.1
217.132.81.14
24.164.83.236
24.46.23.208
71.181.228.232
71.195.113.203

```
^ The IPs that have tried and failed to hack my blog

:)

Alex

---

### Post by ZuLuuuuuu on 2007-11-03
I liked the idea, I am also a minimalist :)

---

### Post by 7Priest7 on 2007-11-03
> **ZuLuuuuuu said:**
> I liked the idea, I am also a minimalist :)

Thanks...

I don't like things like blogspot...

Too Graphical...

I have dialup...

Sometimes I use LYNX...

My Blog gets indexed so people can hear me... that is all I want...

:)


Alex

---

### Post by 7Priest7 on 2007-11-07
I added autofill...
It will give a more clean design for up to 999 posts...

I personally have never posted on anything more than 300 times...

Anyhow It will still work with your current blog implementation (if you have one)

Enjoy :)

Alex

---

### Post by 7Priest7 on 2007-11-17
I put all the links in a table...
In my opinion it makes it look better...

Enjoy :)

Alex

---

