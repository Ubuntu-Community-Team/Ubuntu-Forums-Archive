---
title: "Internet Server"
date: 2007-08-18
forum: Programming Talk
---

### Post by Lster on 2007-08-18
Are there any services on the internet that would allow me to host my server online. I would need full access to it; it would have to be linux; and it must be online 24/7. Do companies offer this kind of thing - and how much does it cost (roughly)?

I'm interested in hosting a small MORPG that is already working well when I test it locally, you see. It would be a lot of fun to host it globally.

Thanks,
Lster

---

### Post by pmasiar on 2007-08-18
Cheap shared hosting companies frown upon long-running precesses like MMORPG - they cannot afford one user hog CPU for too long. But you can have dedicated server hosted for about $100 a month.

---

### Post by Bachstelze on 2007-08-18
$100 a month ? Here, you can have one for 25 &#8364;/month.

---

### Post by trwww on 2007-08-19
Hello,

I rent my dedicated dev servers from crystaltech.com and my production servers from cari.net. I get them elsewhere, too, but these offer the best value for the service.

Regards,

trwww

---

### Post by Lster on 2007-08-19
Thanks, trwww. Would I be able to run my custom Linux Game Server on that both of those? They all seem to talk about hosting a website but I would also want to run my own game server.

Thank you guys,
Lster

---

### Post by Lster on 2007-08-20
*Bump*

---

### Post by ssam on 2007-08-20
it depends what hardware you want.

i have started with [http://www.slicehost.com/](http://www.slicehost.com/) with a 256mb ram xen virtual server for $20 per month. it can do anything that a real sever can do (you get full root access), but you share cpu with other users. there are a few others such as [http://www.gplhost.com/hosting-vps.html](http://www.gplhost.com/hosting-vps.html) (or google for xen virtual server).

to get a whole server will cost more.

---

### Post by LaRoza on 2007-08-20
> **Lster said:**
> ...small MORPG ...


That is a strange description.

---

### Post by trwww on 2007-08-21
> **Lster said:**
> Thanks, trwww. Would I be able to run my custom Linux Game Server on that both of those? They all seem to talk about hosting a website but I would also want to run my own game server.


As I mentioned in my reply, what you need is a dedicated server.

---

### Post by Lster on 2007-08-21
> That is a strange description.

Yes. It could potentially get big :).

I have never used a remote server. Is my access to it command line of graphical. As I doubt it even has a GUI, I bet it is command line! I would have no idea how to control a server.

For example, if it was a Ubuntu server, could I do some apt-get to install a package? How would I upload files to the server? I guess I really need a 'Managed Dedicated Web Servers For Dummies Book' book - are there any guides?

Thanks,
Lster

---

### Post by pmasiar on 2007-08-21
> **Lster said:**
> Is my access to it command line of graphical. As I doubt it even has a GUI, I bet it is command line! 

Yes, likely it will be commandline to start. But it is your own, you can install on it whatever you want. But you also have responsibility to make it secure - server like that (always online, with fast connection) would be prime target for crackers. So if you don't feel ready for it, it's because you aren't :-)

Learn more about linux. Learn administering, security. You can install any GUI on your own server - just many admins prefer not to, because GUI consumes resources they prefer to be used for serving. 

Personally for my, Midnight Commander  (mc) simplifies admin tasks a lot, it is very visual without GUI, using only characters. It is 20 years old, well-proven technology... :-) Good stuff.

> For example, if it was a Ubuntu server, could I do some apt-get to install a package? 

yes.

> How would I upload files to the server? 

puTTy is great, or mc can ftp to the site.

I guess I really need a 'Managed Dedicated Web Servers For Dummies Book' book - are there any guides?

A lot of guides - a lot of would-be admins are exactly in position like you, learning. you are not alone.

---

### Post by Lster on 2007-08-21
Thank you lots. I think your advise is good - maybe I am not ready.

I am sure my MMORPG is pretty secure and I can build in protection for DOS attacks (although I have no idea how to protect against DDOS attacks). I might also use Apache.

What protection might I need - something like Firestarter? Also, the thing that is most worrying me: say I got cracked, would it be possible to reinstall or in anyway recover the server?

As i said, **thank you**!
Lster

---

### Post by CptPicard on 2007-08-21
Don't worry about them talking about website hosting -- they do that because that's what most people do -- host websites. You don't have to.

For example I am currently setting up a dotcom on a dedicated server from Amenworld.com, and it's mercifully bare-bones... just a fairly minimal Debian box I just upgraded to Etch and am customizing to my heart's content. A dedicated server is just that -- a Linux machine at the end of the Internet tube, and you can use it for whatever.

As far as managing it goes, you just ssh into it and use it over the command line like you use your own box. There is no difference. It's bash, just like your local bash.

You DO manage your own box using the shell.. right? :)

---

### Post by triptoe on 2007-08-21
Ultimately wouldn't it be cheaper or more cost effective to use your own hardware for a server and lease the bandwith ? Or is the upload capped on cable and DSL lines?

---

### Post by Lster on 2007-08-21
My internet is capped at 5GB per month so it isn't really possible to host here,

> Don't worry about them talking about website hosting -- they do that because that's what most people do -- host websites. You don't have to.

For example I am currently setting up a dotcom on a dedicated server from Amenworld.com, and it's mercifully bare-bones... just a fairly minimal Debian box I just upgraded to Etch and am customizing to my heart's content. A dedicated server is just that -- a Linux machine at the end of the Internet tube, and you can use it for whatever.

As far as managing it goes, you just ssh into it and use it over the command line like you use your own box. There is no difference. It's bash, just like your local bash.

You DO manage your own box using the shell.. right? 

Thank you. It doesn;t sound too hard... Could you show me an example command of using SSH to gain control of a computer. Maybe you know a guide? What SSH clients are best (for newbies)?

I looked on Wikipedia, but it doesn't give examples...

---

### Post by ssam on 2007-08-21
> **Lster said:**
> My internet is capped at 5GB per month so it isn't really possible to host here,



Thank you. It doesn;t sound too hard... Could you show me an example command of using SSH to gain control of a computer. Maybe you know a guide? What SSH clients are best (for newbies)?

I looked on Wikipedia, but it doesn't give examples...

openssh-client and openssh-server are the most common to use on ubuntu.

the client is installed by default.

if you install the server package you should be able to do
```
ssh localhost
```

note: if you install the server people can now log into your computer if they know (or can guess) your username and password. if you are on the open internet expect a few bruteforce attacks a day. have a look in the servers forum [http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7) you'll find a few threads on these sorts of issues.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) looks useful

---

### Post by Lster on 2007-08-22
Thank you all very much! I know all I need I think...

---

