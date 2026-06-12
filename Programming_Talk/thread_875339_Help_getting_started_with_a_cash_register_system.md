---
title: "Help getting started with a cash register system"
date: 2008-07-30
forum: Programming Talk
---

### Post by Afkpuz on 2008-07-30
Hi all.  I've been thinking about starting a mythtv store that could specialize in installing home theater systems.  My question for you all is about the cash register part.

I'd like my register to run ubuntu and have the basic functionality of a normal register, like placing orders and inventory.  

So really, I just need some help as to where to start.  I'm expecting to have to learn to program, but I would like suggestions on which kind of language to use and which kinds of cash registers would work with a given language.  also, bar code acceptance is a must for this program.  So here are the things that I would need from this register.  


1.) Inventory
Use of barcodes, manual entry, maybe integration of wireless scanner for inventory.

2.) Network connectivity
I'd like to have a separate computer on a local network that could produce an order, maybe in spreadsheet format and have the register be able to read that order and proceed with checkout.

3.) Credit card implementation
I know this would be more difficult and don't know where to start with this.  I guess implementation of a magnetic card reader and the ability to talk to credit card companies.

4.) Data backup
Obviously if I'm running a business, I need to keep records, so some way to back up order information and make it searchable.

5.) Receipt printing
I need to be able to arrange order information and print it.  I think that a regular printer would be fine, as opposed to the 2.5" receipts.  


I know this is a huge question, so if anyone has any insight as to programming language and tips, I'd greatly appreciate it.  Also, know that opening the business is not a pressing matter to me, so right now, I'd like to focus on the programming.  Once I feel confident with my register, I'll work towards the business angle.  thanks

---

### Post by mike_g on 2008-07-30
I'm making a POS system for a takeaway. I coded the software in Java and I have it running via a startup script. I'm still waiting on the reciept printer, but the idea is basically to hook the printer up to the computer and the cash register connects to the printer. The cash register the kicks out when printing the reciept.

If you are thinking of coding something like this from scratch, then its going to be a fair bit of work. If you like I can send you the source of what I have got; havent got around to putting it up on source forge yet. So far I'm the only person working on it, but if you know a little Java then you're welcome to work on it with me.

heres a [screenie ](http://i92.photobucket.com/albums/l15/mikegrundel/Screenshot-1.png)of it.

There are a few issues with it tho: The place I am making it for only deals in cash - so I havent thought about the credit card side of things yet. Nor barcodes for that matter. Also it is currently designed to run as a stand alone unit, although I plan to make it networkable connecting to a MySQL server.

Cheers.

---

### Post by pmasiar on 2008-07-31
> **Afkpuz said:**
> I've been thinking about starting a mythtv store that could specialize in installing home theater systems.  My question for you all is about the cash register part.

I'd like my register to run ubuntu and have the basic functionality of a normal register, like placing orders and inventory.  

So really, I just need some help as to where to start.  I'm expecting to have to learn to program, ...
I know this is a huge question, so if anyone has any insight as to programming language and tips, I'd greatly appreciate it.  Also, know that opening the business is not a pressing matter to me, so right now, I'd like to focus on the programming. 

No, you still don't appreciate how huge this problem is. Companies with dozens of experienced full-time programmers and support personal work years to solve it.

First, you need to learn programming. You may need to learn more than one language: see sticky FAQ. And consider that [it may take 10 years to became expert programmer](http://www.norvig.com/21-days.html).

Start with Python (see wiki in my sig). Then, find existing POS system for ubuntu, and join development - don't start your own. Satchmo ( [http://www.satchmoproject.com/](http://www.satchmoproject.com/) ) is Django-based e-commerce web app in Python.

And decide what is your skill focus. If you are businessman, focus on that, run shop and buy POS system. If you are programmer, focus on POS system, and consider making living from selling maintenance contracts to business owners.

---

### Post by mssever on 2008-07-31
I want to echo pmasiar's comment about the size of this project. Since you don't know programming right now, you'd be learning on this huge must-be-reliable system. And most code written by beginners should be thrown away eventually. Your system would be a maintenance nightmare. Start with something smaller.

My first serious programming projects were websites. When I've looked back at the code later, I'm amazed at how badly they're written.

I can say that the barcode part is fairly simple; many barcode scanners simply show up to the computer as a keyboard and type the scanned-in barcode.

But for a whole system, you're biting off a whole lot.

---

### Post by mike_g on 2008-07-31
> Start with Python (see wiki in my sig). Then, find existing POS system for ubuntu, and join development - don't start your own. Satchmo ( [http://www.satchmoproject.com/](http://www.satchmoproject.com/) ) is Django-based e-commerce web app in Python.
While it looks like a cool project, thats for an e-commerece site; not a till based POS system.

> I can say that the barcode part is fairly simple; many barcode scanners simply show up to the computer as a keyboard and type the scanned-in barcode.
Cool, I'd like to get a barcode scanner to play around with. Could you recommend one in specific that works well on linux? Or, are there generally drivers for all the major types.

---

### Post by mssever on 2008-07-31
> **mike_g said:**
> Cool, I'd like to get a barcode scanner to play around with. Could you recommend one in specific that works well on linux? Or, are there generally drivers for all the major types.
I got mine on eBay for US$35 a year ago (it was a Symbol brand handheld scanner). The most important thing to check for is what kind of connector it has. Many scanners have a connector that looks a bit like an ethernet plug. But you probably don't own any hardware you can plug it into. If you find a commercial-grade scanner with a PS2 or USB connector, you should be good to go. Just don't buy anything that uses an LED or something for its light source as you'll have a hard time getting a good read. Also, you can pick up those CueCat scanners for next to nothing, but out of four I tried, several didn't work at all and the best one would only give me a read 25% of the time.

EDIT: One other thing: The scanners I've messed with decode barcodes in firmware, so be sure that the scanner you use can decode the type of barcodes you want to use. Generally, that's not a problem, though because the scanner will probably support all the common types. Also, you can install the barcode package to create barcodes. KBarcode is the only Linux GUI for the purpose, though it didn't work well for my purposes.

EDIT 2: As far as drivers go, scanners typically present themselves as keyboards, so you should be good to go.

---

### Post by Reiger on 2008-07-31
The difficulty with this is the obvious security/reliability issues involved. Registering means setting up a database means making sure that "box" is far from harm. That's quite diffuclt; many subtle and unforeseen issues can easily become the bane of it.

Then there's the application itself. That sort of stuff usually is pretty complicated because -- all security mechanisms/problems surrounding your database exist on this level also. Also, you need to prevent what is known as XSS.

Then there's the website itself. Writing a good website is a bit of an art, what now with dozens of browsers which are flat out incompatible with each other. OK, granted you can get away with the top 10 most-used; likely -- and using a minimalistic approach to XHTML you can avoid a lot of the more difficult-to-fix problems (resulting from aforementioned incompatibility issues, mostly)...

But you need to make sure that your website is decent-looking; that you have some JavaScript going on in order that your customers can do stuff without making a call to the server each time they click a button...

=== So that makes:
0 ) Acquiring a very, very large amount of patience...
1 ) Getting familiar with your webserver and your operating system on sysadmin level ++
2 ) Acquiring a good reliable working knowledge of Databases and the basic theories behind them
3) Acquiring a good reliable working knowledge of Web Security, and some thechniques
4 ) Learning a dialect of SQL
5 ) Learning some language to handle the server-side application stuff
6 ) Learning XHTML
7 ) Learning CSS
8 ) Learning JavaScript, JScript, ECMAScript <- names for what is basically all the same, but yeah... cross-browser incompatibilities..
9 ) Learn about & ways around browser issues
10 ) Make it all look good
11 ) Test
12 ) Debug
13 ) Remain patient a good while longer...

---

### Post by Afkpuz on 2008-07-31
Yeah, I know it is a big project.  But then again, I don't see myself opening this business for many years.  So I figured it would be good to start learning now while it's only an idea in the back of my head.

So I guess I just would like some direction as to which languages I should start to learn with a POS system as a long term goal.  I can hold off on the web site stuff for now.

---

### Post by drubin on 2008-07-31
> **mike_g said:**
> 
There are a few issues with it tho: The place I am making it for only deals in cash - so I havent thought about the credit card side of things yet. Nor barcodes for that matter. Also it is currently designed to run as a stand alone unit, although I plan to make it networkable connecting to a MySQL server.


Desktop Java applications that connect directly to a MYSQL /any other DB  directly are a huge security flaw.

Java code is incredibly easy to reverse engineer  and have direct access to the data base. 

DELETE * FROM products;

---

