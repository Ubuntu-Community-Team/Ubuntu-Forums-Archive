---
title: "using wget on a site"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by ReaganomicsLamborghini on 2013-03-03
IDK if we are allowed to post outside links to other sites here but I recently registered with Spanishpod101 and a couple of their sister sites. basically these sites have free audio podcasts so you can learn other languages. I wanted to use wget to download all the mp3s and pdfs from the site but I just can't figure it out. I've used wget before on and off for a couple of years to download and mirror sites but I have no clue how to approach this. It's a pain to have to click through each page and use downthemall when I could just get wget and rip the site and sync it to my ipod. Also, they give you full access to the sites for 7 days before they demote you back to basic membership, so does anyone mind checking into this and show me how to use wget on this or any of the sister sites???

---

### Post by TheFu on 2013-03-03
**man wget **
will answer everything.

Something like this
```
$ wget -Amp3 URL
```
should do it.

---

### Post by ReaganomicsLamborghini on 2013-03-03
> **TheFu said:**
> **man wget **
will answer everything.

Something like this
```
$ wget -Amp3 URL
```
should do it.

Nope, that didn't work. I'ma keep skimming around. I've read through the manual a couple of times. Remember I did say I have used wget before. Maybe I'll see if I can spoof the user agent and see how that works.

---

### Post by TheFu on 2013-03-03
[http://blog.jdpfu.com/2009/09/11/wget-rocks](http://blog.jdpfu.com/2009/09/11/wget-rocks)
says to use this: 
```
$ wget -r -nd -A.mp3 URL
```

Obviously, your situation will dictate the specifics.

---

### Post by ReaganomicsLamborghini on 2013-03-05
> **TheFu said:**
> [http://blog.jdpfu.com/2009/09/11/wget-rocks](http://blog.jdpfu.com/2009/09/11/wget-rocks)
says to use this: 
```
$ wget -r -nd -A.mp3 URL
```

Obviously, your situation will dictate the specifics.

I tried using that too but all I get is 5.8mb of html files

---

### Post by lisati on 2013-03-05
> **ReaganomicsLamborghini said:**
> I tried using that too but all I get is 5.8mb of html files

It is possible that the site's webmaster has put some kind of firewall in place to block access by wget and/or IP address, in which case our ability to offer support here will be limited: I've done similar with my website from time to time.

Are there any clues in the HTML files?

---

### Post by TheFu on 2013-03-05
> **ReaganomicsLamborghini said:**
> I tried using that too but all I get is 5.8mb of html files

If you have to sign up, then some sort of cookie related to your authentication is probably need to access those files.
Did you take that into account? Does the wget man page say anything about that, or do you need to use lynx or curl instead?  I know that lynx will let me accept cookies from specific sites Always/Forever, so that could be an option for a little script.  

I'm positive that perl has a way to handle almost all authentication methods too, but that is a steep learning curve when a download manager is really all you want.

I'm not going to sign up to that website - though I do have an interest in improving my terrible Spanish skills.  I've been using memrise and watching telenovelas daily myself.  I've also used Pimsleur, Michel Thomas' methods AND traveled for intensive classes in-country while living with local families.  If you have access to someone in the military, they can check the tapes out from the base library.  I tried Rossetta Stone that way - meh. I did much better with Michel Thomas' method. Some local libraries also have these. By far, the last method was the most rewarding and quickest.  There kids were lots of fun whether they were 2 or 23.  Even the 15-17 yr olds were better than many teens in my area. ;)

BTW, I've used that exact wget command to pull podcasts, but those did not require authentication.

---

### Post by coffeecat on 2013-03-05
@ ReaganomicsLamborghini, you need to read two things. First, go to the spanishpod101.com home page and click on the "terms of use" link at the bottom. Part of this says:

> 8.5 Unauthorized access to the Site is a breach of this Agreement and a violation of the law. Licensee agrees not to access the Site by any means other than through the interface that is provided by Licensor for use in accessing the Site. Licensee agrees not to use any automated means, including, without limitation, agents, robots, scripts, or spiders, to access, monitor, or copy any part of the Site, except those automated means that Licensor has approved in advance in writing.

Now, look at the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy) to which you agreed when you created your forum account. In particular:

> We do not support circumventing TOS, EULA, etc here. 

Thread closed.

---

