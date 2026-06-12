---
title: "How NOT to write a shared library"
date: 2007-11-14
forum: Recurring Discussions
---

### Post by j_g on 2007-11-14
I'm interested in audio, so I'm looking over the (frankly horrible) documentation for this new "Pulse Audio" thing, and I see this function in its shared lib:

```
pa_xmalloc()

Allocates the specified number of bytes, just like malloc() does.

However, in case of OOM, terminate.
```

First of all, why are so many programmers who write a Linux shared library offering a simple wrapper function around malloc? Is it too hard for an app to just call malloc? Is anyone so completely absent-minded that he can't remember malloc is used to allocate memory, so he needs an equivalent wrapper in every shared lib he uses?

Second of all, in the case of "out of memory", it just terminates your app right then and there??? Oh great, The enduser spends an hour working on something, does some operation, and BANG! -- all his hard work goes down the drain because some shared library decides it wants to terminate the app. Absolutely ridiculous. And I see that other pulse audio functions call this pa_xmalloc too, so good luck getting around it.

I can just see it now. Every programmer who uses pulse audio will need to add a feature to his app called "Auto-save before _every_ Pulse Audio call because this may be your last chance to preserve your work". Yeah, that should really yield "low latency".

Sorry, but anyone who puts a call to exit() in a shared library should simply be shot dead. That's really, really crummy, amateurish programming. In a shared lib, if something fails, the professional thing to do is return some error code/signal to the app, indicating that the function failed. Let the app decide what it wants to do. You _don't_ terminate the app on your own.

And anyone who makes such a shared library a part of his operating system should be shot dead, and then stabbed through the heart with a stake just to make sure he's really dead.

God help us if this pulse audio thing is ever chosen to replace ALSA in the kernel. This will make Linux stability and reliability go to hell if you have operating system calls terminating apps at will.

---

### Post by SteveHillier on 2007-11-14
I would like to echo the sentiment of this post.
In the days when I programmed we often had to fit stuff into the small model (64K code and data) and if we were lucky the next one up (64K code, 64K data).
That forced you to write efficient code - pointers not indexed arrays etc, functions not inline code etc.
Now we have almost limitless memory it has led to some poor programming.
Just to add that of course every function should really return with an termination code.  One case I remember the programmer was using long jumps on error leaving all sorts of crap behind when he did so, such as not forcing data writes, not unallocating memory.
Eh! those were the days!!

---

### Post by public_void on 2007-11-14
Every call to malloc should be checked. So rather than put the checking code at every point you call malloc, you put that code in one function normally named 'xmalloc', and call that instead.

---

### Post by Wybiral on 2007-11-14
> **public_void said:**
> Every call to malloc should be checked. So rather than put the checking code at every point you call malloc, you put that code in one function normally named 'xmalloc', and call that instead.

But you still need to check for an exception in the calling code. That's the entire reason malloc returns NULL when it fails... That's your exception.

---

### Post by skeeterbug on 2007-11-14
The real kicker here is that you spent 10-20 minutes writing this post. Did you even bother to spend time emailing the author of the library to express your concerns? Probably not. Yeah, everyone should be "shot dead" because how they think something should be done. Give me a break.

---

### Post by j_g on 2007-11-14
> **SteveHillier said:**
> the programmer was using long jumps on error leaving all sorts of crap behind when he did so

Oh yeah, I forgot about the exceedingly evil longjmp(). I actually saw someone use that in recursive code. I was utterly appalled.

longjmp() is a careless approach toward error handling that only a lazy and negligent programmer would use. Code that uses longjmp is historically buggy and unstable. If someone is using longjmp, he seriously needs to rethink his design.

<snip>

---

### Post by j_g on 2007-11-14
> **public_void said:**
> Every call to malloc should be checked. So rather than put the checking code at every point you call malloc, you put that code in one function normally named 'xmalloc', and call that instead.

So you call exit() right then and there, and the hell with preservation of the enduser's hard work, or the reliability of any software that may use your shared lib with exit()'s in it?

Sorry, but I do not find this technique to be acceptable in terms of reliability, stability, nor even usability. I would never use software that could, at any moment, dump the hard work I had done, or make running apps just disappear at random in a puff of smoke.

Please rethink your error handling techniques, for the sake of endusers everywhere.

---

### Post by j_g on 2007-11-14
> **skeeterbug said:**
> You spent 10-20 minutes writing this post. Did you even bother to spend time emailing the author of the library to express your concerns?

If the pulse audio author actually had his software peer-reviewed before it was put into Fedora, and _nobody_ had balked at this, then I have no faith whatsoever in his peer-review process. A shared lib doesn't need to terminate an app that uses it. ALSA doesn't do it, and there's lots of malloc calls there. Calling exit() in a shared lib is simply sloppy, negligent error handling. _No experienced programmer capable of writing quality code should need to be told this._ He should already know it.

---

### Post by public_void on 2007-11-14
> So you call exit() right then and there, and the hell with preservation of the enduser's hard work, or the reliability of any software that may use your shared lib with exit()'s in it?I never said you should call exit(). I agree you should not call exit() in a library. However you could put error handling code in xmalloc meaning you don't have to put that code throughout your program. The error handling code may be simple such as printing to stderr. Despite having to check the return value of xmalloc, the point is to not to have code repetition to handle the same error after every call.

Edit: After reading the code ([xmalloc.c]("http://pulseaudio.org/browser/trunk/src/pulse/xmalloc.c")) the author does write to stderr.

---

### Post by Wybiral on 2007-11-14
> **public_void said:**
> I never said you should call exit(). I agree you should not call exit() in a library. However you could put error handling code in xmalloc meaning you don't have to put that code throughout your program. The error handling code may be simple such as printing to stderr. Despite having to check the return value of xmalloc, the point is to not to have code repetition to handle the same error after every call.

I think the biggest point is that malloc has error handling, it returns NULL. That's a fine exception that your code can catch. I guess it could print to stderr, but even then I think it would be better to say "unable to allocate audio track 'file.ogg'" as opposed to "allocation error". The first is only possible if the calling code catches the exception.

---

### Post by j_g on 2007-11-14
> **public_void said:**
> I never said you should call exit().

Ok, then we're in agreement. I thought you were justifying a shared library function handling error checking by "on OOM, terminate", because that's what I was objecting to about pa_xmalloc's "error handling".

I do also agree with Wy that a shared lib function should not display any error messages (unless the app has given permission to do so). For one thing, if it's a GUI app, it may not even have stdout/stderr going anywhere (but nul or wherever -- but nowhere that it would be useful to an enduser using a GUI app). The app may prefer to display an error message to the enduser in a way that is applicable to the app. (For example, a GTK app may want to use gtk_message_dialog_new).

A shared lib function should return an error code to the app, and let the app decide how it wants to deal with the error.

> After reading the code xmalloc.c the author does write to stderr.

What else does it do? Specifically, what does the PA_GCC_NORETURN define expand to? Is it a call to exit()? If so, is PA_GCC_NORETURN used in even more places?

Edit: Nevermind, I finally traced it down. It defines to __attribute__((noreturn)) which in turn does indeed yield a call to exit(). (Actually, it may not write to stderr. What is does is call abort() and then exit(). abort() is applicable only if code is compiled with debugging turned on. abort() typically presents an error message. But in release code, abort() defines to nothing. And I imagine that only release code would appear in a release distro. So you don't even get an error message in the release code. It just terminates the app without notice nor explanation),

So, how many other Pulse Audio functions use PA_GCC_NORETURN themselves, and how many other Pulse Audio functions make their own calls to pa_xmalloc?

I really hope the Ubuntu devs are not considering using Pulse Audio as part of the default install. This has the potential to seriously affect system stability and usability as a running app can just randomly vanish into a puff of smoke, perhaps taking an enduser's work with it.

---

### Post by 23meg on 2007-11-14
[QUOTE=j_g]I really hope the Ubuntu devs are not considering using Pulse Audio as part of the default install. This has the potential to seriously affect system stability and usability as a running app can just randomly vanish into a puff of smoke, perhaps taking an enduser's work with it.[/QUOTE]

Why just hope? Why not file a bug, and/or post your objection to the development mailing lists, so that it will have some actual effect on the process?

---

### Post by j_g on 2007-11-14
> **23meg said:**
> Why not file a bug

Well, it's not a bug (and I'm sure the original author doesn't consider it to be so, because he deliberately coded it to do what it does). It's simply a design that I consider to be lacking in stability and usability.

> post your objection to the development mailing lists, so that it will have some actual effect on the process?

I posted my objection in a forum here that is supposed to be specifically for providing the Ubuntu developers "feedback" about what features to add to Ubuntu.

I also posted this thread here, not because I want to rag on the Pulse Audio developer (I would have greatly preferred that it had been what I was looking for), but because I want to alert other Linux developers who may decide to use Pulse Audio, or design a shared lib using similiar error handling techniques, of the perils of such a design. I also want them to be aware of the potential for increased instability and usability if such code should make it into the kernel, so that they too can be aware of this, and register their concern as well.

I would hope that someone on the Ubuntu developer team occasionally reads programming forums here, if to do nothing more than find out what app developers do, and don't, find troublesome, helpful, easy-to-use, difficult, worrisome, etc.

---

### Post by pmasiar on 2007-11-14
so you want to talk about the problem, but not help to solve it?

---

### Post by j_g on 2007-11-14
Alerting people to a potential problem is the best way to avoid it. There's an old saying that an ounce of prevention is worth a pound of cure. That _is_ the "solution".

---

### Post by hanzomon4 on 2007-11-15
Has anyone had a program vanish while using pulseaudio because of this "problem"? Hasn't happened to me on Fedora 8, yet. In every Linux distro I've tried I've had apps just up and die, but nothing is perfect. Maybe this is all some developer mumbo-jumbo thats super important, but it seems pretty small to me especially since you haven't experienced this doomsday you speak of. In fact I've never heard of anyone having a problem, caused by pulseaudio, like what you describe. I'll keep my eyes on what happens with fedora 8, but you may want to put the gun down for now.

Also, I don't think pulseaudio is suppose to replace ALSA... I don't even think it can, were you talking about the ALSA dmix plugin?

---

### Post by Wybiral on 2007-11-15
> **hanzomon4 said:**
> Has anyone had a program vanish while using pulseaudio because of this "problem"? Hasn't happened to me on Fedora 8, yet. In every Linux distro I've tried I've had apps just up and die, but nothing is perfect. Maybe this is all some developer mumbo-jumbo thats super important, but it seems pretty small to me especially since you haven't experienced this doomsday you speak of. In fact I've never heard of anyone having a problem, caused by pulseaudio, like what you describe. I'll keep my eyes on what happens with fedora 8, but you may want to put the gun down for now.

Also, I don't think pulseaudio is suppose to replace ALSA... I don't even think it can, were you talking about the ALSA dmix plugin?

It wouldn't cause a problem if you have enough memory. The only problem a malloc error like this would cause is that it's unable to deal with the inability to allocate MORE memory.

If YOUR program catches it and tells the user that it can't allocate more memory, then all may be well. But, if the library bails on its own, then you have no ability to save the users data and report the error... It just closes.

YOU may not see this error, but people with low memory would. And if an error occurs... Oops. There goes your data!!!

---

### Post by nanotube on 2007-11-15
> **j_g said:**
> 
I posted my objection in a forum here that is supposed to be specifically for providing the Ubuntu developers "feedback" about what features to add to Ubuntu.


well, that's where you are missing some key info. this "programming talk" forum is NOT for ubuntu developers (i.e. people who make ubuntu), but for developers who happen to be using ubuntu. in other words, there no guarantee that you'll catch the eye of any actual ubuntu developers by posting here. as suggested in other posts, you'd do much better by posting a launchpad bug - or even a launchpad question, if you don't think this qualifies as a "bug" per se.

---

### Post by j_g on 2007-11-15
> **hanzomon4 said:**
> Has anyone had a program vanish while using pulseaudio because of this "problem"?

First of all, as Wy rightfully points out, the problem would most likely be manifested in low memory conditions, because the exit() is used in a function to handle memory allocation failure. If you've not encountered a low memory condition, then you likely would not have seen any manifestation of this design flaw.

On the other hand, exit() _may_ have been used in other places in Pulse Audio, and so there _may_ be other conditions (besides low memory) when it could cause instability and unusability. I haven't looked at all the Pulse Audio source code. Within 5 mins of visiting the home page, I ran across this description of pa_malloc() and immediately red flags went off when I read that it can terminate an app by design. Further investigation shows that it does indeed call exit(). I noticed a couple other Pulse Audio functions also call pa_malloc(). Before anyone adds this code to a distro, a serious "security audit" of _all_ the code should be made. There are security and stability issues with it. I'm frankly surprised that Fedora went with it as is.

Will it terminate an app without warning or a chance for data preservation? Absolutely. exit() (and Pulse Audio's use of it) provides no means of notification nor data preservation. The whole purpose of exit() is to terminate an app right then and there.

So, you wouldn't know that it was pulse audio causing any unusual behavior on your system (unless you're running a debug version of the code, and run all your apps from the command line). And remember that not all apps have a user interface, so it's not even that you may see a window disappear. (When I say "app", I mean any non-kernel code -- that is to say, any code not running at ring 0). You may see aberrant behavior that happens for what would appear to be "no reason" to an enduser. Note that Pulse Audio also includes a daemon which may or may not be vulnerable as a result of calling (directly or indirectly) pa_malloc. As an enduser, you wouldn't "see" this daemon go down abruptly. A daemon has no user interface. You simply may notice something weird happening on your system, or something suddenly no longer working.

> it seems pretty small to me especially since you haven't experienced this doomsday you speak of.

Well, I certainly haven't experienced any instability or unusabiliy due to Pulse Audio, because I don't use it on my systems. And I won't be installing it either (not unless a full security audit is done, and these design flaws are fixed).

I also wouldn't expect an enduser to worry about the details of software implementation. That is not something that an enduser should have to deal with at all. But I can assure you that pa_malloc() and any Pulse Audio function that directly or indirectly calls it has the potential to abruptly terminate an app. Just because no one has yet confirmed that this design flaw in Pulse Audio specifically has been responsible for some aberrant behavior doesn't mean that it won't happen (or even that it hasn't happened already. I know that this thing has only recently been put into major use, so it's not likely that we've yet to see people able to identify increased instability due to this software specifically. But it's not like your system is going to let you know that Pulse Audio caused something to stop working. It's a plain call to exit(). User mode just disappears, with whatever consequences that engenders. Has anyone observed something on Fedora suddenly not working as it should - particularly anything that may utilize the sound system?).

> I don't think pulseaudio is suppose to replace ALSA.

I don't know if any kernel folks are planning to eventually deprecate ALSA, and replace it with Pulse Audio. (But I worry that this could be a potential threat. Fedora is already putting it in their distro, and it looks like Suse and Ubuntu are seriously considering it).

But what is true right now is that Pulse Audio sits between an ALSA app and the hardware, and also various other audio APIs and the hardware. If all this user mode code is now suddenly being redirected (without even the code's knowledge) through Pulse Audio, then it all inherits the consequences of Pulse Audio's design.

Hopefully, any kernel developers considering it for inclusion will do a security audit, and see this design flaw. Hopefully, distro providers will do the same. (Again, I'm really surprised the Fedora guys missed it. I would have expected them to be more cautious about stability than other distros).

---

### Post by j_g on 2007-11-15
> **nanotube said:**
> this "programming talk" forum is NOT for ubuntu developers (i.e. people who make ubuntu)

It wasn't in this forum that I posted a message saying that I didn't think Pulse Audio should be included in an upcoming Ubuntu (and linked to this thread for details about my objection). It was a forum here (ie, on this web site) that is purported to be a place where people (ie endusers) provide opinions to the Ubuntu developers as to what should (and persumably shouldn't) be added to Ubuntu.

---

### Post by jespdj on 2007-11-15
> **j_g said:**
> Alerting people to a potential problem is the best way to avoid it. There's an old saying that an ounce of prevention is worth a pound of cure. That _is_ the "solution".
Yes, but you should be alerting the author of PulseAudio, and why do you say that this is "not a bug"? Ofcourse it's a bug. And even if it isn't a real mistake in the code, then it's a design bug. It doesn't really matter if you want to call it a bug or not. It's a problem and the author of PulseAudio must be made aware of it.

Shared libraries must NEVER terminate an application. I'm a Java programmer and doing System.exit(...) (which kills the JVM and so terminates your application) in a library is a deadly sin - especially if you're writing a Java web application that's running in an application server. Doing a System.exit(...) would kill the whole app server.

---

### Post by pmasiar on 2007-11-15
First, i appreciate you wrote this manual and try to alert about possible error.
> **j_g said:**
> Alerting people to a potential problem is the best way to avoid it. There's an old saying that an ounce of prevention is worth a pound of cure. That _is_ the "solution".

I agree, alerting people is **much** better solution than shooting them left and right. :-)

If we decide to go with shooting (which I advice against), my suggestion would be to shoot people who complain and whine but do not report the bug properly, and who know how to do it right but don't want to share with people who strive to implement free code (while learning to do it right). So after couple generations, we have population of developers who report bugs properly and without whining, and share knowledge with beginners.

Most people were not born with genetically inherited deep knowledge of how to manage memory allocation errors in C, and shooting people who don't manage memory properly will thin population of developers significantly - possibly leaving only descendants of OP (assuming OP is the only know exception, at least this what I deduced from the rant :-) ) if this trait is indeed inheritable and dominant - and inheritability is not proven yet, or is it? Better not take chances.  :-)

---

### Post by 23meg on 2007-11-15
[QUOTE=j_g]Well, it's not a bug (and I'm sure the original author doesn't consider it to be so, because he deliberately coded it to do what it does). It's simply a design that I consider to be lacking in stability and usability.
[/QUOTE]

If you think a particular design decision is problematic to the degree that it will indirectly cause crashes and other unwanted behaviour, that's a valid reason to file a bug. 

[QUOTE=j_g]I posted my objection in a forum here that is supposed to be specifically for providing the Ubuntu developers "feedback" about what features to add to Ubuntu.[/QUOTE]

If you mean the Idea Pool, it's not a forum that most Ubuntu developers read. The proper way to contact developers and discuss issues such as this is to post to ubuntu-devel or ubuntu-devel-discuss.

[QUOTE=j_g]I would hope that someone on the Ubuntu developer team occasionally reads programming forums here, if to do nothing more than find out what app developers do, and don't, find troublesome, helpful, easy-to-use, difficult, worrisome, etc.[/QUOTE]

Yes, probably *some* developers scan through the forums occasionally, but *all* of them read the mailing lists *all* the time, and they check their bug mail *all* the time. Posting to forums is a very inefficient way to notify developers of issues such as this.

[QUOTE=j_g]
Alerting people to a potential problem is the best way to avoid it. There's an old saying that an ounce of prevention is worth a pound of cure. That is the "solution".[/QUOTE]

True. But you should choose the right medium to alert the right people.

---

### Post by j_g on 2007-11-15
> **jespdj said:**
> It's a problem and the author of PulseAudio must be made aware of it.

But surely someone on the Fedora team has already done so (assuming they felt it was a problem)! Remember that Pulse Audio functions as the "sound server" for all Fedora user mode code, even code that uses other audio APIs (ie, ALSA, ESD, OSS) since Pulse Audio has "emulation layers" for those APIs so that all app's audio I/O ultimately goes through Pulse Audio. So, it affects every Fedora app that uses audio (including any "desktop code"). I'd be incredibly surprised if the Fedora team did not do a complete security audit upon that code before adding it to Fedora, especially since they tout it as a major new feature of the OS. They _must_ have already seen this. (I spotted it within 5 minutes of visiting the web site. I have absolute confidence that Fedora developers would be capable of finding what I found). And then there are all these SUSE and Ubuntu developers who have officially acknowledged that they're considering Pulse Audio for inclusion in future releases. Surely, their audit of the code has gone at least as far as my 5 minute inspection. I'm really, really not being facetious here. I genuinely would be _shocked_ if I'm the first, let alone only, person out of all of these developers to notice this. That just doesn't seem possible.

So realistically, I must assume that either these other developers do not consider it a problem, and/or the Pulse Audio authors do not consider it a problem or do not want to modify the code. In this case, the only alternative is to make people aware of the problem so that:

1) People can object to the inclusion of Pulse Audio, as it is currently designed, in future distro releases.

2) People writing shared libs can be made aware that there are folks who notice things like this, and really do look very unfavorably upon such coding. The hope is that others will not do the same thing in their shared libs.

```
Shared libraries must NEVER terminate an application.
```

Absolutely. But there it is. In Fedora 8. Soon to be in SUSE, I hear. And being considered for the next version of Ubuntu. (Very probably other distros as well, if these 3 are already leaning toward it). You're not suggesting that the Fedora 8 devs did not do a security audit upon some major addition that has far-reaching affects (ie, can impact all user mode code that employs audio), or that such an audit was carelessly done such that they were unaware they added a shared lib that is deliberately designed to terminate an app?

I'm surely not suggesting it. I'm just saying that it was a bad decision to code Pulse Audio that way, and it was a bad (albeit fully cognizant) decision to include it in a distro despite that design flaw, and this same mistake should not be repeated by others.

---

### Post by tageiru on 2007-11-15
```

void pa_xfree(void *p) {
    if (!p)
        return;

    free(p);
}

```
That's a nice way of hiding bugs. I would prefer getting slapped by glibc when I free NULL pointers.

EDIT: free on GNU ignores NULL, but it is still a bad thing as it can hide actual bugs.

---

### Post by hod139 on 2007-11-15
> **tageiru said:**
> That's a nice way of hiding bugs. I would prefer getting slapped by glibc when I free NULL pointers.
There's nothing wrong with freeing null pointers.  From the man page:
> free() frees the memory space pointed to by ptr, which must  have  been returned by a previous call to malloc(), calloc() or realloc().  Otherwise, or  if  free(ptr)  has  already  been  called  before,  undefined behaviour occurs.  **If ptr is NULL, no operation is performed**(emphasis added)

All those "if(ptr!=NULL)" guards before free/delete calls are useless.  Feeing/deleting null pointers is a well defined behavior.  Be careful though, freeing or deleting a pointer does not set it to null, so don't double free or delete.

---

### Post by j_g on 2007-11-15
> **tageiru said:**
> it can hide actual bugs.

Point taken.

But at least that won't terminate the calling app. What alarms me is the use of exit() in a shared lib that forms a major component of an operating system (in this case, the user mode audio core. Hmmm. It just occurred to me. Somebody better audit the kernel mode Pulse Audio code too).

It was a bad decision to put Pulse Audio into Fedora given this current design flaw. And I'm quite sure  it was a fully informed decision. This is Fedora we're talking about, not some fly-by-night one-man distro. This is essentially the unstable branch of RHEL. No way would Red Hat let a major component into their distro without a full security audit first. They're not going to put it into Fedora first, _then_ do the audit, and then rip it out if it fails the audit. Someone on the Fedora team _knows_ that exit() is there. They do not need to be told.

And the Pulse Audio author surely doesn't need _ANYONE_ to tell him he's got calls to exit() in there, and what those do. He _knows_ it. (Well, unless he's _totally_ incompetent, and I'm unwilling to assume that). He designed it that way. Folks need to stop suggesting that someone should tell him about it.

SOAPBOX ASIDE: Most likely what happened is that he did the error handling this way to "save time" when he was getting the code up and running. It was something "quick and dirty" to get going. No doubt he expected to go back later and add real error handling. But what typically happens in these situations is that the author uses all his time to add new features and the code grows so complex, and so many code paths wind up going through that exit(), that to correct it entails re-editing lots and lots of code. He probably said "The hell with this exit() problem. I'll fix it even later on, _after_ I release the code and people are using it, when I have lots and lots of free time to get rid of it". I tell you folks. Unless you're writing a simple utility, you ultimately _DO NOT_ "save time" by using exit() as "quick and dirty" error handling. You ultimately waste time by going back and having to rewrite too much code that winds its way through that exit(). If you're working on something that may grow into a larger project, you save yourself more time/trouble by doing the error handling correctly _the very first time_ you write the code.

Now, I'm not sure _why_ the Fedora developers chose to go ahead and employ Pulse Audio as is. Perhaps they just wanted to get a jump on other distros, and felt that the trade-off between claiming an "early exclusive" trumped any potential decrease in stability and usability. After all, you have to _first_ persuade new users to choose your distro before those people can find out about its stability and usability. Maybe the Pulse Audio authors made a promise to Fedora devs that this design flaw would get fixed eventually, and the devs said "Ok, that will be sufficient for us". Maybe if anyone ran into a bit of trouble, the devs would suggest "put more memory in your system", and that would suffice until such time as a fix arrived. Maybe other things happened, or other compromises were made. I'm just guessing here.

But it was a concious, and I believe bad, decision. And I hope that other distros don't repeat it.

Furthermore, the whole point of this thread is not to alert the Pulse Audio author to something he already knows about. If that's what any reader thought, then he missed the whole point. The point is to alert programmers who may eventually work on a shared lib, or complex projects, that exit() is a crutch that you should avoid in these situations because it will only give you, and others, problems. Learn from others' mistakes so you don't have to repeat them. Otherwise, 2 years from now, we'll have someone else saying "All these previous audio APIs have flaws". And instead of fixing those (most likely because the other API's authors didn't document their code adequately, and so the new guy figures "I may as well start from scratch. It'll be just as fast and easy"), he'll completely toss away the code bases of OSS, ESD, ALSA, _and_ Pulse Audio, to create yet another sound server code base that repeats the flaws of the previous bases. (Like maybe getting stuck with exit() entwined deep into the bowels of this thing).

This is _not_ how open source is supposed to work. I thought that the whole point of having source was to fix the bugs, and design flaws/limitations, in the code you're using right now, rather than tossing it away and making new codebases that "re-invent the wheel" with equally bad flaws.

Come on. I'm a Win32 programmer. I can't be the only one who "gets" how wrong this is???

---

### Post by winch on 2007-11-15
> **j_g said:**
> And the Pulse Audio author surely doesn't need _ANYONE_ to tell him he's got calls to exit() in there, and what those do. He _knows_ it. (Well, unless he's _totally_ incompetent, and I'm unwilling to assume that). He designed it that way. Folks need to stop suggesting that someone should tell him about it.

Why do you think the project has a public issue tracker? It's so people who are not the author can see what's going on without spending all day searching forums and mailing lists.
If you want people to know about an issue with a project then its public tracker is the first port of call.

---

### Post by pmasiar on 2007-11-15
I am just curious why you waste so much time complaining and whining and second-guessing motives of Fedora developers here, if you can instead post bug in bug tracker and link this thread to Fedora's developers discussion.

Either you are smarter than them, and they will fix the bug (**and will thank you for finding it**), or they are smarted than you, and we will find why it is not a problem.

What is your REAL goal: have a good reason to complain, or get the bug fixed?

---

### Post by j_g on 2007-11-16
> **pmasiar said:**
> I am just curious why you waste so much time complaining and whining and second-guessing motives of Fedora developers here

I'm curious why you waste so much time repeatedly claiming that all I'm doing is "complaining and whining" when my messages obviously have a great deal of very detailed, specific, technical supporting evidence to back up each and every "complaint" (read: legitimate point) I've made. I'm also curious why you yourself are "second-guessing" my motives to be only "complaining and whining" (with your implication that I allegedly have some sort of hidden agenda), when in the very message above, I've had to come right out and explain to certain people who "don't get it" (ie, keep talking about reporting known design details, to some mailing list) exactly what this thread is all about.

Perhaps moderators should also be curious.

Knock it off. I'm not going to complain to the moderators about your personal attacks above, but others around here seem keen to do that. If you want to play that game, that's your prerogative.

---

### Post by j_g on 2007-11-16
> **winch said:**
> Why do you think the project has a public issue tracker?

That's irrelevant to this thread. The thread has nothing to do with Pulse Audio bug reporting, and everything to do with how not to design a shared lib. Pulse Audio is simply an example I recently found that demonstrates what I'm talking about. See the thread title, and original post for details.

---

### Post by SteveHillier on 2007-11-16
I know it is some 15 years since I last wrote code but I would have thought that the code posted as

void pa_xfree(void *p) {
    if (!p)
        return;

    free(p);
}

would be better written 
void pa_xfree(void *p)
{
    if (p)
    {   free(p);
    }
    return;
}

the essence is not the way I do braces but I always work of having only one route out of a function.  The function as originally written has an implied return at the bottom of the function and therefore as I have written it will reduce the number of instructions the code generates and have the advantage that you only ever have to trace one exit path and it allows to to do any tidying up if you need.
If I am wrong I am happy to be corrected by those who are writing code today rather than old fogies like me who stopped writing code a long time ago.

Ugh.  Sorry chaps and chapesses, things have happened to my formatting.  You should be able to get the sense of what I have said.

---

### Post by CptPicard on 2007-11-16
The total code size issue should be completely irrelevant, and even when it comes to executed instruction count, you aren't really saving anything...

When it comes to the multiple returns in function question, I actually got into quite a debate on this with as an undergrad with one teaching assistant (who actually was "on loan" from business school... no wonder she had the "wrong" opinion ;) ) ... she felt strongly that there should be only one return at the end of the function.

It's probably essentially a matter of taste, but I prefer having my functions quit whenever they "can", because after that you no longer need to keep on following how and where the return state is saved and finally returned at the end, after some supposedly orderly (and unneccessary) unwinding of your branches, loops... it's just somehow easier to just "stop" reading the function's logic whenever a returnable state comes around...

---

### Post by aks44 on 2007-11-16
> **CptPicard said:**
> It's probably essentially a matter of taste, but I prefer having my functions quit whenever they "can", because after that you no longer need to keep on following how and where the return state is saved and finally returned at the end, after some supposedly orderly (and unneccessary) unwinding of your branches, loops... it's just somehow easier to just "stop" reading the function's logic whenever a returnable state comes around...


+1

Moreover, any decent optimizing compiler will probably rewrite *both* "styles" anyway depending on the optimization flags.

---

### Post by pmasiar on 2007-11-16
> **j_g said:**
> I'm curious why you waste so much time repeatedly claiming that all I'm doing is "complaining and whining" when my messages obviously have a great deal of very detailed, specific, technical supporting evidence to back up each and every "complaint" (read: legitimate point) I've made.

You don't need to "make detailed point" here, you should report a bug. Do you want to have it fixed?

OK, I do it for you. I assume you are talking about [http://en.wikipedia.org/wiki/Pulse_audio](http://en.wikipedia.org/wiki/Pulse_audio) == [http://pulseaudio.org/](http://pulseaudio.org/) ?

I reported it as a [http://pulseaudio.org/ticket/158](http://pulseaudio.org/ticket/158)

---

### Post by winch on 2007-11-16
> **j_g said:**
> That's irrelevant to this thread. The thread has nothing to do with Pulse Audio bug reporting, and everything to do with how not to design a shared lib. Pulse Audio is simply an example I recently found that demonstrates what I'm talking about. See the thread title, and original post for details.

So if this thread is nothing to do with trying to get the situation improved and warning other distros about the problem why say it is?

If you claim to be acting under a motive and your actions don't back it up people will question all your motives. As seen in this thread after just four posts. Then the thread gets hijacked and whatever your real motive was gets lost in the noise.

---

### Post by pmasiar on 2007-11-16
FYI, bug [http://pulseaudio.org/ticket/158](http://pulseaudio.org/ticket/158) was closed as invalid. 

"Also note that due to overcommiting on Linux OOM errors are generally not handled by malloc() returning NULL, but by killing processes via the OOM killer. So spending much time thinking about handling malloc() returning NULL is generally a waste of it."

If you want to know what those experts (real experts, with names and project) think about OP, you need to follow the link - I cannot post it here, I would be banned. But looks like it was not complete waste of time - they had a good laugh out of it :-)

---

### Post by j_g on 2007-11-16
> **winch said:**
> So if this thread is nothing to do with trying to get the situation improved and warning other distros about the problem why say it is?

I have no idea why you're saying that is what the thread is about. I can't read your mind. I know only that I've already _explicitly_ explained what the thread is about (in a previous post), and I'm quite sure that the title I chose for the thread, and the content of my original post, made it quite clear that it isn't what you mistakenly think it's about. You should already know that your above statement is incorrect.

> If you claim to be acting under a motive and your actions don't back it up

Non sequitor. I don't claim to be acting under any motive other than those I've already identified, and my actions are in accordance with those claims.

Please stop making unfounded accusations about my "motives" and "actions".

> As seen in this thread after just four posts. Then the thread gets hijacked and whatever your real motive was gets lost in the noise.

Yes. The first person to post a totally off-topic reply in this thread was "skeeterbug", after a couple others posted on-topic. His post had nothing to do with "How NOT to write a shared library", nor the point of any preceding posts, nor even about programming. It was a post about bug reporting. If he wanted to know whether anyone had reported a particular bug to Pulse Audio authors, then he should have posted a thread "Has anyone reported a bug to the Pulse Audio mail list?" in a forum about Pulse Audio, or bug reports.

Nevertheless, I think that the whole first page of replies was ontopic, and a good discussion (even from people who may have been expressing views contrary to mine. At least they were ontopic and making actual arguments about programming).

On the second page, a few people repeated the mistake of skeeterbug (probably because his message got that started -- that's how it goes) by continuing to post messages about bug reports, in a thread about "How Not to write shared libs" in a programming forum. The moderators should be moving those posts to an appropriate forum (including your message). And one person even used those offtopic posts as an excuse to launch his usual personal attacks. But the fact this happened is definitely not my fault. It's the fault of the people who posted those messages (and the moderators who left the messages there).

Now the thread has taken another turn into discussing a particular optimization. Mind you, unlike the posts about bug reporting and the personal attacks, this is a _legitimate_ programming discussion, and _should_ be persued in this forum. I just wish that someone had spun it off into a new thread (by the OP, or by moderators doing their job) so this one could remain ontopic, and if someone visiting this forum wanted to get info about either shared libs, or optimizations, he could more quickly and easily find the info without it being buried within a thread that has no relevance to the info he seeks.

I'm moderator of a support forum, and the vast majority of my activity is _not_ spent censoring posts, but rather, organizing and updating posts on the board. I spend _the overwhelming majority_ of my time going through archives to make sure information in old posts is uptodate advice in accordance with the latest developments. And I spend equal amounts of time organizing posts into threads so that info is easily perusable for endusers. The readers of the forum unanimously tell me that, due to these actions, they consider this forum the best source of info on the given topic, and one of the very best forums they've used. I'm pretty sure they wouldn't be nearly as enamored with the way that some folks have been allowed to twist this here thread, even in a quest to post messages that have nothing whatsoever to do with the topic of this forum (ie, programming).

---

### Post by pmasiar on 2007-11-16
There is no bug, as explained by pulseaudio experts. Nothing to report to anyone. Just hot air, IIUC.

If it is your word against theirs, I take expert opinions from a person with a name from known project against anonymous poster every time.

---

### Post by tyoc on 2007-11-16
Nice, now I know a little more about exits.

Also, I think in this forum there is no core developer of Ubuntu, perhaps from time to time, but if you really want to complain about something in a code, you should look for mailing list, bug list... or in the case of Ubuntu launchpad...

---

### Post by CptPicard on 2007-11-16
Got to admit I feel his argument that "software should always save data with worst case scenario in mind in case of crash" is weak :) I'd take checking for malloc == NULL any day over being totally paranoid about saving my user's data all the time. :)

The argument for not terminating from library is valid... maybe not in this case but it is...

---

### Post by public_void on 2007-11-16
That was very informative by the Pulse Audio developer. So there are reasons to call exit in a library. I'd like to thank him for his good reply.

---

### Post by j_g on 2007-11-16
> **public_void said:**
> So there are reasons to call exit in a library.

I disagree completely, for the detailed reasons given in my previous posts. I feel that any serious application programmer, as well as enduser, also would agree that a situation where apps are abruptly terminated without their knowledge, permission, and recourse to save work, is "unreasonable" at best.

I am relieved that there are other developers here who have agreed.

---

### Post by CptPicard on 2007-11-16
> **j_g said:**
> situation where apps are abruptly terminated without their knowledge, permission, and recourse to save work, is "unreasonable" at best.


How do you plan on actually managing that in practice in a hard-OOM situation? On modern systems, you're going to need to malloc just to get out of the mess.

---

### Post by Wybiral on 2007-11-16
> **CptPicard said:**
> How do you plan on actually managing that in practice in a hard-OOM situation? On modern systems, you're going to need to malloc just to get out of the mess.

That's a common argument I hear on this situation. People often say "What does it matter, you're out of memory anyway... How can you recover?"

But there's a huge difference from being able to load a 1gb audio track to being able to allocate the small amount of memory required to say "Unable to load file (needs more memory)".

I don't know anything about pulse or how they're using it, but in general... If you have the possibility of reporting the error (instead of exiting the program) then I would suggest you do that.

The same goes with harddrive space... If I'm trying to save a file and my program bails because I ran out of space, I would be pretty upset. But if it says "Not enough disk space, please free some and try again." then I'm happy.

---

### Post by j_g on 2007-11-17
> **CptPicard said:**
> How do you plan on actually managing that in practice in a hard-OOM situation?

First of all, a decent operating system will _not_ typically cause some sort of "kernel panic" as a result of a memory failure, and start terminating apps. (I realize the Pulse Audio author has implied otherwise, but that's because he doesn't want people to reject an excuse such as "Why should I bother doing proper error checking in _my_ code? The Linux kernel does worse anyway.". That's a straw man argument). Such a situation is only a last resort, in extreme situations. If a memory allocation fails, a decent OS will _first and foremost_ try to return an error code to the app. Let me repeat that: a decent OS will _first and foremost_ try to return an error code to the app. In the case of malloc, it returns 0.

I'm going to stress this next point as well, because I don't want people to be misled by a self-serving, and misleading, implication.

**An app should ALWAYS assume that malloc may return a 0, and in such a case, properly deal with that.** If someone ever tells you that it's "pointless" to try to gracefully handle a malloc failure, _do not believe it_.

An app should never assume that a failed call to malloc will result in the app being terminated. (Well, unless you're calling malloc via Pulse Audio's pa_xalloc. Then, assume crash position). Properly dealing with the situation involves exhausting every possibility to preserve the user's work, and keeping your app running. Improperly dealing with the situation would be doing something like calling exit() right then and there, _especially doing it in a shared lib_ that is to be used as a major component of a distro, such as the audio core, and therefore used by many other apps.

Think about it. How many apps have you written that have a direct, or indirect, call to malloc somewhere? Pretty much every app, right? If every failed call to malloc typically resulted in the caller being abruptly terminated, that would be a really, really, really crummy, useless OS. Would _anyone_ use such an OS to run their servers? Would anyone use it for _any_ serious work? I very much doubt it.

So why do people use Linux to run their servers? Because Linux typically does not terminate an app when a call to malloc fails. It's not a totally crummy, useless OS (despite what certain programmers would have you believe, in an effort to excuse their own bad coding).

So, given that you should expect a malloc failure to return 0, in answer to the question "how does an app deal with an OOM condition (with malloc)?", I say:

Check for a zero return, and try to recover from it in some way. See my post in the thread "Why proper error handling should ALWAYS be done" for an anecdotal example, and a much more detailed discussion of what I mean by "recover".

P.S. Read Wy's post as well for a sober, and more reasonable response than "Why should I do proper error checking in my code? The Linux kernel does worse anyway".

---

### Post by Wybiral on 2007-11-17
I decided to test this out on my own computer using this code:

```

#include <stdio.h>
#include <stdlib.h>

#define MB (1024 * 1024)

int main(int argc, char *argv[])
{
    char *mem = NULL;
    long long unsigned int size = MB * 512;
    for(;;)
    {
        if((mem = malloc(size)) != NULL)
        {
            free(mem);
            printf("Successfully allocated and freed %llu bytes!\n", size);
        }
        else
        {
            printf("Unable to allocate %llu bytes. Resize and try again!\n", size);
            break;
        }
        size += MB * 512;
    }
    return 0;
}

```

Here's the results:
```

Successfully allocated and freed 536870912 bytes!
Successfully allocated and freed 1073741824 bytes!
Successfully allocated and freed 1610612736 bytes!
Successfully allocated and freed 2147483648 bytes!
Unable to allocate 2684354560 bytes. Resize and try again!

```

It worked! It properly failed and reported it...

BTW, I only have 512mb ram. So this issue would actually come up if I were having to use too intensive of an application. I would _much_ rather it give me a message like this than bail without saving my work.

But like I said, I haven't looked in the pulse code so I have no idea what context it's being used. But the generic argument that it's pointless not to bail from a failed malloc is wrong. Please don't write code that is going to destroy peoples work without warning.

---

### Post by j_g on 2007-11-17
> **Wybiral said:**
> It worked!

Oh, I _knew_ that a failed call to malloc typically does _not_ cause the kernel to terminate an app, and I've been telling folks this in previous posts. I've already had a situation where I received back a 0 from malloc on Linux. (Made a mistake in the number of bytes I told it to allocate). I _knew_ that when the Pulse Audio author said *spending much time thinking about handling malloc() returning NULL is generally a waste of it*, he was wrong, wrong, wrong. And then he was wrong too. Several other statements meant to suggest that a failed malloc call may terminate an app anyway, so why worry about it, are a straw man argument.

But some people who didn't know any better believed it. Why? Because he had some software bundled with Fedora? Good for him. Congratulations. But his statements are still wrong.

And he still shouldn't be putting an exit() in a shared lib, especially one that is being used as Fedora's "audio core". He needs to stop excusing that, saying things that make other programmers misunderstand what really happens with a malloc failure, and redesign his code. He should also be very careful what he says. I've read some messages on lists where he talks about latency, and other features, of Pulse Audio being superior to other APIs like ALSA. Don't anyone kid themselves. This guy wants Pulse Audio to be taken seriously for important audio use, and be chosen over other APIs for all audio use. But then he says things like *audio software should be the first one to be killed* (terminated), *audio *never* is a crucial component of the system*, and *If audio crashes due to what reason whatsoever all you lose is that your music stops to play -- but no data is lost*. Now imagine you're the developer of RoseGarden, or Audacity, or Ubuntu Studio, or any other software used by people to do serious audio work. What are you going to think about statements like that? Mark my words. Those will come back to haunt him. Although lots of people have now seen that page, I wouldn't be surprised if those statements mysteriously "disappear" at some point.

Look, I don't have anything against the guy. I have read some things about Pulse Audio, and there are actually some pretty good ideas in it. (But, I haven't looked over all the particular code, so I'm definitely not yet prepared to say that I think his particular implementation is good). And there may be various code in Pulse Audio that I'd say "that's done well". But not in this particular instance. Not in pa_xmalloc. Not with that call to exit(). Not with other Pulse Audio functions directly, and indirectly, winding their way through that code. And his closing of a "bug report" about it as "invalid" only hours after the report, coupled with various statements he made in his explanation, means that I personally would never use his code (nor any update to the code) without a complete security audit to see if there was any unacceptable design in the code.

> I haven't looked in the pulse code so I have no idea what context it's being used.

Here it is in a nutshell. He has a function called pa_xmalloc. It's a wrapper around malloc. When malloc returns a 0 (um... why is even checking for 0 after he said that *handling malloc() returning NULL is generally a waste of it*... like I said, his whole argument just seemed illogical to me), he calls exit(). (Ok, he pedantically insisted that he doesn't call exit. He uses a macro. But it defines to a call to abort() and exit(). Don't believe it? Take your example and modify it to call pa_malloc as it exists now. You will NOT see that last message. Hell, the guy even documents pa_xmalloc as "on OOM, terminate". Since when is terminate not terminate??? I'd say that his explanation is not as forthright as it could be).

And then other Pulse Audio functions also call pa_xmalloc. Plus, he documents it as part of the API, so presumably, he expects apps to also call it, although I would definitely not encourage that.

---

### Post by j_g on 2007-11-17
> **Wybiral said:**
> I decided to test this out on my own computer

Wy, do me a favor. (I'm asking you to do it because there are certain people who apparently need to hear it from you too).

On that malloc failure, go ahead and ignore the zero return value. After all, we all know that *spending much time thinking about handling malloc() returning NULL is generally a waste of it*. So just ignore the fact that malloc returns 0 and go ahead and use that return, such as maybe store a value there:

```
*mem = 'A';
```

Tell us (read: anyone who hasn't used C in over 15 years) what happens when you don't worry about properly handling a zero return value from malloc.

And just for the sake of laughs, then try putting the following code in your app:

```
if (mem == 0) exit();
```

Tell us what difference that makes (ie, how much "better" the latter error handling is than the previous code), so we can compare how well all the above is versus the (proper) error handling of your original code.

I'm in the mood for a good laugh.

---

### Post by aks44 on 2007-11-17
It frightens me that there is the need to even explain this simple thing. In fact, what *really* scares me most is that renowned developers (RedHat, libxine authors, who else?...) knowingly decided to use a flawed library without regard to their end-user's stability.

So much for the "*peer-review ensures quality code*" adage...


I guess I'd better stop my rant here before it becomes unpleasant... :mad:

---

### Post by j_g on 2007-11-17
> **aks44 said:**
> before it becomes unpleasant

No, stick around. After Wy completes the tests and posts the results, things are going to get even funnier.

---

### Post by aks44 on 2007-11-17
> **j_g said:**
> [QUOTE=aks44;3787766]before **it** becomes unpleasant
No, stick around.[/QUOTE]

Precision: before *_my previous rant_* became unpleasant (or even rude, knowing myself) to the people that believe there can be excuses for killing an application from a library... ;)


No way I'll stop watching this thread, it is way more funny than any comedy. :p

---

### Post by NathanB on 2007-11-17
FWIW -- I have really enjoyed these threads... so much so that I've extended the conversation onto Usenet:

[http://groups.google.com/group/alt.os.linux.debian/browse_frm/thread/edadb69dec3e595f/d9a163b7b641a052?hl=en#d9a163b7b641a052](http://groups.google.com/group/alt.os.linux.debian/browse_frm/thread/edadb69dec3e595f/d9a163b7b641a052?hl=en#d9a163b7b641a052)

---

### Post by j_g on 2007-11-17
Omg! That _is_ funny! A person on the newsgroup actually asks the question:

*Do you really think a program can carry on and do anything reasonable when it runs out of memory?*

Um... YES! That's the whole point of checking the error return from malloc, and if it's zero, doing something besides keeling over dead into a call to exit(). Yes Virginia, your app _can_ continue to do something.

Is this guy for real??? And he's calling _you_ "an idiot"???

I tell you. We've got to get computer science courses to teach error handling. Some graduates appear not to know what it entails. (And while we're at it, can we please teach them that a failed call to malloc is not the end of the world, assuming, unlike the Pulse Audio author, you don't believe that it's a waste of time trying to recover from it? On the other hand, a call to exit() is _definitely_ the end of your app. The former is recoverable if you actually know how to write error handling. The latter _is_ fatal).

---

### Post by winch on 2007-11-17
> **Wybiral said:**
> I decided to test this out on my own computer using this code:

```

#include <stdio.h>
#include <stdlib.h>

#define MB (1024 * 1024)

int main(int argc, char *argv[])
{
    char *mem = NULL;
    long long unsigned int size = MB * 512;
    for(;;)
    {
        if((mem = malloc(size)) != NULL)
        {
            free(mem);
            printf("Successfully allocated and freed %llu bytes!\n", size);
        }
        else
        {
            printf("Unable to allocate %llu bytes. Resize and try again!\n", size);
            break;
        }
        size += MB * 512;
    }
    return 0;
}

```


Read this article to understand why your test doesn't really test what you think it does.
[http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html)

Malloc is an abstraction. Like many abstractions it has edge cases where the underlying details leak through. In this case the leak is malloc can allocate memory that doesn't exist. When you try and use the memory there is a problem which the malloc abstraction has no way of dealing with.

---

### Post by aks44 on 2007-11-17
> **winch said:**
> Read this article to understand why your test doesn't really test what you think it does.
[http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html)

Good point.


Back on topic, in this very article the author says (page 2):

> **Check for NULL Pointer after Memory Allocation and Audit for Memory Leak**

This is a simple rule, but it sometimes goes omitted. By checking for NULL, at least you know that the allocator could extend the memory area, although there is no obvious guarantee that it will allocate the needed pages later. Usually, you need to bail out or delay the allocation for a moment, depending on your scenarios. Together with overcommit tunables, you have a decent tool to anticipate OOM because malloc() will return NULL if it believes that it cannot acquire free pages later.
Later:

> **Use ulimit() for User Processes**

With ulimit -v, you can limit the address space a process can allocate with mmap(). When you reach the limit, all mmap(), and hence malloc(), calls will return 0 and the kernel's OOM killer will never start. This is most useful in a multi-user environment where you cannot trust all of the users and want to avoid killing random processes.
The point being: way before any hard, unrecoverable OOM condition is hit, the kernel gives any well behaved application (or library :-\") plenty of time (due to malloc returning NULL) to scale down and/or gracefully clean up its mess.

For those who still doubted, this confirms again that a library killing its host application at the first NULL malloc is just badly designed / behaved. Now when the author of such library says that people making a point about good programming practices have "no clue about memory management" and evokes the kernel's OOM killer to support his claims, oh well, I wonder (not!) who really is clueless...

---

### Post by j_g on 2007-11-17
Wy, I just want to know how putting

```
if (!mem) exit();
```

compares to what happens with your original, "proper" memory checking. That's the real point. You have to put that exit() in there, just like pa_xalloc() does. And now you have an actual working example of how the two different approaches yield two entirely different outcomes, one useful, and the other bad. The minute details of what happens inside that call to malloc are irrelevant. We're talking only about the code around it. That's the error handling part.

---

### Post by winch on 2007-11-17
> **aks44 said:**
> The point being: way before any hard, unrecoverable OOM condition is hit, the kernel gives any well behaved application (or library :-\") plenty of time (due to malloc returning NULL) to scale down and/or gracefully clean up its mess.

The point being is that the malloc abstraction alone doesn't provide the ability to handle the problem. If you want to handle the problem you have to leave the nice simple world provided by malloc and start worrying about lots of complicated details.

The whole point of malloc is to enable people to write software without having to deal with those details.
If malloc alone is the right answer or not is a question that often doesn't have a right answer. People use computers for different tasks and so often have opposing needs. How do you keep audio running for as long as possible for one user and sacrifice it as quickly as possible for another?

---

### Post by runningwithscissors on 2007-11-17
It's a mistake. Probably introduced by a not-very-experienced programmer and overlooked by others.
Happens to the best of projects.

Hopefully, it'll be fixed soon.

---

### Post by Wybiral on 2007-11-17
> **winch said:**
> Read this article to understand why your test doesn't really test what you think it does.
[http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html](http://www.linuxdevcenter.com/pub/a/linux/2006/11/30/linux-out-of-memory.html)

Malloc is an abstraction. Like many abstractions it has edge cases where the underlying details leak through. In this case the leak is malloc can allocate memory that doesn't exist. When you try and use the memory there is a problem which the malloc abstraction has no way of dealing with.

But in C it is considered best practice to check your malloc return. And if this is the case for most oom situations involving malloc, then the pa_malloc is silly anyway (it's checking for a NULL to bail out, why do that if it's not going to bail out anyway?)

But in my experience I haven't found a situation (on my computer) that doesn't result in a NULL return from malloc. It's been consistent. I'd like others to do the same. Maybe it varies from gcc to gcc or kernel to kernel... I don't know. But it's always worked for me.

People don't do it because it's easier to use exit (ie: they're lazy) which may be fine for small applications that aren't really important, but if a useful app might be built with your code, DON'T DO THAT. You are going to screw some users out of their data.

I would be devastated if I had just managed to record that perfect guitar solo I'd been working on for the past month and I try to play it back before saving it and... POOF. It all disappears. I can't play that again! One time thing... But I will say once again: I don't know when PA uses it or when PA will be used. But it doesn't look good.

---

### Post by aks44 on 2007-11-17
> **runningwithscissors said:**
> It's a mistake. Probably introduced by a not-very-experienced programmer and overlooked by others.
It's a deliberate misdesign introduced by a (supposedly) experienced programmer.


> **runningwithscissors said:**
> Hopefully, it'll be fixed soon.
Unfortunately it will probably never be fixed unless the project gets huge pressure from the community.
See the author's answer to pmasiar's bug report (which has been closed as "invalid"): [http://pulseaudio.org/ticket/158](http://pulseaudio.org/ticket/158)

---

### Post by winch on 2007-11-17
> **Wybiral said:**
> But in my experience I haven't found a situation (on my computer) that doesn't result in a NULL return from malloc. It's been consistent. I'd like others to do the same. Maybe it varies from gcc to gcc or kernel to kernel... I don't know. But it's always worked for me.

The link in the post you quoted contains one. The code is below.
BEFORE YOU RUN IT READ THIS, it is very likley to trigger the kernel OOM killer which will inevitably kill the process. On the way it may well kill other process especially ones using lots of memory. If firefox is running it will probably kill it first, save any open documents before running it or you may lose work.

```

#include <stdio.h>
#include <stdlib.h>

#define MEGABYTE 1024*1024

int main(int argc, char *argv[])
{
        void *myblock = NULL;
        int count = 0;

        while(1)
        {
                myblock = (void *) malloc(MEGABYTE);
                if (!myblock) break;
                memset(myblock,1, MEGABYTE);
                printf("Currently allocating %d MB\n",++count);
        }
        exit(0);
        
}

```

> I would be devastated if I had just managed to record that perfect guitar solo I'd been working on for the past month and I try to play it back before saving it and... POOF. It all disappears. I can't play that again! One time thing... But I will say once again: I don't know when PA uses it or when PA will be used. But it doesn't look good.

Then you better make sure you don't run out of memory or the app saves your work on a SIGTERM. Since the app likely to be using lots of memory and is not an essential system process it will be near the top of the OOM killers list of processes to kill.

---

### Post by tyoc on 2007-11-17
I think if an app use it (a client) perhaps after some crash report from the users of that app (if that even gona happen), it will try to check and if get there perhaps  do a workaround.

Also like has been pointed, normally you will handle your own funciton, macro ETC over your data allocation, that mean that if you have pa_malloc and malloc, normally you will write another function YOURAPP_malloc and perhaps only use pa_malloc for things related to PA (Im sure that almost all people do a extra function for handle malloc directly that a workaround for handle the handle of a malloc funtion in other APP)... I dont know the internals, but reading the presentation it say that it is an audio server, thus I will hope that when it crash, only the server will shut down... but guess what?, also the client will crash... (aka in a online "real time" game you shutdown server, players can't continue playing, that depend on the client)... if the term server system is like any other server, thus it will only shutdown the threadprocess that is causing that allocation, I mean that exit or _exit will exit that execution line and you should handle it in your client.

But... if you use that function directly, thus hell yea, you will close your app in that **specific** case... but again, I return to you will normally do your own allocation routines for your OWN USER DATA, not exactly the data that is handling PA...

It will be interesting to see a real test, I mean a client using actually PA from some time now and see if this is a problem for them or not, also for test purpose try to raise that corner case (if you see in the client buglist, mailing list things like: magic close, lose all data, thus perhaps is a impact of this way, but you should then see if it is or not).


I dont know much about sound programming or recording and related, but Im sure that those type of apps use multiple threads or perhaps process to do the work.

---

### Post by Wybiral on 2007-11-17
> **winch said:**
> Then you better make sure you don't run out of memory or the app saves your work on a SIGTERM. Since the app likely to be using lots of memory and is not an essential system process it will be near the top of the OOM killers list of processes to kill.

OK, I ran it... But nothing else died. Here's what I got:
```

...
Currently allocating 2039 MB
Killed

```

But that program was very clearly leaking memory. The kernel doesn't kill this program:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MEGABYTE 1024*1024

int main(int argc, char *argv[])
{
    void *myblock = NULL;
    int count = 1;

    while(1)
    {
        myblock = (void *) malloc(count * MEGABYTE);
        if (!myblock) break;
        memset(myblock, 1, count * MEGABYTE);
        free(myblock);
        printf("Allocated and freed %d MB\n", count);
        count *= 2;
    }
    printf("Sorry Dave... I can't do that.\n");
    return 0;
}

```

Which is a more sane test than trying to rapidly allocate all of the memory. I get this:

```

Allocated and freed 1 MB
Allocated and freed 2 MB
Allocated and freed 4 MB
Allocated and freed 8 MB
Allocated and freed 16 MB
Allocated and freed 32 MB
Allocated and freed 64 MB
Allocated and freed 128 MB
Allocated and freed 256 MB
Allocated and freed 512 MB
Allocated and freed 1024 MB
Sorry Dave... I can't do that.

```

So even if there are cases where it may kill it, that's no excuse to just assume that it always will. There's no reason not to assume it's recoverable.

---

### Post by winch on 2007-11-17
> **Wybiral said:**
> Which is a more sane test than trying to rapidly allocate all of the memory. I get this:

Programs which try to allocate more memory than the system has in total are sane? Who would use such a program, it would at best complain that malloc failed and at worse crash because it didn't check malloc failed.

---

### Post by CptPicard on 2007-11-17
> **winch said:**
> Programs which try to allocate more memory than the system has in total are sane?

The issue is that actually, you don't know. It's surprisingly hard to figure out beforehand if your malloc would succeed or not -- post-check is really the only sane option, if you want to check in the first place...

---

### Post by samjh on 2007-11-17
What an interesting thread.  The most intellectual thread on these forums for quite a while, methinks.

My experience in writing shared libraries is almost nil, so perhaps more informed posters may correct me on this:

I would have thought that the correct way to handle errors in any library would be for the offending function to return an error code, which should then be propagated back to the calling application, and let the application decide what to do.

In the case of malloc() gone wrong, surely it is not too difficult to check for a NULL return, then propagate the error to the calling application for remedial action?  Of course a library designed haphazardly will not allow this easily, but no software should be designed that way, or at least a generic and graceful error-handling framework for all functions should be implemented.

In Linux environments, I think the OOM-killer only kicks in if an offending process tries to use allocated memory that doesn't exist.  So in other words, if the return value of malloc() is checked and error handled before a process starts to manipulate the data within that memory space, there should normally be enough memory to gracefully terminate the process without loss of an end-user's data.  To make it even more robust, a library or application could also implement a handler for SIGTERM from the OOM-killer to handle a graceful exit.

---

### Post by LaRoza on 2007-11-17
> **Wybiral said:**
> 
```

Allocated and freed 1 MB
Allocated and freed 2 MB
Allocated and freed 4 MB
Allocated and freed 8 MB
Allocated and freed 16 MB
Allocated and freed 32 MB
Allocated and freed 64 MB
Allocated and freed 128 MB
Allocated and freed 256 MB
Allocated and freed 512 MB
Allocated and freed 1024 MB
Sorry Dave... I can't do that.

```

I got an infinite loop (that I killed). It put "Allocated and freed 0 MB" for a very long time.

---

### Post by Wybiral on 2007-11-17
> **LaRoza said:**
> I got an infinite loop (that I killed). It put "Allocated and freed 0 MB" for a very long time.

Really? How far did it make it before that happened? Can you try it with a "long long unsigned int" instead of a regular int?

---

### Post by pmasiar on 2007-11-17
> **Wybiral said:**
> 
The same goes with harddrive space... If I'm trying to save a file and my program bails because I ran out of space, I would be pretty upset. But if it says "Not enough disk space, please free some and try again." then I'm happy.

This is exactly what happened to me once (with hard disk being full), and after getting message, saving to other disk, and cleaning up, life continued without a problem.

Obviously, memory is harder - you have only one memory, and when full, it is full.

---

### Post by LaRoza on 2007-11-17
> **Wybiral said:**
> Really? How far did it make it before that happened? Can you try it with a "long long unsigned int" instead of a regular int?

I let the program run again, and dumped the results to a text file. I killed the program when it was started slowing down my computer. The text file is over 500 MB and I can not post it (or even open it).

It seems the if condition is never met, but the memory is never allocated.

---

### Post by DavidBell on 2007-11-17
> **pmasiar said:**
>  you have only one memory, and when full, it is full.

But this is not the case.

If you ask for one byte and malloc says no, well then you really are in trouble. But it is more likely it is going to be refusing requests for Mbytes. If it says no in that case it doesn't mean memory is empty, just that there's not as much as you asked for. So then you cancel the big memory operation and run cleanup code

I'm totally with j_g on this, libs should never terminate their calling app. The way it it is supposed to work is ...

* app calls lib function

* lib function fails due to OOM or *whatever*. lib doesn't kill parent app, it sends back an 'operation failed' return code, often with extra info about why.

* app checks return code, if failed cleans up, alerts user etc, user kills a few processes that *they* decide are not critical, ....

That way between lib, app and user things like unsaved work don't get destroyed without warning.

DB

---

### Post by DavidBell on 2007-11-17
> **LaRoza said:**
> I got an infinite loop (that I killed). It put "Allocated and freed 0 MB" for a very long time.
Did you copy word for word?

Sounds like you didn't initialise

#define MEGABYTE 1024*1024

and

int count = 1;

---

### Post by LaRoza on 2007-11-17
> **DavidBell said:**
> Did you copy word for word?

Sounds like you didn't initialise

#define MEGABYTE 1024*1024

and

int count = 1;
Yes.

I am puzzled by the behavior.

---

### Post by Wybiral on 2007-11-17
> **LaRoza said:**
> Yes.

I am puzzled by the behavior.

Since you got a bunch of 0's for the count, I'm willing to bet it had nothing to do with malloc. It was more likely that malloc wasn't reporting an error because it was only having to allocate 0 bytes (and it gladly did so, lol)

At first I suspected it to be an integer overflow. Such as:
```

#include <stdio.h>

int main(int argc, char *argv[])
{
    int count = 1;
    while(count != 0)
    {
        count *= 2;
        printf("%d\n", count);
    }
    return 0;
}

```

But thinking about it, the odds that you had enough memory for it to get that far are pretty unlikely.

Try adding a "count > 0" to the while loop and see when it exits.

---

### Post by samjh on 2007-11-18
I've just tried Wybiral's code and get the expected behaviour.
```
Allocated and freed 1 MB
Allocated and freed 2 MB
Allocated and freed 4 MB
Allocated and freed 8 MB
Allocated and freed 16 MB
Allocated and freed 32 MB
Allocated and freed 64 MB
Allocated and freed 128 MB
Allocated and freed 256 MB
Allocated and freed 512 MB
Allocated and freed 1024 MB
Sorry Dave... I can't do that.
```
LaRoza, try cutting and pasting Wybrial's code instead of retyping it.  Otherwise perhaps re-install gcc and try again?

---

### Post by j_g on 2007-11-18
> **samjh said:**
> My experience in writing shared libraries is almost nil.

I would have thought that the correct way to handle errors in any library would be for the offending function to return an error code, which should then be propagated back to the calling application, and let the application decide what to do.

And you thought correctly. You've _already_ gotten a head start upon certain people who _have_ written shared libs, because you'll be doing it correctly from the beginning.

---

### Post by LaRoza on 2007-11-18
> **samjh said:**
> 
LaRoza, try cutting and pasting Wybrial's code instead of retyping it.  Otherwise perhaps re-install gcc and try again?

I did copy and paste. Looking for other solutions now, report back later.

---

### Post by LaRoza on 2007-11-18
[php]
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MEGABYTE 1024*1024

int main(int argc, char *argv[])
{
    void *myblock = NULL;
    int count = 1;

    while(count != 0)
    {
        myblock = (void *) malloc(count * MEGABYTE);
        if (!myblock) break;
        memset(myblock, 1, count * MEGABYTE);
        free(myblock);
        printf("Allocated and freed %d MB\n", count);
        count *= 2;
    }
    printf("Sorry Dave... I can't do that.\n");
    return 0;
}
[/php]

```

Allocated and freed 1 MB
Allocated and freed 2 MB
Allocated and freed 4 MB
Allocated and freed 8 MB
Allocated and freed 16 MB
Allocated and freed 32 MB
Allocated and freed 64 MB
Allocated and freed 128 MB
Allocated and freed 256 MB
Allocated and freed 512 MB
Allocated and freed 1024 MB
Allocated and freed 2048 MB
Allocated and freed 4096 MB
Allocated and freed 8192 MB
Allocated and freed 16384 MB
Allocated and freed 32768 MB
Allocated and freed 65536 MB
Allocated and freed 131072 MB
Allocated and freed 262144 MB
Allocated and freed 524288 MB
Allocated and freed 1048576 MB
Allocated and freed 2097152 MB
Allocated and freed 4194304 MB
Allocated and freed 8388608 MB
Allocated and freed 16777216 MB
Allocated and freed 33554432 MB
Allocated and freed 67108864 MB
Allocated and freed 134217728 MB
Allocated and freed 268435456 MB
Allocated and freed 536870912 MB
Allocated and freed 1073741824 MB
Allocated and freed -2147483648 MB
Sorry Dave... I can't do that.

```

I have 2.5 GB of RAM. Explain this please....

---

### Post by Wybiral on 2007-11-18
> **LaRoza said:**
> I have 2.5 GB of RAM. Explain this please....

Ohhh... It's because malloc only accepts "size_t" bytes. On my computer, "size_t" is limited to (2 ^ 32) - 1 or 4294967295. The multiplication in the parameter must be overflowing it and it will never reach more than 4 gb (which your ram + swap is apparently covering). Crazy, I don't think it's possible to allocate more than that much contiguous space.

EDIT:

You could try allocating 2-3 gb of memory before the loop if you want to test whether or not it will catch the NULL return.

---

### Post by DavidBell on 2007-11-18
> **LaRoza said:**
> I have 2.5 GB of RAM. Explain this please....

In addition to what Wybiral said, the reason the last line reports -2147483648 is that *count* is an unsigned int, so the true value of 2147483648 get rolled over to it's negative. The one after that (4GB) fails.

[QUOTE=Wybiral]On my computer, "size_t" is limited to (2 ^ 32) - 1 or 4294967295. [/QUOTE]

Interesting. In 32 bit windows memory pointers are unsigned so you are limited to 2^31 (2GB), though later versions let you compile with a flag to get about 3GB I think.

You actually have to be careful with pointer arithmatic is it really is full 32 bit. Eg if you want to find pointer half way between *A & *B you might be tempted to do *C = (A+B)/2, this always works with 31 bit, but can fail in 32 bit if A + B > 2^32 (rolls over to a low number not half way between).

DB

---

### Post by slavik on 2007-11-18
8GB of RAM, the following code makes my system freeze. :) (not checked completely).

[php]
/*
 *      test.c
 *
 *      Copyright 2007 Vyacheslav Goltser <slavikg@gmail>
 *
 *      This program is free software: you can redistribute it and/or modify
 *      it under the terms of the GNU General Public License as published by
 *      the Free Software Foundation, either version 3 of the License, or
 *      (at your option) any later version.
 *
 *      This program is distributed in the hope that it will be useful,
 *      but WITHOUT ANY WARRANTY; without even the implied warranty of
 *      MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 *      GNU General Public License for more details.
 *
 *      You should have received a copy of the GNU General Public License
 *      along with this program.  If not, see <http://www.gnu.org/licenses/>.
 */


#include <stdio.h>
#include <malloc.h>
#include <unistd.h>
#include <signal.h>

#define SIZE 1024*1024*1024

void handler(int n) {
	printf("I got a SIGINT\n");
	_exit(0);
}

int main(int argc, char** argv)
{
	long long int i = 1024*1024*1024;
	printf("Asking for %d eight times\n", SIZE);
	char *stuff1 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff2 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff3 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff4 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff5 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff6 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff7 = (char *)malloc(sizeof(char)*SIZE);
	char *stuff8 = (char *)malloc(sizeof(char)*SIZE);
	signal(SIGINT,handler);
	while (i--)	{
		*(stuff1+i)=0;
		*(stuff2+i)=0;
		*(stuff3+i)=0;
		*(stuff4+i)=0;
		*(stuff5+i)=0;
		*(stuff6+i)=0;
		*(stuff7+i)=0;
		*(stuff8+i)=0;
	}
	while (1) sleep(1);
	return 0;
}
[/php]

---

### Post by LaRoza on 2007-11-18
I also have a 64 bit processor, but I don't know if that makes a difference.

---

### Post by shevegen on 2007-11-18
> "The real kicker here is that you spent 10-20 minutes writing this post. "
LOL
How slow are you to write posts like this?

I mean... give ME a break. 10-20 minutes for such a post?
HAHAHAH you think anyone takes your guess for serious? :)

> "Did you even bother to spend time emailing the author of the library to express your concerns?"
Why should he? There are two kinds of projects:
One with documentation
and one without.

I dare claim Ogre3d became so popular because it emphasized on docu. And I tell you exactly what to do with code that comes without docu - throw it away so it will never be used.

> 'Yeah, everyone should be "shot dead" because how they think something should be done.'
I dont think everyone. Sometimes projects emerge that really improve things. People should have the liberty to do that. And I endorse everyone who does so, we need the good and better ideas. Every once in a while great projects emerge that replace crappy projects. This is very good and needed.

But for sure those that are too f******* lazy to write documentation should be shot dead. No, not they... noone should be shot dead anyway. Bu the program they have written should be shot. Without mercy. Only then can a change happen.

This is really a disease in the open source world - how can you excel with a better product if the product doesnt care about docu really? About teaching people? Why do so many old-style projects emphasize writing crappy man pages which are so boring - and once they done so, they stop it? This mindset must change. They should TEACH people how to use it, they should EXPLAIN reasons, and so on... and they should STOP with the archaic UNIX concept of throwing one man page out and telling everyone to RTFM. 
This attitude MUST DIE and people that pursue on this attitude MUST STOP.
We are in the world of wikipedia and wikis, of trac management and myriads of other projects that help. But archaic coders dont bother. 

In fact, there are TONS of projects which need a lot of improvements altogether over older projects (not always...) but I wouldnt help a project that does not care about documentation at all. 

Keep your code to yourself in this case.

---

### Post by pmasiar on 2007-11-18
I know projects where top developer creates code, with request to someone chime in and write basic docs. And someone does, and community of experts double-check it and make sure it is correct. This creates a way for top developers not to waste time on writing docs, and less expert people to contribute.

And without shooting anyone :-)

---

### Post by samjh on 2007-11-18
> **LaRoza said:**
> I also have a 64 bit processor, but I don't know if that makes a difference.

I don't think it does for this particular case.  I also have a 64-bit processor, but Wybrial's code works just as he described it.  I have 2 GB of RAM.

[QUOTE=pmasiar]I know projects where top developer creates code, with request to someone chime in and write basic docs. And someone does, and community of experts double-check it and make sure it is correct. This creates a way for top developers not to waste time on writing docs, and less expert people to contribute.[/quote]Documentation should be written parallel to the code itself.  Or at least comment the code so that automatic documentation generators can extract the bare essentials from it.

The HOWTO-style documentation can be written by the community, but the framework for that sort of thing should be established by the development team.

The problem with a non-developer writing the documentation and relying on "experts" to check it, is that these "experts" are usually the developers.  If the developers can't be arsed to write documentation to begin with, then the trend seems to be that they never bother check community documentation anyway.  For non-developers to become "expert" with the software, they need time to learn the thing, and even then they don't have the depth of knowledge the developers do.  At best, you end up with half-obsolete documentation or documentation with a lot of missing content.

No.  Developers should follow industry best-practice, which incidentally happens to be taught to IT students the world over: write documentation as you develop.

Those projects you talk about must be exceptions to the general trend, not the usual case.  Because there are a LOT of FOSS projects with piss-poor documentation (compare GTK's official docs with QT's docs from Trolltech, for example).  I've tried to contribute myself to some of them, but for larger projects that is nigh impossible without copious leisure time.


[SIZE="4"]By the way, isn't this thread supposed to be about "How NOT to write a shared library"?[/SIZE] :p

---

### Post by pmasiar on 2007-11-18
> **samjh said:**
> 
[SIZE="4"]By the way, isn't this thread supposed to be about "How NOT to write a shared library"?[/SIZE] :p

Well, this thread was always a little rant about how FOSS sucks, so complaining about sucking docs is on topic :-)

To people complaining about sucky docs I have two comments: 
1) This is free software. If you understand **what** is wrong with docs, fix it, submit patch. Docs is text, exactly as sources. Would maintainers reject such a patch? And if they do, create another competitive doc website -- if it is so much better, it will be linked.
2) Having bad docs (and sources) is still better than having no docs and no sources, just ask samba people.

And if you say "this is less than perfect", I agree. I am not aware anybody promised anything being perfect in real life. What is?

---

### Post by samjh on 2007-11-18
> **pmasiar said:**
> Well, this thread was always a little rant about how FOSS sucks, so complaining about sucking docs is on topic :-)I disagree.  The subliminal message in this thread  is about improving the standards of FOSS projects, not a statement that they "suck".

j_g doesn't click with PulseAudio developer's use of an exit() in a shared library, which is a valid criticism.  Just because a lot of programmers do it because they can't be bothered to do robust error-handling doesn't mean that it's the right thing to do.  Keeping with best-practice is usually inconvenient work; taking the easy route might be convenient, but if you want top-quality software, it is not the right way.

While I don't agree with j_g's tone, the principle of his pointing out the ill-practice is not to be derided.  He just managed to frame a valid criticism in a not-so-constructive way (shooting people?  come on now). ;)

---

### Post by slavik on 2007-11-18
the only libpurple documentation I've found was anotated function parameters ...

everything else I deduced from looking at code flow (who calls what).

---

### Post by NutMonkey on 2007-11-18
I'd like to point out that the g_malloc() function in GLib also exits.  Where do we fill out the bug report to get glib and everything that uses it removed from Ubuntu, for stability reasons?

Handling malloc() errors gracefully sounds good, but has little practical value.  In a real-world situation where you were out of memory, malloc() will not actually return a 0.  And if it did, there's not much you could do about it.  If you're allocating 1GB at a time you have bigger problems than malloc checking..

If your data is critical, there's another error case you should solve for that's much more common than OOM, which is LOP (Loss of Power).  Solve the problem of how to make sure that your data is not lost when the power goes out, and you will find that you automatically have a solution to the OOM abort case as well.

---

### Post by pmasiar on 2007-11-18
> **samjh said:**
> While I don't agree with j_g's tone, the principle of his pointing out the ill-practice is not to be derided.  He just managed to frame a valid criticism in a not-so-constructive way (shooting people?  come on now). ;)

Effort is judged by the result.

If post does not persuade readers to do what writer suggests them to do, it can be hardly a success.

I agree wholeheartedly with the goal of making free software more stable and usable. Shooting developers, even figuratively, is not a good way to get there, IMHO. So OP need to make some thinking what exactly he wants to accomplish, and how.

---

### Post by j_g on 2007-11-18
> **NutMonkey said:**
> In a real-world situation where you were out of memory, malloc() will not actually return a 0.

I've seen this allegation made numerous times. But it isn't true. We've already seen actual examples of malloc returning a zero, running on actual computers. If your allegation were true, that wouldn't be possible.

> If you're allocating 1GB at a time you have bigger problems than malloc checking.

Such as what? Swapping to disk? Memory fragmentation? Not a problem as long as it doesn't cause a process to up and vanish without the enduser being given recourse to try and reclaim free memory in whatever way he deems preferable (ie, closing down unneeded windows, choosing which apps to terminate, unplugging external devices to see if that frees up RAM, stopping unneeded services... um, daemons... to see if that frees RAM etc), nor cause loss of the enduser's work -- you know, like exit() does (or just ignoring the 0 return value, and pretending it isn't 0 -- which ultimately makes the OS do to your app what exit() does).

To those folks who are still arguing that it's "pointless" to attempt to recover from a malloc failure gracefully because Linux somehow or other makes that impossible, this is both wrong, and a disservice to poor endusers who may be stuck using your software. Don't do it. Just... don't. I don't care if other Linux programmers do it already. Just... don't.

---

### Post by Wybiral on 2007-11-18
> **NutMonkey said:**
> I'd like to point out that the g_malloc() function in GLib also exits.  Where do we fill out the bug report to get glib and everything that uses it removed from Ubuntu, for stability reasons?

You have a point... I guess if everyone else writes unstable code we should jump the bandwagon and join in. [/sarcasm] GLib is a nice library, but that doesn't mean the programmers are Godlike and that you should base all of your work on theirs.

> **NutMonkey said:**
> Handling malloc() errors gracefully sounds good, but has little practical value.  In a real-world situation where you were out of memory, malloc() will not actually return a 0. 

Do you have any examples of this?

> **NutMonkey said:**
> And if it did, there's not much you could do about it.

You can let the library user decide what to do with the issue.

---

### Post by j_g on 2007-11-18
> **pmasiar said:**
> Shooting developers, even figuratively, is not a good way to get there

How many developers have you "figuratively shot" to test your theory? Or is this yet another attempt to derail a legitimate programming thread with more off-topic posts, just to "bury" others' Linux programming discussion with noise (because you think that those statements don't portray Linux in the best possible light, and you don't want anyone else to hear them, since you can't/haven't directly responded to the specific thread topic with a convincing counterargument)?

I thought so.

> If post does not persuade readers to do what writer suggests them to do, it can be hardly a success.

This thread is not about whether anyone actually uses advice from this forum, nor how successful nor unsuccessful particular attempts to offer advice are.

> this thread was always a little rant about how FOSS sucks

Wrong _again_. This thread was (and still would be if you didn't keep bringing it off-topic) "why bad error handling sucks" -- in particular how bad it is to just fall upon your sword by calling exit() when malloc returns 0, instead of trying to gracefully recover from it -- especially when you do the former in a shared lib that a number of other apps use. _That's what it's about_ (for about the third time. Geez).

Another, less important point, was also about why so many programmers seem to be exposing "wrappers" for malloc in their shared libs. It didn't occur to me, upon reading initial replies to this, that people mistakenly thought I meant, "why put the call to malloc in its own function that also does error handling?". (I should have used the word "exposing", in lieu of "offering", in the initial question. That probably would have cleared some misunderstanding). What I meant was, why expose such a function to apps? For example, pa_xalloc() is documented as part of the Pulse Audio API. I presume that the Pulse Audio author therefore intends for apps to call this too (although I strongly do _not_ recommend this). All pa_xmalloc is, is a (bad) wrapper around malloc. And I've seen the same thing in too many other shared libs (well with Linux anyway. Off the top of my head, I can't remember seeing some Win32 lib code that exposed just a simple wrapper around malloc, GlobalAlloc, or VirtualAlloc. So yes, it's a Linux programming problem that I'm seeing. That's not because I'm "attacking Linux". It's just that this appears to be mostly isolated to Linux. But to the extent it appears anywhere, it's a bad thing). Does a programmer who does this think that (other, app) programmers (who would use his shared lib) are so absent-minded they can't remember malloc is used to allocate memory, so programmers need _every_ shared lib they use to have its own version of malloc in it? That's what I meant. I'm tired of seeing shared libs exposing essentially their own (bad, if it calls exit) version of malloc. malloc is in the C library. _That's enough._ (Oh, and the same thing with free() -- ie, pa_xfree).

It was those above two points I made, both pertinent to shared libs (using a shared lib example I found to illustrate the points -- the thread wasn't even about Pulse Audio, and surely not Pulse Audio bug reporting) that this thread was/is about, and so why I called it "How NOT to write a shared library.

It doesn't matter if the shared lib is open source or closed source (so your attempt to cause noise by arguing with your own straw man about this being "an attack on FOSS" is now officially exposed and debunked).

If you're calling malloc, check for a 0 return value, and try to recover gracefully. Do it. Especially do it in a shared lib.

I've told you several times what this thread is about. Yet you continue to maintain it's about something else. Perhaps you should stop reading the thread if you can't figure out what it's about. Or, at least stop posting in it. Thanks (in hopeful anticipation that you'll take my advice. Riiiiight).

---

### Post by nzjrs on 2007-11-19
[http://www.pulseaudio.org/ticket/158](http://www.pulseaudio.org/ticket/158)

---

### Post by j_g on 2007-11-19
That URL above was already posted, and debunked.

---

### Post by SteveHillier on 2007-11-19
> **j_g said:**
> 

I tell you. We've got to get computer science courses to teach error handling. Some graduates appear not to know what it entails. .

It is not that I disagree with the comment but it is a thorny problem.  I can remember writing code for PC in an IBM MVS -> PC comms package.  The problem there was that the mainframe host would give you error codes that conceptually did not exist in a PC.  Messages like 'Unexpected Error Occurred' are not helpful to the user or even the developer but then neither is morphing that error message to its nearest lookalike.
I am sure that situations like these occur every time you go cross platform (take the example of Linux v Windows file permissions).
My examples of course should actually highlight the comment in the quote.  Developers need to know what it entails otherwise you get a lot of c..p code being written.
Good on you j_g for raising this issue.

---

### Post by SteveHillier on 2007-11-19
> **pmasiar said:**
> I know projects where top developer creates code, with request to someone chime in and write basic docs. And someone does, and community of experts double-check it and make sure it is correct. This creates a way for top developers not to waste time on writing docs, and less expert people to contribute.

And without shooting anyone :-)

and what happens?  something gets lost in the translation.  Someone once told me they saw a comment in some code that read "When this code was written only God the the programmer knew what it did.  Now only God knows!!"
If you did it you should document it!

---

### Post by bapoumba on 2007-11-19
This thread got reported _again_. Temp closing for Staff review.

Edit: reopened.

---

