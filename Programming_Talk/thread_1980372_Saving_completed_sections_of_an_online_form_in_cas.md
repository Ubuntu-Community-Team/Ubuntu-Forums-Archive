---
title: "Saving completed sections of an online form in case of disconnect"
date: 2012-05-15
forum: Programming Talk
---

### Post by hanzj on 2012-05-15
We'd like to get an online form on our website to save the completed sections/pages, just in case the visitor somehow disonnects. 

The online form is very lengthy (about 80 questions), and we wouldn't want our visitors to have to start from the beginning if he gets disconnected.


How do we do make this happen?

P.S. I know no coding at all. The extent of my coding is <img src>, <b>, <i>.

---

### Post by roelforg on 2012-05-15
Add some javascript to store/load values to/from cookies as the field gets changed.
Erase the cookies on submit, worst case: One field has to be redone (assuming cookies aren't disabled).

---

### Post by hanzj on 2012-05-15
Roelforg, thanks for your reply.

I added something into my OP: I don't know how to code, but as a Ubuntu user and a grateful UbuntuForums member, I'm willing to copy and paste code. 

You mentioned javascript. Are there javascript files that are ready to be used?

---

### Post by roelforg on 2012-05-15
> **hanzj said:**
> Roelforg, thanks for your reply.
 
I added something into my OP: I don't know how to code, but as a Ubuntu user and a grateful UbuntuForums member, I'm willing to copy and paste code. 
 
You mentioned javascript. Are there javascript files that are ready to be used?
 
[http://www.websitemaken.be/index.php?page=show_item&topic=2](http://www.websitemaken.be/index.php?page=show_item&topic=2)
It's dutch, but explaines everything very well. (google translate will aid you)

---

### Post by hanzj on 2012-05-15
The whole site looks like it's about javascript. Is there a page from that that site that would be particularly helpful?

---

### Post by nothingspecial on 2012-05-15
*Thread moved to **Programming Talk**.*

---

### Post by roelforg on 2012-05-15
> **hanzj said:**
> The whole site looks like it's about javascript. Is there a page from that that site that would be particularly helpful?
 
The general tut and the one about cookies.

---

### Post by hanzj on 2012-05-15
I'm afraid JavaScript would be too complicated for me to learn. Are there some ready-made JS files out there. 
I'm almost certain I'm not the first person who wanted to save online forms.

---

### Post by roelforg on 2012-05-15
> **hanzj said:**
> I'm afraid JavaScript would be too complicated for me to learn. Are there some ready-made JS files out there. 
I'm almost certain I'm not the first person who wanted to save online forms.
 
It's not complex, just take the time to read the tut, it explains exactly how stuf works.
 
I'll give you some hints, use this AFTER reading the tut:
onchange="jscode"
 
And there are no "ready-made js files" because every formlayout is different.
It should take you about one evening to get the hang of js, though.

---

### Post by ofnuts on 2012-05-15
> **hanzj said:**
> We'd like to get an online form on our website to save the completed sections/pages, just in case the visitor somehow disonnects. 

The online form is very lengthy (about 80 questions), and we wouldn't want our visitors to have to start from the beginning if he gets disconnected.


How do we do make this happen?

P.S. I know no coding at all. The extent of my coding is <img src>, <b>, <i>.One obvious solution is to split your form into several pages, which may be better for human factors.

Otherwise you can use AJAX to send to your sever the answer to every question in almost real-time (triggered by "onclick"), so the final submit button becomes a "confirm whatever you have in store".

---

### Post by hanzj on 2012-05-15
Ofnuts. Thanks for your reply.

> **ofnuts said:**
> One obvious solution is to split your form into several pages, which may be better for human factors.

Yes, good idea. We were indeed planning on creating a multipage form. 

With the  multipage form we had in mind:
--The person must begin in page 1
--The person cannot do page 2 or 3 by just clicking a link. Our online questionnaire uses conditional logic. The questions in future pages will depend on answers given on previous pages.


> **ofnuts said:**
> Otherwise you can use AJAX to send to your sever the answer to every question in almost real-time (triggered by "onclick"), so the final submit button becomes a "confirm whatever you have in store".
What happens when the person finishes page 1, is now working on the second page, and the computer loses power? Will he be able to resume work on page 2?

---

### Post by ofnuts on 2012-05-15
> **hanzj said:**
> Ofnuts. Thanks for your reply.



Yes, good idea. We were indeed planning on creating a multipage form. 

With the  multipage form we had in mind:
--The person must begin in page 1
--The person cannot do page 2 or 3 by just clicking a link. Our online questionnaire uses conditional logic. The questions in future pages will depend on answers given on previous pages.

Makes it all the more useful to have it split over several pages, so that different users see different pages.


> **hanzj said:**
> 
What happens when the person finishes page 1, is now working on the second page, and the computer loses power? Will he be able to resume work on page 2?One the single-page questionnaire, you just prefill the page with the answers you already have. In a multi page questionnaire you can serve the first page where there are missing answers, prefilled with those you already have... Actually your "next" button on a page should really be "go to first page with missing answers". When a page is completely answered, this goes to the next.

---

### Post by SeijiSensei on 2012-05-15
What you want to do requires some serious backend programming, probably using something like PHP, session cookies, and a database. I've built just the type of system you describe.  I put the answers from each intermediate page in a database and give the person a reasonably long-lived session cookie to identify his or her individual record upon return from a disconnection.  If your organization is serious about doing this, hire someone who knows how to program.  

The other thing you could consider is a pre-built survey package.  Do a Google search for "php survey software" to see some options.

---

