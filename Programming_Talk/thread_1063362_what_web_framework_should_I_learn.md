---
title: "what web framework should I learn"
date: 2009-02-07
forum: Programming Talk
---

### Post by NinjaWork on 2009-02-07
I'm leaning towards Pylons on the Python side and CodeIgniter on the PHP side. Problem is, there are so many out there.

For Python, I could do TuboGears, Django (really a CMS?), etc. PHP has Symfony, Smarty (templating?), etc. Perl has Maypole, Catalyst, etc. Ruby has Rails, Camping...

BTW...anyone use a VPS? I'm pretty excited about checking one out at either SliceHost or Linode.

TIA ;)

---

### Post by tomchuk on 2009-02-07
I use Django every day and love it. Drupal pays the bills though. These days it's in a weird inbetween space of Content Management Framework -- more than your standard MVC framework and a better dev platform than your average CMS. In all honesty I didn't have a great time using CI, but that might just be me. Web.py appeals for its simplicity and lack of "magic". My Brother swears by Symfony and has made a truckload of cash in the last couple months working in it.

Personally, I'm investing my time in Django, the code and community just feel right to me. But I didn't come to this decision quickly -- I've hacked around in Catayst, CI, Symfony, Pylons, etc. to come to this decision. I suggest you do the same - they are all valid choices, it really boils down to what feels right to you.

As far as VPSs go, I've been with Rimuhosting for years and never had a problem. I've got a VPS in Texas and a dedicated box in NY through them and have had nothing but a great experience with both.

---

### Post by NinjaWork on 2009-02-08
Hi tomchuk, thank you for the great information. I'm pretty new to frameworks, but I can see what you mean about how Django feels right and has a good community behind it. I think I'll take your advice, though, and play around with a bunch and see how they each work.

I did do a few Drupal mods last year and, although Drupal is intense, it is very obtuse to the uninitiated. I thought..."oh yeah, I know PHP"...boy, was I wrong! My advice, if anyone wants to make mods for Drupal is to buy the Drupal book.

Thanks also for the tip on Rimuhosting.

---

### Post by Colonel Kilkenny on 2009-02-08
Django with Python.
PHP is a bit trickier. There's CodeIgniter, CakePHP, Kohana (fork of CodeIgniter), Zend Framework, Symfony, etc.
Atm I would probably go with Kohana which is basically improved CodeIgniter with some sort of ORM etc. CakePHP has quite horrible documentation so I wouldn't use it.

Drupal & Wordpress are quite good both when talking about CMS. Of course they have their own problems as well.

---

### Post by attilagyorffy on 2009-02-09
I'd recommend digging into these frameworks:

**Ruby On Rails (Ruby)**
[http://www.rubyonrails.org](http://www.rubyonrails.org)
This one is far my favorite, it is getting more and more popular these days and it is full open source.  It is built on the top of the 'funkyness' what the Ruby language offers, also it uses the MVC design pattern, which is quite useful in the web development area.

**Django (Python)**
[www.djangoproject.com](www.djangoproject.com)
Well, I've just started to use Django a couple of weeks ago, and so far I love it. It's so similar to the Rails framework in some ways. It is based on the top of MVC too, and because of the two languages (Ruby and Python) share a lot of behavior, you could get familiar with it pretty easily if you already have Ruby/Rails experience.

These are the two what i am currently using and I can honestly recommend them.

---

### Post by NinjaWork on 2009-02-20
thanks again everyone.

At first, I thought install half a dozen and try them all, but then I'm thinking when I program in Python, I forget Perl and PHP, when I program in PHP, I forget Python and Perl, etc.

So...probably, best thing to do is focus and choose the best, which I think is Django.

---

### Post by s.fox on 2009-02-20
> **Colonel Kilkenny said:**
> Django with Python.
PHP is a bit trickier. There's CodeIgniter, CakePHP, Kohana (fork of CodeIgniter), Zend Framework, Symfony, etc.
Atm I would probably go with Kohana which is basically improved CodeIgniter with some sort of ORM etc. CakePHP has quite horrible documentation so I wouldn't use it.

Drupal & Wordpress are quite good both when talking about CMS. Of course they have their own problems as well.

I totally agree with Colonel Killkenny.  I also agree about the CMS,  though I used one once (Joomla) and wouldn't want to use one again.  I just found it too limiting.

---

### Post by OliW on 2009-02-20
Another vote for Django. Only been using it since October but I've built around a dozen now-production sites in it and couldn't be happier. It's definitely not a CMS but it really has everything you'd want to build a custom one. I've gone from hacking things in and out of existing CMSes to spending half the time creating what I need.

As for VPS, I'd seriously suggest Linode. They're super-awesome people with super-duper-awesome server and they're miles better than Slicehost in terms of features especially if you or your audience is Europe based (their NJ datacentre pings really well from England, for example).

In terms of stack, I'm using Cherokee, Django through its SCGI output, SQLite, and serious amounts of memcache. I'm on a Linode 540, handling 3000 visits a day at the moment... Averaging less than half a percent of CPU in the past 24 hours.

I'm about to port my main site over, so perhaps I'll break 1%* =)

*If nobody else if using their share, you can sustain a burst of up to 400% CPU

*cough* Here's my referral code if you want to gift me $20 18f121d2d8e8985a3bd752b945f5410ba2627e69 *cough*

---

### Post by Pharaoh Atem on 2009-04-11
Try Enano CMS, it has a rather complete documentation of its framework in the Mercurial repository. The project is about making a CMS wiki hybrid, while being incredibly modular and secure. Reading the [features page](http://enanocms.org/Features) seems to show a lot of focus towards ease of use and security.

Link to developer page: [http://enanocms.org/Developers](http://enanocms.org/Developers)

---

