---
title: "PHP help"
date: 2011-10-19
forum: Programming Talk
---

### Post by Damascushead on 2011-10-19
I am beginning to program with PHP. In fact I already have a script written which is part of a web design I am working on. However I need some help figuring out how to test my scripts.

I know I need to install the PHP library, but I don't know how to test it. I don't have any kind of server running. Is it possible to test it without a server? Is a framework something I need in order to test PHP? Do I need to install Apache Server? I am just having a bit of trouble understanding how to get started, and the forum posts I have seen have not answered my questions.

Any help would be appreciated!

---

### Post by satanselbow on 2011-10-19
So you've written a php script without having php installed? Isn't that rather putting the cart in front of the horse?

A good place to start might be: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Damascushead on 2011-10-19
Yeah. I guess what I am asking is do I need a LAMP setup in order to test out my script? Is there a way that I can just use PHP without setting up a server?

And yes I know writing a script without installing the library is backwards, but I had something very specific in mind when writing it. It really is an AJAX function which calls a PHP script.


[Revision]- satanselbow- thanks, it looks like LAMP may be the way to go in order to test PHP locally. I was just looking for a really quick way to test my php script without delving into putting a server together. 


Any suggestions from others would still be helpful

---

### Post by satanselbow on 2011-10-19
You can run php from the command line without a server bu theat is pretty useless for web development purposes ;)

---

### Post by GWBouge on 2011-10-19
While you *can* throw the LAMP setup on your desktop and point your browser to localhost for quick testing, I don't think anyone would really advise it.  I find it easiest to just set up a quick Ubuntu Server install in VirtualBox to throw stuff at.

---

### Post by satanselbow on 2011-10-19
> **GWBouge said:**
> While you *can* throw the LAMP setup on your desktop and point your browser to localhost for quick testing, I don't think anyone would really advise it.  I find it easiest to just set up a quick Ubuntu Server install in VirtualBox to throw stuff at.

Just adds more clicks IMHO - you still have to install/config a server somewhere and if you are not familiar with installing a local server why add installing a, possibly, unfamiliar OS variant to the mix as well?

On what evidence do you base your sweeping, personal opinion based generalisation?

---

### Post by Damascushead on 2011-10-19
Upon further reading I saw XAMPP. Is this a quality alternative to a full LAMP install?

GWBouge- thanks for the advice, however I don't think I want to delve into installing Ubuntu Server.

---

### Post by satanselbow on 2011-10-19
> **Damascushead said:**
> Upon further reading I saw XAMPP. Is this a quality alternative to a full LAMP install?

GWBouge- thanks for the advice, however I don't think I want to delve into installing Ubuntu Server.

XAMMP is a out-the-box LAMP installation that is popular with some folks - not a bad solution for a quick n dirty sever and would get you up n running with a minimal amount of configuration ;)

I haven't used it myself for a long old while so cannot really comment further - apart from YES! it would do the job :D

---

### Post by GWBouge on 2011-10-19
> **satanselbow said:**
> On what evidence do you base your sweeping, personal opinion based generalisation?

Read the sig  =oP

S/He asked for suggestions, I provided mine, simple as that.  An Ubuntu Server install takes very little config aside from ticking the boxes for the LAMP stack, there's guides with screenshots around.  And, in my **sweeping, personal opinion based generalisation**, it's not a bad idea to get to know what's behind the stuff you're writing, and if you're uncomfortable with the whole deal, do you really want to mess about installing web services on your desktop?

I'm also curious, are there any advantages to a XAMPP setup aside from just doing:

```
sudo apt-get install apache2 mysql-server php5
```

I'm really not trying to argue here, honest questions, trying to get some more info out there.

---

### Post by Damascushead on 2011-10-19
I am not sure how it differs, I just know it caters more to the developmental process as opposed to actually hosting a site. 
Thanks satanselbow.

---

### Post by mörgæs on 2011-10-19
It is very easy to install LAMP, and it takes few system ressources to run.

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

I would recommend this, if you are aiming for developing PHP.

---

### Post by Damascushead on 2011-10-19
Thank you very much. I think I will give her a try! case closed lol

---

