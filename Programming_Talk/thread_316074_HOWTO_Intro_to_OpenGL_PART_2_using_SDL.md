---
title: "HOWTO: Intro to OpenGL PART 2 using SDL"
date: 2006-12-10
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-12-10
Hi

We've just published a new HOWTO on The Ubuntu Games Developer Resource Wiki

Heres the link:
[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Another great Howto By Wybiral! Well done!

Mike

---

### Post by hod139 on 2006-12-10
Look awesome.  Some comments,
You use the term mipmapping without any explanation of what it does.  You can probably just say something like (or just provide a link to wikipedia :) ): A mipmap stores several reduced versions of the texture along with the original.  This collection of images requires more memory but reduces rendering artifacts. Mipmapping uses the lower resolution versions of the texture when objects are far away and do not require full detail, and can switch to the largest version only when needed.

You stated that the texture sizes have to be a power of two, but don't they also have to be square?  i.e. 512x512 is fine, but 512x256 is not.  I could be wrong I don't remember.  I think all of these restrictions are going away in OpenGL 2.0 anyways.

---

### Post by Wybiral on 2006-12-10
I actually thought about linking to wikipedia (but I kind of don't like those guys). Anyway, you're right, there should be some explanation on there. But I think if they run into it confused, they will probably look it up on wikipedia anyway. So, later today I might add in a small explanation. Thanks for the constructive criticism hod!

(I've been able to use non-square images in textures, so I think its OK as long as each dimension is a power of two)

---

### Post by hod139 on 2006-12-10
> **Wybiral said:**
> I actually thought about linking to wikipedia (but I kind of don't like those guys). 
Agreed, I don't like linking to them but I don't know of a free beginner level OpenGL resource on the web.  Everything I know is for advanced programming.

> 
(I've been able to use non-square images in textures, so I think its OK as long as each dimension is a power of two)I wasn't sure about this so I just tried it, and you are correct, as long each each dimension is a power of 2 it worked.  

What's really strange is I tried loading a texture with funny non-power of two dimensions, and it kinda worked.  The framerate however effectively went to zero, so I'm not sure what is going on.

---

### Post by pmasiar on 2006-12-10
> **hod139 said:**
> I don't like linking to them... 

Very strange for me. Wikipedia is for me first source when researching almost anything, never failed, and often I learned more. I always considered wikipedia a great success of sharing free  information, like free code.

So I am just curious, why you don't like linking to wikipedia? Is it some bad experience you had? Do you guys care to explain?

---

### Post by Wybiral on 2006-12-10
Its hard to explain... I don't have a problem with wikipedia, just a lot of the people that manage the articles. I don't want to put them down, but I'll just say that they are very hypocritical about the kinds of articles they will allow.

---

### Post by Mickeysofine1972 on 2006-12-10
Thats cool that we discovered the texture dimension thing!

We all learn together!

Mike

---

### Post by hod139 on 2006-12-10
> **pmasiar said:**
> Very strange for me. Wikipedia is for me first source when researching almost anything, never failed, and often I learned more. I always considered wikipedia a great success of sharing free  information, like free code.

So I am just curious, why you don't like linking to wikipedia? Is it some bad experience you had? Do you guys care to explain?

My reasoning is different than Wybiral's.  I guess I think wikipedia is fine for finding some quick information and hopefully some more external references, but the problem is that you can't trust anything written.  Nothing is reviewed, anyone can post anything even on topics they are not experts in.  For example, in graphics some definitive resources for information are [siggraph]("http://www.siggraph.org/"), [opengl]("http://www.opengl.org/"), and of course a [good book]("http://www.opengl.org/documentation/books/"). The blue and red books are really good, however not for beginners.  A good beginner book I can recommend is  "[Computer Graphics with OpenGL" by Hearn and Baker.]("http://www.amazon.com/exec/obidos/ASIN/0130153907/ref=nosim/openglorg")

I would never suggest someone attempt to learn something from wikipedia.  Use it to get a general idea and then find a reviewed/trusted resource.  In my opinion books are still the best way to learn.  Another thing you can do is use google to search for class notes from professors.  Google lets you search for a specific file type (like powerpoint or pdf) and sometimes class notes/lectures are easier to learn from than a book.

---

### Post by pmasiar on 2006-12-10
> **hod139 said:**
> I guess I think wikipedia is fine for finding some quick information and hopefully some more external references, but the problem is that you can't trust anything written.  Nothing is reviewed, anyone can post anything even on topics they are not experts in.

I beg to disagree. This is same bogus FUD used against Linux: "anybody can commit anything". Every change on every page is checked by people who care. You can easily add your comments about the books you mentioned, and add other links as you see fit. Within minutes, other people will check your change, and revert them, if it is wrong. It happened to me couple times: some changes I made were accepted, some were reverted. After thinking, I agree that reverted changes were not as appropriate than accepted. 

If you see something missing in wikipedia, fix it. As I see it, it is exactly as complaining about open source programs: If some feature is missing, a bug hurts you badly, go fix it. Wikipedia is even easier to fix. :-)

If you are interested, I can find you wikipedia discussion about this subject :-) so we don't need to repeat FAQ-type discussion.

>  I would never suggest someone attempt to learn something from wikipedia.  Use it to get a general idea and then find a reviewed/trusted resource.  In my opinion books are still the best way to learn.  Another thing you can do is use google to search for class notes from professors.  Google lets you search for a specific file type (like powerpoint or pdf) and sometimes class notes/lectures are easier to learn from than a book.

So we basically agree. Get general idea about the area of knowledge from wikipedia, and follow the links provided. 

And let me add: if you know about other better links, just edit wikipedia page and add them. For me, wikipedia is also *my own* repository of good links *I* found, shared with other people interested in some subject.

Really: make changes you suggested, and lets see tomorrow what will happen to them.

---

### Post by Wybiral on 2006-12-10
But, there are also a lot of people on wikipedia who feel their opinion is better than yours and will change it anyway, even if they are wrong / misinformed. This has also happened to me a number of times. I am in no way saying that wikipedia is bad, just that like all walks of life, there are people who choose to do obnoxious things. There are also little "clicks" on wikipedia that will team up on subjects that disagree with their opinion, I know this sounds ridiculous, but it has happened to quite a few times.

One example is with programming languages, I have added a number of articles on languages I like, and a number of them were deleted by people who were die-hard users of those languages competitors (for all I know, the people who are keeping up the other languages articles). If a group of people find an article they don't like and pend it to be deleted, if no one else sees it and sticks up for it, its gone. This doesn't seem like a fair or very "wiki" style of doing things. Especially when it happens multiple times. It seems like a monopolistic way of doing things to me!

But, this is just my opinion, and my experiences, I am not putting down wikipedia as a whole, just a lot of the people who use it.

---

### Post by pmasiar on 2006-12-10
> **Wybiral said:**
> I have added a number of articles on languages I like, and a number of them were deleted by people who were die-hard users of those languages competitors 

Looks like you are a victim bystander of raging [editwar]("http://en.wikipedia.org/wiki/WP:EDITWAR"). You should make your case at the talk page. Then again, people who care more, who are more persistent, will win. Or you can insist to have different opinion mentioned: if it is not freak argument, it will be accepted.

Big difference between a forum like this, and a wiki is: on wiki, you have to compromise, you cannot care about your ego, about exact wording. Wiki is egoless editing. For some usage, wiki is preferable: wiki eliminates all the cruft, misunderstanding and 
off-topic debates (like this one) and puts discussion in proper context. Say, how anyone interested in wikis but not following this thread would ever find out this discussion? :-) 

On forums also anyone can give advice, and some advice is bad. Same as in wiki.

---

### Post by Wybiral on 2006-12-10
I agree, but I've had entire articles deleted for nonsensical reasons, and I don't really feel the need to continue to rewrite them, so you are absolutely right, but given this kind of behavior wikipedia will have a hard to representing a full non-bias view on things and in a forum, the info may be incorrect, but people can always reply with the correct info, on the wiki, if the info was correct to begin with, someone can simply undo all of the hard work that person put into writing it.

---

### Post by pmasiar on 2006-12-10
in most wikis, and also in wikipedia, anyone can revert a change. So if you care, and someone reverted your change, you can make it back, another revert will trigger page lock and discussion. Some pages (like Bush's biography) are permanently locked and only trusted parties can update them.

Well again you can say about cliques etc. Of course, anonymity allows for that. There was digg mafia upvoting posts of their members. On internet, nobody can tell that you are a dog. ;-)

Same history as in operating systems (Linux versus windows) repeats in encyclopedias: wikipedia versus Encyclopedia Britannica. It has 4 stages: first, they ignore you. Then they ridicule you. Then they fight you. Then you win.

Now, wikipedia is in stage 2. :-)

If you want to know more about wiki way, you may be interested in  website of inventor of concept of wiki, Ward Cunningham: [original wiki]("http://www.c2.com/cgi/wiki?WelcomeVisitors"). You can see from domain (C2) Ward is on the internet for a long time. Nowadays, such a short domain name can cost a million.

---

### Post by hod139 on 2006-12-10
> **pmasiar said:**
> Some pages (like Bush's biography) are permanently locked and only trusted parties can update them.

If you want to know more about wiki way, you may be interested in  website of inventor of concept of wiki, Ward Cunningham: [original wiki]("http://www.c2.com/cgi/wiki?WelcomeVisitors"). You can see from domain (C2) Ward is on the internet for a long time. Nowadays, such a short domain name can cost a million.

I see a problem with your argument here.  First you are saying that the wiki way is the greatest thing since slice bread, but then you say certain pages are permanently locked, which is very anti-wiki.  I think you just highlighted exactly my problem with wikipedia, that there is nothing preventing edits from ignorant, fanatic, racial, agitating, etc people.  Sure the pages can be reverted, but the problem doesn't go away.  I might be viewing the page with the false information is presented.  This is a problem they are aware of and trying to resolve with new methods, like locking pages only "editorial" staff can alter, not allow new anonymous accounts to edit certain pages, etc.  They also have legions of editors constantly scouring the pages looking for problems.

I have no problems with wikipedia, I think it is an awesome tool and I use it many times.  I will never cite it in a paper (unless its a paper about wikipedia) and neither will anyone else in academia because of the untrustworthiness.  This is why there are peer reviewed conferences and journals.  The review process by fellow experts in the field is suppose to (even this process can be fooled sometimes) grant a level of trust and correctness in these journal publications.  My biggest problem with this approach is that for students not in college getting access to these journals and conference proceedings is almost impossible since subscriptions are very expensive.  This is where I think wikipedia fills a much needed gap.

**Edit:** How did an SDL thread turn into a discussion on wikipedia anyway?  Also, you will notice I am not comparing wikipedia to encyclopaedia britannica, I am comparing it to peer reviewed journals.  Wikipedia will never replace these.  However, a peer reviewed wiki would be awesome in my opinion, since all the information hidden in these journals should IMO be public knowledge.

---

### Post by pmasiar on 2006-12-10
> **hod139 said:**
> First you are saying that the wiki way is the greatest thing since slice bread, but then you say certain pages are permanently locked, which is very anti-wiki.

...and I anticipated this question and attempted an answer, but you snipped it out from your quote. Even  in 100% failproof system like forum :-), things can go wrong. :-D

We agree that wiki is good enough for 95% of the use, IMHO. It is the same 95% confidence rate we have in scientific articles. :-) We all know that about one of 20 published articles, peer reviewed by top academia, might still bogus and wrong, but we just pretend it is not happening right?

"Perfect" should not be enemy of "good enough".

> How did an SDL thread turn into a discussion on wikipedia anyway?  

I tried to change title and mark it off-topic, but have no idea how to split a thread. Can we ask moderators to split this discussion as separate thread, so more people can comment? But then again it will be in another forum, and I follow only this one. :-) I should just start new thread, mentioning it in the short answer. :-( Will do next time, I promise. 

> However, a peer reviewed wiki would be awesome in my opinion, since all the information hidden in these journals should IMO be public knowledge.

Wikipedia might be your "peer reviewed wiki". It depends on your definition of "peer". :-)

I agree that it is ridiculous: research financed by public money is hidden in private journals, and schools have to pay loads of money to get the content, created with public funds. How much simpler would be to create a wiki, where anyone can publish article for say $5 and $1 yearly maintenance fee (or even have ads to support yearly maintenance) and peers can comment on it. It will not be anonymous of course: PGP signed articles and comments only.

Hey, someone was looking for a python project recently - here is an idea for free! :-)

---

### Post by hod139 on 2006-12-10
> **pmasiar said:**
> 
We all know that about one of 20 published articles, peer reviewed by top academia, might still bogus and wrong, but we just pretend it is not happening right?


 Where did you get this statistic?  Seeing as I'm currently a graduate student involved in these reviews that hits pretty close to home.  I really doubt 1 in 20 is bogus.

---

### Post by pmasiar on 2006-12-10
I started [new thread about wikipedia]("http://ubuntuforums.org/showthread.php?t=316547"), lets continue there.

---

