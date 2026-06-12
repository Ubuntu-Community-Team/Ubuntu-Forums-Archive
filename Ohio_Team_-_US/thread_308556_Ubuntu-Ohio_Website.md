---
title: "Ubuntu-Ohio Website"
date: 2006-11-28
forum: Ohio Team - US
---

### Post by Vorian on 2006-11-28
One of the projects we'll have going real soon is the official website for the Ohio Team.  

Here is the purpose of this thread:
1. Gather ideas for "must haves" on the site.
2. Establish a team Web-Master, and admin(s) -->must have registered pgp keys on launchpad.

Thoughts?

---

### Post by _lynX on 2006-11-28
[quote=Vorian]1. Gather ideas for "must haves" on the site.[/quote]

I think the basic 'must haves' we need for a site would be: 
* an open calendar
* a list to track scheduled events and plan new events
* photo/information gallery, for posting of pictures and information about various displays or booths set up
* a way to post team news
* a list of goals and other team-specific information
* while not NECESSARY, I think a team planet would be nice. The New Jersey team has one ([http://ubuntu.joeterranova.net/planet/)](http://ubuntu.joeterranova.net/planet/)), and it's a nice way for the team to keep track of each other.

Any help you need with the site I'd be more than happy to give. I have more freetime than I know what to do with sometimes. :D

---

### Post by steven8 on 2006-11-28
I like the team planet very much.  I will be happy to contribute articles and such about ubuntu/linux in general.  I am registered at Launchpad, does that mean I have a pgp key?

---

### Post by _lynX on 2006-11-28
> **steven8 said:**
> I like the team planet very much.  I will be happy to contribute articles and such about ubuntu/linux in general.  I am registered at Launchpad, does that mean I have a pgp key?

Once you've registered, go to your People page (profile). On the right side of the screen, there should be something about "Ubuntero:  No" with a link. Follow the link and it will explain how to get a key, along with how to use that key to sign the Ubuntu Code of Conduct. :)

---

### Post by jpeddicord on 2006-11-28
Would WordPress be a solution? You can extend WP to do about anything, including calendar, meeting management, and such. The Planet idea is nice, although we'll need an aggregator to merge all of the blog feeds.

I have a lot of web design HTML/CSS/PHP/SQL/AJAX/JavaScript experience. I can help out with whatever design/administering is needed (yes I am an Ubuntero). Have a look at my signature to see some of my sites. [http://codechunk.net](http://codechunk.net) is a portal that lists the sites also, although it is under construction.

I have an aggregator script (in PHP) partially written already, but for a different purpose. You can see it at [http://youmakemedia.com/](http://youmakemedia.com/) on the left; titled Oratos Media. It retrieves all of the posts from the network using RSS, and then calculates the latest post and links ot it.

Jacob

---

### Post by meatballhat on 2006-11-29
/*insert two cents*/
While we're discussing website stuff, I wanted to add that I'm currently working on the SpreadUbuntu project with Jenda.  Most of my experience so far with web design / construction has been with PHP, but for SpreadUbuntu we're specifically choosing something Python-based for the sake of consistency with Ubuntu's DNA.  There are a couple of *huge* CMS solutions written in Python such as Plone and other Zope derivatives.  For SpreadUbuntu, we're using Skeletonz --> [http://orangoo.com/skeletonz/](http://orangoo.com/skeletonz/)  It's a *very fast* CMS based primarily on Cheetah --> [http://www.cheetahtemplate.org](http://www.cheetahtemplate.org)

My thinking goeth like: If I force myself to use Python for all manner of stuff, I'll be of more use to Ubuntu as a whole.
/*end two cents*/

---

### Post by Vorian on 2006-11-29
Canonical - hosting will provide
[LIST]
[*] FTP Access 
[*] PHP 4 
[*] CGI Support (python included) 
[*] MySQL database 
[*] E-mail list 
[*] 500 MB of disk space
[*] An ubuntu related domain ( like ohio.ubuntu-us.com )[/LIST]

---

### Post by Vorian on 2006-11-29
> **steven8 said:**
> I will be happy to contribute articles and such about ubuntu/linux in general.  

That will be wonderful!  Thanks:D

---

### Post by skippy13 on 2006-11-29
If Ubuntu provides Python support, I'd recommend Planet Planet for the aggregator.  I just set it up for my family, and it's super easy to use.  It does require a cron job to update, though.

Another option is Drupal.  I believe it has a planet-like aggregation module.

---

### Post by jpeddicord on 2006-11-29
Drupal is a great CMS. I only wish it was PHP5 instead of PHP4 on the servers. Oh well. :rolleyes:

I'll re-state what I said on IRC: We could technically run our own version of PHP5 using CGI. It would take up a chunk of disk space, but I think it would be worth it. magic_quotes must die.

---

### Post by _lynX on 2006-11-29
> **jacobmp92 said:**
> Drupal is a great CMS. I only wish it was PHP5 instead of PHP4 on the servers. Oh well. :rolleyes:

I'll re-state what I said on IRC: We could technically run our own version of PHP5 using CGI. It would take up a chunk of disk space, but I think it would be worth it. magic_quotes must die.

I pay a buttload for a Site5 ([http://www.site5.com/hosting/](http://www.site5.com/hosting/) - Currently on the Gold plan, but I can easily upgrade to something more suitable if need be) host and hardly use it. It's available if the group (or anyone, for that matter) wants it. ^_^

---

### Post by PWill on 2006-12-04
I suggest [Joomla!]("http://www.joomla.org/"), an open-source CMS. I'd be glad to help with the development/design of this site, as well as being one of the admins. I do web design for local businesses in Columbus, so I could do the design for the site.

Here is an example of a Joomla! site that I designed for my school: [CAHS]("http://www.cahs.info/")

Joomla! also has a GUI admin panel, and supports hundreds of extension, such as calendars, blogs, etc.

Also, I have a PGP key, and am an Ubuntuero on [Launchpad]("https://launchpad.net/people/paulwilliams")

I just found the team today, and I joined the mailing list as well as the LP team. I'll be at the IRC meeting on Wednesday.

---

### Post by jpeddicord on 2006-12-04
I'm sorry, but the first word that came to mind when you said Joomla was bloat. :-k 

Then again, there isn't really a CMS that isn't bloated. I always just use WordPress and expand it with themes/plugins. Joomla's menu system alone made me want to stop using it. I tried Drupal also, and while a bit "cleaner," some features seemed a bit unnecessary.

Eh, that's just my opinion.

---

### Post by coder_ on 2006-12-06
Go for Wordpress I'd say.


...Or if we could have Rails support...   *hint* *hint*  Although I doubt it... :P

---

### Post by jpeddicord on 2006-12-06
Canonical's hosting doesn't have Rails, although the host I'm on (DreamHost) does.

I'm starting to wonder if the website request will ever get approved. I don't really care either way, it's just as easy to self host as it is with Canonical. I have 199 GB of space left to spare anyway. :p

---

### Post by PWill on 2006-12-06
Still puching for Joomla here...

Here are the minimum requirements for Joomla 1.0

    * PHP 4.2.x or above - [http://www.php.net](http://www.php.net)
    * MySQL 3.23.x or above - [http://www.mysql.com](http://www.mysql.com)
    * Apache 1.13.19 or above - [http://www.apache.org](http://www.apache.org)

Canonical provides all of these.

---

### Post by Vorian on 2006-12-06
This pole is for the Ohio LoCo team Website Domain Names.

Vote for the one you love the most:mrgreen:

---

### Post by PWill on 2006-12-06
Votd for ubuntuohio.org.
Although the hyphen makes it fit in better, it is harder for some people to remember.

---

### Post by steven8 on 2006-12-06
I voted for the non-hyphenated too.  :-)

---

### Post by jpeddicord on 2006-12-07
I voted for the one with the hypen, but I am fine with either. ;)

---

### Post by Vorian on 2006-12-07
*Update*

Canonical has approved our request (prior to the meeting)

[http://ohio.ubuntu-us.org](http://ohio.ubuntu-us.org)

---

### Post by Vorian on 2006-12-07
The topic of this thread is to discuss the hosting of the Ohio-LoCo site.

There was some discussion about hosting at our last meeting about hosting.  Jacob92 was kind enough to offer hosting for the site.  At the time of the meeting, Canonical sponsored hosting was in question.  

Ironically, a request I made two weeks ago was approved today.  

[http://ohio.ubuntu-us.org](http://ohio.ubuntu-us.org)

Here's what we get with Canonical:[LIST]
[*] FTP Access
[*] PHP 4
[*] CGI Support (python included)
[*] MySQL database
[*] E-mail list
[*] 500 MB of disk space
[*] An ubuntu related domain ( like ohio.ubuntu-us.com )
[*]free long term hosting[/LIST]With Jacobs offer:[LIST]
[*]the sky's the limit![/LIST]What are your thoughts?

---

### Post by PWill on 2006-12-07
Jacob for the win.

---

### Post by jpeddicord on 2006-12-07
Hehe, nice wording.

I'm going to add that I can also get custom emails.
Emails can be forwarded or you can use webmail, or an email client. Squirrelmail is available by default for webmail, but I can install other clents such as Horde.

I do feel a little guilty by saying "No thanks" to Canonical right after it is approved however. :-k

---

### Post by Vorian on 2006-12-07
> **jacobmp92 said:**
> 
I do feel a little guilty by saying "No thanks" to Canonical right after it is approved however. :-k

That's on me.  I put the cart before the horse.  You don't need to worry about it:mrgreen:

---

### Post by rrittenhouse on 2006-12-08
I feel we should use the self hosting with the slight worry that it is not registered to the group and by a member (things happen to members all of the time). I just don't want us to get this going and something possibly happen to the hosting and then we have to start over. Besides that I think we can use it with that worry but we could also use the Canonical hosting to maybe redirect to the new domain? ;) It would make us feel less bad but then again maybe we could just let them give the space to others or something.

Whatever we do im sure it'll be the right thing. 

~Robert

---

### Post by steven8 on 2006-12-08
I voted for Canonical, simply because they are the nice folks who gave us Ubuntu.

---

### Post by jpeddicord on 2006-12-08
Yet another idea:

Start out with Canonical hosting, then if our needs grow, then we can switch servers. :-)

---

### Post by earobinson on 2006-12-08
You guys may want to read this [https://wiki.ubuntu.com/MeetingLogs/OpenWeek_UbuntuCommunity](https://wiki.ubuntu.com/MeetingLogs/OpenWeek_UbuntuCommunity) they are trying to make it easy for you guys to get started using there tools

---

### Post by cstudent on 2006-12-08
I vote for Canoncial hosting. It's a gift horse. I also don't think the domain name is that big a deal either. I believe most people click links as opposed to typing in a web address. Plus you should be able to Google it pretty soon after it is up and running.


Just my 2 Lincolns. :)

---

### Post by jpeddicord on 2006-12-08
It appears we're going in the way of Canonical hosting (though it is probably too early to tell completely). I'll go ahead and copy the files over to the Canonical server to check if everything works. I'll see if I can get a copy of PHP5 running too. :)

**EDIT:** Oh noes, SSH was switched off. PHP also appears to be in safe mode, thus diallowing any chance of PHP5. Darn.

---

### Post by meatballhat on 2006-12-09
funny how these things work, eh?  
I have to admit that my guilt it kicking in, too...  Canonical is trying, and if we - along with other startup LoCo's - adopt their preferred channel of LoCo team-hood, I can't imagine we won't see improvements in their offerings as time goes on.   Wishful thinking?  ... probably :p

---

### Post by Vorian on 2006-12-12
One day to go....

---

### Post by Vorian on 2006-12-12
*bump*

---

### Post by steven8 on 2006-12-12
I just think we should stick with Canonical, because they are the gift horse to us.  I see the voting is headed that way, as well.

How much longer for the vote?

---

### Post by Vorian on 2006-12-13
> **steven8 said:**
> How much longer for the vote?

This poll will close on **December 14th, 2006** at **09:45 PM**

---

### Post by steven8 on 2006-12-13
> This poll will close on December 14th, 2006 at 09:45 PM

Could you be more exact? :-)

---

### Post by jpeddicord on 2006-12-13
[http://ohio.ubuntu-us.org](http://ohio.ubuntu-us.org)

I've already ported most of Drupal over, however, I was unable to copy over the databases. You can find some problems I posted on the site that we'll unfortunately have to avoid. If I can convince the admin to turn off safe mode in PHP, it might be a little better. ;)

---

### Post by Vorian on 2006-12-13
Jacob, you are awesome!  I'll email Matt and see what he can flip the PHP mode for you.

---

### Post by Vorian on 2006-12-14
[www.ubuntu-ohio.org](www.ubuntu-ohio.org) it is!

---

### Post by Vorian on 2006-12-15
> **steven8 said:**
> Could you be more exact? :-)

LOL - oops! forgot the seconds, sorry about that.:redface:

---

### Post by steven8 on 2006-12-15
> LOL - oops! forgot the seconds, sorry about that.

Slackard!!

---

