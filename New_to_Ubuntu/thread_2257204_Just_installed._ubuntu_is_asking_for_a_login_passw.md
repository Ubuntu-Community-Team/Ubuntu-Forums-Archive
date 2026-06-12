---
title: "Just installed. ubuntu is asking for a login password but no setuo for one at instal?"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by gregory10 on 2014-12-17
At the time of installing this dedicated server version of ubuntu and with lamp included at instalation

The aim is to be able to experiment using a dedicated box and get some experience setting up and configuring like a dedicated webserver.
So did the instalations took the easy route on at all stages when prompted during the instal

Now comes the problem ubuntu server is asking me  to login and says this below with prompt flickering
ubuntu login:

there was no time in the instalation that I remember being asked to provide a password for login
so I'm stuck and did try to look up some info on this in the manual
could somebody please help? I would really appreciate it thanks for any help anybody can give me with this

---

### Post by Bashing-om on 2014-12-17
gregory10; Hi !

> **gregory10 said:**
> At the time of installing this dedicated server version of ubuntu and with lamp included at instalation

The aim is to be able to experiment using a dedicated box and get some experience setting up and configuring like a dedicated webserver.
So did the instalations took the easy route on at all stages when prompted during the instal

Now comes the problem ubuntu server is asking me  to login and says this below with prompt flickering
ubuntu login:

there was no time in the instalation that I remember being asked to provide a password for login
so I'm stuck and did try to look up some info on this in the manual
could somebody please help? I would really appreciate it thanks for any help anybody can give me with this

When you installed you were required to provide the system with a "username" and a "password" . That username followed by the password is what is being requested at this time. ( when pass word is entered, there is absolutely no response to the screen - enter password blindly and hit the enter key .

[INDENT]won't do anything, 'till
[INDENT][INDENT][INDENT]you tell the system who you are and authenticate
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregory10 on 2014-12-17
No thats my point it didn't ask me for a user name and password 
this is the problem I was not prompted for a user name or passward

---

### Post by Tadaen_Sylvermane on 2014-12-17
I would check the hash of the download you got and make sure it is official. It should always make you set a username and password. Worst case you can load a live disk and chroot in and create a user and password.

---

### Post by ian-weisser on 2014-12-17
> **gregory10 said:**
> At the time of installing this dedicated server version of ubuntu and with lamp included at instalation

Could you please tell us where you got this 'dedicated server version with lamp included' from?
A link would be most helpful.

---

### Post by gregory10 on 2014-12-18
I got it sorteed after reading another question here about root password no working. I have the same thing in a different way.
basically when installing I was looking for a prompt to create a root password but all they prompted me with was a a list of decisions on various things to include in the installation; one of them being to create user(s) with passwords. Well I skipped it wanting to just have root no users. 

I re-installed now and put a user in just one. So now I can log in and no gui which is going to be an interesting experience that I am looking forward to.
in answer to your question I got if from this site using the repository link in the server page(s). It went ok downloaded the image and made a cd seeing it was around 500miG
thing are OK it works well so far so good. I guess this is solved now.

thanks for any comments and help it all helps

---

### Post by Bashing-om on 2014-12-18
gregory10; Great !

Pleased you are up and running. 

Yeah, a server install has no GUI, It is an added burden for security. If, however, one understands the risks It can be acceptable to install a GUI ( there are scores of desktops available).

As you have questions/concerns, do not hesitate to ask.

[INDENT][INDENT][INDENT]help is what we do
[/INDENT][/INDENT][/INDENT]

---

