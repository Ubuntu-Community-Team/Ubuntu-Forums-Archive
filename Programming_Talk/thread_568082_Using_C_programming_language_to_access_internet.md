---
title: "Using C programming language to access internet"
date: 2007-10-05
forum: Programming Talk
---

### Post by NuNn DaDdY on 2007-10-05
I'm currently beginning a project in which the task is to create a terminal based rss reader using C.  I was wondering where I would find documentation on how to use C to have online access. Thanks.

Locked due to being off topic.  If you wish to help the OP with a solution, then [click here]("http://ubuntuforums.org/showthread.php?t=571362").

---

### Post by pmasiar on 2007-10-05
Is using C negotiable or hard requirement?

I bet you can do it 20 times faster (in development time) and simpler in Python.

Of course if you prefer C for that, go ahead!

---

### Post by LaRoza on 2007-10-05
Socket programming, [http://www.uwo.ca/its/doc/courses/notes/socket/](http://www.uwo.ca/its/doc/courses/notes/socket/)

For Python, it would be much easier using httplib [http://docs.python.org/lib/module-httplib.html](http://docs.python.org/lib/module-httplib.html)

---

### Post by MicahCarrick on 2007-10-05
It'd be pretty easy to use curl as well. You could even run wget into a variable or local file and then parse the contents using something like the XML reader that comes with GLib or libxml.

---

### Post by Wybiral on 2007-10-05
[http://curl.haxx.se/libcurl/](http://curl.haxx.se/libcurl/)

---

### Post by dwhitney67 on 2007-10-06
> **pmasiar said:**
> Is using C negotiable or hard requirement?

I bet you can do it 20 times faster (in development time) and simpler in Python.

Of course if you prefer C for that, go ahead!

It is annoying reading that python can do this, python can do that.  Not everyone is privy to using python.  If someone says that they need help in C ,  C++ or even Swahili, then please dispense with the useless comments about python.

Python maybe great in one's basement or in some puny little company, but in the real world it is not used that widely.  Many jobs require C, C++, and/or Java experience.  Python is a small fish that someday may see the light, but for now it is not used that widely... and probably never will.

I am not trying to say python is inferior, I am just saying that it is not the "golden nugget" that will put plentiful food on one's table, at least not today.

I personally wish I had an answer for the OP, but when I think of RSS, the first thing that comes to mind is XML.  The C language is very basic and there is little support for modern constructs such as XML, much less RSS.

---

### Post by slavik on 2007-10-06
some code to get your started. this goes and fetches the main page from google and prints it to terminal (along with the response header)

```

/*
 *      wget_sortof.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail.com>
 *
 *      This program is free software; you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation; either version 3 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program; if not, write to the Free Software
 *      Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
 */

/* get the main page from google.com */

#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>

int main(int argc, char** argv)
{
	struct sockaddr_in servaddr;
	struct hostent *hp;
	int sock_id;
	char message[1024*1024];
	char msglen;
	char request[] = "GET /index.html HTTP/1.0\n"
	"From: slava!!!\nUser-Agent: wget_sortof by slava\n\n";
	
	//Get a socket	
	if((sock_id = socket(AF_INET, SOCK_STREAM, 0)) == -1) {
		fprintf(stderr,"Couldn't get a socket.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got a socket.\n");
	}
	
	//book uses bzero which my man pages say is deprecated
	//the man page said to use memset instead. :-)
	memset(&servaddr,0,sizeof(servaddr));
	
	//get address for google.com
	if((hp = gethostbyname("google.com")) == NULL) {
		fprintf(stderr,"Couldn't get an address.\n"); exit(EXIT_FAILURE);
	}
	else {
		fprintf(stderr,"Got an address.\n");
	}
	
	//bcopy is deprecated also, using memcpy instead
	memcpy((char *)&servaddr.sin_addr.s_addr, (char *)hp->h_addr, hp->h_length);
	
	//fill int port number and type
	servaddr.sin_port = htons(80);
	servaddr.sin_family = AF_INET;
	
	//make the connection
	if(connect(sock_id, (struct sockaddr *)&servaddr, sizeof(servaddr)) != 0) {
		fprintf(stderr, "Couldn't connect.\n");
	}
	else {
		fprintf(stderr,"Got a connection!!!\n");
	}
	
	//NOW THE HTTP PART!!!
	
	//send the request
	write(sock_id,request,strlen(request));
	
	//read the response
	msglen = read(sock_id,message,1024*1024);
	
	//print the reasponse
	fprintf(stdout,"%s",message);
	
	return 0;
}
```

---

### Post by Wybiral on 2007-10-06
Reading the feed is pretty trivial, especially if you use a good library (such as libCurl).

```

// gcc source.c -lcurl

#include <stdlib.h>
#include <curl/curl.h>

void download_feed(FILE *dst, const char *src)
{
    CURL *handle = curl_easy_init();
    curl_easy_setopt(handle, CURLOPT_URL, src);
    curl_easy_setopt(handle, CURLOPT_WRITEDATA, dst);
    curl_easy_perform(handle);
}

int main()
{
    FILE *feed = fopen("feed.xml", "rw");
    download_feed(feed, "http://feeds.feedburner.com/ICanHasCheezburger");
    fclose(feed);
    return 0;
}

```

Parsing it will be the fun part. Does this have to be a generic feed reader that can reed any rss/atom feeds? Or just for one specific feed that you can tailor to it's format?

String handling and parsing are a pain in C, if it's possible to avoid C, using a higher level language would help.

Here's an example of a simple feed reader in Python (using the feedparser module which you can grab from synaptic) that writes the contents to an HTML file. You could easily modify this to write the contents to the terminal.

```

import feedparser

def title(feed):
    if entry.has_key("title"):
        return entry["title"]
    else:
        return "[Untitled]"

def content(feed):
    if entry.has_key("content"):
        out = ""
        for content in entry.content:
            out += content.value
        return out
    elif entry.has_key("desciption"):
        return entry.description
    return "[Empty]"

feed = feedparser.parse("http://feeds.feedburner.com/ICanHasCheezburger")
out = "<html><body><center>"
for entry in feed['entries']:
    out += "<b>%s</b><br/>%s<hr/><br/>" % (title(feed), content(feed))
out += "</center></body></html>"
open("feed.html", "w").write(out.encode('ascii', 'ignore'))

```

---

### Post by cwaldbieser on 2007-10-07
It seems reasonable to suggest alternative approaches to a programming problem on a general programming forum.  Sometimes there will be a particular tool requirement, sometimes there is not.  It is not always clear from the information provided that such a requirement exists.

When I read the OP's request, it seems like he intends on using C, but there could be many reasons for this, such as:
+ His project requires using C.
+ He hasn't had much exposure to languages other than C.
+ He is under the impression that this is the only way to accomplish the task.
+ C is his favorite letter of the alphabet.

There seems to be little harm in suggesting that such tasks are more easily accomplished with shell tools or scripting languages.  If the OP was unaware, he might benefit from the advice.  He is always free to decline the advice and use his own best judgement.

---

### Post by Wybiral on 2007-10-07
> **dwhitney67 said:**
> Python maybe great in one's basement or in some puny little company, but in the real world it is not used that widely.

So Google (it's used in Google Maps, GMail, and YouTube) is a puny little company? NASA is puny? Ubuntu also [prefers developers to use Python]("http://www.ubuntu.com/community/developerzone/bounties#head-41c34de429ab5a0dd9541ab19d884a40a2e89f9e") over other language. I realize the OP was interested in a C solution, but there is no harm letting them know that C is the wrong tool for the job. No one got hurt, it's just friendly advice.

---

### Post by Mathiasdm on 2007-10-07
> **Wybiral said:**
> So Google (it's used in Google Maps, GMail, and YouTube) is a puny little company? NASA is puny? Ubuntu also [prefers developers to use Python]("http://www.ubuntu.com/community/developerzone/bounties#head-41c34de429ab5a0dd9541ab19d884a40a2e89f9e") over other language. I realize the OP was interested in a C solution, but there is no harm letting them know that C is the wrong tool for the job. No one got hurt, it's just friendly advice.

Who says C is the wrong tool for the job? It might be more complicated in this case, but that doesn't mean it's a bad choice.

Anyways, the OP explicitly mentions C both in the title and in his post "the task is to create a terminal based rss reader using C.".

All this 'use Python' stuff is really annoying. Yes, it's a good language, and yes, I'm sure it's used in lots of companies, but keep the 'use Python' posts to the "what programming language should I use?" posts, instead of filling the entire forum with it.

---

### Post by LaRoza on 2007-10-07
> **Mathiasdm said:**
> 
All this 'use Python' stuff is really annoying. Yes, it's a good language, and yes, I'm sure it's used in lots of companies, but keep the 'use Python' posts to the "what programming language should I use?" posts, instead of filling the entire forum with it.

I (somewhat) agree. The only exception to this is that Python is really, really good at many things, and makes complicated tasks much easier, and also is good for quickly working on a program, then rewriting it in C or some other language after.

I do think the OP specifically wanted C information, and did get that, so there is no loss, although the original Python post was quite random, and didn't address the issue.

---

### Post by pmasiar on 2007-10-07
My original post ended with: "Of course if you prefer C for that, go ahead!"

Can I make any more obvious, that if OP prefers C, I have no problem if s/he uses C for that? 

In opinions of many, Python might be better choice - better tool for the job, and OP is apparently not aware about that fact. Why are so many of you upset about the fact that language what OP initially picked might be not the best choice?

Of course every one of us have preferences, and would like influence other people to have same preferences, to guarantee growth of community of each language. So you want me to lie to OP about C is being good choice (which is not)  just to make sure that C community grows?

I have no problems with C, I used it when it was best available choice for some project back them when it was. :-) I STILL would advice to everyone to learn C, but as SECOND LANGUAGE, because I strongly believe that for most tasks (including the one OP is facing), Python is the best. Do you want me to put bias disclosure in my sig, so it is 3 pages long? I do it, when you do it. :-)

---

### Post by LaRoza on 2007-10-07
> **pmasiar said:**
> 
 Why are so many of you upset about the fact that language what OP initially picked might be not the best choice?

Do you want me to put bias disclosure in my sig, so it is 3 pages long? I do it, when you do it. :-)

I agree, I would not use C for the task mentioned, and would, by random coincidence, use Python, but I feel that a post to a query should at least address the question, which explicity stated C. The response Re: Using C programming language to access internet. "Of course if you prefer C for that, go ahead!", did not help the OP at all.

The sigs are restricted to four lines, I believe. Besides, everyone knows Python is one of the best languages for a variety of tasks, so a disclosure is not needed.

---

### Post by pmasiar on 2007-10-08
> **LaRoza said:**
>  I feel that a post to a query should at least address the question, which explicity stated C. The response Re: Using C programming language to access internet. "Of course if you prefer C for that, go ahead!", did not help the OP at all.

...and my first line was: "Is using C negotiable or hard requirement?" Do you think it was not clear enough? :-)

... and we still did not get any answer to OP for basic questions, but instead of waiting (or suggesting other smart questions to ask), prefer to bash each other about our preferences. I at least disclosed my bias, some ppl try to sneak their own bias as Holy Truth(tm) :-)

---

### Post by Wybiral on 2007-10-08
> **Mathiasdm said:**
> Who says C is the wrong tool for the job? It might be more complicated in this case, but that doesn't mean it's a bad choice.

Anyways, the OP explicitly mentions C both in the title and in his post "the task is to create a terminal based rss reader using C.".

All this 'use Python' stuff is really annoying. Yes, it's a good language, and yes, I'm sure it's used in lots of companies, but keep the 'use Python' posts to the "what programming language should I use?" posts, instead of filling the entire forum with it.

C is a great language for low level stuff and writing libraries, but it's absolutely terrible for string manipulation and parsing. There are much better languages, languages designed for stuff like this (not just Python), hence C is clearly the wrong tool for this job. Sure you can hammer nails in with a screwdriver if you try hard enough, but wouldn't a hammer work better?

If the OP explains why they have to use C, then I doubt anyone would suggest another language. As it stands, maybe they were unaware that it was a bad language for this kind of thing and they would actually benefit from someone suggesting a better tool for the job. In the end, nobody got hurt. In fact, the thread wouldn't even get flamed if you didn't play forum police and try to start wars over it. The OP would just ignore it or explain why they can't use another language and it would have been dropped.

If any of the moderators feel like I've stepped over the line, they will let me know and I'll be more careful next time. But stop trying to do their job for them.

---

### Post by Mathiasdm on 2007-10-08
> **Wybiral said:**
> 
If the OP explains why they have to use C, then I doubt anyone would suggest another language. As it stands, maybe they were unaware that it was a bad language for this kind of thing and they would actually benefit from someone suggesting a better tool for the job. In the end, nobody got hurt. In fact, the thread wouldn't even get flamed if you didn't play forum police and try to start wars over it. The OP would just ignore it or explain why they can't use another language and it would have been dropped.
I've never posted a 'why another Python suggestion' question in any other thread. I just joined in on this discussion, since it's something that seems to return quite often.

I do believe there hasn't been any flaming in this thread, and that we've all just discussed it in a civilised way ;-)

---

### Post by slavik on 2007-10-08
Perl was designed for text processing, so was awk, Python wasn't.

---

### Post by ryno519 on 2007-10-08
Can we stop arguing about whether C is better than Python at X or Python is better than C at Y. Can't we just all take a step back for a second... and admit that C++ is better than any of your piddling little languages?

I keed, I keed. :)

Disclaimer: The above was a joke, do not take seriously.

---

### Post by pmasiar on 2007-10-08
> **slavik said:**
> Perl was designed for text processing, so was awk, Python wasn't.

It is because Python was designed for writing programs by humans, Perl wasn't :-)

In case someone missed it, the above is a joke.

---

### Post by Wybiral on 2007-10-08
> **slavik said:**
> Perl was designed for text processing, so was awk, Python wasn't.

I didn't say text processing specifically but Python is safe, has a good string library, and has lots of good parsing libraries available. It's a pretty useful tool for things like this. I also never said Perl wasn't a potential tool for this job. You should really stop taking everything as a personal attack.

If you disagree that Python is a better tool for this job than C, then I would be interested to hear why. That was the only point I was trying to make. I really don't see how this argument has any relevance at all aside from you trying to start a Python vs Perl war for no reason.

---

### Post by j_g on 2007-10-08
> **dwhitney67 said:**
> It is annoying reading that python can do this, python can do that.  Not everyone is privy to using python. If someone says that they need help in C ,  C++ or even Swahili, then please dispense with the useless comments about python.

I agree 100% with your above assessment, and I've said pretty much the same thing (ie, about certain posters who absolutely insist upon replying in just about every thread on this board when such posters are not answering the specific questions asked, and in fact do not have the knowledge/experience to answer). Unfortunately, the moderators on this forum do not care about this situation, and in fact, have gotten a little too biased in favor of allowing certain habitual offenders to do this over and over with impunity. Moderators have even penalized people who complain about things like you have above (so be very careful).

Just today, I answered a question here about XLib programming. I posted a very thorough, explicit, useful answer to the OP's question. I did want to help him. But I _really, really_ had reservations about even posting due to my complete lack of confidence in the moderation on this forum. The quality of moderation is a big turnoff here.

I fully expect your complaint to fall on deaf airs, and rather than things getting better, it's likely the moderation on this forum will result in the people with legitimate complaints being penalized, rather than the folks who are habitually off-topic and engaged in mindless advocacy (here, python advocacy). I say this based upon historical precedence. At the time I am posting this, this thread (much like so many other examples on this forum) has _already_ gone competely off-topic into yet another useless argument among "advocates" -- totally unrelated to the OP's question. And I want to stress this... look through the preceding posts to see where things started going wrong, and you'll see the _same names_ as in the other many threads where the same thing happened. It's not a coincidence. And neither is the fact that moderators have let it happen over and over again, at the same time coming down on anyone who complains about it.

---

### Post by Wybiral on 2007-10-08
> **j_g said:**
> I agree 100% with your above assessment, and I've said pretty much the same thing (ie, about certain posters who absolutely insist upon replying in just about every thread on this board when such posters are not answering the specific questions asked, and in fact do not have the knowledge/experience to answer). Unfortunately, the moderators on this forum do not care about this situation, and in fact, have gotten a little too biased in favor of allowing certain habitual offenders to do this over and over with impunity. Moderators have even penalized people who complain about things like you have above (so be very careful).

So far a few people have posted responses with related help to the OP and NEITHER of you are amongst those people. You are the ones derailing this thread, I was just offering some advice. Maybe it wasn't exactly what they were looking for, but it was more on topic then your responses (and I offer this advice after offering completely on topic advice).

---

### Post by j_g on 2007-10-08
> **Wybiral said:**
> You are the ones derailing this thread

Incorrect. As I pointed out, the thread was _**already** totally offtopic_ at the time of my posting. Check the preceding posts for the usual culprits. You'll see the same names as in the many other threads where the same thing happens over and over and over.

The evidence speaks for itself.

---

### Post by Mathiasdm on 2007-10-08
> **Wybiral said:**
> So far a few people have posted responses with related help to the OP and NEITHER of you are amongst those people. You are the ones derailing this thread, I was just offering some advice. Maybe it wasn't exactly what they were looking for, but it was more on topic then your responses (and I offer this advice after offering completely on topic advice).

I've sent a report to the mods, to ask them to split this thread, so we can have a nice thread to discuss the 'Python advocacy' ;-)

---

### Post by j_g on 2007-10-08
And what happens tomorrow, or the next day, when those same people who respond to just about every thread on this forum, and habitually do not answer the OP's question and take the thread off-topic, do it again in another thread... with total impunity as usual?

---

### Post by slavik on 2007-10-09
I did socket programming in Perl before I did it in C ... but honestly, doing it in C brought more joy to me. Why? Because I understood how Perl/Python/Anything where it's one line to make a socket does it.

pmasiar, you always used to say "learn to crawl before walking," people driving their cars are crawling, but professional drivers (Dale Earnhardt Jr., Jeff Gordon, Ayrton Sena, Damon Hill) are walking because they know (intimately) how/why their car works the way it does.

To be a professional beta tester for game companies you have to be almost as good at programming as the actual game devs.

Look at how we learn other hard science subjects. Do we start with lasers and particle accelarators? No, we start with basics. C is the basics. Learn how it is done in C (or in turn how it is done in assembly, or even the actual circuit) and then learn to appreciate regular expressions and single line socket code.

Here's a question to force you to learn something. In x86 assembly, there is an instruction to multiply two numbers (mul). When we are taught multiplication, we are taught that it is repeated addidtion, so 25 * 5 is 25 + 25 + 25 + 25 + 25, here's a kicker, a CPU does these 5 additions faster than using 5 add instructions.

As a side bonus, take a look at how add instruction is done in hardware and why it can handle two's complement without doing anything special(add and sub are done on the same exact circuit without caring for signs, or even the actual operation almost).

---

### Post by Wybiral on 2007-10-09
> **slavik said:**
> Look at how we learn other hard science subjects. Do we start with lasers and particle accelarators? No, we start with basics. C is the basics. Learn how it is done in C (or in turn how it is done in assembly, or even the actual circuit) and then learn to appreciate regular expressions and single line socket code.

I agree with this to an extent. I think some people naturally absorb low level stuff faster (probably those people who understand the low level components and have more of an interest in circuits and binary logic). But some people can't sit through all of that and are better off jumping right into coding with a higher level language (then they can learn the details later, but they really SHOULD learn the details at some point). It really depends on the person IMO.

I preferred the low level stuff first, playing with logic circuits and assembly (I still do a lot of assembly programming just for kicks) then on to C and eventually C++. But eventually I noticed whenever I played with higher level languages I could get the same code written in fractions of the time it took in lower level languages (even before I learned all the ins and outs of those HLLs). But I do have to admit that C and assembly have a fun puzzle-esque glow to them (at the same time, getting code written 10x faster has a glow too).

---

### Post by Sef on 2007-10-09
Locking this thread.   If you want to help the OP with their question, click [right here]("http://ubuntuforums.org/showthread.php?t=571362").

---

