---
title: "ASP &amp; .NET in Linux?"
date: 2007-07-26
forum: Programming Talk
---

### Post by gary0 on 2007-07-26
Alright, I am sick of my win xp pro box which I use to host my wifes website crashing, restarting, and doing otherwise unsavoury things. It is rebooting now as I type for the fifth time. Is there any way at all that I can host asp and .NET sites in Linux? I'm ok with apache and flat HTML files, but dynamic sites...? Not too sure. I don't really want to go to the hassle of converting all to PHP or Perl or Python as this site has over 100 pages! Half of which are just run on the server and not actually seen in the browser (database calls, security checks etc). Is there an add-on for apache that will allow this site to run in linux? It is the only reason I still have a windows box. If I could get this this working in linux, well, bye bye windows.

Thanks in advance,
Gary (frustrated web developer).

---

### Post by gvoima on 2007-07-26
[http://www.mono-project.com/]("http://www.mono-project.com/")

That should do it..

Do a google search on "asp.net linux" and "mono project" for more information of how to get it to work. And be sure to check the helps on the mono webpage.

---

### Post by pmasiar on 2007-07-26
> **gary0 said:**
> Alright, I am sick of my win xp pro box ... Is there any way at all that I can host asp and .NET sites in Linux? ... (frustrated web developer).

As they say, think in advance before writing any code: code is like tattoo -- will stick on you for a long time!

As you found, platform you selected is crap, and you are stuck with code for crappy platform. Mono *might* solve some problems, but you hardly can expect free clone of .NET as smooth and mature as proprietary original. One of the reasons is, clone does not attract as many developers as it's completely free competitors (LAMP: Linux+Apache+MySQL+Perl/Python/PHP/Ruby). And one of the reasons is, LAMP stack is (in opinion of many) superior platform. Another reason is: it's a sucker game to follow proprietary competitor feature for feature: sometimes you need to recreate bug exactly as in original. And it is not fun either.

You have 3 options: 
1) stick with ASP/XP for this project, get it done and forget it
2) Try Mono and be forever guinea pig for new versions, chasing the functionality of the proprietary original
3) Consider ASP as learning experience, throw it away and switch to something better.

Then, consider how urgently you need stable release, and what are your long-term goals. 

Are you ready to be guinea pig for Mono? Do you want to become Mono expert? Did you planned to do your next project on LAMP platform anyway?

Because it is website for your wife, (1) looks not an option - you cannot forget about your customer :-) maybe it is time to bite the bullet and switch? I don't know what your website does, but I am continually amazed how powerful is TurboGears (one of major Python web app frameworks). Your ASP pages are decent start for templates (you have web design done), you have SQL and database design, so writing controllers to handle request and fetch data for templates should be easier - and you already understand your app.

As they say, when developing app, plan pilot version to throw - you will throw it anyway :-)

---

### Post by Peyton on 2007-07-27
> **gvoima said:**
> [http://www.mono-project.com/]("http://www.mono-project.com/")

More specifically, see this page:

[http://www.mono-project.com/ASP.NET](http://www.mono-project.com/ASP.NET)

---

### Post by gary0 on 2007-07-27
Thanks for the prompt replies guys. I did this website about 4 years ago before I discovered linux. It is a site that shows my wifes artwork and photos. It has lain dormant for a couple of years, and I recently revived it for her. [www.brooke-engledow.co.uk](www.brooke-engledow.co.uk) 

I do have mono, but haven't been able to devote too much time to learning it due to work and family commitments. I will certainly look into TurboGears - is it in the repos?

I know it's (iis) is a crap platform, I knew when I started that it was vulnerable to nasties etc, but at the time, it was all I had available.

I guess I'm just another victim of vendor lock-in. I'll have more time on my hands come the winter, so will knuckle down and get LAMP under my belt.

Thanks again for you help and suggestions.
Gary.

---

### Post by gary0 on 2007-07-28
Well guys, I downloaded turbogears, how do i implement it now? I have Eclipse and idle so is it a plugin for either of these? Any and all guidance wold be muchly appreciated.

Thanks,
Gary.

---

### Post by pmasiar on 2007-07-28
Try tutorials first: [http://docs.turbogears.org/1.0](http://docs.turbogears.org/1.0)

Turbogears book is excellent: "Rapid app development with TG", worth every penny. If you have more questions, ask on TG list - see you there :-)

---

### Post by Steveway on 2007-07-28
Sorry to say this but you need ASP and .NET to make a site like that?
That is just a big waste, why not use static sites for those 9 pages?
Or use a gallery-script such as gallery2 or coppermine.
But hundreds of pages with ASP and .NET only for this are really overkill.

---

### Post by gary0 on 2007-07-29
Well, because there is an admin section which allows her to upload, edit, remove, items, and administer the guestbook etc. There's actually about 50 pages in all, including include files, css, and securiity stuff.

I have only one page for each category that displays the selected picture (showpic.asp, showdrawing.asp etc). When she uploads her new stuff (that stuff on there is 3-4 years old), it would be a pain to make a new html page for each new picture. This way, she just needs to upload the thumbnail and the picture, tell the db where it is, and bingo - it appears on the site. A 2 minute job for her. Why have potentially 100's of pages to display 100's of pictures when just one will do it? All I do is just pass the ID of the thumbnail to showpic.asp and there it is.

And at the time, this was a learning experience for me. I wrote a site for The British Amateur Radio Society which did have hundreds of pages. It included 3 levels of login (guest, member and admin), which would allocate certain permissions depending on your login status, all data encrypted and stored in a remote database, online voting system for current issues/debates, a book review system where any member could post a review, round table live discussion area, private email system (callsign@bars.org), the ability for new users to register online, license VDN validation algorithm, callsign search etc. They loved it. So from that small art site, grew this considerably larger site. There were members form all over the world. BARS are now no more, but I do still have the website here (not online though).

So now you know.

Gary.

---

### Post by Note360 on 2007-07-29
Nice page though. Lets see I am having trouble getting xsp to work my self but i have no idea why (tomcat wont work either :().


Nevermind, i just had to reboot. install xsp and the apache bindings for it and itll integrate right into your apache installation (then you can integrate php python ruby whatever you want eventually. ASP is nice i guess but these languages do better under linux)

---

