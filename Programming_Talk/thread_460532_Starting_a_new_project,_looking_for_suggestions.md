---
title: "Starting a new project, looking for suggestions"
date: 2007-05-31
forum: Programming Talk
---

### Post by netkid91 on 2007-05-31
Being a high school student that has had a chance to take a close look at the software that my school district uses, I have found that I could make a much better, completely web-based solution. I am mostly in the planning phases of this project, but I thought I'd ask people here a few things.  Mainly, I have a few questions I am unsure about, and I'd also like some opinions on my plan, which I am going to describe in detail here.

  My idea is to provide a grab-bag of services that school districts can pick from, such as teacher/student email, attendance tracking, library management, etc.  just to list a few planned applications, and charge a monthly fee per school for these services, moreover a modest one.  Since all of the software would be hosted off-site, they would never have to worry about management of  the software, reducing support costs for them.

  So I ask you, especially if you have any experience working in a school setting, what all needs to be available in such a package?  Also, does anyone here know of any good but cheap VPS hosting (actual root-access virtual server, the industry is beginning to confuse 'virtual servers' with 'shared hosting with cPanel)?  Finally, is there a way to add tagging support to IMAP mail servers a'la GMail, and if it must be done in software, how to do so in RoR (Ruby on Rails)?

---

### Post by Daveski on 2007-05-31
> **netkid91 said:**
> Since all of the software would be hosted off-site, they would never have to worry about management of  the software, reducing support costs for them.

No lessons today - our internet connection is down.

---

### Post by seamless on 2007-05-31
Take a look at [Unicon]("http://www.unicon.net/") and [Blackboard]("http://www.blackboard.com/us/index.Bb"), they are the industry leaders in what you are talking about. They will be your competition especially if you plan on selling it comercially.

---

### Post by netkid91 on 2007-05-31
> **Daveski said:**
> No lessons today - our internet connection is down.
Hehe, already planned for that. Did you hear about [Google Gears]("http://gears.google.com")?  Not to mention in todays world, school *is* stopped anyways if your 'net connection is down, and in times of crisis, good old grade books still exist.

Edit: Seriously though, anyone know how to add tags to IMAP mail?

---

### Post by Daveski on 2007-05-31
> **netkid91 said:**
>  Did you hear about [Google Gears]("http://gears.google.com")?  Not to mention in todays world, school *is* stopped anyways if your 'net connection is down, and in times of crisis, good old grade books still exist.

Yes, technology is looking good. I am old-school though and think that support from a central body is great, but having a self-sufficient IT has it's own benefits. Besides, I don't like the idea that Government run education facilities have to pay a company such as Microsoft for all software, and neither do I like the idea that most people are only taught to use a single companies product. So I don't like that idea that another company would be making a profit from the education of a Nation (or Nations).

As you state in your sig, Linux and Open Source are free. There is a great deal of education in maintaining these systems.

---

### Post by netkid91 on 2007-05-31
> **Daveski said:**
> Yes, technology is looking good. I am old-school though and think that support from a central body is great, but having a self-sufficient IT has it's own benefits. Besides, I don't like the idea that Government run education facilities have to pay a company such as Microsoft for all software, and neither do I like the idea that most people are only taught to use a single companies product. So I don't like that idea that another company would be making a profit from the education of a Nation (or Nations).

As you state in your sig, Linux and Open Source are free. There is a great deal of education in maintaining these systems.

I like your view on things, and I really appreciate your insight.  In addition to developing this hosted service I should also make an open-source version (that is not inferior in functionality) for districts that ARE willing to support it themselves, and have the IT department to manage such an installation.  Also, I have no intent on turning a profit on my endeavor, in fact, any extra money I would make would probably only go towards working on the software, and donating to charity.

---

### Post by obrient on 2007-05-31
As someone who works in a school and is a OSS user, but realizes schools fears on OSS you would be in a good place if you could create a single sign on application that would allow teachers, students, and administrators (think from Vice Principal to Superintendent as well as clerical and tech staff) to do their job. 

This is a real panacea and is a way off still. Most schools are looking at something that makes teachers jobs easier for educating students as yourself. They also have a lot to consider with stability and support. I know that a lot of schools are interested in buying software because they feel that it there is support behind it. This is another thing that you need to consider. 

I have to say I admire your ambition, and I do think you have a great idea. I would say that you really need to think outside of the Moodle/Blackboard box of only delivering content. Look at the management of a school and how to integrate systems together with layer of users and you will be golden. I would definitely be interested to hear your thoughts and ideas. My job is to work with teachers to help them use technology in the schools so I have a great opposite perspective of you as a student. 

Also think about growth. Also your hosted service at least where I work would not be the ideal. We would rather buy a box that would be supported and managed in house. Not that there isn't the other side of the coin. This is totally dependent on the schools existing infrastructure. 

Keep me posted, and talk to your teachers and principals. They are probably a lot more approachable then you think :)

---

### Post by netkid91 on 2007-05-31
> **obrient said:**
> As someone who works in a school and is a OSS user, but realizes schools fears on OSS you would be in a good place if you could create a single sign on application that would allow teachers, students, and administrators (think from Vice Principal to Superintendent as well as clerical and tech staff) to do their job. 

This is a real panacea and is a way off still. Most schools are looking at something that makes teachers jobs easier for educating students as yourself. They also have a lot to consider with stability and support. I know that a lot of schools are interested in buying software because they feel that it there is support behind it. This is another thing that you need to consider. 

I have to say I admire your ambition, and I do think you have a great idea. I would say that you really need to think outside of the Moodle/Blackboard box of only delivering content. Look at the management of a school and how to integrate systems together with layer of users and you will be golden. I would definitely be interested to hear your thoughts and ideas. My job is to work with teachers to help them use technology in the schools so I have a great opposite perspective of you as a student. 

Also think about growth. Also your hosted service at least where I work would not be the ideal. We would rather buy a box that would be supported and managed in house. Not that there isn't the other side of the coin. This is totally dependent on the schools existing infrastructure. 

Keep me posted, and talk to your teachers and principals. They are probably a lot more approachable then you think :)
**WOW**, thank you for all of that, seriously.  So in addition to my hosted service, I **will** make a OSS version, but also "sell" the same software in a box, with the sole difference of easier setup, and included support.  I am planning on having a moodle-ish component to my work, but yes, most of my idea is on managing the school instead of delivering content.  I would love to continue to hear your ideas, so keep them coming.

---

### Post by big_area on 2007-05-31
need/want any help with design/code?

---

### Post by netkid91 on 2007-05-31
You know Ruby on Rails?

---

### Post by big_area on 2007-05-31
no, but i have been looking for a reason to learn a new language

---

### Post by obrient on 2007-05-31
Two thoughts on how to see what the government requires for reporting and such would be to check out [http://www.ed.gov/index.jhtml](http://www.ed.gov/index.jhtml). Another would be to check out your home states Department of Educations Website. This would give you some basic ideas on how school systems are managed. 

You may also want to check out educational bloggers such as David Warlick, Will Richardson, and Alan November. They will give you some insight into the teachers perspective. 

As you work on this keep in mind the end goal of education is to help students become life long learners. You seem to already get this I have a feeling. It seems that you are interested in computers and will do the work needed to get to your goal.

Keep me in the loop I would like to advise as much as possible. It is my personal opinion that education needs to expose more students to technology and not just writing papers with it.

---

### Post by netkid91 on 2007-05-31
> **big_area said:**
> no, but i have been looking for a reason to learn a new language

> **obrient said:**
> Two thoughts on how to see what the government requires for reporting and such would be to check out [http://www.ed.gov/index.jhtml](http://www.ed.gov/index.jhtml). Another would be to check out your home states Department of Educations Website. This would give you some basic ideas on how school systems are managed. 

You may also want to check out educational bloggers such as David Warlick, Will Richardson, and Alan November. They will give you some insight into the teachers perspective. 

As you work on this keep in mind the end goal of education is to help students become life long learners. You seem to already get this I have a feeling. It seems that you are interested in computers and will do the work needed to get to your goal.

Keep me in the loop I would like to advise as much as possible. It is my personal opinion that education needs to expose more students to technology and not just writing papers with it.
Well Big, you are more then welcome to help me, the best part about rails is it's great documentation and it's easy to learn as you go, plus it's easy to begin with.
Also Obrient, of course we will keep you in the loop, I appreciate your insight and perspective and I think it's value in my project is incredible.

---

### Post by pmasiar on 2007-05-31
take look at edubuntu, skolelinux and just look around. There are couple of F/OSS projects like this, you may want to join with them instead of creating a dud. It is *a lot* of work to code, maintain, and *document* all that.

---

### Post by netkid91 on 2007-05-31
I am not making a Linux distro, I am making a completely web-based set of tools to replace many software packages current schools are using for grades, attendance, library managment, etc.

---

### Post by ankursethi on 2007-06-01
My school has a content delivery system (mainly videos) that is hosted in-house but maintained by an external company. I don't know exactly how the system works, but AFAIK there is one person from the company (Educomp) who supervises over a couple of the school's own sysadmins.

In-house hosting is what schools would want. In addition to content delivery, the system will have to support school management as well, as many posters above have said. It would be nice - if your school happens to have a website and are willing to implement it - if the teachers/students could log into the system from anywhere and get access to content (assignments, reference resources etc. for students and grade books for teachers). The possibilities for such a system are endless.

IMHO, it would be better if you first build a prototype which is fairly modular and show it to your school management, and then add features incrementally as desired by the teachers.

---

### Post by pmasiar on 2007-06-01
> **netkid91 said:**
> I am not making a Linux distro, I am making a completely web-based set of tools to replace many software packages current schools are using for grades, attendance, library managment, etc.

Did you looked up what they do? They do the same you want to do - and then pack the tools as distro to simplify deployment :-)  And they have user community. IMNSHO you are much better off join existing project doing something you wantto do than start your own (unless you want something radically different - and can prove why).

But of course it is your time and your life. Just a free suggestion.

---

### Post by netkid91 on 2007-06-01
Edubuntu does not do these things, it provides terminal services and has some zope applications for online learning, but nothing like what I am describing  Also ankursethi, the beauty of Ruby on Rails is it's modular nature.  You have no need for a plugin system since you can just add a few new controllers and they have access to all the same stuff as the rest of the app.

Edit: Google Code project [http://code.google.com/p/capmuselect/](http://code.google.com/p/capmuselect/) for anyone who wishes to help.

---

### Post by obrient on 2007-06-01
I was just thinking you may want to look at some of the projects like DSpace and other FOSS library automation systems. They are usually done by colleges, but would be a good place to start. Also check out [http://funnymonkey.com/](http://funnymonkey.com/) which is a company that is working with Drupal to do some of the teacher type stuff that Moodle does. Another idea is contributing or adding to their concept.

---

### Post by Daveski on 2007-06-01
> **netkid91 said:**
> I like your view on things, and I really appreciate your insight.  In addition to developing this hosted service I should also make an open-source version (that is not inferior in functionality) for districts that ARE willing to support it themselves, and have the IT department to manage such an installation.  Also, I have no intent on turning a profit on my endeavor, in fact, any extra money I would make would probably only go towards working on the software, and donating to charity.

This sounds good then - I think we have agreeing principles. Keep us posted with your progress and let it be known if you need something doing.

---

### Post by obrient on 2007-07-26
Hey not sure if you were thinking about email and calendars for part of your project. If so check out [Zimbra,]("http://www.zimbra.com/products/") It seems pretty slick as an Ajax based client and server.

---

