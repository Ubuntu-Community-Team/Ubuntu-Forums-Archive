---
title: "Learning PHP, thinking of hosting"
date: 2005-01-18
forum: Programming Talk
---

### Post by mcollins on 2005-01-18
I'm learning PHP, although it's taken a back seat as I've been learning Linux. But my machine is running awesome now and it's time to get back to my studies. I have a website that's hosted by a company that uses the LAMP setup. So on windows I would just upload my files to my server to test them out. Of course now I'm thinking maybe I should set up my own LAMP combo and test my PHP pages locally. I have cable internet, I could even try hosting my site! But I might be in over my head just thinking about it. I've been reading old postings and some of them sound scary. My web host works, they have the CPanel and all, and I get plenty of bandwidth to test stuff. I notices the Ubuntu repositorys have what I need, saving me from having to compile source code. If it's easy enough I'll do it. What do you think?

Oh, and about editors. In Windows I was using Dreamweaver. That's not an option now. To be honest it was a little too bloated for me anyway. I don't know about you but when there are tons of menus and panels, I get distracted. I'm always thinking there's something I need to configure. I like simplicity. I noticed a lot of you are using VIM. I'm already learning that, for editing config files. It might be all I need for PHP files, especially at my level right now.

---

### Post by LB06 on 2005-01-18
I am running a LAMP server too on Ubuntu, because I don't want to pay for a host if my website isn't finished anyway. The only minor hickups I encountered were the strange config layout for Apache inherited from Debian and the fact that I couldn't get mysql running through apache/php. This could be fixed by installing php4-mysql from universe and uncommenting a line from php.ini (load mysql.so or sth). I think this issue will be fixed in Hoary.

---

### Post by jdodson on 2005-01-18
i use ubuntu for LAMP as well.  runs really well.  i had to do some config file diving like you mentioned.  in the end it was easier to setup LAMP in fedora, but after it is all setup its not that big of a deal.

---

### Post by defkewl on 2005-02-12
So what is your problem now? I can't seem to find your problem based on your posting.

---

### Post by ups on 2005-02-13
I'm also running LAMP, and there's not much configuration I needed - except for the mysql extension loading part.

As for editors, there are several available - bluefish, nvu, screem - u can search the forum for more on them.

---

### Post by Jad on 2005-02-14
if you are noob at all in configuring your local LAMP, install Xamp, from apachefriends.org, its nice 
and you can swtich between php4 and 5 with a single command, which I like it.

---

### Post by Jad on 2005-02-14
one more good feature, all of Xamp configuration files, are in one folder, this will make your lamping life much easier, specially for testing.

---

