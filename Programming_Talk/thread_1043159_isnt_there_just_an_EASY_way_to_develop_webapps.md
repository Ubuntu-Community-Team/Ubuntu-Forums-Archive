---
title: "isnt there just an EASY way to develop webapps?"
date: 2009-01-18
forum: Programming Talk
---

### Post by jabibi on 2009-01-18
I'd like to make a webapp, but since its purpose its the administration of my business, the way i wanna do it then its a sort of a complex application


but i'm not an experienced programmer all i know is some C which I already forgot, Java which i manage to get around thanks to netbeans code completion and GUI designer and also some sql.

But rather than making a desktop app, I'd like to access it from a web browser.

So This is the main question of this thread:

I havent found any way that i can easily design a GUI and add events to it and code it. I once used JSP long time ago for a small and simple app but I dont like the fact that it has to refresh the page on every change.
AJAX seems so complex and it looks like it has all to be done manually.
Maybe something like this just doesnt exist?

I tried with Zope which seemed to be very good but I didnt even understand how to use it, didnt even know where do to put the python code hahaha (i'd still have to learn python), read some docs about it and nothing maybe i'm just too dumb now and i'm stuck with the little I learned on using netbeans

Its not that I wouldnt want to learn I just dont have much time to dedicate to it everyday.


So....... any recommendations?


on the other hand, I could resign to the web idea if it gets to heavy and just stick to a desktop app with netbeans which is also cool but I have zero experience with printers (I will be needing to print bills, invoices, reports) both to physical paper and PDF, is it too difficult with java? anybody know some good printing tutorials?



you might get the idea that i'm too lazy but it's just that i'm not a programmer, just a regular guy with little time and basic programming skills trying to get some advice

---

### Post by pp. on 2009-01-18
> **jabibi said:**
> administration of my business, the way i wanna do it then its a sort of a complex application ... but i'm not an experienced programmer

That way lies ruin. If you're short on time and write your own application to drive your business, you'll most probably wind up still shorter on time and with an application which requires more fiddling than it saves for your business.

I'd advise to find an open source app which comes close to the way you want your business run, or perhaps even a closed source one, if that meets your requirements better.

Having said that, both Ruby on Rails and Django are reputed to be easy ways to build web applications. I haven't tried either, though.

---

### Post by Tomosaur on 2009-01-18
There's no need to make things complex for yourself. Making a web application which can even come CLOSE to the functionality of a desktop application is no mean feat. Sure, there are some very nice web apps out there which are incredibly impressive compared to their desktop counterparts, but unless you have the time and know-how to implement it, you're better off just staying well clear.

I don't know what business exactly you need to administer, but if there's any particular reason why you need access to one machine at all times, you can just use remote desktop, or even just a simple networked app. Without more details about what exactly you want to do, it's difficult to help you out.

---

### Post by jabibi on 2009-01-18
what i want to do is a program for managing inventory, sales, expenses, clients, providers, printing sale invoices & bills, etc etc, i've already somewhat modeled the whole database structure, it's about 50 tables

I already got a commercial desktop app but it's really lousy and unreliable i've almost lost my data several times already, and reporting tool is just terrible, quality software is just too expensive in my country plus there are none available that will work with sql DB's like Postgre, i've only got a small shop and thats why i want to make my own software, as i already said i'm no expert but i'm capable of it, just need some help from time to time. and choosing the tools of the trade is an essential decition I rather consult with the community

remote desktop could be an interesting idea. Also i've been reading a bit about javafx, it's looking okay.


networked app was my alternative but i mostly wanted a web base application because (besides the ability to access it from any computer on the network which i need to do too) when the time comes to print something to paper I could just print it out from the web browser since i really dont have a clue how to print anything from a regular desktop application on any programming language




**PP** do you know any specific names of these open source business apps you say? i might check them out but i'm not sure if theyll work for me since i'm not in the US and things always change from country to country, like the types of taxes and how theyre charged, stuff like that, plus my coworkers dont speak english either




**Tomosaur**, which languages/tools for webdev would you recommend me to start trying out and decide which one might be best for me?



what do you ppl think of javafx? is it cut out for this kind of things?


in case i just end up with regular desktop app, any recommendations on the "printing" subject?

---

### Post by wmcbrine on 2009-01-18
Why not hire someone to do it for you? That's easy (just costs money). I think it's usually the appropriate solution, assuming the business itself isn't web design. :)

---

### Post by pp. on 2009-01-18
The kind of software you're looking for is commonly called "ERP". I just googled for "open source erp" and got a number of hits which looked all very promising. I presume that you can find out which of those support your language(s) of choice without too much difficulty.

Please understand that I do not know any of those products even by reputation. I just tell you that there are so many products out there that it would be somewhat surprising if you couldn't find one that meets your needs.

Writing a useable application based on 50 or so tables and maintaining it after that is not a task I would entrust a beginning programmer with, and I would not entrust my business to the application written by such.

---

### Post by cybrid on 2009-01-18
I must agree with the rest of the people of the thread. I work as J2EE developer professionaly and designing, developing and maintaining an ERP, even a small one, is not an easy task. You should either hire a professional developer or find and use the opensource solution that best suites your needs.

---

### Post by DocForbin on 2009-01-18
What features of this web app would require dynamic/rich "technologies" like ajax or javafx?

Plain ole PHP is *extremely* easy to learn, and is supported in recent versions of NetBeans, as is Ruby on Rails.

No offense, but you don't sound particularly interested in learning any language/framework. Designing the gui is probably the trivial part here, and no tool is going to build a inventory/billing system for your business. Why not find something open source that meets most of your needs and you can customize. Or just hire a programmer.

---

### Post by module0000 on 2009-01-18
If you did decide to use an existing desktop app...I would recomend you look at OpenOffice Base, it's similar to microsoft access.  It lets you design backend database, front-end GUI's, and has wizards to make several visually appealing reports.  All this can be printed and whatnot without any programming know-how.

If you are going to design it yourself though, PHP is a sensible choice for a webapp, and won't take more than a day or two to understand and be functional in.

Best of luck to you with your project.

---

### Post by Reiger on 2009-01-18
Please consider the following points:
[list="1"]
[*]Presumably you're dealing with sensitive information. You presumably want to keep it safe.
[*]You want to do file access. That is inherently unsafe when the service is publically available. If not that's another matter.
[*]You want a GUI. That is inherently troublesome.
[*]You want reliability.
[*]You presumably have physical access to the device on which the maintainance is to be performed. That machine is presumably connected to I/O devices like keyboard, mouse and monitor.
[/list]

So if you just voted yes on all accounts (especially when you agree that your machine is not to be publically available anyways) then you are better off using a stand-alone, desktop-type application. Why? Adding a remote component into the mix is going to make the whole thing a lot more complicated:
-- Remote means that you must take additional things into account: persistency (data must somehow be actually stored not thrown away after the HTTP connection expires), consistency (data must be consistent both at the front as well as the back end), security (especially if you use a public network such as the internet to make your remote calls).

If others must at all times be able to access the machine, then you'll have little choice but to go for a networked solution.

Plus you want to do printing, which in the remote case would require you to do additional work on getting something decent on paper (plain HTML/XHTML doesn't render well on paper) you will want to look into either some kind of 'built-in' support for printing (Java has packages for that IIRC) or an 'intermediary format' such as PDF.

---

### Post by jabibi on 2009-01-19
alright guys thanks all for your time & suggestions

i've been researching some commercial apps and open source ones as well, need more time checking them tho


nevertheless i'm gonna start practicing making small trivial applications, because i Do want to become better at programming

---

