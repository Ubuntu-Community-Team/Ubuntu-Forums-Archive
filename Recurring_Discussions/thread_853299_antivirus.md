---
title: "antivirus?"
date: 2008-07-08
forum: Recurring Discussions
---

### Post by jimi_hendrix on 2008-07-08
:guitar:

is there a good free linux compatable antivirus out there i can get?...

---

### Post by wolfen69 on 2008-07-08
unless you are sharing files with windows computers,(to protect windows, not ubuntu) it is not needed. but clamav is one you could use. it is in synaptic.

---

### Post by Kralizec on 2008-07-08
Avast! ([www.avast.com](www.avast.com)), which is free for Windows, has an equally free (though not open source) Linux version.

---

### Post by jimi_hendrix on 2008-07-08
ok...on my vista side (im dual booting) i use avg but i dont think they support linux

---

### Post by Dr Small on 2008-07-08
Why do you need an antivirus? You are running Linux.

---

### Post by jamesrfla on 2008-07-08
What about a firewall do you need one? I will be hosting a web server, mail server, and ssh server. If nobody knows my domain name exept my friends do I need a firewall or Virus protection?

---

### Post by AOZ on 2008-07-08
Generally, anti-virus is not needed in linux. I've never heard of an infected linux box. If you really want more protection firestarter will do the trick. But generally, you dont need to worry about that stuff now. 

P.S. be wary of free anti-virus software...you get what you pay for

---

### Post by sydbat on 2008-07-08
Firestarter (in the repos I think) is a GUI for the built in firewall.

(sort of OT) I don't mean to sound harsh, but whenever people ask about what anti-virus to use in Ubuntu (or Linux in general), why is there always at least one unhelpful post telling the OP that anti-virus is not needed in Linux (or something similar)? This is not helpful. Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install. Sure, it is up to Windows users to have proper anti-virus protection and practice proper blah, blah, blah, but I find it almost offensive when I see this kind of response to a serious question.

I apologize if I have offended anyone, but please refrain from posting unhelpful things like this for new Ubuntu/Gnu/Linux users.

---

### Post by damis648 on 2008-07-08
> **AOZ said:**
> P.S. be wary of free anti-virus software...you get what you pay for

I guess this is somewhat true, on the point of not having many definitions.

PS. Your avatar is awesome!

---

### Post by tjwoosta on 2008-07-08
the only time you eould ever need an antivirus in linux is if you share files with a windows computer 
(you dont want to be a carrier, and spread the viruses)

you can get avast antivirus for linux (only availible for 32bit )

or you can go with clamav (its in synaptic)


> P.S. be wary of free anti-virus software...you get what you pay for

thats actullay not entirely true

i have been using free avast antivirus on windows for the past year and it has never failed me yet 
(my windows machine runs very nice)

(it uses far less memory then the **bloated** antivirus programs that you have to pay for, like norton or mccaffe) yet it still has a very large and up to date virus database

id say its actually better

---

### Post by jamesrfla on 2008-07-08
jimi_hendrix you don't need to worry about virus protection or a firewall unless you are going to host something on the internet with your Ubuntu computer. As for me I don't know if I need the ant-virus and firewall or not because I will be using Ubuntu to host stuff on the web.

---

### Post by Dr Small on 2008-07-08
Yes, you will need a firewall, (you already have one installed by default called "iptables"). Just because no one knows your address does't mean you won't be found or get hit.

Virus protection? No. Unless you are going to be receiving files from Windows users that will be distributing to Windows users. You won't be infected, but they would be easily transfering the virus by the help of you.

---

### Post by AOZ on 2008-07-08
> **sydbat said:**
> Firestarter (in the repos I think) is a GUI for the built in firewall.

(sort of OT) I don't mean to sound harsh, but whenever people ask about what anti-virus to use in Ubuntu (or Linux in general), why is there always at least one unhelpful post telling the OP that anti-virus is not needed in Linux (or something similar)? This is not helpful. Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install. Sure, it is up to Windows users to have proper anti-virus protection and practice proper blah, blah, blah, but I find it almost offensive when I see this kind of response to a serious question.

I apologize if I have offended anyone, but please refrain from posting unhelpful things like this for new Ubuntu/Gnu/Linux users.

It may look like were just shutting him down or being unhelpful, but you could also look at it as i'm saving him time browsing the web for something that is relatively useless. The better way to do it is to just protect your windows partition with it's own anti-virus software

Plus i did recomend firstarter anyways:)

---

### Post by sydbat on 2008-07-08
Then the answer for you - jamesrfla - is yes..at least the firewall part. 

For anti-virus, I find that clamav tends to give false positives, but when you figure that part out, it should be pretty good.

---

### Post by AOZ on 2008-07-08
> **damis648 said:**
> PS. Your avatar is awesome!

thanks:)

---

### Post by Dr Small on 2008-07-08
> **sydbat said:**
> Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install.

I have never *ever* heard of anything like this. Let's be realistic here. Give the facts, steer the new user in the proper direction, and in turn save them time / frustration of setting up an Antivirus that's protection is really not needed.

---

### Post by jamesrfla on 2008-07-08
My Ubuntu computer is the file server and my Windows computers is the client. I run virus protection on all of my Windows computers so I don't think I will have to worry about virus protection on my Ubuntu desktop. I did try firestarter on my Ubuntu and it block all of my ssh and web server. Should I get another one or just stay with the one I got called iptables?

---

### Post by sydbat on 2008-07-08
> **AOZ said:**
> It may look like were just shutting him down or being unhelpful, but you could also look at it as i'm saving him time browsing the web for something that is relatively useless. The better way to do it is to just protect your windows partition with it's own anti-virus software

Plus i did recomend firstarter anyways:)Yes you did. Kudos. 

Again, I apologize, but I have seen these kinds of dismissal-type posts too often (not specifically from you) and find it frustrating when no other solution is subsequently given (which you have done...YAY!!). But I agree with the anti-virus on the windows partition and using that regularly...might be the better solution too!

---

### Post by phoenix_abhi on 2008-07-08
There are a lot of anti virus available, Clam AV is in synaptic also. Others are AVG (A tutorial available in this forum search for it) and Avast is also there. Use firesarter (firewall) for more confidence.

Nobody had ever heard about the virus in Linux, that does not meant that a virus never be out there.  why Clam Av is available in resources ? The developers themselves given open choice to the users.

Everyone wants to safe guard their system either way. Keeping an AV and a Firewall is not at all a bad solution

---

### Post by decoherence on 2008-07-08
> **Dr Small said:**
> I have never *ever* heard of anything like this. Let's be realistic here. Give the facts, steer the new user in the proper direction, and in turn save them time / frustration of setting up an Antivirus that's protection is really not needed.

One shouldn't assume you know what the user is doing. You say you've never ever heard of anything like that, I wonder how? If you work in a corporate environment and are exchanging files with Windows users then yes, you definitely need antivirus on your linux machine.

If you don't work in a corporate environment but still exchange files with Windows users... well, it's pretty rude to send someone an infected file, regardless of what operating system you're using.

So, where to draw the line is pretty clear. If you exchange data with Windows machines, you should have antivirus. How you can say you've never heard of this, I don't know.

ADD: hmmm. some of your previous posts seem contradictory. probably some misunderstanding somewhere down the line.

---

### Post by t0p on 2008-07-08
> **jamesrfla said:**
> What about a firewall do you need one? I will be hosting a web server, mail server, and ssh server. If nobody knows my domain name exept my friends do I need a firewall or Virus protection?

If you're running services like that, open to the internet, you definitely do not want to rely for security on the fact that "nobody knows [your] domain name except [your] friends".  That security model is known as "security through obscurity", which has been proven time and time again to not work.  I'd say a firewall is a necessity when you're running those servers from your box.

---

### Post by jamesrfla on 2008-07-08
Okay then I should get a firewall since the default one doesn't seem to work that well. What firewall do you recommend? I have already tried firestarter and it won't let me server services through the firewall.

---

### Post by t0p on 2008-07-08
> **sydbat said:**
> Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install.

Uhh, no they don't! Most people who ask about anti-virus for Ubuntu do so because they are used to Windows and assume all OSes are vulnerable to viral attack.

> **sydbat said:**
> 
I apologize if I have offended anyone, but please refrain from posting unhelpful things like this for new Ubuntu/Gnu/Linux users.

It's *not* unhelpful to tell these people that Ubuntu doesn't need anti-virus.  It may save them from wasted time and concern trying to track down something that is not needed,

---

### Post by t0p on 2008-07-08
> **jamesrfla said:**
> Okay then I should get a firewall since the default one doesn't seem to work that well. What firewall do you recommend? I have already tried firestarter and it won't let me server services through the firewall.

Firestarter isn't a firewall.  The firewall built into Ubuntu is **iptables**.  Firestarter is a gui tool for configuring iptables.  And I'm a bit confused by what you say that firestarter won't let you run servers.  You should be able to configure it to do anything you want.

**EDIT:** If you're having problems figuring out how to use firestarter, check out the documentation at [http://www.fs-security.com/docs/]("http://www.fs-security.com/docs/")

**ANOTHER EDIT:** Damn! A dead link!  Sorry!!!

---

### Post by Dr Small on 2008-07-08
> **decoherence said:**
> You say you've never ever heard of anything like that, I wonder how?
[...]
So, where to draw the line is pretty clear. If you exchange data with Windows machines, you should have antivirus. How you can say you've never heard of this, I don't know.


Apparently you missed the point I was trying to make, or simply forgot to read the quote that I had quoted. For added verification:
[quote=sydbat]Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install.[/quote]
That is what I have never heard of. Perhaps I am mistaken, but what I got out of it, was that the viruses on the linux partition are going over into their Windows partition and corrupting thing. THIS is what I have never heard of.

> ADD: hmmm. some of your previous posts seem contradictory. probably some misunderstanding somewhere down the line. 
Contradictions? where may I ask? I simply stated that if you are running Linux, then there is no real need for an Antivirus. Later I came back and said that if you are hosting files from Windows user TO windows users, then just to protect the Windows users, it would be courteous to have an Antivirus installed so the virus doesn't spread.

I see no contradictions there.

Dr Small

---

### Post by Frak on 2008-07-08
You don't need an anti-virus. Plain and Simple.

---

### Post by Jazzy_Jeff on 2008-07-08
> **sydbat said:**
> Firestarter (in the repos I think) is a GUI for the built in firewall.

(sort of OT) I don't mean to sound harsh, but whenever people ask about what anti-virus to use in Ubuntu (or Linux in general), why is there always at least one unhelpful post telling the OP that anti-virus is not needed in Linux (or something similar)? This is not helpful. Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install. Sure, it is up to Windows users to have proper anti-virus protection and practice proper blah, blah, blah, but I find it almost offensive when I see this kind of response to a serious question.

I apologize if I have offended anyone, but please refrain from posting unhelpful things like this for new Ubuntu/Gnu/Linux users.
How is this unhelpful. Some people don't know they don't need antivirus protection. I personally use online email only so antivirus would be a waste of time for me.

---

### Post by Dr Small on 2008-07-08
> **Frak said:**
> You don't need an anti-virus. Plain and Simple.
That's what I've been trying to say from the git-go. :)

---

### Post by jamesrfla on 2008-07-08
I installed firestarter and went through the setup wizard and then went to another computer and tried to access my web site and nothing came up. Then I disabled it and went back to the other computer and the web site cam up. Any ideas? I think I screwed the firewall configuration. :(

---

### Post by brian_p on 2008-07-08
> **decoherence said:**
> So, where to draw the line is pretty clear. If you exchange data with Windows machines, you should have antivirus.

There is no 'should' about it. Two possibilities exist:

1. The Windows machine runs antivirus software so there is no need for me to duplicate someone else's protective measures.

2. The Windows machine has no antivirus software installed. Now why should I take responsibility for protecting that machine?

---

### Post by Dr Small on 2008-07-08
> **jamesrfla said:**
> I installed firestarter and went through the setup wizard and then went to another computer and tried to access my web site and nothing came up. Then I disabled it and went back to the other computer and the web site cam up. Any ideas? I think I screwed the firewall configuration. :(
The setup wizard doesn't open any ports. You have to go to the Policy tab and allow port 80 as an inbound connection.

---

### Post by Frak on 2008-07-08
> **Dr Small said:**
> That's what I've been trying to say from the git-go. :)
We should have a new rule, an assumption really:

**New users are not finding an anti-virus to protect their Windows Partitions. Not matter how much you would like to help them with that, I have a thought in the back of my head that they *Do Not Care*. Just tell them, at least for the time being, that they Do Not need an anti-virus.**

Very simple really.

---

### Post by brian_p on 2008-07-08
> **jamesrfla said:**
> I installed firestarter and went through the setup wizard and then went to another computer and tried to access my web site and nothing came up. Then I disabled it and went back to the other computer and the web site cam up. Any ideas? I think I screwed the firewall configuration. :(

You have used firestarter to block the ports you are offering services on. But you want those services to be available. You might conclude that setting up a firewall is not useful for you.

---

### Post by sydbat on 2008-07-08
I apologize. I did not mean this to become any type of flame war.

To clarify my position (while I do agree with all the "no need for anti-virus" posts), I come from a Windows background. Most people starting out with Gnu/Linux/Ubuntu are the same. YES, we do have a "viruses are going to kill my computer" mindset and want to make sure this doesn't happen (to us or anyone else).

When I stated that > Most OP's ask because they are dual booting and/or want to be good citizens and do not want Windows viruses going beyond their machine/into their Windows install.I meant for transferring files, forwarding emails, etc.

My main concern, in my original post, was the dismissal factor. Sure, GNU/Linux does not really need any type of anti-virus solution unless it is a server of some kind. Telling the new Ubuntu user this as an explanation to "You don't need anti-virus in Linux" is where I was going. Simply saying no anti-virus needed is not helpful. Those of us new to GNU/Linux need to be told these things.

Again, please accept my apology for this misunderstanding.

---

### Post by Paqman on 2008-07-08
It's probably worth mentioning that the antivirus clients available for Linux scan for Windows viruses. It's up to the user to decide how much use that is to them. Personally, I don't see any point in installing one on a desktop system.

There _is_ a virus threat to Linux desktops, but it's taken care of through regular updates and the way the OS is designed, not by a separate layer of software like it is with Windows.

---

### Post by Frak on 2008-07-08
> **Paqman said:**
> It's probably worth mentioning that the antivirus clients available for Linux scan for Windows viruses. It's up to the user to decide how much use that is to them. Personally, I don't see any point in installing one on a desktop system.

There _is_ a virus threat to Linux desktops, but it's taken care of through regular updates and the way the OS is designed, not by a separate layer of software like it is with Windows.
There were very few Linux virii out in the wild, and they were eliminated years ago. The only ones now are grown in labs as a proof-of-concept.

---

### Post by SunnyRabbiera on 2008-07-08
> **jamesrfla said:**
> What about a firewall do you need one? I will be hosting a web server, mail server, and ssh server. If nobody knows my domain name exept my friends do I need a firewall or Virus protection?

If you are hosting a web server then a anti virus client will come in handy to protect windows users from stuff you might per chance pick up along the way.
Clam is a great client, it has a frontend called klam that is also in the repositories.

---

### Post by decoherence on 2008-07-08
> **Dr Small said:**
> That is what I have never heard of. Perhaps I am mistaken, but what I got out of it, was that the viruses on the linux partition are going over into their Windows partition and corrupting thing. THIS is what I have never heard of.

People share files between their Linux and Windows partitions. If I downloaded a questionable file with Linux, I would definitely want to run antivirus on it before using it in Windows.

The poster may have made it sound like files were spontaneously copying from one partition to another, but that wasn't how I read it.

> Contradictions? where may I ask?

None. T'was a misunderstanding after all :)

---

### Post by jamesrfla on 2008-07-08
I got firestarter and it went to another computer and it works. Although it is slower to bring up the web page now.

---

### Post by Frak on 2008-07-08
> **jamesrfla said:**
> I got firestarter and it went to another computer and it works. Although it is slower to bring up the web page now.
Meet the filtering system at work.

---

### Post by saratchandra on 2008-07-08
> **AOZ said:**
> Generally, anti-virus is not needed in linux. I've never heard of an infected linux box. If you really want more protection firestarter will do the trick. But generally, you dont need to worry about that stuff now. 

P.S. be wary of free anti-virus software...**you get what you pay for**

I paid nothing for ubuntu and its awesome.

---

### Post by Paqman on 2008-07-08
> **Frak said:**
> There were very few Linux virii out in the wild, and they were eliminated years ago. The only ones now are grown in labs as a proof-of-concept.

I disagree.

[Wikipedia on Linux Malware](http://en.wikipedia.org/wiki/Linux_Viruses)

The article references this news piece from 2006: [Linux Malware on the Rise](http://www.internetnews.com/dev-news/article.php/3601946).

I would agree that if you have an up-to-date system you are patched for all known Linux malware, but the idea that the threat is only theoretical is not correct.

---

### Post by Frak on 2008-07-08
> **Paqman said:**
> I disagree.

[Wikipedia on Linux Malware](http://en.wikipedia.org/wiki/Linux_Viruses)

The article references this news piece from 2006: [Linux Malware on the Rise](http://www.internetnews.com/dev-news/article.php/3601946).

I would agree that if you have an up-to-date system you are patched for all known Linux malware, but the idea that the threat is only theoretical is not correct.
Those are minor virii, nothing to be afraid of with an up-to-date system.

Most security holes are patched within a day.

---

### Post by jamesrfla on 2008-07-08
> **SunnyRabbiera said:**
> If you are hosting a web server then a anti virus client will come in handy to protect windows users from stuff you might per chance pick up along the way.
Clam is a great client, it has a frontend called klam that is also in the repositories.
So I need a firewall and anti-virus protection for my server??

---

### Post by brian_p on 2008-07-08
> **Paqman said:**
> I disagree.

[Wikipedia on Linux Malware](http://en.wikipedia.org/wiki/Linux_Viruses)

The article references this news piece from 2006: [Linux Malware on the Rise](http://www.internetnews.com/dev-news/article.php/3601946).

I would agree that if you have an up-to-date system you are patched for all known Linux malware, but the idea that the threat is only theoretical is not correct.

That list of viruses and trojans for Linux at Wikipedia: are there any there which do not need root assistance to access system files? I thought not. So no danger from them!

Worms are a threat because they attack services. Hence the need for keeping up to date with software.

---

### Post by Frak on 2008-07-08
> **jamesrfla said:**
> So I need a firewall and anti-virus protection for my server??
Firewall is a good recommendation to have.

Anti-Virus, not so much. That's more of your choice than anything else.

---

### Post by RequinB4 on 2008-07-08
> **jamesrfla said:**
> So I need a firewall and anti-virus protection for my server??

Firewall - Recommended, even if you don't need it, because you never know when you might accidently open a port...

A/v - Depends on your server.  If it's a samba or mail server, you SHOULD have antivirus because you actively share files with windows users.  If it's more of a personal ftp repository for files you want to access everywhere, it's still helpful but not as important.

---

### Post by brian_p on 2008-07-08
> **jamesrfla said:**
> So I need a firewall . . . 

You first used firestarter to block all incoming ports. Not a single one of these ports were open in the first place apart from 80, which you want to be open. Firestarter closed port 80. So then you had to open port 80 in the firewall. In other words, you are back to where you started.

Now you work out for yourself whether you need a firewall.

---

### Post by SunnyRabbiera on 2008-07-08
> **jamesrfla said:**
> So I need a firewall and anti-virus protection for my server??

Well it can help by taking precautions, even though your linux machine will be safe from viruses even if they do get in your windows usi9ng visitors to your web server will get infected...
Using a anti virus and firewall is a good idea on a web server.

---

### Post by t0p on 2008-07-08
> **AOZ said:**
> be wary of free anti-virus software...you get what you pay for

I can't believe you wrote that! Anti-virus is like any other software - some is really expensive and crap, some is free and wonderful.  Most of the people in this forum run Ubuntu, which is generally free and is generally great. There's no reason why anti-virus software shouldn't also follow this trend.

---

### Post by t0p on 2008-07-08
> **brian_p said:**
> You first used firestarter to block all incoming ports. Not a single one of these ports were open in the first place apart from 80, which you want to be open.

Where'd you get the idea all his incoming ports were closed? How do you think he's running a web server, mail server and ssh server with all ports closed?!

---

### Post by jamesrfla on 2008-07-08
> **t0p said:**
> Where'd you get the idea all his incoming ports were closed? How do you think he's running a web server, mail server and ssh server with all ports closed?!

Also remote desktop, samba, and webmin to add to the list. Also dose firestarter or a anti-virus protection startup when I boot or take up any ram when not using it.

---

### Post by brian_p on 2008-07-08
> **t0p said:**
> Where'd you get the idea all his incoming ports were closed? How do you think he's running a web server, mail server and ssh server with all ports closed?!

You missed the essential point but I'll restructure the argument anyway.

You first used firestarter to block all incoming ports. Not a single one of these ports were open in the first place apart from a, b, c, d and e, which you want to be open. Firestarter closed ports a, b, c, d and e. So then you had to open ports a, b, c, d and e in the firewall. In other words, you are back to where you started.

And in addition: if a service is bound to localhost only (an MTA and samba are examples of services which often are) a firewall is of no consequence.

---

### Post by jimi_hendrix on 2008-07-08
> **tjwoosta said:**
> the only time you eould ever need an antivirus in linux is if you share files with a windows computer 
(you dont want to be a carrier, and spread the viruses)

you can get avast antivirus for linux (only availible for 32bit )

or you can go with clamav (its in synaptic)




thats actullay not entirely true

i have been using free avast antivirus on windows for the past year and it has never failed me yet 
(my windows machine runs very nice)



(it uses far less memory then the **bloated** antivirus programs that you have to pay for, like norton or mccaffe) yet it still has a very large and up to date virus database

id say its actually better

i went with clamav...just how do i know if its working?

---

### Post by Frak on 2008-07-08
> **jimi_hendrix said:**
> i went with clamav...just how do i know if its working?
Download a test virus (virus that doesn't do anything) and run a scan on it.

---

### Post by t0p on 2008-07-08
> **brian_p said:**
> You missed the essential point but I'll restructure the argument anyway.

You first used firestarter to block all incoming ports. Not a single one of these ports were open in the first place apart from a, b, c, d and e, which you want to be open. Firestarter closed ports a, b, c, d and e. So then you had to open ports a, b, c, d and e in the firewall. In other words, you are back to where you started.

And in addition: if a service is bound to localhost only (an MTA and samba are examples of services which often are) a firewall is of no consequence.

A firewall is more versatile than just deciding to open or close certain ports - after all, as brian_p points out, you don't need a firewall to do that!

Let's imagine that jamesrfla discovers a large number of suspicious failed logins have been made on his ssh server.  He can see which ip address(es) the attempts were made from, then he can configure the firewall to block those addresses from logging in.

Or, he can tell firestarter to allow ssh logins from a few certain ip addresses, which he knows belong to authorized users.

There are many such situations that a firewall can deal with.  It's a handy thing to have if your computer is facing the internet with open ports.

---

### Post by jimi_hendrix on 2008-07-08
how do i run a scan...i see no icon for it

---

### Post by jimi_hendrix on 2008-07-08
> **t0p said:**
> A firewall is more versatile than just deciding to open or close certain ports - after all, as brian_p points out, you don't need a firewall to do that!

Let's imagine that jamesrfla discovers a large number of suspicious failed logins have been made on his ssh server.  He can see which ip address(es) the attempts were made from, then he can configure the firewall to block those addresses from logging in.

Or, he can tell firestarter to allow ssh logins from a few certain ip addresses, which he knows belong to authorized users.

There are many such situations that a firewall can deal with.  It's a handy thing to have if your computer is facing the internet with open ports.


is there a firewall in synaptic i can get?

---

### Post by t0p on 2008-07-08
> **jimi_hendrix said:**
> is there a firewall in synaptic i can get?

Yes! There's **Firestarter**.

---

### Post by jimi_hendrix on 2008-07-08
ok and 1 more thing...whats a ssh?

---

### Post by tjwoosta on 2008-07-08
> ok and 1 more thing...whats a ssh?
Secure shell. A program that allows a user to log into another computer remotely across the Internet, while maintaining complete security.


look here for more info
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by lisati on 2008-07-08
> **jimi_hendrix said:**
> ok...on my vista side (im dual booting) i use avg but i dont think they support linux


There is a free version, see [http://free.avg.com/ww.download?prd=afl](http://free.avg.com/ww.download?prd=afl)
**Importan**t: in order to do the updates using its GUI mode, you need to add your user to the 'avg' group. Although this is in the documentation, who reads it?

---

### Post by brian_p on 2008-07-08
> **t0p said:**
> A firewall is more versatile than just deciding to open or close certain ports - after all, as brian_p points out, you don't need a firewall to do that!

brian_p believes running a service opens a port. He also believes first denying packets and then allowing packets to the port with a firewall and then running the service comes under the heading of nonsense.

> Let's imagine that jamesrfla discovers a large number of suspicious failed logins have been made on his ssh server.  He can see which ip address(es) the attempts were made from, then he can configure the firewall to block those addresses from logging in.

jamesrfla will read up on ssh and learn it provides secure communication and nobody but nobody can log in without authentication, rendering failed attempts mere annoyances.

> Or, he can tell firestarter to allow ssh logins from a few certain ip addresses, which he knows belong to authorized users.

He will also have read the sshd_config manual and found he can easily do that directly with ssh.

---

### Post by jimi_hendrix on 2008-07-08
and how do i know if my antivirus/firewall is up?

---

### Post by jamesrfla on 2008-07-08
Okay I don't know what is causing this but I am just going to do a fresh install of Ubuntu. My questions is the firewall installed when I install Ubuntu. When I install ssh server dose the firewall automatically open the port for ssh and block everything else?

---

### Post by k3lt01 on 2008-07-09
> **AOZ said:**
> P.S. be wary of free anti-virus software...you get what you pay for Considering we are in a forum devoted to FREE software the flawed logic in that statement is amazing.

---

### Post by Paqman on 2008-07-09
> **jamesrfla said:**
> Okay I don't know what is causing this but I am just going to do a fresh install of Ubuntu. My questions is the firewall installed when I install Ubuntu. When I install ssh server dose the firewall automatically open the port for ssh and block everything else?

A port is only a vulnerability if it has a service listening on it. So a default install that has no server-type software installed is completely locked down. Installing a service that listens on a specific port such as ssh will create a (theoretical) vulnerabilty there. It's then up to the software that listens on that port to be secure.

The crucial difference between Linux and Windows here is that by default Windows is listening on all sorts of weird ports, whereas Linux (or at the very least, Ubuntu) starts off completely secure.

---

### Post by t0p on 2008-07-09
So, **brian_p**, is it your opinion that no one needs a firewall?  That appears to be what you're suggesting.

---

### Post by mcduck on 2008-07-09
> **jamesrfla said:**
> Okay I don't know what is causing this but I am just going to do a fresh install of Ubuntu. My questions is the firewall installed when I install Ubuntu. When I install ssh server dose the firewall automatically open the port for ssh and block everything else?

There is no firewall installed when ypou install Ubuntu. (Well, the kernel has everything that a firewall needs to work, but without anything actually providing it ruels to work with I wouldn't call it a firewall). All ports are open by default so there is no need to open any ports for ssh. No connections are blocked, as there is no active firewall, taht would block them, and blocking connections with a firewall is absolutely waste of time if there is no service running that would respond to incoming connections.

BTW, somebody here mentioned being awary of free anti-virus apps. That's nonsense, many free antivirus apps have beaten  most of the expensive commercial ones in all tests. High price doesn't make things better. (eh, knowing that we are uing a free OS that doesn't even need that free/commercial antivirus app should prove my point ;))

---

### Post by btdown on 2008-07-09
eh don't bother scanning windows files/partitions with linux Av programs..I was unfortunate enough to download two separate files with different viruses on my windows machine.
After I was finished disinfecting, I downloaded those infected files again to my linux machine and scanned those files with fully updated versions of:

ClamAV
F-Prot
Avira

Not one of them saw either virus....(xpantivirus 2008 and virtumonde were the viruses in case anyone was wondering..)

I suspect if I has installed AVG, the the results would have been the same....

---

