---
title: "A tricky Question"
date: 2008-07-29
forum: Programming Talk
---

### Post by ral0r3us on 2008-07-29
[SIZE="2"]Does anyone have any Idea what do i need to twick in apache code to force it
to reload it's conf file at a given interval?? let's say every second or something.
The idea behind this is that i want to change The MaxClients Directive online.
Any ideas will be appreciated. Given my experience tho there wont be any
 answers since Google has nothing on the subject.. :confused: but anyway
if you come up with something i'll buy ya a beer :guitar:[/SIZE]

---

### Post by mssever on 2008-07-29
> **ral0r3us said:**
> [SIZE=2]Does anyone have any Idea what do i need to twick in apache code to force it
to reload it's conf file at a given interval?? let's say every second or something.
The idea behind this is that i want to change The MaxClients Directive online.
Any ideas will be appreciated. Given my experience tho there wont be any
 answers since Google has nothing on the subject.. :confused: but anyway
if you come up with something i'll buy ya a beer[/SIZE]You could use cron or some other script to run [FONT=Courier New]apache2ctl graceful[/FONT] every so often. But doing this is a bad idea since it will severely impact the server's performance. It'd be much better to have whatever script you're using to change the MaxClients directive run [FONT=Courier New]apache2ctl graceful[/FONT] only when a change is made.

Don't worry about the beer. I'm a teetotaler. :)

---

### Post by ral0r3us on 2008-07-29
> **mssever said:**
> You could use cron or some other script to run [FONT=Courier New]apache2ctl graceful[/FONT] every so often. But doing this is a bad idea since it will severely impact the server's performance. It'd be much better to have whatever script you're using to change the MaxClients directive run [FONT=Courier New]apache2ctl graceful[/FONT] only when a change is made.

Don't worry about the beer. I'm a teetotaler. :)

Ahh well i've posted the same subject sooo many times that it seems i dont 
explain well anymore. I know all about graceful etc my friend, but as you said
i cannot afford it. What i'm actually asking, is if there is a Human being out
there that knows how can i alter apache code to make it possible to re-load it's 
configuration files without the need of any kind of restart. Sadly i've looked
at the source code... and with great bitterness i admit that without 
a hint of some sort i wont be able to figure out this gargantuan mess. It's the rarest occasions
that i ask for help, and when i do no one is able to answer :(

P.S. Nice try but you didnt earn your tee either :P hehe.

---

### Post by mssever on 2008-07-29
> **ral0r3us said:**
> Ahh well i've posted the same subject sooo many times that it seems i dont 
explain well anymore. I know all about graceful etc my friend, but as you said
i cannot afford it. What i'm actually asking, is if there is a Human being out
there that knows how can i alter apache code to make it possible to re-load it's 
configuration files without the need of any kind of restart. Sadly i've looked
at the source code... and with great bitterness i admit that without 
a hint of some sort i wont be able to figure out this gargantuan mess. It's the rarest occasions
that i ask for help, and when i do no one is able to answer :(

P.S. Nice try but you didnt earn your tee either :P hehe.
I think that your problem would likely require some major changes to the Apache architecture. Now, I've never read Apache's source, so this is just conjecture. But there are likely good reasons why Apache requires a restart. You'd probably have to not only modify Apache to notice config changes, but you'd have to make Apache apply those changes cleanly AND propagate all those changes to the children.

I don't understand why you can't just let your MaxClients change script call apache2ctl. Assuming you've got Apache configured reasonably, you shouldn't have to change MaxClients very often. And this approach would be much simpler.

---

### Post by ral0r3us on 2008-07-30
> **mssever said:**
> I think that your problem would likely require some major changes to the Apache architecture. Now, I've never read Apache's source, so this is just conjecture. But there are likely good reasons why Apache requires a restart. You'd probably have to not only modify Apache to notice config changes, but you'd have to make Apache apply those changes cleanly AND propagate all those changes to the children.

I don't understand why you can't just let your MaxClients change script call apache2ctl. Assuming you've got Apache configured reasonably, you shouldn't have to change MaxClients very often. And this approach would be much simpler.

You're most probably right, but here is the deal, MaxClients sets the boundary
ap_daemons_limit which in fact enforces the limit to how many forks you'll actually 
have. This var is in prefork.c (for mpm=prefork ofc), one idea is to use a pipe
or a fifo to have my program communicate to apache directly what this value 
should be. The point is that if i have let's say X daemons spawned and i want
to reduce em (aka reduce MaxClients) to X - K then i think i'll have K
zombies :lolflag:
But my reasoning is this, if i have a flexible boundary then i have better control
over apache + my soft will probably be useful to the community :)
Now imagine i use apachectl and all it's scripts (tbh only graceful approaches the
function i need) what do they do? They kill all the daemons eventually either 
gracefully or brutally, at this point i've created a bottleneck cause the server
will eventually be unavailable for 2-3 seconds + it will get a hell of a TCP queue
which will overload it for the next minute or so for no reason. The child does not
need to know how many of them are out there so no need to kill em for nothin.

P.S. I appreciate the feedback tho :)

---

### Post by mssever on 2008-07-30
> **ral0r3us said:**
> But my reasoning is this, if i have a flexible boundary then i have better control
over apache + my soft will probably be useful to the community :)
Now imagine i use apachectl and all it's scripts (tbh only graceful approaches the
function i need) what do they do? They kill all the daemons eventually either 
gracefully or brutally, at this point i've created a bottleneck cause the server
will eventually be unavailable for 2-3 seconds + it will get a hell of a TCP queue
which will overload it for the next minute or so for no reason. The child does not
need to know how many of them are out there so no need to kill em for nothin.
Have you asked the folks over at Apache about this? They'd know more about this than I do. I understand that apache2ctl graceful is suboptimal, but I just don't understand the need for the ability to change MaxClients at runtime--unless you're trying to adjust for varying server load, in which case a solution no doubt already exists. But then, I'm no Apache expert, either.

---

### Post by ral0r3us on 2008-07-30
> **mssever said:**
> Have you asked the folks over at Apache about this? They'd know more about this than I do. I understand that apache2ctl graceful is suboptimal, but I just don't understand the need for the ability to change MaxClients at runtime--unless you're trying to adjust for varying server load, in which case a solution no doubt already exists. But then, I'm no Apache expert, either.
:):) I think i'll do that, dunno why it never crossed my mind to ask the people that
made this server :lolflag: hehe, but anyway i think if found a solution.. all that code
grepping did pay out a last! Dunno how stable my solution is (i might have modified something
that really must not be mofified) but it seems to adapt to the new values pretty fast ^^ :)
But it's never a bad idea to double check, so i'll send em the modified source to 
tell me what they think of it.

---

### Post by slavik on 2008-07-30
**apache2ctl reload** will reload the config, but you don't want to run that every second for reasons stated above. what you would want to do is to have the page run a php script (submit stuff to it via POST) and the php script could then maybe do **`apache2ctl reload`**

but then you need to make sure that the www-user has permissions to run the command.

---

### Post by mssever on 2008-07-31
> **slavik said:**
> **apache2ctl reload** will reload the config
The OP already indicated his/her familiarity with apache2ctl. In addition, apache2ctl reload isn't a valid command. The command that best fits the OP's situation is apache2ctl graceful, though the OP has already given some good reasons why it isn't optimal.

---

### Post by ral0r3us on 2008-07-31
> **mssever said:**
> The OP already indicated his/her familiarity with apache2ctl. In addition, apache2ctl reload isn't a valid command. The command that best fits the OP's situation is apache2ctl graceful, though the OP has already given some good reasons why it isn't optimal.
I am happy to announce i have found a solution :guitar: i hacked a bit apache
code and now it reloads the value of MaxClients very fast with no need to restart
it :) It's really really responsive to changes to the MaxClients directive since i injected the code
right at the server's main loop (for version 1.3.41 still working on later versions)
If anyone needs the code i am more than happy to share it, but since i'm not really
familiar to this forums rules i will wait till some member of the staff gives me the go.

P.S. apache2ctl reload isn't a command indeed, it's just a renamed script
of ./apache2ctl graceful since all the reload scripts i've seen send a USR1 or HUP signal.
 This kind of implementation is used in Red Hat as far as i know
but really it's just another way to implement the apache2ctl script and nothing 
more. (it's a he not she btw :P)

P.P.S. Slavik you ain't infallible mate :P hehe

---

### Post by mssever on 2008-07-31
> **ral0r3us said:**
> If anyone needs the code i am more than happy to share it, but since i'm not really
familiar to this forums rules i will wait till some member of the staff gives me the go.
I'm not staff, but I know that there's nothing in the rules to prohibit you from posting open source code that you modified.

---

### Post by ral0r3us on 2008-07-31
> **mssever said:**
> I'm not staff, but I know that there's nothing in the rules to prohibit you from posting open source code that you modified.
:) sounds reasonable! Oke here it goes. (was easier than i thought it would be, apache is 
really easy goin after all)
This will work only for Version 1.3.41 of Apache and since i just made it work 
i cannot guarantee that it will function perfectly, in other words DO NOT try this on PRODUCTION SERVERS!
Having that out of the way the code is pretty straightforward:
```
void fetch_max_clients(void)
{
    /** Addition to Fetch MaxClients Value "Live" **/
    char temp[255]; /* Just a temp array used to compare
						 the pulled strings from the file
						 against newDirective.name       */
    int new_ap_daemons_limit = 0, old_ap_daemons_limit;
    old_ap_daemons_limit = ap_daemons_limit;
    int children_to_gracefully_kill;
    int counter = 0;
    pid_t pid;
    int to_kill;
    char *httpdConfFile = "";

    FILE *ptrApacheConf; /* Self explanatory */


	httpdConfFile = malloc(sizeof(char)*(strlen(ap_server_root)+strlen(ap_server_confname)+1));
	strcpy(httpdConfFile, ap_server_root);
	strcat(httpdConfFile, "/");
	strcat(httpdConfFile, ap_server_confname);

	if ((ptrApacheConf = fopen(httpdConfFile, "r")) == NULL)
		fprintf(stderr,"File %s could not be opened.\n", httpdConfFile);

  	else {         /* The file is scanned
						   until a match or EOF
    					   is found          */
		while (!feof(ptrApacheConf)) {
		fscanf(ptrApacheConf, "%s", temp);
			if (strcmp(temp, "MaxClients") == 0)
				break;
		}

	}

	fscanf(ptrApacheConf, "%s", temp);
    new_ap_daemons_limit = atoi(temp);
	fclose(ptrApacheConf);
	free(httpdConfFile);
	
	if (new_ap_daemons_limit == old_ap_daemons_limit)
		return;

	if (new_ap_daemons_limit < old_ap_daemons_limit) {
        children_to_gracefully_kill = old_ap_daemons_limit - new_ap_daemons_limit;
			
/** In case we have reached here it simply means
    that the new MaxClients Directive is less than 
    the old one so we need to take care of the extra
    children since apache doesn't do that, and they will
    probably end up like zombies eating up memory **/        
        while (children_to_gracefully_kill > 0) {
            to_kill = children_to_gracefully_kill + new_ap_daemons_limit;
            --children_to_gracefully_kill;
            pid = ap_scoreboard_image->parent[to_kill].pid;
				
				/** Make sure we got a valid pid And certainly NOT zero **/
            if (in_pid_table(pid) && (pid != (pid_t) 0)) {
                kill(pid, SIGHUP);
            }
            else {
                ap_log_error(APLOG_MARK, APLOG_NOERRNO|APLOG_ERR, server_conf,
                         "Bad pid (%d) in scoreboard slot %d", pid, to_kill);
            }
        }
        ap_daemons_limit = new_ap_daemons_limit;
	}
	else
        ap_daemons_limit = new_ap_daemons_limit;

	return;

}
```
Inject this code snippet around line 5120 of http_main.c after this declaration:
```
/*
 * Define the signal that is used to kill off children if idle_count
 * is greater then ap_daemons_max_free. Usually we will use SIGUSR1
 * to gracefully shutdown, but unfortunatly some OS will need other 
 * signals to ensure that the child process is terminated and the 
 * scoreboard pool is not growing to infinity. Also set the signal we
 * use to kill of childs that exceed timeout. This effect has been
* seen at least on Cygwin 1.x. -- Stipe Tolj <tolj@wapme-systems.de>
 */
#if defined(CYGWIN)
#define SIG_IDLE_KILL SIGKILL
#define SIG_TIMEOUT_KILL SIGUSR2
#else
#define SIG_IDLE_KILL SIGUSR1
#define SIG_TIMEOUT_KILL SIGALRM
#endif
// <<-------- The snippet should be injected here!

```
When this is done, search the http_main.c for this:
```
while (!restart_pending && !shutdown_pending)
```
This is the main loop of the server (standalone NOT inetd)
and insert a call to the newly made function after this line:
```
int pid = wait_or_timeout(&status);
```
it should look something like this:
```
	while (!restart_pending && !shutdown_pending) {
	    int child_slot;
	    ap_wait_t status;
	    int pid = wait_or_timeout(&status);
	    
	fetch_max_clients();
        .
        .
        .

```

And that's it :) If you raise MaxClients Directive in httpd.conf it will be accounted for
instantly (well ok not instantly but you'll see a reaction in less than a second)
If you want to lower the MaxClients then what i do is kill off the children with
higher pid numbers since (as apache folks mention in the code) children with
lower pid numbers tend to occupy space in the CPU cache and therefore serve up 
more requests :guitar: And since i got this far i think i'll fix up KeepAliveTimeout as 
well, but this one will be trickier than MaxClients, since KeepAliveTimeout
is propagated to the current generation of children, so it will take up
from 20secs to 1-2 mins (maybe more!) for the changes to get into effect, depending of
the traffic of course!

---

### Post by LaRoza on 2008-07-31
> **ral0r3us said:**
> 
If anyone needs the code i am more than happy to share it, but since i'm not really
familiar to this forums rules i will wait till some member of the staff gives me the go.

If it is open source (and Apache is) and you want to release the code, you can :-)

> 
P.P.S. Slavik you ain't infallible mate :P hehe
No, he isn't. I am.

---

### Post by slavik on 2008-07-31
that's a quote from a dilbert character, guess which one. :) (I like him because he is a problem solver and takes advantage of dumb corporations).

---

### Post by ral0r3us on 2008-07-31
> **slavik said:**
> that's a quote from a dilbert character, guess which one. :) (I like him because he is a problem solver and takes advantage of dumb corporations).

hahahaha nice one, no idea what you're talking about, which makes it even funnier :) 
btw, didn't wait long for your approval guys but i reasoned:
hell why not... this is a linux world after all :guitar:

P.S. You really need to add more smilies.. that guitar man can't feel his fingers anymore :lolflag:

---

### Post by mssever on 2008-07-31
> **ral0r3us said:**
> P.S. You really need to add more smilies.. that guitar man can't feel his fingers anymore
Then hopefully he'll stop playing! The two smilies that annoy me are: :guitar: and:lolflag:. If the animation were killed, then it would be a lot better, though someone playing the guitar is rarely relevant to the situations in which people use it.

---

### Post by ral0r3us on 2008-07-31
> **mssever said:**
> Then hopefully he'll stop playing! The two smilies that annoy me are: :guitar: and:lolflag:. If the animation were killed, then it would be a lot better, though someone playing the guitar is rarely relevant to the situations in which people use it.

Honestly there aren't much to choose from ya know :lolflag: hhehehhehehee
+ i think the lolflag is very nice :D especially the hair is awesome :) the 
lil star ---> :KS should get perma ban tho

---

### Post by pmasiar on 2008-07-31
> **slavik said:**
> that's a quote from a dilbert character, guess which one. :) (I like him because he is a problem solver and takes advantage of dumb corporations).

but [http://en.wikipedia.org/wiki/Dogbert](http://en.wikipedia.org/wiki/Dogbert) is also megalomaniac who wants to enslave all humans. I was surprised you selected Dogbert as your avatar. Your love of Perl suggested more freewheeling, enterprise-hating personality, but I might be wrong :-)

---

### Post by slavik on 2008-07-31
> **pmasiar said:**
> but [http://en.wikipedia.org/wiki/Dogbert](http://en.wikipedia.org/wiki/Dogbert) is also megalomaniac who wants to enslave all humans. I was surprised you selected Dogbert as your avatar. Your love of Perl suggested more freewheeling, enterprise-hating personality, but I might be wrong :-)
who said I didn't want to enslave all the humans? :-p

---

### Post by pmasiar on 2008-07-31
> **slavik said:**
> who said I didn't want to enslave all the humans? :-p

I see. Becoming forum mod was just the first step. :-)

If I have to be assimilated, I'll go with borgs... They are at least competent :-)

---

### Post by ral0r3us on 2008-07-31
> **slavik said:**
> who said I didn't want to enslave all the humans? :-p

You picked the wrong side tho :P /reroll to Microsoft hahahaha

---

### Post by drubin on 2008-07-31
This thread has more smilies then any other thread I have seen in a long time.

I once read some where a while ago that it is bad form to include smilies all over the place in posts on forums or mailing lists is this true?

It does annoy me some what but then again this is just me.

---

### Post by mssever on 2008-07-31
> **rubinboy said:**
> I once read some where a while ago that it is bad form to include smilies all over the place in posts on forums or mailing lists is this true?
I haven't heard it before, but I'd agree with it. Smilies are sometimes useful to convey information that would normally be carried by voice (such as sarcasm).

But mostly, they're overused and in the same category as running ten exclamation points together or using LOL as punctuation. Overusing smilies tends to suggest that your vocabulary is too small to express yourself effectively.

Oh, and just for irony: :KS:popcorn::):(:confused::guitar::lolflag:

Edit: One other thing I hate is that when people paste information, sometimes the data gets helpfully converted to 8).

---

### Post by drubin on 2008-07-31
> **mssever said:**
> I haven't heard it before, but I'd agree with it. Smilies are sometimes useful to convey information that would normally be carried by voice (such as sarcasm).

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) 

Take a look at the section header "Send questions in accessible, standard formats"

---

### Post by ral0r3us on 2008-07-31
> **rubinboy said:**
> [http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html) 

Take a look at the section header "Send questions in accessible, standard formats"
Don't be up tight rubin boyo, i think people interested in how to ask questions
can easily find the way on their own... plus hackers don't go on advertising what they are...
smartie pants :P

Anyway, thank you guys it's been interesting and enjoying talking to you all!

P.S. My field of specialty is Control Engineering if you got any troubles with some
crazy robots out there i would be happy to help you out. (if i can of course)

P.P.S. Oh and as you noticed there were no smiles and all... i hope you're happy ruby.

---

### Post by drubin on 2008-08-01
> **ral0r3us said:**
> Don't be up tight rubin boyo, i think people interested in how to ask questions
can easily find the way on their own... plus hackers don't go on advertising what they are...
smartie pants :P

I personally think if you/any one else have never read that (or a similar) one then it is your DUTY to read I before posting on forums. It has nothing to do with knowing how to ask question in daily life it has to do with written non verbal forums with a time delay where you are not able to qualify what you mean.


Do you know what the definition of Hacker is? 
[http://journalism.berkeley.edu/projects/biplog/archive/001168.html](http://journalism.berkeley.edu/projects/biplog/archive/001168.html) Hacker VS Cracker


My link was in response to  
> I haven't heard it before, but I'd agree with it. Smilies are sometimes useful to convey information that would normally be carried by voice (such as sarcasm).


[QUOTE
P.P.S. Oh and as you noticed there were no smiles and all... i hope you're happy ruby.[/QUOTE]

I never said you can't use them, Nor did i say that it was your posts that contained the smilies. Did you think you over used on the smilies. :) ha ha

---

### Post by nvteighen on 2008-08-01
> **slavik said:**
> who said I didn't want to enslave all the humans? :-p

Another one? Man, I'll start learning Java to protect myself :)

Ah, is this guy :guitar: Steve Howe, Jimi Hendrix, Joe Satriani, Eric Clapton, Robert Fripp or any other guitar hero?... or just a guy with a guitar?

---

### Post by ral0r3us on 2008-08-01
> **nvteighen said:**
> 
Ah, is this guy :guitar: Steve Howe, Jimi Hendrix, Joe Satriani, Eric Clapton, Robert Fripp or any other guitar hero?... or just a guy with a guitar?
As long as he ain't Malmsteen all is cool :-p

---

### Post by pmasiar on 2008-08-01
> **nvteighen said:**
> Another one? Man, I'll start learning Java to protect myself :)

another one down to java trap...

learn a free dynamic and agile language: Perl at least, Ruby is better, Python is the best!

---

### Post by drubin on 2008-08-01
> **pmasiar said:**
> another one down to java trap...

learn a free dynamic and agile language: Perl at least, Ruby is better, Python is the best!

Java has become free and opensource!

---

### Post by slavik on 2008-08-01
> **nvteighen said:**
> Another one? Man, I'll start learning Java to protect myself :)

Ah, is this guy :guitar: Steve Howe, Jimi Hendrix, Joe Satriani, Eric Clapton, Robert Fripp or any other guitar hero?... or just a guy with a guitar?
it's me at the tender age of 5. :)

---

### Post by pmasiar on 2008-08-01
> **rubinboy said:**
> Java has become free and opensource!

but Java never was, and never will be, dynamic and agile :-)

---

### Post by drubin on 2008-08-01
> **pmasiar said:**
> but Java never was, and never will be, dynamic and agile :-)

In some ways "static typeing" is a pro over dynamic as in the case of python,perl.

It is easier to maintain  and understand what is going on. Yes dynamic is allot faster for prototyping and quick development but for maintenance?? 


Yes I like python too :)

---

### Post by mssever on 2008-08-01
> **rubinboy said:**
> In some ways "static typeing" is a pro over dynamic as in the case of python,perl.

It is easier to maintain  and understand what is going on. Yes dynamic is allot faster for prototyping and quick development but for maintenance?? 
I've only had that problem in Ruby where a small handful of methods will return nil on error instead of raising exceptions like they should do. Other than that, why should I care what type the object is? It doesn't matter too much when you're using duck typing.

---

### Post by pmasiar on 2008-08-01
> **rubinboy said:**
> In some ways "static typeing" is a pro over dynamic as in the case of python,perl.

I have hard time to understand what is going on in this sentence. Do you use "dynameic typeing"? :-)

> It is easier to maintain  and understand what is going on. Yes dynamic is allot faster for prototyping and quick development but for maintenance?? 

With unit testing, checking for type (duck-typing way: presence of methods) is just the simplest test you write. So you can have both rapid development (agility) and maintaineability.

---

### Post by nvteighen on 2008-08-01
> **pmasiar said:**
> another one down to java trap...

learn a free dynamic and agile language: Perl at least, Ruby is better, Python is the best!

You know I wouldn't go for Java, as I'd prefer staying at the back, implementing some kind of useless data type in several .c files, wondering on exotic libc complains at some random memory address and then just create a main module with a crappy interface as an excuse to test the whole (again, useless) backend. :) (another smiley for this thread)

Ah, and I'm already in Python! I've some mixed impressions on it: agile, but too much built-in features (what would you expect from a C-guy? I'm used to raw and crude minimalism)... Of course, the language it's interesting, specially the coherent way the language is constructed and how the different types connect each other. And I need to play around with it a little more, obviously.

---

### Post by drubin on 2008-08-01
> **pmasiar said:**
> I have hard time to understand what is going on in this sentence. Do you use "dynameic typeing"? :-)

Sorry. I meant to use the term loosely typed. (Hope this is the correct term now).

**Edit:** [http://en.wikipedia.org/wiki/Duck_typing](http://en.wikipedia.org/wiki/Duck_typing)  Not so keen on this... looks messy.

---

### Post by mssever on 2008-08-01
> **rubinboy said:**
> [http://en.wikipedia.org/wiki/Duck_typing](http://en.wikipedia.org/wiki/Duck_typing)  Not so keen on this... looks messy.Not really. If an object has a method with a given name, you can usually assume that it'll behave in a sensible manner analogous to other objects with that method. If you call a non-existent method, you get an exception. Here are some Ruby examples: ```
begin #Equivalent to try in some other languages
  foo.each do |i| # This is the most common method of iterating over an object in Ruby
    puts i # I don't have to worry about i's type. puts automatically calls i.to_s to convert i to a string.
  end
rescue NoMethodError
  puts "I can't iterate over this object"
end

# Alternate method
if foo.respond_to? :each
  foo.each do |i|
    puts i
  end
else
  puts "I can't iterate over this object"
end
```Note that there's little need for explicit typecasting just to iterate. And in those situations where it is necessary, a little duck typing generally takes of that, too.

---

### Post by drubin on 2008-08-02
Ok I see the point. But how is duck typing any different from creating an interface that every object implements?

---

### Post by mssever on 2008-08-02
> **rubinboy said:**
> Ok I see the point. But how is duck typing any different from creating an interface that every object implements?
If you're using static typing, you still have to care about the object's type when you use it. For example, here's a silly example involving returning a string representation of an arbitrary object (in Ruby):
```
def store_string(some_object) # some_object can be any arbitrary type
  # The to_s method returns a string representation of the receiver.
  # to_s is defined in Object, the base class for everything in Ruby, and
  # many classes override it to provide a logical value for the class.
  some_object.to_s # Ruby implicitly returns the result of the last expression
end
``` So, even if there were a common interface to implement to convert an object to a string, that still doesn't change the fact that in statically-typed languages, you still have to declare types for your method signatures. In this example, we know that the return value will be a String, but we don't know (or care about) the input type. Actually, Ruby really only has one type, Object (or VALUE in the C source). Everything else is simply some subclass of Object.

Furthermore, using an interface approach generally *requires* you to implement the entire interface, whether you need all of it or not. Suppose you had a comparison interface, but your code only needed the < operator. Why write the others just to satisfy the interpreter?

Actually, Ruby does have something a bit like interfaces, but much more flexible. Ruby is a single inheritance language, but it supports mixing in modules (Ruby modules != Python modules), which means that the module's methods and instance variables are copied into the target class. So, suppose you wanted to be able to compare strings by length, and suppose strings didn't already provide comparison: ```
class String # Ruby lets you modify classes at any time. If you wanted, you could subclass String instead.
  def <=>(other) # This is Ruby's generic comparison operator.
    self.length <=> other.length # We don't care about other's type. If it doesn't have a length, we'll just get an exception.
  end
  
  include Comparable # Mix in the Comparable module, which gives us a full set of comparison operators defined in terms of our <=> method.
end
```

---

