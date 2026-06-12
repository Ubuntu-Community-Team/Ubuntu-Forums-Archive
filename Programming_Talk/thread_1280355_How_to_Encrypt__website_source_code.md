---
title: "How to Encrypt  website source code?"
date: 2009-10-01
forum: Programming Talk
---

### Post by hockey97 on 2009-10-01
Hi, I would like to know where I can learn how to encrypt html,php code. 

I want to prevent others from stealing my own code,artwork, and reading how my website is structured. 

I googled around and only been finding products on the net that cost 100 bucks or  more to buy the software that will do it. 

I would rather find a free way of doing this.

---

### Post by ninjapirate89 on 2009-10-01
> **hockey97 said:**
> Hi, I would like to know where I can learn how to encrypt html,php code. 

I want to prevent others from stealing my own code,artwork, and reading how my website is structured. 

I googled around and only been finding products on the net that cost 100 bucks or  more to buy the software that will do it. 

I would rather find a free way of doing this.

Using my limited knowledge of web design and such, I would say that PHP is server side and can't be copied and basic HTML won't give them much of an idea on how your site is structured. I don't know what to say about people copying your images though.

---

### Post by mobilediesel on 2009-10-02
The only sure way to prevent people from copying your stuff is to keep it offline. If you put it on a publicly accessible website, people will take what they like.

---

### Post by wmcbrine on 2009-10-02
> **hockey97 said:**
> Hi, I would like to know where I can learn how to encrypt html,php code.Forget it. The nature of HTML is that the browser needs to see it in order to render it. You can't encrypt it. At most, you can obfuscate it.

> *I want to prevent others from stealing my own code,artwork, and reading how my website is structured.*Too bad. 

BTW, as I general rule, I've found that the people most concerned about this are the ones who have the least to worry about, in terms of having anything worth stealing. Of course I haven't seen *your* pages, so no doubt you're the exception. :)

---

### Post by nvteighen on 2009-10-02
Hm... FYI, some years ago, MS created a device that "encrypted" embedded JScript (in this case the distinction with Javascript *is* important). Actually, that "encryption" was some sort of bytecode compilation, possibly just precompiling the scripts exactly the way IE 6 did in any regular page, but just doing it before. That "JScript encryptor" dissappeared really soonly, but can be taken as a project aiming to the "encrypted" web development idea.


Of course, that compiled code was only IE 6 compatible ;)

---

### Post by Simian Man on 2009-10-02
You definitely can't keep people from stealing your images.  At the very least they can take a screenshot of your page and get the images out with a paint program.

And I think it's extremely foolish to be worried about people stealing your HTML code.  The web is full of free HTML code, why would yours me so much more valuable?

The best you can do is implement as much logic as you can in server side PHP code, which a browser never sees, as opposed to Javascript, which the browser has to see.

It's pretty silly to ask this, especially on a forum dedicated to open source software :).

---

### Post by wojox on 2009-10-02
Just Google: html obfuscate or php obfuscate

---

### Post by kavon89 on 2009-10-02
That's like saying you want to hide the words of your book. Best you can do is obstruficate your code before publishing it, looks the same to a machine but would make anyone loose interest in your website quickly... however would make you look like you write bad code.

---

### Post by uljanow on 2009-10-02
Try disabling the context menu. :P

---

### Post by Simian Man on 2009-10-02
> **uljanow said:**
> Try disabling the context menu. :P

You can still do View->Page Source or Ctrl-U (not to mention downloading with wget).  Disabling the context menu would only fool *really* inept people.

---

### Post by hessiess on 2009-10-02
> **uljanow said:**
> Try disabling the context menu. :P

Try disabling JavaScript ;)
As already stated by all the previous posters, Preventing people from seeing your HTML/CSS/Images is *completely* imposable. Your best bet is implementing everything server side (better for security/accessibility anyway) and using a copyright notice.

---

### Post by NoaHall on 2009-10-02
If you want to disable the context menu, so they can't right click, do

<body oncontextmenu="return false";>

on every webpage you want right click to be disabled. This will stop most people from stealing your images, at least.

---

### Post by hockey97 on 2009-10-02
> **kavon89 said:**
> That's like saying you want to hide the words of your book. Best you can do is obstruficate your code before publishing it, looks the same to a machine but would make anyone loose interest in your website quickly... however would make you look like you write bad code.

No not really. It's not like if I made a book I want to hide the words inside the book. That's a wrong analogy. It's more like for example lets say I made a book. I have to choose a well known publisher but all publishers want me to label in each book how I made it meaning what machines I used to produce this book and who wrote it and the address of the person that wrote it.  What I want to do is still provide this information only to the publishers but scramble the contact and machine info so only the publisher can read this. 

What I am saying is if you google encrypt html websites. You get a load of results with many products on the market that claims it will encrypt your source code meaning html. So when a person clicks view source in a browser  it will show nothing but encrypted information something no human can understand.

They even claim that they can prevent people from obtaining  the legit image url making it harder for someone to just save the images and then transfer them. The reason is that when source is displayed in the browser for the user or the user used any editor it will be viewed as encrypted. Yet when the browser wants to render the html it will then decypt it  before th browser will read it. 

From what I was explained is that any editor software just like view source or any textual program/software it will be viewed as encrypted information. The browsers will only see the true html code.

here is one website that has such software: [http://www.byterun.com/html-protector.php](http://www.byterun.com/html-protector.php)

if you google encrypt html websites. You will find many software out their that claims what I explained above. 

I thought you can encrypt the html code  but only decrypt it when the browser is ready to render it.  So the browsers will only see the true code.


I may not have anything of value right now but want to prepair if I decide to hire professional artists or something down the road. I rather not pay 5,000 and watch that work get stolen and used on many websites.

Here is another site offering another software package to prevent hackers to hack your site or prevent attacks. They even said no one can steal your images and no one can copy your website to their computer meaning offline copying of the website. No one can copy your source code of the site meaning javascript and html.


I want to make it harder to anyone to try and steal images or code. 

I really don't care if html code is free on the net. 

html code on the net that is free dosen't give the code in ready website format. Meaning you can't just download all html code that will get you a ready made website where they can then just make small changes to get a full working website going. I know their is free templates online . 

You just telling me like for example. Wall mart shopping centers has a oranized floor plan for most of their stores. I mean if anyone can walk in the store look at the floor plans and how everything is setup and see how they display their wall mart logos on stuff. Why not have me a small business just go out and start building a shop that uses everything what wal-mart did. So I have a mini look a like wal-mart. I start making millions because people now think I am a wal-mart shop. 

This is illegal. Even though html code is free all over the net the difference is that the html code is a tool or resource to assist building a site. Just like cement and bricks are used for building commercial stores. I mean if you look most of the shops use brick and cement and paved tar on their lots. It's a common thing but what makes those shops different? Is it the design of the structure?  It's mainly how the person uses those tools and resources to make their creation. The creation is what makes each store or in this case each website different. 

So saying that html code is free on the net why not allow people steal my html code?  The reason is how you used the html code to make the website is how the websites look different.  

Since they have access to html code they have access to the css code and javascript code. 

I know php is not shown. but their is ways to download the .php file. I forgot how it's done. Some hacker told me and I followed what he said. I then somehow got a prompt asking me if you would like download domain.com/login.php  So I clicked yes and then opened it in my editor and saw all the php code of my login script. 

I want to just take measures to prevent hackers or people stealing data from my site. 

Cause If I don't get a handle on the hackers no one will want to use my website. I mean would you like to put your personal information on my site knowing that hackers can easily hack my site and steal your personal information?

I came on here asking because I seen many program software that claims that they can encrypt and prevent hackers  or anyone from stealing data from your website. So I asked here thinking that you guys may know a way or some open sourced lib or software that can do such a think. Cause the softwares I found cost money. 

I even did see on some professional websites of big corps that when I view their source code I can't read their html tags or anything like that it gets rplaced with numbers and % signs with & signs and some letters that really mean nothing to a human when read.

---

### Post by hessiess on 2009-10-02
For the browser to be able to display it it must be able to decrypt it. This means that the decryption code must be in the source, meaning that anyone can decrypt it. This is not encryption but obfuscation.

Also search engines only see your page source, they do NOT run JavaScript. So say goodbye to any chance of getting a good result from search engines.

If you are that paranoid about protecting your data, don't put it on the net, end of.

---

### Post by hockey97 on 2009-10-02
> **wojox said:**
> Just Google: html obfuscate or php obfuscate

Thank you, That is what I was looking for. I now found some open source packages. So I will use them.

Is their any website or place that can teach me how this is done? I am interested on how to make the codes myself. I am not going to make them but just for learning purposes would like to see whats done behind the scenes. I will google for it.

---

### Post by nvteighen on 2009-10-02
> **hockey97 said:**
> 
I want to just take measures to prevent hackers or people stealing data from my site. 


If you stay with a proper Model-View-Controller design, the HTML (the "View" side) will just show presentation code, no data. What you need is proper design, not encryption.

---

### Post by ve4cib on 2009-10-02
Obfuscation does not make it impossible for people to steal your code.  In fact, if you've got a really slick-looking page that everyone (apparently) wants to steal then obfuscating it might even make them *more* likely to produce an exact-copy of your page; they can't easily go in and change attributes or modify parts of it.  So either they'll move to another site (your preference) or they'll just give up trying to change it and just use what you've given them.

As for stealing images and text, that is, quite frankly impossible.  As soon as the image is displayed in the user's browser it's likely to be cached (i.e. saved on their HD) where they can fetch it offline.  Or they can print-screen the page.  Or they can look up the URL in the code.  Or any combination of the above.  The only way to keep your images private is to keep them offline.


EDIT:

I just tried the demo version of that HTML Protector product you linked to.  It took me less than 30 seconds to get a plaintext version of the HTML.  Open the page in Firefox, open Firebug, click on the HTML tab --> Edit HTML, select all, copy, open up Geany, paste.  Remove the spurious "This page is protected by blah-blah" divs.  Done.  And they charge how much for this product?

---

### Post by johnl on 2009-10-02
> **NoaHall said:**
> If you want to disable the context menu, so they can't right click, do

<body oncontextmenu="return false";>

on every webpage you want right click to be disabled. This will stop most people from stealing your images, at least.

When I come across a website that does this, it pisses me off to no end.  I like to use the right click context menu to do things like go back, open in new tab/window, refresh, view image, etc.

Besides, it's not like disabling the context menu accomplishes anything except screaming 'this site designed by amateurs'.  If someone wants to 'steal' your HTML or images, it's not hard.  Your website is serving them.

---

### Post by NoaHall on 2009-10-02
It does slow people down, and there are bEtter ways, such as stopping of dragging files into a new tab.

It does not say amateur, it says someone who has thought of everything.

---

### Post by wmcbrine on 2009-10-02
It says paranoid *and* amateur.

---

### Post by NoaHall on 2009-10-02
You obviously have no idea on how to make a secure website, so don't post in this thread.

To OP ->

One way you could ensure nothing happens to your images, is to watermark them. You can do this either with php, or manually.

html isn't really worth stealing.

---

### Post by johnl on 2009-10-02
> **NoaHall said:**
> You obviously have no idea on how to make a secure website, so don't post in this thread.

To OP ->

One way you could ensure nothing happens to your images, is to watermark them. You can do this either with php, or manually.

html isn't really worth stealing.

Disabling the context menu has nothing to do with making a 'secure' website.  All it does is disable a piece of useful functionality for the user.  It doesn't stop anyone from viewing source or downloading images.

---

### Post by NoaHall on 2009-10-02
It can HELP stop. It doesn't have to really totally prevent that, as that takes a advance bit of coding, but it's good to prevent the masses from working out how to do.

Also, it can be enabled by typing some code into the address bar.

---

### Post by MadCow108 on 2009-10-02
> **NoaHall said:**
> It can HELP stop. It doesn't have to really totally prevent that, as that takes a advance bit of coding, but it's good to prevent the masses from working out how to do.

Also, it can be enabled by typing some code into the address bar.

it does not take an "advance bit of coding" its impossible by design except you force some weird browser which messes with the system onto the user.

luckily some browsers (like opera) don't even allow pages to mess with the context menus, I hate it when pages do that (and not because I want to steal stuff...)

---

### Post by supirman on 2009-10-02
> **wmcbrine said:**
> it says paranoid *and* amateur.

+1

---

### Post by NoaHall on 2009-10-02
> **MadCow108 said:**
> it does not take an "advance bit of coding" its impossible by design except you force some weird browser which messes with the system onto the user.

luckily some browsers (like opera) don't even allow pages to mess with the context menus, I hate it when pages do that (and not because I want to steal stuff...)

I didn't mean with javascript - you can create it so the image files are embedded in such a way that they don't exist when you download them.

Take a look at this site ->
[http://bilddagboken.se/p/frontpage.html](http://bilddagboken.se/p/frontpage.html)

There is only one way to download the images, if they are HD, as they become proper jpg's, not just gifs, and on the image front page.
Click on the images, so you get the larger version, and then see if you can download it.
Although, this site is mainly a mix of js and php.

---

### Post by MadCow108 on 2009-10-02
yes that totally worked....
it took me less than 5 seconds to get the HD version. That is the time it took to open my browser cache (and my pc is very slow :) )
(with plugins and javascript enabled)

and with firebug its easy to get the url of the picture itself, a little spacer gif on top of your pictures only stops the computer illiterates from downloading

---

### Post by NoaHall on 2009-10-02
No no no xD Not the HD version, the normal pictures. They've messed up the HD side of it. You'll see the images are stored as "spacer.gif" which when downloaded is just a blank image.

---

### Post by MadCow108 on 2009-10-02
no their not.
The spacer.gif is a transparent gif lying on top of the image. (a very old technique... already saw that in the nineties, and it was just as easy to circumvent back then)
go underneath that and you have the real picture (in every view I found on that page).

---

### Post by NoaHall on 2009-10-02
Hm, I'm unfamiliar with that one. Explain how you solved it?
I know how to get the file, but I don't understand how it works. The gif is placed on top of the real image?

---

### Post by MadCow108 on 2009-10-02
you just place a transparent gif of the same size on top of your picture.
When you now right click onto the picture to save it you get the gif instead of the picture underneath.

This doesn't prevent the picture from being cached on the disk by the browser or a html debugger (like firebug or dragonfly) to navigate below the gif to the real picture.

---

### Post by NoaHall on 2009-10-02
Ah, really? On Windows, I believe that site used to prevent a cache too, because it wasn't there when I used to use vista.

---

### Post by Cope57 on 2009-10-02
Use this and save it as index.html

```
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>This Page Intentionally Left Blank</title>
<meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />
<style type="text/css">
/*<![CDATA[*/
 div.c1 {text-align: center}
/*]]>*/
</style>
</head>
<body><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />
<blockquote>
<div class="c1"><strong>This Page Intentionally Left Blank</strong>
</div>
</blockquote>
</body>
</html>
```

If you seriously want to encrypt websites and code, why post it in the first place?
Keep it on your encrypted hard drive, in a fireproof safe, and remove any hardware which allows connection to the Internet.  I am sure your content would be safe then. **[/sarcasm]**

---

### Post by wmcbrine on 2009-10-02
BTW, the "Nuke Anything" extension is good for removing junk like invisible overlays, although it's been a while since I ran into that silliness. But just today, I saw a site that rendered its full content, then threw up a "you must register to read this" overlay. But, in fact, I didn't. :)

NoaHall, blocking right-click has nothing whatsoever to do with making a web site secure. The one and only way to secure your data is to not present it to the user in the first place. I'm sorry that you and the OP are confused on this point, but it's reality.

---

### Post by NoaHall on 2009-10-03
I know that it doesn't really make it secure, but what I'm saying, is that it will slow down the ignorant masses from downloading your pictures.

---

### Post by Can+~ on 2009-10-03
> **NoaHall said:**
> I know that it doesn't really make it secure, but what I'm saying, is that it will slow down the ignorant masses from downloading your pictures.

Funny that you were fooled by that old trick too. I could download it with ease on Chromium.

But then the ignorant masses talk to their geek friend, bother them to death, and they send them the full link.

Everything what you see on the web is currently being cached on your memory (and hard drive). And as my brother once told me "Once that something is on the client side, it's not yours anymore.".

From the OP:

> I know php is not shown. but their is ways to download the .php file. I forgot how it's done. Some hacker told me and I followed what he said. I then somehow got a prompt asking me if you would like download domain.com/login.php So I clicked yes and then opened it in my editor and saw all the php code of my login script. 
If you don't want something to be "stolen", then don't put on it on the web on the first place.

Yes, because you're an ignorant on terms of security. I've answered all your previous questions (I remember when you were trying to store HTML pages as strings on a database).

PHP, or any server languages with Apache, is safe as long as it can only be read by apache, processed and sent to the client side as a finished html structured file. I'm betting that your apache server or folder is not configured properly.

> I want to make it harder to anyone to try and steal images or code.

That's why there are Creative Commons and other licences. Say:

[LIST=1]
[*] A single person that "steals" your image, won't do much with it, probably make a signature, an avatar, or whatever.
[*] A company that uses your image on their website and uses it to sell product, are a target for a lawsuit.
[/LIST]

See? Individuals copying things are meaningless. You can make as many analogies as you want about Stealing on real life, but none  of them can be applied here, because digital information is that, information, it can be replicated, as opposed to real life objects. (Are you reading this, RIAA?)

Now, if you insist on this, I will give you some hints:

[LIST=1]
[*] Most "background" imaging and things for layout are rarely stolen, pretty much because this things are totally generic, so you're safe here.
[*] If you want to sell art, or music, or something, don't put it directly on the site, have a lower resolution, shorter version preview, and have PHP provide a limited download, like a hash key that will be valid for a while. Just take a look at rapidshare or megaupload, they never give you a direct link, everything is processed by their servers.
[*] If you want to publish your own images/screenshots, you can add a watermark on them (See: Gamespot logo on images, etc).
[/LIST]

---

### Post by NoaHall on 2009-10-03
I wasn't fooled by the disabling of context menu. I hadn't come across the transparent gif on top of jpg before.

---

### Post by TheBuzzSaw on 2009-10-03
I'll just reiterate.

There is zero value in encrypting/protecting your HTML. The best web developers in the world leave their HTML/CSS exposed. There is nothing mystical that you could possibly have in your site that either has not been done already or could not be replicated with minimal effort. HTML and CSS both feature *extremely limited* syntax. A web developer's value comes in his/her ability to wield these tools and produce good content on the fly customized for particular needs. The time you waste trying to protect your HTML would be much better spent simply making the site better.

I do web development professionally. I take web standards very seriously. I guarantee that if I looked at your HTML, I would see several things that you need to fix.

As for your images, again, forget it. Casual saving/sharing of your images is not going to harm your bottom line. That operates under the premise that your images are even worth sharing. Do not overvalue your content. There are 500+ ways of extracting images now matter how you "protect" them.

You have to think realistically. The only people who would even consider "stealing" your stuff are people just messing around with experimental layouts. No one would put out a professional site consisting of your content. Stick a copyright notice in your footer and be done with it.

I will never understand this attitude of "look but don't touch" on the Internet. Either put your content out there or stick it in a safe. Stop trying to dictate others' behavior.

---

### Post by NoaHall on 2009-10-03
Well, like I said before, to stop copying of your images, you could use a watermark, so people know where it came from, and thus promoting your site on others when they don't even mean to. You can do this manually offline, manually online, or use a php to do them all on the fly.

---

### Post by TheBuzzSaw on 2009-10-03
> **NoaHall said:**
> Well, like I said before, to stop copying of your images, you could use a watermark, so people know where it came from, and thus promoting your site on others when they don't even mean to. You can do this manually offline, manually online, or use a php to do them all on the fly.
This assumes that there will be lots of art that needs to be protected. What about images used primarily for site effects? (Borders, backgrounds, etc.)

---

### Post by NoaHall on 2009-10-03
Well, borders and backgrounds are easy to reproduce anyway, as are all vector images.

I was thinking more of protecting his artists images from being copied.

---

### Post by nvteighen on 2009-10-04
> **NoaHall said:**
> 
I was thinking more of protecting his artists images from being copied.

The current trend to do that is using Adobe Flash galleries. It's the most efficient way by far.

---

### Post by TheBuzzSaw on 2009-10-04
> **nvteighen said:**
> The current trend to do that is using Adobe Flash galleries. It's the most efficient way by far.
Screenshot. :)

---

### Post by nvteighen on 2009-10-04
> **TheBuzzSaw said:**
> Screenshot. :)
Heck... I can't think of any right now... and I can't find my mother's art teacher website, who did that in there...

But if I just happened to invent it (which I'm sure I'm not) it's not a bad idea, is it? :P

---

### Post by NoaHall on 2009-10-04
You didn't invent it, it does exist :). I've used it once or twice, but not since moving full time to Linux.

---

### Post by TheBuzzSaw on 2009-10-04
I'll just say that updating HTML is much easier than updating Flash.

---

### Post by wmcbrine on 2009-10-04
There are tools to rip images from Flash, and I've done that as well. But yeah, in the end, if you can see it, you can grab a screenshot. It means you'll lose a little bit of quality if you have to recompress it to JPEG, but that's about it. That's what all this stuff comes down to, in the end: a slight degradation in the user experience. Preventing copies? Never, not once.

---

### Post by Khushboo_khan on 2009-10-08
well php is a server side scripting language and no one copy your php code becouse it is not shown to the user. and you can't keep people from stealing your image becouse they copy paste it in to paint.

---

### Post by hockey97 on 2009-12-09
well, I found some libs that encrypts the whole websites code.
It protects from anyone from copy and pasting images right from the site. It does claim to prevent a screenshot... what it does is that where images are being displayed it would load in a black box as the image when it detects a screenshot being taken placed while the browser is running. 
I don't know how true this is but hear many others online use it and they claim that they couldn't steal any images from their site. I can also change the black box to a image that I want to be displayed instead of the regular images. This could be like a image with text saying copyright infringement. 

Right now I don't think I have any good images created or artwork made like the graphics that is worth while. I just want to protect the site just in case some time down down in the future I might hire a artist to make my website graphics and would hate to get ripped off finding other websites using such artwork.

the source code get's encrypted when the browser ask to display the raw source code using view source code. That's only when the client tries to view the source code. Other then that it's in the raw source code state allowing the browser to render the code properly. If you don't know the images source link then your can't steal such a image.

The lib is a php lib and their is some bash script and addons to apache server which allows this lib to function properly. 

It also is high end secure and monitors client activities and can figure out if the person is attempting to hack the site.

---

### Post by CptPicard on 2009-12-10
You know, even assuming that this thing works, it is worthwhile asking why even sites that actually do have something worth "stealing" do not bother with such "protections".

You wouldn't happen to have a live example of a site that uses this?

---

### Post by wmcbrine on 2009-12-10
> **hockey97 said:**
> well, I found some libs that encrypts the whole websites code.Sucker.

---

### Post by grayrainbow on 2009-12-10
> **hockey97 said:**
> well, I found some libs that encrypts the whole websites code.
It protects from anyone from copy and pasting images right from the site. It does claim to prevent a screenshot... what it does is that where images are being displayed it would load in a black box as the image when it detects a screenshot being taken placed while the browser is running. 
I don't know how true this is but hear many others online use it and they claim that they couldn't steal any images from their site. I can also change the black box to a image that I want to be displayed instead of the regular images. This could be like a image with text saying copyright infringement. 

Right now I don't think I have any good images created or artwork made like the graphics that is worth while. I just want to protect the site just in case some time down down in the future I might hire a artist to make my website graphics and would hate to get ripped off finding other websites using such artwork.

the source code get's encrypted when the browser ask to display the raw source code using view source code. That's only when the client tries to view the source code. Other then that it's in the raw source code state allowing the browser to render the code properly. If you don't know the images source link then your can't steal such a image.

The lib is a php lib and their is some bash script and addons to apache server which allows this lib to function properly. 

It also is high end secure and monitors client activities and can figure out if the person is attempting to hack the site.
You realize that if I want to steal images from "encrypted" site, I won't use my Opera, don't you? Just like if I steal your car, the court is the only option for copyright violations.

---

### Post by TheBuzzSaw on 2009-12-10
*ignore/delete*

---

### Post by TheBuzzSaw on 2009-12-10
*ignore/delete*

---

### Post by TheBuzzSaw on 2009-12-10
Anyone who honestly contemplates using such anti-copy technology doesn't really understand the world he/she lives in. Are you fully aware of what all is involved in copyright infringement? When was the last time you saw a **professional** site blatantly copy another site? From there, who even *wants* a copied site? People hire designers to achieve that unique look. Go ahead; next time you hire designer, tell them you are hiring them "strictly to avoid copyright infringement". Nevermind the designer's talents and unique perspective...

People ripping content generally fall into one of the following categories:

(A) -- They are casual web consumers who simple want to save the content for future viewing offline and/or in case the web site goes down later. This is a compliment to the content creator in that the content was good enough for someone to want to preserve it.

(B) -- They are kids or young web designers who are just screwing around. They wanted a quick layout for some little video game community or something like that. Again, this is a compliment and does nothing to devalue the original. They are not profiting off anything.

(C) -- They are professionals who run their own sites who know better than to blatantly copy others' content. Copying is social suicide. This is the Internet. If someone copies others' content, people will find out, and they will find out **quickly**. The truth will be made known.

The bottom line is that people are more honest than you give them credit for. So, exactly which group are you hoping to deflect with this protection scheme?

---

### Post by CptPicard on 2009-12-10
... that, and that most websites are essentially "unique products" by their nature. The way they put stuff together on the site serves the purpose of presenting that exact site to the world. There only thing worth mimicking is usually some general technique being made use of on the presentation side, and that sort of stuff is not under copyright.

---

### Post by A_Fiachra on 2009-12-10
Isn't php obfuscated by its nature?

I read it and get a headache.

:-p

---

### Post by Reiger on 2009-12-10
<ringing-voice>
*It's not going to work...*
</ringing-voice>
<exasperated-voice>
You see this? That's a browser. A browser which lets you disable bits and pieces of JavaScript at will; even inject bits of your own.
</exasperated-voice>

---

### Post by nvteighen on 2009-12-11
> **TheBuzzSaw said:**
> 
People ripping content generally fall into one of the following categories:

(A) -- They are casual web consumers who simple want to save the content for future viewing offline and/or in case the web site goes down later. This is a compliment to the content creator in that the content was good enough for someone to want to preserve it.


Something usually not considered as copyright infringement...

> 
(B) -- They are kids or young web designers who are just screwing around. They wanted a quick layout for some little video game community or something like that. Again, this is a compliment and does nothing to devalue the original. They are not profiting off anything.


Something that nobody will care about and in some places like Spain it wouldn't either be copyright infringement because there's no profit.

> 
(C) -- They are professionals who run their own sites who know better than to blatantly copy others' content. Copying is social suicide. This is the Internet. If someone copies others' content, people will find out, and they will find out **quickly**. The truth will be made known.


Which means idiotic behaivor.

Please, I think this thread has enough arguments against this "source obfuscation" idea. Again, year ago Microsoft tried to push its JScript compiler and didn't work ([http://msdn.microsoft.com/en-us/library/cbfz3598%28VS.85%29.aspx](http://msdn.microsoft.com/en-us/library/cbfz3598%28VS.85%29.aspx))... People started to disable right click, but weren't aware that anybody could fetch their page (wget or whatever... even using "Save As..." in your browser) and look it in a text editor...

---

### Post by abhilashm86 on 2009-12-11
website is public!! for sake, please don't hide your code!!
i've a [personal website ]("http://abhilash.co.nr/")  done using adobe flex, i've shown the code!! 
there is thrill and improving of a product when code is public
foss--> show me the code!!

---

### Post by nebu on 2009-12-11
try using .htacess files

apache will let u set permissions for external user on htacess

---

### Post by hockey97 on 2010-03-21
> **TheBuzzSaw said:**
> Anyone who honestly contemplates using such anti-copy technology doesn't really understand the world he/she lives in. Are you fully aware of what all is involved in copyright infringement? When was the last time you saw a **professional** site blatantly copy another site? From there, who even *wants* a copied site? People hire designers to achieve that unique look. Go ahead; next time you hire designer, tell them you are hiring them "strictly to avoid copyright infringement". Nevermind the designer's talents and unique perspective...

People ripping content generally fall into one of the following categories:

(A) -- They are casual web consumers who simple want to save the content for future viewing offline and/or in case the web site goes down later. This is a compliment to the content creator in that the content was good enough for someone to want to preserve it.

(B) -- They are kids or young web designers who are just screwing around. They wanted a quick layout for some little video game community or something like that. Again, this is a compliment and does nothing to devalue the original. They are not profiting off anything.

(C) -- They are professionals who run their own sites who know better than to blatantly copy others' content. Copying is social suicide. This is the Internet. If someone copies others' content, people will find out, and they will find out **quickly**. The truth will be made known.

The bottom line is that people are more honest than you give them credit for. So, exactly which group are you hoping to deflect with this protection scheme?



Wow... I can see many here don't have good business skills.

First off hackers can make exact copies of your website.

This leads to making fake login pages and then connecting to a public network and using a dns redirect so when people go to your site instead they went to a hackers exact copy of your site yet the webpage url is the same as yours. So no one will notice the huge difference and would login giving the hacker access to there account once they know the login data.

on top of it. Images  and code are not easily made and cost either money or time. 

I know websites are different in nature no one makes exact copies. Yet they do go web surfing looking at code they love that makes special effects for a website or does a certain function that is impressive.

they go around and collect code and copy it paste it to there site and may the changes so it will work properly on there page. for the original owner of that code they could of spent a month or so on the code or idea of the function. Yet a person can steal it within seconds and add on to it to improve on it. 


what most saying here is why bother protect your work and rights when people will do whatever it takes to steal it.

If you think this way then don't even get into a business at all.

Look at microsoft and the game consoles they invest alot of money to anti-piracy technology to prevent people from buring games.

Yet people still do it and find ways around it. Yet  if you notice the hackers took a while to get a work around the protection that the companies had on there game consoles.

They done it to prevent piracy/ copyright infringment. 



So you ask me why am I worried about this... it's simple  why allow others to steal your work and help them out.

now some of you said that this is silly cuz the website is public and what do you expect when it goes public. 

It's just the same as any other product. Why protect the work of the GM car.... why  does KFC protect their recipes for the chicken... I mean the product is in the public realm you should expect people to steal it so let them steal it.

What your saying is just like if a robber broke into your home and plan on stealing your tv and any cash you have.

You caught the guy stealing the stuff. You can either do one call the cops  or just say well you can have it good luck to you enjoy.

2 different things.... calling the cops is a legal step saying your not allow it... the 2nd  option if you allow the person to steal it then you have no legal right over that content since it clearly shows the guy isn't stealing but taking a so called donation or legally taking goods.

So not protecting your websites codes and image or at least making a attempt to automatically shows that you are allowing the public to use your code for whatever use. 

This allows the hackers to grab your code for free. They can make fake logins to your site and could sell that code legally. 

the people who buy it and use that code would still violate a criminal law.

I do know how to make a website secure... meaning in programming terms.
I  just want to do extra to show that I don't allow my copyrights to be infringed upon.

Also to make it harder for people to just steal the work. Like some said they can just take a screen shot. 

That is true but I never seen someone take a screen shot and be able to steal images at the original quality. 

My whole point is a legal standpoint. If you don't protect your sites code then it's assumed you have not problem allowing others to stealing your code and images.

Just like your home network router.... If you don't put a password protection on that router connections. Then the law assumes you allow the public to use it.

---

### Post by CptPicard on 2010-03-21
> **hockey97 said:**
> Wow... I can see many here don't have good business skills.

Apparently, most of the rest of the world doesn't either, as I can't see this kind of "encryption" being used to prevent copying pretty much anywhere else.

> 
This leads to making fake login pages...

Then why is it that the whole industry is apparently making use of other kind of anti-phishing techniques, and not encrypting their site?

> 
on top of it. Images  and code are not easily made and cost either money or time.

You do have copyright, you know. Enforce it if someone uses your stuff and it bothers you.

When it comes to code, one really needs to understand that programmers are constantly trying to push down the effort needed to write something as basic as a webpage by trying to come up with open libraries and the like. They're not exactly concerned about someone copying a generally well known idea... that kind of an "idea commons" is typical in a craft such as programming.


> 
I know websites are different in nature no one makes exact copies. Yet they do go web surfing looking at code they love that makes special effects for a website or does a certain function that is impressive.

Yeah, and I've read a LOT of code in my lifetime to give me ideas. Nothing wrong with that. Programmers should do that.

> 
they go around and collect code and copy it paste it to there site and may the changes so it will work properly on there page.

That kind of a programmer is not worth his pay anyway; it's probable he doesn't quite understand what he is doing and the end result will be barely functional.

> 
 for the original owner of that code they could of spent a month or so on the code or idea of the function. Yet a person can steal it within seconds and add on to it to improve on it. 

Welcome to open source... there really is nothing of interest in the actual web app client side functionality implementation that would require it to be closed source. It is so trivial that people write open libraries and frameworks just to have it over with. With all due respect, it may seem like that to *you* ... but not to more experienced programmers in general.

> 
what most saying here is why bother protect your work and rights when people will do whatever it takes to steal it.

There is nothing worth protecting in the work. As a designer you just want to get it done at an hourly rate, pretty much. Everyone is happier if it's less of an issue.

> 
If you think this way then don't even get into a business at all.

So you believe spending a lot of time and effort on a useless "encryption" scheme that will destroy the usability of your site makes good business sense?

In the end, it's still under copyright. Books are out there to be read, but you can't start printing and selling your own copies.

---

### Post by wmcbrine on 2010-03-21
> **hockey97 said:**
> My whole point is a legal standpoint. If you don't protect your sites code then it's assumed you have not problem allowing others to stealing your code and images.No, it isn't. You're confusing trademark with copyright, or thinking of copyright law that hasn't been valid for many decades. And even then, "protection" is a legal concept, not a technical one -- protecting a trademark would mean suing people who misused it, and the (obsolete) copyright issue would mean affixing notice. That's all.

> *Just like your home network router.... If you don't put a password protection on that router connections. Then the law assumes you allow the public to use it.*Also wrong.

---

### Post by worseisworser on 2010-03-21
HTML and (most) JS is not interesting enough to warrant this since these things are part of the presentation layer (non-business) of your project.

If you think otherwise you are wrong. End-of-story and discussion.

---

### Post by TheBuzzSaw on 2010-03-21
hockey97, I would rip your post to shreds, but CptPicard did it for me. I *am* in business in web design. I suppose all that money I am making is imaginary. Considering how my sites are *gasp* unprotected and open for the world to see!

Your true assets are in the server-side code. Obfuscating HTML is like taking a picture of a bulletin board and then using Photoshop to hide all the tape, tacks, etc. to hide how I managed to hang all the paper and stuff onto it. People can still achieve the same layout using alternate means. It is pointless on so many levels.

Here, hockey97: [http://www.werewolfhaven.net/](http://www.werewolfhaven.net/) -- Look at the code. Copy it all you want. Go ahead. Yes, I made that site. It is my wife's art site (so she made all the graphics), but all the code is mine.

---

### Post by Hellkeepa on 2010-03-21
HELLo!

**hockey97**: Replace "website" in your post with "book", as **CptPicard** hinted towards in his closing paragraph. Then you'll see how ridiculous your post is.

Hell, as for the whole "encrypting" of a website, I have two words for you: "Firebug" and "Dragonfly".

When it comes to this whole business thing: I wonder how Facebook, Google, et al got any business at all, according to you. Or what about the original 1 million pixels site?

As **TheBuzzSaw** said: We're not paid for the end product, we're paid for our knowledge to create said product in an efficient, professional and working manner. The ones who just rips sites off of others will get two things: Bad publicity and sued.

Happy codin'!

---

### Post by soltanis on 2010-03-21
/facepalm guys

I wanted to point out that using Javascript + HTML 5, you could be a real jerk and "encrypt" your website source code (read obfuscate it really badly).

Similar to ways viruses "encrypt" (read obfuscate really badly) themselves by using small code stubs to decrypt the rest of the program, your HTML code could theoretically be a big mess that a small Javascript stub decrypts and then passes to the browser DOM for dynamic rendering.

Of course then all someone needs to do is run the very same code themselves and intercept the output. I hope you're starting to see how futile this is.

You can do the same thing with images; encrypt the content somehow, then use Javascript to decrypt and render the content using a Canvas element itself.

Again, that's a really jerk move to do and anyone really determined will simply decrypt the content themselves, write it to a file, and rearrange it to a format they can use.

Please don't be like the DRM maniacs who are trying to keep people from copying movies by making everything HDMI encrypted, using title keys, and HDCP. It doesn't work -- because there's always one step of the pipeline you can't obfuscate or encrypt, and that's the part between your eyeball and the screen.

---

### Post by slavik on 2010-03-21
hockey97, if you find a way to completely encrypt your source code so that it somehow becomes unreadable (completely random chars) but render able, you should call MPAA, they will be very interested to buy your technology.

---

### Post by soltanis on 2010-03-22
> **slavik said:**
> hockey97, if you find a way to completely encrypt your source code so that it somehow becomes unreadable (completely random chars) but render able, you should call MPAA, they will be very interested to buy your technology.

You mean steal it, patent it, then sue him for infringement.

---

### Post by slavik on 2010-03-22
well, his method will be encrypted, so nobody will be able to use it ever ...

---

### Post by linuxgurumaniac on 2010-03-22
HAHAHHAHAHAHHAHHA
This is one of the most hilarious thread I've ever read.

thx for the laughs ;) :guitar:

---

### Post by lavinog on 2010-03-22
One solution would be to create your own browser application that will work with only your site.
When a user goes to your site with a html compliant browser, redirect them to a download page that says something on the lines of:
"I am trying to keep people from stealing my code, therefore I am requireing you to use my custom browser software to view this site."
You should also make a page for search engines to crawl.

---

### Post by wmcbrine on 2010-03-22
> **lavinog said:**
> One solution would be to create your own browser application that will work with only your site.Yeah, that'll be popular.

---

### Post by Goveynetcom on 2010-03-22
> **wojox said:**
> Just Google: html obfuscate or php obfuscate
I would also say that :D .

---

### Post by Ferrat on 2010-03-23
Well in theory I guess you might be able to encrypt a website by using a "proxy" page and creating your own program to run on the server and having the encrypted site only viewable from that page which asks the program for it and the program in turn decrypts the requested site if everything checks out, if you understand what I mean, but it would take some doing.
Better yet you could have the encrypted files on another server which the program connects to and forwards after decrypting, none of the files would actually be on the server and if you create the program yourself you should be fairly safe. :)

---

### Post by TheBuzzSaw on 2010-03-23
The thing is that HTML, CSS, etc. are means to an end. HTML is not like C++ where there are fancy algorithms, states, etc. It is a presentational markup language that simple states "I want this image to hang here, and I want this to be that color". What is there to hide? Even if there was an all-powerful encryption tool, again, HTML is not a complex system. There are 1001 ways to accomplish any given layout. All it takes is eyeballs and a brain.

Then, there is still the issue of the overinflated ego in thinking that your HTML so valuable in the first place...

---

### Post by myrtle1908 on 2010-03-23
> **TheBuzzSaw said:**
> The thing is that HTML, CSS, etc. are means to an end. HTML is not like C++ where there are fancy algorithms, states, etc. It is a presentational markup language that simple states "I want this image to hang here, and I want this to be that color". What is there to hide? Even if there was an all-powerful encryption tool, again, HTML is not a complex system. There are 1001 ways to accomplish any given layout. All it takes is eyeballs and a brain.

Then, there is still the issue of the overinflated ego in thinking that your HTML so valuable in the first place...

Exactly!

---

### Post by LKjell on 2010-03-24
This reminds me on people that sends email message through attachment.

So the idea is there. Create a pdf,dvi,png..etc from your html files and linked them as links on your site. That way they cannot see your source code.

---

### Post by lavinog on 2010-03-24
> **LKjell said:**
> This reminds me on people that sends email message through attachment.

So the idea is there. Create a pdf,dvi,png..etc from your html files and linked them as links on your site. That way they cannot see your source code.

That just makes copying the site much easier though.

---

### Post by LKjell on 2010-03-24
> **lavinog said:**
> That just makes copying the site much easier though.

How? People can already do a screenshot. This guy want to hide his html codes not content. If you want to hide content then do not link anything.

---

### Post by blinktagsecurity on 2010-04-17
Just wrap your content in <blink> tags, that will do the trick.

---

### Post by nvteighen on 2010-04-17
> **blinktagsecurity said:**
> Just wrap your content in <blink> tags, that will do the trick.

!!?

---

### Post by Paqman on 2010-04-17
> **blinktagsecurity said:**
> Just wrap your content in <blink> tags, that will do the trick.

This suggestion is awesome!

---

