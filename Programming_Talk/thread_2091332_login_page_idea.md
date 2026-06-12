---
title: "login page idea"
date: 2012-12-04
forum: Programming Talk
---

### Post by conradin on 2012-12-04
Hi all, 
I was looking for unique (website) login page ideas, and started to realize they all look exactly the same. So then I thought maybe voice logins would be cool. But that also sounded hard to implement. Ive come to the idea that maybe my website could have an array of fake and real users to select from, and require a checksum of some sort. Maybe the login process could be changed somehow to be even simpler. 

Im interested on other peoples thoughts about this.

---

### Post by Tony Flury on 2012-12-05
By providing a list of users (some real and some fake), you make it easier for someone to break in - as you have told them all of the valid users names - and they just have to keeping picking names until one works.

Ideally you need to have something secret that is only known to a valid user and uiquely identifies that user (and only that user) - that is why most logins tend to be 2 (or even 3) item logins - you identify the user and the user provides a secret as two seperate items. Combining them into one item risks your site as a user only has to write down and loose one item - rather than having to wwrite down and loose both items (I know i ocassionally write down my obsufcated password - none of my usernames are writen down; so if I ever loose my password security is compromised less, as any attacker still has to work out my user name).

Bear in mind any security system ideally has 4 functions : 
[LIST]
[*]Authentication - Do you know who is logging in, and that they are allowed to do so.
[*]Access - Can the users access the data they need to, but only access the data they are allowed to
[*]Auditing - Can we track what the users do and what they change.
[*]Recovery - Ae we able to recover previous data states. 
[/LIST]

You should ask yourself does your system implement these (or at least the first two), and is it easier or harder for someoe to gain unauthorised access.

---

