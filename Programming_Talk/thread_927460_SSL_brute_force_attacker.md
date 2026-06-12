---
title: "SSL brute force attacker"
date: 2008-09-23
forum: Programming Talk
---

### Post by oneadvent on 2008-09-23
I am looking for a program that will do a brute force attack on an open ssl port.

What are my options with Ubuntu?

Thanks!

---

### Post by CptPicard on 2008-09-23
You could always ask the NSA... ;)

The whole point of SSL is that you're not going to be able to brute-force your way into the traffic. If you could, you really need to file a bug or something.

Now, if SSL is used only to encrypt end-to-end and not authenticate and you can actually get a cleartext connection to the port, then it's all up to whatever is running at the other end.

---

### Post by tinny on 2008-09-23
SSL can be broken. But the thing that makes a crypto system like SSL secure is the fact that it cant be cracked within a reasonable amount of time.

I read an article the other day saying that given todays computing power a hacker would require 1 trillion years to brute force attack a 128bit SSL key.

Good luck.

---

### Post by StOoZ on 2008-09-23
1 trillion years? thats it?

using divide and conquer methods (with many threads...) this can be lowered , I guess.

---

### Post by CptPicard on 2008-09-23
Your amount of threads (and say, distributed boxes) grows linearly, whereas your key space size grows exponentially in the number of bits... that's why this won't work. When you have your million boxes together, all we need to do is to add a few more bits.. :)

---

### Post by annatar on 2008-09-23
> Your amount of threads (and say, distributed boxes) grows linearly, whereas your key space size grows exponentially in the number of bits... that's why this won't work. When you have your million boxes together, all we need to do is to add a few more bits.. 

That might not be of much use when quantum computers come out...:mad:

---

### Post by oneadvent on 2008-09-23
Right, that drifted away....

I meant only as a login to the system. I don't see what is so hard, it asks for a username and it asks for a password. It gives you 3 chances at a password then it ends the connection.

There has to be a program, albeit a slow one, that will brute force the password until it gets in.

I mean if it was a website I could use jack or something, isn't there one for a simple ssl login?

---

### Post by CptPicard on 2008-09-23
> **oneadvent said:**
> 
I mean if it was a website I could use jack or something, isn't there one for a simple ssl login?

If it really was so simple that there was a cracking tool, UNIX security would be a total joke and we'd have a humongous global zombie network in our hands.

Typically a login system makes you wait for an increasing amount of time at each wrong answer, and should limit concurrent attempts. Keyspace size takes care of the rest.

---

### Post by signifer123 on 2008-09-23
> **oneadvent said:**
> Right, that drifted away....

I meant only as a login to the system. I don't see what is so hard, it asks for a username and it asks for a password. It gives you 3 chances at a password then it ends the connection.

There has to be a program, albeit a slow one, that will brute force the password until it gets in.

I mean if it was a website I could use jack or something, isn't there one for a simple ssl login?

You use things like this ([http://www.csc.liv.ac.uk/~greg/sshdfilter/](http://www.csc.liv.ac.uk/~greg/sshdfilter/)) to prevent people bruteforcing. 

But use THC-Hydra to test how long it will take for you to crack your own passwords. It can also check all other sorts of passwords.

---

### Post by oneadvent on 2008-09-23
I had seen THC-Hydra but I did not see where it specifically included ssh attacks.

Thanks for the tip, I will look into it further!

---

### Post by tinny on 2008-09-23
> **StOoZ said:**
> 1 trillion years? thats it?

using divide and conquer methods (with many threads...) this can be lowered , I guess.

There is WAY more to it than that.

> **CptPicard said:**
> If it really was so simple that there was a cracking tool, UNIX security would be a total joke and we'd have a humongous global zombie network in our hands.

Typically a login system makes you wait for an increasing amount of time at each wrong answer, and should limit concurrent attempts. Keyspace size takes care of the rest.

Not to mention that usually important sites will lock you out after 3-5 failed login attempts.

Hackers have pretty much given up on this type of attack and rather go for a key logging or phishing approach.

But an over confident student will always waste their time... :)

---

### Post by CptPicard on 2008-09-23
> **tinny said:**
> 
But an over confident student will always waste their time... :)

As pmasiar likes to say... attitude is no substitute for competence.

---

### Post by oneadvent on 2008-09-23
Well so far I have tried a bunch of times and it hasn't locked me out.

How about a deb of Hydra? or better yet xhydra?

Ye of little faith.

---

### Post by tinny on 2008-09-23
> **oneadvent said:**
> Well so far I have tried a bunch of times and it hasn't locked me out.

How about a deb of Hydra? or better yet xhydra?

Ye of little faith.

Being locked out has nothing to do with SSL. Any web site worth its weight will lock you out after X failed attempts.

What exactly are you doing? Do you have some sort of automated program that hits a web site with different user name and password combinations? If so you are not attacking SSL.

To attack SSL you will need to somehow get a sample of an SSL encrypted HTTPS request and then run your genius brute force attack on that. E.g Run the encrypted request though a cipher with many many... different key combinations. (Brute force attack in its simplest form)

---

### Post by tinny on 2008-09-23
BTW: It looks to me like this THC-Hydra attacks weak passwords not SSL.

---

### Post by cprofitt on 2008-09-23
> **tinny said:**
> SSL can be broken. But the thing that makes a crypto system like SSL secure is the fact that it cant be cracked within a reasonable amount of time.

I read an article the other day saying that given todays computing power a hacker would require 1 trillion years to brute force attack a 128bit SSL key.

Good luck.

Assuming your 128bit SSL key actually had 128bits of randomness - yes.

---

### Post by slavik on 2008-09-23
there is a project that took a 64bit encrypted message and a decrypted message and then tried to find the key using brute force ... took them like 5 years (this is a distributed system a la seti@home/folding@home). Now, they are doing the same with 75 bits, when they were asked about 128bit AES ... they said they would never try it.

---

### Post by oneadvent on 2008-09-23
Okay its like this, maybe i'm wrong on the terminology, I type:

```
ssh -l Administrator 207.151.177.30
```

It then asks for my password, which it gives me 3 chances of guessing.

Now, there has to be a program that will try passwords out of a list file until it gets in.

---

### Post by drubin on 2008-09-23
> **oneadvent said:**
> I am looking for a program that will do a brute force attack on an open ssl port.

What are my options with Ubuntu?

Thanks!

Is this even a valid question on these forums? asking for a hacking program?

---

### Post by oneadvent on 2008-09-23
I'm sorry if I crossed the line, they can delete my thread, but this is something that should be available, if not just for the security standpoint.

---

### Post by drubin on 2008-09-23
> **oneadvent said:**
> I'm sorry if I crossed the line, they can delete my thread, but this is something that should be available, if not just for the security standpoint.

It is ok I assume (I am not a mod).

What security standpoint would this be about? as the other posts have listed Brute force is next to imposible giving a humans lifespan and the average life span of  a server. 

You will be dead and have replaced the server before you would crack it by brute force.

---

### Post by oneadvent on 2008-09-23
See thats what i'm not understanding, if I were to open the dictionary and start trying passwords from the beginning it would take maybe a couple months, but it could be done, now automate that and do it w/o front end display times. 

And the practical application would be someone testing their own box remotely.

---

### Post by drubin on 2008-09-23
> **oneadvent said:**
> See thats what i'm not understanding, if I were to open the dictionary and start trying passwords from the beginning it would take maybe a couple months, but it could be done, now automate that and do it w/o front end display times. 

And the practical application would be someone testing their own box remotely.

That is a little different from asking for an application to brute force a password. brute force is supposed to try /ever/ possible combination. Your method limits it to dictionary words. hugely less. 

I do have another question on this topic what is the encryption algorim used to use your login password in the /etc/shadow file.

---

### Post by oneadvent on 2008-09-23
this is my shadow file:
> 
root:!:14138:0:99999:7:::
daemon:*:14062:0:99999:7:::
bin:*:14062:0:99999:7:::
sys:*:14062:0:99999:7:::
sync:*:14062:0:99999:7:::
games:*:14062:0:99999:7:::
man:*:14062:0:99999:7:::
lp:*:14062:0:99999:7:::
mail:*:14062:0:99999:7:::
news:*:14062:0:99999:7:::
uucp:*:14062:0:99999:7:::
proxy:*:14062:0:99999:7:::
www-data:*:14062:0:99999:7:::
backup:*:14062:0:99999:7:::
list:*:14062:0:99999:7:::
irc:*:14062:0:99999:7:::
gnats:*:14062:0:99999:7:::
nobody:*:14062:0:99999:7:::
libuuid:!:14062:0:99999:7:::
dhcp:*:14062:0:99999:7:::
syslog:*:14062:0:99999:7:::
klog:*:14062:0:99999:7:::
hplip:*:14062:0:99999:7:::
avahi-autoipd:*:14062:0:99999:7:::
gdm:*:14062:0:99999:7:::
pulse:*:14062:0:99999:7:::
messagebus:*:14062:0:99999:7:::
avahi:*:14062:0:99999:7:::
polkituser:*:14062:0:99999:7:::
haldaemon:*:14062:0:99999:7:::
oneadvent:$1$6Bx/Gy2o$KcOkNtVBYljxAqmiIlY5z0:14140:0:99999:7:::


well using a dictionary should be the idea used here.

---

### Post by tinny on 2008-09-23
So lets say we are trying to brute force a login. We need both a user name and password.

The user name is say 8 base 64 characters and the password is 8 base 64 characters.

I may be wrong but in total that's 1.1579208923731619542357098500869e+77 combinations, right?

Also, any worth while system should have measures in place to detect a denial of service attack (even if its a weak attack) E.g repetitive hits from a single IP.

We are dealing with unimaginable numbers here. (If the user has chosen a strong password, personally I don't use any words that exist in the dictionary)

Targeting weak user name / passwords may be a different story...?

---

### Post by LaRoza on 2008-09-24
> **CptPicard said:**
> If it really was so simple that there was a cracking tool, UNIX security would be a total joke and we'd have a humongous global zombie network in our hands.


Ssh! That is the basis for my runtime...

> **CptPicard said:**
> As pmasiar likes to say... attitude is no substitute for competence.

Except in politics.

> **rubinboy said:**
> Is this even a valid question on these forums? asking for a hacking program?

No. Although it is impossible, thus, not closed.

---

### Post by LaRoza on 2008-09-24
> **tinny said:**
> 
I may be wrong but in total that's 1.1579208923731619542357098500869e+77 combinations, right?

Give or take a couple.

---

### Post by LaRoza on 2008-09-24
> **rubinboy said:**
> 
You will be dead and have replaced the server before you would crack it by brute force.

Machines are patient...

---

### Post by drubin on 2008-09-24
> **LaRoza said:**
> Machines are patient...

/me runs for the hills, LaRoza going into hacking mode. 

I am offically going to pack up and move to the mountains and live in a mud hut where the machine can not find me. :)

---

### Post by oneadvent on 2008-09-24
See but you are all failing to narrow the possibilities down, for instance we can assume that most people that are using windows machines don't change the default user, so we can have a file of "passwords" being 2000 or so long and a file of "usernames" being 20 or so long, now we have narrowed our attempts to 40k...and say on average it takes 4.5 seconds (10 seconds to log in and 1 second each time for 3 chances.) times 40k gives us a total time to run time of 50 hours, or two days roughly, as a failure, less with passing.

Now someone tell me that isn't possible.

I bet that kind of program would succeed 70 or so percent of the time.

---

### Post by slavik on 2008-09-24
> **oneadvent said:**
> See but you are all failing to narrow the possibilities down, for instance we can assume that most people that are using windows machines don't change the default user, so we can have a file of "passwords" being 2000 or so long and a file of "usernames" being 20 or so long, now we have narrowed our attempts to 40k...and say on average it takes 4.5 seconds (10 seconds to log in and 1 second each time for 3 chances.) times 40k gives us a total time to run time of 50 hours, or two days roughly, as a failure, less with passing.

Now someone tell me that isn't possible.

I bet that kind of program would succeed 70 or so percent of the time.
that's not a brute force attack anymore, it is now a dictionary attack.

Now, onto nitpicking. SSL is used for encryption not authentication. authentication is done with hashes (md5 is very common, although there is a move to the SHA family now).

so, here's something simple to crack ... pick a 64bit symmetric key encryption method (triple DES or such) and then encode a message with some key. record the time needed to make the encryption. if it's too fast, do it like 100 times or something (and take the mean). then take the time and multiply it by 2^64 (number of possible keys in 64bit) ... now you have the time it would have taken you to try all possible keys on your system. if you want, convert the key to an unsigned int and multiply it by the average encryption time and you get the time you'd need to get to that key.

you can do the same with 128bit ... if you want more fun, try a 256bit AES ...

if you want more fun, try a 1kbit SHA2 :)

---

### Post by oneadvent on 2008-09-24
Right thats all fun, but I'm talking very basic here guys. A batch type program that just continues to try just like if I sat here and did it myself. 

Isn't there a program for that sort of attack?

---

### Post by slavik on 2008-09-25
never seen one and if you were trying to log in to a system where there is an increasing timeout before you can try again, it would take a long time ...

---

### Post by oneadvent on 2008-09-25
Well I sat here for 10 minutes doing it and I did not get slower, just much more annoying. Thats when I thought, surely someone has seen this weakness and written a program to exploit that.

Surely.

---

### Post by tinny on 2008-09-25
> **oneadvent said:**
> Well I sat here for 10 minutes doing it and I did not get slower, just much more annoying. Thats when I thought, surely someone has seen this weakness and written a program to exploit that.

Surely.

](*,)

What weakness!?!?!?

---

### Post by oneadvent on 2008-09-25
OMG I explained it like 4 posts ago.

Using a dictionary attack of 2000 words and 20 usernames you could easily crack into 70 percent of computers running ssl on default values in 2 days.

That is a weakness. Now such a weakness would not apply to a Linux computer.

I'm sorry I fail to see how you see no weakness in a 2 day hack.

---

### Post by tinny on 2008-09-25
Im sorry but you really are clueless.

Think about it. 70% of computer users (hundreds of millions) can be reduced to just 20 user names.

> 
running ssl on default values


Can you please explain default ssl values...

---

### Post by oneadvent on 2008-09-25
No you just aren't thinking outside of the box.

I'm saying 20 percent of people on Windoze machines that just use whatever default username their computer comes with. Or they choose things like Mine or Sister or whatever, that would be a small list.

Look you are assuming that people that do not use windows want a secure password on their computer and the fact is they do not. They want something easy to remember.

---

### Post by y@w on 2008-09-25
Are you talking about SSL or SSH? I fail to see how SSL has anything to do with any of this..

---

### Post by oneadvent on 2008-09-25
OMG

Your right. This has become a total fail thread by that one error.

Yes I meant SSH....

:(

---

### Post by slavik on 2008-09-25
you need to read about botnets and how people take computers over, you are making a complicated solution to a simple problem.

---

### Post by oneadvent on 2008-09-25
Um so admin....anyway we can change this to SSH in the title?

---

### Post by y@w on 2008-09-25
Ok, you keep saying SSL..

Anyway, you are absolutely right.. SSH is not inherently secure. Just because it's encrypted end-to-end doesn't make it secure. It's secured either by using alternative authentication practices or strong passwords or some other means. Using the default openSSH settings, it's pretty easy to get brute forced. However.. Windows doesn't come "out of the box" with an SSH server so I don't see how that applies. 

It's not necessarily a weakness in SSH.. Anyone could put up an open relay SMTP server if they wanted, too.

---

### Post by oneadvent on 2008-09-25
So what program can I use to do that?

Cause Hydra is apparently impossible to install.

---

### Post by y@w on 2008-09-25
I haven't dabbled on that side of brute-forcing an SSH connection, so I wouldn't know. It looked like it would be a straight-forward compile though..

---

### Post by y@w on 2008-09-25
I'm still very curious on how you plan on doing this with Windows, however.. 

Like slavik said I think you're over-simplifying the solution.

---

### Post by oneadvent on 2008-09-25
Ya well I cant figure it out, and I'm not alone there is a thread for that evil program. I dont understand why they cant just make a deb of it and save us all the pain of figuring out what dependency isn't met.

---

### Post by LaRoza on 2008-09-25
> **oneadvent said:**
> Um so admin....anyway we can change this to SSH in the title?
No. I left it open because SSL was impossible. Such discussions are not allowed on the forum ;)

> **y@w said:**
> 
However.. Windows doesn't come "out of the box" with an SSH server so I don't see how that applies. 


Neither does Ubuntu.

---

### Post by tinny on 2008-09-25
> **oneadvent said:**
> OMG

Your right. This has become a total fail thread by that one error.

Yes I meant SSH....

:(


Ok so now we are talking about SSH. ;) ;) ;) (Correct acronyms are important :) )

So your theory is that there are all these Windows noobs using "sister", "brother", "mum" etc... as a user name on their windows machines that they have taken the trouble to install an SSH server on right?

Now, is the above a likely scenario?

Anyway, yes a POORLY setup SSH server can be brute forced. But it is just sys admin 101 to setup a SSH server correctly. 

FYI: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

(Now I think it is time to close this thread as no good can come out of answering the OP's question: **"So what program can I use to do that?"**)

---

### Post by LaRoza on 2008-09-25
> **tinny said:**
> 
(Now I think it is time to close this thread as no good can come out of answering the OP's question: **"So what program can I use to do that?"**)

Quite right. Closed.

---

