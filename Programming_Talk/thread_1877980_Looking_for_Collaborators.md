---
title: "Looking for Collaborators"
date: 2011-11-09
forum: Programming Talk
---

### Post by jmadero on 2011-11-09
This is a double post so I hope this doesn't violate forum rules (someone in the community cafe told me I might want to post here as well). Here's a link to the discussion happening, hoping to get person/people together in the next few days to start the brainstorming. Thanks

[http://ubuntuforums.org/showthread.php?t=1877727](http://ubuntuforums.org/showthread.php?t=1877727)

---

### Post by Smart Viking on 2011-11-09
I'd be willing to share technical knowledge about Python, if that's the language you chose to use.

---

### Post by Drenriza on 2011-11-09
I'm also new to programming, but would like to learn. Where i have spent most of my time in C#. But if a slot is open, im up for it.

---

### Post by 11jmb on 2011-11-09
I don't have time to be a full-time developer or anything, but I can provide some guidance if you would like. 

First of all, I recommend clearly defining your problem. "debt management" is not nearly enough. You need to start thinking about use cases: Who is going to use this and for what?

Do you have accounting experience? somebody on the project should. 

Once you have use cases that are detailed and clearly defined, then you can move forward.

Also, I recommend getting a basic website as kind of a "home base" for collaboration. Something simple like blogspot might be a good start

Good luck :D

---

### Post by jmadero on 2011-11-09
For those of you with technical knowledge I'm hearing python is the way to go, I have no experience in python but am willing to go that route if it's equal to or better than C++ (I've always been told C++ has a lot of benefits of Python including speed and compatibility with different distros/OS's.

As for other comments, anyone who is truly interested please message me and I'll get you my email address so we can start an IRC chat soon to discuss the project.

I do have a pretty detailed idea of what I want the debt management program to look like and what functionality I want it to have (ie. 11jmb I think I have your concern covered at least for the first few phases). 

I wrote over on the other forum entry that the first phase will be similar to Chase Blueprint. The basic idea is that the user can enter into a ledger credit card expenditures and along with it you can edit the # of payments you want to take to pay off each individual item (you can create groups so it'll auto set "monthly expenditures" to 1 payment in order to save on interest while setting larger items to multiple payments -- ie you buy a computer and you want to have it paid off in 12 months). This is definitely the first thing I want the program to do, beyond this I have more ideas but would want to tackle one thing at a time. 

I can get a basic website up but wanted to see if I could get a few people to agree to help first, even if it's just joining a mailing list to put in feedback or contribute a little code/check code/anything really. Lastly, I have a background in economics/math and also have a Masters in Public Admin where I focused on Public Finances so I think I can handle the math aspect of it (but would like to discuss programming techniques to see if someone has better ideas).

PM me if you're interested, really a long term project that I expect to be slow and a learning experience for myself and possibly others. First time I've attempted to manage/start a program so hoping it works out.

---

### Post by 11jmb on 2011-11-09
Don't worry about language yet. If you want to do this right, there is still a lot of work to be done before you write a line of code.

Is this credit card tool the only thing you want to do or is it just one part? The reason I ask is because vision is extremely important. If you have vision, then this credit card tool (as well as everything else) can be programmed to fit into your vision. 

Use cases are a good way to start, and then you can start conceptualizing how you want your code (objects) to handle these use cases, which will eventually lead you towards a UML diagram. Then, and only then, should the coding begin. Trust me, you think of so much as you go through these early design steps that would be completely lost if you just dove into the code.

I think you have good intentions for incremental progress, and a credit card tool can be your first implementation, but as you start adding functionality, there is a very good chance that your project will turn into kludgey spaghetti code if you do not formalize your vision from the start

---

### Post by jmadero on 2011-11-09
Really appreciate the advice. The credit card tool is only one aspect of what I envision, I guess I figured that getting a few programmers to talk to me (including yourself) would help me really pinpoint everything I want the program to do. In general I see a ton of functionality for debt that is missing in all software that I've eve seen, these include:

1. Credit Card Blueprint -- already mentioned

2. Student Debt -- Handling subsidized, unsubsidized loans, calculating interest, etc... most websites that I've seen (my wife and I both have our fair share of student loan debt)are horrible about describing your interest and what not. One easy to read program would be nice

3. Mortgage Loan

4. Auto Loans

5. Other Loans

6. Other liabilities (ie. child support, etc...this is just a big maybe that came to mind)


So here are a couple use cases:

1. I have a credit card that I use for regular bills and large purchase items. I want a program that I can put in number of payments for each item and the program will then tell me a "minimum payment" or "suggested payment" based on the information I provide

2. I have $500 to put towards my debt this month, where is the optimal place for me to put the money towards taking into account interest rates, suggested payment from above & minimum payments required for each item.


Any way that we can take this part of the convo out of forum and move it to email, I'd love a person(s) to brainstorm with. 

For anyone interested in developing, input would be great here also :)

---

### Post by 11jmb on 2011-11-09
You are on the right track here. It sounds like at the highest level, this is meant to be targeted towards individuals, or possibly personal accountants, not small businesses, banks or corporations. Am I right here?

In general, I favor open collaboration where many people can view and make comments. Perhaps you could set up a SF site for the project and link to it on this thread. After that, if there is something that you would rather talk personally about, you can PM me.

It looks like your professional background will help a lot in the development phase, but I would try to find an experienced accountant (perhaps a friend or a friend of some other developer) who can help refine the vision of what a good personal finance tool would do. This phase is always difficult, because "customers" almost always speak in terms of interface rather than functionality, so it may take some prying to figure out what that vision is, but it will be worthwhile.

---

### Post by jmadero on 2011-11-09
Sounds good, let's keep the discussion here as I get a site up and, what is SF site? 

You are correct, for individuals, any individual with debt who wants an organized way to pay down debt and see how much they are losing due to debt (ie what is the interest really costing them). 

I have one dev who PM'ed me and it looks like he/she is on board, I'll be starting an email group and in the coming week I'll be sending out an email to move the discussion to a mailing group/IRC to start the real brainstorming/use cases.

I'm glad no one has said "oh there's software that already does that" seems like I've found a niche that has been missed :)

---

### Post by 11jmb on 2011-11-09
Sourceforge. I think that it will have everything you need as you move forward. 

I don't really do much OSS devel, but I'm pretty sure that SF will suit your needs. Perhaps somebody else here may have another recommendation, but its a good starting point.

---

### Post by jmadero on 2011-11-09
Okay obviously early for this but, I need name suggestions so I can do github, website and SF. I think debt-management software sounds boring ;) I'm not too good with the creative stuff like this. Suggestions?

---

### Post by 11jmb on 2011-11-09
Im not going to be any help there either lol. Is there a specific reason that you want to set up all three of those right away?

---

### Post by jmadero on 2011-11-09
Just to get them all done, feel like at this point they are things I can do on my own. I already have a github, website would be easy enough using blogspot and SF looks easy but all three need some kind of project name, lol, and my mind draws a blank.

I've also contact an accountant colleague of mine to see if she or one of her colleagues would mind offering feedback as the project comes together. I suspect her or someone she knows will be willing to, I promised her it wouldn't be too time consuming :)

---

### Post by karlson on 2011-11-09
> **jmadero said:**
> This is a double post so I hope this doesn't violate forum rules (someone in the community cafe told me I might want to post here as well). Here's a link to the discussion happening, hoping to get person/people together in the next few days to start the brainstorming. Thanks

[http://ubuntuforums.org/showthread.php?t=1877727](http://ubuntuforums.org/showthread.php?t=1877727)


After reading both threads I have a question:

> 
The program is a finance debt management program. What I've found is that there is no software that is really a complete debt management piece of software. This would include loans, mortgage, credit cards, etc...


What exactly does this mean?

Based on my understanding of what you are trying to do you are looking to do a personal accounting system.  So instead of trying to do everything from scratch may be it would be better to contribute to project like GnuCASH.

---

### Post by jmadero on 2011-11-09
Karlson yeah I thought that if I got a few people to collaborate we would most likely use code from other projects but none of them have what I want in terms of really managing debt, they are more just balancing accounts. I've tried GnuCash, KMyMoney (personal favorite) and a couple others but like I said, none have really a debt component. I figured that the brainstorming would lead to a comprehensive list of uses that (hopefully we) would want and then we could discuss how to implement those, whether by using a lot of code from others, a little code from others, or starting from scratch so we have real understanding (and less clutter) of everything in the code.

In terms of debt management what I mean really comes down to what the threads have said already, complete control over one's debt with clear summaries, suggestions of pay down based on user input, etc... Presenting the information in a much cleaner, more comprehensive  & sleeker way than websites provide or that other pieces of software provide.

One for instance about what something like KMyMoney lacks is the option to put in # of payments per transaction and then calculate suggested payments based off of this. Also lacks the ability to calculate minimum payments (based on rules that Credit Cards legally have to provide), etc...

I have found that through my years of using different debt instruments (from credit cards to student loans and car loans) the information just becomes hard to follow, handle, etc... and this comes from someone who really has a firm understanding of interest and math in general. 

This is the niche I'm hoping to fill with this piece of software

---

### Post by 11jmb on 2011-11-09
> **jmadero said:**
> Just to get them all done, feel like at this point they are things I can do on my own. I already have a github, website would be easy enough using blogspot and SF looks easy 

Keep your developers in one place. They should not have to read three different threads and checkout source from two different places while working on this project. If you want to start basic collaboration on blogspot with the goal eventually migrating to github or sourceforge, fine, but you are going to lose interest if you make things complicated.

---

### Post by jmadero on 2011-11-09
fair enough, you would suggest blogspot to start then? I prefer github personally, has the wiki options, also has a nice way to keep track of software but I'm up for suggestions

---

### Post by 11jmb on 2011-11-09
You really just need a place where devs can communicate effectively, so its up to you.

[http://en.wikipedia.org/wiki/Comparison_of_open_source_software_hosting_facilities](http://en.wikipedia.org/wiki/Comparison_of_open_source_software_hosting_facilities)

source forge seems to be more feature-rich than github. which may help some in the future, and you can change your project name to something more interesting down the road.

---

### Post by karlson on 2011-11-09
> **jmadero said:**
> Karlson yeah I thought that if I got a few people to collaborate we would most likely use code from other projects but none of them have what I want in terms of really managing debt, they are more just balancing accounts. I've tried GnuCash, KMyMoney (personal favorite) and a couple others but like I said, none have really a debt component. I figured that the brainstorming would lead to a comprehensive list of uses that (hopefully we) would want and then we could discuss how to implement those, whether by using a lot of code from others, a little code from others, or starting from scratch so we have real understanding (and less clutter) of everything in the code.

In terms of debt management what I mean really comes down to what the threads have said already, complete control over one's debt with clear summaries, suggestions of pay down based on user input, etc... Presenting the information in a much cleaner, more comprehensive  & sleeker way than websites provide or that other pieces of software provide.

One for instance about what something like KMyMoney lacks is the option to put in # of payments per transaction and then calculate suggested payments based off of this. Also lacks the ability to calculate minimum payments (based on rules that Credit Cards legally have to provide), etc...

I have found that through my years of using different debt instruments (from credit cards to student loans and car loans) the information just becomes hard to follow, handle, etc... and this comes from someone who really has a firm understanding of interest and math in general. 

This is the niche I'm hoping to fill with this piece of software

Collaboration notwithstanding but I think that adding functionality as a plugin to GnuCASH or KMyMoney would serve people better.  Managing debt is important but you will have to provide the functionality of actually managing accounts, tracking expenses, etc on top of what you are doing because I for one don't see the use of one without the other.

---

### Post by jmadero on 2011-11-09
I am going to start up a SF project but part of the discussion will be "is this better as a plugin", personally I looked at the source for kmymoney and I saw a lot that I wouldn't want (what I consider to be clutter but maybe others use often). After getting a long list of uses that I (and hopefully others) would want, the next discussion will be "is this a standalone project". 

The other option is to make a new project that incorproates basic balancing functions that GNUCash or KMyMoney have but take out a lot of the extras, clean up the code and add the features that will fulfill the features that come with the use list.

Lastly, personally I don't love the look of either KMyMoney or GnuCash, I'm one of the ones who thinks "the vast majority of systems these days have resources to spare, why not use at least some of them", this isn't to say add flashy stuff just to add it but I do like nice looking (while still functional) pieces of software. An example of this is I do use the cube in compiz (and then devilspie to move software to sides of the cube automatically). 

I'm going to post shortly a link to the SF and this conversation can continue, starting with uses, and then moving towards "how do we move forward". 

Excited for this, glad I have people interested at least in the concept and willing to give the time to offer opinions

---

### Post by jmadero on 2011-11-09
here it is: 

[https://sourceforge.net/p/debtmanagement/discussion/](https://sourceforge.net/p/debtmanagement/discussion/)

---

### Post by 11jmb on 2011-11-09
Looks good. I won't have the time to really develop for you, but I can put in my $0.02 every day or two.

Again, good luck :)

---

