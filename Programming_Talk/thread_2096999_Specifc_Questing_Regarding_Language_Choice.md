---
title: "Specifc Questing Regarding Language Choice"
date: 2012-12-21
forum: Programming Talk
---

### Post by tomokun on 2012-12-21
Ok guys, so I've been through the language sticky, and I'll be honest - I'm a 0-level, never been kissed newb at programming.

Basically, I'm a writer who has decided that I want to dive into the world of programming, to see what it's like.

I've done some very basic things in Visual Basic, Basica, and HTML, but I never got very far in any specific area.

My GOAL in learning programming would be to understand network security (because it absolutely mystifies me), and to create my own applications (or at least manage the coders I would hire better). I currently manage content writers, and I do so extremely effectively because I understand writing on a fundamental level. I'd love to be able to understand programming in the same way so that I can know when I'm being reasonable and unreasonable, and so that I can look at a project mid-way and have a reasonable understanding on what has to happen next.

Yes, I expect that to learn this that it will take me quite a bit of time, and fortunately I have the time to invest.

So, the question is, in order to accomplish these goals, what is the language that I should learn first, that will help me develop good habits and insights.

Currently I started going through a C tutorial, but after reading through the sticky, I'm wondering if that's the exact wrong way to go?

Ideally, I'd like to learn a language I can actually use in the real world.

---

### Post by trent.josephsen on 2012-12-21
I normally suggest Python for people who are just starting out, but for some reason I have a good feeling about Perl for you. Partially because you self-identify as a writer, but mostly it's just a gut feeling.

I do think that *Learning Perl* is the best introductory programming book for self-study, hands down. If you have money to spend on a book, you will not regret the purchase. It takes the reader from no knowledge to some quite useful scripts in a surprisingly short time.

Perl is pretty easy to get started with and very popular for real-world applications. It's often used for server-side scripting, CGI, that kind of thing, and I think it would be a good starting point for the network security aspect.

Python is a bit more regular and mathematical, and another excellent choice for a first language should you choose to use it instead.

Good luck!

EDIT to add: it should really go without saying that the best language for you depends on many factors, it's impossible for me or anyone to know in advance what is best for you, and any choices you make must be your own. That said, I stand by my original recommendation.

---

### Post by DTSDeveloper on 2012-12-21
first of all, c is a great langauge for networks and is only the wrong way because it is a hard language to learn as ur first one. second i recommend python but i never use have used perl so i cant say that python is a better choice

---

### Post by tomokun on 2012-12-21
Thank you both for your feedback. 

What are some of the other factors that would help to narrow down which language would be best for me, out of curiosity? 

I will definitely check out Perl and Python, but what makes C so difficult to learn?

---

### Post by kevinharper on 2012-12-22
> What are some of the other factors that would help to narrow down which language would be best for me, out of curiosity? 
You mentioned you wanted to learn programming so you could direct a team of programmers you would be hiring.

Is this team going to be building network-related projects? I think the type of software intended to be built has a lot to do with making a decision like this (and from our end, giving suggestions).

---

### Post by Mikeb85 on 2012-12-22
I'd go with Python or Ruby.  Both are easy to learn, readable (important if you're managing people, or so I hear), and powerful (though not necessarily fast).  

I personally like Ruby - it's easy to set up, get libraries, learn, and you can do alot with it.  Performance is ever improving, and 1.9 is pretty quick for a dynamic language.  Python is a great choice because it forces convention, and has alot of the same benefits as Ruby, though doesn't have the same easy set up (Rubygems makes adding libraries stupid simple).  

I started from scratch fairly recently too, learning Ruby, playing with Python, Clojure and OCaml, and although they all have their perks (I especially enjoy OCaml), I keep coming back to Ruby.  Everything that requires effort in other languages is trivial in Ruby, and I can build stuff easily.

---

### Post by SuperCamel on 2012-12-22
> **tomokun said:**
> Thank you both for your feedback. 

What are some of the other factors that would help to narrow down which language would be best for me, out of curiosity? 

I will definitely check out Perl and Python, but what makes C so difficult to learn?

There is nothing difficult about C at all. It's 'low level', meaning it doesn't automatically handle memory, variables must be explicitly declared and all that stuff. But it's a heck of a lot simpler than a lot of other languages and I believe learning a lower level language such as C will make you a better programmer by forcing you to know the nitty grity stuff. All programming languages are difficult until you've learned them properly and C doesn't take as long as other many languages.

---

### Post by Bachstelze on 2012-12-22
> **SuperCamel said:**
> **There is nothing difficult about C** at all. It's 'low level', meaning it doesn't automatically handle memory, variables must be explicitly declared and all that stuff. But it's a heck of a lot simpler than a lot of other languages and I believe learning a lower level language such as C will make you a better programmer by forcing you to know the nitty grity stuff. **All programming languages are difficult until you've learned them properly** and C doesn't take as long as other many languages.

Self-contradiction much?

My take on this is that people who learn C as their first language are virtually guaranteed to see the trees but not the forest. We have a user here (everyone will know whom I am talking about) who has exactly this problem, keeps on wondering about obscure technicalities (for example about the use of extern) but it is unknown if he ever coded anything meaningful (my guess is no).

---

### Post by tomokun on 2012-12-22
> **kevinharper said:**
> You mentioned you wanted to learn programming so you could direct a team of programmers you would be hiring.

Is this team going to be building network-related projects? I think the type of software intended to be built has a lot to do with making a decision like this (and from our end, giving suggestions).

Mainly they'll be building webpages and utility software for internal use. I want to build a project management program that will allow me automatically hire and assign team members based on output, and I'm trying to make it have very visible benchmarks based on performance.

Let me also add that I also see "app building" in our future, and this would be one of the first areas where I would want to "play".

---

### Post by trent.josephsen on 2012-12-22
> **tomokun said:**
> Mainly they'll be building webpages and utility software for internal use.
Still sounds like a job for Perl, unless there's some particular other language they will be using. If they will all be working in C#, learn that instead. You don't want to be the guy self-taught in an unrelated language setting goals for and evaluating the rest of the shop. I don't ask my plumber whether the electrician has done a good job.

> I want to build a project management program that will allow me automatically hire and assign team members based on output, and I'm trying to make it have very visible benchmarks based on performance.

Urgh. You know your own business best, of course, but this sounds like something Dilbert's boss would say.

---

### Post by tomokun on 2012-12-22
> **trent.josephsen said:**
> 
Urgh. You know your own business best, of course, but this sounds like something Dilbert's boss would say.

*nods* I've developed a performance based business model for my writers. So far it's working really well, not just profitably, but the writers like it too.

I DO have to hire lots of writers to keep up with everyone's schedule, but essentially the writers can make their own schedule and do as much or as little work as they want, and they get paid based off of what they produce, and fined per day for turning in things late. Since they agree to deadlines before being assigned a project, and they are free to reject any assignments given to them, there's never a situation where they are given an assignment whose deadline they aren't aware of.

The biggest bottle-neck I have is processing the incoming orders from clients and filling them in for the best writers for the job that are available. Essentially, I'm just going to try to build a software that automates the entire process, rather than me having to deal with the whole thing myself. :p

I'm reading the Learning Perl book now, so far it's pretty easy, although I don't get what they mean by "chomp" or why it's necessary. Other than that, everything has been very clear.

Is there a "compiler" (I think that's what I'd need) to start writing programs in that's better than others for Perl?

Also, is there anything on the Google Play store that I should download that would make this easier (or provide a cloud-based base for me to program off of).

Once again, thanks to EVERYONE for your responses, I'm taking everything you guys say into consideration, and reading up on it as well. :)

---

### Post by trent.josephsen on 2012-12-22
I thought it might be something like that. Sounds like you know what you're doing and project management is not my strong suit, so I will rescind my criticism.

> **tomokun said:**
> I'm reading the Learning Perl book now, so far it's pretty easy, although I don't get what they mean by "chomp" or why it's necessary. Other than that, everything has been very clear.

Is there a "compiler" (I think that's what I'd need) to start writing programs in that's better than others for Perl?

If you're programming in Linux, the system Perl is all you need. Unless it's really ancient (pre-5.8 or so) you'll probably find no difference between it and the most recent version. I don't have experience using Perl on Windows but I know there are two "major" Perl distributions for Windows: ActiveState and Strawberry Perl. (I'd advise using Linux anyway, if you can.)

As for chomp, the terminal your Perl program runs in is line buffered -- that is, your program doesn't receive any input until you've hit Enter at the end of the line. Pressing Enter puts a newline character into the input stream (which is represented by <STDIN>), and all chomp does is take that newline character out so that you don't read it as part of your input. (I'm never sure when I've explained something sufficiently, so I'm stopping here unless you ask for clarification. :) )

> Also, is there anything on the Google Play store that I should download that would make this easier (or provide a cloud-based base for me to program off of).

I'm not sure what you mean exactly. Are you looking for an IDE, like Visual Studio?

---

### Post by tomokun on 2012-12-22
> **trent.josephsen said:**
> I thought it might be something like that. Sounds like you know what you're doing and project management is not my strong suit, so I will rescind my criticism.


No worries, it's a valid point, and most owners don't take employee perspective into account. :p Performance based pay is usually a way of saying that you don't trust someone and you're cheap, lol.


> **trent.josephsen said:**
> 
There are two "major" Perl distributions for Windows: ActiveState and Strawberry Perl. (I'd advise using Linux anyway, if you can.)

I'm not sure what you mean exactly. Are you looking for an IDE, like Visual Studio?


Basically your last question ties into the answer you gave. I'm looking for something which will visually point out when I've typed in something that doesn't make sense, like Visual Studio, but that I can run off Chrome like sourceLair.

SourceLair seems to only work for C or C++ though, so I ws wondering if there was an equivalent for Perl that you could recommend.

Is sourcelair =~ to Activestate do you think?

I have no REAL experience with Linux, but I'll look into these programs. All I have right now are Windows PC's and a tablet, and I'm loathe to give up Microsoft Office and some of the other Windows only programs I have to use as of now.

> **trent.josephsen said:**
> 
As for chomp, the terminal your Perl program runs in is line buffered -- that is, your program doesn't receive any input until you've hit Enter at the end of the line. Pressing Enter puts a newline character into the input stream (which is represented by <STDIN>), and all chomp does is take that newline character out so that you don't read it as part of your input. (I'm never sure when I've explained something sufficiently, so I'm stopping here unless you ask for clarification. :) )


Over explanation is good in my book :p

And yes, that seems to make sense. The Enter key has it's own character, and if you're doing the "Hello World" program tutorial, you don't want to have to compare "Randal" to "Randal(Enter)"

---

### Post by kevinharper on 2012-12-22
I agree w/ trent. You should consider perl. It's often referred to as a swiss army chain saw in regards to it's potential. I specially like trent's suggestion because you've admitted you want to do web-based programming.

Best of luck to you.

---

### Post by trent.josephsen on 2012-12-22
I've never used what you might call an IDE with Perl, so I couldn't suggest any of those available (there's an oldish [perlmonks thread](http://www.perlmonks.org/?node_id=639314) about Perl IDEs if you're looking for a list).

I try not to be the anti-IDE guy, but I've found that IDEs really don't do it for me in terms of workflow. My essential Perl development environment consists of a terminal window to run code in and an editor to edit code in. I'm not sure how to achieve that in Windows, either... perhaps someone else can throw in a suggestion.

> I have no REAL experience with Linux, but I'll look into these programs. All I have right now are Windows PC's and a tablet, and I'm loathe to give up Microsoft Office and some of the other Windows only programs I have to use as of now.

Could you install Linux in a virtual machine, via VirtualBox or VMware? It requires a bit more power than installing directly to your hard drive but it's the lowest-impact method. If you have access to a Mac that's also a possibility (Mac OS X includes Perl, albeit a slightly old version). There's no technical reason to give up Windows to be able to run Linux. Just my $0.02

---

### Post by tomokun on 2012-12-22
> **trent.josephsen said:**
> I've never used what you might call an IDE with Perl, so I couldn't suggest any of those available (there's an oldish [perlmonks thread](http://www.perlmonks.org/?node_id=639314) about Perl IDEs if you're looking for a list).

I try not to be the anti-IDE guy, but I've found that IDEs really don't do it for me in terms of workflow. My essential Perl development environment consists of a terminal window to run code in and an editor to edit code in. I'm not sure how to achieve that in Windows, either... perhaps someone else can throw in a suggestion.



Could you install Linux in a virtual machine, via VirtualBox or VMware? It requires a bit more power than installing directly to your hard drive but it's the lowest-impact method. If you have access to a Mac that's also a possibility (Mac OS X includes Perl, albeit a slightly old version). There's no technical reason to give up Windows to be able to run Linux. Just my $0.02


I've not looked into what it would take to do that. Do you mean dual boot or can I actually get linux to run on a machine that I can access via my browser?

That would be awesome if that's possible, but to answer your question, my machine is robust enough to run most software (although the laptop I'm on can barely run Windows 7 properly). I'll look into virtual box and the others and see if I can get them to work like you're suggesting.

Again, thanks so much for all your feedback It's really been very helpful.

---

### Post by trent.josephsen on 2012-12-22
With VMWare you can actually do exactly that, run through a browser (although it can be quite slow). But you don't have to, just install VMWare/Virtualbox as you would any program and you can install Linux on a virtual machine without risking your Windows install or messing around with dual booting. You won't be playing any demanding games on the VM but that's not really why people install Linux in the first place :)

VirtualBox has a free version. I haven't used VMWare lately but I think you have to pay for the desktop version (VMWare Fusion). IIRC VMWare Server (the version that works over the Internet) is free (as in beer), but it is more complicated to set up.

---

