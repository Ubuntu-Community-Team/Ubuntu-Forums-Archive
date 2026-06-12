---
title: "Developing a website..."
date: 2009-07-19
forum: Programming Talk
---

### Post by gjoellee on 2009-07-19
Hi, I am currently working a lot on my website [http://www.kshoster.net/](http://www.kshoster.net/) and I need some other peoples opinions on how the website looks, and how it behaves.

EDIT: I have now update the website template. And you should take a look at the website again. Read post #37 to see whats new.

---

### Post by keith.newell on 2009-07-19
I think it looks pretty slick, with a nice clean interface.  :)

---

### Post by spupy on 2009-07-19
I really like the minimalistic design. Nice work! What will your website be about?

Two things that got my attention:
* On the "Reviews" and "Tutorial" pages there are links, but they don't look like such (they look like list of text). I heard a saying: "Everything that looks like something you would want to click, should be clickable. Everything that is clickable should look like it is."
* The username link in the text "Submitted by <user_name>" doesn't lead to an email or something, but I suppose this is because the website is still in alpha version?

Keep up the good work, and update us on the status. :popcorn:

---

### Post by hessiess on 2009-07-19
The main page content is added with JavaScript, so will be *completely* invisible to search engines.
The noscript tag should contain a plain text representation of the content added by the scripting, *NOT* a `please enable javascript' message. Which is both completely useless to search engines, and makes the site unusable for disabled users using text-to-speech, Braille displays and other asistive technologies.

for example, look at all the pages returned by google with a simple `please enable javascript' query: [http://www.google.co.uk/search?q=please+enable+javascript&hl=en&safe=off&client=firefox-a&rls=org.mozilla:en-US:official&hs=Ytx&start=10&sa=N](http://www.google.co.uk/search?q=please+enable+javascript&hl=en&safe=off&client=firefox-a&rls=org.mozilla:en-US:official&hs=Ytx&start=10&sa=N)

Also you should have your CSS in an external style sheet, and link it into your pages.

Another problem is the layout breaks if you zoom the text, this is another big usability problem for partly sighted people who need a larger font size. also on the topic of fonts, there is too little contrast between the light blue text and white background.

---

### Post by gjoellee on 2009-07-20
> **spupy said:**
> I really like the minimalistic design. Nice work! What will your website be about?

Two things that got my attention:
* On the "Reviews" and "Tutorial" pages there are links, but they don't look like such (they look like list of text). I heard a saying: "Everything that looks like something you would want to click, should be clickable. Everything that is clickable should look like it is."

* The username link in the text "Submitted by <user_name>" doesn't lead to an email or something, but I suppose this is because the website is still in alpha version?

Keep up the good work, and update us on the status. :popcorn:

0. My website is about Linux. You can read about Linux distributions, read tutorials if you need help, get the latest Linux news, read reviews and download some scripts etc... which may help you a lot.

1. I have been aware of that. I am working on something that will look cool, but maybe I should come up with a temporary fix?

2. You will see some mail links with the next build :P


> **hessiess said:**
> The main page content is added with JavaScript, so will be *completely* invisible to search engines.
The noscript tag should contain a plain text representation of the content added by the scripting, *NOT* a `please enable javascript' message. Which is both completely useless to search engines, and makes the site unusable for disabled users using text-to-speech, Braille displays and other asistive technologies.

Also you should have your CSS in an external style sheet, and link it into your pages.

Another problem is the layout breaks if you zoom the text, this is another big usability problem for partly sighted people who need a larger font size. also on the topic of fonts, there is too little contrast between the light blue text and white background.


Ok, I will have to work on the noscript there :P

This is the one on the index page right? That should be a quick fix.

I which web browser does the layout break? It works fine for me in both Firefox 3.5 and Internet Explorer 8.

When it comes to the font colors, I don't think there is to little contrast. I am however planning to make the sidebar content black. How does that sound?

---

### Post by Nevon on 2009-07-20
Other people have already mentioned some of the things I was going to say. However, I have one thing that really bugs me, that hasn't been mentioned yet. That logo needs to be replaced. First of all it's way to cluttered with three characters and text in front. Secondly, that text is terrible. I know that Gimp is really, really bad with text, so it's not all that easy to make something attractive - but it needs to be reworked. 

Other than that, it looks pretty good. I like the overall color scheme. However, you might want to change the link color for regular sized text. That blue on white is kind of hard to read. It looks good on the headers, because they're bigger. But in regular text it's a little hard on the eyes.

---

### Post by gjoellee on 2009-07-20
I have uploaded some new changes. The changelog is in our forum: [http://kshoster.net/forum/viewtopic.php?f=11&t=11&p=13#p13](http://kshoster.net/forum/viewtopic.php?f=11&t=11&p=13#p13)

---

### Post by hessiess on 2009-07-20
> 
I which web browser does the layout break? It works fine for me in both Firefox 3.5 and Internet Explorer 8.

Firefox 3.5, open View -> zoom -> enable `zoom text only'. then press ctrl and the `+' key a few times, the navigation text breaks out of the navigation bar and wraps onto another line, as the text is white, and the background of the section it wraps onto is also white, it becomes invisible. You could partly fix this by specifying the height of the navi background using EM.

> 
When it comes to the font colors, I don't think there is to little contrast. I am however planning to make the sidebar content black. How does that sound?

Black would be good, though personally I would just stick with the blue and make it a little darker. I do calibrate my monitors, which can make a large difference to the apparent contrast of displayed colours. If you do anything with graphics, espetily on the web you rilley should calibrate your monitor.

On a side note, the first thing I thought of when I read `KsHoster', is `web hosting provider', if the site is about Linux you may want to change the name.

---

### Post by Jakob Von Gunten on 2009-07-20
The light blue text on white produces the bad contrast, and difficult on the eyes.

Same for the main logo, the faded and washed out white text is just bright.

It has been mentioned but the websites URL "kshoster.net" is difficult to remember since it doesn't have anything memorable about it, or any link to the content of the site.

I'm sure there is a better name you can register than what you are using now, nobody will remember it.

I like the simple horizontal menu at the top, and the pages has a good overall design.

---

### Post by gjoellee on 2009-07-20
> **Jakob Von Gunten said:**
> 
 It has been mentioned but the websites URL "kshoster.net" is difficult to remember since it doesn't have anything memorable about it, or any link to the content of the site.


I started using a piczo website a few years ago, but a friend at school gave be this domain as he did not use it. I will rather stick with a weird URL then using piczo. Also I am to young to have a card I can use on the internet so the causes some issues when it comes to changing the domain name. I do have the money to get a new domain, but I am not sure if I can convince anyone to buy it for me, even if I could pay them back...
  
I have been thinking about: [www.lintut.com]("http://www.lintut.com") I find it quite easy to remember.

---

### Post by gjoellee on 2009-07-20
Forgot to upload the new CSS file. Now you can see the new changes :P

---

### Post by Reiger on 2009-07-20
You may want to look at this: [[IMG]http://img136.imageshack.us/img136/7583/snapshot1a.th.png[/IMG]](http://img136.imageshack.us/i/snapshot1a.png/)

---

### Post by gjoellee on 2009-07-20
> **Reiger said:**
> You may want to look at this: [[IMG]http://img136.imageshack.us/img136/7583/snapshot1a.th.png[/IMG]]("http://img136.imageshack.us/i/snapshot1a.png/")

OK, I can confirm this in Opera 9.64, Firefox 3.5 and Internet Explorer 8. Currently working on it to see if there is a way I can solve it. Does anyone have a theory on how to fix it?

---

### Post by gjoellee on 2009-07-20
The noscript had been modifed now!

---

### Post by gjoellee on 2009-07-20
(I Know I should not triple post)
 
I will start posting the changelog into the forum, as it already is written with BBCode.

**General**
-Added Lightbox v2
-Critical bug fix: JavaScript for the Lightbox did conflict with the jQuery JavaScripts causing the jQuery applications to only display as HTML.

**User Interface**
-No images has borders anymore

**Forum**
-No changes here for this build

---

### Post by KingNeil on 2009-07-20
The first thing I notice is that the news scrolls way too fast on the home page. There is also no way of moving between stories yourself on the home page. There needs to be left and right arrows that let you scroll through. Those are just two things I picked up by looking at your site for 2 seconds.

---

### Post by gjoellee on 2009-07-21
> **KingNeil said:**
> The first thing I notice is that the news scrolls way too fast on the home page. There is also no way of moving between stories yourself on the home page. There needs to be left and right arrows that let you scroll through. Those are just two things I picked up by looking at your site for 2 seconds.

I think arrows may be to difficult for be to add, but I will at least try to add arrows. I have now also change the scroll time from 6 sec to 8 sec.

---

### Post by gjoellee on 2009-07-21
I have added a new slideshow on the front page with arrows! Check it out!

NOTE: I have not yet added all the content some the are a lot off **** there at the moment.

---

### Post by Mirge on 2009-07-21
As someone already pointed out, dynamically loading your content with JS is going to make it so that search engines can't see your content.

---

### Post by ebharv on 2009-07-21
I think your site looks awesome. However, when clicking one of the top links a  new tab opened in FF (3.0.11) after initially visiting your site. For example when I clicked the link [http://www.kshoster.net/](http://www.kshoster.net/) and clicked News a new tab opened, but clicking Tutorials in the new tab (or Home) does not open a new tab (or window if you don't have windows set to open in tabs in FF). Clicking Forums always opens a new tab (and I believe this is your intent). It may have something to do with how you process the query string. 

Just thought I'd let you know.

Quick question: What's your forum (i.e. simplemachines, phpbb, self made)?

---

### Post by gjoellee on 2009-07-22
> **Mirge said:**
> As someone already pointed out, dynamically loading your content with JS is going to make it so that search engines can't see your content.

This application works great without JavaScript as well. Won't search engines even pick that up?

> **ebharv said:**
> I think your site looks awesome. However, when clicking one of the top links a  new tab opened in FF (3.0.11) after initially visiting your site. For example when I clicked the link [http://www.kshoster.net/](http://www.kshoster.net/) and clicked News a new tab opened, but clicking Tutorials in the new tab (or Home) does not open a new tab (or window if you don't have windows set to open in tabs in FF). Clicking Forums always opens a new tab (and I believe this is your intent). It may have something to do with how you process the query string. 

Just thought I'd let you know.

Quick question: What's your forum (i.e. simplemachines, phpbb, self made)?

The news link does not open a new tab or window anymore. (Thanks, I actually did not notice!) And yes, the Forum page is supposed to open in a new tab or page.

I am using PHPBB3 and I am very happy with it. Just remember! If you add PHPBB to your website, you might get a lot of spam in your forums even with a CAPTCHA. See how to prevent this from happening in this post: [http://www.phpbb.com/community/viewtopic.php?t=427852](http://www.phpbb.com/community/viewtopic.php?t=427852)

---

### Post by v8YKxgHe on 2009-07-22
You're taking user input and directly inserting that to include a PHP file - very bad. Why? Example: [http://www.kshoster.net/?q=../index ]("http://www.kshoster.net/?q=../index")

Recursion ftw. You're script is open to NULL byte injection because of this, and so if your webserver was not setup, or PHP even (not sure what is escaping it, I do hope you don't have magic_quotes_gpc enabled!) to escape the null byte, I would be able to see your '/etc/passwd' file.

As it stands, I can make your site include any PHP file that the webserver has access to. May we see the code? I can rip it apart and get it secure.

Also, why are you using XHTML, but sending it as HTML? ;) Only use XHTML if you know what you're doing and that you know you need it.

---

### Post by gjoellee on 2009-07-22
> **AlexC_ said:**
> You're taking user input and directly inserting that to include a PHP file - very bad. Why? Example: [http://www.kshoster.net/?q=../index ]("http://www.kshoster.net/?q=../index")

Recursion ftw. You're script is open to NULL byte injection because of this, and so if your webserver was not setup, or PHP even (not sure what is escaping it, I do hope you don't have magic_quotes_gpc enabled!) to escape the null byte, I would be able to see your '/etc/passwd' file.

As it stands, I can make your site include any PHP file that the webserver has access to. May we see the code? I can rip it apart and get it secure.

Also, why are you using XHTML, but sending it as HTML? ;) Only use XHTML if you know what you're doing and that you know you need it.

I am not the code exper, there is another guy that does that. He is on vacation. I have to admit that I don't understand so much of what you've posted there.

When it comes to the webserver, it is one.com which owns that.

What code...the index.php? It is added as an attachment. NOTE: I cannot upload php files to ubuntuforums so it is in .txt format.

---

### Post by v8YKxgHe on 2009-07-23
Ok well you can always pass on my comments to him. The PHP code he uses is:

```
<?php
$q = $_GET['q'];
if(!isset($q)) {
	$q = "main";
}

include("inc/$q.php");
?>
```

There is 3 things wrong with it. Firstly not checking if the 'q' index of $_GET exists, which will lead to undefined index PHP notice if it does not exist.

Secondly, the variable '$q' will always be set, since he has just assigned it the line above (and so the entire 'if' statement is pointless).

Thirdly is the issue I pointed out, taking using input and putting it directly into PHP to include a file.

You'll want something more like either of these for a small site:

```

<?php
	// A:
	if ( empty($_GET['q']) || !in_array($_GET['q'], array('home', 'article', 'about')) ) {
		$page = 'default';
	} else {
		$page = trim($_GET['q']);
	}
	require 'inc/'.$page.'.php';

	// B:
	$page = empty($_GET['q']) ? null : trim($_GET['q']);
	switch( $page ) {
		case 'home':
		case 'article':
		case 'about':
			$file = $page.'.php';
			break;
		default:
			$file = 'default.php';
	}
	require 'inc/'.$file;
?>
```

There are loads of little ways of doing it, and I'm too tired to give more better examples.

---

### Post by gjoellee on 2009-07-23
Thanks...I am adding this new code for the next build :D

---

### Post by gjoellee on 2009-07-23
Index file updated. [http://www.kshoster.net/?q=../index](http://www.kshoster.net/?q=../index) looks normal!

---

### Post by Reiger on 2009-07-23
From a cursory overview: 

It is fairly sloppy code actually. 21 errors according to the W3C validator and most of them are just silly whoops-I-forgot-to-escape-my-ampersands/ whoops-I-forgot-to-close-my-tag errors.

There are a fair few more serious errors in the sense that they are wrong on a "structure level" of your document: using <p> elements where they are not allowed. (I'm guessing using <p> elements inside <p> elements.) And of course the rush for target="_blank" in hyperlinks.

---

### Post by gjoellee on 2009-07-23
> **Reiger said:**
> From a cursory overview: 

It is fairly sloppy code actually. 21 errors according to the W3C validator and most of them are just silly whoops-I-forgot-to-escape-my-ampersands/ whoops-I-forgot-to-close-my-tag errors.

There are a fair few more serious errors in the sense that they are wrong on a "structure level" of your document: using <p> elements where they are not allowed. (I'm guessing using <p> elements inside <p> elements.) And of course the rush for target="_blank" in hyperlinks.

Thanks, I will take a look at the results and fix them.

I have also just announced some forum updates that you will see in the future.
> -Enhanced BBCode
-Change rank names
-Change user group names
-Improve the personal messaging
-Make new topic icons
-and more!


**A few more changes has been done**:
-Lighter slideshow background on the front page
-New page UI has been changed: "Posted by" section has been moved form the bottom of the article to under the header, and the comments link has been removed as you're now able to post comments.
-Version added to the footer

---

### Post by gjoellee on 2009-07-23
> **Nevon said:**
> However, you might want to change the link color for regular sized text. That blue on white is kind of hard to read. It looks good on the headers, because they're bigger. But in regular text it's a little hard on the eyes.

> **Jakob Von Gunten said:**
> The light blue text on white produces the bad contrast, and difficult on the eyes.


You have been heard!

Link color changed to: #696969 (dark gray)
Header and non-hovered link color changed to: #2f91ff (darker blue the the previous, easier on the eyes)

---

### Post by gjoellee on 2009-07-25
FINALLY! I have bade the basic UI for the About page! Link here: [http://kshoster.net/?q=about](http://kshoster.net/?q=about)

What do you think? Please test everything to the limit!

---

### Post by gjoellee on 2009-07-25
[http://www.kshoster.net/](http://www.kshoster.net/) is now W3Schools xhtml 1.0 strict! :D

---

### Post by v8YKxgHe on 2009-07-26
> **gjoellee said:**
> [http://www.kshoster.net/](http://www.kshoster.net/) is now W3Schools xhtml 1.0 strict! :D

It's W3C. W3Schools is an unrelated website with tutorials/references towards HTML/CSS/JavaScript etc.

And you still want to be using HTML not XHTML ;)

---

### Post by blpanther on 2009-07-26
I think this type of menu where the stuff moves when you hoover over it is a bit outdated, like early flash fascination, apart from that I quite like it

---

### Post by gjoellee on 2009-07-26
> **AlexC_ said:**
> It's W3C. W3Schools is an unrelated website with tutorials/references towards HTML/CSS/JavaScript etc.


Whoooops! I knew that 8-[

> **blpanther said:**
> I think this type of menu where the stuff moves when you hoover over it is a bit outdated, like early flash fascination, apart from that I quite like it


Good to hear that you like it! However I am not yet finished with that menu's design. When you are not hovering it, it looks quite boring.



**While I am making a post maybe I should tell you a little about hat my next plans are....**

1. I am currently working on a new UI for the Downloads page.

2. I might change the UI on the Reviews page and the Tutorials page as the jQuery plugins cause conflicts with all the other javascript applications. The new UI for those pages will probably be the same UI as I use on the About page. Remember that I am not sure about this yet.

3. I am working on a new KsHoster logo!

4. The forum will receive a new style, and quite a few enhancements.

5. All the UI work has to be finished.

And when all that is done and working the website moves from Alpha to Beta, which means that there will be a UI freeze.

---

### Post by gjoellee on 2009-07-26
New upload containing some interesting new enhancements:

-**The same link effects as on the About page has been added to the Reviews page and to the Tutorials page. (NOTE: The link table has not yet been themed for the KsHoster website.)**

-jQuery UI conflicts fixed

-Lightbox fix has been added to one page. Lightbox will be added to all the pages that requires it in the next build.

---

### Post by gjoellee on 2009-07-29
I have started working on the forums now. I have already changed the forum template. Check it out: [http://kshoster.net/forum/](http://kshoster.net/forum/)

I am not finished with the template or it's contents, but this is the start. :P

More forums will also be added, subforums will be added. The whole forum will be more complete.

---

### Post by gjoellee on 2009-07-30
I have done a huge update and here is the changelog:¨

-New template
-New logo
-Link theme for the About page, Tutorials page and Reviews page is updated
-The forum shares template with the rest of the website
-New logo
-New favicon
-Zooming bugs are fixed

Hope you like it! It is also easier on the eyes :D

---

### Post by UbuKunubi on 2009-07-30
Hello,

Seeing as your further up the road than me on this, I would appreciate any suggestions you could make about my project, which can be found at [http://91.108.75.118/](http://91.108.75.118/)

I have yet to register the domain name, but that is only a matter of time.
I would like to spend all day, every day on this, but like everyone else I have to work and put bread on the table, so my progress is only an hour a day (little and often making for regular progress!)

Thanks,
Ubu

---

### Post by gjoellee on 2009-07-30
> **UbuKunubi said:**
> Hello,

Seeing as your further up the road than me on this, I would appreciate any suggestions you could make about my project, which can be found at [http://91.108.75.118/](http://91.108.75.118/)

I have yet to register the domain name, but that is only a matter of time.
I would like to spend all day, every day on this, but like everyone else I have to work and put bread on the table, so my progress is only an hour a day (little and often making for regular progress!)

Thanks,
Ubu

I look at this as a thread hijack. Please create your own thread about this. If you want to speak with me please contact me by mail or personal messaging.

---

### Post by Mirge on 2009-07-30
> **UbuKunubi said:**
> Hello,

Seeing as your further up the road than me on this, I would appreciate any suggestions you could make about my project, which can be found at [http://91.108.75.118/](http://91.108.75.118/)

I have yet to register the domain name, but that is only a matter of time.
I would like to spend all day, every day on this, but like everyone else I have to work and put bread on the table, so my progress is only an hour a day (little and often making for regular progress!)

Thanks,
Ubu

Instead of relying on HTML markup to resize your images, you should actually resize your images... will be a much smaller filesize that way (content loads faster + less bandwidth usage).

And it might just be me, but I _really_ don't care for frames.

---

### Post by hessiess on 2009-07-30
> **UbuKunubi said:**
> Hello,

Seeing as your further up the road than me on this, I would appreciate any suggestions you could make about my project, which can be found at [http://91.108.75.118/](http://91.108.75.118/)

I have yet to register the domain name, but that is only a matter of time.
I would like to spend all day, every day on this, but like everyone else I have to work and put bread on the table, so my progress is only an hour a day (little and often making for regular progress!)

Thanks,
Ubu

Get rid of the frames. and start your own thread.

---

### Post by JordyD on 2009-07-30
Yes, frames are no-nos. :D And I'm not even a web developer.

---

### Post by Mirge on 2009-07-30
> **gjoellee said:**
> I look at this as a thread hijack. Please create your own thread about this. If you want to speak with me please contact me by mail or personal messaging.

Whoops I didn't notice that post (I clicked the "Goto first unread post" image) when I replied. Probably a good idea to start your own thread, I agree.

---

### Post by gjoellee on 2009-08-01
**Update:**

-I have added more forums, and sorted it in categories. I have also added forum rules.

-I have added some nice code,tip and warning designs on the website. (Not really sure how to describe it). You just better se yourself. Here is a page with a CODE and TIP design thing: [http://kshoster.net/?q=tutorials/arch/themegnomeroot](http://kshoster.net/?q=tutorials/arch/themegnomeroot)

NOTE: I have no pages with a warning design thing yet.

-Lightbox is fixed

-All the tutorials pages has been modified a little. Some small typo fixes and a few advertisement removals.

---

### Post by JordyD on 2009-08-01
> **gjoellee said:**
> [http://kshoster.net/?q=tutorials/arch/themegnomeroot](http://kshoster.net/?q=tutorials/arch/themegnomeroot)

In this tutorial, it says, "If you change themes, fonts or icons you must repeat the commands above". But the above commands are making symbolic links, so the commands do not have to be repeated.

---

### Post by gjoellee on 2009-08-02
> **JordyD said:**
> In this tutorial, it says, "If you change themes, fonts or icons you must repeat the commands above". But the above commands are making symbolic links, so the commands do not have to be repeated.

Whoops, I've never really thought about that. Thanks :D


Oh, by the way: I will just change the UI on the front page a little, and create a UI for the Downloads page. The only things that remains then is just a few small tweaks, and KsHoster 1.0 is done! (Of course I will add missing content)

---

### Post by gjoellee on 2009-08-02
I have updated the design of the slider on the front page:

-The header is red
-It is wider
-Darker and wider backgroud
-New arrows

With that, I am also announcing the KsHoster 1.0 Beta (moved from Alpha). Now I am a giant leap closer to KsHoster 1.0!

---

### Post by credobyte on 2009-08-02
Section :: Tutorials

[LIST]
[*]on mouse over ( link ), gray tab at the end shifts to the right, however, left side is still at the same coordinates .. looks weird :roll:
[/LIST]

Overall, everything runs a bit too smoothly for me ( just an opinion ).

---

### Post by gjoellee on 2009-08-02
> **credobyte said:**
> Section :: Tutorials

[LIST]
[*]on mouse over ( link ), gray tab at the end shifts to the right, however, left side is still at the same coordinates .. looks weird :roll:
[/LIST]

Overall, everything runs a bit too smoothly for me ( just an opinion ).

Is is supposed to be like that, even though it might be weird.

Yikes, how can things be running a little to smooth?! :o

---

### Post by credobyte on 2009-08-02
> **gjoellee said:**
> Is is supposed to be like that, even though it might be weird.

Yikes, how can things be running a little to smooth?! :o

I can't explain, what exactly runs too "smoothly" - it's just the way it is :) This is why I never ask for feedback on my own sites - I know that there are hundreds of people who will dislike it and in the same time, thousands of fans visiting it again and again.

---

### Post by Mirge on 2009-08-02
[http://www.kshoster.net/?q=tutorials](http://www.kshoster.net/?q=tutorials)

I don't like how the links wobble in there... and then once it's loaded, they wobble or whatever on mouseover.

Just seems like there's too much work put into the appearance, showing off "cool" effects... and not enough work into actual content. Yes, you CAN put too much pizazz into a site, making the site less tolerable to people who just want to get content they're after quickly... and you could end up annoying users more than actually helping them.

---

### Post by gjoellee on 2009-08-03
> **Mirge said:**
> [http://www.kshoster.net/?q=tutorials](http://www.kshoster.net/?q=tutorials)

I don't like how the links wobble in there... and then once it's loaded, they wobble or whatever on mouseover.

Just seems like there's too much work put into the appearance, showing off "cool" effects... and not enough work into actual content. Yes, you CAN put too much pizazz into a site, making the site less tolerable to people who just want to get content they're after quickly... and you could end up annoying users more than actually helping them.

I have been thinking about those links, but those where the best I could find at the moment. I will search for new solutions for a later version as those links won't be practical when more links will be added.

But at the moment the best way to use the website without the effects is to don't have JavaScript enabled.

---

### Post by Mirge on 2009-08-03
Don't get me wrong, I like Javascript. I like effects. I just think that Javascript should be used to enhance/simplify the user's experience, not hinder it or annoy.

Will wait & see what you come up with next.

---

### Post by gjoellee on 2009-08-03
OK, I have managed to stop the little animation first so you only get the animation on hover. This also causes the page to load a little faster. :P

Also to make it more practical I may make the categories collapse able (or if you write in in one word, I don't know).

---

### Post by gjoellee on 2009-08-03
Important Update!

I have made the "expanding" link categories expand able. If you collapse one category, your browser will remember it for later. The same if you open one. If yo collapse one with JavaScript enabled, then refresh the page without JavaScript enabled all the categories should be open.

(hope you understand it :D I am quite terrible at explaining things)

---

### Post by credobyte on 2009-08-03
[http://www.kshoster.net/?q=downloads]("http://www.kshoster.net/?q=downloads:")
> Sorry...
There was an error loading this page. Please stay tuned for a fix.Errors should be eliminated ;)

---

### Post by gjoellee on 2009-08-03
> **credobyte said:**
> [http://www.kshoster.net/?q=downloads]("http://www.kshoster.net/?q=downloads:")
Errors should be eliminated ;)

Working on it ;)

---

### Post by ArmenianLeader4 on 2009-08-03
Looks like a good site, but I think that you could tweak some minor design elements so that they look better. Also, the text may be a little on the small-ish size, and the color of it seems to make it blend with its background. 

Oh, and by saying that there are a few design elements, for example, you can change those arrows a bit by adding drop shadow or something, it could look better with that grunge-y background you've got going. Also, for the behavior of the scroller window itself, you can use javascript to make a small image on the bottom change, depending on what page you're on. Like, maybe dots or something, and then one lights up corresponding to the page you are viewing. You can make that happen using CSS right on your main HTML code like this:

> } 
#tic { 
  border: .05em #000000 solid; 
  font-size:0.85em; 
  padding:10px; 
  inset;background-color:white; 
  width:400px; 
  line-height:20px; 
} 
#tic * { 
  font-size: 1em; 
  margin:0px; 
  color:#000000; 
  padding:0px; 
  display:none; 
} 
#tic a { 
  display:inline; 
  color:#000000; 
} 
#drawing { 
    position:absolute; 
    width:206px; 
    height:191px; 
    z-index:1; 
    visibility: hidden; 
} 
#figure { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:2; 
    visibility: hidden; 
} 
#interior { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:3; 
    visibility: hidden; 
} 
#landscape { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:4; 
    visibility: hidden; 
} 
#stilllife { 
    position:absolute; 
    width:206; 
    height:191; 
    z-index:5; 
    visibility: hidden; 
}And then, you could implement Java into that code and add something like this:

> <script type="text/JavaScript"> 
<!-- 
function MM_findObj(n, d) { //v4.01 
  var p,i,x;  if(!d) d=document; if((p=n.indexOf("?"))>0&&parent.frames.length) { 
    d=parent.frames[n.substring(p+1)].document; n=n.substring(0,p);} 
  if(!(x=d[n])&&d.all) x=d.all[n]; for (i=0;!x&&i<d.forms.length;i++) x=d.forms[i][n]; 
  for(i=0;!x&&d.layers&&i<d.layers.length;i++) x=MM_findObj(n,d.layers[i].document); 
  if(!x && d.getElementById) x=d.getElementById(n); return x; 
} 
 
function MM_showHideLayers() { //v6.0 
  var i,p,v,obj,args=MM_showHideLayers.arguments; 
  for (i=0; i<(args.length-2); i+=3) if ((obj=MM_findObj(args[i]))!=null) { v=args[i+2]; 
    if (obj.style) { obj=obj.style; v=(v=='show')?'visible':(v=='hide')?'hidden':v; } 
    obj.visibility=v; } 
} 
//--> 
</script>And then, for an image you want to change, just tag it, like so:

> 
<div id="figure"><img src="imagename.jpg" width="206" height="200" /></div>I don't know. Your site looks really good, but you can do whatever you want, its your site.

Oh, and not to sound too picky, but you have a grammatical error on your first page: > This means that some parts of the website is not yet finished, and is under development.  It should be "some parts of the website are not yet finished" not "is." :D

---

### Post by gjoellee on 2009-08-04
I will take a look at it, ArmanianLeader4.:D

**Some changes has been done:**

-The code/tips boxes on in the tutorials pages are in gradient color, and not only in one color anymore.

-The previously gray ugly boxes at the top and bottom on the page, are not white, and not visible anymore. (making the website look a lot cleaner)

**-The Download page has been fixed and received a new _partially_ finished UI.**

-New link color; "hover" and "active" color: #ff9a9a, "link" and "visited" color: #dedede

---

### Post by gjoellee on 2009-08-04
**Another update on the front page:**

-The background is now darker and gradient, so it is easier to read all the text there. A computer screen has been added behind the added images to it looks like the images are shown in a computer screen. :P

-The navigation arrows on the front page does now have shadows :D

---

### Post by gjoellee on 2009-08-07
I have started doing some work at the download page. Direct link: [http://kshoster.net/?q=downloads](http://kshoster.net/?q=downloads)

I will not notify you of changes being done on the test page, but I will notify you when the download page is finished.

Just some small things I have done:

-Added a little red line on the background for the sliding application on the bottom of the page
-Added some separators between the the top links on the sliding application on the bottom of the page 

NOTE: The download page is nothing near finished and huge changes will be uploaded soon!

---

### Post by gjoellee on 2009-08-08
Download page has been removed because it turns out the I don't have enough time to maintain all the downloads that I had planned to add. Some downloads may be added to tutorials pages etc...

NOTE: You can follow the website development in our forums: [http://kshoster.net/forum/viewforum.php?f=16](http://kshoster.net/forum/viewforum.php?f=16)

I have now also made a date for **KsHoster 1.0** to be finished and uploaded. It is **September 1st** (if there are no further problems).

---

### Post by gjoellee on 2009-08-14
I just wanted to say thank you far all you that have helped making KsHoster a more usable website. If you want to contribute more with the website's further development, you may find more information in the KsHoster forums when that time comes.

Thank you, your'e all great :P

---

