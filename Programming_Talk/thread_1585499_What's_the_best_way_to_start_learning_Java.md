---
title: "What's the best way to start learning Java"
date: 2010-09-30
forum: Programming Talk
---

### Post by ki4jgt on 2010-09-30
I want to write a web browser with specific feature, really custom and all. I am new to Java and think it will take me about three years to achieve this goal. Can anyone tell me where to start. I don't even have any software installed yet, b/c all the information I can find online references 8.04 or releases before that.

---

### Post by dv3500ea on 2010-09-30
Install the package: [default-jdk]("apt:default-jdk").
You can then use the ```
javac
``` command to compile to bytecode and the ```
java
``` command to run the compiled code.

You can write programs in Gedit, the default text editor. Have a look [here]("http://ubuntuforums.org/showpost.php?p=1997993") for java resources.

Is there a specific reason you want to use java? I wouldn't really reccommend it if you haven't programmed before. For beginner programming (and actually for most other programming), [Ruby]("http://www.ruby-lang.org/en/") or [Python]("http://www.python.org/") would be a better choice. Whatever you choose, be prepared that developing a web browser is a very big task.

---

### Post by lespaul_rentals on 2010-09-30
You should try searching Google. A quick search would turn up software that would be of help, such as IDEs, books that could be of reference, example source code, and much more.

It shouldn't matter if search results are intended for 8.04. Software still runs the same, and many applications around at that time are still in the repositories.

---

### Post by algnod on 2010-09-30
Look at:

[http://download.oracle.com/javase/tutorial/](http://download.oracle.com/javase/tutorial/)

and start with:

[http://download.oracle.com/javase/tutorial/getStarted/index.html](http://download.oracle.com/javase/tutorial/getStarted/index.html)

the java tutorial is very well written and you will find everything you need to get you started.

As for tools a text editor and commandline javac is a good idea initially. As you advance IDEs are a great help and either eclipse or netbeans will do the job just fine.

---

### Post by ki4jgt on 2010-09-30
Thanks, I work quite well with BASIC and decided the Java would help me because it's interplatforum. I know python is, but I hate it. It confuses me, because I find myself trying to write in BASIC while I'm using Python. I've seen a webbrowser in BASIC, which ran a lot like Firefox. Once I looked at the source code behind it, I flipped.

Yeah, well I just don't want to have outdated information. That would stink.

and Thanks

---

### Post by lespaul_rentals on 2010-09-30
> **ki4jgt said:**
> Thanks, I work quite well with BASIC and decided the Java would help me because it's interplatforum. I know python is, but I hate it. It confuses me, because I find myself trying to write in BASIC while I'm using Python. I've seen a webbrowser in BASIC, which ran a lot like Firefox. Once I looked at the source code behind it, I flipped.

Yeah, well I just don't want to have outdated information. That would stink.

and Thanks

Theoretically, many languages are cross-platform. Java is based on the cross-platform runtime environment, which allows the code to function exactly the same on every platform, regardless of hardware, operating system, etc.

Good luck. Pick up an O'Reilly book -- they're great.

---

### Post by smartbei on 2010-09-30
If you a decent background in programming, I recommend [http://download.oracle.com/javase/tutorial/](http://download.oracle.com/javase/tutorial/).

Also, I highly doubt that what you want to do is write a web browser from scratch. What is the feature you want to add? Perhaps you could achieve what you want with a plugin to one of the open-source browsers?

---

### Post by ki4jgt on 2010-09-30
This is how I want to build it:

[http://forum.codecall.net/general-programming/32018-network-encryption-programing-new-post.html](http://forum.codecall.net/general-programming/32018-network-encryption-programing-new-post.html)

---

### Post by ki4jgt on 2010-09-30
There is no web browser in the world designed like that LOL. Most of the people I've talked to about it say it's impossible

You get a better idea if you start on the first page LOL

---

### Post by dv3500ea on 2010-09-30
You posted:
```

The Internet could be rewritten:

- Every user could potentially get an unlimited connection
- Every Server (Website) could have an unlimited connection to everyone using it!
- Every server (Website) could have the ability to experience 100% uptime
- All communications could be completely confidential between the two individuals talking and no one else.
- All using the current set of protocols we are currently using (TCP/IP)
- No one could monitor your communications
- HTML could be made simpler and still maintain it's (complete) functionality
- The Internet could be FREE (No Price)
- While maintaining proper authentication protocols (people would still be able to be traced for illegal stuff)
- The only hardware required would be a MODERN computer (Windows Vista/7, Linix, Apple)

And we currently have the technology!

Now, what if I told you, I could prove it?

```
This *is* impossible due to physical limits of hardware. Also, most of what you listed can not be changed by a web browser.

---

### Post by ki4jgt on 2010-09-30
Read further into the forum. I'm putting other services into the browser, so it's not just a browser

---

### Post by lespaul_rentals on 2010-10-03
I'm sorry, man, but this is not feasible. Is it possible? Yes. But feasible? No.

[QUOTE=ki4jgt]- Every user could potentially get an unlimited connection[/QUOTE]

Do you mean unlimited in transfer speed or monthly bandwidth? If the former, you will need to find a way to distribute the fastest method of connection to every single person (and that's only the beginning). If the latter, you will need to completely bypass ISPs and throttling methods.


[QUOTE=ki4jgt]- Every Server (Website) could have an unlimited connection to everyone using it![/QUOTE]

That's really not possible. There are supercomputers with dozens upon dozens of NICs clustered in huge server farms that can handle millions of connections, but even then, there's a limit that can be reached. Must every person wishing to host a website buy a host of this magnitude in order to comply with the standards you wish to set?

[QUOTE=ki4jgt]- Every server (Website) could have the ability to experience 100% uptime[/QUOTE]

We already have the "ability." Things like power outages, storms, floods, and fires make up a major hurdle. Many web hosts promise 99.9% uptime, and most keep their promises. There isn't a protocol that could be invented, or a method of serving, that could guarantee 100% uptime.

[QUOTE=ki4jgt]- All communications could be completely confidential between the two individuals talking and no one else.[/QUOTE]

That's already been done.

[QUOTE=ki4jgt]- All using the current set of protocols we are currently using (TCP/IP)[/QUOTE]

Right.

[QUOTE=ki4jgt]- No one could monitor your communications[/QUOTE]

So, do you propose running an individual line to the server for each connection? How will communications not pass through a central hub at one point or another?

[QUOTE=ki4jgt]- HTML could be made simpler and still maintain it's (complete) functionality[/QUOTE]

It's hard to get much simpler than HTML.

[QUOTE=ki4jgt]- The Internet could be FREE (No Price)[/QUOTE]

Who would lay the cable? Who would project the satellite signals? Who would maintain the DSLAMs and other such components?

[QUOTE=ki4jgt]- While maintaining proper authentication protocols (people would still be able to be traced for illegal stuff)[/QUOTE]

But, wait...I thought all communication would also be encrypted and impossible to intercept, meaning the bad guys could *not* be traced. And who is going to maintain the "proper authentication protocols"?

[QUOTE=ki4jgt]- The only hardware required would be a MODERN computer (Windows Vista/7, Linix, Apple)[/QUOTE]

[QUOTE=ki4jgt]And we currently have the technology![/QUOTE]

Yes, we do. However, the technology is far too expensive for the average person to afford, and you would have to convince the entire world to move your direction.

[QUOTE=ki4jgt]Now, what if I told you, I could prove it?[/QUOTE]

All you've proven at this point is that you have a very lacking knowledge of the network layers and protocols, in addition to a lack of understanding regarding the insane amount of overhaul that would be needed to implement such a thing.

I myself have contemplated an Internet such as this, and never in my most illogical fantasy did the packets travel to their destination in the form of archaic protocols such as HTTP. To go through with such a plan, one would need to go back to the drawing board and change everything from the way network cards send data to the way servers receive it...not to mention the changes that would have to be made between all that!

That you think this is feasible indicates you need to go back to square one and think this through. Read up on your networks (everything from infrastructure to protocols) and you will see what I mean when I say what I say.

I appreciate your ambition, but use your exuberance to further your understanding of computers and then focus it on projects that are less idealistic and more practical.

[QUOTE=ki4jgt]I've gotten things about computers without even having to be told, so much so that I've amazed teachers at school and other computer professionals.[/QUOTE]

Don't attempt to flaunt your intuition, especially after it has failed you in this regard.

---

### Post by ki4jgt on 2010-10-03
Keep reading. Make sure to read the whole thing, I explain in detail later.
There is no line to be laid.

---

